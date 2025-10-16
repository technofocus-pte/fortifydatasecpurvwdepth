# **ラボ4 – Sensitivity Labelsの操作**

## 導入

このラボでは、Contoso Ltd のシステム管理者である Patti Fernandez
の役割を担います。組織はドイツのRednitzhembachに拠点を置き、組織のInformation
Protectionポリシーの一環として、人事部門のすべての従業員ドキュメントにSensitivity
Labelsが付けられていることを確認するための機密性計画を現在実装しています。

**目的**

- Microsoft 365 および SharePoint でSensitivity
  Labelsのサポートを有効にします。

- 保護設定を使用して、Sensitivity
  Labelsとサブラベルを作成して公開します。

- Microsoft 365 アプリ (Word、Outlook、OneDrive) にSensitivity
  Labelsを適用します。

- Sensitive Information
  Typesに基づいて自動ラベル付けポリシーを構成およびテストします。

## 演習1 – Sensitivity Labelsのサポートを有効にする

MSOnlineモジュールと SharePoint Online PowerShell
モジュールをインストールし、テナント上でSensitivity
Labelsのサポートを有効にします。

1.  Windowsアイコンを右クリックし、 **Windows
    PowerShell（Admin）に移動してクリックします。** 

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image1.png)

2.  **「User Account Control」ダイアログ ボックス**で、
    **「Yes」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image2.png)

3.  最新の Microsoft Online PowerShell モジュール
    バージョンをインストールするには、次のコマンドレットを入力します。

    **+++ Install-Module -Name MSOnline +++**

    ![A screenshot of a computer Description automatically generated](./media/image3.png)

4.  **You are installing the modules from an untrusted
    repository...というメッセージが表示され**たら、
    **Y**と入力してEnterボタンを押します。

    ![BrokenImage](./media/image4.png)

5.  最新の SharePoint Online PowerShell モジュール
    バージョンをインストールするには、次のコマンドレットを入力します。

    **+++Install-Module -NameMicrosoft.Online.SharePoint.PowerShell+++**

    ![A screenshot of a computer Description automatically generated](./media/image5.png)

6.  **You are installing the modules from an untrusted repository...
    message...というメッセージが表示され**たら、
    **Yと入力し**てEnterボタンを押します。

    ![A screenshot of a computer screen Description automatically generated](./media/image6.png)

7.  Microsoft Online
    サービスに接続するには、次のコマンドレットを入力します。

    **+++ Connect-MsolService +++**

    ![BrokenImage](./media/image7.png)

8.  **\[Sign in to your account\]
    フォーム**で、ユーザー名**PattiF@WWLxXXXXXX.onmicrosoft.com**とリソース
    タブに指定されているユーザー パスワードを使用して、 **Patti
    Fernandez**としてログインします。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image8.png)

    ![A screenshot of a computer program AI-generated content may be incorrect.](./media/image9.png)

9.  ドメインを取得するには、次のコマンドレットを入力します。

    **+++\\domain = get-msoldomain +++**

    ![BrokenImage](./media/image10.png)

10. SharePoint 管理者 URL
    を作成するには、次のコマンドレットを入力します。

**+++\\adminurl = "https://" +\\ domain.Name.split ( '.')\[ 0\]
+"-admin.sharepoint.com"+++**

    ![A screenshot of a computer screen Description automatically generated](./media/image11.png)

11. SharePoint Online
    管理センターにサインインするには、次のコマンドレットを入力します。

**+++ Connect-SPOService -url \\adminurl +++**

    ![A screenshot of a computer screen Description automatically generated](./media/image12.png)

12. **「Sign in to your account」フォーム**で、ラボ環境のリソース
    タブで提供されている資格情報を使用して**MOD
    Administrator**としてログインします。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image13.png)

13. Sensitivity
    Labelsのサポートを有効にするには、次のコマンドレットを入力します。

**+++ Set-SPOTenant -EnableAIPIntegration $true +++**

    ![BrokenImage](./media/image14.png)

14. **Y (はい)**で変更を確認し、Enter キーを押します。

    ![BrokenImage](./media/image15.png)

15. **PowerShellウィンドウ**を閉じます。

Teams および SharePoint サイトでのSensitivity
Labelsのサポートが正常に有効になりました。

## 演習2 – Sensitivity Labelsの作成

このタスクでは、人事部から人事従業員のドキュメントに適用するSensitivity
Labelsの要求を受けました。社内ドキュメント用のSensitivity
Labelsと人事部用のサブラベルを作成します。

1.  **Microsoft Edge**ブラウザのプライベートウィンドウで、 **+++**
    https://purview.microsoft.com **+++にアクセスし、 Patti
    Fernandez**としてログインします。ユーザー名**PattiF@WWLxXXXXXX.onmicrosoft.com**と、リソース
    タブに指定されたユーザー パスワード。

2.  Microsoft Purview ポータルの左側のナビゲーション ウィンドウで、
    **\[Solutions\]** \> **\[Information Protection\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image16.png)

3.  サブナビゲーションから、 **\[Sensitivity Labels\]** \> **\[create
    Lables\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image17.png)

4.  New **Sensitivity Labels**ウィザードが起動します。**Label
    details**ページで、管理者向けの**Name**、**Description for
    admins**と**Description for usersに**以下の情報を入力します。

    - Name: **+++Internal+++**

    - Display name: **+++Internal+++**

    - Description for users: **+++ Internal sensitivity label +++**

    - Description for admins: **+++ Internal sensitivity
      label for Contoso +++**

      ![A screenshot of a computer AI-generated content may be incorrect.](./media/image18.png)

5.  **「Next」**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image19.png)

6.  **「Define the scope for this label」ページ**で、 **「Files & other
    data
    assets」**のチェックボックスが選択されていることを確認します。次に、
    **「Meetings」のチェックボックスをオフにして、
    「Next」ボタン**をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image20.png)

7.  **\[Choose protection settings for the types of items you
    selected」ページ**で、 **「Next」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image21.png)

8.  ファイルとメールの**Auto-labelingページ**で、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

9.  **\[Define protection settings for groups and sites\]ページ**で、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

10. **「Review your settings and finish」ページ**で、 **「Create
    label」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image24.png)

11. **「Your sensitivity label was created」ページ**で、 **「Don’t
    create a policy yet」**のラジオボタンを選択します。
    **「Done」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image25.png)

12. **Information Protection**ページで、
    **「Internal」**ラベルに移動し、縦の省略記号を選択します。

13. 次に、 **「Create sublabel」**に移動してクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

14. New **Sensitivity Labels**ウィザードが起動します。**Label
    details**ページで、以下の情報を入力してください。

    - Name: **+++Employee data (HR) +++**

    - Display name: **+++Employee data (HR) +++**

    - Description for users: **+++This HR
      label is the default label for all specified documents in the
      HR Department. +++**

    - Description for admins: **+++This label is created in
      consultation with Ms.Jones (Head of HR department). Contact her,
      when you want to change settings of the label. +++**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image27.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image28.png)

15. **\[Define the scope for this
    label** **\]ページ**で、\[ファイルとその他のデータ資産\]、\[電子メール\]、\[会議\]
    のチェックボックスが選択されていることを確認し、
    **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image29.png)

16. **「Choose protection settings for labeled items」ページ**で、
    **「Control Access」**オプションを選択します。
    **「Next」**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image30.png)

17. **\[Access control\]ページ**で、 **\[Configure access control
    settings\] が**選択されていることを確認します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image31.png)

18. 暗号化設定に次の情報を入力します。

    - Assign permissions now or let users decide?: **Assign permissions
      now**

    - User access to content expires: **Never**

    - Allow offline access: **Only for a number of days**

    - Users have offline access to the content for this many
      days: **15**

    - ![A screenshot of a computer AI-generated content may be incorrect.](./media/image32.png)

19. **\[Assign permissions\]**リンクを選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image33.png)

20. **\[Assign permissions\]ペイン**で、**\[+ Add any authenticated
    users\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image34.png)

21. **\[Save\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image35.png)

22. **\[Access control\]ページ**で、 **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image36.png)

23. **\[Auto-labeling for files and emails**\]**ページ**で、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image37.png)

24. **\[Define protection settings for groups and sites\]ページ**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image38.png)

25. **\[Review your settings and finish\]ページ**で、 **\[Create
    Label\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image39.png)

26. **Your sensitivity label was createdページ**で、 **\[Don’t create a
    policy yet\]** ラジオ ボタンを選択し、
    **\[Done\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image40.png)

組織の内部ポリシーのSensitivity Labelsと人事 (HR)
部門の機密サブラベルが正常に作成されました。

## 演習3 – Sensitivity Labelsの公開

ここで、内部および HR のSensitivity
Labelsを公開し、公開されたSensitivity Labelsを HR ユーザーが HR
ドキュメントに適用できるようにします。

1.  **Microsoft
    Edge**で**+++https://purview.microsoft.com+++**に移動し、ユーザー名**PattiF@WWLxXXXXXX.onmicrosoft.com**とリソース
    タブに指定されているユーザー パスワードを使用して**Patti
    Fernandez**としてログインします。

2.  Microsoft Purview ポータルの左側のナビゲーション ウィンドウで、
    **\[Solutions\]** \> **\[Information Protection\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image41.png)

3.  サブナビゲーションから、 **\[Sensitivity Labels\]** \> **\[Publish
    Labels\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image42.png)

4.  Sensitivity Labelsの公開ウィザードが起動します。

5.  **\[Choose sensitivity labels to publish\]ページ**で、\[**Choose
    sensitivity labels to publish\]**リンクを選択します。

    ![A screenshot of a computer Description automatically generated](./media/image43.png)

6.  右側に「**Sensitivity Labels to
    publish」**というサイドバーが表示されます。

7.  **「Internal」**および**「Internal/Employee Data
    (HR)」**のチェックボックスをオンにします。 **「Add」**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image44.png)

8.  **\[Choose sensitivity labels to publish\]ページ**で、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image45.png)

9.  管理ユニットの割り当てページで、 **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image46.png)

10. **\[Publish to users and groups\]**ページで、 **\[Users and
    groups\]**チェックボックスが選択されていることを確認し、
    **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image47.png)

11. **\[Policy settings\]**ページで、 **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image48.png)

12. **\[Apply a default label to documents\]**ページで、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image49.png)

13. **\[Apply a default label to emails\]**ページで、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image50.png)

14. **Default settings for meetings and calendar events**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image51.png)

15. **Default settings for Fabric and Power BI content ページ**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image52.png)

16. **「Name your policy」ページ**で次の情報を入力し、
    **「Next」**ボタンをクリックします。

    - **Name**: **+++Internal HR employee data+++**

    - **Enter a description for your sensitivity label
      policy**: **+++This HR label is to be applied to internal HR
      employee data. +++**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image53.png)

17. **\[Review and finish\]ページ**で、 **\[Submit\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image54.png)

18. ポリシーが作成され、完了すると「**New policy
    created」**というメッセージが表示されます。

19. **Done and proceed to next task without closing the
    window**を選択し**ます**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image55.png)

社内および人事のSensitivity
Labelsの公開に成功しました。変更がすべてのユーザーとサービスに反映されるまで、最大24時間かかる場合がありますのでご注意ください。

## 演習4 – Sensitivity Labelsの操作

このタスクでは、Word および Outlook のメールにSensitivity
Labelsを作成します。作成されたドキュメントは OneDrive
に保存され、人事担当者にメールで送信されます。

1.  **+++https://portal.office.com+++**に移動し、 **Patti
    Fernandez**としてログインします。

2.  場合によっては、 **「Copilot everywhere you need it」**ダイアログ
    ボックスが表示されるので、それを閉じます。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image56.png)

3.  次に、左側のナビゲーション メニューで**\[Apps\]をクリックし、
    \[Word\]**をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image57.png)

4.  **「Welcome, Patti Fernandez! 」ページ**で、 **「Create blank
    document」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image58.png)

5.  **Your privacy options**のメッセージが表示されたら、
    **\[Close\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image59.png)

6.  Word 文書に次の内容を入力します。

**+++ Important HR employee document.+++**

7.  次に、上部のペインから**「Sensitivity」**を選択してドロップダウン
    メニューを開き、 **「Internal」**に移動してクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image60.png)

観察:**社内の緊急事態**、機密情報の選択**- 財務**および情報 8. ✅

8.  ラベルを適用するには、 **「Employee data (HR)」**をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image61.png)

**注**：この演習のタスク1で実行したスクリプトにより、テナントのWordでSensitivity
Labelsが有効化されました。Microsoft Word
Onlineで有効化が反映されるまでに1時間かかる場合があります。WordにSensitivity
Labelsメニューが表示されない場合は、後でこのラボに戻るか、この演習のタスク1を正しく完了していることを確認してください。

9.  ウィンドウの左上にある「**Document –
    Saved**」を選択し、ファイル名として**「HR
    Document」と入力してEnter**キーを押します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image62.png)

10. Wordタブを閉じます。M365 Copilot – アプリページで、
    **Outlook**をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image63.png)

11. **「Your privacy matters」**ダイアログボックスが表示された場合は、
    **「Continue」**ボタンをクリックします。

    ![A screen shot of a computer AI-generated content may be incorrect.](./media/image64.png)

12. Web 上の Outlook で、ウィンドウの左上から**\[New
    message\]を選択します。**

    ![A screenshot of a computer Description automatically generated](./media/image65.png)

13. **\[To\] フィールド**に名前**「Adele」を入力し**、ドロップダウン
    リストから**Adele Vanceを選択します。**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image66.png)

14. 件名欄に、 **「 +++Employee data for HR+++ 」と入力します**。

15. メール本文に次のメッセージを挿入します。

  **+++Dear Ms. Adele,**

  **Please find attached the important HR employee document.**

  **Kind regards,**

  **Patti Fernandez+++**

    ![A screenshot of a computer Description automatically generated](./media/image67.png)

16. 下部のメニューから**ペーパークリップの記号**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image68.png)

17. ドキュメントを添付するには、 **「Sugested attachments」**の下の**HR
    Document.docx**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image69.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image70.png)

18. ドキュメントが添付された電子メールメッセージを送信するには、**\[Send\]**を選択します。

19. ブラウザウィンドウを開いたままにしておきます。

Sensitivity
Labels付きの人事Word文書を作成し、OneDriveに保存しました。その後、この文書を人事担当者にメールで送信しましたが、その担当者のメールアドレスにもSensitivity
Labelsが設定されていました。

試用アカウントでは、メールを送信することはできますが、メールが返送され、現在のテナントの受信者に届かないことに注意してください。

## 演習5 – 自動ラベル付けの設定

**European General Data Protection Regulation
(GPDR)**に関連する情報が含まれていることが判明したドキュメントと電子メールに自動的にラベルを付ける**Sensitivity
Labels**を作成します。

1.  **Microsoft Edge**では、Microsoft Purview ポータル
    タブが開いたままになります。

2.  ポータルには**Patti Fernandez**としてログインする必要があります。

3.  「**Information Protection**」の下にある「**Sensitivity
    Labels**」に移動し、「**Internal**」ラベルの横にあるチェックボックスをオンにして、縦の省略記号をクリックします。「+**Create
    sublabel**」をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image71.png)

4.  New **Sensitivity Labels**ウィザードが起動します。**Label
    detailsで** ページで、次の情報を入力します。

    - Name: **+++GDPR Germany+++**

    - Display name: **+++GDPR Germany+++**

    - Description for users: **+++This document or email contains data
      related to the European General Data
      Protection Regulation(GPDR) for the region Germany. +++**

    - Description for admins: **+++This label is auto applied
      to German GDPR documents. +++**

5.  **「Next」**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image72.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image73.png)

6.  **\[Define the scope for this label\]**ページで、 **\[Files & other
    data assets\]、\[Emails\]** 、
    **\[Meetings\]のチェックボックスが選択されていることを確認し、
    \[Next\]ボタン**をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image74.png)

7.  **\[Choose protection settings for the types of items you
    selected\]ページ**で、 **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image75.png)

8.  **\[Auto-labeling for files and emails\] ページ**で、
    **\[Auto-labeling for files and emails\]**のトグルをオンにします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image76.png)

9.  **\[Detect content that matches these conditions\] セクション**で、
    **\[+Add condition\]を選択し**、 **\[Content
    contains\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image77.png)

10. **\[Content contains**\]
    セクションで\[テキスト**の\[Add\]**を選択し、 **\[Sensitive
    Information Types\]** を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image78.png)

11. 右側に**Sensitive Information Types**パネルが表示されます。

12. **「Search for Sensitive Information
    Types」検索パネル**で、次の情報を入力します。

**+++German+++**

13. Enterボタンを押すと、ドイツに関連するSensitive Information
    Typesが表示されます。すべてのSensitive Information
    Typesを選択するには、
    **「Name」**の横にあるチェックボックスをオンにしてください**。**

    ![BrokenImage](./media/image79.png)

14. **\[Add\]**を選択します。

    ![BrokenImage](./media/image80.png)

15. **「Next」**を選択します。

    ![A screenshot of a computer Description automatically generated](./media/image81.png)

16. **\[Define protection settings for groups and sites\]**ページで、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image82.png)

17. **\[Review your settings and finish\]ページ**で、 **\[Create
    label\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image83.png)

18. **「Your sensitivity label was created」ページ**で、
    **「Automatically apply label to sensitive content」**ラジオ
    ボタンを選択し、 **「Done」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image84.png)

19. サブナビゲーションから、 **\[Sensitivity Labels\]** \> **\[Publish
    Labels\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image85.png)

20. **Publish sensitivity labels wizard**が起動します。

21. **\[Choose sensitivity labels to publish\]ページ**で、\[**Choose
    sensitivity labels to publish\]**リンクを選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image86.png)

22. 右側に「**Sensitivity labels to
    publish**」パネルが表示されます。「**Internal**」と「**Internal/GDPR
    Germany**」のチェックボックスをオンにし、「**Add**」ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image87.png)

23. **\[Choose sensitivity labels to publish\]ページ**で、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image88.png)

24. 管理ユニットの割り当てページで、
    **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image89.png)

25. **\[Publish to users and groups\]**ページで、
    **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image90.png)

26. **\[Policy settings\]ページ**で、 **\[Next\]**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image91.png)

27. **\[Apply a default label to documents\]ページ**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image92.png)

28. **\[Apply a default label to emails\]ページ**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image93.png)

29. **Default settings for meetings and calendar events**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image94.png)

30. **Default settings for Fabric and Power BI contentページ**で、
    **\[Next\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image95.png)

31. **「Name your policy」ページ**で、次の情報を入力します。

    - Name: **+++GDPR Germany policy+++**

    - Enter a description for your sensitivity label
      policy: **+++This auto apply sensitivity labels policy is for the
      GDPR region of Germany. +++**

32. **「Next」**を選択します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image96.png)

33. **\[Review and finish\]ページ**で、 **\[Submit\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image97.png)

34. **\[New policy created\]ページ**で、
    **\[Done\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image98.png)

## まとめ

このラボでは、Contoso Ltd. のシステム管理者である Patti Fernandez
の役割を担い、Microsoft Purview Sensitivity Labels を使用してInformation
Protectionを実装しました。PowerShell を使用して SharePoint と Teams
でSensitivity
Labelsのサポートを有効にし、社内ラベルと人事固有のサブラベルを作成・公開し、これらのラベルを
Word 文書と Outlook メールに適用しました。また、ドイツ固有の GDPR
関連コンテンツ用の自動ラベル付けSensitivity
Labelsを作成・公開しました。これらの手順により、人事および規制文書が組織内で適切に分類・保護されます。

