# Laboratório 3 – Gerenciando classificadores treináveis

## Objetivo:

O locatário da Contoso Ltd. contém uma coleção de sites do SharePoint
que serão usados no futuro para armazenar vários documentos e relatórios
relacionados a finanças. Devido à natureza desses documentos, você
precisa criar um classificador treinável para reconhecer e rotular esses
arquivos. Para isso, você ativará classificadores treináveis
personalizados e criará um novo neste laboratório.

## Exercício 1 – Criando um classificador treinável

Nesta tarefa, Patti criará um novo classificador treinável e selecionará
diferentes sites do SharePoint para identificar dados típicos criados e
armazenados pela Contoso Ltd.

1.  No **Microsoft Edge**, abra uma **New InPrivate Window**, navegue
    até `https://purview.microsoft.com` e faça login como **Patti
    Fernandez** usando o nome de usuário
    `PattiF@WWLx{TENANTPREFIX}.onmicrosoft.com` e a Senha de Usuário
    fornecida na guia de recursos.

2.  No painel de navegação à esquerda, selecione **Solutions** \> **Data
    Loss Prevention**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image1.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

3.  Expanda **Classifiers** no painel esquerdo. Selecione **Trainable
    Classifiers** no painel de subnavegação. Selecione **+ Create
    trainable classifier** para criar um novo classificador.

![](./media/image2.png)

4.  Insira as seguintes informações na página **Name and describe your
    trainable classifier**:

    - Name: `Contoso Company Data`

    - Description:
      `Trainable classifier for company data produced and stored by Contoso Ltd``.`

5.  Selecione **Next**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image3.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

8.  Selecione **Choose sites** para abrir o painel do lado direito.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image4.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

9.  Selecione os seguintes sites do SharePoint e selecione **Add**.

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

![](./media/image5.png)

10. Aguarde até que o site escolhido seja exibido na lista e selecione
    **Next**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image6.png)

Uma captura de tela de um computador Descrição gerada automaticamente

11. Na **página** **Source of the negative sample content**, selecione o
    site **Learn** e, em seguida, selecione **Next**.

12. Examine as configurações e selecione **Create trainable
    classifier**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image7.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

13. Quando a mensagem Your trainable classifier was created for
    mostrada, selecione **Done**.

Os documentos e arquivos no site do SharePoint escolhido agora estão
sendo analisados, o que pode levar até 24 horas. Quando estiver pronto,
você pode executar o seguinte:

- Testar o classificador

- Revisar o classificador

- Publicar o classificador

Você pode explorar os classificadores já existentes para uma revisão
mais aprofundada.

## Resumo:

Você criou com sucesso um classificador treinável personalizado que
corresponde aos arquivos armazenados nos sites existentes do SharePoint
da Contoso Ltd.
