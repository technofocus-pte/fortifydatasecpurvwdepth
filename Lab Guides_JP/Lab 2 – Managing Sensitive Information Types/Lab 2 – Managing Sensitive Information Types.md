**ラボ 2 – Sensitive Information Typesの管理**

**導入**

Contoso Ltd. では以前、チケット ソリューションでサポート チケットを処理する際に、従業員が顧客の個人情報を誤って送信してしまうという問題がありました。

今後のユーザー教育のため、メールや文書に含まれる従業員ID（大文字3文字と数字6桁）をSensitive Information Typesで識別するためのカスタムSensitive Information Typesが必要となります。誤検出率を下げるため、「Employee」と「ID」というキーワードを使用します。

**目的**

- 正規表現とキーワード リストを使用して、**カスタムのSensitive Information Types**を作成します。

- **EDM-based sensitive info type**を構成および定義します。

- **EDM アップロード エージェント**にアップロードします。

- 機密性の高い健康関連の用語を識別するために、**キーワード辞書ベースのSensitive Information Types**を構築します。

- カスタムのSensitive Info Typesをポリシーに適用する前に、その正確性をテストして検証します。

**演習1 – カスタムSensitive Information Typesの作成**

この演習では、**Security & Compliance Center PowerShell** モジュールを使用して、キーワード「Employee」および「ID」の近くにあるEmployee ID のパターンを認識する新しいカスタムSensitive Info Typesを作成します。

1.  Edge ブラウザーで InPrivate ウィンドウを開き、アドレス バーに次の URL を入力してMicrosoft Purview ポータルを開きます: https://purview.microsoft.com 。次に、ユーザー名**PattiF@TenantName**とリソース タブに指定されているユーザー パスワードを使用して**Patti Fernandez**としてログインします。

> <img src="media/image1.png" style="width:6.26806in;height:5.79306in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image2.png" style="width:6.26806in;height:5.8875in" alt="A screenshot of a login box AI-generated content may be incorrect." />

2.  **「Welcome to the new Microsoft Purview protal!** **」**ダイアログボックスが表示されたら、「**Get Started**」ボタンをクリックし**ます**。

> <img src="media/image3.png" style="width:6.26806in;height:6.53819in" />

3.  左側のナビゲーションから、 **\[Solutions\]** \> **\[Data Loss Prevention\]**を選択します。

> <img src="media/image4.png" style="width:6.26806in;height:3.40347in" />
>
> **注：**Solutionsリストに**Data Loss Preventionが**表示されない場合は、数分待ってからページを再度アップロードしてください。それでもSolutionsリストにData Loss Preventionが表示されない場合は、通常のブラウジングウィンドウを使用してログインしてください。

4.  左ペインから**「Classifiers」**を選択します。サブナビゲーションペインから**「Sensitive Info Types」**を選択します。 **「+Create Sensitive Info Types」**を選択して、新しいSensitive Info Typesを作成するためのウィザードを開きます。

> <img src="media/image5.png" style="width:6.26806in;height:3.53889in" alt="A screenshot of a computer Description automatically generated" />

5.  **「Name your sensitive info type」**ページで、次の情報を入力します。

    - **Name**: Contoso Employee IDs

    - **Description**: Pattern for Contoso employee IDs

6.  **「Next」**を選択します。

> <img src="media/image6.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

7.  **\[Define patterns for this sensitive info type\]**ページで、 **\[Create pattern\]**を選択します。

<img src="media/image7.png" style="width:6.26806in;height:3.53889in" alt="A screenshot of a computer Description automatically generated" />

8.  右側に表示される**\[New pattern\]**ペインで、 **\[Add primary element** **\]**を選択し、 **\[Regular expression\]**を選択します。

<img src="media/image8.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

9.  新しい右側のペイン**「Add a regular expression」**で、次のように入力します。

    - **ID** : Contoso ID

    - **Regular expression**: \s\\A-Z\\{3}\\0-9\\{6}\s

    - **String match**を選択

10. **\[Done\]**を選択します。

<img src="media/image9.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

11. \[New pattern\] ペインで、**Character proximity値**を***100***文字に減らします。

> <img src="media/image10.png" style="width:6.26806in;height:3.38056in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image11.png" style="width:6.26806in;height:3.4in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. **「Supporting elements」**見出しに移動し、 **「+ Add supporting elements or group of elements」**ドロップダウン メニューをクリックして、 **「Keywork list」**を選択します。

> <img src="media/image12.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

13. **\[Add a keyword list\]**ペインで、次のように入力します。

    - **ID**: Employee ID keywords

    - **Case insensitive**:Employee ID

> <img src="media/image13.png" style="width:6.26806in;height:3.34236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. **「Word match」の**横にあるラジオボタンを選択します。次に、 **「Done」**ボタンをクリックします。

> <img src="media/image14.png" style="width:6.26806in;height:3.40417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. 次に、**「Create」**ボタンをクリックします。

> <img src="media/image15.png" style="width:6.26806in;height:3.40139in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. **Define patterns for this sensitive info type** ページに戻り、 **\[Next\]**を選択します。

> <img src="media/image16.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application, Teams Description automatically generated" />

17. **\[Choose the recommended confidence level to show in compliance policies\]**ページで、既定値を使用して**\[Next\]**ボタンを選択します。

> <img src="media/image17.png" style="width:6.26806in;height:3.68889in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. **「Review settings and finish」**ページで設定を確認し、 **「Create」**を選択します。正常に作成されたら、 **「Done」**を選択します。

> <img src="media/image18.png" style="width:6.26806in;height:4.07847in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image19.png" style="width:6.26806in;height:3.56667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. ブラウザウィンドウを開いたままにしておきます。

100 文字の範囲内で 3 つの大文字、6 つの数字、およびキーワード「Employee」または「ID」のパターンでEmployee ID を識別するための新しいSensitive Info Typesを正常に作成しました。

**演習2 – EDMベースの分類情報タイプの作成**

追加の検索パターンとして、従業員データのデータベーススキーマを使用して、EDMベースの分類を作成します。データベースソースファイルは、従業員の以下のデータフィールド（名前、生年月日、住所、従業員ID）でフォーマットされます。

1.  「Solutions」をクリックし、 **「Data Loss Prevention」**を選択します**。**

> <img src="media/image20.png" style="width:6.26806in;height:3.44236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  **「Classifiers」**をクリックし、 **「EDM classifiers」**を選択します。EDM CLASSIFIERSページで、 **「New EDM experience」の**横にあるトグルボタンをクリックして**Off**にします。

> <img src="media/image21.png" style="width:6.26806in;height:3.38125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  次に、 **「Create** **EDM schema」をクリックします** <img src="media/image22.png" style="width:6.26806in;height:3.37222in" />

4.  **Name**フィールドにemployeedbと入力します。

5.  **Description**フィールドに「従業員データベーススキーマ」と入力します。**すべてのスキーマ フィールドの区切り文字と句読点を無視するの**チェックを外します。

> <img src="media/image23.png" style="width:6.26806in;height:3.33889in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image24.png" style="width:6.26806in;height:3.34306in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  最初のスキーマ フィールド名に「名前」と入力し、「**フィールドは検索可能です」**ボックスをオンにします。

> <img src="media/image25.png" style="width:6.26806in;height:3.40347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **\[無視する区切り文字と句読点を選択\]**のドロップダウンをクリックし、 **\[ハイフン\]** 、 **\[ピリオド\]** 、 \[**スペース\]** 、 **\[開き括弧\]** 、 **\[閉じ括弧\]**を選択します。

> <img src="media/image26.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

8.  下端から**+ スキーマ データ フィールドの追加を**選択します。

> <img src="media/image27.png" style="width:6.26806in;height:3.1875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **スキーマ フィールド名**で、**スキーマ フィールド \#2の下に**「生年月日」と入力します。

10. もう一度、下端から**「+ スキーマ データ フィールドの追加」**を選択します。

11. **スキーマ フィールド名**で、**スキーマ フィールド \#3の下に**StreetAddressと入力します。

12. 最後に、下端から**+ スキーマ データ フィールドの追加を**選択します。

13. **スキーマ フィールド名**で、**スキーマ フィールド \#4の下に**EmployeeIDと入力します。

14. 選択した**フィールドは検索可能です**。

15. **\[保存\]**を選択します。

> <img src="media/image28.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

16. 左側のペインから**EDM Sensitive Info Types**を選択し、 **+ EDM Sensitive Info Typesの作成を選択して、 EDM ルール パッケージウィザード**を開きます。

> <img src="media/image29.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. **\[データ ストア スキーマの定義\]ページ**で、 **\[既存の EDM スキーマを選択\]を選択します**。

> <img src="media/image30.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

18. **employeedb**を選択し、**追加を選択します**。

> <img src="media/image31.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application Description automatically generated" />

19. データ ストア スキーマを確認し、 **\[次へ\]を選択します**。

> <img src="media/image32.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

20. **この EDM Sensitive Info Typesのパターンの定義ページ**で、 **+ パターンの作成を選択します**。

> <img src="media/image33.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

21. 右側の \[**新しいパターン\]ペイン**の**\[プライマリ要素\]**フィールドで、 ***EmployeeIDを選択します***。

22. **プライマリ要素のSensitive Info Types**の下で、**Sensitive Info Typesを選択を選択します**。

> <img src="media/image34.png" style="width:6.26806in;height:7.41806in" alt="A screenshot of a pattern Description automatically generated" />

23. **検索**バーに「Contoso」と入力し、Enter キーを押します。

24. **Contoso 従業員 ID**を選択し、 **\[完了\]を選択します**。

25. **\[完了\]**を選択します。

> <img src="media/image35.png" style="width:6.26806in;height:7.41806in" alt="A screenshot of a computer Description automaticall generated" />

26. *この EDM Sensitive Information Typesのパターンを定義する画面*で**次へ**を選択します。

> <img src="media/image36.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application Description automatically generated" />

27. **推奨される信頼度レベルと文字の近接性を選択する**場合は、デフォルト値をそのままにして、 **\[次へ\]を選択します**。

> <img src="media/image37.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application, Word Description automatically generated" />

28. **EDM のSensitive Info Typesの名前と説明のページ**で、名前として「Contoso Employee EDM」と入力します。

29. **管理者向けの説明欄**に、従業員の個人情報のEDMベースのSensitive Info Typesを入力します。 **次。**

> <img src="media/image38.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, text, application Description automatically generated" />

30. 設定を確認して、 **\[送信\]を選択します**。

> <img src="media/image39.png" style="width:6.26806in;height:3.1875in" alt="Graphical user interface, application Description automatically generated" />

31. **EDM のSensitive Info Typesが作成されましたページ**で、 **\[完了\]を選択します**。

> <img src="media/image40.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

32. Microsoft Purview ポータルでブラウザを開いたままにしておきます。

データベース ファイル ソースから従業員データを識別するための新しい EDM ベースの分類Sensitive Information Typesが正常に作成されました。

**演習3 – EDMベースの分類データソースの作成**

EDM ベースの分類を機密データを含むデータベースに関連付けるには、次に、EDM UPLOAD AGENT ツールを使用してSensitive Information Typeの実際のデータをハッシュしてアップロードする必要があります。

1.  **Microsoft Edge**ブラウザーで、 https://go.microsoft.com/fwlink/? linkid=2088639 にアクセスして、EDM ダウンロード エージェントをダウンロードします。

2.  **Open file**リンクをクリックして、 **EdmUploadAgent.msi**にアクセスします。

> <img src="media/image41.png" style="width:6.26806in;height:3.61875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  **\[Welcome to the Microsoft Exact Data Match Upload Agent Setup Wizard** **\]**ダイアログ ボックスで、 **\[Next\]**ボタンをクリックします。

> <img src="media/image42.png" style="width:6.26806in;height:4.91111in" />

4.  **Microsoft Exact Data Match Upload Agent Setup** wizardで、 **\[Next\]**を選択します。

    - **\[I accept the terms in the License Agreement\]**を選択し、 **\[Next\]**を選択します。

    - **Destination Folder** のパスを変更せず、 **\[Next\]**を選択します。

    - **\[Install\]**を選択します。

    - **\[User Account Control\]**ウィンドウが開いたら、 **\[Yes\]**を選択します。

    - ログインを求められた場合は、 **Patti の**アカウントを使用してログインします。

    - インストールが完了したら、 **\[Finish\]**を選択します。

5.  次に、Windowsアイコンを右クリックし、ファイル名を指定して「**Run」**をクリックします**。「Run」**ダイアログボックスに「notepad」と入力し、 「**OK」**ボタンをクリックします。

> <img src="media/image43.png" style="width:6.26806in;height:5.38819in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image44.png" style="width:6.26806in;height:3.27778in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  メモ帳に次のテキストを入力します。

> Name,Birthdate,StreetAddress,EmployeeID
>
> Patti Fernandez,01.06.1980,1Main Street,CSO123456
>
> Christie Cline,31.01.1985,2Secondary Street,CSO654321
>
> <img src="media/image45.png" style="width:6.26806in;height:3.75972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Fileを選択し、EmployeeData.csv として保存します。

8.  **\[Save as type\]**のドロップダウンを選択し、 **\[All files\] (*.*)**を選択します。

9.  **Encoding**フィールドで、 **UTF-8**が選択されていることを確認し、 **\[Save\]**ボタンをクリックします。

> <img src="media/image46.png" style="width:6.26806in;height:3.92847in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Notepadウィンドウを閉じます。

11. タスクバーの**Windows**アイコンを右クリックし、 **「Windows PowerShell (Admin)」**を選択して管理者として実行します。

> <img src="media/image47.png" style="width:6.26806in;height:5.25764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. **「User Account Control」**ダイアログ **ボックス**で、 **「Yes」**ボタンをクリックします。

> <img src="media/image48.png" style="width:6.26806in;height:4.40764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. EDM Upload Agent ディレクトリに移動します。

> cd "C:\Program Files\Microsoft\\ EdmUploadAgent "
>
> <img src="media/image49.png" style="width:6.26806in;height:3.30625in" alt="Text Description automatically generated" />

14. 次のコマンドレットを実行して、アカウントでデータベースをテナントにアップロードすることを承認します。

> .\EdmUploadAgent.exe /承認
>
> <img src="media/image50.png" style="width:6.26806in;height:3.30625in" alt="A computer screen with a black screen AI-generated content may be incorrect." />

15. **\[Pick an account\]**ウィンドウが表示されたら、ユーザー名**PattiF@TenantName**とResourcesタブで指定したユーザー パスワードを使用して、 **Patti Fernandez**としてログインします。(またはリセットした新しいパスワード)

> <img src="media/image51.png" style="width:6.26806in;height:4.89583in" alt="A computer screen with a sign in box AI-generated content may be incorrect." />
>
> <img src="media/image52.png" style="width:6.26806in;height:4.35903in" alt="A screenshot of a login box AI-generated content may be incorrect." />

16. PowerShell で次のスクリプトを実行して、EDM ベースの分類Sensitive Information Typeのデータベース スキーマ定義をダウンロードします。

> .\EdmUploadAgent.exe /保存スキーマ/データストア名 従業員データベース/出力ディレクトリ"C:\Users\Admin\Documents\\
>
> **注**：最後のコマンドが失敗した場合、 **EDM_DataUploaders**グループのメンバーシップが適用されるまでさらに時間がかかる可能性があります。スキーマファイルのダウンロードが可能になるまで、最大1時間かかる場合があります。失敗した場合は、次のタスクに進み、後でこの手順に戻ってください。または、VM 上のドキュメントフォルダへのパスを確認してください。
>
> <img src="media/image53.png" style="width:6.26806in;height:3.31042in" alt="A computer screen with text on it AI-generated content may be incorrect." />

17. PowerShell で次のスクリプトを実行して、データベース ファイルをハッシュし、EDM ベースの分類Sensitive Information Typeにアップロードします。

.\EdmUploadAgent.exe /UploadData /DataStoreName employeedb /DataFile C:\Users\Admin\Documents\EmployeeData.csv /HashLocation "C:\Users\Admin\Documents\\ /Schema "C:\Users\Admin\Documents\employeedb.xml"

\![\](./media/image50.png)

\*\*Note:\*\* If you get the following errors

Error Type: System.IO.FileNotFoundException

Error Message: Unable to find the specified file.

\*\*Check the path where you saved the file EmployeeData.csv\*\*

\![Text Description automatically generated\](./media/image51.png)

19. 状態が完了に変わるまでアップロードの進行状況を確認し、次の PowerShell コマンドを実行します。

> .\EdmUploadAgent.exe /GetSession /DataStoreName employeedb
>
> <img src="media/image54.png" style="width:6.26806in;height:3.04931in" alt="A screenshot of a computer program AI-generated content may be incorrect." />

EDMベースの分類Sensitive Information Typeのデータベース ファイルをハッシュしてアップロードしました。

**演習4 – キーワード辞書の作成**

同僚が病欠を報告した後にユーザーがメールを送信した際に、個人情報漏洩の違反が複数発生しました。その際、病欠の理由が公表されていました。このような事態は絶対に避けなければなりません。

1.  **Microsoft Edge**で、**新しい InPrivate ウィンドウ**を開き**、** https://purview.microsoft.comに移動して、ユーザー名**PattiF@TenantName**とResourcesタブに指定されているユーザー パスワードを使用して**Patti Fernandez**としてログインします。

2.  左側のナビゲーションから、 **\[Solutions\]** \> **\[Data Loss Prevention\]**を選択します。

> <img src="media/image55.png" style="width:6.26806in;height:3.93819in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  左ペインから**「Classifiers」**を選択します。サブナビゲーションペインから**「Sensitive Info Types」**を選択します。 **「+Create Sensitive Info Types」**を選択して、新しいSensitive Info Typesを作成するためのウィザードを開きます。

> <img src="media/image56.png" style="width:6.26806in;height:3.17917in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  **「Name your sensitive info type」**ページで、次のように入力します。

    - Name: Contoso Diseases List

    - Description: List of possible diseases of employees.

> <img src="media/image57.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

5.  **「Next」**を選択します。

6.  **\[Define patterns for this sensitive info type\]**ページで、 **\[+Create pattern\]**を選択します。

> <img src="media/image58.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

7.  **Primary element** の下のドロップダウン フィールドを選択し、**Keyword dictionary**を選択します。

> <img src="media/image59.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

8.  **Add a keyword dictionary**ページで、名前として「 Diseases Dictionary \*」と入力します。

9.  **Keywords**領域に、次のキーワードをそれぞれ別の行に入力します。

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

10. **\[Done\]**を選択します。

11. **\[Supporting elements\]**の下で、 **\[+Add supporting elements or group of elements\]**ドロップダウンを選択し、**keyword list** を選択して、キーワード ディクショナリに追加のサポートを追加します。

> <img src="media/image61.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

12. **「Add a keyword list」**ページで、 **ID**フィールドに「Employee」と入力します。 **「Case insensitive」**ボックスに、以下のキーワードをそれぞれ1行ずつ入力し、 **「Done」**ボタンをクリックします。

> Employee ID
>
> leave
>
> reason
>
> <img src="media/image62.png" style="width:6.26806in;height:3.52431in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. **\[New pattern\]**ページで構成を確認し、 **\[Create\]**を選択します。

> <img src="media/image63.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application Description automatically generated" />

14. **Define patterns for this sensitive info type** で、 **\[Next\]**を選択します。

> <img src="media/image64.png" style="width:6.26806in;height:3.18333in" alt="Graphical user interface, application, Teams Description automatically generated" />

15. **Choose the recommended confidence level to show in compliance policies** では、既定値をそのままにして、 **\[Next\]**を選択します。

> <img src="media/image65.png" style="width:6.26806in;height:3.18333in" alt="A screenshot of a computer Description automatically generated" />

16. **「Review settings and finish」**ページで設定を確認し、 **「Create」**を選択します。プロセスが完了したら、 **「Done」**を選択します。

> <img src="media/image66.png" style="width:6.26806in;height:3.18333in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Microsoft Purview ポータルのブラウザ ウィンドウを開いたままにしておきます。

キーワード辞書に基づいて新しいSensitive Information Typeを作成し、誤検知率を下げるためのキーワードを追加しました。次のタスクに進んでください。

**演習 5 – カスタムのSensitive Information Typeの操作**

カスタムのSensitive Information Typeは、ポリシーで使用する前に必ずテストする必要があります。そうしないと、カスタム検索パターンの誤動作によりデータの損失や漏洩が発生する可能性があります。

1.  Windowsアイコンを右クリックし、「**Run」**をクリックします。「**Run**」ダイアログボックスに**「 +++notepad+++」**と入力し、 **「OK」**ボタンをクリックします。

> <img src="media/image43.png" style="width:6.26806in;height:5.38819in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image44.png" style="width:6.26806in;height:3.27778in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Notepadウィンドウに次のテキストを入力します。

> Employee Patti Fernandez with Employee ID ABC123456 is on leave because of the flu/influenza

3.  **\[File\]**を選択し、 \[SickTestDataとして保存\]を選択して**\[Save\]を選択します**。

4.  Notepadウィンドウを閉じます。

5.  **Microsoft Edge**では、Microsoft Purview ポータルのタブがまだ開いているはずです。開いている場合は、それを選択して次の手順に進みます。閉じてしまった場合は、新しいタブでhttps://purview.microsoft.comにアクセスします。ユーザー名**PattiF@TenantName**とResourcesタブに表示されているユーザーパスワードを使用して、 **Patti Fernandez**としてログインします。

6.  左側のナビゲーションペインで**「Solutions」** \> **「Data Loss Prevention」を選択し**、 **「Classifiers」**の下にある「**Sensitive Info Types」を選択します**。右上の**Search**ボックスに「Contoso」と入力し、Enterキーを押します。 **「Contoso Employee ID」をクリックして**右側のペインを開きます。

<img src="media/image67.png" style="width:6.26806in;height:3.38889in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  右側のペインから**「Test」**を選択します。

> <img src="media/image68.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

8.  **\[Upload file to test\]**ページで、 **\[Upload file\]**を選択します。

> <img src="media/image69.png" style="width:6.26806in;height:3.9125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **\[Documents\]**を選択し、 **SickTestData**という名前のファイルを選択して**\[Open\]**を選択します。

> <img src="media/image70.png" style="width:6.26806in;height:3.41806in" alt="Graphical user interface, text, application Description automatically generated" />

10. 分析を開始するには、 **「Test」**を選択します。

> <img src="media/image71.png" style="width:6.26806in;height:3.9125in" alt="Graphical user interface, text, application Description automatically generated" />

11. **「Match results」**ページで、見つかった一致を確認します。

> <img src="media/image72.png" style="width:6.26806in;height:3.40556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. **\[Finish\]**を選択し、 **\[X\]**ボタンをクリックしてテスト ページを閉じます。

> <img src="media/image73.png" style="width:6.26806in;height:3.37569in" alt="A screenshot of a search engine AI-generated content may be incorrect." />

13. **Data classification**ページに戻り、 **「Contoso Diseases List」**という名前のSensitive Info Typesを選択します。

14. 右側のペインで、 **\[Test\]**を選択します。

> <img src="media/image74.png" style="width:6.26806in;height:3.9125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. **\[Upload file to test\]**ページで、 **\[Upload file\]**を選択します。

> <img src="media/image75.png" style="width:6.26806in;height:3.9125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. **\[Documents\]**を選択し、 *SickTestData*という名前のファイルを選択して**\[Open\]**を選択します。

17. 分析を開始するには、**「Test」**を選択します。

> <img src="media/image76.png" style="width:6.26806in;height:3.9125in" alt="Graphical user interface, text, application Description automatically generated" />

18. **「Match results」**ページで、見つかった一致を確認します。確認が完了したら、**「Finish」**を選択します**。**

> <img src="media/image77.png" style="width:6.26806in;height:3.64306in" alt="Graphical user interface, text, application Description automatically generated" />

**まとめ：**

このラボでは、正規表現、キーワード辞書、および Exact Data Match (EDM) テクニックを使用して Microsoft Purview でカスタムのSensitive Information Type (SIT) を作成およびテストし、Data Loss Prevention機能を強化する方法を学習しました。
