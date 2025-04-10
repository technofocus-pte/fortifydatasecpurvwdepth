# 實驗 7 – 配置內部風險管理

## 目的:

在此實驗室中，我們將學習如何使用 Insider Risk Management 策略配置
Insider Risk Management。我們將使用我們在實驗室 2
中創建的敏感信息類型和我們在實驗室 5 中創建的 DLP
策略來創建策略，以保護組織免受有風險的瀏覽器使用或任何數據盜竊或泄漏的影響。

爲此，我們將在 Azure
中創建一個基礎結構，該基礎結構將代表組織中的設備。我們將瞭解如何在 Azure
AD 和 Intune 中載入這些設備，幷在其上安裝 MDM
代理，以便可以使用它們從這些計算機獲取警報。

## 練習 1：同步 VM 時鐘

1.  登錄到 VM 後，選擇 Windows 圖標。然後搜索 **Date and time，幷選擇
    Date and time settings** 。

![A screenshot of a computer Description automatically
generated](./media/image1.jpg)

自動生成的計算機 Description 的屏幕截圖

2.  在打開的 個人設置 屏幕上，單擊 **Sync now** 下 其他設置.

![A screenshot of a computer Description automatically
generated](./media/image2.jpg)

自動生成的計算機 Description 的屏幕截圖

3.  這負責同步時間，以防自動同步不起作用。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image3.png)

以中等置信度自動生成的計算機描述的屏幕截圖

## 練習 2：創建 Insider Risk Management 策略。

### 先决條件

#### 步驟 1 - 將用戶添加到預覽體驗成員風險管理角色組

1.  如果 Microsoft Purview 門戶已打開，請繼續執行步驟 2，否則，請打開
    `https://purview.microsoft.com` 幷使用 **MOD
    Administrator**憑據登錄。

![](./media/image4.png)

2.  在導航中，選擇 **Settings**，然後選擇 **Role groups**，在 **Role
    groups下**，選擇 **Insider Risk Management**。然後選擇
    **Edit**。在側窗格中，再次選擇 **Edit**

![](./media/image5.png)

3.  在 **Edit Members of the role group** 頁面上，選擇 **Choose
    users**。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

自動生成的計算機 Description 的屏幕截圖

4.  選中 **MOD Admin、Patti、Megan 和 Alex** 附近的複選框。然後選擇
    **Select** 。

![](./media/image7.png)

5.  然後選擇 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

自動生成的計算機 Description 的屏幕截圖

6.  選擇 **Save** 將用戶添加到角色組。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

自動生成的計算機 Description 的屏幕截圖

7.  選擇 **Done** 以完成這些步驟。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

自動生成的計算機 Description 的屏幕截圖

#### 步驟 2 - 啓用內部風險分析見解

1.  在 Microsoft Purview 門戶中。導航到 ** Settings**，轉到 **nsider
    risk management**。轉到 **Analytics**，啓用單選按鈕，然後單擊
    **Save**。

![](./media/image11.png)

#### 第 3 步 – 載入設備

在此部署方案中，你將載入尚未載入的設備，幷且你只想檢測 Windows 10
設備上的內部風險活動。

我們需要在 Microsoft Entra ID
中注册我們的設備/VM，作爲創建任何內部風險策略的先决條件。

1.  在 VM 上打開 Windows **Setting **。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

自動生成的計算機 Description 的屏幕截圖

2.  轉到 **Accounts \> Access work or school**。在 **Access** **work or
    school** 頁面上，單擊 **Connect**。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

自動生成的計算機 Description 的屏幕截圖

3.  在**Set up a work or school account** 提示中，單擊 **Join this
    device to Microsoft Entra ID。**

![](./media/image14.png)

4.  在登錄提示中，使用 實驗室環境的 resources 選項卡上提供的 **MOD**
    **Administrator** 憑證登錄。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

自動生成的計算機 Description 的屏幕截圖

![Graphical user interface, application, PowerPoint Description
automatically generated](./media/image16.png)

自動生成圖形用戶界面、應用程序、PowerPoint 描述

5.  在 提示 **Make sure This is your organization** 中按 **Join** 。

![Graphical user interface, text, application Description automatically
generated](./media/image17.png)

自動生成圖形用戶界面、文本、應用程序描述

6.  完成後，您將看到一個確認窗口**：ou're all setup！**。點擊**Done**。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

自動生成的計算機 Description 的屏幕截圖

7.  再次轉到 **accounts \> Access work or school**。在 **Access work or
    school** 頁面上，單擊 **Connect**。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

自動生成的計算機 Description 的屏幕截圖

8.  在 **Set up a work or school account** 提示中，使用 **MOD**
    **Administrator** 憑據登錄。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

自動生成的計算機 Description 的屏幕截圖

9.  在 **Setting up your device** 頁面上，選擇 **Got it** 。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

自動生成的計算機 Description 的屏幕截圖

10. 現在轉到 **windows settings \> Accounts \> Access work or school \>
    Connected to Contoso MDM \> Info \> Sync**。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

自動生成的計算機 Description 的屏幕截圖

![A screenshot of a computer Description automatically
generated](./media/image22.png)

自動生成的計算機 Description 的屏幕截圖

11. 單擊 VM 上的 Windows 符號。選擇用戶 **Admin** 幷選擇 **Sign out**。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

自動生成的計算機 Description 的屏幕截圖

12. 在用戶屏幕上，選擇 **Other user**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image24.png)

以中等置信度自動生成的計算機描述的屏幕截圖

13. 輸入實驗室環境主頁上提供的 O365 憑據，然後以 **MOD
    Administrator**身份登錄 VM。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image25.png)

以中等置信度自動生成的計算機描述的屏幕截圖

14. 關閉 Windows 設置應用程序。 ` ``在`` ` 實驗室 VM 上使用 **MOD
    Administrator** 帳戶登錄 https://purview.microsoft.com。

15. 選擇 **Settings \> Device onboarding \> Devices**。

![](./media/image26.png)

16. 單擊 **Turn on Device onboarding**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

自動生成的計算機 Description 的屏幕截圖

17. 從 **Settings \> Device onboarding \> Onboarding**。單擊 **Download
    package**。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

自動生成的計算機 Description 的屏幕截圖

18. 右鍵單擊文件幷 **Extract all ...** 。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image29.png)

以中等置信度自動生成的計算機描述的屏幕截圖

![A screenshot of a computer Description automatically
generated](./media/image30.png)

自動生成的計算機 Description 的屏幕截圖

19. 完成後，打開文件夾幷使用**Administrator**權限運行文件。

![A computer screen with a computer screen Description automatically
generated](./media/image31.png)

帶有計算機屏幕的計算機屏幕自動生成的描述

20. 單擊 **More info**。

![Graphical user interface, application Description automatically
generated](./media/image32.png)

圖形用戶界面，自動生成應用程序描述

21. 單擊 **Run anyway**。

![A screenshot of a computer error Description automatically
generated](./media/image33.png)

自動生成的計算機錯誤描述的屏幕截圖

22. 在命令提示符中，按 **Y** 鍵幷按 Enter 鍵確認幷在出現提示時繼續。

![A screenshot of a computer error Description automatically
generated](./media/image34.png)

自動生成的計算機錯誤描述的屏幕截圖

23. 您將收到一條消息，指出設備已載入。在命令提示符中收到消息後，**Press
    any key to continue…**，按任意鍵。

24. 關閉命令提示符後，在管理員模式下打開命令提示符以運行檢測測試，然後在提示符下複製幷運行以下命令。命令提示符窗口將自動關閉。

`powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'`

![Text Description automatically generated](./media/image35.png)

自動生成文本描述

25. 通過單擊導航中的設置**打開 settings**，然後選擇 **Devices
    Onboarding** \> **Devices**。

**注意：**雖然啓用設備載入通常需要大約 60 秒，但請最多等待 30 分鐘。

26. 您將能够檢查 **Devices**
    列表。在您載入設備之前，該列表將爲空，完成後，您將能够看到您的 VM
    列爲已載入的設備。

### 任務 1：創建組織範圍的策略以檢測風險瀏覽器使用情况幷對其進行評分

#### 步驟 1 – 創建新策略

1.  如果您在上一個任務中關閉了瀏覽器窗口，請打開
    `https://purview.microsoft.com` 幷使用管理員憑證登錄。

2.  轉到 **Insider Risk Management** 幷選擇 **Policies** 選項卡。選擇
    **Create policy** 以打開策略嚮導。

![](./media/image36.png)

3.  在 **Choose a policy template **頁面上，在 **Choose a policy
    template **下**選擇  Risky browser usage (preview)**。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

自動生成的計算機 Description 的屏幕截圖

4.  確保滿足所有先决條件。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

自動生成的計算機 Description 的屏幕截圖

5.  選擇 **Next ** 繼續。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

自動生成的計算機 Description 的屏幕截圖

6.  在 **Name and description** 頁面上，填寫以下字段:

    - 姓名 （必填）：`Risky usage of browser`

    - 描述（可選）：`This is a test policy for the risky browser usage.`

7.  選擇 ** Next** 繼續。

![Graphical user interface, text, application Description automatically
generated](./media/image40.png)

自動生成圖形用戶界面、文本、應用程序描述

8.  在**Choose users, groups, & adaptive scopes **頁面上，選擇 **All
    users, groups, & adaptive scopes**。選擇 **Next** 繼續。

9.  在 **Exclude users and groups** 頁上，選擇 **Next**。

10. 在 **Decide whether to prioritize** 頁面上，選擇 **I don't want to
    specify priority content right
    now**（創建策略後，您將能够執行此作）。選擇 Next 繼續。

![Graphical user interface, text, application Description automatically
generated](./media/image41.png)

自動生成圖形用戶界面、文本、應用程序描述

11. 在  **Triggers for this policy** 頁上，選擇 **Turn on indicators**。

![A screenshot of a computer Description automatically
generated](./media/image42.png)

自動生成的計算機 Description 的屏幕截圖

12. 在 **Choose indicators to turn on上**，選擇**Select all under Risky
    browsing indicators (preview)下的“全選”**，然後取消選中其餘框。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

自動生成的計算機 Description 的屏幕截圖

13. 向下滾動幷選擇 **Save**。

14. 在 **Triggers for this policy 的 Select** **which activities will
    trigger this policy 下。** 選擇所有選項，然後單擊** Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image44.png)

自動生成圖形用戶界面、文本、應用程序描述

15. 在 **Triggering thresholds for this policy**頁上，選擇**Use custom
    thresholds (Recommended)**，將所有閾值更改爲每天 **1**
    個，然後選擇 **Next**。

![Graphical user interface, application Description automatically
generated](./media/image45.png)

圖形用戶界面，自動生成應用程序描述

![A screenshot of a computer Description automatically
generated](./media/image46.png)

自動生成的計算機 Description 的屏幕截圖

16. 在 **indicators** 頁面上，選擇 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

自動生成的計算機 Description 的屏幕截圖

17. 在 ** Decide whether to use default or custom indicator
    thresholds上**，選擇 ** Use default thresholds for all
    indicators**，然後選擇 ** Next**。

![Graphical user interface, text, application Description automatically
generated](./media/image48.png)

自動生成圖形用戶界面、文本、應用程序描述

18. 在 **Review settings and finish上**，選擇 **Submit**。

![Graphical user interface, text, application Description automatically
generated](./media/image49.png)

自動生成圖形用戶界面、文本、應用程序描述

19. 在 **Your policy was created** 上，選擇 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image50.png)

自動生成的計算機 Description 的屏幕截圖

20. 保持選項卡打開幷繼續執行下一個任務。

#### 步驟 2 - 對策略進行評分

1.  單擊名爲 **Risky usage of browser** 的新策略。選擇 **Start scoring
    activity for users**。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

自動生成的計算機 Description 的屏幕截圖

2.  在 **Add users to multiple policies** 窗格的 **Reason** 字段中，鍵入
    **Testing the policy**。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

自動生成的計算機 Description 的屏幕截圖

3.  在 **This should last for （choose between 5 to 30 days）**
    字段中，選擇 **10** 天。

4.  使用 **Search user to add to policies** 字段。添加 **MOD
    Admin**。然後單擊 **Start scoring activity**。

5.  確認您已開始 **Scoring activity for 1 users** 後，單擊 **Close**。

6.  ![A screenshot of a computer screen Description automatically
    generated with medium confidence](./media/image53.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

### 任務 2：離職用戶竊取數據

#### 步驟 1 – 創建新策略

1.  如果您在上一個任務中關閉了瀏覽器窗口，請打開
    `https://purview.microsoft.com` 幷使用管理員憑證登錄。

2.  轉到 **Insider Risk Management** 幷選擇 **Policies** 選項卡。選擇
    **Create policy**以打開策略嚮導。

![](./media/image36.png)

3.  在 Choose a policy template 頁面上，在 Data theft 下選擇 Data theft
    by deleaveing users。選擇 下一步 繼續。

![A screenshot of a computer Description automatically
generated](./media/image54.png)

自動生成的計算機 Description 的屏幕截圖

4.  在 **Name and description** 頁面上，填寫以下字段:

    - 姓名 （必填）：`Data theft by a user`

    - 描述（可選）：`This is a test policy for the preventing data theft.`

5.  選擇 ** Next** 繼續。

![A screenshot of a computer Description automatically
generated](./media/image55.png)

自動生成的計算機 Description 的屏幕截圖

6.  在**Choose users, groups, & adaptive scopes **頁面上，選擇** All
    users, groups, & adaptive scopes**。選擇 **Next ** 繼續。

7.  在 **Exclude users, groups, & adaptive scopes**頁面上，選擇
    **Next**。

8.  在 **Decide whether to prioritize （决定是否確定優先級**）
    頁面上，選擇 **I want to specify priority content
    （我想指定優先內容**）。選中 **Sensitivity labels **和 **ensitive
    info types 的複選框**。選擇 **Next** 繼續。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image56.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

9.  在 ** Sensitivity labels to prioritize**頁上，選擇 ** Add or edit
    sensitivity labels**。在浮出控件窗格中，選擇 ** Internal/Employee
    data (HR) **，然後單擊“** Add**。然後單擊 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

10. 在  **Sensitive info types to prioritize**頁上，選擇“ **Add or edit
    sensitive info types**。在浮出控件窗格中，**Credit Card
    Number**, **Contoso Employee ID** 和 **Contoso Employee EDM**。選擇
    **Add**。然後單擊 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

自動生成的計算機 Description 的屏幕截圖

11. 在 **Decide whether to only activity with priority content**
    上，選擇 **Get alerts for all activity**。選擇 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

12. 在此策略頁的觸發器上，選擇默認值，然後選擇 下一步。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image60.png)

以中等置信度自動生成的計算機描述的屏幕截圖

13. 在 **Indicators** 頁面上，從提示中選擇 **Turn on indicators**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image61.png)

以中等置信度自動生成的計算機描述的屏幕截圖

14. 在 **Select all under Office indicators ，**然後單擊 **Save**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image62.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

15. 選擇所有選項，然後單擊 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

自動生成的計算機 Description 的屏幕截圖

16. 在 **Detection options**頁面上，選擇默認值，然後選擇 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

自動生成的計算機 Description 的屏幕截圖

17. 在** indicators **頁面上，選擇**Next**。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

自動生成的計算機 Description 的屏幕截圖

18. 在 ** Decide whether to use default or custom indicator
    thresholds上**，選擇 ** Customise thresholds**，爲每個階段分別使用
    **1**、**2** 和 **3** 個事件，然後選擇 Next。

![A screenshot of a computer screen Description automatically
generated](./media/image65.png)

自動生成的計算機屏幕描述的屏幕截圖

19. 在 **Review settings and finish 上**，選擇 **Submit** 。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

自動生成的計算機 Description 的屏幕截圖

20. 在 **Your policy was created** 上，選擇 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

自動生成的計算機 Description 的屏幕截圖

21. 保持選項卡打開幷繼續執行下一個任務。

#### 步驟 2 - 對策略進行評分

1.  單擊名爲 **Data theft by a user** 的新策略。選擇 **Start scoring
    activity for users**。

![A screenshot of a computer Description automatically
generated](./media/image68.png)

自動生成的計算機 Description 的屏幕截圖

2.  在 **Add users to multiple policies 窗格的 Reason 字段中**，鍵入
    **Testing the policy**。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

自動生成的計算機 Description 的屏幕截圖

3.  在 **This should last for （choose between 5 to 30 days）**
    字段中，選擇 **10** 天。

4.  使用 **Search user to add to policies** 字段。添加 **MOD
    Admin**。然後單擊 **Start scoring activity**。

5.  確認您已開始 **Scoring activity for 1 users** 後，單擊 **Close**。

![A screenshot of a computer Description automatically
generated](./media/image69.png)

自動生成的計算機 Description 的屏幕截圖

### 任務 3：用戶數據泄露

#### 步驟 1 – 創建新策略

1.  如果您在上一個任務中關閉了瀏覽器窗口，請打開
    `https://purview.microsoft.com` 幷使用管理員憑證登錄。

2.  轉到 **Insider Risk Management** 幷選擇 **Policies** 選項卡。選擇
    **Create policy** 以打開策略嚮導。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

自動生成的計算機 Description 的屏幕截圖

3.  在 **Choose a policy template** 頁面上，在 **Data leaks**下選擇
    **Data leaks** 。選擇 **Next** 繼續。

![A screenshot of a computer Description automatically
generated](./media/image70.png)

自動生成的計算機 Description 的屏幕截圖

4.  在 **Name and description** 頁面上，填寫以下字段:

    - 姓名 （必填）：`Data leaks by a user`

    - 描述（可選）：`This is a test policy for preventing data leaks.`

5.  選擇 **Next** 繼續。

![A screenshot of a computer Description automatically
generated](./media/image71.png)

自動生成的計算機 Description 的屏幕截圖

6.  在 **Choose users and groups**頁面上，選擇 **Include all users and
    groups**。選擇 **Next** 繼續。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

自動生成的計算機 Description 的屏幕截圖

7.  在 **Exclude users and groups**頁上，選擇 **Next**。

8.  在 **Decide whether to prioritize** 頁面上，選擇 **I want to specify
    priority content**。選中 **SharePoint
    網站**、**敏感度標簽**和**敏感信息類型的複選框**。選擇 **下一步**
    繼續。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image73.png)

以中等置信度自動生成的計算機描述的屏幕截圖

9.  在 **SharePoint sites to prioritize** 頁面上，選擇 **Add or edit
    SharePoint sites**。在彈出窗格中，選擇
    `https://{TENANTPREFIX}.sharepoint.com/sites/ContosoWeb1` 幷選擇
    **Add**。然後單擊 **Next**。

10. 在 **Sensitivity labels to prioritize** 頁上，選擇 ** Add or edit
    sensitivity labels.**。在浮出控件窗格中，選擇 ** Internal/Employee
    data (HR) **，然後單擊 **Add** 。然後單擊 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

11. 在 **Sensitive info types to prioritize **頁上，選擇** Add or edit
    sensitive info types**。在浮出控件窗格中，搜索幷選擇 **Credit Card
    Number**, **Contoso Employee ID** 和 **Contoso Employee EDM**。選擇
    **Add**。然後單擊 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

自動生成的計算機 Description 的屏幕截圖

12. 在 **Decide whether to only activity with priority content**
    上，選擇 **Get alerts for all activity** 。選擇 **Next**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

13. 在 ** Triggers for this policy** 頁上，選擇 **User performs an
    exfiltration activity** 附近的“單選按鈕”。在
    “選擇將觸發此策略的活動” 下，選擇所有可用選項，尤其是 **Download
    content from SharePoint**。然後選擇 Next 。

![A screenshot of a computer Description automatically
generated](./media/image74.png)

自動生成的計算機 Description 的屏幕截圖

14. 在 **Triggering thresholds for this policy** 上，選擇 **Use custom
    thresholds**。將每個閾值設置爲 **1**，然後選擇 **Next**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image75.png)

以中等置信度自動生成的計算機描述的屏幕截圖

15. 在 **Indicators** 頁面上選擇默認設置**，** 然後選擇 **Next**。

16. 在 ** Decide whether to use default or custom indicator thresholds**
    上，選擇 ** Customise thresholds**，爲每個階段分別使用 **1**、**2**
    和 **3** 個事件，然後選擇 **Next**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image76.png)

以中等置信度自動生成的計算機描述的屏幕截圖

17. 在 **Review settings and finish 上**，選擇 **Submit**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image77.png)

以中等置信度自動生成的計算機描述的屏幕截圖

18. 在 **Your policy was created** 上，選擇 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image78.png)

自動生成的計算機 Description 的屏幕截圖

19. 保持選項卡打開幷繼續執行下一個任務。

#### 步驟 2 - 對策略進行評分

1.  單擊名爲 **Data leaks by a user** 的新策略。選擇 **Start scoring
    activity for users**。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image79.png)

以中等置信度自動生成的計算機描述的屏幕截圖

2.  在 **Reason field in the Add users to multiple
    policies**窗格 中，鍵入 Testing the policy。在 **This should last
    for （choose between 5 to 30 days）** 字段中，選擇 **10** 天。使用
    **Search user to add to policies** 字段。添加 **MOD
    Admin**。然後單擊 **Start scoring activity**。

3.  確認您已開始 **Scoring activity for 1 個用戶**後，單擊 **Close**.

您已成功創建 Insider 風險管理策略。

## 總結：

在此實驗室中，我們探索了從端到端設置 Insider Risk
Management。使用您自己的訂閱和許可證，您還可以使用此實驗室指南創建一個
Azure 設置，該設置還可用于爲 Insider Risk
管理策略創建各種警報（包括發送包含受限數據的電子郵件，這無法通過試用訂閱實現），您可以使用這些策略來探索
Purview 上的自適應保護功能。
