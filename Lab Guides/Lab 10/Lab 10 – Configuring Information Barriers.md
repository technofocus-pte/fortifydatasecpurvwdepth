# Laboratório 10 – Configuração de barreiras de informações

## Objetivo:

A Contoso tem cinco departamentos: *RH*, *Vendas*, *Marketing*,
*Pesquisa* e *Manufatura*. Para manter a conformidade com os
regulamentos do setor, os usuários de alguns departamentos não devem se
comunicar com outros departamentos, conforme listado na tabela a seguir:

[TABLE]

Para essa estrutura, o plano da Contoso inclui três Policies de IB:

1.  Uma política de IB criada para impedir que a equipe de vendas se
    comunique com a pesquisa

2.  Outra política do IB para impedir que a Pesquisa se comunique com a
    equipe de vendas.

3.  Uma política de IB projetada para permitir que a Manufatura se
    comunique apenas com RH e Marketing.

## Exercício 1 – Pré-requisitos

### Tarefa 1 – Criar segmento para usuários em sua organização

1.  Em sua VM, no **PowerShell** run as administrator.

![Imagem quebrada](./media/image1.png)

Imagem interrompida

2.  Execute o seguinte:

`Install-Module ExchangeOnlineManagement`

3.  Se for solicitado ‘**Do you want PowerShellGet to install and import
    the NuGet provider now?**’ e ‘**Are you sure you want to install the
    modules from ‘PSGallery’?**’ Digite **y** e pressione Enter.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image2.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

4.  Execute o seguinte comando assim que a instalação estiver concluída.

`Import-Module ExchangeOnlineManagement`

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image3.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

5.  Agora execute o seguinte comando para se conectar ao Exchange
    Online.

`Connect-``IPPSSession`

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image4.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

6.  Faça login usando as credenciais do **MOD Administrator** fornecidas
    na página inicial do ambiente de laboratório.

![Imagem quebrada](./media/image5.png)

Imagem interrompida

7.  Execute o comando a seguir, um por um, no **PowerShell** para criar
    a estrutura da organização.

`New-``OrganizationSegment`` -Name "HR" -``UserGroupFilter`` "Department -eq 'HR'"`

![Imagem quebrada](./media/image6.png)

Imagem interrompida

`New-``OrganizationSegment`` -Name "Sales" -``UserGroupFilter`` "Department -eq 'Sales'"`

`New-``OrganizationSegment`` -Name "Marketing" -``UserGroupFilter`` "Department -eq 'Marketing'"`

`New-``OrganizationSegment`` -Name "Research" -``UserGroupFilter`` "Department -eq 'Research'"`

`New-``OrganizationSegment`` -Name "Manufacturing" -``UserGroupFilter`` "Department -eq 'Manufacturing'"`

### Tarefa 2 – Ativar a pesquisa de diretório com escopo no Microsoft Teams

Para ativar a pesquisa por nome

1.  Vá para o centro de administração do Microsoft Teams acessando o
    site https://admin.teams.microsoft.com, selecione **Teams** \>
    **Teams settings**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image7.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

2.  Em **Search by name**, próximo ao **Scope directory search using an
    Exchange address book policy**, **On** o botão de alternância.
    Selecione **Save**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image8.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

## Exercício 2 – Criar Policies de IB

### Tarefa 1 – Bloquear comunicações entre segmentos

1.  Faça login no site `https://purview.microsoft.com/` usando
    credenciais do MOD Administration, fornecidas na guia de recursos do
    seu ambiente.

2.  No painel de navegação esquerdo, selecione **Solutions** \>
    **Information barriers**.

![](./media/image9.png)

3.  Na subnavegação, selecione **Policies**. Na página **Policies**,
    selecione **Create policy** para criar e configurar uma nova
    política de IB.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image10.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

4.  Na página **Name**, digite um nome para a política:
    `Sales-Research`. Em seguida, selecione **Next**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image11.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

5.  Na página **Assigned segment**, selecione **Choose segment**. No
    painel **Select assigned segment for this policy**, selecione Sales.
    Agora selecione **Add** para adicionar o segmento selecionado à
    política. Você só pode selecionar um segmento.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image12.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

6.  Selecione **Next**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image13.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

7.  Na página **Communication and collaboration**, selecione
    **Blocked.** Selecione **Choose segment**, selecione **Research** e,
    em seguida, selecione **Add.**

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image14.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

8.  Na página **Communication and collaboration**, selecione o tipo de
    política como Blocked no campo **Communication and collaboration**.
    Selecione **Next**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image15.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

9.  Na página **Policy status**, alterne o status da política ativa para
    **On**. Selecione **Next** para continuar.

![Imagem quebrada](./media/image16.png)

Imagem interrompida

10. Na página **Review your settings**, revise as configurações que você
    escolheu para a política e quaisquer sugestões ou avisos para suas
    seleções. Selecione **Edit** para alterar qualquer um dos segmentos
    e status da política ou selecione **Submit** para criar a política.

![Imagem quebrada](./media/image17.png)

Imagem interrompida

11. Selecione **Done** depois que a política for criada.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image18.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

### Tarefa 2 – Criar Policies de IB por meio do PowerShell

1.  Em sua VM, no **PowerShell** run as adminstrator.

![Imagem quebrada](./media/image1.png)

Imagem interrompida

2.  Execute o seguinte:

`Import-Module ExchangeOnlineManagement`

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image19.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

3.  Agora execute o seguinte comando para se conectar ao Exchange
    Online.

`Connect-``IPPSSession`

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image4.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

4.  Faça login usando as credenciais **MOD Administrator** fornecidas na
    página de recursos do ambiente de laboratório.

5.  Execute o comando a seguir para criar uma política de IB chamada
    **Research-Sales**. Quando essa política estiver ativa e aplicada,
    ela ajudará a impedir que os usuários que estão no segmento de
    **Research** se comuniquem com os usuários no segmento de **Sales**.

`New-``InformationBarrierPolicy`` -Name "Research-Sales" -``AssignedSegment`` "Research" -``SegmentsBlocked`` "Sales" -State Inactive`

![Imagem quebrada](./media/image20.png)

Imagem interrompida

6.  Execute o comando a seguir para criar uma política de IB chamada
    **Manufacturing-HRMarketing**. Quando esta política está ativa e
    aplicada, a **Manufacturing** pode se comunicar apenas com **HR** e
    **Marketing**. RH e Marketing não estão impedidos de se comunicar
    com outros segmentos.

`New-``InformationBarrierPolicy`` -Name "Manufacturing-``HRMarketing``" -``AssignedSegment`` "Manufacturing" -``SegmentsAllowed`` "``HR","Marketing","Manufacturing``" -State Inactive`

![Uma captura de tela de computador de um programa de computador
Descrição gerada automaticamente](./media/image21.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

7.  Faça login no site `https://purview.microsoft.com/` usando as
    credenciais do **MOD Administration**, fornecidas na home page do
    seu ambiente.

8.  No painel de navegação esquerdo, selecione **Information barriers**
    \> **Policies**. Na página **Policies**. Você poderá ver as Policies
    que criamos.

![](./media/image22.png)

## Exercício 3 – Aplicar Policies de IB

1.  Faça login no `https://purview.microsoft.com/` usando as credenciais
    do MOD Administration, fornecidas na guia de recursos do seu
    ambiente.

2.  No painel de navegação esquerdo, selecione **Information barriers**.

![](./media/image9.png)

3.  Na subnavegação, selecione **Policy applications**. Selecione
    **Apply all policies**.

![](./media/image23.png)

**Resumo:**

Neste laboratório, aprendemos a criar os segmentos para implementar as
políticas de IB. Desenvolvemos diferentes políticas para criar barreiras
de informações, permitindo ou bloqueando a comunicação e a colaboração
entre diferentes segmentos.
