**ラボ13 – Retentionの実装と管理**

あなたはContoso Ltd.のコンプライアンス管理者、パティ・フェルナンデスです。同社は、財務データと特権通信に関連するリスクを軽減するため、データセキュリティ戦略を強化しています。あなたは、監査への対応を支援し、不要なデータRetentionを制限し、機密性の高い通信を適切に監視するためのMicrosoft PurviewデータRetentionソリューションを構成するよう依頼されています。

**タスク**:

- Retention labelを作成する

- Retention labelを公開する

- 自動適用Retention labelポリシーを作成する

- 静的Retentionポリシーを作成する

- SharePoint コンテンツを回復する

**演習1 – Retention labelを作成する**

このタスクでは、監査と調査の目的でRetentionする必要がある機密の財務データのRetention labelを作成します。

1.  管理者として VM にログインします。

2.  Microsoft Edge で、 https://purview.microsoft.comに移動し、 pattif@TenantNameとしてサインインします。

3.  **\[Solutions\]** \> **\[Data Lifecycle Management\]**に移動します。

> <img src="media/image1.png" style="width:6.26806in;height:3.54653in" />

4.  次に、**Retention labelsを選択します**。

> <img src="media/image2.png" style="width:6.26806in;height:3.54653in" />

5.  **\[Labels\]ページ**で、 **\[Create a label\]を選択します**。

> <img src="media/image3.png" style="width:6.26806in;height:3.54653in" />

6.  **「Name your retention label」ページ**で、次のように入力します。

    - **Name**: Sensitive Financial Records

    - **Description for users**: Use for financial files with sensitive data that must be retained for audit or security purposes.

    - **Description for admins**: Retains high-impact financial data for 5 years to support audits and security investigations.

7.  **「Next」**を選択します。

> <img src="media/image4.png" style="width:6.26806in;height:3.54653in" />

8.  **\[Define label settings\]ページ**で、 **\[Retain items forever or for a specific period\]を選択し**、 **\[Next\]を選択します**。

> <img src="media/image5.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **「Define the period」ページ**で、Retention期間の構成入力に次の値が設定されていることを確認します。

    - **How long is the period?**: 5 Years

> <img src="media/image6.png" style="width:6.26806in;height:3.54653in" />

- **When should the period begin?**: When items were modified

> <img src="media/image7.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. **「Next」**を選択します。

> <img src="media/image8.png" style="width:6.26806in;height:3.54653in" />

11. **\[Choose what happens after the retention period**\] ページで、 **\[Delete items automatically\]を選択し**、 **\[Next\]を選択します**。

> <img src="media/image9.png" style="width:6.26806in;height:3.54653in" />

12. **\[Review and finish\]ページ**で、 **\[Create label\]を選択します**。

> <img src="media/image10.png" style="width:6.26806in;height:3.54653in" />

13. **\[Your retention label is created\]ページ**で、 **\[Do nothing\]**オプションを選択し、 **\[Done\]を選択します**。

> <img src="media/image11.png" style="width:6.26806in;height:3.54653in" />

データの露出を減らすために、財務コンテンツを 5 年間Retentionし、その後削除するRetention labelを作成しました。

**演習2 – Retention labelを公開する**

このタスクでは、Retention labelを公開して、ユーザーが Exchange、SharePoint、OneDrive などの Microsoft 365 サービスに適用できるようにします。

1.  Microsoft Purview で、 **\[Solutions\]** \> **\[Data Lifecycle Management\]** \> **\[Retention label\]に移動します**。

> <img src="media/image12.png" style="width:6.26806in;height:3.54653in" />

2.  **Sensitive Financial Records** **ラベルの**横にあるチェックボックスをオンにし、**Publish labelsアイコン**を選択してこのRetention labelを公開します。

> <img src="media/image13.png" style="width:6.26806in;height:3.54653in" />

3.  **\[Choose labels to publish\]ページ**で、 **\[Sensitive Financial Records\]**ラベルが選択されていることを確認し、 **\[Next\]を選択します**。

> <img src="media/image14.png" style="width:6.26806in;height:3.54653in" />

4.  **\[Policy scope\]**ページで**\[Next\]を選択します**。

> <img src="media/image15.png" style="width:6.26806in;height:3.54653in" />

5.  **Choose the type of retention policy to create** ページで、 **\[Static\]を選択し**、 **\[Next\]を選択します**。

> <img src="media/image16.png" style="width:6.26806in;height:3.54653in" />

6.  **\[Choose where to publish labels\]**ページで、 **\[Let me choose specific locations\] を選択し**、以下を選択します。

    - Exchangeメールボックス

    - SharePoint クラシックとコミュニケーション サイト

    - OneDriveアカウント

    - 他の場所の選択をすべて解除

7.  **「Next」**を選択します。

> <img src="media/image17.png" style="width:6.26806in;height:3.54653in" />

8.  **Name your policy** に以下を入力します。

    - **Name**: Sensitive Financial Data Retention

    - **Description**: Makes the 'Sensitive Financial Records' label available to users in Exchange, SharePoint, and OneDrive.

9.  **「Next」**を選択します。

> <img src="media/image18.png" style="width:6.26806in;height:3.54653in" />

10. **\[Finish\]ページ**で、 **\[Submit\]を選択します**。

> <img src="media/image19.png" style="width:6.26806in;height:3.54653in" />

11. **\[Your retention label was published\]ページ**で、 **\[Done\]を選択します**。

> <img src="media/image20.png" style="width:6.26806in;height:3.54653in" />

Retention labelを公開し、ユーザーが主要な Microsoft 365 サービスに適用できるようにしました。

**演習3 – 自動適用Retention labelポリシーを作成する**

このタスクでは、個人の財務情報を含むコンテンツにRetention labelを自動的に適用するポリシーを構成します。

1.  Microsoft Purview で、 **\[Solutions** \> **Data Lifecycle Management** \> **Policies** \> **Label policies\]に移動します**。

> <img src="media/image21.png" style="width:6.26806in;height:3.54653in" />

2.  **\[Label policies\]ページ**で、 **\[Auto-apply a label\]を選択して**、ラベルの構成を開始します。

> <img src="media/image22.png" style="width:6.26806in;height:3.54653in" />

3.  **「Let's get started page」ページ**で、次のように入力します。

    - **Name**: Auto-apply Personal Financial PII

    - **Description**: Applies this label to personal financial data to help meet audit and investigation requirements. Retains content for 3 years.

4.  **「Next」**を選択します。

> <img src="media/image23.png" style="width:6.26806in;height:3.54653in" />

5.  **\[Choose the type of content you want to apply this label to\]ページ**で、 **\[Apply label to content that contains sensitive info\]を選択し**、 **\[Next\]を選択します**。

> <img src="media/image24.png" style="width:6.26806in;height:3.54653in" />

6.  **\[Content that contains sensitive info\]ページ**で、 **\[Financial\]**カテゴリを選択し、**U.S. Gramm-Leach-Bliley Act (GLBA)** 規制を選択して、 **\[Next\]を選択します**。

> <img src="media/image25.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **\[Define content that contains sensitive info\]ページ**で、 **\[Next\]を選択します**。

> <img src="media/image26.png" style="width:6.26806in;height:3.54653in" />

8.  **\[Policy Scope\]ページ**で、 **\[Next\]を選択します**。

> <img src="media/image27.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **Choose the type of retention policy to createページ**で、**Staticを選択します**。**Nextを選択します**。

> <img src="media/image28.png" style="width:6.26806in;height:3.54653in" />

10. **\[Choose where to publish labels\]**ページで、 **\[Let me choose specific locations\] を選択し**、以下を選択します。

    - Exchangeメールボックス

    - SharePoint クラシックとコミュニケーション サイト

    - OneDriveアカウント

    - 他の場所の選択をすべて解除

11. **「Next」**を選択します。

> <img src="media/image29.png" style="width:6.26806in;height:3.54653in" />

12. **\[Choose a label to auto-apply\]ページ**で、 **\[Add label\]を選択します**。

> <img src="media/image30.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. **\[Choose a label\]フライアウト**で、 **\[Personal Financial PII\]を選択し**、 **\[Add\]を選択します**。

> <img src="media/image31.png" style="width:6.26806in;height:3.54653in" />

14. **\[Choose a label to auto-apply\]ページ**に戻り、 **\[Next\]を選択します**。

> <img src="media/image32.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. **\[Decide whether to test or run your policy**\] で、 **\[Test the policy before running it\]を選択し**、 **\[Next\]を選択します**。

> <img src="media/image33.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. **\[Review and Finish\]ページ**で、 **\[Submit\]を選択します**。

> <img src="media/image34.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. 次に、 **「Your auto-labeling policy has been created** **」ページ**で**「Done」を選択します**。

> <img src="media/image35.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

個人の財務データを識別し、Retention labelを自動的に適用する自動適用ポリシーを作成しました。

**演習4 – 静的Retention policiesを作成する**

このタスクでは、長期的なデータ リスクを軽減するために、Microsoft Teams コンテンツの静的Retention policiesを作成します。

1.  Microsoft Purview で、 **\[Solutions** \> **Data Lifecycle Management** \> **Policies** \> **Retention policies\]に移動します**。

> <img src="media/image36.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  **\[Retention policies\]ページ**で、 **\[New Retention policies\]を選択します**。

> <img src="media/image37.png" style="width:6.26806in;height:3.54653in" />

3.  **「Name your Retention policies」ページ**で、次のように入力します。

    - **Name**: Teams Retention

    - **Description**: Retains Teams chats and channel messages for 3 years, then deletes them to reduce long-term data risk.

4.  **「Next」**を選択します。

> <img src="media/image38.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  **\[Policy scope\]ページ**で、 **\[Next\]を選択します**。

> <img src="media/image39.png" style="width:6.26806in;height:3.54653in" />

6.  **\[Choose the type of retention policy to create\]ページ**で、 **\[Static\]を選択し**、 **「Next」を選択します**。

> <img src="media/image40.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **\[Choose locations to apply the policy\]ページ**で、以下を有効にします。

    - Teams チャネル メッセージ

    - Teamsチャット

    - その他の場所はすべて無効のままにします。

8.  **「Next」**を選択します。

> <img src="media/image41.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **Decide if you want to retain content, delete it, or both** ページで、保持構成に次の値が設定されていることを確認します。

    - **\[Retain items for a specific period\]**を選択します。

    - **「Retain items for a specific period」**の下で、ドロップダウンリストから**「Custom」を選択します。**

> <img src="media/image42.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- 年フィールドを3に変更します

- **Start the retention period based on**: When items were last modified

> <img src="media/image43.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- **At the end of the retention period**: Delete items automatically

10. **「Next」**を選択します。

> <img src="media/image44.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. **\[Review and finish\]**ページで**\[Submit\]を選択します**。

> <img src="media/image45.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. 次に、 **\[You successfully created a retention policy\]ページ**で**\[Done\]を選択します**。

> <img src="media/image46.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Teams メッセージを 3 年間保持してから自動的に削除する静的Retention policiesを構成しました。

**演習5 – 適応型スコープを作成する**

このタスクでは、リーダーシップと運用の役割に関連付けられた Microsoft 365 グループを対象とする適応型スコープを定義します。

1.  Microsoft Purview で、 **\[Settings** \> **Roles and scopes** \> **Adaptive scopes\] を選択します**。

2.  **「Adaptive scopes」**ページで、 **「+Create scope」を選択します**。

> <img src="media/image47.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  **「Name your adaptive policy scope」**ページで、次のように入力します。

    - **Name**: Leadership and Ops Groups

    - **Description**: Targets Leadership and Operations M365 groups with privileged access to sensitive data.

4.  **「Next」**を選択します。

> <img src="media/image48.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  **Assign admin unit** ページで、 **「Next」を選択します**。

> <img src="media/image49.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  **\[What type of scope do you want to create?\]**ページで**\[Microsoft 365 Groups\]を選択し**、 **「Next」を選択します**。

> <img src="media/image50.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **「Create the query to define users」**ページの**「User attributes」セクション**で、ユーザー属性の構成に次の値が選択されていることを確認します。

    - **Attribute**ドロップダウンを選択し、Nameを選択します。

> <img src="media/image51.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- 次のフィールドの値はデフォルト**のままにしておきます**

- LeadershipをValueとして入力します。

8.  **「Create the query to define users」ページ**で**「+ Add attribute」**を選択して、2 番目の属性を追加します。

> <img src="media/image52.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  先ほど設定したフィールドの下の新しいフィールドで、次の値を設定します。

    - クエリ演算子のドロップダウンを選択し、 And から**Orに更新します**。

> <img src="media/image53.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- **Attribute**ドロップダウンを選択し、 **Nameを選択します**。

> <img src="media/image54.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- 次のフィールドの値はデフォルト**のままにしておきます**

- **Value**としてOperationsを入力します

10. **「Next」**を選択します。

> <img src="media/image55.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. **\[Review abd finish\]**ページで**\[Submit\]を選択します**。

> <img src="media/image56.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. Adaptive scopeが作成されたら、\[**Your scope was created\]ページ**で**\[Done\]を選択します**。

> <img src="media/image57.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

組織内の特権グループのターゲット保持をサポートするAdaptive scopeを作成しました。

**演習6 – Adaptive Retention policiesを作成する**

このタスクでは、作成したAdaptive scopeを使用して、機密性の高い責任を負う Microsoft 365 グループのRetention policiesを構成します。

1.  Microsoft Purviewで、**Solutions** \> **Data Lifecycle Management** \> **Policies** \>  **Retention policiesに移動します。** <img src="media/image58.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  **\[Retention policies\]ページ**で、 **\[+New Retention policies\]を選択します**。

> <img src="media/image59.png" style="width:6.26806in;height:3.54653in" />

3.  **「Name your retention policy」**ページで次のように入力します。

    - **Name**: Privileged Group Retention

    - **Description**: Retains content from Leadership and Operations groups for 5 years to support audit and investigation.

4.  **「Next」**を選択します。

> <img src="media/image60.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  **\[Policy Scope\]**ページで**「Next」を選択します**。

> <img src="media/image61.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  **Choose the type of retention policy to create** ページで、Adaptive**を選択し**、Next**を選択します**。

> <img src="media/image62.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **\[Choose adaptive policy scopes and locations\]**ページで、 **\[+Add scopes\]を選択します**。

> <img src="media/image63.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  **\[Choose adaptive policy scopes\]フライアウト パネル**で**、\[Leadership and Ops Groups** **\]**のチェック ボックスをオンにし、パネルの下部にある**\[Add\]**を選択します。

> <img src="media/image64.png" style="width:6.26806in;height:3.54653in" />

9.  **Choose locations to apply the policy** に戻り、以下を有効にします。

    - Microsoft 365 Group mailboxes & sites

    - その他の場所はすべて無効のままにします。

10. **「Next」**を選択します。

> <img src="media/image65.png" style="width:6.26806in;height:3.54653in" />

11. **Decide if you want to retain content, delete it, or both** ページで、保持構成に次の値が設定されていることを確認します。

    - **\[Retain items for a specific period\]**を選択します。

    - **「Retain items for a specific period」**の下で、ドロップダウンリストから**5 yearsを選択します。**

    - **Start the retention period based on**: When items were last modified

    - **At the end of the retention period**: Delete items automatically

12. **「Next」**を選択します。

> <img src="media/image66.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. **\[Review and finish\]**ページで**\[Submit\]を選択します**。

> <img src="media/image67.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. ポリシーが作成されたら、 **\[Done\]**を選択します。

> <img src="media/image68.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

特権グループが所有するコンテンツに適用され、削除されるまで 5 年間保持されるRetention policiesを作成しました。

**演習7 – SharePointコンテンツの回復**

このタスクでは、SharePoint サイトから削除されたドキュメントの復元をシミュレートして、回復オプションを検証します。

1.  VM にログインしたまま、Microsoft Purview で Patti Fernandez としてログインしている必要があります。

2.  左上隅にあるアプリ ランチャー (グリッド アイコン) を選択し、サブメニューから \[**More apps\]を選択します。**

> <img src="media/image69.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  **SharePoint**を選択します。

> <img src="media/image70.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  SharePoint ランディング ページで「Benefits」を検索し、検索結果から**「Benefits @ Contoso」**を選択します。

> <img src="media/image71.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  左側のサイドバーで**\[Documents\]を選択します**。

> <img src="media/image72.png" style="width:6.26806in;height:3.54653in" />

6.  **\[Documents\]ページ**で、 **Vacation Policies.pptx**のチェックボックスをオンにし、アクション バーから**\[Delete\]を選択します。**

> <img src="media/image73.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  **\[Delete?\]ダイアログ**で、 **\[Delete\]を選択します**。

> <img src="media/image74.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  左側のサイドバーで、 **\[Recycle bin\]を選択します**。

> <img src="media/image75.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  **\[Recycle bin\]ページ**で、 **Vacation Policies.pptx**を右クリックし、 **\[Restore\]を選択します**。

> <img src="media/image76.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. 左側のサイドバーで**「Documents」を選択し**、ファイルが復元されていることを確認します。

> <img src="media/image77.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

削除されたドキュメントを SharePoint サイトから正常に復元しました。
