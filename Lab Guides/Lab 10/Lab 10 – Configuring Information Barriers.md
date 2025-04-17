# ラボ 10 – 情報バリアの設定

## 目的:

Contoso には、人事、営業、マーケティング、研究、製造の 5
つの部門があります。業界の規制に準拠し続けるために、次の表に示すように、一部の部門のユーザーは他の部門と通信することが許可されていません。

[TABLE]

この構造では、Contoso の計画には 3 つの IB ポリシーが含まれています。

1.  営業部門が研究部門と通信できないように設計された IB ポリシー

2.  研究部門が営業部門と通信できないようにする別の IB ポリシー。

3.  製造部門が HR
    およびマーケティング部門とのみ通信できるように設計された IB
    ポリシー。

## エクササイズ 1 – 前提条件

### タスク 1 – 組織内のユーザーのセグメントを作成する

1\. VM 上で、管理者として PowerShell
を実行します。![BrokenImage](./media/image1.png)


`2. ``以下を実行します``。`

`Install-Module ``ExchangeOnlineManagement`

3.  PowerShellGet で NuGet
    プロバイダーを今すぐインストールしてインポートしますか?」および​​「「PSGallery」からモジュールをインストールしてもよろしいですか?」というメッセージが表示されたら、y
    と入力して Enter キーを押します。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  インストールが完了したら、次のコマンドを実行します。

`Import-Module ``ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image3.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

5.  次のコマンドを実行して、Exchange Online に接続します。

`Connect-``IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6.  ラボ環境のホームページに記載されている MOD
    管理者の資格情報を使用してログインします。

![BrokenImage](./media/image5.png)


7.  PowerShell で次のコマンドを 1 つずつ実行して、組織構造を作成します。

`New-``OrganizationSegment`` -Name "HR" -``UserGroupFilter`` "Department -eq 'HR'"`

![BrokenImage](./media/image6.png)


`New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"`

`New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"`

`New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"`

`New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"`

### タスク 2 – Microsoft Teams でスコープ ディレクトリ検索を有効にする

名前による検索を有効にするには

1.  https://admin.teams.microsoft.com にアクセスし、\[Teams\] \> \[Teams
    settings\] を選択して、Microsoft Teams 管理センターに移動します。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

2\. \[Search by name\] の \[Scope directory search using an Exchange
address book policy\] の横にあるトグルをオンにします。\[Save\]
を選択します。![A screenshot of a computer Description automatically
generated](./media/image8.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

## エクササイズ 2 – Create IB policies

### タスク– セグメント間の通信をブロックする

1\. 環境のリソース タブで指定された MOD
管理の資格情報を使用して、https://purview.microsoft.com/
にサインインします。

2\. 左側のナビゲーション ウィンドウで、\[Solutions \> Information
barriers\] を選択します。![](./media/image9.png)

3.  サブナビゲーションで、「Policy」を選択します。「Policy」ページで、「Create
    policy」を選択して、新しい IB ポリシーを作成して構成します。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  \[Name\] ページで、ポリシーの名前 (Sales-Research)
    を入力します。次に、\[Next\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

5\. \[Assigned segment\] ページで、\[Choose segment\]
を選択します。\[このポリシーに割り当てられたセグメントを選択\]
ペインで、\[Sales\] を選択します。次に、\[Add\]
を選択して、選択したセグメントをポリシーに追加します。選択できるセグメントは
1 つだけです。![A screenshot of a computer Description automatically
generated](./media/image12.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6\. 「Next」を選択します。![A screenshot of a computer Description
automatically generated](./media/image13.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7.  \[Communication and collaboration\] で、\[Blocked\]
    を選択します。\[Choose segment\] を選択し、\[Research\]
    を選択して、\[Add\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

8.  \[Communication and collaboration\] ページで、\[Communication and
    collaboration\] フィールドのポリシー タイプとして \[Blocked\]
    を選択します。\[Next\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

9.  \[Policy status\] ページで、アクティブなポリシー
    ステータスをオンに切り替えます。\[Next\] を選択して続行します。

![BrokenImage](./media/image16.png)


10\. \[Review your settings\]
ページで、ポリシーに選択した設定と、選択内容に関する提案や警告を確認します。\[Edit\]
を選択してポリシーのセグメントとステータスを変更するか、\[Submit\]
を選択してポリシーを作成します。![BrokenImage](./media/image17.png)


11\. ポリシーが作成されたら、「Done」を選択します。![A screenshot of a
computer Description automatically generated](./media/image18.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

### タスク 2 – PowerShell 経由で IB ポリシーを作成する

1\. VM 上で、管理者として PowerShell
を実行します。![Image](./media/image1.png)


2.  `以下を実行します``。`

> `Import-Module ``ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image19.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3.  `次のコマンドを実行して、``Exchange Online ``に接続します。`

> `Connect-``IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  ラボ環境のリソース ページに記載されている MOD
    管理者の資格情報を使用してログインします。

5.  次のコマンドを実行して、Research-Sales という IB
    ポリシーを作成します。このポリシーがアクティブになって適用されると、Research
    セグメントのユーザーが Sales
    セグメントのユーザーと通信するのを防ぐのに役立ちます。

`New-``InformationBarrierPolicy`` -Name "Research-Sales" -``AssignedSegment`` "Research" -SegmentsBlocked "Sales" -State Inactive`

![BrokenImage](./media/image20.png)


6.  次のコマンドを実行して、Manufacturing-HRMarketing という IB
    ポリシーを作成します。このポリシーがアクティブになって適用されている場合、製造部門は
    HR およびマーケティング部門とのみ通信できます。HR
    およびマーケティング部門は他のセグメントとの通信が制限されません。

`New-``InformationBarrierPolicy`` -Name "Manufacturing-``HRMarketing``" -``AssignedSegment`` "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive`

![A computer screen shot of a computer program Description automatically
generated](./media/image21.png)

コンピュータプログラムのスクリーンショット 説明は自動的に生成されます

7\. 環境のホームページに記載されている MOD
管理の資格情報を使用して、https://purview.microsoft.com/
にサインインします。

8\. 左側のナビゲーション ペインで、\[Information barriers \> Policies\]
を選択します。\[Policies\]
ページで、作成したポリシーを確認できます。![](./media/image22.png)

## エクササイズ 3 – IB ポリシーを適用する

1\. 環境のリソース タブで指定された MOD
管理の資格情報を使用して、https://purview.microsoft.com/
にサインインします。

2\. 左側のナビゲーション ウィンドウで、\[Information barriers\]
を選択します。![](./media/image9.png)

3\. サブナビゲーションで、「Policy applications」を選択します。「Apply
all policies」を選択します。![](./media/image23.png)

**概要:**

このラボでは、IB
ポリシーを実装するためのセグメントの作成方法を学習しました。異なるセグメント間の通信とコラボレーションを許可またはブロックすることで情報バリアを作成するためのさまざまなポリシーを作成しました。
