**ラボ 10 – Microsoft Purview を使用して Fabric と Power BI でSensitivity labelを強制する**

**導入**

FabricおよびPower BI（Power BI Desktopを含む）のMicrosoft Purview Information ProtectionのSensitivity labelをテナントで有効にする必要があります。Sensitivity labelを有効にすると、次のようになります。

- 組織内の指定されたユーザーとセキュリティグループは、Fabric コンテンツにSensitivity labelを適用できます。Fabric サービスでは、これは任意の Fabric アイテムを意味します。Power BI Desktop では、 .pbixファイルを意味します。

- サービスでは、組織のすべてのメンバーがラベルを閲覧できます。デスクトップでは、ラベルが公開されている組織のメンバーのみがラベルを閲覧できます。

**客観的**

- Microsoft Purview を使用して、Microsoft Fabric で手動のSensitivity label ポリシーを有効にし、優先順位を付けます。

**演習 1 – Microsoft Fabric の試用版をアクティブ化し、Purview Hub にアクセスする**

1.  Edge ブラウザーのアドレス バーを開き、次の URL を入力して Fabric ポータルを開きます - https://app.fabric.microsoft.com

<img src="media/image1.png" style="width:6.26806in;height:4.21667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**注**: Fabric ポータルに直接アクセスする場合は、手順 2 と 3 をスキップしてください。

2.  テナントの資格情報を入力します。

<img src="media/image2.png" style="width:6.26806in;height:4.86597in" />

<img src="media/image3.png" style="width:6.26806in;height:4.37778in" />

3.  パスワード欄にテナントパスワードを入力します。次に、「**Sign in」**ボタンをクリックします。

<img src="media/image4.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

4.  **\[Welcome to the Fabric view\]ダイアログ ボックス**で、 **\[Cancel\]**ボタンをクリックします。

<img src="media/image5.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  コマンド バーのプロフィール アイコンをクリックします。

<img src="media/image6.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  **「Free trial」ボタン**に移動してクリックします。

<img src="media/image7.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **Activate your 60-day free Fabric trial capacityのTrial capacityリージョン**で、**Default – West US 3** **リージョンが選択されている**ことを確認し、**Activateボタン**をクリックします。

<img src="media/image8.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  **Successfully upgraded to a free Microsoft Fabric trial** ダイアログ ボックスで、 **\[Got it\]**ボタンをクリックします。

<img src="media/image9.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  コマンド バーの**\[Settings\]ギア ボックス**をクリックします。

<img src="media/image10.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. **「Microsoft Purview hub（Preview）」リンク**をクリックします。次に、 **「Microsoft Purview hub（Preview）」ページで、 「Information Protection」タイル**をクリックします。

<img src="media/image11.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image12.png" style="width:6.26806in;height:3.69028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. 場合によっては、 **「Pick an account」**ダイアログ ボックスが表示されるので、テナント ID を選択します。

<img src="media/image13.png" style="width:6.26806in;height:3.78958in" />

12. **\[Welcome to Information Protection in the new Microsoft Purview portal\]**で、 **\[Get started\]**ボタンをクリックします。

<img src="media/image14.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**演習 2 – Fabric と Power BI のSensitivity label ポリシーの作成と構成**

1.  \[Information Protection\] ブレードで、 **\[Policies\]**の横にあるドロップダウンに移動してクリックします。

<img src="media/image15.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  次に、 **「Label publishing policies」をクリックします**。 **「Label publishing policies」ページで、 「Publish label」**をクリックします。

<img src="media/image16.png" style="width:6.26806in;height:3.68611in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  **「Create policy」ページ**で、 **「Choose sensitivity label to publish」**リンクに移動してクリックします。

<img src="media/image17.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  **Sensitivity label to publish** **の**ペインが右側に表示されるので、移動して**「Confidential」の横にあるチェックボックスを選択し、 「Add」ボタン**をクリックします。

<img src="media/image18.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  次に、 **「Next」**ボタンをクリックします。

<img src="media/image19.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  **Assign admin units** ページで、 **\[Next\]**ボタンをクリックします。

<img src="media/image20.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **\[Publish to users and groups\]ページ**で、 **\[Users and groups\] の**横にあるチェックボックスが選択されていることを確認し、 **\[Next\]ボタン**をクリックします。

<img src="media/image21.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  **Policy settingsページ**で、 **「Require users to apply a label to their Fabric and Power BI content」**の横にあるチェックボックスをオンにします。次に、 **「Next」**ボタンをクリックします。

<img src="media/image22.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image23.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **Default settings for documents – Apply a default label to documents** **ページ**で、 **\[Next\]**ボタンをクリックします。

<img src="media/image24.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

10. **Default settings for documents – Apply a default label to emails** **ページ**で、 **\[Next\]**ボタンをクリックします。

<img src="media/image25.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

11. **Default settings for meetings and calendar events** **ページ**で、 **\[Next\]**ボタンをクリックします。

<img src="media/image26.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

12. **Default settings for Fabric and Power BI content** **ページ**で、 **\[Next\]**ボタンをクリックします。

<img src="media/image27.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. **「Name your policy」**ページの「**Name」**欄に「Manual Labeling – HR Confidential Docs」と入力します。「**Name」**ボタンをクリックします。

<img src="media/image28.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. **「Review and finish」ページ**で、 **「Submit」**ボタンをクリックします。

<img src="media/image29.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. ポリシーが正常に作成されました。「**Done」**ボタンをクリックしてください。

<img src="media/image30.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. **Label policiesページ**に、**Manual Labeling – HR Confidential Docs** **ポリシーが正常に作成された**ことが表示されます。

<img src="media/image31.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. **「Manual Labeling – HR Confidential Docs」**を選択し、水平の省略記号をクリックして移動し、「**Move up」を選択して**優先度を変更します。

<img src="media/image32.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image33.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. もう一度、 **\[Manual Labeling – HR Confidential Docs\] を選択し**、その横にある水平の省略記号をクリックして、 **\[Move up\]を選択します**。

<img src="media/image34.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. **「Manual Labeling – HR Confidential Docs」の**優先度が 1 に変更されていることがわかります。

<img src="media/image35.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**まとめ**

このラボでは、Microsoft Fabric の試用版を有効化し、Microsoft Purview ポータルにアクセスし、Fabric および Power BI コンテンツに「Confidential」ラベルを適用することをユーザーに義務付ける必須のSensitivity labelポリシーを作成しました。その後、ポリシーの適用優先順位を設定しました。
