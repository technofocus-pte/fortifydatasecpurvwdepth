**Laboratório 7 – Configurando o Insider Risk Management**

**Introdução**

Neste laboratório, aprenderemos como configurar o Insider Risk Management usando as Políticas de Insider Risk Management. Utilizaremos os Sensitive Info Types criados no Laboratório 1 e as políticas de DLP criadas no Lab 4 para criar políticas que protegerão a organização contra uso arriscado do navegador, roubo de dados ou vazamentos de informações.

Para isso, criaremos uma infraestrutura no Azure que representará os dispositivos da organização. Aprenderemos como integrar esses dispositivos ao Azure AD e ao Intune, além de instalar um agente MDM, para que seja possível receber alertas dessas máquinas.

**Objetivos**

- Sincronizar os relógios das VMs para garantir configurações de horário precisas para testes de políticas.

- Atribuir usuários ao grupo de funções de Insider Risk Management no Microsoft Purview.

- Habilitar insights analíticos para detecção de riscos internos nos níveis de locatário e usuário.

- Integrar dispositivos Windows 10 ao Microsoft Defender for Endpoint para monitoramento de riscos internos.

- Criar e configurar políticas de Insider Risk Management para::

  - Uso arriscado do navegador

  - Roubo de dados por usuários em desligamento

  - Vazamento de dados por usuários

- Pontuar cada política para simular cenários de detecção de risco interno para a conta MOD Administrator.

**Exercicio 1: Configurando o ambiente**

**Tarefa 0 : Sincronizar o relógio da VM**

1.  Feche todas as abas do navegador Microsoft Edge abertas na VM. Clique no ícone do **Windows** e, em seguida, clique em **Settings**, conforme mostrado na imagem abaixo.

> <img src="media/image1.png" style="width:6.26806in;height:5.35972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Na barra de pesquisa do **Windows Settings**, digite Date & time settings e selecione **Date & time settings** na lista.

> <img src="media/image2.png" style="width:6.26806in;height:3.45417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na página **Date & time**, navegue e clique no botão **Sync now**.

> <img src="media/image3.png" style="width:6.26806in;height:3.39167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Exercício 2 – Criar políticas de Insider Risk Management**

**Pré-requisitos**

**Etapa 1 – Adicionar usuários ao grupo de funções de Insider Risk Management**

1.  Abra o portal do Microsoft Purview: https://purview.microsoft.com e faça login com as credenciais do **MOD Administrator**.

2.  No menu de navegação à esquerda, clique em **Settings.**

> <img src="media/image4.png" style="width:6.26806in;height:3.43472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  No painel **Settings**, navegue e clique em **Roles and scopes**. Clique em **Role groups**, marque a caixa ao lado de **Insider Risk Management** e clique no ícone de lápis para **Edit**.

> <img src="media/image5.png" style="width:6.26806in;height:4.52153in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image6.png" style="width:6.26806in;height:3.97361in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Na página **Edit Members of the role group**, clique em **Choose users**.

> <img src="media/image7.png" style="width:6.26806in;height:3.48125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Marque a caixa ao lado de **Alex Wilber** e clique no botão **Select**.\
    Caso **Alex Wilber** já esteja selecionado, ignore esta etapa.

> **Observação**: caso você não tenha visto os nomes Megan Bowen e MOD Administrator na opção Edit members name, além do nome Alex, selecione também os nomes Megan Bowen e MOD Administrator.
>
> .
>
> <img src="media/image8.png" style="width:6.26806in;height:3.49722in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Certifique-se de que MOD Administrator, Megan Bowen e Alex Wilber estejam listados e clique no botão **Next**.

> <img src="media/image9.png" style="width:6.26806in;height:3.46597in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Selecione **Save** para adicionar os usuários ao grupo de funções.

> <img src="media/image10.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer Description automatically generated" />

8.  Selecione **Done** para concluir as etapas.

> <img src="media/image11.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer Description automatically generated" />

**Etapa 2 – Habilite insights de análise de risco interno**

1.  No portal do Microsoft Purview, navegue até **Settings**, role a página e clique em **Insider risk management**. Na página **Insider Risk Management settings – Analytics**, ative os botões **Show insights at tenant level** e **Show insights at user level**. Em seguida, clique no botão **Save**.

> <img src="media/image12.png" style="width:6.26806in;height:3.46944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Etapa 3 – Integração de um dispositivo**

Neste cenário de implementação, você integrará dispositivos que ainda não foram integrados e deseja detectar atividades de risco interno em dispositivos Windows 10.

Precisamos registrar o dispositivo/VM no Microsoft Entra ID como pré-requisito para criar qualquer política de Insider Risk.

1.  Clique no ícone do Windows e selecione **Settings**, conforme mostrado na imagem abaixo..

> <img src="media/image13.png" style="width:6.26806in;height:3.93403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Vá para **Accounts** \> **Access work or school**. Na página **Access work or school**, clique em **Connect**.

> <img src="media/image14.png" style="width:6.26806in;height:3.75556in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image15.png" style="width:6.26806in;height:4.93542in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na janela **Set up a work or school account**, clique em **Join this device to Microsoft Entra ID**.

> <img src="media/image16.png" style="width:6.26806in;height:4.09514in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Na solicitação de login, faça login com as credenciais de **MOD Administrator** fornecidas na guia Resources do seu ambiente de laboratório.

> <img src="media/image17.png" style="width:6.26806in;height:5.95625in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image18.png" style="width:6.26806in;height:6.00347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Na caixa de diálogo **Make sure this is your organisation**, clique no botão **Join**.

> <img src="media/image19.png" style="width:6.26806in;height:3.65764in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

6.  Após a conclusão, será exibida a janela **You're all set!**. Clique em **Done**.

> <img src="media/image20.png" style="width:6.26806in;height:5.82153in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Novamente, na página **Access work or school**, clique em **Connect**.

> <img src="media/image21.png" style="width:6.26806in;height:4.59444in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  Na janela **Set up a work or school account**, faça login usando as credenciais do MOD Administrator.

> <img src="media/image22.png" style="width:6.26806in;height:5.86042in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image23.png" style="width:6.26806in;height:5.7in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na caixa de diálogo **Stay signed in?**, clique no botão **Yes**.

> <img src="media/image24.png" style="width:6.26806in;height:4.925in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Caso a caixa de diálogo **Setting up your device** seja exibida, selecione **Got it**.

> <img src="media/image25.png" style="width:6.26806in;height:3.51458in" alt="A screenshot of a computer Description automatically generated" />

11. Agora vá para **Windows settings** \> **Accounts** \> **Access work or school** \> **Connected to Contoso MDM** \> **Info** \> **Sync**.

> <img src="media/image26.png" style="width:6.26806in;height:4.30486in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image27.png" style="width:6.26806in;height:5.60347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. Clique no símbolo do Windows na sua VM. Selecione o usuário **Admin** e selecione **Sign out**.

> <img src="media/image28.png" style="width:6.26806in;height:6.05972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na tela de usuários, selecione **Other user**.

> <img src="media/image29.png" style="width:6.26806in;height:3.78403in" alt="A screenshot of a computer Description automatically generated with medium confidence" />

14. Insira suas credenciais do O365 fornecidas na página inicial do ambiente do laboratório e faça login na VM como **MOD Administrator**.

> <img src="media/image30.png" style="width:6.26806in;height:4.95556in" alt="A screenshot of a login screen AI-generated content may be incorrect." />

15. Faça login em https://purview.microsoft.com usando sua conta **MOD Administrator** na VM do laboratório.

16. No portal do **Microsoft Purview**, navegue e selecione **Settings** \> **Device onboarding** \> **Devices**. Clique em **Turn on Device onboarding**.

<img src="media/image31.png" style="width:6.26806in;height:3.31875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Na caixa de diálogo **Turn on device onboarding**, clique no botão **OK**.

> <img src="media/image32.png" style="width:6.26806in;height:4.00069in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Na caixa de diálogo **Device monitoring is being turned on**, clique no botão **OK**.

> <img src="media/image33.png" style="width:6.26806in;height:3.74375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Aguarde alguns minutos e, em seguida, atualize a página.

> <img src="media/image34.png" style="width:6.26806in;height:3.84583in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image35.png" style="width:6.26806in;height:3.65347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

20. Em **Settings** \> **Device onboarding** \> **Onboarding**, clique em **Download package**.

> <img src="media/image36.png" style="width:6.26806in;height:3.39028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

21. Após o download, copie o arquivo para a área de trabalho. Clique com o botão direito no arquivo e selecione **Extract all…**, em seguida clique no botão **Extract.**

> <img src="media/image37.png" style="width:6.26806in;height:4.69514in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image38.png" style="width:6.26806in;height:5.37778in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image39.png" style="width:6.26806in;height:4.61944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

22. Após a extração, abra a pasta e execute o arquivo com privilégios de **administrador**.

> <img src="media/image40.png" style="width:6.26806in;height:3.92083in" alt="A computer screen with a computer screen Description automatically generated" />

23. Caso a caixa de diálogo **Search for app in the Store?** seja exibida, clique no botão **Yes**; caso contrário, ignore.

24. Na caixa de diálogo **The publisher could not be verified. Are you sure you want to run this software?**, clique no botão **Run**.

> <img src="media/image41.png" style="width:6.26806in;height:4.48889in" alt="A screenshot of a computer AI-generated content may be incorrect." />

25. Caso a caixa de diálogo **User Account Control** seja exibida, clique no botão **Yes**.

> <img src="media/image42.png" style="width:6.26806in;height:4.31181in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

26. No Command Prompt, pressione **Y** e pressione Enter para confirmar. Você receberá uma mensagem informando que o dispositivo foi integrado. No Command Prompt, ao receber a mensagem **Press any key to continue . . .**, pressione qualquer tecla.

> <img src="media/image43.png" style="width:6.26806in;height:2.29861in" alt="A screenshot of a computer error Description automatically generated" />

27. Após o fechamento do Prompt de Comando, abra o Prompt de Comando em modo administrador digitando **cmd** na barra de pesquisa do Windows, clicando com o botão direito em **Prompt de Comando** e selecionando **Run as administrator**.

> <img src="media/image44.png" style="width:6.26806in;height:5.90208in" alt="A screenshot of a computer AI-generated content may be incorrect." />

28. Na caixa de diálogo **User Account Control**, clique no botão **Yes**.

> <img src="media/image42.png" style="width:6.26806in;height:4.31181in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

29. Execute um teste de detecção executando o seguinte comando. A janela do Command Prompt será fechada automaticamente.

> powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden \$ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'
>
> <img src="media/image45.png" style="width:6.26806in;height:3.30625in" alt="Text Description automatically generated" />

30. Feche a conexão da VM.

31. Abra as configurações clicando em **Settings** no menu de navegação e selecione **Devices Onboarding** \> **Devices**.

> **Observação:** embora normalmente leve cerca de 60 segundos para a integração de dispositivos ser habilitada, permita até 30 minutos.

32. Você poderá verificar a lista em **Devices**. A lista ficará vazia até que os dispositivos sejam integrados; após isso, você poderá visualizar suas VMs listadas como dispositivos integrados.

**Tarefa 1 – Criar uma política para toda a organização para detectar e pontuar o uso arriscado do navegador**

**Etapa 1 – Criar uma nova política**

1.  No portal do Microsoft Purview, clique em Solutions e, em seguida, clique em **Insider Risk Management**.

> <img src="media/image46.png" style="width:6.26806in;height:3.48403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Clique em **Policies**. Na página Policies, clique em **+ Create policy** \> **Custom policy**.

> <img src="media/image47.png" style="width:6.26806in;height:3.46319in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na página Choose a policy template, escolha Risky browser usage (preview), em Risky browser usage (preview).

> <img src="media/image48.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

4.  Revise todos os pré-requisitos.

> <img src="media/image49.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

5.  Selecione **Next** para continuar.

> <img src="media/image50.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

6.  Na página **Name and description**, preencha os seguintes campos:

    - Name: Risky usage of browser

    - Description: This is a test policy for the risky browser usage

7.  Selecione **Next** para continuar.

> <img src="media/image51.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

8.  Na página **Choose users, groups, & adaptive scopes**, selecione **All users, groups, & adaptive scopes**. Selecione **Next** para continuar.

> <img src="media/image52.png" style="width:6.26806in;height:3.6125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Exclude users and groups**, selecione **Next**.

> <img src="media/image53.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Na página Decide whether to prioritize, selecione **I don't want to priority content right now**. Selecione **Next** para continuar.

> <img src="media/image54.png" style="width:6.26806in;height:3.49514in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. Na página **Choose triggering event for this policy**, selecione o botão **Turn on indicators**.

> <img src="media/image55.png" style="width:6.26806in;height:3.45069in" alt="A screenshot of a computer Description automatically generated" />

12. Na caixa de diálogo **Turn on indicators for your organization**, role a página para baixo e clique no botão **Choose indicators to turn on**.

> <img src="media/image56.png" style="width:6.26806in;height:3.94097in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image57.png" style="width:6.26806in;height:3.9875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na caixa de diálogo **Choose indicators to turn on**, certifique-se de que, em Risky browsing indicators (preview), todos os indicadores estejam selecionados.

> <img src="media/image58.png" style="width:6.26806in;height:4.00833in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image59.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automatically generated" />

14. Role a página para baixo e selecione **Save**.

15. Na página **Choose triggering event for this policy**, certifique-se de que o botão de opção ao lado de **User browsed to a potentially risky website** esteja selecionado. Em **Select which activities will trigger this policy**, selecione todas as opções e clique no botão **Next**.

> <img src="media/image60.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

16. Na página **Choose thresholds for triggering events**, selecione o botão de opção **Choose your own thresholds**, altere todos os limites para 1 per day e selecione **Next**.

> <img src="media/image61.png" style="width:6.26806in;height:3.47153in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image62.png" style="width:6.26806in;height:4.12708in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Na página **Indicators**, selecione **Next**.

> <img src="media/image63.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

18. Na página **Choose threshold type for indicators**, certifique-se de que **Apply thresholds provided by Microsoft** esteja selecionado e clique no botão **Next**.

> <img src="media/image64.png" style="width:6.26806in;height:3.44792in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Na página **Review settings and finish**, selecione **Submit**.

> <img src="media/image65.png" style="width:6.26806in;height:3.44514in" alt="A screenshot of a computer AI-generated content may be incorrect." />

20. Na página **Your policy was created**, selecione **Done**.

> <img src="media/image66.png" style="width:6.26806in;height:3.4375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

21. Mantenha a guia aberta e continue para a próxima tarefa.

**Etapa 2 – Avalie a política**

1.  Clique na nova política chamada Risky usage of browser. Selecione **Start scoring activity for users**.

> <img src="media/image67.png" style="width:6.26806in;height:3.50417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  No campo Reason for scoring activity, insira Testing the policy. No campo **Scoring activity for this many days (between 5 and 30)**, selecione **10 days**.

> <img src="media/image68.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  No campo Score activity for these users, digite MOD e selecione MOD administrator.

> <img src="media/image69.png" style="width:6.26806in;height:3.45833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Em seguida, clique no botão **Start scoring activity**.

> <img src="media/image70.png" style="width:6.26806in;height:3.46389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Clique no botão **Close**.

> <img src="media/image71.png" style="width:6.26806in;height:3.46528in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarefa 2 – Roubo de dados por usuários que estão saindo da empresa**

**Etapa 1 – Criar uma nova política**

1.  Na página **Policies**, clique em **+ Create policy** e selecione **Custom policy**.

> <img src="media/image72.png" style="width:6.26806in;height:3.46181in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Na página Choose a policy template, escolha Data theft by departing users, em Data theft. Selecione Next para continuar.

> <img src="media/image73.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automatically generated" />

3.  Na página **Name and description**, preencha os seguintes campos:

    - Name: Data theft by a user

    - Description: This is a test policy for preventing data theft

4.  Selecione **Next** para continuar.

> <img src="media/image74.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automatically generated" />

5.  Na página **Choose users, groups, & adaptive scopes**, selecione o botão de opção ao lado de \*\* All users, groups, and adaptive scopes\*\*, e clique no botão **Next**.

\![A screenshot of a computer Description automaticall generated\](./media/uu1.png)

6.  Na página **Exclude users and groups (optional)**, clique no botão **Next**.

\![A screenshot of a computer Description automaticall generated\](./media/uu2.png)

7.  Na página **Decide whether to prioritize content**, selecione **I want to prioritize content**. Marque apenas as caixas **Sensitivity labels** e **Sensitive info types**. Selecione **Next** para continuar.

> <img src="media/image75.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer screen Description automatically generated with medium confidence" />

8.  Na página **Sensitivity labels to prioritize**, selecione **Add or edit sensitivity labels**. Na barra de pesquisa **Add or edit sensitivity labels**, digite employee e pressione Enter, selecione **Internal/Employee data (HR)** e selecione **Add**. Em seguida, clique em **Next**.

> <img src="media/image76.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer screen Description automatically generated with medium confidence" />

9.  Na página **Sensitive info types to prioritize**, selecione **Add or edit sensitive info types**. No painel lateral, procure e selecione **Credit Card Number**, **Contoso Employee ID** e **Contoso Employee EDM**. Selecione **Add** e, em seguida, clique em **Next**.

> <img src="media/image77.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automaticall generated" />

10. Na página **Decide whether to score only activity with priority content**, certifique-se de que **Get alerts for all activity** esteja selecionado. Em seguida, clique no botão **Next**.

> <img src="media/image78.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer screen Description automatically generated with medium confidence" />

11. Na página **Choose triggering event for this policy**, mantenha a seleção padrão e clique em **Next**.

> <img src="media/image79.png" style="width:6.26806in;height:4.06597in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. Na página **Indicators**, clique no menu suspenso ao lado de **Office indicators (31/31 selected)**.

> <img src="media/image80.png" style="width:6.26806in;height:3.47708in" alt="A screenshot of a computer AI-generated content may b incorrect." />

13. Certifique-se de que todos os Office indicators estejam selecionados e clique no botão **Next**.

> <img src="media/image81.png" style="width:6.26806in;height:3.48194in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Mantenha todos os parâmetros da página **Detection options** no estado padrão e clique no botão **Next**.

> <img src="media/image82.png" style="width:6.26806in;height:3.48264in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. Na página **Choose threshold type for indicators**, selecione o botão de opção **Choose your own thresholds**, role a página e clique no menu suspenso **Office indicators**.

> <img src="media/image83.png" style="width:6.26806in;height:3.47847in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image84.png" style="width:6.26806in;height:4.1125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. Em **Sharing SharePoint files with people outside the organization**, utilize 1, 2 e 3 eventos para cada estágio, respectivamente, e selecione **Next**.

> <img src="media/image85.png" style="width:6.26806in;height:3.47917in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Na página **Review settings and finish**, clique no botão **Submit**.

> <img src="media/image86.png" style="width:6.26806in;height:3.45764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Na página Your policy was created, selecione Done.

> <img src="media/image87.png" style="width:6.26806in;height:3.43819in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Etapa 2 – Avaliar a política**

1.  Clique na nova política chamada **Data theft by a user**. Selecione **Start scoring activity for users**.

> <img src="media/image88.png" style="width:6.26806in;height:3.44722in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  No campo Reason for scoring activity, Testing the policy. No campo **Scoring activity for this many days (between 5 and 30)**, selecione **10 days**.

> <img src="media/image68.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  No campo Score activity for these users, digite MOD e então selecione MOD administrator.

> <img src="media/image69.png" style="width:6.26806in;height:3.45833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Em seguida, clique no botão **Start scoring activity**.

> <img src="media/image70.png" style="width:6.26806in;height:3.46389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Clique no botão **Close**.

> <img src="media/image89.png" style="width:6.26806in;height:6.02361in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarefa 3 – Vazamentos de dados por usuários**

**Etapa 1 – Criar uma nova política**

1.  Na página **Policies**, clique em **+ Create policy** e selecione **Custom policy**.

> <img src="media/image72.png" style="width:6.26806in;height:3.46181in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Na página **Choose a policy template**, escolha **Data leaks**, em **Data leaks**. Selecione **Next** para continuar.

> <img src="media/image90.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer Description automatically generated" />

3.  Na página **Name and description**, preencha os seguintes campos:

    - Name: Data leaks by a user

    - Description: This is a test policy for preventing data leaks

4.  Selecione **Next** para continuar.

> <img src="media/image91.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer Description automatically generated" />

5.  Na página **Choose users, groups, & adaptive scopes**, certifique-se de que o botão de opção **All users, groups, and adaptive scopes** esteja selecionado e clique no botão **Next** para continuar.

> <img src="media/image92.png" style="width:6.26806in;height:4.06458in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Na página **Exclude users and groups (optional)**, clique no botão **Next**.

7.  Na página **Decide whether to prioritize**, selecione **I want to priority content**. Marque as caixas **SharePoint sites**, **Sensitivity labels** e **Sensitive info types**. Clique no botão **Next**.

> <img src="media/image93.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer Description automatically generated wit medium confidence" />

8.  Na página **SharePoint sites to prioritize**, selecione **Add or edit SharePoint sites**. No painel lateral, digite https://WWLxXXXXXX.sharepoint.com/sites/ContosoWeb1, marque a caixa ao lado de **Contoso Web 1** e clique no botão **Add**. Em seguida, clique em **Next**.

> **Observação**: o prefixo do locatário **XXXXXX** está disponível na guia **Resources**.
>
> <img src="media/image94.png" style="width:6.26806in;height:3.43333in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image95.png" style="width:6.26806in;height:3.42431in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image96.png" style="width:6.26806in;height:3.40139in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Na página **Sensitivity labels to prioritize**, selecione **Add or edit sensitivity labels**. No painel lateral, digite employee, marque a caixa Internal/Employee data (HR) e clique no botão **Add**. Em seguida, clique no botão **Next**.

> <img src="media/image97.png" style="width:6.26806in;height:3.76667in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image98.png" style="width:6.26806in;height:4.03958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Na página **Sensitive info types to prioritize**, selecione **Add or edit sensitive info types**. No painel lateral, procure e selecione Credit Card Number, Contoso Employee ID e Contoso Employee EDM. Selecione **Add** e, em seguida, clique em **Next**.

\![A screenshot of a computer Description automatically generated\](./media/image79.png)

11. Na página **Decide whether to score only activity with priority content**, selecione **Get alerts for all activity**. Selecione **Next**.

> <img src="media/image99.png" style="width:6.26806in;height:4.025in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

12. Na página **Choose triggering event for this policy**, certifique-se de que o botão de opção **User performs an exfiltration activity** esteja selecionado. Em **Select which activities will trigger this policy**, selecione **Download content from SharePoint**, **Sending email with attachments to recipients outside the organisation** e **Sharing SharePoint files with people outside the organization**, e selecione **Next**.

> <img src="media/image100.png" style="width:6.26806in;height:4.1in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />
>
> <img src="media/image101.png" style="width:6.26806in;height:4.20278in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Na página **Choose thresholds for triggering events**, selecione o botão de opção **Choose your own thresholds**, defina todos os limites como 1 e selecione **Next**.

> <img src="media/image102.png" style="width:6.26806in;height:4.10694in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image103.png" style="width:6.26806in;height:3.98403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Mantenha as configurações padrão na página **Indicators** e selecione **Next**.

> <img src="media/image104.png" style="width:6.26806in;height:4.06111in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. Mantenha as configurações padrão na página **Detection options** e selecione **Next**.

> <img src="media/image105.png" style="width:6.26806in;height:4.125in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

16. Na página **Choose threshold type for indicators**, certifique-se de que o botão de opção **Choose your own thresholds** esteja selecionado. Em seguida, clique em Office indicators, utilize 1, 2 e 3 eventos para cada estágio, respectivamente, e selecione **Next**.

> <img src="media/image106.png" style="width:6.26806in;height:4.19306in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image107.png" style="width:6.26806in;height:4.10833in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image108.png" style="width:6.26806in;height:4.14861in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Na página **Review settings and finish**, selecione **Submit**.

> <img src="media/image109.png" style="width:6.26806in;height:4.17222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Na página Your policy was created, selecione Done.

> <img src="media/image110.png" style="width:6.26806in;height:4.17083in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Etapa 2 – Avaliar a política**

1.  Na página **Policies**, marque a caixa ao lado da nova política chamada **Data leaks by a user**. Em seguida, selecione **Start scoring activity for users**.

> <img src="media/image111.png" style="width:6.26806in;height:3.42361in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  No campo Reason for scoring activity, digite Testing the policy. No campo **Scoring activity for this many days (between 5 and 30)**, selecione **10 days**. No campo Score activity for these users, digite MOD e selecione MOD administrator.

> <img src="media/image68.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image69.png" style="width:6.26806in;height:3.45833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Em seguida, clique no botão **Start scoring activity**.

> <img src="media/image70.png" style="width:6.26806in;height:3.46389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Clique no botão **Close**.

> <img src="media/image112.png" style="width:6.26806in;height:5.78194in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumo:**

Neste laboratório, você primeiro preparou o ambiente sincronizando os relógios das VMs e integrando os usuários e dispositivos necessários para o Insider Risk Management no Microsoft Purview. Você habilitou insights analíticos e verificou a versão do cliente antimalware Defender em todas as VMs de destino. Após integrar os dispositivos, você criou três políticas diferentes de Insider Risk Management para monitorar e pontuar atividades relacionadas ao uso arriscado do navegador, possível roubo de dados por usuários que estão saindo da empresa e vazamentos de dados por usuários internos. Cada política foi personalizada com rótulos de confidencialidade, sites do SharePoint e sensitive information types como conteúdo prioritário, e os limites foram configurados para acionar alertas e pontuação. Por fim, você iniciou atividades de pontuação para simular cenários reais de risco interno e avaliar a eficácia das políticas configuradas.
