**Laboratório 13 – Implementar e gerenciar a retenção**

Você é Patti Fernandez, administradora de conformidade na Contoso Ltd. A empresa está reforçando sua estratégia de segurança de dados para reduzir a exposição a riscos relacionados a dados financeiros e comunicações confidenciais. Você foi solicitada a configurar soluções de retenção do Microsoft Purview que ofereçam suporte à preparação para auditorias, limitem a retenção desnecessária de dados e garantam a supervisão adequada de comunicações confidenciais.

**Tarefas**:

- Criar um rótulo de retenção

- Publicar um rótulo de retenção

- Criar uma política de rótulos de retenção com aplicação automática.

- Criar uma política de retenção estática

- Recuperar conteúdo do SharePoint

**Exercício 1 – Criar um rótulo de retenção**

Nesta tarefa, você criará um rótulo de retenção para dados financeiros confidenciais que precisam ser mantidos para fins de auditoria e investigação.

1.  Faça login na VM como administrador.

2.  No Microsoft Edge, acesse https://purview.microsoft.com e faça login como pattif@TenantName.

3.  Navegue até **Solutions \> Data Lifecycle Management.**

> <img src="media/image1.png" style="width:6.26806in;height:3.54653in" />

4.  Em seguida, selecione **Retention labels.**

> <img src="media/image2.png" style="width:6.26806in;height:3.54653in" />

5.  Na página **Labels**, selecione **Create a label.**

> <img src="media/image3.png" style="width:6.26806in;height:3.54653in" />

6.  Na página **Name your retention label**, insira:

    - **Name**: Sensitive Financial Records

    - **Description for users**: Use for financial files with sensitive data that must be retained for audit or security purposes.

    - **Description for admins**: Retains high-impact financial data for 5 years to support audits and security investigations.

7.  Selecione **Next**.

> <img src="media/image4.png" style="width:6.26806in;height:3.54653in" />

8.  Na página **Define label settings**, selecione **Retain items forever or for a specific period** e, em seguida, selecione **Next**.

> <img src="media/image5.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Define the retention period**, certifique-se de que estes valores estejam definidos no campo de configuração do período de retenção:

    - **Qual a duração do período?**: 5 Years

> <img src="media/image6.png" style="width:6.26806in;height:3.54653in" />

- **Quando deve começar o período?**: When items were modified.

> <img src="media/image7.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Selecione **Next**.

> <img src="media/image8.png" style="width:6.26806in;height:3.54653in" />

11. Na página **Choose what happens after the retention period,** selecione **Delete items automatically** e, em seguida, selecione **Next**.

> <img src="media/image9.png" style="width:6.26806in;height:3.54653in" />

12. Na página **Review and finish**, selecione **Create label**.

> <img src="media/image10.png" style="width:6.26806in;height:3.54653in" />

13. Na página **Your retention label is created**, selecione a opção **Do nothing** e, em seguida, selecione **Done**.

> <img src="media/image11.png" style="width:6.26806in;height:3.54653in" />

Você criou um rótulo de retenção que mantém o conteúdo financeiro por cinco anos e o exclui posteriormente para reduzir a exposição de dados.

**Exercício 2 – Publicar um rótulo de retenção**

Nesta tarefa, você publicará o rótulo de retenção para que os usuários possam aplicá-lo em serviços do Microsoft 365, como Exchange, SharePoint e OneDrive.

1.  No Microsoft Purview, navegue até **Solutions \> Data Lifecycle Management \> Retention labels.**

> <img src="media/image12.png" style="width:6.26806in;height:3.54653in" />

2.  Selecione a caixa ao lado do rótulo **Sensitive Financial Records** e, em seguida, selecione o ícone **Publish labels** para publicar este rótulo de retenção.

> <img src="media/image13.png" style="width:6.26806in;height:3.54653in" />

3.  Na página **Choose labels to publish**, verifique se o rótulo **Sensitive Financial Records** está selecionado e, em seguida, selecione **Next**.

> <img src="media/image14.png" style="width:6.26806in;height:3.54653in" />

4.  Na página **Policy Scope**, selecione **Next**.

> <img src="media/image15.png" style="width:6.26806in;height:3.54653in" />

5.  Na página **Choose the type of retention policy to create,** selecione **Static** e, em seguida, selecione **Next**.

> <img src="media/image16.png" style="width:6.26806in;height:3.54653in" />

6.  Na página **Choose where to publish labels**, selecione **Let me choose specific locations** e selecione:

    - Exchange mailboxes

    - SharePoint classic and communication sites

    - OneDrive accounts

    - Deselect all other locations

7.  Selecione **Next**.

> <img src="media/image17.png" style="width:6.26806in;height:3.54653in" />

8.  Em **Name your policy,** insira:

    - **Name**: Sensitive Financial Data Retention

    - **Description**: Makes the 'Sensitive Financial Records' label available to users in Exchange, SharePoint, and OneDrive.

9.  Selecione **Next**.

> <img src="media/image18.png" style="width:6.26806in;height:3.54653in" />

10. Em **Finish**, selecione **Submit**.

> <img src="media/image19.png" style="width:6.26806in;height:3.54653in" />

11. Na página **Your retention label was published**, selecione **Done**.

> <img src="media/image20.png" style="width:6.26806in;height:3.54653in" />

Você publicou o rótulo de retenção, disponibilizando-o para que os usuários o apliquem em serviços importantes do Microsoft 365.

**Exercício 3 – Criar uma política de rótulo de retenção com aplicação automática**

Nesta tarefa, você configurará uma política que aplica automaticamente um rótulo de retenção ao conteúdo que contém informações financeiras pessoais.

1.  No Microsoft Purview, navegue até **Solutions** \> **Data Lifecycle Management** \> **Policies** \> **Label policies**.

> <img src="media/image21.png" style="width:6.26806in;height:3.54653in" />

2.  Na página **Label policies**, selecione **Auto-apply a label** para iniciar a configuração do rótulo.

> <img src="media/image22.png" style="width:6.26806in;height:3.54653in" />

3.  Em **Let's get started page**, digite:

    - **Name**: Auto-apply Personal Financial PII

    - **Description**: Applies this label to personal financial data to help meet audit and investigation requirements. Retains content for 3 years.

4.  Selecione **Next**.

> <img src="media/image23.png" style="width:6.26806in;height:3.54653in" />

5.  Na página **Choose the type of content you want to apply this label to**, selecione **Apply label to content that contains sensitive info** e, em seguida, selecione **Next**.

> <img src="media/image24.png" style="width:6.26806in;height:3.54653in" />

6.  Na página **Content that contains sensitive info**, selecione a categoria **Financial**, depois selecione a regulamentação **U.S. Gramm-Leach-Bliley Act (GLBA)** e, em seguida, selecione **Next**.

> <img src="media/image25.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na página **Define content that contains sensitive info**, selecione **Next**.

> <img src="media/image26.png" style="width:6.26806in;height:3.54653in" />

8.  Na página **Policy Scope**, selecione **Next**.

> <img src="media/image27.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Choose the type of retention policy to create**, selecione **Static**. Selecione **Next**.

> <img src="media/image28.png" style="width:6.26806in;height:3.54653in" />

10. Na página **Choose where to publish labels**, selecione **Let me choose specific locations** e selecione:

    - Exchange mailboxes

    - SharePoint classic and communication sites

    - OneDrive accounts

    - Deselect all other locations

11. Selecione **Next**.

> <img src="media/image29.png" style="width:6.26806in;height:3.54653in" />

12. Na página **Choose a label to auto-apply**, selecione **Add label**.

> <img src="media/image30.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na janela suspensa **Choose a label**, selecione **Personal Financial PII** e, em seguida, selecione **Add**.

> <img src="media/image31.png" style="width:6.26806in;height:3.54653in" />

14. Na página **Choose a label to auto-apply**, selecione **Next**.

> <img src="media/image32.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. Na tela **Decide whether to test or run your policy**, selecione **Test the policy before running it** e, em seguida, selecione **Next**.

> <img src="media/image33.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. Na página **Review and finish**, selecione **Submit**.

> <img src="media/image34.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Em seguida, selecione **Done** na página **Your auto-labeling policy has been created.**

> <img src="media/image35.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você criou uma política de aplicação automática que identifica dados financeiros pessoais e aplica um rótulo de retenção automaticamente.

**Exercício 4 – Criar uma política de retenção estática**

Nesta tarefa, você criará uma política de retenção estática para o conteúdo do Microsoft Teams, a fim de ajudar a reduzir o risco de dados a longo prazo.

1.  No Microsoft Purview, navegue até **Solutions** \> **Data Lifecycle Management** \> **Policies** \> **Retention policies**.

> <img src="media/image36.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Na página **Retention policies**, selecione **New retention policy**.

> <img src="media/image37.png" style="width:6.26806in;height:3.54653in" />

3.  Na página **Name your retention policy**, insira:

    - **Name**: Teams Retention

    - **Description**: Retains Teams chats and channel messages for 3 years, then deletes them to reduce long-term data risk.

4.  Selecione **Next**.

> <img src="media/image38.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Na página **Policy Scope**, selecione **Next**.

> <img src="media/image39.png" style="width:6.26806in;height:3.54653in" />

6.  Na página **Choose the type of retention policy to create**, selecione **Static** e, em seguida, selecione **Next**.

> <img src="media/image40.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na página **Choose locations to apply the policy**, ative:

    - Teams channel messages

    - Teams chats

    - Leave all other locations disabled.

8.  Selecione **Next**.

> <img src="media/image41.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Decide if you want to retain content, delete it, or both**, certifique-se de que estes valores estejam definidos para a configuração de retenção:

    - Selecione **Retain items for a specific period**.

    - Em **Retain items for a specific period**, selecione **Custom** na lista suspensa.

> <img src="media/image42.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Altere o campo **years** para 3

<!-- -->

- **Start the retention period based on**: When items were last modified.

> <img src="media/image43.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- **At the end of the retention period**: Delete items automatically.

10. Selecione **Next**.

> <img src="media/image44.png" style="width:6.26806in;height:3.54653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

1.  Na página **Review and finish,** selecione **Submit**.

> <img src="media/image45.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Em seguida, selecione **Done** na página **You successfully created a retention policy**.

> <img src="media/image46.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você configurou uma política de retenção estática que mantém as mensagens do Teams por três anos antes de excluí-las automaticamente.

**Exercício 5 – Criar um escopo adaptativo**

Nesta tarefa, você definirá um escopo adaptativo que tem como alvo grupos do Microsoft 365 associados a funções de liderança e operações.

1.  No Microsoft Purview, acesse **Settings** \> **Roles and scopes** \> **Adaptive scopes**.

2.  Na página **Adaptive scopes**, selecione **+ Create scope**.

> <img src="media/image47.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na página **Name your adaptive policy scope,** insira:

    - **Name**: Leadership and Ops Groups

    - **Description**: Targets Leadership and Operations M365 groups with privileged access to sensitive data.

4.  Selecione **Next**.

> <img src="media/image48.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Na página **Assign admin unit,** selecione **Next**.

> <img src="media/image49.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Na página **What type of scope do you want to create?,** selecione **Microsoft 365 Groups** e, em seguida, selecione **Next**.

> <img src="media/image50.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na página **Create the query to define users**, na seção **User attributes**, certifique-se de que esses valores estejam selecionados para a configuração de atributos do usuário:

    - Selecione o **Attribute** no menu suspenso e, em seguida, selecione **Name.**

> <img src="media/image51.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Mantenha o valor padrão **is equal to no** campo seguinte.

- Insira Leadership como **Value.**

8.  Adicione um segundo atributo selecionando **+ Add attribute** na página **Create the query to define users**

> <img src="media/image52.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  No novo campo, abaixo do que acabamos de configurar, insira os seguintes valores:

    - Selecione o menu suspenso do operador de consulta e altere-o de **And** para **Or**.

> <img src="media/image53.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Selecione **Attribute** no menu suspenso e, em seguida, selecione **Name**.

> <img src="media/image54.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Deixe o valor padrão *i**s equal to*** no campo seguinte.

- Insira Operations como o **Value.**

10. Selecione **Next**.

> <img src="media/image55.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. Na página **Review and finish,** selecione **Submit**.

> <img src="media/image56.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. Após criar seu escopo adaptativo, selecione **Done** na página **Your scope was created.**

> <img src="media/image57.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você criou um escopo adaptável para oferecer suporte à retenção direcionada para grupos privilegiados na organização.

**Exercício 6 – Crie uma política de retenção adaptativa**

Nesta tarefa, você usará o escopo adaptativo que criou para configurar uma política de retenção para grupos do Microsoft 365 com responsabilidades confidenciais.

1.  No Microsoft Purview, navegue até **Solutions** \> **Data Lifecycle Management** \> **Policies** \> **Retention policies**.

> <img src="media/image58.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Na página **Retention policies**, selecione **+ New retention policy**.

> <img src="media/image59.png" style="width:6.27083in;height:3.54167in" />

3.  Na página **Name your retention policy,** insira:

    - **Name**: Privileged Group Retention

    - **Description**: Retains content from Leadership and Operations groups for 5 years to support audit and investigation.

4.  Selecione **Next**.

> <img src="media/image60.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Na página **Policy Scope**, selecione **Next**.

> <img src="media/image61.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Na página **Choose the type of retention policy to create,** selecione **Adaptive** e, em seguida, selecione **Next**.

> <img src="media/image62.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na página **Choose adaptive policy scopes and locations,** selecione **+ Add scopes**.

> <img src="media/image63.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  No painel suspenso **Choose adaptive policy scopes,** selecione a caixa de seleção **Leadership and Ops Groups** e, em seguida, selecione **Add** na parte inferior do painel.

> <img src="media/image64.png" style="width:6.27083in;height:3.54167in" />

9.  De volta à tela **Choose locations to apply the policy,** habilite:

    - Microsoft 365 Group mailboxes & sites

    - Leave all other locations disabled.

10. Selecione **Next**.

> <img src="media/image65.png" style="width:6.27083in;height:3.54167in" />

11. Na página **Decide if you want to retain content, delete it, or both,** certifique-se de que esses valores estejam definidos para a configuração de retenção:

    - Selecione **Retain items for a specific period**.

    - Em **Retain items for a specific period**, selecione **5 years** na lista suspensa.

    - **Start the retention period based on**: When items were last modified.

    - **At the end of the retention period**: Delete items automatically.

12. Selecione **Next**.

> <img src="media/image66.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na página **Review and finish,** selecione **Submit**.

> <img src="media/image67.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Selecione **Done** após a criação da política.

> <img src="media/image68.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você criou uma política de retenção que se aplica ao conteúdo pertencente a grupos privilegiados, mantendo-o por cinco anos antes de sua exclusão.

**Exercício 7 – Recuperar conteúdo do SharePoint**

Nesta tarefa, você simulará a restauração de um documento excluído de um site do SharePoint para validar suas opções de recuperação.

1.  Você ainda deve estar conectado à VM e logado como Patti Fernandez no Microsoft Purview.

2.  Selecione o iniciador de aplicativos (o ícone de grade) no canto superior esquerdo e, em seguida, selecione **More apps** no submenu.

> <img src="media/image69.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Selecione **SharePoint**.

> <img src="media/image70.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Na página inicial do SharePoint, pesquise por Benefits e selecione **Benefits @ Contoso** nos resultados da pesquisa.

> <img src="media/image71.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Na barra lateral esquerda, selecione **Documents**.

> <img src="media/image72.png" style="width:6.27083in;height:3.54167in" />

6.  Na página **Documents**, selecione a caixa de seleção do arquivo **Vacation Policies.pptx** e, em seguida, selecione **Delete** na barra de ações.

> <img src="media/image73.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na caixa de diálogo **Delete?,** selecione **Delete**.

> <img src="media/image74.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  Na barra lateral esquerda, selecione **Recycle bin**.

> <img src="media/image75.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Recycle bin**, clique com o botão direito do mouse em **Vacation Policies.pptx** e selecione **Restore**.

> <img src="media/image76.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Na barra lateral esquerda, selecione **Documents** e observe que o arquivo foi restaurado.

> <img src="media/image77.png" style="width:6.27083in;height:3.54167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você recuperou com sucesso um documento excluído de um site do SharePoint.
