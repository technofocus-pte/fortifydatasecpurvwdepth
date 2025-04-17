# ラボ 4 – 機密ラベルの操作

## 目的:

このラボでは、Contoso Ltd のシステム管理者である Patti Fernandez
の役割を担います。組織はドイツの Rednitzhembach
に拠点を置いており、組織の情報保護ポリシーの一環として、人事部門のすべての従業員ドキュメントに機密ラベルが付けられていることを確認するための機密性計画を現在実装しています。

## エクササイズ1 – 機密ラベルのサポートを有効にする

このタスクでは、MSOnline モジュールと SharePoint Online PowerShell
モジュールをインストールし、テナントで機密ラベルのサポートを有効にします。

1.  1\. タスクバーの Windows
    シンボルをマウスの右ボタンで選択し、「Windows PowerShell
    (Admin)」を選択して管理者として実行します。![A screenshot of a
    computer Description automatically generated](./media/image1.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

2.  `ユーザー`` ``アカウント制御ウィンドウで`` [``Yes``] ``を選択して`` Enter ``キーを押します。`

3.  `次のコマンドレットを入力して、最新の`` Microsoft Online PowerShell ``モジュール`` ``バージョンをインストールします。`

> `Install-Module -Name ``MSOnline`

![A screenshot of a computer Description automatically
generated](./media/image2.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  NuGet セキュリティ ダイアログと信頼されていないリポジトリ
    セキュリティ ダイアログで Y (Yes) を選択して Enter
    キーを押します。処理が完了するまでに時間がかかる場合があります。

![BrokenImage](./media/image3.png)


5.  次のコマンドレットを入力して、最新の SharePoint Online PowerShell
    モジュール バージョンをインストールします。

`Install-Module -Name ``Microsoft.Online.SharePoint.PowerShell`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6.  6\. 「Untrusted repository
    security」ダイアログで「Y」（Yes）を選択して Enter キーを押します。

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

7.  次のコマンドレットを入力して、Microsoft Online
    サービスに接続します。

`Connect-``MsolService`

![BrokenImage](./media/image6.png)


8.  \[Sign in to your account\] フォームで、ユーザー名
    PattiF@{TENANTPREFIX}.onmicrosoft.com とリソース
    タブに指定されているユーザー パスワードを使用して、Patti Fernandez
    としてログインします。

![A screenshot of a computer screen Description automatically
generated](./media/image7.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

9.  サインインしたら、PowerShell ウィンドウに移動します。

10. 次のコマンドレットを入力してドメインを取得します。

`$domain = get-``msoldomain`

![BrokenImage](./media/image8.png)


11. 次のコマンドレットを入力して、SharePoint 管理者 URL を作成します。

`$``adminurl`` = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"`

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

12. 次のコマンドレットを入力して、SharePoint Online
    管理センターにサインインします。

`Connect-``SPOService`` -``url`` $``adminurl`

![A screenshot of a computer screen Description automatically
generated](./media/image10.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

13. `「``Sign in to your account``」フォームで、ラボ環境のリソース`` ``タブで提供された資格情報を使用して`` MOD ``管理者としてログインします。`

14. `サインインしたら、``PowerShell ``ウィンドウを選択します。`

15. ` ``機密ラベルのサポートを有効にするには、次のコマンドレットを入力します。`

> `Set-``SPOTenant`` -``EnableAIPIntegration`` $true`

![BrokenImage](./media/image11.png)


16. Y (Yes) を押して変更を確認し、Enter キーを押します。

![BrokenImage](./media/image12.png)


17. PowerShell ウィンドウを閉じます。

Teams および SharePoint
サイトでの機密ラベルのサポートが正常に有効になりました。

## エクササイズ2 – 機密ラベルの作成

このタスクでは、人事部門が人事従業員ドキュメントに適用する機密ラベルを要求しています。社内ドキュメントの機密ラベルと人事部門のサブラベルを作成します。

1.  Microsoft Edge で https://purview.microsoft.com に移動し、ユーザー名
    PattiF@{TENANTPREFIX}.onmicrosoft.com とリソース
    タブに表示されているユーザー パスワードを使用して Patti Fernandez
    としてログインします。

2.  Microsoft Purview ポータルの左側のナビゲーション
    ペインで、\[Solutions\] \> \[Information Protection\]
    を選択します。![](./media/image13.png)

&nbsp;

3.  サブナビゲーションから「Sensitivity Labels」\>「Create
    Labels」を選択します。

![](./media/image14.png)

4.  新しい機密ラベル
    ウィザードが起動します。ラベルの詳細ページで、管理者の名前、説明、およびユーザーの説明に次の情報を入力します。

    - 名前: `Internal`

    - 表示名: `Internal`

    - ユーザー向けの説明: `Internal sensitivity label`

    - 管理者向けの説明: `Internal sensitivity label for Contoso.`

![Graphical user interface, text, application, email Description
automatically generated](./media/image15.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、電子メールの説明が自動的に生成されます

5.  **Next**を選択します。

![Graphical user interface, text, application Description automatically
generated](./media/image16.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

6.  \[Define the scope for this label\]
    ページで、メール、ファイル、Power BI アイテムを保護する \[Items\]
    オプションを選択します。\[Meetings\]
    の横にあるボックスのチェックを外します。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7.  **Next**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

8.  「Choose protection settings for labeled
    items」ページで、「Next」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

9.  「Auto-labeling for files and
    emails」ページで、「Next」を選択します。![A screenshot of a computer
    Description automatically generated](./media/image20.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

10. \[Define protection settings for groups and sites\]
    ページで、\[Next\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

11. 「Auto-labeling for schematized data assets
    (preview)」ページで、「Next」を選択します。

![Graphical user interface, text, application Description automatically
generated](./media/image22.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

12\. 「Review your settings and finish」ページで、「Create
label」を選択します。![A screenshot of a computer Description
automatically generated](./media/image23.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

13. ラベルが作成され、完了すると「Your sensitivity label was
    created」というメッセージが表示されます。

14. 「Don’t create a policy yet」を選択し、「Done」を選択します。

![A screenshot of a computer screen Description automatically
generated](./media/image24.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

15. \[Information Protection\] ページで、新しく作成した 内部
    ラベルを強調表示し (選択せずに)、垂直方向の \[...\] を選択します。

16. ドロップダウン メニューから「+ Add sub label」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

17. 新しい機密ラベル
    ウィザードが起動します。ラベルの詳細ページで、次の情報を入力します。

o 名前: 従業員データ (HR)

o 表示名: 従業員データ (HR)

o ユーザー向けの説明: この HR ラベルは、HR
部門のすべての指定されたドキュメントのデフォルト ラベルです。

o 管理者向けの説明: このラベルは、Jones 氏 (HR 部門長)
と相談して作成されました。ラベルの設定を変更する場合は、Jones
氏に連絡してください。![](./media/image26.png)

18\. 「 Next」を選択します。![](./media/image27.png)

19. \[Define the scope for this label\]
    ページで、電子メール、ファイル、会議を保護する \[Items\]
    オプションを選択します。\[Next\] を選択します。

![](./media/image28.png)

20\. 「Choose protection settings for labeled items」ページで、「Control
Access」オプションを選択します。「Next」を選択します。

![](./media/image29.png)

21. 「Access Control」ページで、「Configure access
    control」を選択します。

![](./media/image30.png)

22. 暗号化設定に次の情報を入力します。

o 今すぐ権限を割り当てるか、ユーザーに決定させるか:
今すぐ権限を割り当てる

o コンテンツへのユーザー アクセスの有効期限: なし

o オフライン アクセスを許可する: 指定した日数のみ

o ユーザーがコンテンツにオフラインでアクセスできる日数: 15![A screenshot
of a computer Description automatically generated](./media/image31.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

23. 「Assign permissions」リンクを選択します。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

24\. \[Assign permissions\] ペインで、\[+ Add any authenticated users\]
を選択します。![BrokenImage](./media/image33.png)


25. **Save**を選択します。

![BrokenImage](./media/image34.png)


26. 「Encryption」ページで、「Next」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

27\. 「Auto-labeling for files and
emails」ページで、「Next」を選択します。![A screenshot of a computer
Description automatically generated](./media/image36.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

28\. 「Define protection settings for groups and
sites」ページで、「Next」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

29\. 「Auto-labeling for schematized data assests
(preview)」ページで、「Next」を選択します。![A screenshot of a computer
Description automatically generated](./media/image38.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

> 30\. 「Review your settings and finish」ページで、「Create
> label」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

31\. ラベルが作成され、完了すると「Your sensitivity label was
created」というメッセージが表示されます。

32\. 「Don’t create a policy yet」を選択し、「Done」を選択します。![A
screenshot of a computer screen Description automatically
generated](./media/image40.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

33\. タブを開いたままにして、次のタスクに進みます。

組織の内部ポリシーの機密ラベルと人事 (HR)
部門の機密サブラベルが正常に作成されました。

## エクササイズ3 – 機密ラベルの公開

ここで、内部および HR の機密ラベルを公開して、公開された機密ラベルを HR
ユーザーが HR ドキュメントに適用できるようにします。

1.  Microsoft Edge で https://purview.microsoft.com に移動し、ユーザー名
    PattiF@{TENANTPREFIX}.onmicrosoft.com とリソース
    タブに表示されているユーザー パスワードを使用して Patti Fernandez
    としてログインします。

2.  Microsoft Purview ポータルの左側のナビゲーション
    ペインで、\[Solutions\] \> \[Information Protection\]
    を選択します。![](./media/image13.png)

3\. サブナビゲーションから、「Sensitivity labels」\>「Publish
labels」を選択します。![](./media/image41.png)

4\. 機密ラベルの公開ウィザードが起動します。

5\. \[Choose sensitivity labels to publish\] ページで、\[Choose
sensitivity labels to publish\] リンクを選択します。![A screenshot of a
computer Description automatically generated](./media/image42.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6\. 右側に「Sensitivity labels to
publish」というサイドバーが表示されます。

7\. 「Internal and Internal/Employee Data
(HR)」チェックボックスをオンにします。![A screenshot of a computer
Description automatically generated](./media/image43.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

8.  **Add**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image44.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

9.  \[Choose sensitivity labels to publish\] ページで、\[Next\]
    を選択します。

![A screenshot of a computer Description automatically
generated](./media/image45.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

10\. \[Publish to users and groups\] ページで、\[Next\]
を選択します。![A screenshot of a computer Description automatically
generated](./media/image46.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

11\.
ポリシー設定ページで、「Next」を選択します。![BrokenImage](./media/image47.png)


12\. 「Apply a default label to
documents」ページで、「Next」を選択します。![A screenshot of a computer
Description automatically generated](./media/image48.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

13. \[Apply a default label\] ページで、\[Next\] を選択します。

14. \[Default settings for meetings and calendar events\] で、\[Next\]
    を選択します。

15. \[Default settings for Fabric and Power BI content\]
    ページで、\[Next\] を選択します。

16. \[Name your policy\] ページで、次の情報を入力します。

    - 名前: 内部 HR 従業員データ

    - 機密ラベル ポリシーの説明を入力します: この HR ラベルは、内部 HR
      従業員データに適用されます。

![Graphical user interface, text, application, email Description
automatically generated](./media/image49.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、電子メールの説明が自動的に生成されます

17. 「Next」を選択します。

![Graphical user interface, text, application Description automatically
generated](./media/image50.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

18\. 「Review and finish」ページで、「Submit」を選択します。![Graphical
user interface, text, application Description automatically
generated](./media/image51.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

19. ポリシーが作成され、完了すると「New policy
    created」というメッセージが表示されます。

20. \[Done\] を選択し、ウィンドウを閉じずに次のタスクに進みます。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

内部および HR
の機密ラベルが正常に公開されました。変更がすべてのユーザーとサービスに複製されるまでに最大
24 時間かかる場合があることに注意してください。

## エクササイズ4 – 機密ラベルの操作

このタスクでは、Word および Outlook
の電子メールに機密ラベルを作成します。作成されたドキュメントは OneDrive
に保存され、電子メールで人事担当者に送信されます。

1.  https://portal.office.com に移動し、Patti Fernandez
    としてログインします。

2.  「Office 365 message is
    shown」というメッセージが表示されたら、閉じます。![Graphical user
    interface Description automatically generated](./media/image53.png)

グラフィカルユーザーインターフェースの説明は自動的に生成されます

3.  左側のペインから Microsoft Word シンボルを選択して、Word Online
    を開きます。

![Graphical user interface, website Description automatically
generated](./media/image54.png)

グラフィカルユーザーインターフェイス、ウェブサイトの説明は自動的に生成されます

4.  新しいドキュメントを作成するには、「New blank
    document」を選択します。

![Graphical user interface, website Description automatically
generated](./media/image55.png)

グラフィカルユーザーインターフェイス、ウェブサイトの説明は自動的に生成されます

5.  プライバシー オプションのメッセージが表示された場合は、\[Close\]
    を選択して閉じます。

![BrokenImage](./media/image56.png)


6.  `Word ``文書に次の内容を入力します。`

> 重要な人事従業員文書。

![Graphical user interface, application, Word Description automatically
generated](./media/image57.png)

グラフィカルユーザーインターフェイス、アプリケーション、Wordの説明が自動的に生成されます

7\. 上部のペインから「Sensitivity」を選択して、ドロップダウン
メニューを開きます。![Graphical user interface, application, Word
Description automatically generated](./media/image58.png)

グラフィカルユーザーインターフェイス、アプリケーション、Wordの説明が自動的に生成されます

7.  ラベルを適用するには、「Internal \> Employee data
    (HR)」を選択します。

> 注: この演習のタスク 1 で実行したスクリプトによって、テナントの Word
> で機密ラベルがアクティブ化されたことに注意してください。Microsoft Word
> オンラインでそのアクティブ化が実現されるまでに 1
> 時間かかる場合があります。Word に機密ラベル
> メニューが表示されない場合は、後でこのラボに戻るか、この演習のタスク 1
> を適切に完了したことを確認する必要があります。

![BrokenImage](./media/image59.png)


9\. ウィンドウの左上にある「Document –
Saved」を選択し、ファイル名として「HR Document」と入力して Enter
キーを押します。![Graphical user interface, application, Word
Description automatically generated](./media/image60.png)

グラフィカルユーザーインターフェイス、アプリケーション、Wordの説明が自動的に生成されます

10\. Word タブを閉じて Office 365 タブに戻ります。左側のペインから
Outlook シンボルを選択して、Outlook on the web を開きます。![Graphical
user interface, text, application Description automatically
generated](./media/image61.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

11. ようこそメッセージが表示されたら、\[X\] を選択して閉じます。

12. Outlook on the Web で、ウィンドウの左上から \[New message\]
    を選択します。

![A screenshot of a computer Description automatically
generated](./media/image62.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

13\. \[To\] フィールドに名前「Adele」を入力し、ドロップダウン
リストから「Adele Vance」を選択します。![](./media/image63.png)

14. 件名欄に「Employee data for HR」と入力します。

15. 電子メール メッセージ (ページ下部の大きなコンテンツ パネル)
    内に、次のメッセージを挿入します。

&nbsp;

    DearMs. Adele,
    Please find attached the important HR employee document.
    Kind regards,
    Patti Fernandez

![A screenshot of a computer Description automatically
generated](./media/image64.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

16. 下部のメニューからペーパークリップのシンボルを選択します。

![](./media/image65.png)

17. ドキュメントを添付するには、\[Suggested attachments\] の下の HR
    Document.docx を選択します。

18. \[Send\] を選択して、ドキュメントが添付された電子メール
    メッセージを送信します。

19. ブラウザー ウィンドウを開いたままにします。

機密ラベル付きの HR Word 文書を正常に作成し、OneDrive
に保存しました。次に、機密ラベルが設定されたメールをスタッフ
メンバーに電子メールで送信しました。

試用アカウントでは、メールを送信することはできますが、メールは返送され、現在のテナントの受信者に届かないことに注意してください。

## エクササイズ5 – 自動ラベル付けの構成

このタスクでは、欧州一般データ保護規則 (GPDR)
に関連する情報が含まれていることが検出されたドキュメントと電子メールに自動的にラベルを付ける機密ラベルを作成します。

1.  Microsoft Edge では、Microsoft Purview ポータル
    タブが開いたままになっているはずです。

2.  Patti Fernandez としてポータルにログインしているはずです。

3.  \[Information Protection\] の下で \[Label\] を選択し、既存の
    \[内部\] ラベルを強調表示して (選択せずに)、3
    つのドットを選択します。\[+ Create sublabel\]
    メニュー項目を選択します。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  New sensitivity label
    ウィザードが起動します。ラベルの詳細ページで、次の情報を入力します。

    - `名前``: GDPR ``ドイツ`

    - `表示名``: GDPR ``ドイツ`

    - `ユーザー向けの説明``: ``このドキュメントまたはメールには、ドイツ地域の欧州一般データ保護規則`` (GPDR) ``に関連するデータが含まれています。`

    - `管理者向けの説明``: ``このラベルは、ドイツの`` GDPR ``ドキュメントに自動的に適用されます。`

5.  **Next**を選択します。

![BrokenImage](./media/image67.png)


6.  \[Define the scope for this label\]
    ページで、ファイル、電子メール、会議のアイテムを保護する \[Items\]
    オプションを選択します。次に、\[Next\] を選択します。

![BrokenImage](./media/image68.png)


7\. 「Choose protection settings for labeled
items」ページで、「Next」を選択します。![BrokenImage](./media/image69.png)


8\. 「Auto-labeling for files and emails」ページで、「Auto-labeling for
files and emails」を有効に設定します。![Graphical user interface, text,
application Description automatically generated](./media/image70.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

9\. \[Detect content that matches these conditions \] セクションで、\[+
Add condition\] を選択し、\[Content contains\]
を選択します。![BrokenImage](./media/image71.png)


10\. 「Content contains」セクションで「Add」を選択し、「Sensitive info
types」を選択します。![A screenshot of a computer Description
automatically generated](./media/image72.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

11. 右側にSensitive info typesパネルが表示されます。

12. Sensitive info typesの検索パネルで、次の情報を入力します。

`German`

13. キーボードの Enter
    キーを押すと、ドイツに関連する機密情報の種類が結果に表示されます。\[Select
    all\] チェックボックスを押します。

![BrokenImage](./media/image73.png)


14. **Add**を選択します。

![BrokenImage](./media/image74.png)


15. **Next**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image75.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

16\. 「Define protection settings for groups and
sites」ページで、「Next」を選択します。![A screenshot of a computer
Description automatically generated](./media/image76.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

17. 「Auto-labeling for schematized data assets
    (preview)」ページで、「Next」を選択します。

18. 「Default settings for Fabric and Power BI
    content」ページにリダイレクトされた場合は、「Next」を選択します。

19. 「Review your settings and finish」ページで、「Create
    label」を選択します。

20\. ラベルが作成され、完了すると「Your sensitivity label was
created.」というメッセージが表示されます。次の手順で、「Don’t create a
policy yet.」を選択します。次に、「Done」を選択します。![Graphical user
interface, text, application, Word Description automatically
generated](./media/image77.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、Wordの説明が自動的に生成されます

21. サブナビゲーションから、「Sensitivity Label」\>「Publish
    Label」を選択します。

![](./media/image41.png)

22. 機密ラベルの公開ウィザードが起動します。

![Graphical user interface, text, application, Word Description
automatically generated](./media/image78.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、Wordの説明が自動的に生成されます

23\. \[Choose sensitivity labels to publish\] ページで、\[Choose
sensitivity labels to publish\] リンクを選択します。![A screenshot of a
computer Description automatically generated](./media/image79.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

24\. 右側に「Sensitivity labels to
publish」というサイドバーが表示されます。![Graphical user interface,
application, Word Description automatically
generated](./media/image80.png)

グラフィカルユーザーインターフェイス、アプリケーション、Wordの説明が自動的に生成されます

25\. \[Internal and Internal/GDPR Germany\]
チェックボックスをオンにし、\[Add\] を選択します。![Graphical user
interface, application, Word Description automatically
generated](./media/image81.png)

グラフィカルユーザーインターフェイス、アプリケーション、Wordの説明が自動的に生成されます

26. \[Choose sensitivity labels to publish\] ページで、\[Next\]
    を選択します。

![Graphical user interface, text, application, Word Description
automatically generated](./media/image82.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、Wordの説明が自動的に生成されます

27\. \[Publish to users and groups\] ページで、\[Next\]
を選択します。![Graphical user interface, text, application Description
automatically generated](./media/image83.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

28\. Policy settingsページで、「Next」を選択します。![Graphical user
interface, text, application, Word Description automatically
generated](./media/image84.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、Wordの説明が自動的に生成されます

29\. 「Apply a default label to
documents」ページで、「Next」を選択します。![Graphical user interface,
text, application Description automatically
generated](./media/image85.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

30. \[Apply a default label to emails\] ページで、\[Next\]
    を選択します。

31. \[Default settings for meetings and calendar events\] で、\[Next\]
    を選択します。

32. \[Default settings for Fabric and Power BI content\]
    ページで、\[Next\] を選択します。

33. \[Name your policy\] ページで、次の情報を入力します。

> o 名前: GDPR ドイツ ポリシー
>
> o 機密ラベル ポリシーの説明を入力します:
> この機密ラベルの自動適用ポリシーは、ドイツの GDPR 地域向けです。Select
> **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image86.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

35\. 「Review and finish」ページで、「Submit」を選択します。![Graphical
user interface, application Description automatically
generated](./media/image87.png)

グラフィカルユーザーインターフェイス、アプリケーションの説明は自動的に生成されます

36. ポリシーが作成され、完了すると「New policy
    created」というメッセージが表示されます。

37. \[Done\] を選択します。

![Graphical user interface, text, application, Word Description
automatically generated](./media/image88.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーション、Wordの説明が自動的に生成されます

## 概要:

ドイツ地域の GDPR
ドキュメントの自動適用機密ラベルが正常に作成され、公開されました。

自動適用機密ラベルの適用には最大 24
時間かかる場合があることに注意してください。25,000
件を超えるドキュメントに適用する場合は、この期間が長くなります
(つまり、1 日の制限)。
