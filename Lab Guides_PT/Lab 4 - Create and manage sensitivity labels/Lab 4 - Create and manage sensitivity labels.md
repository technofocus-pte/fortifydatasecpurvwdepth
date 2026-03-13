**Laboratório 4 – Criar e gerenciar rótulos de confidencialidade**

**Introdução**

Patti Fernandez, administradora de segurança de informações da Contoso Ltd., está implementando uma estrutura moderna de rótulos de confidencialidade para fortalecer a proteção de dados em toda a organização. Patti cria e publica grupos de rótulos de confidencialidade e rótulos para classificar e proteger o conteúdo, incluindo criptografia, rotulagem automática e Double Key Encryption (DKE). Patti também integrará o Microsoft Purview ao Microsoft Defender for Cloud Apps para estender os controles de proteção de dados aos arquivos armazenados em locais na nuvem.

**Objetivos:**

- Habilitar suporte para rótulos de confidencialidade

- Criar um grupo de rótulos

- Criar um rótulo secundário

- Publicar rótulos

- Configurar a rotulagem automática

- Criar e publicar um rótulo DKE para conteúdo confidencial

- Habilitar a integração do Microsoft Purview no Defender for Cloud Apps

- Criar uma política de arquivos para rotular arquivos compartilhados externamente

**Exercício 1 – Habilitar suporte para rótulos de confidencialidade**

Nesta tarefa, você habilitará a coautoria para rótulos de confidencialidade, o que também habilita rótulos de confidencialidade para arquivos no SharePoint e no OneDrive.

1.  Você ainda deve estar conectado à VM usando a conta de **administrador**.

2.  Abra o **Microsoft Edge**, navegue até https://purview.microsoft.com e faça login no Microsoft Purview como Patti Fernandes.

3.  Na navegação à esquerda, selecione **Settings \> Information Protection**.

> <img src="media/image1.png" style="width:6.26806in;height:3.46111in" />

4.  Na página **Information Protection settings**, certifique-se de estar na guia **Co-authoring for files with sensitivity labels**.

5.  Selecione a caixa de seleção **Turn on co-authoring for files with sensitivity labels**.

> <img src="media/image2.png" style="width:6.26806in;height:3.53472in" />

6.  Selecione **Apply** na parte inferior da tela.

> <img src="media/image3.png" style="width:6.26806in;height:3.53472in" />

Você habilitou com sucesso o suporte a rótulos de confidencialidade para arquivos no SharePoint e OneDrive.

**Exercício 2 - Trabalhando com rótulos de confidencialidade**

**Tarefa 1 – Criar um grupo de rótulos**

Nesta tarefa, você criará um grupo de rótulos para organizar rótulos de confidencialidade internos. Os grupos de rótulos funcionam como recipientes para rótulos relacionados, como classificações de departamento ou unidade de negócios.

1.  No **Microsoft Edge**, navegue até https://purview.microsoft.com.

2.  No portal Microsoft Purview, selecione **Solutions** na barra lateral esquerda e, em seguida, selecione **Information Protection**.

> <img src="media/image4.png" style="width:6.26806in;height:3.53472in" />

3.  Na página **Microsoft Information Protection**, na barra lateral esquerda, selecione **Sensitivity labels**.

> <img src="media/image5.png" style="width:6.26806in;height:3.53472in" />

4.  Na página **Sensitivity labels**, selecione **+ Create \> Label group**.

> <img src="media/image6.png" style="width:6.26806in;height:3.53472in" />

5.  A configuração **New label group** será iniciada. Em **Provide basic details for this label group**, insira:

    - **Name**: Internal

    - **Display name**: Internal

    - **Description for users**: Internal sensitivity label.

    - **Description for admins**: Internal sensitivity label group for Contoso.

6.  Selecione **Next**.

> <img src="media/image7.png" style="width:6.26806in;height:3.53472in" />

7.  Na página **Review your settings and finish**, selecione **Create label group**.

> <img src="media/image8.png" style="width:6.26806in;height:3.53472in" />

8.  Na página **Your label group was created successfully**, selecione **Don't create a label yet** e, em seguida, selecione **Done**.

> <img src="media/image9.png" style="width:6.26806in;height:3.53472in" />

Você criou um grupo de rótulos para uso interno. Esse grupo ajuda a gerenciar rótulos relacionados para departamentos ou categorias de dados específicas.

**Tarefa 2 – Criar um rótulo secundário**

Agora que você criou um grupo de rótulos, você adicionará um rótulo secundário para conteúdo relacionado a RH. Esse rótulo aplica criptografia e marcações de conteúdo para proteger dados de RH contra acesso não autorizado.

1.  Na página **Sensitivity labels**, localize o grupo de rótulos de confidencialidade **Internal**. Selecione as reticências verticais (**…**) ao lado dele e, em seguida, selecione **+ Create label in group** no menu suspenso.

> <img src="media/image10.png" style="width:6.26806in;height:3.53472in" />

2.  O assistente **New sensitivity label** será iniciado. Na página **Provide basic details for this label**, insira:

    - **Name**: Employee data (HR)

    - **Display name**: Employee data (HR)

    - **Description for users**: This HR label is the default label for all specified documents in the HR Department.

    - **Description for admins**: This label is created in consultation with Ms. Jones (Head of the HR department). Contact her if you need to change the label settings.

3.  Selecione **Next**.

> <img src="media/image11.png" style="width:6.26806in;height:3.53472in" />

4.  Na página **Define the scope for this label**, selecione **Files** e **Emails**. Se a caixa de seleção **Meetings** estiver selecionada, certifique-se de desmarcá-la.

5.  Selecione **Next**.

> <img src="media/image12.png" style="width:6.26806in;height:3.53472in" />

6.  Na página **Choose protection settings for labeled items**, selecione as opções **Control access** e **Apply content marking**, e depois selecione **Next**.

> <img src="media/image13.png" style="width:6.26806in;height:3.53472in" />

7.  Na página **Access control**, selecione **Configure access control settings**.

8.  Configure as configurações de criptografia com as seguintes opções:

    - **Assign permissions now or let users decide?**: Assign permissions now

    - **User access to content expires**: Never

    - **Allow offline access**: Only for a number of days

    - **Users have offline access to the content for this many days**: 15<img src="media/image14.png" style="width:6.26806in;height:3.53472in" />

    - Selecione o link **Assign permissions**. No painel **Assign permissions**, selecione **+ Add any authenticated users** e, em seguida, selecione **Save** para aplicar essa configuração.<img src="media/image14.png" style="width:6.26806in;height:3.53472in" /><img src="media/image15.png" style="width:6.26806in;height:3.53472in" />

9.  Na página **Access control**, selecione **Next**.

> <img src="media/image16.png" style="width:6.26806in;height:3.53472in" />

10. Na página **Content marking**, selecione o botão de alternância para habilitar **Content marking**.

> <img src="media/image17.png" style="width:6.26806in;height:3.53472in" />

11. Para cada um dos seguintes tipos de marcação, marque a caixa de seleção e selecione o ícone de edição para inserir o texto:

| **Tipo de marcação** | **Texto**            |
|----------------------|----------------------|
| Add a watermark      | INTERNAL USE ONLY    |
| Add a header         | Internal Document    |
| Add a footer         | Contoso Confidential |

12. Selecione **Next**.

> <img src="media/image18.png" style="width:6.26806in;height:3.53472in" />

13. Na página **Auto-labeling for files and emails**, selecione **Next**.

> <img src="media/image19.png" style="width:6.26806in;height:3.53472in" />

14. Na página **Define protection settings for groups and sites**, selecione **Next**.

> <img src="media/image20.png" style="width:6.26806in;height:3.53472in" />

15. Na página **Review your settings and finish**, selecione **Create label**.

> <img src="media/image21.png" style="width:6.26806in;height:3.53472in" />

16. Na página **Your sensitivity label was created**, selecione **Don't create a policy yet** e, em seguida, selecione **Done**.

> <img src="media/image22.png" style="width:6.26806in;height:3.53472in" />

Você criou um rótulo secundário dentro do grupo interno. O rótulo aplica criptografia e marcações de conteúdo a documentos de RH, tornando os dados sensíveis fáceis de identificar e protegidos por política.

**Tarefa 3 – Publicar rótulos**

Em seguida, você publicará o rótulo de RH do grupo Internal para que os usuários do departamento de RH possam aplicá-lo aos seus documentos.

1.  No **Microsoft Edge**, a guia do portal **Microsoft Purview** ainda deve estar aberta. Caso contrário, navegue até https://purview.microsoft.com \> **Solutions** \> **Information Protection** \> **Sensitivity labels**.

2.  Na página **Sensitivity labels**, selecione **Publish labels**.

> <img src="media/image23.png" style="width:6.26806in;height:3.53472in" />

3.  A configuração dos rótulos de confidencialidade será iniciada.

4.  Na página **Choose sensitivity labels to publish**, selecione o link **Choose sensitivity labels to publish**.

> <img src="media/image24.png" style="width:6.26806in;height:3.53472in" />

5.  No painel **Sensitivity labels to publish**, selecione a caixa de seleção **Internal/Employee data (HR)** e, em seguida, selecione **Add** na parte inferior do painel.

> <img src="media/image25.png" style="width:6.26806in;height:3.53472in" />

6.  De volta à página **Choose sensitivity labels to publish**, selecione **Next**.

> <img src="media/image26.png" style="width:6.26806in;height:3.53472in" />

7.  Na página **Assign admin units**, selecione **Next**.

> <img src="media/image27.png" style="width:6.26806in;height:3.53472in" />

8.  Na página **Publish to users and groups**, selecione **Next**.

> <img src="media/image28.png" style="width:6.26806in;height:3.53472in" />

9.  Na página **Policy settings**, selecione **Next**.

> <img src="media/image29.png" style="width:6.26806in;height:3.53472in" />

10. Na página **Default settings for documents**, selecione **Next**.

> <img src="media/image30.png" style="width:6.26806in;height:3.53472in" />

11. Na página **Default settings for emails**, selecione **Next**.

> <img src="media/image31.png" style="width:6.26806in;height:3.53472in" />

12. Na página **Default settings for meetings and calendar events**, selecione **Next**.

> <img src="media/image32.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na página **Default settings for Fabric and Power BI content**, selecione **Next**.

> <img src="media/image33.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Na página **Name your policy**, insira:

    - **Name**: Internal HR employee data

    - **Enter a description for your sensitivity label policy**: This HR label is to be applied to internal HR employee data.

15. Selecione **Next**.

> <img src="media/image34.png" style="width:6.26806in;height:3.53472in" />

16. Na página **Review and finish**, selecione **Submit**.

> <img src="media/image35.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Na página **New policy created**, selecione **Done** para concluir a publicação da política de rótulos.

> <img src="media/image36.png" style="width:6.26806in;height:3.53472in" />

Você publicou o grupo de rótulos interno e seu rótulo de RH para que os usuários possam aplicá-los aos documentos de RH. Pode levar até 24 horas para que a política seja propagada pelos serviços.

**Tarefa 4 – Configurar rotulagem automática**

1.  No portal **Microsoft Purview**, selecione **Solutions \> Information Protection \> Sensitivity labels**.

2.  Na página **Sensitivity labels**, localize o grupo de rótulos de confidencialidade **Internal**. Selecione as reticências verticais (**...**) e, em seguida, selecione **+ Create label in group** no menu suspenso.

> <img src="media/image37.png" style="width:6.26806in;height:3.53472in" />

3.  Na página **Provide basic details for this label**, insira:

| **Detalhes** | **Texto** |
|----|----|
| **Name** | Financial Data |
| **Display name** | Financial Data |
| **Description for users** | This content contains financial data that must be labeled and protected. |
| **Description for admins** | This label is used for content that includes sensitive financial identifiers. |

4.  Selecione **Next**.

> <img src="media/image38.png" style="width:6.26806in;height:3.53472in" />

5.  Na página **Define the scope for this label**, selecione **Files and Emails**. Se a caixa de seleção **Meetings** estiver selecionada, certifique-se de desmarcá-la.

6.  Selecione **Next**.

> <img src="media/image39.png" style="width:6.26806in;height:3.53472in" />

7.  Na página **Choose protection settings for labeled items**, selecione **Next**.

> <img src="media/image40.png" style="width:6.26806in;height:3.53472in" />

8.  Na página **Auto-labeling for files and emails**, defina **Auto-labeling for files and emails** como habilitado.

> <img src="media/image41.png" style="width:6.26806in;height:3.53472in" />

9.  Na seção **Detect content that matches these conditions**, selecione **+ Add condition \> Content contains**.

> <img src="media/image42.png" style="width:6.26806in;height:3.53472in" />

10. Na seção **Content contains**, selecione **Add \> Sensitive info types**.

> <img src="media/image43.png" style="width:6.26806in;height:3.53472in" />

11. No painel **Sensitive info types**, pesquise e selecione os seguintes tipos de informações confidenciais:

    - Credit Card Number

    - ABA Routing Number

    - SWIFT Code

12. Selecione **Add**.

> <img src="media/image44.png" style="width:6.26806in;height:3.53472in" />

13. De volta à página **Auto-labeling for files and emails**, selecione **Next**.

> <img src="media/image45.png" style="width:6.26806in;height:3.53472in" />

14. Na página **Define protection settings for groups and sites**, selecione **Next**.

> <img src="media/image46.png" style="width:6.26806in;height:3.53472in" />

15. Na página **Review your settings and finish**, selecione **Create label**.

> <img src="media/image47.png" style="width:6.26806in;height:3.53472in" />

16. Na página **Your sensitivity label was created**, selecione **Automatically apply label to sensitive content** e, em seguida, selecione **Done**.

> <img src="media/image48.png" style="width:6.26806in;height:3.53472in" />

17. Na página **Create auto-labeling policy**, selecione **Review policy**.

> <img src="media/image49.png" style="width:6.26806in;height:3.53472in" />

18. Na página **Name your auto-labeling policy**, mantenha o valor padrão e selecione **Next**.

> <img src="media/image50.png" style="width:6.26806in;height:3.53472in" />

19. Na página **Choose a label to auto-apply**, verifique se o rótulo *Internal/Financial Data* está selecionado e selecione **Next**.

> <img src="media/image51.png" style="width:6.26806in;height:3.53472in" />

20. Na página **Assign admin units**, selecione **Next**.

> <img src="media/image52.png" style="width:6.26806in;height:3.53472in" />

21. Na página **Choose locations where you want to apply the label**, selecione as opções para:

    - Exchange email

    - SharePoint sites

    - OneDrive accounts

22. Selecione **Next**.

> <img src="media/image53.png" style="width:6.26806in;height:3.53472in" />

23. Na página **Set up common or advanced rules**, mantenha **Common rules** selecionado e selecione **Next**.

> <img src="media/image54.png" style="width:6.26806in;height:3.53472in" />

24. Na página **Define rules for content in all locations**, expanda a regra *Financial Data* para confirmar que as regras esperadas estão definidas e selecione **Next**.

> <img src="media/image55.png" style="width:6.26806in;height:3.53472in" />

25. Na página **Additional settings for email**, selecione **Next**..

> <img src="media/image56.png" style="width:6.26806in;height:3.53472in" />

26. Na página **Decide if you want to test out the policy now or later**, selecione **Run policy in simulation mode** e marque a caixa **Automatically turn on policy if not modified after 7 days in simulation.**

> <img src="media/image57.png" style="width:6.26806in;height:3.53472in" />

27. Selecione **Next**.

> <img src="media/image58.png" style="width:6.26806in;height:3.53472in" />

28. Na página **Review and finish**, selecione **Create policy**.

> <img src="media/image59.png" style="width:6.26806in;height:3.53472in" />

29. Na página **Your auto-labeling policy was created**, selecione **Done**..

Você criou um rótulo secundário para dados financeiros e configurou uma política de rotulagem automática que detecta e rotula o conteúdo que contém informações financeiras.

**Tarefa 5 – Criar e publicar um rótulo DKE para conteúdo confidencial**

Em seguida, você criará um rótulo secundário no grupo interno que utiliza Double Key Encryption (DKE) e marca d’água dinâmica para proteger conteúdo jurídico confidencial.

1.  No **Microsoft Edge**, navegue até https://purview.microsoft.com e entre no portal Microsoft Purview como **Patti Fernandes**.

2.  No portal **Microsoft Purview**, selecione **Solutions \> Information Protection \> Sensitivity labels**.

3.  Na página **Sensitivity labels**, localize o grupo de rótulos de confidencialidade **Internal**. Selecione as reticências verticais (**...**) e selecione **+ Create label in group** no menu suspenso.

> <img src="media/image60.png" style="width:6.26806in;height:3.53472in" />

4.  Na página **Provide basic details for this label**, insira:

| **Detalhes** | **Texto** |
|----|----|
| **Name** | Confidential Legal |
| **Display name** | Confidential Legal |
| **Description for users** | Use this label for highly sensitive legal content that must be encrypted using Double Key Encryption. |
| **Description for admins** | Label configured with DKE and dynamic watermarking for highly sensitive legal content. |

5.  Selecione **Next**.

> <img src="media/image61.png" style="width:6.26806in;height:3.53472in" />

6.  Na página **Define the scope for this label**, selecione **Files and Emails**. Certifique-se de que **Meetings** esteja desmarcado e selecione **Next**.

> <img src="media/image62.png" style="width:6.26806in;height:3.53472in" />

7.  Na página **Choose protection settings for the types of items you selected**, selecione **Control access** e selecione **Next**.

> <img src="media/image63.png" style="width:6.26806in;height:3.53472in" />

8.  Na página **Access control**, selecione **Configure access control settings**.

> <img src="media/image64.png" style="width:6.26806in;height:3.53472in" />

9.  Defina as configurações de criptografia com as seguintes opções:

    - **Assign permissions now or let users decide?**: Assign permissions now

    - **User access to content expires**: A number of days after label is applied

    - **Access expires this many days after the label is applied**: 5

    - **Allow offline access**: Never

    - Selecione o link **Assign permissions**. No painel **Assign permissions**, selecione **+ Add users or groups**.

> <img src="media/image65.png" style="width:6.26806in;height:3.53472in" />

- No painel **Add users or groups**, pesquise e selecione Legal Team e Patti Fernandes, depois selecione **Add**.

> <img src="media/image66.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Na página **Assign permissions**, selecione **Save**.

> <img src="media/image67.png" style="width:6.26806in;height:3.53472in" />

10. De volta à página **Access control**, marque a caixa **Use dynamic watermarking** e selecione **Customize text (optional)**.

> <img src="media/image68.png" style="width:6.26806in;height:3.53472in" />

11. Na página **Add custom text to watermark (optional)**, insira **Confidential** e selecione **UPN** e **Timestamp**.

12. Selecione **Save** na parte inferior do painel lateral.

> <img src="media/image69.png" style="width:6.26806in;height:3.53472in" />

13. De volta à página **Access control**, marque a caixa de seleção **Use Double Key Encryption** e insira https://testingdke1.azurewebsites.net/Test como a URL do serviço de Double Key Encryption.

14. Selecione **Next**.

> <img src="media/image70.png" style="width:6.26806in;height:3.53472in" />

15. Na página **Auto-labeling for files and emails**, selecione **Next**.

> <img src="media/image71.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. Na página **Define protection settings for groups and sites**, selecione **Next**.

> <img src="media/image46.png" style="width:6.26806in;height:3.53472in" />

17. Na página **Review your settings and finish**, selecione **Create label**.

> <img src="media/image72.png" style="width:6.26806in;height:3.53472in" />

18. Na página **Your sensitivity label was created**, selecione **Publish label to users' apps** e, em seguida, selecione **Done**.

> <img src="media/image73.png" style="width:6.26806in;height:3.53472in" />

19. Na página lateral **Publish label**, selecione **Create new label policy**.

> <img src="media/image74.png" style="width:6.26806in;height:3.53472in" />

20. Na página **Choose sensitivity labels to publish**, selecione **Choose sensitivity labels to publish** e adicione **Internal/Confidential Legal label**, em seguida selecione **Add**.

> <img src="media/image75.png" style="width:6.26806in;height:3.53472in" />

21. Selecione **Next.**

> <img src="media/image76.png" style="width:6.26806in;height:3.53472in" />

22. Na página **Assign admin units**, selecione **Next**.

> <img src="media/image77.png" style="width:6.26806in;height:3.53472in" />

23. Na página **Publish to users and groups**, mantenha a opção padrão selecionada e selecione **Next**.

> <img src="media/image78.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

24. Na página **Policy settings**, marque a caixa de seleção **Users must provide a justification to remove a label or lower its classification** e selecione **Next**.

> <img src="media/image79.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

25. Na página **Default settings for documents**, selecione **Next**.

> <img src="media/image80.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

26. Na página **Default settings for emails**, selecione **Next**.

> <img src="media/image81.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

27. Na página **Default settings for meetings and calendar events**, selecione **Next**.

> <img src="media/image82.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

28. Na página **Default settings for Fabric and Power BI content**, selecione **Next**.

> <img src="media/image83.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

29. Na página **Name your policy**, insira:

    - **Name**: Confidential Legal

    - **Description**: Enables manual use of the DKE label for confidential content accessible by Legal.

30. Selecione **Next**.

> <img src="media/image84.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

31. Na página **Review and finish**, selecione **Submit**.

> <img src="media/image85.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

32. Na página **New policy created**, selecione **Done**.

> <img src="media/image86.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você criou e publicou um rótulo secundário usando Double Key Encryption (DKE) e marca d’água dinâmica. Esse rótulo restringe o acesso a usuários autorizados e exige justificativa para rebaixamento da classificação.

**Exercício 3 – Política de arquivos usando rótulos de confidencialidade com o Microsoft Purview**

**Tarefa 1 – Habilitar a integração do Microsoft Purview no Defender for Cloud Apps**

Com os rótulos de confidencialidade criados e publicados, você agora integrará o Microsoft Purview ao Microsoft Defender for Cloud Apps. Essa integração permite que o Defender examine arquivos em busca de rótulos de confidencialidade e aplique monitoramento de arquivos.

1.  Abra o **Microsoft Edge** e acesse o **Microsoft Defender** navegando até https://security.microsoft.com.

2.  Na navegação à esquerda, selecione **Settings** e, em seguida, **Cloud Apps**.

> <img src="media/image87.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na seção **Information Protection** no painel esquerdo, selecione **Microsoft Information Protection**.

> <img src="media/image88.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Na página **Microsoft Information Protection**, marque ambas as caixas de seleção disponíveis na página:

    - **Automatically scan new files for Microsoft Information Protection sensitivity labels and content inspection warnings**

> Permite que o Defender for Cloud Apps examine automaticamente arquivos novos ou modificados em busca de rótulos de confidencialidade e avisos de inspeção de conteúdo do Microsoft Purview.

- **Only scan files for Microsoft Information Protection sensitivity labels and content inspection warnings from this tenant**

> Limita a verificação a rótulos e avisos criados apenas na sua própria organização. Rótulos aplicados por locatários externos serão ignorados.

5.  Selecione **Save** para aplicar as configurações.

> <img src="media/image89.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Na seção **Information Protection** no painel esquerdo, selecione **Files**.

> <img src="media/image90.png" style="width:6.26806in;height:3.53472in" />

7.  Na página **Files**, selecione **Enable file monitoring**.

> <img src="media/image91.png" style="width:6.26806in;height:3.53472in" />

8.  Selecione **Save** para aplicar as configurações.

> <img src="media/image92.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você habilitou a integração do Microsoft Purview no Defender for Cloud Apps. Agora, o Defender pode detectar rótulos de confidencialidade e monitorar arquivos para avaliação de políticas e ações de governança.

**Tarefa 2 – Criar uma política de arquivos para rotular arquivos compartilhados externamente**

Por fim, você criará uma política de arquivos que aplica automaticamente um rótulo de confidencialidade a arquivos compartilhados externamente. Isso garante que o conteúdo sensível permaneça protegido mesmo quando compartilhado fora da organização.

1.  No **Microsoft Defender**, navegue até **Cloud apps \> Policies \> Policy management**.

> <img src="media/image93.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Selecione a guia **Information protection** e, em seguida, **Create policy \> File policy**.

> <img src="media/image94.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na página **Create file policy**, configure:

    - **Policy name**: Auto-label externally shared files

    - **Policy severity**: **High**

    - **Category**: **DLP**

    - Na seção **Files matching all of the following**:

      - Para o primeiro filtro, configure os menus suspensos como: **Access level equals external**

      - Para o segundo filtro, configure os menus suspensos como: **Last modified after (date)** e utilize a data de hoje

> <img src="media/image95.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Em **Governance actions**, expanda **Microsoft OneDrive for Business**:

  - Marque a caixa **Apply sensitivity label**

  - No menu suspenso, selecione **Highly Confidential-Specified People**

> <img src="media/image96.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

- Repita o mesmo processo para **Microsoft SharePoint Online**

  - Selecione a caixa de seleção **Apply sensitivity label**

  - Selecione **Highly Confidential-Specified People** no menu suspenso

> <img src="media/image97.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Selecione **Create** para concluir a criação da política de arquivos.

> <img src="media/image98.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Você criou uma política de arquivos que aplica rótulos de confidencialidade a arquivos compartilhados externamente. Essa política amplia sua estratégia de proteção de informações para conteúdos armazenados na nuvem.

**Resumo**

Neste laboratório, você assumiu o papel de Patti Fernandez, administradora de segurança da informação na Contoso Ltd., e implementou proteção de informações usando rótulos de confidencialidade do Microsoft Purview. Você habilitou o suporte a rótulos de confidencialidade, criou e publicou grupos e rótulos secundários, configurou rotulagem automática, aplicou Double Key Encryption (DKE) e integrou o Microsoft Purview ao Microsoft Defender for Cloud Apps. Além disso, você criou políticas de arquivo para garantir que conteúdos confidenciais permaneçam protegidos, mesmo quando compartilhados externamente.
