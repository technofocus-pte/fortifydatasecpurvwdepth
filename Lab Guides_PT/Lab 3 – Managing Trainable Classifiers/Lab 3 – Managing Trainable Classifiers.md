**Laboratório 3 – Gerenciando Trainable Classifiers**

**Introdução**

O locatário da Contoso Ltd. contém uma coleção de sites do SharePoint com o nome Sales and Marketing, que será utilizada futuramente para armazenar diversos documentos e relatórios relacionados a dados financeiros. Devido à natureza desses documentos, é necessário criar um trainable classifier para reconhecer e rotular esses arquivos. Para esse propósito, neste laboratório você ativará trainable classifiers personalizados e criará um novo classificador treinável.

**Objetivos**

- Criar um trainable classifier para identificar e categorizar dados típicos armazenados em sites específicos do SharePoint.

**Exercício 1 – Criando um trainable classifier**

Nesta tarefa, a Patti criará um novo trainable classifier e selecionará diferentes sites do SharePoint para identificar dados típicos criados e armazenados pela Contoso Ltd.

1.  No **Microsoft Edge**, abra uma nova **janela de navegação privada**, acesse **+++[<u>https://purview.microsoft.com+++</u>](https://purview.microsoft.com+++)** e faça login como **Patti Fernandez** usando o nome de usuário [**<u>PattiF@WWLxXXXXXX.onmicrosoft.com</u>**](mailto:PattiF@WWLxXXXXXX.onmicrosoft.com) e a senha de usuário fornecida na guia Resources.

2.  Na navegação à esquerda, selecione **Solutions** \> **Data Loss Prevention**.

> <img src="media/image1.png" style="width:6.26806in;height:3.30486in" />

3.  Expanda **Classifiers** no painel esquerdo. Selecione **Trainable Classifiers** no painel de subnavegação. Selecione **+ Create trainable classifier** para criar um novo classificador.

> <img src="media/image2.png" style="width:6.26806in;height:3.30694in" />

4.  Insira as seguintes informações:

5.  Name: **+++Contoso Company Data+++**

6.  Description: **+++Trainable classifier for company data produced and stored by Contoso Ltd.+++**

7.  Selecione **Next**.

> <img src="media/image3.png" style="width:6.26806in;height:3.32014in" alt="A screenshot of a computer Description automatically generated" />

8.  Selecione **Choose sites** para abrir o painel do lado direito.

> <img src="media/image4.png" style="width:6.26806in;height:3.32014in" alt="A screenshot of a computer Description automatically generated" />

9.  Selecione os seguintes sites do SharePoint e, em seguida, selecione **Add**.

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

> <img src="media/image5.png" style="width:6.26806in;height:3.32014in" />

10. Aguarde até que os sites selecionados sejam exibidos na lista e selecione **Next**.

> <img src="media/image6.png" style="width:6.26806in;height:3.32014in" alt="A screenshot of a computer Description automatically generated" />

11. Na página **Source of the negative sample content**, clique em **+ Choose sites**.

> <img src="media/image7.png" style="width:6.26806in;height:3.39236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. No painel **Add SharePoint sites**, navegue e marque a caixa de seleção ao lado de **Learn** e, em seguida, clique no botão **Add**.

> <img src="media/image8.png" style="width:6.26806in;height:3.39375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Clique no botão **Next**.

> <img src="media/image9.png" style="width:6.26806in;height:3.44236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Revise as configurações e selecione **Create trainable classifier**.

> <img src="media/image10.png" style="width:6.26806in;height:3.40347in" />

15. Na página **Your trainable classifier is being trained**, clique no botão **Done**.

> <img src="media/image11.png" style="width:6.26806in;height:3.42292in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Os documentos e arquivos nos sites do SharePoint selecionados agora estão sendo analisados, o que pode levar até 24 horas.

**Resumo:**

Neste laboratório, você criou um trainable classifier personalizado no Microsoft Purview chamado *Contoso Company Data,* selecionando sites relevantes do SharePoint como fontes de conteúdo positivo e negativo. Esse classificador analisará documentos para identificar dados específicos da empresa, sendo que o processo de treinamento pode levar até 24 horas.
