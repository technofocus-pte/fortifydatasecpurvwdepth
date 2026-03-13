**實驗室 2 – 管理敏感信息類型​**

**介紹**

Contoso 有限公司此前曾遇到員工在工單支持工單處理時意外發送客戶個人信息的問題。

為了未來教育用戶，需要自定義敏感信息類型來識別電子郵件和文檔中的員工ID，這些文件由三個大寫字符和六個數字組成，使用敏感信息類型。為降低誤報率，將使用關鍵詞“員工”和“ID”。

**目標**

- 使用正則表達式和關鍵詞列表**創建**  **custom sensitive information type**。

- 利用結構化員工數據**配置並定義  EDM-based sensitive info type**。

- 將員工數據哈希並上傳到  **EDM Upload Agent** 進行分類。

- 構建**基於 keyword dictionary-based sensitive info type **，以識別機密的健康相關術語。

- 在應用到政策之前，測試並驗證自定義敏感信息類型的準確性。

**練習 1 – 創建自定義敏感信息類型**

在本練習中，您將使用 **Security & Compliance Center PowerShell** 模塊創建一種新的自定義敏感信息類型，識別“Employee”和“ID”關鍵字附近的員工ID模式。

1.  在你的 Edge 瀏覽器中打開一個 InPrivate 窗口，在地址欄輸入以下 URL，打開 Microssoft Purview 門戶：https://purview.microsoft.com，然後 **用**資源標簽頁上的用戶名 **PattiF@TenantName** **和用**戶密碼登錄為 **Patti Fernandez。**

> <img src="media/image1.png" style="width:6.26806in;height:5.79306in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image2.png" style="width:6.26806in;height:5.8875in" alt="A screenshot of a login box AI-generated content may be incorrect." />

2.  如果  **Welcome to the new Microsoft Purview protal!** 對話框出現, 然後點擊**“開始**使用”按鈕

> <img src="media/image3.png" style="width:6.26806in;height:6.53819in" />

3.  從左側導航中選擇**Solutions** \> **Data Loss Prevention**.

> <img src="media/image4.png" style="width:6.26806in;height:3.40347in" />
>
> **注釋**: 如果你在解決方案列表中沒有看到 ** Data Loss Prevention**，請等待幾分鐘後重新上傳頁面。如果解決方案列表中仍然沒有看到數據丟失防止，請使用普通（正常）瀏覽窗口登錄。

4.  從左側面板選擇 **Classifiers **。 **在子導航面板中**選擇 **Sensitive info types**。選擇 **+ Create sensitive info type** 以打開新的敏感信息類型嚮導。

> <img src="media/image5.png" style="width:6.26806in;height:3.53889in" alt="A screenshot of a computer Description automatically generated" />

5.  在 **Name your sensitive info type** 頁面, enter the following information:

    - **名字**: Contoso Employee IDs

    - **描述**: Pattern for Contoso employee IDs

6.  選擇 **Next**.

> <img src="media/image6.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

7.  在 **Define patterns for this sensitive info type** 頁面, 選擇 **Create pattern**.

<img src="media/image7.png" style="width:6.26806in;height:3.53889in" alt="A screenshot of a computer Description automatically generated" />

8.  在 **New pattern** 右側的面板，選擇 **Add primary element** 並選擇 **Regular expression**.

<img src="media/image8.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

9.  在新的右側面板中 **Add a regular expression**, 請加入以下內容：

    - **ID**: Contoso IDs

    - **Regular expression**: \s\\A-Z\\{3}\\0-9\\{6}\s

    - Select **String match**

10. 選擇 **Done**.

<img src="media/image9.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

11. 在新模式面板中，減少**Character proximity** value to ***100*** characters.

> <img src="media/image10.png" style="width:6.26806in;height:3.38056in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image11.png" style="width:6.26806in;height:3.4in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. 導航至 **Supporting elements**  標題, 點擊**+ Add supporting elements or group of elements** 下拉菜單並選擇 **Keyword list**.

> <img src="media/image12.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

13. 在**Add a keyword list** 窗口, 請加入以下內容：

    - **ID**: Employee ID keywords

    - **Case insensitive**:Employee ID

> <img src="media/image13.png" style="width:6.26806in;height:3.34236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. 向下滾動，選擇  **Word match** 旁邊的單選按鈕。 然後，點擊**“Done**”按鈕。

> <img src="media/image14.png" style="width:6.26806in;height:3.40417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. 現在，點擊 **“Create **”按鈕。

> <img src="media/image15.png" style="width:6.26806in;height:3.40139in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. 在 **Define patterns for this sensitive info type** 頁面選擇 **Next**.

> <img src="media/image16.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application, Teams Description automatically generated" />

17. 在 **Choose the recommended confidence level to show in compliance policies**頁面, 使用默認值，然後選擇**“下一步”按鈕。**

> <img src="media/image17.png" style="width:6.26806in;height:3.68889in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. 在 **Review settings and finish** 頁面查看設置並選擇**創建**。 成功創建後選擇**完成**。

> <img src="media/image18.png" style="width:6.26806in;height:4.07847in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image19.png" style="width:6.26806in;height:3.56667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. 保持瀏覽器窗口開啟.

您已成功創建一種新的敏感信息類型，用於識別員工ID，採用三個大寫字符、六個數字以及100字符範圍內的關鍵詞“Employee”或“IDS”。

**練習 2 – 創建基於 EDM 的分類信息類型**

作為額外的搜索模式，你將創建一個基於EDM的分類，並建立一個員工數據的數據庫模式。數據庫源文件將採用以下員工數據字段格式：姓名、出生日期、街道地址和員工ID。

1.  點擊“解決方案”，然後選擇 **Data Loss Prevention**

> <img src="media/image20.png" style="width:6.26806in;height:3.44236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  點擊 **“Classifiers**”，然後選擇**EDM分類器**。在EDM分類器頁面，點擊**新 New EDM experience**即可 **Off**

> <img src="media/image21.png" style="width:6.26806in;height:3.38125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  然後點擊 **Create** **EDM schema**

> <img src="media/image22.png" style="width:6.26806in;height:3.37222in" />

4.  在 **Name** 字段, 輸入 employeedb.

5.  在 **Description** 字段, 輸入 Employee Database schema.. 取消勾選**Ignore delimiters and punctuation for all schema fields**.

> <img src="media/image23.png" style="width:6.26806in;height:3.33889in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image24.png" style="width:6.26806in;height:3.34306in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  在第一個模式字段名稱中輸入名稱，標記 **Field is searchable **框。

> <img src="media/image25.png" style="width:6.26806in;height:3.40347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  點擊下拉菜單 **Choose delimiters and punctuation to ignore** 並 **Hyphen**, **Period**, **Space**, **Open parenthesis** 和 **Close parenthesis**.

> <img src="media/image26.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

8.  選擇 **+ Add schema data field** 從較低的部分開始。

> <img src="media/image27.png" style="width:6.26806in;height:3.1875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  在 **Schema field name**, **Schema field \#2** 下, 輸入 Birthdate.

10. 選擇 **+ Add schema data field** 又是低價。

11. 在**模式字段名稱中**, **Schema field \#3 下**, 輸入 StreetAddress.

12. 選擇 **+ Add schema data field** 最後一次從低端。

13. 在**Schema field name**, **Schema field \#4 下**, 輸入 EmployeeID.

14. 選擇 **Field is searchable**.

15. 選擇 **Save**.

> <img src="media/image28.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

16. 從左側窗格選擇 **EDM sensitive info types**類型，然後選擇**+  Create EDM sensitive info type **以打開**EDM rule package** 嚮導。

> <img src="media/image29.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. **在Define data store schema** 頁面, 選擇 **Choose an existing EDM schema**.

> <img src="media/image30.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

18. 選擇 **employeedb** 並選擇 **Add**.

> <img src="media/image31.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application Description automatically generated" />

19. 查看數據存儲模式並選擇**Next**.

> <img src="media/image32.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

20. 在 **Define patterns for this EDM sensitive info type** 頁面, 選擇 **+ Create pattern**.

> <img src="media/image33.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

21. 在 **New pattern** 右側的玻璃, 在 **Primary element** 字段, 選擇 ***EmployeeID***.

22. 在**Primary element's sensitive info type 下**, 選擇 **Choose sensitive info type**.

> <img src="media/image34.png" style="width:6.26806in;height:7.41806in" alt="A screenshot of a pattern Description automatically generated" />

23. 在 **搜索**欄, 輸入 Contoso 然後按下回車鍵。

24. 選擇 **Contoso Employee IDs** 並選擇**Done**.

25. 選擇 **Done**.

> <img src="media/image35.png" style="width:6.26806in;height:7.41806in" alt="A screenshot of a computer Description automaticall generated" />

26. 在**“**定義圖案”界面中選擇下一步，用於此EDM敏感信息類型界面。

> <img src="media/image36.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application Description automatically generated" />

27. 在 **Choose the recommended confidence level and character proximity** 讓默認值保持不變，然後選擇**“下一步**”。

> <img src="media/image37.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application, Word Description automatically generated" />

28. 在 **Name and describe your EDM sensitive info type** 頁面, 輸入 Contoso Employee EDM for the name.

29. 在 **Description for admins** 字段, 輸入 EDM-based sensitive information type for employee personal information.選擇 **Next.**

> <img src="media/image38.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application Description automatically generated" />

30. 檢查設置並選擇**Submit**.

> <img src="media/image39.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

31. 在 **Your EDM sensitive info type was created** 頁面, 選擇 **Done**.

> <img src="media/image40.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

32. 保持瀏覽器打開，打開Microsoft Purview門戶。

您已成功創建了一種基於EDM的新分類敏感信息類型，用於識別數據庫文件源中的員工數據。

**練習 3 – 創建基於 EDM 的分類數據源**

要將基於EDM的分類與包含敏感數據的數據庫關聯，接下來需要通過EDM上傳代理工具對敏感信息類型的實際數據進行哈希和上傳。

1.  在 **Microsoft Edge** 瀏覽器, 導航到 https://go.microsoft.com/fwlink/?linkid=2088639 以下載EDM下載代理。

2.  點擊 **Open file** 訪問鏈接 **EdmUploadAgent.msi**

> <img src="media/image41.png" style="width:6.26806in;height:3.61875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  在 **Welcome to the Microsoft Exact Data Match Upload Agent Setup Wizard** 對話框，點擊**“下一步**”按鈕。

> <img src="media/image42.png" style="width:6.26806in;height:4.91111in" />

4.  在 **Microsoft Exact Data Match Upload Agent Setup** 巫師, 選擇 **Next**.

    - 選擇 **I accept the terms in the License Agreement** 並選擇 **Next**.

    - 不要更改默認**的目標文件夾**路徑並選擇**“下一步**”。

    - 選擇**安裝**以執行安裝。

    - 當**用戶賬戶控制**窗口打開時，選擇**“是**”。

    - 如果被要求登錄，請通過**Patti**的賬戶登錄。

    - 安裝完成後，選擇**完成**。

5.  現在，右鍵點擊Windows圖標，導航並點擊**“運行**”。在**“運行**”對話框中，輸入“記事本”，然後點擊**確定**按鈕。

> <img src="media/image43.png" style="width:6.26806in;height:5.38819in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image44.png" style="width:6.26806in;height:3.27778in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  在記事本中輸入以下文字：

> Name,Birthdate,StreetAddress,EmployeeID
>
> Patti Fernandez,01.06.1980,1Main Street,CSO123456
>
> Christie Cline,31.01.1985,2Secondary Street,CSO654321
>
> <img src="media/image45.png" style="width:6.26806in;height:3.75972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  選擇文件並另存為：EmployeeData.csv

8.  選擇“**Save as type**”**下的拉菜單** ，然後選擇**“所有文件”（*。*）。**

9.  在**編碼**字段中，確保選擇**了UTF-8**，然後點擊**保存**按鈕。

> <img src="media/image46.png" style="width:6.26806in;height:3.92847in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. 關閉記事本窗口。

11. 右鍵點擊 任務欄上的 **Windows** 圖標，選擇 **Windows PowerShell（管理員）**以管理員身份運行。

> <img src="media/image47.png" style="width:6.26806in;height:5.25764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. 在 **User Account Control** 對話框，點擊**“Yes ”**按鈕。

> <img src="media/image48.png" style="width:6.26806in;height:4.40764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. 導航至EDM上傳代理目錄：

> cd "C:\Program Files\Microsoft\EdmUploadAgent"
>
> <img src="media/image49.png" style="width:6.26806in;height:3.30625in" alt="Text Description automatically generated" />

14. 通過運行以下命令，使用您的賬戶授權將數據庫上傳到租戶:

> .\EdmUploadAgent.exe /Authorize
>
> <img src="media/image50.png" style="width:6.26806in;height:3.30625in" alt="A computer screen with a black screen AI-generated content may be incorrect." />

15. 當**顯示“Pick an account**” 窗口時，請 **用用戶**名**PattiF@TenantName和**資源標簽頁上給出的用戶密碼登錄**Patti Fernandez。（或者用你重置的新密碼。）**

> <img src="media/image51.png" style="width:6.26806in;height:4.89583in" alt="A computer screen with a sign in box AI-generated content may be incorrect." />
>
> <img src="media/image52.png" style="width:6.26806in;height:4.35903in" alt="A screenshot of a login box AI-generated content may be incorrect." />

16. 通過在PowerShell中運行以下腳本，下載基於EDM的分類敏感信息類型的數據庫模式定義：

> .\EdmUploadAgent.exe /SaveSchema /DataStoreName employeedb /OutputDir "C:\Users\Admin\Documents\\
>
> **注釋**: 如果最後一個命令失敗，可能需要更多時間才能應用**EDM_DataUploaders**組成員身份。下載schema文件可能需要長達一小時。如果失敗，繼續下一個任務，稍後再回到這一步。或者檢查虛擬機裡的路徑文件文件夾。
>
> <img src="media/image53.png" style="width:6.26806in;height:3.31042in" alt="A computer screen with text on it AI-generated content may be incorrect." />

17. 通過在PowerShell中運行以下腳本，對數據庫文件進行哈希並上傳到基於EDM的分類敏感信息類型:

.\EdmUploadAgent.exe /UploadData /DataStoreName employeedb /DataFile C:\Users\Admin\Documents\EmployeeData.csv /HashLocation "C:\Users\Admin\Documents\\ /Schema "C:\Users\Admin\Documents\employeedb.xml"

\![\](./media/image50.png)

\*\*Note:\*\* If you get the following errors

Error Type: System.IO.FileNotFoundException

Error Message: Unable to find the specified file.

\*\*Check the path where you saved the file EmployeeData.csv\*\*

\![Text Description automatically generated\](./media/image51.png)

19. 檢查上傳進度直到狀態變成完成，然後執行以下PowerShell命令:

> .\EdmUploadAgent.exe /GetSession /DataStoreName employeedb
>
> <img src="media/image54.png" style="width:6.26806in;height:3.04931in" alt="A screenshot of a computer program AI-generated content may be incorrect." />

你已經成功哈希並上傳了一個基於EDM的分類敏感信息類型的數據庫文件.

**練習 4 – 創建關鍵詞詞典**

多起個人信息洩露事件發生在同事報告病假後用戶發送郵件。當這種情況發生時，疾病或疾病的原因會被傳達出來。我們不希望這種情況發生。

1.  在 **Microsoft Edge**, 開 **New InPrivate Window**, 導航到 https://purview.microsoft.com 登錄時為 **Patti Fernandez** 使用用戶名 **PattiF@TenantName** 和資源標簽頁上給出的用戶密碼。

2.  從左側導航中選擇**Solutions** \> **Data Loss Prevention**.

> <img src="media/image55.png" style="width:6.26806in;height:3.93819in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  從左側面板選擇 **Classifiers **。在子導航面板中 **Sensitive info types**。選擇 **+Create sensitive info type**以打開新的敏感信息類型嚮導。

> <img src="media/image56.png" style="width:6.26806in;height:3.17917in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  在**Name your sensitive info type** 頁面, enter the following:

    1.  名字: Contoso Diseases List

    2.  描述: List of possible diseases of employees.

> <img src="media/image57.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

5.  選擇 **Next**.

6.  在 **Define patterns for this sensitive info type** 頁面, 選擇 **+ Create pattern**.

> <img src="media/image58.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

7.  選擇下方下拉字段 **Primary element** 並選擇 **Keyword dictionary**.

> <img src="media/image59.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

8.  在 **Add a keyword dictionary** 頁面，請輸入姓名 Diseases Dictionary\*.

9.  在 **Keywords** 區域將以下關鍵詞輸入，分別在一行中：

> flu
>
> influenza
>
> cold
>
> bronchitis
>
> otitis
>
> <img src="media/image60.png" style="width:6.26806in;height:3.18333in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. 選擇 **Done**.

11. 在 **“ Supporting elements” 下方**，選擇**“+Add supporting elements or group of elements**，選擇**keyword list **以增加對關鍵詞詞典的額外支持。

> <img src="media/image61.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

12. 在**添加關鍵詞列表**頁面的ID欄輸入**“員工**”。在大小**寫不敏感**的框中，輸入以下關鍵詞，分別在一行中，然後點擊**“完成**”按鈕：

> Employee ID
>
> leave
>
> reason
>
> <img src="media/image62.png" style="width:6.26806in;height:3.52431in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. 在 **New pattern** 頁面, 查看配置並選擇**創建**。

> <img src="media/image63.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

14. 在 **Define patterns for this sensitive info type** 選擇 **Next**.

> <img src="media/image64.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

15. 在 **Choose the recommended confidence level to show in compliance policies** 讓默認值保持不變並選擇**Next**.

> <img src="media/image65.png" style="width:6.26806in;height:3.18333in" alt="A screenshot of a computer Description automatically generated" />

16. 在 **Review settings and finish** 頁面，查看你的設置並選擇**“創建**”。流程完成後選擇**“完成**”。

> <img src="media/image66.png" style="width:6.26806in;height:3.18333in" alt="A screenshot of a computer AI-generated content may be incorrect." />

1.  保持 Microsoft Purview 門戶中的瀏覽器窗口開啟。

你已經成功基於關鍵詞詞典創建了一個新的敏感信息類型，並添加了更多關鍵詞以降低誤報率。繼續下一個任務。

**練習 5 – Working with custom Sensitive Information Types**

自定義敏感信息類型在策略中使用前應始終進行測試，否則由於自定義搜索模式故障，可能導致數據丟失或洩露。

1.  右鍵點擊Windows圖標，導航並點擊**“運行**”。 在**“運行**”對話框中，輸入 +++notepad+++，然後點擊**確定**按鈕。

> <img src="media/image43.png" style="width:6.26806in;height:5.38819in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image44.png" style="width:6.26806in;height:3.27778in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  在記事本窗口輸入以下文字：

> Employee Patti Fernandez with Employee ID ABC123456 is on leave because of the flu/influenza

3.  選擇 **File** 以及《拯救AsSickTestData 然後選擇**保存**。

4.  關閉記事本窗口。

5.  在 **Microsoft Edge**, Microsoft Purview 門戶標簽頁應該仍然開著。如果有，選擇它並進入下一步。如果你關閉了它，然後在新標簽頁裡進入 https://purview.microsoft.com。**使用資源標簽頁上的用戶名**PattiF@TenantName**和用**戶密碼登錄為 Patti Fernandez。

6.  在左側導航面板中選擇“ **Solutions** \> **Data Loss Prevention**，然後在**分類器**中**選擇敏感信息類型**。在**搜索**框中，右上角輸入Contoso並按回車。點擊**Contoso員工IDS**打開右側面板。

<img src="media/image67.png" style="width:6.26806in;height:3.38889in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  從右側面板**選擇**測試。

> <img src="media/image68.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

8.  在 **Upload file to test** 頁面, 選擇 **Upload file**.

> <img src="media/image69.png" style="width:6.26806in;height:3.9125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  從左側窗格選擇**“文檔**”，選擇名為 **SickTestData** 的文件，然後選擇**“打開**”。

> <img src="media/image70.png" style="width:6.26806in;height:3.41806in" alt="Graphical user interface, text, application Description automatically generated" />

10. 選擇**測試**開始分析。

> <img src="media/image71.png" style="width:6.26806in;height:3.9125in" alt="Graphical user interface, text, application Description automatically generated" />

11. 在**匹配結果**頁面，查看找到的匹配。

> <img src="media/image72.png" style="width:6.26806in;height:3.40556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. 選擇**完成**，然後點擊X鍵關閉測試頁面 。

> <img src="media/image73.png" style="width:6.26806in;height:3.37569in" alt="A screenshot of a search engine AI-generated content may be incorrect." />

13. 回到**數據分類**頁面，選擇名為**“Contoso Diseases List”的敏感信息類型**。

14. 在右側面板中，選擇測試。

> <img src="media/image74.png" style="width:6.26806in;height:3.9125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. 在“**Upload file to test** ”頁面，選擇**“上傳  Upload file**”。

> <img src="media/image75.png" style="width:6.26806in;height:3.9125in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> 16． 從左側窗格選擇**“Documents **”，選擇名為 *SickTestData* 的文件，然後選擇**“打開**”。

17. 選擇 **Test **開始分析。

> <img src="media/image76.png" style="width:6.26806in;height:3.9125in" alt="Graphical user interface, text, application Description automatically generated" />

18. 在**匹配結果**頁面，查看找到的匹配。審核完成後，選擇**“結束**”。

> <img src="media/image77.png" style="width:6.26806in;height:3.64306in" alt="Graphical user interface, text, application Description automatically generated" />

**總結:**

在本實驗室中，你學習了如何在Microsoft Purview中創建和測試自定義敏感信息類型（SITE），使用正則表達式、關鍵詞詞典和精確數據匹配（EDM）技術，以增強數據丟失防護能力。
