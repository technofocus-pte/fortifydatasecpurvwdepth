# Laboratorio 3 – Gestione dei classificatori addestrabili

## Obiettivo:

Il tenant di Contoso Ltd. contiene raccolte siti di SharePoint che
verranno utilizzate in futuro per archiviare diversi documenti e report
finanziari. A causa della natura di questi documenti, è necessario
creare un classificatore sottoponibile a training per riconoscere ed
etichettare questi file. A questo scopo, si attiveranno classificatori
con training personalizzati e ne verrà creato uno nuovo in questo lab.

## Esercizio 1 – Creazione di un classificatore addestrabile

In questa attività, Patti creerà un nuovo classificatore sottoponibile a
training e selezionerà diversi siti di SharePoint per identificare i
dati tipici creati e archiviati da Contoso Ltd.

1.  In **Microsoft Edge** aprire una **New InPrivate Window**, passare a
    `https://purview.microsoft.com` e accedere come **Patti Fernandez**
    utilizzando il nome utente
    `PattiF@WWLx{TENANTPREFIX}.onmicrosoft.com` e la password utente
    specificata nella scheda delle risorse.

2.  Nel riquadro di spostamento a sinistra, selezionare **Solutions \>
    Data Loss Prevention**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image1.png)

Uno screenshot di un computer Descrizione generata automaticamente

3.  Espandere **Classifiers** nel riquadro sinistro. Selezionare
    **Trainable Classifiers** nel riquadro di spostamento secondario.
    Selezionare **+ Create trainable classifier** per creare un nuovo
    classificatore.

![](./media/image2.png)

4.  Immettere le informazioni seguenti nella pagina **Name and describe
    your trainable classifier**:

    - Name: Contoso Company Data 

    - Description: Trainable classifier for company data produced and
      stored by Contoso Ltd. 

5.  Selezionare **Next**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image3.png)

Uno screenshot di un computer Descrizione generata automaticamente

8.  Selezionare **Choose sites** per aprire il riquadro laterale destro.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image4.png)

Uno screenshot di un computer Descrizione generata automaticamente

9.  Selezionare i siti di SharePoint seguenti e selezionare **Add**.

- Brand 

&nbsp;

- Digital Initiative Public Relations 

&nbsp;

- Work 

&nbsp;

- Sales and Marketing 

&nbsp;

- Mark 8 Project Team 

![](./media/image5.png)

10. Attendere che il sito scelto venga visualizzato nell'elenco e
    seleziona **Next**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image6.png)

Uno screenshot di un computer Descrizione generata automaticamente

11. Nella **pagina Source of the negative sample content,** selezionare
    il sito **Learn** e quindi selezionare **Next**.

12. Esaminare le impostazioni e selezionare **Create trainable
    classifier.**

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image7.png)

Uno screenshot di un computer Descrizione generata automaticamente

13. Quando viene visualizzato il messaggio **Your trainable classifier
    was created**, selezionare **Done**.

I documenti e i file nel sito SharePoint scelto sono ora in fase di
analisi, operazione che può richiedere fino a 24 ore. Una volta pronto,
puoi eseguire le seguenti operazioni.

- Testare il classificatore

- Esaminare il classificatore

- Pubblicare il classificatore

È possibile esplorare i classificatori già esistenti per un'ulteriore
revisione.

## Sommario:

È stato creato un classificatore con training personalizzato che
corrisponde ai file archiviati nei siti di SharePoint esistenti di
Contoso Ltd.
