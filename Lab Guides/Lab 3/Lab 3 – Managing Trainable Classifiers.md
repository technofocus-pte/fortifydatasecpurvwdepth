# ラボ 3 – トレーニング可能な分類器の管理

## 目的:

Contoso Ltd.
テナントには、将来的に複数の財務関連のドキュメントやレポートを保存するために使用される
SharePoint サイト
コレクションが含まれています。これらのドキュメントの性質上、これらのファイルを認識してラベルを付けるトレーニング可能な分類子を作成する必要があります。この目的のために、このラボではカスタムのトレーニング可能な分類子をアクティブ化し、新しい分類子を作成します。

## エクササイズ1 – 学習可能な分類器の作成

このタスクでは、Patti は新しいトレーニング可能な分類子を作成し、Contoso
Ltd によって作成および保存された一般的なデータを識別するためにさまざまな
SharePoint サイトを選択します。

1.  Microsoft Edge で、新しい InPrivate
    ウィンドウを開き、https://purview.microsoft.com
    に移動して、ユーザー名 PattiF@WWLx{TENANTPREFIX}.onmicrosoft.com
    とリソース タブに表示されているユーザー パスワードを使用して Patti
    Fernandez としてログインします。

2.  左側のナビゲーションから、\[Solutions\] \> \[Data Loss Prevention\]
    を選択します。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

3.  左側のペインから「Classifiers」を展開します。サブナビゲーション
    ペインから「Trainable Classifiers」を選択します。「+ Create
    trainable classifier to create a new
    classifier」を選択して、新しい分類子を作成します。

![](./media/image2.png)

4.  トレーニング可能な分類子の名前と説明ページに次の情報を入力します。

    - 名前: `Contoso Company Data`

    - 説明:
      `Trainable classifier for company data produced and stored by Contoso Ltd.`

5.  **Next**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

8.  「Choose sites」を選択して右側のペインを開きます。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

9.  次の SharePoint サイトを選択し、\[Add\] を選択します。

    - ブランド

    - デジタル イニシアチブ 広報

    - 仕事

    - セールスおよびマーケティング

    - Mark 8 プロジェクト チーム

![](./media/image5.png)

10. 選択したサイトがリストに表示されるまで待ってから、「Next」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

11. ネガティブ サンプル コンテンツのソース ページで、サイト \[Learn\]
    を選択し、\[Next\] を選択します。

12. 設定を確認し、\[Create trainable classifier\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

13. 「Your trainable classifier was
    created」というメッセージが表示されたら、「Done」を選択します。

選択した SharePoint
サイト内のドキュメントとファイルが分析中です。分析には最大 24
時間かかる場合があります。準備ができたら、次の操作を実行できます。

- 分類器をテストする

- 分類器を確認する

- 分類器を公開する

既存の分類子を調べて、さらに詳しく確認することができます。

## 概要:

Contoso Ltd の既存の SharePoint
サイトに保存されているファイルに一致するカスタムのトレーニング可能な分類子が正常に作成されました。
