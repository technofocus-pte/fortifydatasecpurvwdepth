#  ラボ8 – 適応型保護の機能を探る

## エクササイズ1 – 適応型保護の設定

### タスク 1 – 適応型保護のリスクレベルの設定

1.  Microsoft Edge で、新しい InPrivate
    ウィンドウを開き、https://purview.microsoft.com
    に移動して、管理者テナントを使用してログインします。

2.  ナビゲーション バーから、\[Solutions\] \> \[Insider リスク管理\]
    に移動します。

![](./media/image1.png)

3\. サブナビゲーションから、「Adaptive Protection
(Preview)」を選択します。![A screenshot of a computer Description
automatically generated](./media/image2.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4\. Adaptive Protection を有効にする際にクイック スタート
オプションを使用したため、2 つの DLP
ポリシーが作成されていることがわかります。![A screenshot of a computer
Description automatically generated](./media/image3.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

5\. サブメニューから「Risk levels for Adaptive
Protection」をクリックし、ドロップダウンから「Data leaks by a
user」を選択します。![BrokenImage](./media/image4.png)


6.  リスク レベルの条件の定義で、高リスクの場合は「ユーザーが少なくとも
    3
    つのデータ流出アクティビティをそれぞれ実行…」を選択します。中リスクの場合は「ユーザーが少なくとも
    2
    つのデータ流出アクティビティをそれぞれ実行…」を選択します。軽度リスクの場合は「ユーザーが少なくとも
    1
    つのデータ流出アクティビティをそれぞれ実行…」を選択します。次に、\[Save\]
    をクリックします。

![BrokenImage](./media/image5.png)


7.  同様に、インサイダー
    リスク管理で利用可能なすべてのポリシーの条件をカスタマイズできます。

8.  これで、各レベルの DLP ポリシーをカスタマイズできます。

### タスク 2 – 各リスクレベルにおけるデフォルトのDLPポリシーの検討

Adaptive Protection

1\. 「Adaptive Protection」で、「DLP Policy」を選択し、「Endpoint
DLP」の「Adaptive Protection
Policy」を選択します。![BrokenImage](./media/image6.png)


2.  **Edit**を選択します。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image7.png)

コンピュータ画面のスクリーンショット。中程度の信頼性で自動生成された説明

3\. 「Customize advanced DLP
rules」に到達するまで「Next」をクリックします。![A screenshot of a
computer Description automatically generated](./media/image8.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

4.  各リスク レベルに設定されたルールと条件を確認します。\[Next\]
    をクリックします。

5.  \[Policy mode\] ページで、\[Turn it on\] の横にあるラジオ
    ボタンを選択します。\[Next\] をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

6\. 「」を選択します。![A screenshot of a computer Description
automatically generated](./media/image9.png)

コンピュータのスクリーンショット 説明は自動的に生成されました

7.  手順を繰り返して、Teams および Exchange DLP
    の適応型保護ポリシーを有効にします。

8.  現時点ではルールやポリシーは作成しませんが、ラボを完了した後で利用可能なさまざまなオプションを調べることができます。
