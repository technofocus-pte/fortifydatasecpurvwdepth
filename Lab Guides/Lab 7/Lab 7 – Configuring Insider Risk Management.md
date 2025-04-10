# 实验 7 – 配置内部风险管理

## 目的:

在此实验室中，我们将学习如何使用 Insider Risk Management 策略配置
Insider Risk Management。我们将使用我们在实验室 2
中创建的敏感信息类型和我们在实验室 5 中创建的 DLP
策略来创建策略，以保护组织免受有风险的浏览器使用或任何数据盗窃或泄漏的影响。

为此，我们将在 Azure
中创建一个基础结构，该基础结构将代表组织中的设备。我们将了解如何在 Azure
AD 和 Intune 中载入这些设备，并在其上安装 MDM
代理，以便可以使用它们从这些计算机获取警报。

## 练习 1：同步 VM 时钟

1.  登录到 VM 后，选择 Windows 图标。然后搜索 **Date and time，并选择
    Date and time settings** 。

![A screenshot of a computer Description automatically
generated](./media/image1.jpg)

自动生成的计算机 Description 的屏幕截图

2.  在打开的 个人设置 屏幕上，单击 **Sync now** 下 其他设置.

![A screenshot of a computer Description automatically
generated](./media/image2.jpg)

自动生成的计算机 Description 的屏幕截图

3.  这负责同步时间，以防自动同步不起作用。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image3.png)

以中等置信度自动生成的计算机描述的屏幕截图

## 练习 2：创建 Insider Risk Management 策略。

### 先决条件

#### 步骤 1 - 将用户添加到预览体验成员风险管理角色组

1.  如果 Microsoft Purview 门户已打开，请继续执行步骤 2，否则，请打开
    `https://purview.microsoft.com` 并使用 **MOD
    Administrator**凭据登录。

![](./media/image4.png)

2.  在导航中，选择 **Settings**，然后选择 **Role groups**，在 **Role
    groups下**，选择 **Insider Risk Management**。然后选择
    **Edit**。在侧窗格中，再次选择 **Edit**

![](./media/image5.png)

3.  在 **Edit Members of the role group** 页面上，选择 **Choose
    users**。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

自动生成的计算机 Description 的屏幕截图

4.  选中 **MOD Admin、Patti、Megan 和 Alex** 附近的复选框。然后选择
    **Select** 。

![](./media/image7.png)

5.  然后选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

自动生成的计算机 Description 的屏幕截图

6.  选择 **Save** 将用户添加到角色组。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

自动生成的计算机 Description 的屏幕截图

7.  选择 **Done** 以完成这些步骤。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

自动生成的计算机 Description 的屏幕截图

#### 步骤 2 - 启用内部风险分析见解

1.  在 Microsoft Purview 门户中。导航到 ** Settings**，转到 **nsider
    risk management**。转到 **Analytics**，启用单选按钮，然后单击
    **Save**。

![](./media/image11.png)

#### 第 3 步 – 载入设备

在此部署方案中，你将载入尚未载入的设备，并且你只想检测 Windows 10
设备上的内部风险活动。

我们需要在 Microsoft Entra ID
中注册我们的设备/VM，作为创建任何内部风险策略的先决条件。

1.  在 VM 上打开 Windows **Setting **。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

自动生成的计算机 Description 的屏幕截图

2.  转到 **Accounts \> Access work or school**。在 **Access** **work or
    school** 页面上，单击 **Connect**。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

自动生成的计算机 Description 的屏幕截图

3.  在**Set up a work or school account** 提示中，单击 **Join this
    device to Microsoft Entra ID。**

![](./media/image14.png)

4.  在登录提示中，使用 实验室环境的 resources 选项卡上提供的 **MOD**
    **Administrator** 凭证登录。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

自动生成的计算机 Description 的屏幕截图

![Graphical user interface, application, PowerPoint Description
automatically generated](./media/image16.png)

自动生成图形用户界面、应用程序、PowerPoint 描述

5.  在 提示 **Make sure This is your organization** 中按 **Join** 。

![Graphical user interface, text, application Description automatically
generated](./media/image17.png)

自动生成图形用户界面、文本、应用程序描述

6.  完成后，您将看到一个确认窗口**：ou're all setup！**。点击**Done**。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

自动生成的计算机 Description 的屏幕截图

7.  再次转到 **accounts \> Access work or school**。在 **Access work or
    school** 页面上，单击 **Connect**。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

自动生成的计算机 Description 的屏幕截图

8.  在 **Set up a work or school account** 提示中，使用 **MOD**
    **Administrator** 凭据登录。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

自动生成的计算机 Description 的屏幕截图

9.  在 **Setting up your device** 页面上，选择 **Got it** 。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

自动生成的计算机 Description 的屏幕截图

10. 现在转到 **windows settings \> Accounts \> Access work or school \>
    Connected to Contoso MDM \> Info \> Sync**。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

自动生成的计算机 Description 的屏幕截图

![A screenshot of a computer Description automatically
generated](./media/image22.png)

自动生成的计算机 Description 的屏幕截图

11. 单击 VM 上的 Windows 符号。选择用户 **Admin** 并选择 **Sign out**。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

自动生成的计算机 Description 的屏幕截图

12. 在用户屏幕上，选择 **Other user**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image24.png)

以中等置信度自动生成的计算机描述的屏幕截图

13. 输入实验室环境主页上提供的 O365 凭据，然后以 **MOD
    Administrator**身份登录 VM。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image25.png)

以中等置信度自动生成的计算机描述的屏幕截图

14. 关闭 Windows 设置应用程序。 ` ``在`` ` 实验室 VM 上使用 **MOD
    Administrator** 帐户登录 https://purview.microsoft.com。

15. 选择 **Settings \> Device onboarding \> Devices**。

![](./media/image26.png)

16. 单击 **Turn on Device onboarding**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

自动生成的计算机 Description 的屏幕截图

17. 从 **Settings \> Device onboarding \> Onboarding**。单击 **Download
    package**。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

自动生成的计算机 Description 的屏幕截图

18. 右键单击文件并 **Extract all ...** 。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image29.png)

以中等置信度自动生成的计算机描述的屏幕截图

![A screenshot of a computer Description automatically
generated](./media/image30.png)

自动生成的计算机 Description 的屏幕截图

19. 完成后，打开文件夹并使用**Administrator**权限运行文件。

![A computer screen with a computer screen Description automatically
generated](./media/image31.png)

带有计算机屏幕的计算机屏幕自动生成的描述

20. 单击 **More info**。

![Graphical user interface, application Description automatically
generated](./media/image32.png)

图形用户界面，自动生成应用程序描述

21. 单击 **Run anyway**。

![A screenshot of a computer error Description automatically
generated](./media/image33.png)

自动生成的计算机错误描述的屏幕截图

22. 在命令提示符中，按 **Y** 键并按 Enter 键确认并在出现提示时继续。

![A screenshot of a computer error Description automatically
generated](./media/image34.png)

自动生成的计算机错误描述的屏幕截图

23. 您将收到一条消息，指出设备已载入。在命令提示符中收到消息后，**Press
    any key to continue…**，按任意键。

24. 关闭命令提示符后，在管理员模式下打开命令提示符以运行检测测试，然后在提示符下复制并运行以下命令。命令提示符窗口将自动关闭。

`p``owershell.exe -``NoExit`` -``ExecutionPolicy`` Bypass -``WindowStyle`` Hidden $``ErrorActionPreference``= 'silentlycontinue';(New-ObjectSystem.Net.WebClient``).DownloadFile``('``http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe``'``);Start``-Process 'C:\test-WDATP-test\invoice.exe'`

![Text Description automatically generated](./media/image35.png)

自动生成文本描述

25. 通过单击导航中的设置**打开 settings**，然后选择 **Devices
    Onboarding** \> **Devices**。

**注意：**虽然启用设备载入通常需要大约 60 秒，但请最多等待 30 分钟。

26. 您将能够检查 **Devices**
    列表。在您载入设备之前，该列表将为空，完成后，您将能够看到您的 VM
    列为已载入的设备。

### 任务 1：创建组织范围的策略以检测风险浏览器使用情况并对其进行评分

#### 步骤 1 – 创建新策略

1.  如果您在上一个任务中关闭了浏览器窗口，请打开
    `https://purview.microsoft.com` 并使用管理员凭证登录。

2.  转到 **Insider Risk Management** 并选择 **Policies** 选项卡。选择
    **Create policy** 以打开策略向导。

![](./media/image36.png)

3.  在 **Choose a policy template **页面上，在 **Choose a policy
    template **下**选择  Risky browser usage (preview)**。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

自动生成的计算机 Description 的屏幕截图

4.  确保满足所有先决条件。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

自动生成的计算机 Description 的屏幕截图

5.  选择 **Next ** 继续。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

自动生成的计算机 Description 的屏幕截图

6.  在 **Name and description** 页面上，填写以下字段:

    - 姓名 （必填）：`Risky usage of browser`

    - 描述（可选）：`This is a test policy for the risky browser usage.`

7.  选择 ** Next** 继续。

![Graphical user interface, text, application Description automatically
generated](./media/image40.png)

自动生成图形用户界面、文本、应用程序描述

8.  在**Choose users, groups, & adaptive scopes **页面上，选择 **All
    users, groups, & adaptive scopes**。选择 **Next** 继续。

9.  在 **Exclude users and groups** 页上，选择 **Next**。

10. 在 **Decide whether to prioritize** 页面上，选择 **I don't want to
    specify priority content right
    now**（创建策略后，您将能够执行此作）。选择 Next 继续。

![Graphical user interface, text, application Description automatically
generated](./media/image41.png)

自动生成图形用户界面、文本、应用程序描述

11. 在  **Triggers for this policy** 页上，选择 **Turn on indicators**。

![A screenshot of a computer Description automatically
generated](./media/image42.png)

自动生成的计算机 Description 的屏幕截图

12. 在 **Choose indicators to turn on上**，选择**Select all under Risky
    browsing indicators (preview)下的“全选”**，然后取消选中其余框。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

自动生成的计算机 Description 的屏幕截图

13. 向下滚动并选择 **Save**。

14. 在 **Triggers for this policy 的 Select** **which activities will
    trigger this policy 下。** 选择所有选项，然后单击** Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image44.png)

自动生成图形用户界面、文本、应用程序描述

15. 在 **Triggering thresholds for this policy**页上，选择**Use custom
    thresholds (Recommended)**，将所有阈值更改为每天 **1**
    个，然后选择 **Next**。

![Graphical user interface, application Description automatically
generated](./media/image45.png)

图形用户界面，自动生成应用程序描述

![A screenshot of a computer Description automatically
generated](./media/image46.png)

自动生成的计算机 Description 的屏幕截图

16. 在 **indicators** 页面上，选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

自动生成的计算机 Description 的屏幕截图

17. 在 ** Decide whether to use default or custom indicator
    thresholds上**，选择 ** Use default thresholds for all
    indicators**，然后选择 ** Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image48.png)

自动生成图形用户界面、文本、应用程序描述

18. 在 **Review settings and finish上**，选择 **Submit**。

![Graphical user interface, text, application Description automatically
generated](./media/image49.png)

自动生成图形用户界面、文本、应用程序描述

19. 在 **Your policy was created** 上，选择 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image50.png)

自动生成的计算机 Description 的屏幕截图

20. 保持选项卡打开并继续执行下一个任务。

#### 步骤 2 - 对策略进行评分

1.  单击名为 **Risky usage of browser** 的新策略。选择 **Start scoring
    activity for users**。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

自动生成的计算机 Description 的屏幕截图

2.  在 **Add users to multiple policies** 窗格的 **Reason** 字段中，键入
    **Testing the policy**。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

自动生成的计算机 Description 的屏幕截图

3.  在 **This should last for （choose between 5 to 30 days）**
    字段中，选择 **10** 天。

4.  使用 **Search user to add to policies** 字段。添加 **MOD
    Admin**。然后单击 **Start scoring activity**。

5.  确认您已开始 **Scoring activity for 1 users** 后，单击 **Close**。

6.  ![A screenshot of a computer screen Description automatically
    generated with medium confidence](./media/image53.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

### 任务 2：离职用户窃取数据

#### 步骤 1 – 创建新策略

1.  如果您在上一个任务中关闭了浏览器窗口，请打开
    `https://purview.microsoft.com` 并使用管理员凭证登录。

2.  转到 **Insider Risk Management** 并选择 **Policies** 选项卡。选择
    **Create policy**以打开策略向导。

![](./media/image36.png)

3.  在 Choose a policy template 页面上，在 Data theft 下选择 Data theft
    by deleaveing users。选择 下一步 继续。

![A screenshot of a computer Description automatically
generated](./media/image54.png)

自动生成的计算机 Description 的屏幕截图

4.  在 **Name and description** 页面上，填写以下字段:

    - 姓名 （必填）：`Data theft by a user`

    - 描述（可选）：`This is a test policy for the preventing data theft.`

5.  选择 ** Next** 继续。

![A screenshot of a computer Description automatically
generated](./media/image55.png)

自动生成的计算机 Description 的屏幕截图

6.  在**Choose users, groups, & adaptive scopes **页面上，选择** All
    users, groups, & adaptive scopes**。选择 **Next ** 继续。

7.  在 **Exclude users, groups, & adaptive scopes**页面上，选择
    **Next**。

8.  在 **Decide whether to prioritize （决定是否确定优先级**）
    页面上，选择 **I want to specify priority content
    （我想指定优先内容**）。选中 **Sensitivity labels **和 **ensitive
    info types 的复选框**。选择 **Next** 继续。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image56.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

9.  在 ** Sensitivity labels to prioritize**页上，选择 ** Add or edit
    sensitivity labels**。在浮出控件窗格中，选择 ** Internal/Employee
    data (HR) **，然后单击“** Add**。然后单击 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

10. 在  **Sensitive info types to prioritize**页上，选择“ **Add or edit
    sensitive info types**。在浮出控件窗格中，**Credit Card
    Number**, **Contoso Employee ID** 和 **Contoso Employee EDM**。选择
    **Add**。然后单击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

自动生成的计算机 Description 的屏幕截图

11. 在 **Decide whether to only activity with priority content**
    上，选择 **Get alerts for all activity**。选择 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

12. 在此策略页的触发器上，选择默认值，然后选择 下一步。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image60.png)

以中等置信度自动生成的计算机描述的屏幕截图

13. 在 **Indicators** 页面上，从提示中选择 **Turn on indicators**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image61.png)

以中等置信度自动生成的计算机描述的屏幕截图

14. 在 **Select all under Office indicators ，**然后单击 **Save**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image62.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

15. 选择所有选项，然后单击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

自动生成的计算机 Description 的屏幕截图

16. 在 **Detection options**页面上，选择默认值，然后选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

自动生成的计算机 Description 的屏幕截图

17. 在** indicators **页面上，选择**Next**。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

自动生成的计算机 Description 的屏幕截图

18. 在 ** Decide whether to use default or custom indicator
    thresholds上**，选择 ** Customise thresholds**，为每个阶段分别使用
    **1**、**2** 和 **3** 个事件，然后选择 Next。

![A screenshot of a computer screen Description automatically
generated](./media/image65.png)

自动生成的计算机屏幕描述的屏幕截图

19. 在 **Review settings and finish 上**，选择 **Submit** 。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

自动生成的计算机 Description 的屏幕截图

20. 在 **Your policy was created** 上，选择 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

自动生成的计算机 Description 的屏幕截图

21. 保持选项卡打开并继续执行下一个任务。

#### 步骤 2 - 对策略进行评分

1.  单击名为 **Data theft by a user** 的新策略。选择 **Start scoring
    activity for users**。

![A screenshot of a computer Description automatically
generated](./media/image68.png)

自动生成的计算机 Description 的屏幕截图

2.  在 **Add users to multiple policies 窗格的 Reason 字段中**，键入
    **Testing the policy**。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

自动生成的计算机 Description 的屏幕截图

3.  在 **This should last for （choose between 5 to 30 days）**
    字段中，选择 **10** 天。

4.  使用 **Search user to add to policies** 字段。添加 **MOD
    Admin**。然后单击 **Start scoring activity**。

5.  确认您已开始 **Scoring activity for 1 users** 后，单击 **Close**。

![A screenshot of a computer Description automatically
generated](./media/image69.png)

自动生成的计算机 Description 的屏幕截图

### 任务 3：用户数据泄露

#### 步骤 1 – 创建新策略

1.  如果您在上一个任务中关闭了浏览器窗口，请打开
    `https://purview.microsoft.com` 并使用管理员凭证登录。

2.  转到 **Insider Risk Management** 并选择 **Policies** 选项卡。选择
    **Create policy** 以打开策略向导。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

自动生成的计算机 Description 的屏幕截图

3.  在 **Choose a policy template** 页面上，在 **Data leaks**下选择
    **Data leaks** 。选择 **Next** 继续。

![A screenshot of a computer Description automatically
generated](./media/image70.png)

自动生成的计算机 Description 的屏幕截图

4.  在 **Name and description** 页面上，填写以下字段:

    - 姓名 （必填）：`Data leaks by a user`

    - 描述（可选）：`This is a test policy for preventing data leaks.`

5.  选择 **Next** 继续。

![A screenshot of a computer Description automatically
generated](./media/image71.png)

自动生成的计算机 Description 的屏幕截图

6.  在 **Choose users and groups**页面上，选择 **Include all users and
    groups**。选择 **Next** 继续。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

自动生成的计算机 Description 的屏幕截图

7.  在 **Exclude users and groups**页上，选择 **Next**。

8.  在 **Decide whether to prioritize** 页面上，选择 **I want to specify
    priority content**。选中 **SharePoint
    网站**、**敏感度标签**和**敏感信息类型的复选框**。选择 **下一步**
    继续。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image73.png)

以中等置信度自动生成的计算机描述的屏幕截图

9.  在 **SharePoint sites to prioritize** 页面上，选择 **Add or edit
    SharePoint sites**。在弹出窗格中，选择
    `https://{TENANTPREFIX``}.sharepoint.com``/sites/ContosoWeb1` 并选择
    **Add**。然后单击 **Next**。

10. 在 **Sensitivity labels to prioritize** 页上，选择 ** Add or edit
    sensitivity labels.**。在浮出控件窗格中，选择 ** Internal/Employee
    data (HR) **，然后单击 **Add** 。然后单击 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

11. 在 **Sensitive info types to prioritize **页上，选择** Add or edit
    sensitive info types**。在浮出控件窗格中，搜索并选择 **Credit Card
    Number**, **Contoso Employee ID** 和 **Contoso Employee EDM**。选择
    **Add**。然后单击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

自动生成的计算机 Description 的屏幕截图

12. 在 **Decide whether to only activity with priority content**
    上，选择 **Get alerts for all activity** 。选择 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

13. 在 ** Triggers for this policy** 页上，选择 **User performs an
    exfiltration activity** 附近的“单选按钮”。在
    “选择将触发此策略的活动” 下，选择所有可用选项，尤其是 **Download
    content from SharePoint**。然后选择 Next 。

![A screenshot of a computer Description automatically
generated](./media/image74.png)

自动生成的计算机 Description 的屏幕截图

14. 在 **Triggering thresholds for this policy** 上，选择 **Use custom
    thresholds**。将每个阈值设置为 **1**，然后选择 **Next**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image75.png)

以中等置信度自动生成的计算机描述的屏幕截图

15. 在 **Indicators** 页面上选择默认设置**，** 然后选择 **Next**。

16. 在 ** Decide whether to use default or custom indicator thresholds**
    上，选择 ** Customise thresholds**，为每个阶段分别使用 **1**、**2**
    和 **3** 个事件，然后选择 **Next**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image76.png)

以中等置信度自动生成的计算机描述的屏幕截图

17. 在 **Review settings and finish 上**，选择 **Submit**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image77.png)

以中等置信度自动生成的计算机描述的屏幕截图

18. 在 **Your policy was created** 上，选择 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image78.png)

自动生成的计算机 Description 的屏幕截图

19. 保持选项卡打开并继续执行下一个任务。

#### 步骤 2 - 对策略进行评分

1.  单击名为 **Data leaks by a user** 的新策略。选择 **Start scoring
    activity for users**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image79.png)

以中等置信度自动生成的计算机描述的屏幕截图

2.  在 **Reason field in the Add users to multiple
    policies**窗格 中，键入 Testing the policy。在 **This should last
    for （choose between 5 to 30 days）** 字段中，选择 **10** 天。使用
    **Search user to add to policies** 字段。添加 **MOD
    Admin**。然后单击 **Start scoring activity**。

3.  确认您已开始 **Scoring activity for 1 个用户**后，单击 **Close**.

您已成功创建 Insider 风险管理策略。

## 总结：

在此实验室中，我们探索了从端到端设置 Insider Risk
Management。使用您自己的订阅和许可证，您还可以使用此实验室指南创建一个
Azure 设置，该设置还可用于为 Insider Risk
管理策略创建各种警报（包括发送包含受限数据的电子邮件，这无法通过试用订阅实现），您可以使用这些策略来探索
Purview 上的自适应保护功能。
