**ラボ 11 – FabricでInformation Protectionポリシーを構成する**

**導入**

Information Protectionテナント設定は、Power BI テナント内の機密情報を保護するのに役立ちます。コンテンツにSensitivity labelを許可および適用することで、適切なユーザーのみが情報を閲覧およびアクセスできるようになります。

**客観的**

- 管理ポータルを通じて Microsoft Fabric のInformation Protection機能を有効にして、Sensitivity labelの適用を準備します。

**演習 1 – Fabric Admin Portal でInformation Protection設定を構成する**

1.  Fabric ポータルのホームページで、コマンド バーの**\[Settings\]アイコンをクリックし、 \[Governance and insights\]セクションに移動して、 \[Admin portal\]リンク**をクリックします。

> <img src="media/image1.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Admin portal – Tenant settingsで、**Information Protection**セクションまで下にスクロールします。

> <img src="media/image2.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  **「Allow users to apply sensitivity labels for content」**の横にある再生ボタンをクリックします。

> <img src="media/image3.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  トグルボタンをクリックして有効にします。この設定を有効にすると、指定されたユーザーがMicrosoft Purview Information ProtectionからSensitivity labelを適用できるようになります。

> <img src="media/image4.png" style="width:6.26806in;height:3.80833in" />

5.  次に、**「Apply」**ボタンをクリックします。

> <img src="media/image5.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> **注: \[Apply\]**ボタンが強調表示されていない場合は、 **\[Specific security groups**\] ラジオ ボタンを選択し、 **\[The entire organization**\] ラジオ ボタンを再度選択します。

6.  **\[Tenant settings will be applied within the next 15 minutes」**という通知が表示されます。

> <img src="media/image6.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **「Apply sensitivity labels from data sources to their data in Power BI」**の横にあるプレイアイコンをクリックします。

> <img src="media/image7.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  有効にするには、トグルボタンをクリックします。

> <img src="media/image8.png" style="width:6.26806in;height:3.80833in" />

9.  この設定を有効にすると、サポートされているデータ ソース内のSensitivity labelが付けられたデータに接続する Power BI セマンティック モデルはそれらのラベルを継承できるため、Power BI に取り込まれたときにデータは分類され、セキュリティが保護されたままになります。

> **「Apply」ボタン**をクリックします。
>
> <img src="media/image9.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. **\[Tenant settings will be applied within the next 15 minutes」**という通知が表示されます。

> <img src="media/image10.png" style="width:6.26806in;height:3.80833in" />

11. **「Automatically apply sensitivity labels to downstream content」**の横にあるプレイアイコンをクリックします。

> <img src="media/image11.png" style="width:6.26806in;height:3.80833in" />

12. 有効にするには、トグルボタンをクリックします。

> <img src="media/image12.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. この設定を有効にすると、Sensitivity labelを変更したり、Fabric コンテンツに適用したりするたびに、そのラベルは対象となるダウンストリーム コンテンツにも適用されます。

> **「Apply」ボタン**をクリックします。
>
> <img src="media/image13.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. 「Tenant settings will be applied within the next 15 minutes」という通知が表示されます。

> <img src="media/image14.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. **「Allow workspace admins to override automatically applied sensitivity labels**」の横にあるプレイアイコンをクリックします。

> <img src="media/image15.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. 有効にするには、トグルボタンをクリックします。

> <img src="media/image16.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. この設定により、ワークスペース管理者は、ラベル変更の適用ルールに関係なく、自動的に適用されたSensitivity labelを上書きできるようになります。

> **「Apply」**ボタンをクリックします
>
> <img src="media/image17.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. 「Tenant settings will be applied within the next 15 minutes」という通知が表示されます。

> <img src="media/image18.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. **Restrict content with protected labels from being shared via link with everyone in your organization**の横にあるプレイアイコンをクリックします。

> <img src="media/image19.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

20. 有効にするには、トグルボタンをクリックします。

> <img src="media/image20.png" style="width:6.26806in;height:3.80833in" />

21. この設定を有効にすると、ユーザーはSensitivity labelに保護設定があるコンテンツについて、組織内のユーザー向けの共有リンクを生成できなくなります。

> **「Apply」**ボタンをクリックします
>
> <img src="media/image21.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

22. 「Tenant settings will be applied within the next 15 minutes」という通知が表示されます。

> <img src="media/image22.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

23. **「Domain admins can set default sensitivity labels for their domains (preview)」**の横にあるプレイアイコンをクリックします。

> <img src="media/image23.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

24. 有効にするには、トグルボタンをクリックします。

> <img src="media/image24.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

25. **「Apply」ボタン**をクリックします。

> <img src="media/image25.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

26. 「Tenant settings will be applied within the next 15 minutes」という通知が表示されます。

> <img src="media/image26.png" style="width:6.26806in;height:3.80833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**まとめ**

このラボでは、Microsoft Fabric 管理ポータルでさまざまなInformation Protection設定を有効にして、Sensitivity labelの適用、継承、自動ラベル付け、管理者のオーバーライドをサポートしました。
