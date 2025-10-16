# **ラボ 10: Microsoft Purview を使用して Fabric と Power BI でSensitivity Labelを適用する**

**紹介**

FabricおよびPower BI（Power BI Desktopを含む）のMicrosoft Purview
Information ProtectionのSensitivity
labelsをテナントで有効にする必要があります。Sensitivity
labelsを有効にすると、次のようになります。

- 組織内の指定されたユーザーとセキュリティグループは、 Fabric
  コンテンツにSensitivity labelsを適用できます。Fabric
  サービスでは、これは任意の Fabric アイテムを意味します。Power BI
  Desktop では、 .pbixファイルを意味します。

- サービスでは、組織のすべてのメンバーがラベルを閲覧できます。デスクトップでは、ラベルが公開されている組織のメンバーのみがラベルを閲覧できます。

**目的**

- Microsoft Purview を使用して、Microsoft Fabric で手動のSensitivity
  labels ポリシーを有効にし、優先順位を付けます。

**演習 1: Microsoft Fabric の試用版をアクティブ化し、Purview Hub
にアクセスする**

1.  Edge ブラウザーのアドレス バーを開き、次の URL を入力して Fabric
    ポータルを開きます -

  **+++https://app.fabric.microsoft.com+++**

  ![A screenshot of a computer AI-generated content may be incorrect.](./media/image1.png)

**注**: Fabric ポータルに直接アクセスする場合は、手順 2 と 3
をスキップしてください。

2.  テナントの資格情報を入力します。

    ![](./media/image2.png)

    ![](./media/image3.png)

3.  パスワード欄にテナントパスワードを入力します。次に、「**Sign
    in」**ボタンをクリックします。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image4.png)

4.  **Welcome to the Fabric view**ダイアログ
    ボックスで、\[**Cancel\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image5.png)

5.  コマンドバーのプロフィール アイコンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image6.png)

6.  **「Free trial」**ボタンに移動してクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image7.png)

7.  **Activate your 60-day free Fabric trial capacity - Trial capacity
    region**で**、Default – West US
    3**リージョンが選択されていることを確認し、
    **Activate**ボタンをクリックします。

    ![](./media/image8.png)

8.  **Successfully upgraded to a free Microsoft Fabric trial**ダイアログ
    ボックスで、 **\[Got it\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image9.png)

9.  コマンド バーの**\[設定\]**ギア ボックスをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image10.png)

10. Governance and insightsのセクションに移動し、 **Microsoft Purview
    hub (preview)**リンクをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image11.png)

11. **Microsoft Purview hub (preview)**ページで、 **\[Information
    Protection\]**タイルをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image12.png)

12. **Pick an account**ダイアログ ボックスが表示された場合、テナント ID
    を選択します。

    ![](./media/image13.png)

13. **Welcome to Information Protection in the new Microsoft Purview
    portal**ダイアログ ボックスが表示された場合は、 **\[Get
    started\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image14.png)

**演習 2: Fabric と Power BI 向けのSensitivity labels
ポリシーを作成して構成する**

1.  \[Information Protection\] ブレードで、
    **\[Policies\]**の横にあるドロップダウンに移動してクリックします。

    ![](./media/image15.png)

2.  次に、 **Label publishing policies**をクリックします。 **Label
    policies**ページで、 **Publish label**をクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image16.png)

3.  **Create policyページ**で、「**Choose sensitivity label to
    publish」**リンクに移動してクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image17.png)

4.  **Sensitivity label to
    publish**ペインが右側に表示されるので、移動して**「Confidential」**の横にあるチェックボックスを選択し、
    「**Add**」ボタンをクリックします。

    ![](./media/image18.png)

5.  次に、 **「Next」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image19.png)

6.  **Assign admin units**ページで、 **Next**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image20.png)

7.  **Publish to users and groupsページ**で、 **Users and
    groups**の横にあるチェックボックスが選択されていることを確認し、
    **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image21.png)

8.  **Policy settings**ページで、 **Require users to apply a label to
    their Fabric and Power BI
    content**の横にあるチェックボックスを選択します。次に、
    **「Next」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

9.  **Default settings for documents – Apply a default label to
    documents**ページで、 **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image24.png)

10. **Default settings for documents – Apply a default label to
    emails**ページで、 **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image25.png)

11. **Default settings for meetings and calendar eventsページ**で、
    **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image26.png)

12. **Default settings for Fabric and Power BI contentページ**で、
    **\[Next\]**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image27.png)

13. **Name your policy**ページの**Name**欄に、**+++Manual Labeling – HR
    Confidential
    Docs+++**と入力します。「**Next」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image28.png)

14. **Review and finishページ**で、
    **「Submit」**ボタンをクリックします。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image29.png)

15. ポリシーが正常に作成されました。「**Done」**ボタンをクリックしてください。

    ![](./media/image30.png)

16. **Label policies**ページに、**Manual Labeling – HR Confidential
    Docs**ポリシーが正常に作成されたことが表示されます。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image31.png)

17. **Manual Labeling – HR Confidential
    Docs**を選択し、水平の省略記号をクリックして移動し、「**Move
    up」**を選択して優先度を変更します。

    ![](./media/image32.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image33.png)

18. もう一度、 **\[Manual Labeling – HR Confidential
    Docs\]**を選択し、その横にある水平の省略記号をクリックして、
    **\[Move up\]を選択します**。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image34.png)

19. **Manual Labeling – HR Confidential Docs**の優先度が 1
    に変更されていることがわかります。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image35.png)

**まとめ**

このラボでは、Microsoft Fabric の試用版を有効化し、Microsoft Purview
ポータルにアクセスし、ユーザーに Fabric および Power BI
コンテンツに「Confidential」ラベルを適用させるよう必須のsensitivity
labelポリシーを作成しました。。その後、ポリシーの適用優先順位を設定しました。

