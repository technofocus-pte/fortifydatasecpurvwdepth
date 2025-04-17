# ラボ 7 – インサイダーリスク管理の設定

## 目的:

このラボでは、インサイダー リスク管理ポリシーを使用してインサイダー
リスク管理を構成する方法を学習します。ラボ 2
で作成した機密情報の種類とラボ 5 で作成した DLP
ポリシーを使用して、危険なブラウザーの使用やデータの盗難や漏洩から組織を保護するポリシーを作成します。

これを行うには、組織内のデバイスを表すインフラストラクチャを Azure
に作成します。これらのデバイスを Azure AD と Intune にオンボードし、MDM
エージェントをインストールして、それらのマシンからアラートを取得できるようにする方法を学習します。

## エクササイズ1: VMクロックを同期する

1\. VM にログインした後、Windows
アイコンを選択します。次に、日付と時刻を検索し、日付と時刻の設定を選択します。![A
screenshot of a computer Description automatically
generated](./media/image1.jpg)

コンピュータのスクリーンショット 説明は自動的に生成されました

2\. 開いた「Settings」画面で、「Additional settings」の「Sync
now」をクリックします。![A screenshot of a computer Description
automatically generated](./media/image2.jpg)

コンピュータのスクリーンショット 説明は自動的に生成されました

3.  自動同期が機能しない場合に備えて、時刻の同期が行われます。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image3.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

## エクササイズ2: インサイダー リスク管理ポリシーを作成します。

### 前提条件

#### ステップ 1 – Insider リスク管理役割グループにユーザーを追加する

1.  Microsoft Purview ポータルが開いている場合は手順 2
    に進みます。そうでない場合は、https://purview.microsoft.com
    を開き、MOD ADMINISTRATORの資格情報でログインします。

![](./media/image4.png)

2.  ナビゲーションで設定を選択し、役割グループの下の「Role
    groups」を選択し、「Insider Risk
    Management」を選択します。次に「Edit」を選択します。サイドペインで再度「Edit」を選択します。

![](./media/image5.png)

3\.
役割グループのメンバーの編集ページで、ユーザーの選択を選択します。![A
screenshot of a computer Description automatically
generated](./media/image6.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4\. MOD Admin、Patti、Megan、Alex
の横にあるチェックボックスをオンにします。次に、\[Select\]
を選択します。![](./media/image7.png)

5\. 次に「Next」を選択します。![A screenshot of a computer Description
automatically generated](./media/image8.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6.  \[Save\] を選択して、ユーザーをロール グループに追加します。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7\. 「Done」を選択して手順を完了します。![A screenshot of a computer
Description automatically generated](./media/image10.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

#### ステップ2 – インサイダーリスク分析の洞察を有効にする

1.  Microsoft Purview ポータルで、\[Settings\] に移動し、\[Insider
    リスク管理\] に移動します。\[Analytics\] に移動してラジオ
    ボタンを有効にし、\[Save\] をクリックします。

![](./media/image11.png)

#### ステップ3 – デバイスのオンボーディング

この展開シナリオでは、まだオンボードされていないデバイスをオンボードし、Windows
10 デバイスでインサイダー リスク アクティビティを検出するだけです。

インサイダー リスク ポリシーを作成するための前提条件として、デバイス/VM
を Microsoft Entra ID に登録する必要があります。

1\. VM で Windows 設定を開きます。![A screenshot of a computer
Description automatically generated](./media/image12.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

2\. \[Accounts \> Access work or school\] に移動します。\[Access work or
school\] ページで、\[Connect\] をクリックします。![A screenshot of a
computer Description automatically generated](./media/image13.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3\. 「Set up a work or school account」プロンプトで、「Join this device
to Microsoft Entra ID」をクリックします。![](./media/image14.png)

4\. サインイン プロンプトで、ラボ環境のリソース タブに指定されている MOD
Administratorの資格情報を使用してサインインします。![A screenshot of a
computer Description automatically generated](./media/image15.png)

![Graphical user interface, application, PowerPoint Description
automatically generated](./media/image16.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

グラフィカルユーザーインターフェイス、アプリケーション、PowerPointの説明が自動的に生成されます

5\.
これがあなたの組織であることを確認するプロンプトで「Join」を押します。![Graphical
user interface, text, application Description automatically
generated](./media/image17.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

6\.
完了すると、確認ウィンドウが表示されます。これで設定は完了です。\[Done\]
をクリックします。![A screenshot of a computer Description automatically
generated](./media/image18.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7\. もう一度、\[Accounts \> Access work or school\]
に移動します。\[Access work or school\] ページで、\[Connect\]
をクリックします。![A screenshot of a computer Description automatically
generated](./media/image13.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

8\. 「Set up a work or school account」プロンプトで、MOD
ADMINISTRATORの資格情報を使用してログインします。![A screenshot of a
computer Description automatically generated](./media/image19.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

9\. 「Setting up your device」ページで、「Got it」を選択します。![A
screenshot of a computer Description automatically
generated](./media/image20.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

10\. 次に、windows settings \> Accounts \> Access work or school \>
Connected to Contoso MDM \> Info \> Syncに移動します。![A screenshot of
a computer Description automatically generated](./media/image21.png)

![A screenshot of a computer Description automatically
generated](./media/image22.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

コンピュータのスクリーンショット 説明は自動的に生成されました

11\. VM 上の Windows
シンボルをクリックします。ユーザー管理者を選択し、\[Sign out\]
を選択します。![A screenshot of a computer Description automatically
generated](./media/image23.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

12\. ユーザー画面で「Other users」を選択します。![A screenshot of a
computer Description automatically generated with medium
confidence](./media/image24.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

13. ラボ環境のホームページに記載されている O365 資格情報を入力し、MOD
    ADMINISTRATORとして VM にログインします。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image25.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

14\. Windows 設定アプリを閉じます。ラボ VM で MOD
ADMINISTRATORアカウントを使用して https://purview.microsoft.com
にサインインします。

15\. \[Settings \> Device onboarding \> Devices\]
を選択します。![](./media/image26.png)

16\. 「Turn on Device onboarding」をクリックします。![A screenshot of a
computer Description automatically generated](./media/image27.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

17\. 「Settings \> Device onboarding \> Onboarding」から、「Download
package」をクリックします。![A screenshot of a computer Description
automatically generated](./media/image28.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

18\. ファイルを右クリックして「Extract all…」を選択します。![A
screenshot of a computer Description automatically generated with medium
confidence](./media/image29.png)

![A screenshot of a computer Description automatically
generated](./media/image30.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

コンピュータのスクリーンショット 説明は自動的に生成されました

19. 完了したら、フォルダーを開き、管理者権限でファイルを実行します。

![A computer screen with a computer screen Description automatically
generated](./media/image31.png)

コンピュータ画面とコンピュータ画面の説明が自動的に生成されます

20\. 「More info」をクリックします。![Graphical user interface,
application Description automatically generated](./media/image32.png)

グラフィカルユーザーインターフェイス、アプリケーションの説明は自動的に生成されます

21\. とにかく「Run」をクリックします。![A screenshot of a computer error
Description automatically generated](./media/image33.png)

コンピュータエラーのスクリーンショット 説明は自動的に生成されました

22\. コマンド プロンプトで、Y キーを押して Enter
キーを押して確認し、プロンプトが表示されたら続行します。![A screenshot
of a computer error Description automatically
generated](./media/image34.png)

コンピュータエラーのスクリーンショット 説明は自動的に生成されました

23. デバイスがオンボードされたというメッセージが表示されます。コマンド
    プロンプトで、「Press any key to continue
    …」というメッセージが表示されたら、任意のキーを押します。

24. コマンド プロンプトが閉じたら、管理者モードでコマンド
    プロンプトを開き、検出テストを実行し、プロンプトで以下のコマンドをコピーして実行します。コマンド
    プロンプト ウィンドウは自動的に閉じます。

`powershell.exe -``NoExit`` -``ExecutionPolicy`` Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'`

![Text Description automatically generated](./media/image35.png)

自動生成されるテキスト説明

25. ナビゲーションの設定をクリックして設定を開き、「Devices Onboarding
    \> Devices」を選択します。

注: デバイスのオンボーディングが有効になるまでに通常約 60
秒かかりますが、最大 30 分ほどお待ちください。

26. デバイス
    リストを確認できます。デバイスをオンボードするまでリストは空ですが、完了すると、オンボードされたデバイスとして
    VM がリストされます。

### タスク 1: 危険なブラウザの使用を検出してスコアリングするための組織全体のポリシーを作成する

#### ステップ1 – 新しいポリシーを作成する

1.  前のタスクでブラウザー
    ウィンドウを閉じた場合は、https://purview.microsoft.com
    を開き、管理者の資格情報でログインします。

2.  Insider Risk Management に移動し、\[Policy\]
    タブを選択します。\[Create policy\] を選択して、ポリシー
    ウィザードを開きます。

![](./media/image36.png)

3\. \[Choose a policy template\] ページで、\[Risky browser usage
(preview)\] の下にある \[Risky browser usage (preview)\]
を選択します。![A screenshot of a computer Description automatically
generated](./media/image37.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4\. すべての前提条件が満たされていることを確認します。![A screenshot of
a computer Description automatically generated](./media/image38.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

5\. 「Next」を選択して続行します。![A screenshot of a computer
Description automatically generated](./media/image39.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6.  「Name and description」ページで、次のフィールドに入力します。

    - 名前 (必須): ブラウザの危険な使用

    - 説明 (オプション): これは、危険なブラウザの使用に関するテスト
      ポリシーです。

o 「Next」を選択して続行します。![Graphical user interface, text,
application Description automatically generated](./media/image40.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

8.  \[Choose users, groups, & adaptive scopes\] ページで、\[All users,
    groups, & adaptive scopes.\] を選択します。\[Next\]
    を選択して続行します。

9.  \[Exclude users and groups\] ページで、\[Next\] を選択します。

10. \[Decide whether to prioritize\] ページで、\[I don’t want to specify
    priority content right now\] を選択します
    (ポリシーの作成後にこれを実行できるようになります)。\[Next\]
    を選択して続行します。

![Graphical user interface, text, application Description automatically
generated](./media/image41.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

11\. \[Triggers for this policy\] ページで、\[Turn on indicators\]
を選択します。![A screenshot of a computer Description automatically
generated](./media/image42.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

12\. \[Choose indicators to turn on\] で、\[Risky browsing indicators
(preview)\] の下にある \[Select all\]
を選択し、残りのボックスのチェックを外します。![A screenshot of a
computer Description automatically generated](./media/image43.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

13. 下にスクロールして \[Save\] を選択します。

14. \[Triggers for this policy\] の \[Select which activities will
    trigger this policy\] で、すべてのオプションを選択し、\[Next\]
    をクリックします。

![Graphical user interface, text, application Description automatically
generated](./media/image44.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

15\. \[Triggering thresholds for this policy\] ページで、\[Use custom
thresholds (Recommended)\] を選択し、すべてのしきい値を 1 日あたり 1
に変更して、\[Next\] を選択します。![Graphical user interface,
application Description automatically generated](./media/image45.png)

![A screenshot of a computer Description automatically
generated](./media/image46.png)

グラフィカルユーザーインターフェイス、アプリケーションの説明は自動的に生成されます

コンピュータのスクリーンショット 説明は自動的に生成されました

16\. インジケーターページで、「Next」を選択します。![A screenshot of a
computer Description automatically generated](./media/image47.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

17\. \[Decide whether to use default or custom indicator thresholds\]
で、\[Use default thresholds for all indicators\] を選択し、\[Next\]
を選択します。![Graphical user interface, text, application Description
automatically generated](./media/image48.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

18\. 「Review settings and
finish」で、「Submit」を選択します。![Graphical user interface, text,
application Description automatically generated](./media/image49.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

19\. ポリシーが作成されたら、「Done」を選択します。![A screenshot of a
computer Description automatically generated](./media/image50.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

20. タブを開いたまま、次のタスクに進みます。

#### ステップ2 – ポリシーを評価する

1.  「ブラウザの危険な使用」という新しいポリシーをクリックします。「ユーザーのアクティビティのスコアリングを開始」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

2.  \[Add users to multiple policies\] ペインの \[Reasons\]
    フィールドに、「Testing the policy」と入力します。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3.  \[This should last for (choose between 5 and 30 days)\]
    フィールドで、\[10 days\] を選択します。

4.  \[Search user to add to policies\] フィールドを使用します。MOD
    ADMINISTRATORを追加します。次に、\[Start scoring activity\]
    をクリックします。

5.  1 人のユーザーに対してスコアリング
    アクティビティを開始したという確認が表示されたら、\[Close\]
    をクリックします。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image53.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

### タスク2: 離脱したユーザーによるデータ盗難

#### ステップ1 – 新しいポリシーを作成する

1.  前のタスクでブラウザー
    ウィンドウを閉じた場合は、https://purview.microsoft.com
    を開き、管理者の資格情報でログインします。

2.  Insider Risk Management に移動し、\[Policy\]
    タブを選択します。\[Create policy\] を選択して、ポリシー
    ウィザードを開きます。

![](./media/image36.png)

3\. \[Choose a policy template\] ページで、\[Data theft\] の下にある
\[Data theft by departing users\] を選択します。\[Next\]
を選択して続行します。![A screenshot of a computer Description
automatically generated](./media/image54.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  「Name and description」ページで、次のフィールドに入力します。

    - 名前 (必須): ユーザーによるデータ盗難

    - 説明 (オプション): これはデータ盗難を防止するためのテスト
      ポリシーです。

5\. 「Next」を選択して続行します。![A screenshot of a computer
Description automatically generated](./media/image55.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6.  \[Choose users, groups, & adaptive scopes\] ページで、\[All users,
    groups, & adaptive scopes\] を選択します。\[Next\]
    を選択して続行します。

7.  \[Exclude users, groups, & adaptive scopes\] ページで、\[Next\]
    を選択します。

8.  \[Decide whether to prioritize\] ページで、\[I want to specify
    priority content\] を選択します。\[Sensitivity labels\] と
    \[Sensitive info types\] のチェック ボックスをオンにします。\[Next\]
    を選択して続行します。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image56.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

9.  \[Sensitivity labels to prioritize\] ページで、\[Add or edit
    sensitivity labels\] を選択します。 フライアウト
    ペインで、\[Internal/Employee data (HR)\] を選択し、\[Add\]
    を選択します。 次に、\[Next\] をクリックします。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

10. \[Sensitive info types to prioritize\] ページで、\[Add or edit
    sensitive info types\] を選択します。 フライアウト
    ペインで、\[Credit Card Number\]、\[Contoso Employee ID\]、\[Contoso
    Employee EDM\] を検索して選択します。 \[Add\] を選択します。
    次に、\[Next\] をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

11. 「Decide whether to score only activity with priority
    content」で、「Get alerts for all
    activity」を選択します。「Next」を選択します。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

12\. このポリシーのトリガー ページで、デフォルトを選択し、\[Next\]
を選択します。![A screenshot of a computer Description automatically
generated with medium confidence](./media/image60.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

13\. 「Indicators」ページで、プロンプトから「Turn on indicators from the
prompt」を選択します。![A screenshot of a computer Description
automatically generated with medium confidence](./media/image61.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

14\. \[Office indicators\] の下の \[Select all\] を選択し、\[Save\]
をクリックします。![A screenshot of a computer screen Description
automatically generated with medium confidence](./media/image62.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

15\. すべてのオプションを選択し、「Next」をクリックします。![A
screenshot of a computer Description automatically
generated](./media/image63.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

16\. 検出オプション ページで、デフォルトを選択し、\[Next\]
を選択します。![A screenshot of a computer Description automatically
generated](./media/image64.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

17\. インジケーターページで、「Next」を選択します。![A screenshot of a
computer Description automatically generated](./media/image47.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

18\.
デフォルトまたはカスタムのインジケーターしきい値を使用するかどうかを決定するには、しきい値のカスタマイズを選択し、各ステージにそれぞれ
1、2、3 のイベントを使用して、次へを選択します。![A screenshot of a
computer screen Description automatically
generated](./media/image65.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

19\. 「Review settings and finish」で、「Submit」を選択します。![A
screenshot of a computer Description automatically
generated](./media/image66.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

20\. ポリシーが作成されたら、「Done」を選択します。![A screenshot of a
computer Description automatically generated](./media/image67.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

21. タブを開いたまま、次のタスクに進みます。

#### ステップ2 – ポリシーを評価する

1.  「Data theft by a
    user」という新しいポリシーをクリックします。「Start scoring activity
    for users」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image68.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

2.  \[Add users to multiple policies\] ペインの \[Reason\]
    フィールドに、「Testing the policy」と入力します。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3.  \[This should last for (choose between 5 and 30 days)\]
    フィールドで、\[10 days\] を選択します。

4.  \[Search user to add to policies\] フィールドを使用します。MOD
    ADMINISTRATORを追加します。次に、\[Start scoring activity\]
    をクリックします。

5.  1 人のユーザーに対してスコアリング
    アクティビティを開始したという確認が表示されたら、\[Close\]
    をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image69.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

### タスク3: ユーザーによるデータ漏洩

#### ステップ1 – 新しいポリシーを作成する

1.  前のタスクでブラウザー
    ウィンドウを閉じた場合は、https://purview.microsoft.com
    を開き、管理者の資格情報でログインします。

2.  Insider Risk Management に移動し、\[Policy\]
    タブを選択します。\[Create policy\] を選択して、ポリシー
    ウィザードを開きます。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3\. \[Choose a policy template\] ページで、\[Data leaks\] の下にある
\[Data leaks\] を選択します。\[Next\] を選択して続行します。![A
screenshot of a computer Description automatically
generated](./media/image70.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  「Name and description」ページで、次のフィールドに入力します。

    - 名前 (必須): ユーザーによるデータ漏洩

    - 説明 (オプション): これはデータ漏洩を防ぐためのテスト
      ポリシーです。

5\. 「Next」を選択して続行します。![A screenshot of a computer
Description automatically generated](./media/image71.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6\. \[Choose users and groups page\] ページで、\[Include all users and
groups\] を選択します。\[Next\] を選択して続行します。![A screenshot of
a computer Description automatically generated](./media/image72.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7.  \[Exclude users and groups\] ページで、\[Next\] を選択します。

8.  \[Decide whether to prioritize\] ページで、\[I want to specify
    priority content\] を選択します。SharePoint
    サイト、機密ラベル、機密情報の種類の各チェック
    ボックスをオンにします。\[Next\] を選択して続行します。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image73.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

9.  \[SharePoint sites to prioritize\] ページで、\[Add or edit
    SharePoint sites\] を選択します。ポップアップ
    ウィンドウで、https://{TENANTPREFIX}.sharepoint.com/sites/ContosoWeb1
    を選択し、\[Add\] を選択します。次に、\[Next\] をクリックします。

10. \[Sensitivity labels to prioritize\] ページで、\[Add or edit
    sensitivity labels\] を選択します。ポップアップ
    ウィンドウで、\[Internal/Employee data (HR)\] を選択し、\[Add\]
    を選択します。次に、\[Next\] をクリックします。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

11. \[Sensitive info types to prioritize\] ページで、\[Add or edit
    sensitive info types\] を選択します。 フライアウト
    ペインで、\[Credit Card Number\]、\[Contoso Employee ID\]、\[Contoso
    Employee EDM\] を検索して選択します。 \[Add\] を選択します。
    次に、\[Next\] をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

12\. 「Decide whether to score only activity with priority」で、「Get
alerts for all activity」を選択します。「Next」を選択します。![A
screenshot of a computer screen Description automatically generated with
medium confidence](./media/image59.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

13. \[Triggers for this policy\] ページで、\[Radio button near User
    performs an exfiltration activity\] の横にあるラジオ
    ボタンを選択します。\[select which activities will trigger this
    policy\] で、使用可能なすべてのオプション (特に \[SharePoint
    からコンテンツをダウンロード\]) を選択し、\[Next\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image74.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

14. Triggering thresholds for this policyで、Use custom
    thresholdsを選択します。すべてのしきい値を 1
    に設定し、Nextを選択します。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image75.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

15. \[Indicators\] ページで既定の設定を選択し、\[Next\] を選択します。

16. \[Decide whether to use default or custom indicator thresholds\]
    で、\[Customise thresholds\] を選択し、ステージごとにそれぞれ
    1、2、3 のイベントを使用して、\[Next\] を選択します。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image76.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

17\. 「Review settings and finish」で、「Submit」を選択します。![A
screenshot of a computer Description automatically generated with medium
confidence](./media/image77.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

18. ポリシーが作成されたら、「Done」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image78.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

> 19\. タブを開いたまま、次のタスクに進みます。

#### ステップ2 – ポリシーを評価する

1.  「Data leaks by a
    user」という新しいポリシーをクリックします。「Start scoring activity
    for users.」を選択します。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image79.png)

コンピュータのスクリーンショットの説明は中程度の確信度で自動的に生成されました

2.  \[Add users to multiple policies\] ペインの \[Reason\]
    フィールドに、「Testing the policy」と入力します。 \[この期間 (5 ～
    30 日間を選択)\] フィールドで、\[10 days\] を選択します。 \[Search
    user to add to policies\] フィールドを使用します。 MOD
    ADMINISTRATORを追加します。次に、\[Start scoring activity\]
    をクリックします。

3.  1 人のユーザーに対してスコアリング
    アクティビティを開始したという確認が表示されたら、\[閉じる\]
    をクリックします。

Insider リスク管理ポリシーが正常に作成されました。

## 概要:

このラボでは、Insider Risk Management
のセットアップを最初から最後まで説明しました。独自のサブスクリプションとライセンスがあれば、このラボ
ガイドを使用して Azure セットアップを作成し、Purview の Adaptive
Protection 機能を調べるために使用できる Insider Risk Management
ポリシーのさまざまなアラート
(試用版サブスクリプションでは不可能な、制限されたデータを含む電子メールの送信を含む)
を作成することもできます。
