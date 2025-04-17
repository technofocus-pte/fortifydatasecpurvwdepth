# Laboratório 8 – Explorando os recursos da Proteção Adaptativa

## Exercício 1 – Configurando a proteção adaptativa

### Tarefa 1 – Definição dos níveis de risco para a Proteção Adaptativa

1.  No Microsoft Edge, abra uma Nova Janela InPrivate, navegue até
    `https://purview.microsoft.com` e faça login usando o locatário
    admin.

2.  Na barra de navegação, acesse **Solutions** \> **Insider risk**
    **management**.

![](./media/image1.png)

3.  Na subnavegação, selecione **Adaptive Protection (Preview).**

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image2.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

4.  Como usamos a opção de início rápido ao ativar a **Proteção
    Adaptativa**, podemos ver duas políticas de DLP criadas.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image3.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

5.  Agora clique em **Risk levels for Adaptive Protection**  no submenu
    e, no menu suspenso, selecione **Data leaks by a user**.

![Imagem quebrada](./media/image4.png)

Imagem interrompida

6.  Em **Define conditions for risk levels**, selecione **User performs
    at least 3 data exfiltration activities, each…** para risco
    **Elevated**. Selecione **User performs at least 2 data exfiltration
    activities, each…** para risco **Moderate**. Selecione **User
    performs at least 1 data exfiltration activities, each…** para risco
    **Minor**. Em seguida, clique em **Salve**.

![Imagem quebrada](./media/image5.png)

Imagem interrompida

7.  Da mesma forma, você pode personalizar as condições de todas as
    políticas disponíveis no Insider Risk Management.

8.  Agora podemos personalizar a política DLP para cada nível.

### Tarefa 2 – Explorar as políticas padrão de DLP para cada um dos níveis de risco de Proteção Adaptativa

1.  Em Adaptive Protection, selecione DLP Polices e selecione Adaptive
    Protection Policy for Endpoint DLP.

![Imagem quebrada](./media/image6.png)

Imagem interrompida

2.  Selecione **Edit**.

![Uma captura de tela de uma tela de computador Descrição gerada
automaticamente com confiança média](./media/image7.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

3.  Clique em Next até chegar a **Customize advanced DLP rules**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image8.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

4.  Verifique as regras e as condições estabelecidas para cada nível de
    risco. Clique em **Next**.

5.  Na página **Policy mode**, selecione o botão de opção próximo a
    **Turn it on right away**. Clique em **Next**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image9.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

6.  Selecione **Submit**.

![Uma captura de tela de um computador Descrição gerada
automaticamente](./media/image9.png)

Uma captura de tela de uma descrição de computador gerada
automaticamente

7.  Repita as etapas para ativar a Política de Proteção Adaptativa para
    o Teams e o Exchange DLP.

8.  Não criaremos nenhuma regra ou política por enquanto, mas você
    poderá explorar várias opções disponíveis depois de concluir o
    laboratório.
