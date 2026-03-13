**Laboratório 5 – Explorando os recursos da Proteção Adaptativa**

**Introdução**

A Proteção Adaptativa no Microsoft Purview integra o Microsoft Purview Insider Risk Management com o Microsoft Purview Data Loss Prevention (DLP). Quando o Insider Risk identifica um usuário que está envolvido em comportamento arriscado, ele é atribuído dinamicamente a um nível de risco interno. Em seguida, a Proteção Adaptativa pode criar automaticamente uma política de DLP para ajudar a proteger a organização contra o comportamento arriscado associado a esse nível de risco interno

**Objetivos**

- Definir limites de risco para a Proteção Adaptativa no Insider Risk Management.

- Criar e configurar uma política de DLP personalizada para proteção de endpoints.

- Definir condições usando trainable classifiers e níveis de risco interno.

- Aplicar ações para bloquear atividades de exfiltração de dados de alto risco.

- Habilitar a política para aplicação imediata.

**Exercício 1 – Configurar a Proteção Adaptativa**

**Tarefa 1 – Configurar os níveis de risco para a Proteção Adaptativa**

1.  Abra uma guia do navegador Microsoft Edge em uma janela normal, faça login no portal do Microsoft Purview usando as credenciais do **MOD Administrator** e navegue até **Solutions** \> **Insider risk management**.

> <img src="media/image1.png" style="width:6.26806in;height:3.34861in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  No painel esquerdo do **Insider Risk Management**, navegue e clique em **Adaptive Protection**.

> <img src="media/image2.png" style="width:6.26806in;height:3.43194in" />

3.  Na página **Adaptive Protection**, clique em **Insider risk levels**. Em seguida, navegue até a seção **Insider risk policy** e clique no menu suspenso ao lado de **Select a policy**. Navegue e marque a caixa de seleção ao lado de **Data leaks by a user**.

> <img src="media/image3.png" style="width:6.26806in;height:3.43542in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image4.png" style="width:6.26806in;height:3.37708in" />

4.  Em **Conditions for insider risk levels**, selecione User performs at least 3 data exfiltration activities, each… para o campo **Elevated risk level**. Selecione User performs at least 2 data exfiltration activities, each… para o campo **Moderate risk level**. Selecione User performs at least 1 data exfiltration activities, each… para o campo **Minor risk level**. Em seguida, role a página para baixo e selecione o botão **Save**.

> <img src="media/image5.png" style="width:6.26806in;height:3.43125in" />

5.  Clique no botão **Save**.

> <img src="media/image6.png" style="width:6.26806in;height:3.49028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarefa 2 – Criar uma política DLP de proteção adaptativa personalizada para endpoint**

1.  Na página **Adaptive Protection**, navegue e clique em **Data Loss Prevention** e, em seguida, clique em **+ Create policy**.

> <img src="media/image7.png" style="width:6.26806in;height:4.24722in" />

2.  Na página **Choose what type of data to protect**, certifique-se de que o botão de opção **Data stored in connected sources** esteja selecionado.

> <img src="media/image8.png" style="width:6.26806in;height:3.44722in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Na página **Template or custom policy**, na seção **Categories**, navegue e selecione **Custom** e, em seguida, em **Regulations**, clique em **Custom policy**.

> <img src="media/image9.png" style="width:6.26806in;height:3.41458in" />

4.  Na página **Name your DLP policy**, no campo **Name**, insira Custom Policy for Endpoint.

> <img src="media/image10.png" style="width:6.26806in;height:3.41389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Na página **Assign admin units**, clique no botão **Next**.

> <img src="media/image11.png" style="width:6.26806in;height:3.43681in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Na página **Choose where to apply the policy**, clique no botão **Next**.

> <img src="media/image12.png" style="width:6.26806in;height:3.44097in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Na página **Define policy settings**, clique no botão **Next**.

> <img src="media/image13.png" style="width:6.26806in;height:3.42847in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  Na página **Customize advanced DLP rules**, clique em **+ Create rule**.

> <img src="media/image14.png" style="width:6.26806in;height:3.40556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  No campo **Create rule**, insira Adaptive Protection block rule for Endpoint DLP

> <img src="media/image15.png" style="width:6.26806in;height:3.44375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Clique no menu suspenso ao lado de **Select one or more risk levels** e marque a caixa de seleção ao lado de **Elevated risk level**.

> <img src="media/image16.png" style="width:6.26806in;height:3.41042in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. Clique no menu suspenso ao lado de **+ Add condition** e selecione **Content contains**.

> <img src="media/image17.png" style="width:6.26806in;height:3.53958in" />

12. Na seção **Content contains**, clique no menu suspenso ao lado de **Add** e selecione **Trainable classifiers**.

> <img src="media/image18.png" style="width:6.26806in;height:3.41042in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. No painel **Trainable classifiers** exibido no lado direito, navegue e marque as caixas de seleção ao lado de **Source code**, **Agreements**, **HR** e **IP**, e clique no botão **Add**.

> <img src="media/image19.png" style="width:6.26806in;height:3.39792in" />
>
> <img src="media/image20.png" style="width:6.26806in;height:3.40972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Na seção **Actions**, clique no menu suspenso ao lado de **Add an action** e selecione **Audit or restrict activities on devices**.

> <img src="media/image21.png" style="width:6.26806in;height:3.36736in" />

15. Selecione **Block** para **Copy to clipboard**, **Copy to a removable USB device**, **Copy to a network share** e **Print**.

> <img src="media/image22.png" style="width:6.26806in;height:3.43403in" alt="A screenshot of a computer AI-generated content may be incorrect." />..
>
> <img src="media/image23.png" style="width:6.26806in;height:3.40417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. Na seção **Incident reports**, no campo **Use this severity level in admin alerts and reports**, selecione **Low** no menu suspenso. Em seguida, clique no botão **Save**.

> <img src="media/image24.png" style="width:6.26806in;height:3.39236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Clique no botão **Next**.

> <img src="media/image25.png" style="width:6.26806in;height:3.40903in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Na página **Policy mode**, selecione o botão de opção ao lado de **Turn the policy on immediately** e clique no botão **Next**.

> <img src="media/image26.png" style="width:6.26806in;height:3.41875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Na página **Review and finish**, clique no botão **Submit**.

> <img src="media/image27.png" style="width:6.26806in;height:3.41944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

20. Na página **New policy created**, clique no botão **Done**.

> <img src="media/image28.png" style="width:6.26806in;height:3.43542in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumo**

Neste exercício, você configurou a Proteção Adaptativa no Microsoft Purview, definindo inicialmente os níveis de risco interno com base em limites de atividades de exfiltração de dados. Em seguida, você criou uma política personalizada de Data Loss Prevention (DLP) para dispositivos de endpoint que utiliza a Proteção Adaptativa para restringir automaticamente atividades — como cópia para USB ou impressão — quando um risco elevado é detectado. A política direciona conteúdo sensível usando trainable classifiers e aplica ações rigorosas com base nos níveis de risco interno para mitigar possíveis vazamentos de dados.
