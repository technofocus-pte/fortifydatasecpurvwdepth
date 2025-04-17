# ラボ 9 – 通信コンプライアンスの構成

## 目的:

このラボでは、コンプライアンス
ポリシーを構成して、組織内のユーザーによって伝達される機密情報を検出します。前のラボで作成した機密情報の種類を使用して、電子メールで伝達される従業員の健康データや従業員
ID を検出します。

## エクササイズ1 – コミュニケーションコンプライアンスの権限を有効にする

このタスクでは、ユーザーを特定の役割グループに割り当てて、組織内のさまざまなユーザー間で通信コンプライアンス
アクセスと責任をセグメント化します。

1.  Microsoft Purview ポータルが開いている場合は手順 2
    に進みます。そうでない場合は、https://purview.microsoft.com
    を開き、MOD 管理者の資格情報でログインします。

2.  ナビゲーションで \[Settings\] を選択し、\[Role groups\] の下の
    \[Role groups\] を選択して、\[Communication compliance\]
    を選択します。次に、\[Edit\] を選択します。サイド ペインで、もう一度
    \[Edit\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3.  役割グループのメンバーの編集で、Choose usersを選択します。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4\. MOD 管理者、Megan Bowen、Patti Fernandez
が選択されていることを確認します。次に、\[Select\]
を選択します。![](./media/image3.png)

5.  **Next**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6\. \[Save\] を選択して、ユーザーをロール グループに追加します。\[Done\]
を選択して手順を完了します。![A screenshot of a computer Description
automatically generated](./media/image5.png)

![A screenshot of a computer Description automatically
generated](./media/image6.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

コンピュータのスクリーンショット 説明は自動的に生成されました

## エクササイズ2 – コミュニケーションコンプライアンスのためのグループの設定

ポリシーでは、電子メール
アドレスを使用して個人またはグループを識別します。セットアップを簡素化するために、コミュニケーションをレビューするユーザーのグループと、それらのコミュニケーションをレビューするユーザーのグループを作成できます。

PowerShell を使用して、割り当てられたグループのグローバル
コミュニケーション コンプライアンス
ポリシーの配布グループを構成できます。これにより、単一のポリシーで何千人ものユーザーのメッセージを検出し、新しい従業員が組織に加わるたびにコミュニケーション
コンプライアンス ポリシーを最新の状態に保つことができます。

1.  管理者モードで PowerShell を開きます。

2.  次のコマンドレットを入力して、Exchange Online PowerShell
    モジュールを使用し、テナントに接続します。

`Connect-``ExchangeOnline`

![Text Description automatically generated](./media/image7.png)

自動生成されるテキスト説明

3\. サインインウィンドウが表示されたら、MOD
Administratorとしてサインインします。![BrokenImage](./media/image8.png)


4.  次のプロパティを使用して、グローバル通信コンプライアンス
    ポリシー専用の配布グループを作成します。

    - MemberDepartRestriction =
      Closed。ユーザーが配布グループから自分自身を削除できないようにします。

    - MemberJoinRestriction =
      Closed。ユーザーが配布グループに自分自身を追加できないようにします。

    - ModerationEnabled =
      True。このグループに送信されるすべてのメッセージが承認の対象となり、グループが通信コンプライアンス
      ポリシー構成外で通信するために使用されていないようにします。

`New-``DistributionGroup`` -Name "Communication Compliance Group Contoso" -Alias "CCG_Contoso" -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true`

![BrokenImage](./media/image9.png)


注: 組織内の通信コンプライアンス
ポリシーに追加されたユーザーを追跡するには、次のコマンドのように
Exchange カスタム属性を追加できます。

`Set-``DistributionGroup`` -Identity "Communication Compliance Group Contoso"-CustomAttribute1 "MonitoredCommunication"`

![A screen shot of a computer Description automatically
generated](./media/image10.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

5.  次の PowerShell スクリプトを定期的に実行して、ユーザーを通信コンプライアンス ポリシーに追加します。

> $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
>     $i = 0
>     ForEach ($M in $Mbx)
>     {
>     Write-Host "Adding" $M.DisplayName
>     Add-DistributionGroupMember -Identity "Communication Compliance Group Contoso" -Member $M.DistinguishedName -ErrorAction SilentlyContinue
>     Set-Mailbox -Identity $M.Alias -CustomAttribute1 "MonitoredCommunication"
>     $i++
>     }
>     Write-Host $i "Mailboxes added to supervisory review distribution group."

![BrokenImage](./media/image11.png)



注:
このスクリプトは、特定の間隔ごとに実行されることになっています。現時点では、Microsoft
365 管理センターの \[アクティブなチームとグループ\]
の下に配布リストが表示されます。

グループ名をクリックすると、\[メンバー\]
タブの下にリストされているすべてのユーザーが表示されます。

![BrokenImage](./media/image12.png)


## エクササイズ3 – コミュニケーションコンプライアンスポリシーの作成

1.  Microsoft Purview コンプライアンス ポータルが開いている場合は、手順
    2 に進みます。そうでない場合は、https://purview.microsoft.com
    を開いて、MOD 管理者としてログインします。

2.  Microsoft Purview ポータルで、\[Solutions \> Communication
    compliance\] を選択します。

3.  サブナビゲーションから \[Policy\] を選択します。次に、\[Create
    policy\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4\. ドロップダウンから「Custom
policy」を選択します。![](./media/image14.png)

5.  \[Name your DLP policy\] ページで、\[Name\] フィールドに「My first
    communication Compliance policy」と入力し、\[Description\]
    フィールドに「This is a policy to test communication
    Compliance」と入力します。Next\] を選択します。

![Graphical user interface, text, application Description automatically
generated](./media/image15.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

6\. 「Choose supervised users and
reviewers」ページで、残りの設定はデフォルトのままにして、「Reviews」の下に
Patti Fernandez を追加します。次に、「Next」をクリックします。![A
screenshot of a computer Description automatically
generated](./media/image16.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7.  通信ページで、Microsoft 365
    の場所の下にあるすべてのボックスをオンにして、\[Next\]
    をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

8\. \[Choose conditions and review percentage\] で \[Add condition\]
を選択し、ドロップダウンから \[Content contains any of these sensitive
info types\] を選択します。![A screenshot of a computer screen
Description automatically generated](./media/image18.png)

コンピュータ画面のスクリーンショット 説明は自動的に生成されました

9.  \[Content contains any of these sensitive info types\]
    ボックスで、\[Add\] を選択し、\[Sensitive info types\]
    をクリックして、contoso
    を検索します。以前のラボで作成したすべての機密情報の種類にチェックを入れます。次に、\[Add\]
    をクリックします。

![Graphical user interface, text, application Description automatically
generated](./media/image19.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

10. 「Choose conditions and review percentage」で、「Use OCR to extract
    text from images」の横にあるボックスをオンにし、「Review
    percentage」を 100% に設定して、「Next」をクリックします。

![Graphical user interface, application Description automatically
generated](./media/image20.png)

グラフィカルユーザーインターフェイス、アプリケーションの説明は自動的に生成されます

11\. \[Review and finish\] ページで、\[Create policy\]
を選択します。![Graphical user interface, text, application Description
automatically generated](./media/image21.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

12\. 「Your policy was
created」ページが表示され、ポリシーがいつアクティブ化されるか、どの通信がキャプチャされるかを示すガイドラインが表示されます。![Graphical
user interface, text, application Description automatically
generated](./media/image22.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

## エクササイズ4 – コミュニケーションコンプライアンスポリシーの編集

1.  Microsoft Purview コンプライアンス ポータルが開いている場合は、手順
    2 に進みます。そうでない場合は、https://purview.microsoft.com
    を開いて、MOD 管理者としてログインします。

2.  Microsoft Purview ポータルで、\[Settings \> Communication compliance
    \> Policies\]に移動し、\[My first communication compliance policy\]
    の近くにある 3 つのドットを選択して、\[Edit\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3\.
ポリシーの名前と説明を空白のままにして、「Next」をクリックします。![Graphical
user interface, text, application Description automatically
generated](./media/image24.png)

グラフィカルユーザーインターフェイス、テキスト、アプリケーションの説明が自動的に生成されます

4\. \[Choose supervised user and reviewers\] の \[Supervised users and
groups\] で、\[Select users button\] ボタンを選択します。![Graphical
user interface, application, Teams Description automatically
generated](./media/image25.png)

グラフィカルユーザーインターフェイス、アプリケーション、Teamsの説明が自動的に生成されます

5\. \[Start typing to find users or groups, search for Communication\]
で、「Communication」を検索し、\[Communication Compliance Groups
Contoso\] を選択します。![](./media/image26.png)

6\. 「Reviewers」の下の「Choose supervised user and reviewers」で、MOD
管理者をレビュー担当者に追加します。![Graphical user interface,
application, Teams Description automatically
generated](./media/image27.png)

グラフィカルユーザーインターフェイス、アプリケーション、Teamsの説明が自動的に生成されます

7.  「Review and finish」ページが表示されるまで「次へ」を選択します。

8.  「Save」をクリックします。

## エクササイズ5 – 通知テンプレートの作成とユーザー匿名化の設定

1\. Microsoft Purview ポータルで、右上隅から \[Settings\]
を選択し、\[Communication compliance\]
を選択します。![](./media/image28.png)

2\. \[Privacy\] タブを選択します。匿名化を有効にするには、\[Show
anonymized versions of usernames\]
が選択されていることを確認します。\[Save\] を選択します。![A screenshot
of a computer Description automatically generated](./media/image29.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3\. 「Notice templates」タブに移動し、「Create notice
template」を選択します。![](./media/image30.png)

4.  「Change notification
    template」ページで、次のフィールドに入力します。

    - テンプレート名 (必須): サンプル通知

    - 送信元 (必須): Patti
      と入力し、ドロップダウンから名前を選択して、Patti Fernandez
      を選択します。

    - Cc (オプション): MOD
      と入力し、ドロップダウンから名前を選択して、MOD
      管理者を選択します。

    - 件名 (必須): コミュニケーション バイオレット社のコミュニケーション
      コンプライアンス ポリシー。

    - メッセージ本文 (必須):
      今後の参照用にこれをメモし、現在のコミュニケーションの妥当な理由を記入してください。

5\. 「C-reate」と「C-reate」を唱えて、「Nochi se mp'ate」と言います。![A
screenshot of a computer Description automatically
generated](./media/image31.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

## エクササイズ6 – コミュニケーションコンプライアンスポリシーのテスト

試用アカウントでは、電子メールを送信する権限はありませんが、独自のライセンスがある場合にポリシーをテストする方法を理解するには、次の手順を確認してください。手順を実行することはできますが、メールは現在のテナントの受信者に届きません。

1.  https://outlook.office365.com/mail/ にアクセスして Outlook
    を開き、ユーザー名 adelev@{TENANTPREFIX}.onmicrosoft.com とユーザー
    パスワードでサインインします。

2.  次のメッセージ本文を記載したメールを個人のメール
    アカウントに送信します。

メッセージ本文: 従業員 Patti Fernandez EMP123456
は、インフルエンザのため欠勤しています

注: 電子メール メッセージは、ポリシーで完全に処理されるまでに約 24
時間かかる場合があります。Microsoft Teams、Yammer、およびサードパーティ
プラットフォームでの通信は、ポリシーで完全に処理されるまでに約 48
時間かかる場合があります。

https://purview.microsoft.com/ に Patti Fernandez
としてサインインします。\[コミュニケーション コンプライアンス\] \>
\[アラート\] に移動して、24 時間後にポリシーのアラートを表示します。

**概要:**

このラボでは、通信コンプライアンスのアクセス許可を有効にし、ポリシーを作成して管理し、通知テンプレートを作成してユーザーの匿名化を構成する方法を学習しました。
