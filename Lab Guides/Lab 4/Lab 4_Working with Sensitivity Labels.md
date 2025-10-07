**实验室 4_使用敏感度标签**

## 介绍

在本练习中，你将扮演 Contoso Ltd 的系统管理员 Patti Fernandez
的角色。你的组织位于德国
Rednitzhembach，目前正在实施敏感度计划，以确保人力资源部门中的所有员工文档都已标记为敏感度标签，作为组织信息保护策略的一部分。

**目标**

- 在 Microsoft 365 和 SharePoint 中启用对敏感度标签的支持。

- 使用保护设置创建和发布敏感度标签和子标签。

- 在 Microsoft 365 应用 （Word、Outlook、OneDrive） 中应用敏感度标签。

- 根据敏感信息类型配置和测试自动标记策略。

## 练习 1 – 启用对敏感度标签的支持

在此任务中，你将安装 MSOnline 模块和 SharePoint Online PowerShell
模块，并在租户上启用对敏感度标签的支持。

1.  右键单击 Windows 图标，然后导航并单击 **Windows PowerShell (Admin)**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  在“**User Account Control** ”对话框中，单击“**Yes**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  输入以下 cmdlet 以安装最新的 Microsoft Online PowerShell 模块版本:

**+++Install-Module -Name MSOnline+++**

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  在 **You are installing the modules from an untrusted repository...
    message**，键入 **Y**，然后按 Enter 按钮

> ![BrokenImage](./media/image4.png)

5.  输入以下 cmdlet 以安装最新的 SharePoint Online PowerShell 模块版本:

**+++Install-Module -NameMicrosoft.Online.SharePoint.PowerShell+++**

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  在 **You are installing the modules from an untrusted repository...
    message**,键入 **Y**，然后按 Enter 按钮

> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

7.  输入以下 cmdlet 以连接到 Microsoft Online 服务:

**+++Connect-MsolService+++**

![BrokenImage](./media/image7.png)

8.  在**Sign in to your account** 表单中，使用资源选项卡上提供的用户名
    **PattiF@WWLxXXXXXX.onmicrosoft.com** 和用户密码以 **Patti
    Fernandez** 身份登录。

> ![A screenshot of a computer screen AI-generated content may be
> incorrect.](./media/image8.png)
>
> ![A screenshot of a computer program AI-generated content may be
> incorrect.](./media/image9.png)

9.  输入以下 cmdlet 以获取域:

**+++\\domain = get-msoldomain+++**

![BrokenImage](./media/image10.png)

10. 输入以下 cmdlet 以创建 SharePoint 管理员 URL:

**+++\\adminurl = "https://" +\\domain.Name.split('.')\[0\] +"-admin.sharepoint.com"+++**

![A screenshot of a computer screen Description automatically
generated](./media/image11.png)

11. 输入以下 cmdlet 以登录到 SharePoint Online 管理中心:

**+++Connect-SPOService -url \\adminurl+++**

![A screenshot of a computer screen Description automatically
generated](./media/image12.png)

12. 在“**Sign in to your
    account** ”窗体中，使用实验室环境的“资源”选项卡中提供的凭据以 **MOD
    Administrator** 身份登录。![A screenshot of a computer screen
    AI-generated content may be incorrect.](./media/image13.png)

13. 输入以下 cmdlet 以启用对敏感度标签的支持:

**+++Set-SPOTenant -EnableAIPIntegration $true+++**

![BrokenImage](./media/image14.png)

14. 使用 **Y** 表示是确认更改，然后按 Enter。

![BrokenImage](./media/image15.png)

15. 关闭 **PowerShell** 窗口。

已成功启用对 Teams 和 SharePoint 网站敏感度标签的支持。

## 练习 2 – 创建敏感度标签

在此任务中，人力资源部门已请求将敏感度标签应用于人力资源员工文档。你将为内部文档创建敏感度标签，并为
HR 部门创建子标签。

1.  在私人窗口中打开 **Microsoft Edge** 浏览器，导航到
    **+++**https://purview.microsoft.com**+++**并使用资源选项卡上给出的用户名
    **PattiF@WWLxXXXXXX.onmicrosoft.com** 和用户密码以 Patti Fernandez
    身份登录。

2.  在Microsoft Purview 门户的左侧导航窗格中，选择“**Solutions** \>
    **Information Protection**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

3.  从子导航中，选择“**Sensitivity Labels** \> **Create Labels**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

4.  “**New sensitivity label**”向导将启动。在“**Name**”、“**Description
    for admins**”和**“Description for users “Label
    details ”**页上，输入以下信息:

    - 名字: **+++Internal+++**

    - 显示名称: **+++Internal+++**

    - 用户说明: **+++Internal sensitivity label+++**

    - 管理员说明: **+++Internal sensitivity label for Contoso.+++**

    - ![A screenshot of a computer AI-generated content may be
      incorrect.](./media/image18.png)

5.  选择 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

6.  在“**Define the scope for this label** ”页上，确保选中“**Files &
    other data
    assets**”复选框。然后，取消选中“**Meetings**”复选框，然后单击“**Next**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  在“**Choose protection settings for the types of items you
    selected**”页上，单击“**Next**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

8.  在“文件和电子邮件的 **Auto-labeling** ”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

9.  在“**Define protection settings for groups and
    sites**”页上，选择“**Next**”。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

10. 在“**Review your settings and finish** ”页上，单击“**Create
    label**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

11. 在“**Your sensitivity label was created**”页上，导航并选择“**Don’t
    create a policy yet**”单选按钮。然后，单击“**Done**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

12. 在“**Information
    protection**”页上，导航到“**Internal**”标签，然后选择垂直省略号 

13. 然后，导航并单击 **Create sublabel**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

14. “**New sensitivity label”**向导将启动。在 Label details 页上
    ，输入以下信息:

    - 名字: **+++Employee data (HR) +++**

    - 显示名称: **+++Employee data (HR) +++**

    - 用户说明: **+++This HR label is the default label for all
      specified documents in the HR Department. +++**

    - 管理员说明: **+++This label is created in
      consultation with Ms.Jones (Head of HR department). Contact her,
      when you want to change settings of the label. +++**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

15. 在“**Define the scope for this
    label ”**页上，确保选中“文件和其他数据资产”、“电子邮件”和“会议”复选框，然后单击“**Next**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

16. 在“**Choose protection settings for labeled
    items** ”页上，选择“**Control Access** ”选项。选择 **Next**。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

17. 在**Access control**页面上，确保选择 **Configure access control
    settings**。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

18. 在加密设置中输入以下信息:

    - 立即分配权限还是让用户决定？：**Assign permissions now**

    - 用户对内容的访问权限过期：**Never**

    - 允许离线访问：**Only for a number of days**

    - 用户可以在这许多天内离线访问内容：**15**

    &nbsp;

    - ![A screenshot of a computer AI-generated content may be
      incorrect.](./media/image32.png)

19. 选择“**Assign permissions** ”链接。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

20. 在“**Assign permissions** ”窗格中，选择“**+ Add any authenticated
    users**”。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image34.png)

21. 选择 **Save。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

22. 在“**Access control**”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

23. 在“**Auto-labeling for files and emails** ”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

24. 在“**Define protection settings for groups and
    sites**”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

25. 在“**Review your settings and finish**”页上，选择“**Create
    label**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

26. 在“**Your sensitivity label was created**”页上，选择“尚**Don’t
    create a policy yet**”单选按钮，然后单击“**Done**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

已成功为组织内部策略创建敏感度标签，并为人力资源 （HR）
部门创建敏感度子标签。

## 练习 3 – 发布敏感度标签

现在，你将发布内部和 HR 敏感度标签，以便 HR
用户可以使用已发布的敏感度标签应用于其 HR 文档。

1.  在 **Microsoft Edge** 中，导航到
    **+++https://purview.microsoft.com+++**，然后使用资源选项卡上提供的用户名
    **PattiF@WWLxXXXXXX.onmicrosoft.com** 和用户密码以 **Patti
    Fernandez** 身份登录。 

2.  在Microsoft Purview 门户的左侧导航窗格中，选择“**Solutions** \>
    **Information Protection**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

3.  从子导航中，选择“**Sensitivity Labels** \> **Publish Labels**”。

![](./media/image42.png)

4.  发布敏感度标签向导将启动。

5.  在“**Choose sensitivity labels to publish**”页上，选择“**Choose
    sensitivity labels to publish** ”链接。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

6.  右侧将显示一个名为“**Sensitivity labels to publish**”的侧栏。

7.  选中**I nternal** 和 **Internal/Employee Data
    (HR)** 复选框。选择**Add**。 

![](./media/image44.png)

8.  在“**Choose sensitivity labels to publish**”页上，选择“**Next**”。

![](./media/image45.png)

9.  在“Assign admin units”页上，选择“**Next**”。

![](./media/image46.png)

10. 在“**Publish to users and groups**”页上，确保选中“**Users and
    groups**”复选框，然后单击“**Next**”按钮。

![](./media/image47.png)

11. 在“**Policy settings** ”页上，选择“**Next**”。

![](./media/image48.png)

12. 在 **Apply a default label to documents** 页上，选择**Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

13. 在“**Apply a default label to emails**”页上，选择“**Next**”。 

> ![](./media/image50.png)

14. 在 **Default settings for meetings and calendar events**
    上，选择**Next**。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image51.png)

15. 在“**Default settings for Fabric and Power BI
    content**”页上，选择“**Next**”。** **

> ![](./media/image52.png)

16. 在“**Name your policy**”页上，输入以下信息，然后单击“**Next**”按钮:

    - **名字**: **+++Internal HR employee data+++**

    - **输入敏感度标签策略的说明**: **+++This HR label is to be applied
      to internal HR employee data. +++**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

17. 在“**Review and finish** ”页上，选择“**Submit**”。

![](./media/image54.png)

18. 将创建策略，完成后将显示一条消息，显示 **New policy created**。

19. 选择 **Done and proceed to next task without closing the window**。

![](./media/image55.png)

已成功发布内部和 HR 敏感度标签。请注意，更改最多可能需要 24
小时才能复制到所有用户和服务。

## 练习 4 – 使用敏感度标签

在此任务中，你将在 Word 和 Outlook
电子邮件中创建敏感度标签。创建的文档将存储在 OneDrive
中，并通过电子邮件发送给人力资源员工。

1.  导航到 **+++https://portal.office.com+++**并以 Patti **Fernandez**
    身份登录。

2.  如果出现“**Copilot everywhere you need it**”对话框，然后将其关闭。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

3.  现在，单击左侧导航菜单上的**Apps**，然后单击 **Word**。![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image57.png)

4.  **Welcome, Patti Fernandez!** 页面，单击“**Create blank
    document**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

5.  如果出现“**Your privacy options**”消息，请单击“**Close**”按钮。 

![](./media/image59.png)

6.  在word文档中输入以下内容:

**+++Important HR employee document.+++**

7.  然后，从顶部窗格中选择 **Sensitivity**
    以打开下拉菜单，导航并单击**Internal**。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

注意：如果在下拉菜单中没有看到“**内部**”，请选择“**机密 -
财务**”并跳过步骤 8。✅

8.  单击“**Employee data (HR)**”以应用标签。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

**注意**： 请注意，在本练习的任务 1 中运行的脚本在 Word
中为租户激活了敏感度标签。有时可能需要一个小时才能在 Microsoft Word
在线中实现该激活。如果在 Word
中看不到“敏感度标签”菜单，则可能需要稍后返回到此实验室，或确保正确完成本练习的任务
1。

9.  选择 **Document – Saved** 在窗口的左上角，输入 **HR
    Document** 作为文件名，然后按 **Enter** 键。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

10. 关闭单词选项卡。在 M365 Copilot – 应用页面中，单击 **Outlook**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

11. 如果出现“**Your privacy matters**”对话框，请单击“**Continue**”按钮。

![A screen shot of a computer AI-generated content may be
incorrect.](./media/image64.png)

12. 在 Outlook 网页版中，从 窗口左上角选择“**New message**”。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

13. 在收件人字段中输入名称：**Adele**，然后从下拉列表中选择 **Adele
    Vance**。 

![](./media/image66.png)

14. 在主题字段中，输入: **+++Employee data for HR+++**.

15. 在电子邮件正文中，插入以下消息:

> **+++Dear Ms. Adele,**
>
> **Please find attached the important HR employee document.**
>
> **Kind regards,**
>
> **Patti Fernandez+++**

![A screenshot of a computer Description automatically
generated](./media/image67.png)

16. 从底部菜单中选择**回形针符号。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. 选择 **Suggested attachments** 下方的 **HR Document.docx** 
    以附加文档。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image70.png)

18. 选择**“Send”**以发送带有附加文档的电子邮件。

19. 保持浏览器窗口打开。

你已成功创建具有敏感度标签的 HR Word 文档，该文档已保存到 OneDrive
中。然后，你通过电子邮件将文档发送给 HR
工作人员，其中电子邮件也设置了敏感度标签。

请注意，在试用帐户中，您将能够发送邮件，但它会退回，并且无法从当前租户到达收件人。

## 练习 5 – 配置自动标记

在此任务中，你将创建一个 **Sensitivity
Label** ，该标签将自动标记发现包含与 **European General Data Protection
Regulation (GPDR)** 相关的信息的文档和电子邮件。

1.  在 **Microsoft Edge** 中，Microsoft Purview 门户选项卡仍应打开。

2.  您应该以 **Patti Fernandez** 的身份登录门户。

3.  在“**Information protection**”下，导航并单击“**Sensitivity**
    **Labels**”，选中“**Internal
    label**”旁边的复选框，然后单击垂直省略号。导航并单击 **+ Create
    sublabel**。

![](./media/image71.png)

4.  “**New sensitivity label** ”向导将启动。在 **label details**
    页上，输入以下信息 :

    1.  名字: **+++GDPR Germany+++**

    2.  显示名称: **+++GDPR Germany+++**

    3.  用户说明: **+++This document or email contains data related to
        the European General Data Protection Regulation(GPDR) for the
        region Germany. +++**

    4.  管理员说明: **+++This label is auto applied to German GDPR
        documents. +++**

5.  选择 **Next**。

![](./media/image72.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

6.  在“**Define the scope for this label** ”页上，确保选中“**Files &
    other data assets,
    Emails,**”和“**Meetings**”复选框，然后单击“**Next**”按钮。

![](./media/image74.png)

7.  在“**Choose protection settings for the types of items you
    selected**”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

8.  在“**Auto-labeling for files and
    emails** ”页上，打开“**Auto-labeling for files and
    emails**”切换开关。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

9.  在“**Detect content that matches these
    conditions** ”部分中，选择“**+Add condition** ”，然后选择“**Content
    contains**”。

![](./media/image77.png)

10. 在“**Content contains** ”部分中，选择“**Add**”，然后选择“**Sensitive
    info types**”。 ![](./media/image78.png)

11. 右侧将显示“**Sensitive info types** ”面板。

12. 在“**Search for sensitive info types**”搜索面板中，输入以下信息:

**+++German+++**

13. 按回车键，结果将显示与德国相关的灵敏度信息类型。选中“**Name**”旁边的复选框
    以选择所有敏感信息类型。

![BrokenImage](./media/image79.png)

14. 选择 **Add**。 

![BrokenImage](./media/image80.png)

15. 选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image81.png)

16. 在“**Define protection settings for groups and
    sites** ”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

17. 在“**Review your settings and finish**”页上，选择“**Create
    label**”。 

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image83.png)

18. 在“**Your sensitivity label was created**”页上，选择“**Automatically
    apply label to sensitive
    content**”的单选按钮，然后单击“**Done**”按钮。

![](./media/image84.png)

19. 从子导航中，选择“**Sensitivity Labels** \> **Publish Labels**”。

![](./media/image85.png)

20. “**Publish sensitivity labels**”向导将启动。 

21. 在“**Choose sensitivity labels to publish**”页上，选择“**Choose
    sensitivity labels to publish**”链接。

![](./media/image86.png)

22. **Sensitivity labels to publish**
    窗格将显示在右侧。导航并选中“**Internal** ”和“**Internal/GDPR
    Germany** ”复选框，然后单击“**Add**”按钮**。**

![](./media/image87.png)

23. 在“**Choose sensitivity labels to publish**”页上，选择“**Next**”。

![](./media/image88.png)

24. 在“Assign admin units”页上，单击“**Next**”按钮。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image89.png)

25. 在“**Publish to users and groups** ”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

26. 在“**Policy settings** ”页上，选择“**Next** ”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

27. 在 **Apply a default label to documents** 页上，选择**Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

28. 在“**Apply a default label to emails** ”页上，选择“**Next**”。

> ![A screenshot of a computer screen AI-generated content may be
> incorrect.](./media/image93.png)

29. 在 **Default settings for meetings and calendar events** 上，选择
    **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

30. 在“**Default settings for Fabric and Power BI
    content **”页上，选择“**Next**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

31. 在“**Name your policy**”页上，输入以下信息:

    1.  名字: **+++GDPR Germany policy+++**

    2.  输入敏感度标签策略的说明: **+++This auto apply sensitivity
        labels policy is for the GDPR region of Germany. +++**

32. 选择 **Next**。

![](./media/image96.png)

33. 在“**Review and finish** ”页上，选择“**Submit**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

34. 在“**New policy created**”页面上，单击“**Done**”按钮。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

## 总结

在本实验室中，你担任 Contoso Ltd. 的系统管理员 Patti Fernandez
的角色，并使用 Microsoft Purview 敏感度标签实现信息保护。使用 PowerShell
在 SharePoint 和 Teams
中启用了敏感度标签支持，创建并发布了内部标签和特定于 HR 的子标签，并在
Word 文档和 Outlook 电子邮件中应用了这些标签。你还为特定于德国的 GDPR
相关内容创建并发布了自动标记敏感度标签。这些步骤可确保人力资源和监管文件在组织内得到正确分类和保护。
