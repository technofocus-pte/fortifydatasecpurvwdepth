# 实验 2 — 管理敏感信息类型

## 目的:

Contoso Ltd.
以前遇到过员工在工单解决方案中处理支持工单时意外发送客户的个人信息的问题。

为了在将来教育用户，需要自定义敏感信息类型来识别电子邮件和文档中的员工
ID，这些 ID
由三个大写字符和六个数字组成，使用敏感信息类型。为了降低误报率，将使用关键字
“Employee” 和 “IDs”。

在本练习中，您将创建：

- 新的自定义敏感信息类型

- 基于 EDM 的分类数据库

- 关键字字典

## 练习 1 – 创建自定义敏感信息类型

在本练习中，你将使用 **Security & Compliance Center PowerShell**
模块创建新的自定义敏感信息类型，该类型可识别关键字“Employee”和“ID”附近的员工
ID 模式。

1.  在 **Microsoft Edge** 中，打开 **New InPrivate Window**，导航到
    `https://purview.microsoft.com` 并使用用户名
    PattiF@{TENANTPREFIX}.onmicrosoft.com 和资源选项卡上提供的用户密码以
    **Patti Fernandez**` ``身份登录`` `
    。如果系统提示，请同意条款和条件，然后选择 **Get started**。

2.  从左侧导航栏中，选择 **Solutions** \> **Data Loss Prevention**。

![](./media/image1.png)

3.  从左侧窗格中选择 **Classifiers。**从子导航窗格中选择 **Sensitive
    info types** 。选择 **+Create sensitive info
    type**以打开新敏感信息类型的向导。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

自动生成的计算机 Description 的屏幕截图

4.  在 **Name your sensitive info type**页上，输入以下信息:

    - **Name**: `Contoso Employee IDs`

    - **Description**: `Pattern for Contoso Employee IDs.`

5.  选择 **Next**。

![Graphical user interface, application Description automatically
generated](./media/image3.png)

图形用户界面，自动生成应用程序描述

6.  在 Define patterns for this sensitive info type 页上，选择 Create
    pattern。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

自动生成的计算机 Description 的屏幕截图

7.  在右侧的 **New pattern** 窗格中，选择 **Add primary element**
    ，然后选择 **Regular expression**。

![Graphical user interface, application, Teams Description automatically
generated](./media/image5.png)

自动生成图形用户界面、应用程序、Teams 描述

8.  在新的右侧窗格 **Add a regular expression** 中，输入以下内容:

    - **ID**: `Contoso IDs`

    - **Regular expression**: `\s\[A-Z\]{3}\[0-9\]{6}\s`

    - Select **String match**

9.  选择 **Done**。

![Graphical user interface, application Description automatically
generated](./media/image6.png)

图形用户界面，自动生成应用程序描述

10. 再次在右侧的 **New pattern** 窗格中，**在 Supporting elements
    下**，选择 **+ Add supporting elements or group of
    elements**下拉菜单，然后选择 **Keyword list**。

![Graphical user interface, application Description automatically
generated](./media/image7.png)

图形用户界面，自动生成应用程序描述

10. 在新的右侧窗格 **Add a keyword list** 中，输入以下内容:

    - **ID**: `Employee ID keywords`

    - **Case insensitive**:

&nbsp;

    Employee
    ID

11. 在 Case Sensitive ***字段***下为 **Word match** 选择径向

12. 选择 **Done**。

![Graphical user interface, text, application Description automatically
generated](./media/image8.png)

自动生成图形用户界面、文本、应用程序描述

13. 在 New pattern 窗口中，将 **Character proximity** 值减少到 ***100***
    个字符。

![Graphical user interface, text, application Description automatically
generated](./media/image9.png)

自动生成图形用户界面、文本、应用程序描述

14. 选择 **Create** 按钮。

15. 返回 **Define patterns for this sensitive info type** 页，选择
    **Next**。

![Graphical user interface, text, application, Teams Description
automatically generated](./media/image10.png)

自动生成图形用户界面、文本、应用程序、Teams 描述

16. 在 **Choose the recommended confidence level to show in compliance
    policies** 页面上，使用默认值，然后选择 **Next**。

![BrokenImage](./media/image11.png)


17. 在 **Review settings and finish** 页面上，查看设置并选择
    **Create**。成功创建后，选择 **Done**。

![Graphical user interface, text, application Description automatically
generated](./media/image12.png)

自动生成图形用户界面、文本、应用程序描述

18. 使浏览器窗口保持打开状态。

您已成功创建新的敏感信息类型，以 3 个大写字符、6 个数字和 100
个字符范围内的关键字“Employee”或“ID”模式标识员工 ID。

## 练习 2 – 创建基于 EDM 的分类信息类型

作为额外的搜索模式，您将使用员工数据的数据库架构创建基于 EDM
的分类。数据库源文件将使用员工的以下数据字段进行格式设置：Name、Birthdate、StreetAddress
和 EmployeeID。

1.  选择 **Solutions \> Data Loss Prevention \> Classifiers**，导航到
    **EDM classifiers**，关闭 **New EDM experience**，然后从 EDM Schema
    中选择**+ Create EDM schema** 以创建新的架构定义。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

自动生成的计算机 Description 的屏幕截图

2.  在 **Name** 字段中，输入 employeedb。

3.  在 **Description** 字段中，输入 Employee Database schema..

4.  启用 **Ignore delimiters and punctuation for all schema fields**。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

自动生成的计算机 Description 的屏幕截图

5.  单击 **Choose delimiters and punctuation** **的下拉列表，**然后选择
    **Hyphen, Period, Space, Open parenthesis** 和 **Close
    parenthesis**。

![Graphical user interface, application Description automatically
generated](./media/image15.png)

图形用户界面，自动生成应用程序描述

6.  在第一个 Schema field name 中，输入 `Name` 并标记 **Field is
    searchable** 框。

7.  从 下端选择 **+ Add schema data field**。

![BrokenImage](./media/image16.png)


8.  在 **Schema field name 中的** Schema field \#2 **下**，输入
    `Birthdate`。

9.  再次从下端选择 **+ Add schema data field**。

&nbsp;

10. 在 **Schema field name** 中，在 **Schema field \#3** 下，输入
    `StreetAddress`。

11. 最后一次从下端选择 **+ Add schema data field**。

12. 在 **Schema field name 中的 Schema field \#4 下**，输入
    `EmployeeID`。

13. 选择 **Field is searchable**。

14. 选择 **Save**。

![Graphical user interface, application Description automatically
generated](./media/image17.png)

图形用户界面，自动生成应用程序描述

15. 从左窗格中选择 **EDM sensitive info types**，然后选择 **+ Create EDM
    sensitive info type** 以打开 **EDM rule package** 向导。

![](./media/image18.png)

16. 在 **Define data store schema** 页面上，选择 **Choose an existing
    EDM schema**。

![Graphical user interface, application Description automatically
generated](./media/image19.png)

图形用户界面，自动生成应用程序描述

17. 选择 **employeedb** ，然后选择 **Add**。

![Graphical user interface, text, application Description automatically
generated](./media/image20.png)

自动生成图形用户界面、文本、应用程序描述

18. 查看数据存储架构，然后选择 **Next**。

![Graphical user interface, application Description automatically
generated](./media/image21.png)

图形用户界面，自动生成应用程序描述

19. 在 **Define patterns for this EDM sensitive info type** 页上，选择
    **+ Create pattern**。

![Graphical user interface, application Description automatically
generated](./media/image22.png)

图形用户界面，自动生成应用程序描述

20. 在右侧的 **New pattern** 窗格的 **Primary element** 字段中，选择
    ***EmployeeID***。

21. 在 **Primary element's sensitive information type**下，选择 **Choose
    sensitive information type** 。

![A screenshot of a pattern Description automatically
generated](./media/image23.png)

自动生成的模式 Description 的屏幕截图

22. 在 **Search** 栏中，输入 ***Contoso*** 并按 Enter 键。

23. 选择 **Contoso Employee ID，** 然后选择 **Done**。

24. 选择 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

自动生成的计算机 Description 的屏幕截图

25. 在 **Define patterns for this EDM sensitive info type** 屏幕中选择
    **Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image25.png)

自动生成图形用户界面、文本、应用程序描述

26. 在 **Choose the recommended confidence level and character
    proximity** 中，保留默认值，然后选择 **Next**。

![Graphical user interface, text, application, Word Description
automatically generated](./media/image26.png)

自动生成图形用户界面、文本、应用程序、Word 描述

27. 在 **Name and describe your EDM sensitive info type** 页中，输入
    `Contoso Employee EDM` 作为名称。

28. 在 **Description for admins** 字段中，为员工个人信息输入
    `基于`` EDM ``的敏感信息类型``。`。选择 **Next。**

![Graphical user interface, text, application Description automatically
generated](./media/image27.png)

自动生成图形用户界面、文本、应用程序描述

29. 查看设置，然后选择 **Submit**。

![Graphical user interface, application Description automatically
generated](./media/image28.png)

图形用户界面，自动生成应用程序描述

30. 在 **Your EDM sensitive info type**页上，选择 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

自动生成的计算机 Description 的屏幕截图

31. 使用 Microsoft Purview 门户使浏览器保持打开状态。

您已成功创建新的基于 EDM
的分类敏感信息类型，用于从数据库文件源中识别员工数据。

## 练习 3 – 创建基于 EDM 的分类数据源

要将基于 EDM 的分类与包含敏感数据的数据库相关联，接下来需要通过 EDM
上传代理工具对敏感信息类型的实际数据进行哈希处理和上传。

1.  在 **Microsoft Edge** 中，导航到
    `https://go.microsoft.com/fwlink/?linkid=2088639` 以访问 EDM
    下载代理。

2.  选择 **Run**下载并安装该工具。

![BrokenImage](./media/image30.png)


3.  在 **Microsoft Exact Data Match Upload Agent Setup** 向导中，选择
    **Next**。

    - **选择 I accept the terms in the License Agreement，然后选择
      Next。**

    - 请勿更改默认的 **Destination Folder** 路径，然后选择 **Next**。

    - 选择 **Install** 以执行安装。

    - 当 **User Account Control** 窗口打开时，选择 **Yes**。

    - 如果要求登录，请通过 **Patti** 的帐户登录。

    - 安装完成后，选择 **Finish。**

    - 选择左下角的 Windows 符号打开开始菜单，输入**Notebook** 并选择
      **Notebook** 从开始菜单中。

    - 在记事本窗口的第一行中输入以下文本（确保在新行中输入以下所有三个文本。

&nbsp;

    Name,Birthdate,StreetAddress,EmployeeID
    Patti Fernandez,01.06.1980,1Main Street,CSO123456
    Christie Cline,31.01.1985,2Secondary Street,CSO654321

4.  选择 File （文件） 和 Save as： `EmployeeData.csv`

5.  选择**下拉列表 Save as type：**，然后选择 **All Files (.)**中。

6.  选择 Encoding： **的下拉列表**，然后选择 **UTF-8** 并选择 **Save**。

![BrokenImage](./media/image31.png)


7.  关闭记事本窗口。

8.  用鼠标右键选择任务栏中的 Windows 符号，然后选择 **Windows PowerShell
    （Admin）** 并以管理员身份运行。

![BrokenImage](./media/image32.png)


9.  当 **User Account Control** 窗口打开时，选择 **Yes**。

10. 导航到 EDM Upload Agent 目录：

`cd "C:\Program Files\Microsoft\``EdmUploadAgent``"`

![Text Description automatically generated](./media/image33.png)

Text Description automatically generated

11. 通过运行以下 cmdlet，使用您的帐户授权将数据库上传到您的租户：

`.\EdmUploadAgent.exe /Authorize`

![BrokenImage](./media/image34.png)


12. 当 **Pick an account （选择帐户**） 窗口显示时， 使用用户名
    PattiF@{TENANTPREFIX}.onmicrosoft.com` ``和资源选项卡上提供的用户密码以`` `**Patti
    Fernandez** 身份登录。

**注意**：对于后续步骤，请确保文件的路径与 VM
中的路径相似。它可能与说明或屏幕截图不同。在这种情况下，请在命令中相应地更改文件的路径。

13. 通过在 PowerShell 中运行以下脚本，下载基于 EDM
    的分类敏感信息类型的数据库架构定义

`.\EdmUploadAgent.exe /``SaveSchema`` /``DataStoreName`` ``employeedb`` /``OutputDir`` "C:\Users\Admin\Documents\"`

**注意**：如果最后一个命令失败，则可能需要更多时间才能应用
**EDM_DataUploaders** 组成员资格。可能需要长达一小时才能下载 Schema
文件。如果失败，请继续执行下一个任务，稍后返回此步骤。或者检查 VM 上
documents 文件夹的路径。

![BrokenImage](./media/image35.png)


> \`14.通过在PowerShell中运行以下脚本，对数据库文件进行哈希处理，并将其上传到基于
> EDM 的分类敏感信息类型：

`.\EdmUploadAgent.exe /``UploadData`` /``DataStoreName`` ``employeedb`` /``DataFile`` "C:\Users\Admin\Documents\EmployeeData.csv" /``HashLocation`` "C:\Users\Admin\Documents\" /Schema "C:\Users\Admin\Documents\employeedb.xml"`

![BrokenImage](./media/image36.png)


**注意：** 如果您收到以下错误

错误类型: System.IO.FileNotFoundException

错误消息：找不到指定的文件。

检查保存文件的路径EmployeeData.csv

![Text Description automatically generated](./media/image37.png)

自动生成文本描述

15. 检查上传进度，直到状态更改为 completed （已完成），然后运行以下
    PowerShell 命令：

`.\EdmUploadAgent.exe /``GetSession`` /``DataStoreName`` ``employeedb`

![BrokenImage](./media/image38.png)


您已成功对基于 EDM 的分类敏感信息类型进行哈希处理并上传数据库文件。

## 练习 4 – 创建关键字词典

当用户在同事报告病假后发送电子邮件时，发生了几起个人信息泄露违规行为。当这种情况发生时，生病或生病的原因就被发出来了。我们不希望这种情况发生。

1.  在 **Microsoft Edge** 中，打开一个 **New InPrivate Window**，导航到
    `https://purview.microsoft.com`，然后使用用户名
    PattiF@{TENANTPREFIX}.onmicrosoft.com 和资源选项卡上提供的用户密码以
    `Patti Fernandez` 身份登录。

2.  从左侧导航栏中，选择 **Solutions** \> **Data Loss Prevention**。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

自动生成的计算机 Description 的屏幕截图

3.  从左侧窗格中选择 **Classifiers。**从子导航窗格中选择 **Sensitive
    info types** 。选择 **+Create sensitive info type**
    以打开新敏感信息类型的向导。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

自动生成的计算机 Description 的屏幕截图

4.  在 **Name your sensitive info type**页上，输入以下内容:

    - 名字: `Contoso Diseases List`

    - 描述: `List of possible diseases of employees.`

![Graphical user interface, application, Teams Description automatically
generated](./media/image39.png)

自动生成图形用户界面、应用程序、Teams 描述

5.  选择 **Next**。

6.  在 **Define patterns for this sensitive info type**页上，选择 **+
    Create pattern**。

![Graphical user interface, application, Teams Description automatically
generated](./media/image40.png)

自动生成图形用户界面、应用程序、Teams 描述

7.  选择 **Primary element** 下的下拉字段 ，然后选择 **Keyword
    dictionary**。

![Graphical user interface, application Description automatically
generated](./media/image41.png)

图形用户界面，自动生成应用程序描述

8.  在 **Add a keyword dictionary** 页面中，输入名称
    `Diseases Dictionary`。

9.  在 **Keywords** 区域中，输入以下关键字，每个关键字都放在单独的行中

&nbsp;

    flu
    influenza
    cold
    bronchitis
    otitis

![BrokenImage](./media/image42.png)


10. 选择 **Done**。

11. 在 **Supporting elements下**，选择 **+ Add supporting elements or
    group of elements**下拉列表，然后选择 **keyword
    list**以添加对关键字词典的其他支持。

![Graphical user interface, application Description automatically
generated](./media/image43.png)

图形用户界面，自动生成应用程序描述

12. 在 **Add a keyword list**页中`，在 `ID 字段中输入 员工缺勤。在
    **Case insensitive**
    框中，输入以下关键字，每个关键字都放在单独的行中

&nbsp;

    employee
    absence
    reason

![Graphical user interface, application Description automatically
generated](./media/image44.png)

图形用户界面，自动生成应用程序描述

13.选择 **Done**。

14.在 **New pattern** 页面中，查看配置并选择 **Create**。

![Graphical user interface, application Description automatically
generated](./media/image45.png)

图形用户界面，自动生成应用程序描述

15. 在 **Define patterns for this sensitive info type**中，选择
    **Next**。

![Graphical user interface, application, Teams Description automatically
generated](./media/image46.png)

自动生成图形用户界面、应用程序、Teams 描述

16. 在 **Choose the recommended confidence level to show in compliance
    policies** 中，保留默认值，然后选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

自动生成的计算机 Description 的屏幕截图

17. 在 **Review settings and finish** 页面中，查看您的设置并选择
    **Create**。该过程完成后，选择 **Done**。

![BrokenImage](./media/image48.png)


18. 使 Microsoft Purview 门户中的浏览器窗口保持打开状态。

您已成功基于关键字字典创建新的敏感信息类型，并添加了更多关键字以降低误报率。继续执行下一个任务。

## 练习 5 – 使用自定义敏感信息类型

在策略中使用自定义敏感信息类型之前，应始终对其进行测试，否则可能会因自定义搜索模式故障而导致数据丢失或泄漏。

1.  选择左下角的 Windows
    符号打开开始菜单，输入**Notepad**并选择**Notepad**从开始菜单中。

2.  在记事本窗口中输入以下**Notepad**

`Employee Patti Fernandez EMP123456 is on absence because of the flu/influenza`

3.  选择 **File （文件** ） 和 Save As `SickTestData`` `，然后选择
    **Save**。

4.  关闭记事本窗口。

5.  在 **Microsoft Edge** 中，Microsoft Purview
    门户选项卡应仍处于打开状态。如果是这样，请选择它并继续下一步。如果您关闭了它，则在新选项卡中导航到
    `https://purview.microsoft.com`。 **使用用户名**
    PattiF@{TENANTPREFIX}.onmicrosoft.com` ``和资源选项卡上提供的用户密码以`` `**Patti
    Fernandez** 身份登录。

6.  在左侧导航窗格中，选择 **Solutions** \> **Data Loss
    Prevention**，然后在 **Classifiers** 下**Sensitive info
    types**。在右上角的 **Search （搜索**） 框中，输入 ***Contoso***
    并按 **Enter**。选择 **Contoso 员工 ID** 以打开右侧窗格。

![A screenshot of a computer Description automatically
generated](./media/image49.png)

自动生成的计算机 Description 的屏幕截图

7.  从 右侧窗格中选择 **Test**。

![A screenshot of a computer Description automatically
generated](./media/image50.png)

自动生成的计算机 Description 的屏幕截图

8.  在 **Upload file to test** 页面上，选择 **Upload file**。

![BrokenImage](./media/image51.png)


9.  从左侧窗格中选择 **Documents** ，选择名为 **SickTestData**
    的文件，然后选择 **Open**。

![Graphical user interface, text, application Description automatically
generated](./media/image52.png)

自动生成图形用户界面、文本、应用程序描述

10. 选择 **Test** 以开始分析。

![Graphical user interface, text, application Description automatically
generated](./media/image53.png)

自动生成图形用户界面、文本、应用程序描述

11. 在 **Match results** 页面上，查看找到的匹配项。

![BrokenImage](./media/image54.png)


12. 选择 **Finish** 并通过单击 **X** 按钮关闭测试页面 。

![Graphical user interface, text, application Description automatically
generated](./media/image55.png)

自动生成图形用户界面、文本、应用程序描述

13. 返回 **Data classification** 页，选择名为 **Contoso Diseases List**
    的 Sensitive Information Type。

14. 在右侧窗格中，选择 **Test**.

![BrokenImage](./media/image56.png)


15. 在 **Upload file to test** 页面上，选择 **Upload file**。

![BrokenImage](./media/image57.png)


16. 从左侧窗格中选择 **Documents**，选择名为 *SickTestData*
    的文件，然后选择 **Open**。

17. 选择 **Test** 以开始分析。

![Graphical user interface, text, application Description automatically
generated](./media/image58.png)

自动生成图形用户界面、文本、应用程序描述

18. 在 **Match results** 页面上，查看找到的匹配项。完成后，查看，选择
    **Finish**。

![Graphical user interface, application Description automatically
generated](./media/image59.png)

图形用户界面，自动生成应用程序描述

## 总结:

您已成功测试了两种自定义敏感信息类型，并验证了搜索模式可识别所需的模式。您已完成敏感信息类型的创建，可以继续进行下一个练习。
