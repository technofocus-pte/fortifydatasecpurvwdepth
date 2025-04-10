# 实验 9 – 配置通信合规性

## 目的:

在本实验中，您将配置合规性策略，以检测组织中用户传达的任何敏感信息。您将使用在前面的实验室中创建的敏感信息类型来检测通过电子邮件传达的员工健康数据或员工
ID。

## 练习 1 - 启用通信合规性权限

在此任务中，您将用户分配到特定角色组，以对组织中不同用户之间的通信合规性、访问权限和职责进行分段。

1.  如果 Microsoft Purview 门户已打开，请继续执行步骤 2，否则，请打开
    `https://purview.microsoft.com` 并使用 **MOD Administrator**
    凭据登录。

2.  在导航中，选择 **Settings**，然后选择 **Role groups**，在 **Role
    groups** 下，选择Communication Compliance。然后选择
    **Edit**。在侧窗格中，再次选择 **Edit**。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

自动生成的计算机 Description 的屏幕截图

3.  在 **Edit members of the role group** 上，选择 **Choose Users** 。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

自动生成的计算机 Description 的屏幕截图

4.  确保选择 **MOD Administrator**、**Megan Bowen** 和 **Patti
    Fernandez**。然后选择 **Select**。

![](./media/image3.png)

5.  选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

自动生成的计算机 Description 的屏幕截图

6.  选择 **Save** 将用户添加到角色组。选择 **Done** 以完成这些步骤。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

自动生成的计算机 Description 的屏幕截图

![A screenshot of a computer Description automatically
generated](./media/image6.png)

自动生成的计算机 Description 的屏幕截图

## 练习 2 - 设置通信合规性组

在该策略中，您将使用电子邮件地址来识别个人或人群。为了简化设置，您可以为审核其通信的人员创建组，并为审核这些通信的人员创建组。

可以使用 PowerShell
为分配的组配置全局通信合规性策略的通讯组。这使您能够使用单个策略检测数千个用户的消息，并在新员工加入组织时保持通信合规性策略更新。

1.  在管理员模式下打开 **PowerShell**。

2.  输入以下 cmdlet 以使用 **Exchange Online PowerShell**
    模块并连接到您的租户：

`Connect-``ExchangeOnline`

![Text Description automatically generated](./media/image7.png)

自动生成文本描述

3.  当显示 **Sign in** 窗口时，以 **MOD Administrator 身份登录**。

![BrokenImage](./media/image8.png)

4.  使用以下属性为全局通信合规性策略创建专用通讯组:

    - **MemberDepartRestriction =
      Closed**。确保用户无法将自己从通讯组中删除。

    - **MemberJoinRestriction = Closed**确保用户无法将自己添加到通讯组。

    - **ModerationEnabled =
      True**。确保发送到此组的所有消息都需要审批，并且该组不用于通信合规性策略配置之外的通信。

`New-DistributionGroup -Name "Communication Compliance Group Contoso" -Alias "CCG_Contoso" -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true`

![BrokenImage](./media/image9.png)

**注意：**可以按  **following command** 添加 **Exchange Custom
Attribute**，以跟踪添加到组织中通信合规性策略的用户。

`Set-``DistributionGroup`` -Identity "Communication Compliance Group Contoso"-CustomAttribute1 "MonitoredCommunication"`

![A screen shot of a computer Description automatically
generated](./media/image10.png)

自动生成的计算机描述的屏幕截图

5.  按定期计划运行以下 PowerShell 脚本，将用户添加到通信合规性策略：

&nbsp;

    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
    Write-Host "Adding" $M.DisplayName
    Add-DistributionGroupMember -Identity "Communication Compliance Group Contoso" -Member $M.DistinguishedName -ErrorAction SilentlyContinue
    Set-Mailbox -Identity $M.Alias -CustomAttribute1 "MonitoredCommunication"
    $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."

![BrokenImage](./media/image11.png)

**注意：**此脚本应该在每个特定间隔后运行。截至现在，您将能够在Microsoft
365 admin中心的活跃团队和组下看到分发列表。

如果单击组名称，您将能够看到 members 选项卡下列出的所有用户。

![BrokenImage](./media/image12.png)

## 练习 3 - 创建通信合规性策略

1.  如果 **Microsoft Purview** 合规门户已打开，请继续执行步骤
    2，否则，请打开 `https://purview.microsoft.com` 并以 **MOD
    Administrator** 身份登录。

2.  在 Microsoft Purview 门户中，选择 **Soltions** \> **Communication
    compliance**。

3.  从子导航中选择，选择 **Policy**。然后选择 **Create policy**。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

自动生成的计算机 Description 的屏幕截图

4.  从下拉列表中选择 **Custom policy**。

![](./media/image14.png)

5.  在 “命名 DLP 策略 ”页上，在 ` `**Name** 字段中键入 My first
    communication compliance policy，并在  **Description** 字段中键入
    This is a policy to test communication compliance。选择 **Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image15.png)

自动生成图形用户界面、文本、应用程序描述

6.  在 **Choose supervised users and
    reviewers**页面上，保留其余的默认设置，并在 “审阅” 下添加 **Patti
    Fernandez**。然后点击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

自动生成的计算机 Description 的屏幕截图

7.  在 **communications**页面上，选中 **Microsoft 365 locations**
    下的所有框，然后单击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

自动生成的计算机 Description 的屏幕截图

8.  在 ** Choose conditions and review percentage** 上，选择 **Add
    condition**，从下拉列表中选择 **Content contains any of these
    sensitive info types**。

![A screenshot of a computer screen Description automatically
generated](./media/image18.png)

自动生成的计算机屏幕描述的屏幕截图

9.  在  **Content contains any of these sensitive info types**
    框中，选择 ** Add**，单击 ** Sensitive info types**，然后搜索
    **contoso**。选中我们在早期实验室中创建的所有敏感信息类型的框。然后单击
    **Add**

![Graphical user interface, text, application Description automatically
generated](./media/image19.png)

自动生成图形用户界面、文本、应用程序描述

10. 在 **Choose conditions and review percentage** 上，选中 **Use OCR to
    extract text from images** 旁边的框，将 ** Review percentage to
    100%，**然后单击 Next。

![Graphical user interface, application Description automatically
generated](./media/image20.png)

图形用户界面，自动生成应用程序描述

11. 在 **Review and finish**页面上，选择 **Create policy**。

![Graphical user interface, text, application Description automatically
generated](./media/image21.png)

自动生成图形用户界面、文本、应用程序描述

12. 系统会显示 **Your policy was
    created**页面，其中包含有关何时激活政策以及将捕获哪些通信的指南。![Graphical
    user interface, text, application Description automatically
    generated](./media/image22.png)

自动生成图形用户界面、文本、应用程序描述

## 练习 4 - 编辑通信合规性策略

1.  如果 Microsoft Purview 合规门户已打开，请继续执行步骤
    2，否则，请打开 `https://purview.microsoft.com` 并以 **MOD
    Administrator**身份登录。

2.  在 Microsoft Purview 门户中，转到 **Settings \> Communication
    compliance \> Policies**，选择 **My first communication compliance
    policy** 旁边的三个点 ，然后选择 **Edit**。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

自动生成的计算机 Description 的屏幕截图

3.  将 **Name and description your policy** 留空，然后单击 **Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image24.png)

自动生成图形用户界面、文本、应用程序描述

4.  在 **Choose supervised user and reviewers** 和 **Supervised
    users and groups下**，选择  **Select users** 按钮。

![Graphical user interface, application, Teams Description automatically
generated](./media/image25.png)

自动生成图形用户界面、应用程序、Teams 描述

5.  在 **Start typing to find users or groups** 中，搜索
    **Communication **，然后选择 ** Communication Compliance Groups
    Contoso**。

![](./media/image26.png)

6.  在 Choose supervised user and reviewers上，在 Reviewers下，将 MOD
    Administrator 添加到 Reviewers。

![Graphical user interface, application, Teams Description automatically
generated](./media/image27.png)

自动生成图形用户界面、应用程序、Teams 描述

7.  选择 **Next**，直到到达 **Review and finish** 页面。

8.  点击 **Save**。

## 练习 5 – 创建通知模板并配置用户匿名化

1.  在 Microsoft Purview 门户中，选择右上角的 Settings，然后选择
    **Communication compliance**。

![](./media/image28.png)

2.  选择 Privacy 选项卡。要启用匿名化，请确保选中 **Show anonymized
    versions of username。**选择 **Save**。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

自动生成的计算机 Description 的屏幕截图

3.  导航到 **Notice templates** 选项卡，然后选择 **Create notice
    template**。

![](./media/image30.png)

4.  在 **Modify a notice template** 页面上，填写以下字段：

    - 模板名称 （必填）: 样品通知

    - 发送自 （必填）: 通过键入 **Patti** 并从下拉列表中选择姓名来选择
      **Patti Fernandez。**

    - CC（可选）: 通过键入 MOD 并从下拉列表中选择名称来选择 MOD
      administrator。

    - 主题 （必填）：你的通信违反了公司的通信合规性策略。

    - 消息正文
      （必填）：请记下这一点以备将来参考，并为您当前的通信提供可接受的理由。

5.  选择 **Create** 以创建并保存通知模板。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

自动生成的计算机 Description 的屏幕截图

## 练习 6 - 测试通信合规性策略

在试用帐户中，您将无权发送任何电子邮件，但可以查看以下步骤，了解如何在拥有自己的许可证时测试策略。您可以执行步骤，但您的邮件将无法从当前租户到达收件人。

1.  转到 https://outlook.office365.com/mail/ 打开
    Outlook，然后使用用户名 `adelev``@{TENANTPREFIX}.``onmicrosoft.com`
    和用户密码登录。

2.  向您的个人电子邮件账户发送一封电子邮件，其中包含以下邮件正文。

消息正文: `Employee Patti Fernandez EMP123456 is on absence because of the flu/influenza`

**注意** 电子邮件可能需要大约 24 小时才能在策略中完全处理。Microsoft
Teams、Yammer 和第三方平台中的通信可能需要大约 48
小时才能在策略中完全处理。

以 `Patti Fernandez`` 的身份`登录 https://purview.microsoft.com/。导航到
**Communication compliance \> Alerts** ，在 24 小时后查看策略的警报。

**总结:**

在本实验中，我们学习了如何启用通信合规性权限、创建策略、管理策略，然后创建通知模板并配置用户匿名化。
