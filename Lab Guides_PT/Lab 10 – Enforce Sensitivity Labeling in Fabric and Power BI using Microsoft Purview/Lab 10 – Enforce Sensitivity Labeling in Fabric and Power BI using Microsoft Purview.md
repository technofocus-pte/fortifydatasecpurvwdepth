**Laboratório 10 – Implementar rótulos de confidencialidade no Fabric e no Power BI usando o Microsoft Purview**

**Introdução**

Os rótulos de confidencialidade do Microsoft Purview Information Protection no Fabric e no Power BI (incluindo o Power BI Desktop) devem estar habilitados no locatário. Quando os rótulos de confidencialidade estão habilitados:

- Usuários e grupos de segurança especificados na organização podem aplicar rótulos de confidencialidade ao conteúdo do Fabric. No serviço do Fabric, isso significa qualquer item do Fabric. No Power BI Desktop, isso se refere aos arquivos .pbix.

- No serviço, todos os membros da organização conseguem visualizar esses rótulos. No Desktop, apenas os membros da organização para os quais os rótulos foram publicados conseguem visualizá-los.

**Objetivo**

- Habilitar e priorizar uma política de rótulo de confidencialidade manual no Microsoft Fabric usando o Microsoft Purview.

**Exercício 1 – Ativar a Avaliação do Microsoft Fabric e Acessar o Purview Hub**

1.  Abra o navegador Edge e, na barra de endereços, insira a seguinte URL para acessar o portal do Fabric - https://app.fabric.microsoft.com

<img src="media/image1.png" style="width:6.26806in;height:4.21667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Observação**: caso você seja direcionado diretamente para o portal do Fabric, ignore as etapas \#2 e 3.

2.  Insira as credenciais do seu locatário.

<img src="media/image2.png" style="width:6.26806in;height:4.86597in" />

<img src="media/image3.png" style="width:6.26806in;height:4.37778in" />

3.  No campo de senha, insira a senha do locatário e clique no botão **Sign in**.

<img src="media/image4.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

4.  Na caixa de diálogo **Welcome to the Fabric view**, clique no botão **Cancel**.

<img src="media/image5.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Clique no ícone de perfil na barra de comandos.

<img src="media/image6.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Navegue e clique no botão **Free trial**.

<img src="media/image7.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na tela **Activate your 60-day free Fabric trial capacity**, na região **Trial capacity**, certifique-se de que a região **Default – West US 3** esteja selecionada e clique no botão **Activate**.

<img src="media/image8.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  Na caixa de diálogo **Successfully upgraded to a free Microsoft Fabric trial**, clique no botão **Got it**.

<img src="media/image9.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Clique no ícone de engrenagem **Settings** na barra de comandos.

<img src="media/image10.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Navegue até a seção Governance and insights e clique no link **Microsoft Purview hub (preview)**. Em seguida, na página **Microsoft Purview hub (preview)**, navegue e clique no bloco **Information Protection**.

<img src="media/image11.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image12.png" style="width:6.26806in;height:3.69028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. Caso a caixa de diálogo **Pick an account** seja exibida, selecione o ID do seu locatário.

<img src="media/image13.png" style="width:6.26806in;height:3.78958in" />

12. Na caixa de diálogo **Welcome to Information Protection in the new Microsoft Purview portal**, clique no botão **Get started**.

<img src="media/image14.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Exercício 2 – Criar e Configurar uma Política de Rótulo de Confidencialidade para Fabric e Power BI**

1.  No painel Information Protection, navegue e clique no menu suspenso ao lado de **Policies**.

<img src="media/image15.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Clique em **Label publishing policies**. Na página **Label publishing policies**, navegue e clique em **Publish label**.

<img src="media/image16.png" style="width:6.26806in;height:3.68611in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na página **Create policy**, navegue e clique no link **Choose sensitivity label to publish**.

<img src="media/image17.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  O painel **Sensitivity label to publish** será exibido no lado direito. Navegue, marque a caixa de seleção ao lado de **Confidential** e clique no botão **Add**.

<img src="media/image18.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Clique no botão **Next**.

<img src="media/image19.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Na página **Assign admin units**, clique no botão **Next**.

<img src="media/image20.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na página **Publish to users and groups**, certifique-se de que a caixa de seleção **Users and groups** esteja marcada e clique no botão **Next**.

<img src="media/image21.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  Na página **Policy settings**, marque a caixa de seleção **Require users to apply a label to their Fabric and Power BI content** e clique no botão **Next**.

<img src="media/image22.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image23.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Default settings for documents – Apply a default label to documents**, clique no botão **Next**.

<img src="media/image24.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

10. Na página **Default settings for documents – Apply a default label to emails**, clique no botão **Next**.

<img src="media/image25.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

11. Na página **Default settings for meetings and calendar events**, clique no botão **Next**.

<img src="media/image26.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

12. Na página **Default settings for Fabric and Power BI content**, clique no botão **Next**.

<img src="media/image27.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na página **Name your policy**, no campo **Name**, insira: Manual Labeling – HR Confidential Docs. Em seguida, clique no botão **Next**..

<img src="media/image28.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Na página **Review and finish**, clique no botão **Submit**.

<img src="media/image29.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. A política foi criada com sucesso. Agora, clique no botão **Done**.

<img src="media/image30.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. Na página **Label policies**, você verá que a política **Manual Labeling – HR Confidential Docs** foi criada com sucesso.

<img src="media/image31.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Selecione **Manual Labeling – HR Confidential Docs**, clique no menu de reticências horizontais e selecione **Move up** para alterar a prioridade.

<img src="media/image32.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image33.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Selecione novamente **Manual Labeling – HR Confidential Docs**, clique no menu de reticências horizontais ao lado da política e selecione **Move up**.

<img src="media/image34.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Você observará que a prioridade da política **Manual Labeling – HR Confidential Docs** foi alterada para 1.

<img src="media/image35.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumo**

Neste laboratório, você ativou uma avaliação do Microsoft Fabric, acessou o portal do Microsoft Purview e criou uma política obrigatória de rótulo de confidencialidade que exige que os usuários apliquem o rótulo “Confidential” ao conteúdo do Fabric e do Power BI. Em seguida, a política foi priorizada para implementação.
