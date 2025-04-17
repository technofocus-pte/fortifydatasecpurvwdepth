# Lab 4 – Utilizzo delle etichette di riservatezza

## Obiettivo:

In questo lab si assumerà il ruolo di Patti Fernandez, amministratore di
sistema per Contoso Ltd. L'organizzazione ha sede a Rednitzhembach, in
Germania, e sta attualmente implementando un piano di riservatezza per
garantire che tutti i documenti dei dipendenti nel reparto Risorse umane
siano stati contrassegnati con un'etichetta di riservatezza come parte
dei criteri di protezione delle informazioni dell'organizzazione.

## Esercizio 1 – Abilitazione del supporto per le etichette di riservatezza

In questa attività verranno installati il modulo MSOnline e il modulo
PowerShell di SharePoint Online e verrà abilitato il supporto per le
etichette di riservatezza nel tenant.

1.  Selezionare il simbolo di Windows nella barra delle applicazioni con
    il tasto destro del mouse e selezionare **Windows PowerShell
    (Admin)** ed eseguire come amministratore.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

Uno screenshot di un computer Descrizione generata automaticamente

2.  Confermare la finestra **User Account Control** con **Yes** e
    premere Invio.

3.  Immettere il cmdlet seguente per installare la versione più recente
    del modulo Microsoft Online PowerShell:

`Install-Module -Name MSOnline`

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Uno screenshot di un computer Descrizione generata automaticamente

4.  Confermare la finestra di dialogo di sicurezza NuGet e la finestra
    di dialogo di sicurezza del repository non attendibile con Y per Sì
    e premere **Enter**. Il completamento dell'elaborazione potrebbe
    richiedere un po' di tempo.

![BrokenImage](./media/image3.png)

Immagine rotta

5.  Immettere il cmdlet seguente per installare la versione più recente
    del modulo PowerShell di SharePoint Online:

`Install-Module -Name Microsoft.Online.SharePoint.PowerShell`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Uno screenshot di un computer Descrizione generata automaticamente

6.  Confermare la finestra di dialogo di sicurezza dell'archivio non
    attendibile con **Y** per Sì e premere Invio.

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

Uno screenshot dello schermo di un computer Descrizione generata
automaticamente

7.  Immettere il cmdlet seguente per connettersi al servizio Microsoft
    Online:

`Connect-MsolService`

![BrokenImage](./media/image6.png)

Immagine rotta

8.  Nel modulo **Sign in to your account**, accedere come **Patti
    Fernandez** utilizzando il nome utente
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` e la password utente fornita
    nella scheda delle risorse.

![A screenshot of a computer screen Description automatically
generated](./media/image7.png)

Uno screenshot dello schermo di un computer Descrizione generata
automaticamente

9.  Dopo aver effettuato l'accesso, passare alla finestra di
    **PowerShell**.

10. Immettere il cmdlet seguente per ottenere il dominio:

`$domain = get-msoldomain`

![BrokenImage](./media/image8.png)

Immagine rotta

11. Immettere il cmdlet seguente per creare l'URL di amministrazione di
    SharePoint:

`$adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"`

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

Uno screenshot dello schermo di un computer Descrizione generata
automaticamente

12. Immettere il cmdlet seguente per accedere all'interfaccia di
    amministrazione di SharePoint Online:

`Connect-SPOService -url $adminurl`

![A screenshot of a computer screen Description automatically
generated](./media/image10.png)

Uno screenshot dello schermo di un computer Descrizione generata
automaticamente

13. Nel modulo **Sign in to your account**, accedere come **MOD
    Administrator** utilizzando le credenziali fornite nella scheda
    delle risorse del tuo ambiente lab.

14. Dopo aver effettuato l'accesso, selezionare la finestra di
    PowerShell.

15. Immettere il cmdlet seguente per abilitare il supporto per le
    etichette di riservatezza:

`Set-SPOTenant -EnableAIPIntegration $true`

![BrokenImage](./media/image11.png)

Immagine rotta

16. Confermare le modifiche con **Y** per Sì e premere Invio.

![BrokenImage](./media/image12.png)

Immagine rotta

17. Chiudere la finestra di **PowerShell**.

Il supporto per le etichette di riservatezza è stato abilitato con i
siti di Teams e SharePoint.

## Esercizio 2 - Creazione di etichette di riservatezza

In questa attività, il reparto risorse umane ha richiesto un'etichetta
di riservatezza da applicare ai documenti dei dipendenti delle risorse
umane. Si creerà un'etichetta di riservatezza per i documenti interni e
un'etichetta secondaria per il reparto risorse umane.

1.  In **Microsoft Edge** andare a `https://purview.microsoft.com` e
    accedere come **Patti Fernandez** utilizzando il nome utente
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` e la password utente fornita
    nella scheda delle risorse.

2.  Nel portale di Microsoft Purview, nel riquadro di spostamento
    sinistro, selezionare **Solutions \> Information Protection**.

![](./media/image13.png)

3.  Nella barra di navigazione secondaria, selezionare **Sensitivity
    Labels \> Create Labels**.

![](./media/image14.png)

4.  Verrà avviata la procedura guidata **New sensitivity label**. Nella
    pagina **Label details** per **Name**, **Description for admins** e
    **Description for users**, immettere le informazioni seguenti:

    - Name: `Internal`

    - Display name: `Internal`

    - Description for users: `Internal sensitivity label`

    - Description for admins: `Internal sensitivity label for Contoso.`

![Graphical user interface, text, application, email Description
automatically generated](./media/image15.png)

Interfaccia utente grafica, testo, applicazione, e-mail Descrizione
generata automaticamente

5.  Selezionare **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image16.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

6.  Nella pagina **Define the scope for this label,** selezionare
    l'opzione **Items** che protegge i messaggi di posta elettronica, i
    file e gli elementi di Power BI. Deseleziona la casella accanto a
    **Meetings**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

Uno screenshot di un computer Descrizione generata automaticamente

7.  Selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

Uno screenshot di un computer Descrizione generata automaticamente

8.  Nella pagina **Choose protection settings for labeled items,**
    selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

Uno screenshot di un computer Descrizione generata automaticamente

9.  Nella pagina **Auto-labeling** di etichette per file e messaggi di
    posta elettronica, selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

Uno screenshot di un computer Descrizione generata automaticamente

10. Nella pagina **Define protection settings for groups and sites,**
    selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

Uno screenshot di un computer Descrizione generata automaticamente

11. Nella pagina **Auto-labeling for schematized data assets
    (preview),** selezionare **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image22.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

12. Nella pagina **Review your settings and finish,** selezionare
    **Create label.**

![A screenshot of a computer Description automatically
generated](./media/image23.png)

Uno screenshot di un computer Descrizione generata automaticamente

13. L'etichetta verrà creata e al termine, verrà visualizzato un
    messaggio: **Your sensitivity label was created**

14. Selezionare **Don’t create a policy yet,** quindi selezionare
    **Done**.

![A screenshot of a computer screen Description automatically
generated](./media/image24.png)

Uno screenshot dello schermo di un computer Descrizione generata
automaticamente

15. Nella pagina **Information protection**, evidenziare (senza
    selezionare) l'etichetta interna appena creata e selezionare il
    verticale**...**.

16. Selezionare **+ Add sub label** dal menu a discesa.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

Uno screenshot di un computer Descrizione generata automaticamente

17. Verrà avviata la procedura guidata **New sensitivity label**. Nella
    pagina **Label details,** immettere le informazioni seguenti:

    - Name: `Employee data (HR)`

    - Display name: `Employee data (HR)`

    - Description for users:
      `This HR label is the default label for all specified documents in the HR Department.`

    - Description for admins:
      `This label is created in consultation with Ms.Jones (Head of HR department). Contact her, when you want to change settings of the label.`

![](./media/image26.png)

18. Selezionare **Next**.

![](./media/image27.png)

19. Nella pagina **Define the scope for this label,** selezionare
    l'opzione **Items** che protegge messaggi di posta elettronica, file
    e riunioni. Selezionare **Next**.

![](./media/image28.png)

20. Nella pagina **Choose protection settings for labeled items,**
    selezionare l'opzione **Control Access**. Selezionare **Next**.

![](./media/image29.png)

21. Nella pagina **Access Control,** selezionare **Configure access
    control ettings**.

![](./media/image30.png)

22. Immettere le seguenti informazioni nelle impostazioni di
    crittografia:

    - Assign permissions now or let users decide?: **Assign permissions
      now**

    - User access to content expires: **Never**

    - Allow offline access: **Only for a number of days**

    - Users have offline access to the content for this many days:
      **15**

![A screenshot of a computer Description automatically
generated](./media/image31.png)

Uno screenshot di un computer Descrizione generata automaticamente

23. Selezionare il link **Assign permissions**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

Uno screenshot di un computer Descrizione generata automaticamente

24. Nel riquadro **Assign permissions,** selezionare l'opzione **+ Add
    any authenticated users**.

![BrokenImage](./media/image33.png)

Immagine rotta

25. Selezionare **Save**.

![BrokenImage](./media/image34.png)

Immagine rotta

26. Nella pagina **Encryption,** selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

Uno screenshot di un computer Descrizione generata automaticamente

27. Nella pagina **Auto-labeling for files and emails,** selezionare
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

Uno screenshot di un computer Descrizione generata automaticamente

28. Nella pagina **Define protection settings for groups and sites,**
    selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

Uno screenshot di un computer Descrizione generata automaticamente

29. Nella pagina **Auto-labeling for schematized data assests
    (preview),** selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

Uno screenshot di un computer Descrizione generata automaticamente

30. Nella pagina **Review your settings and finish,** selezionare
    **Create label**.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

Uno screenshot di un computer Descrizione generata automaticamente

31. L'etichetta verrà creata e, al termine, verrà visualizzato un
    messaggio **Your sensitivity label was created**.

32. Selezionare **Don’t create a policy yet,** quindi selezionare
    **Done**.

![A screenshot of a computer screen Description automatically
generated](./media/image40.png)

Uno screenshot dello schermo di un computer Descrizione generata
automaticamente

33. Tieni aperta la scheda per passare all'attività successiva.

È stata creata un'etichetta di riservatezza per i criteri interni
dell'organizzazione e un'etichetta secondaria di riservatezza per il
reparto Risorse umane (HR).

## Esercizio 3 - Pubblicazione di etichette di riservatezza

A questo punto si pubblicherà l'etichetta di riservatezza interna e HR
in modo che le etichette di riservatezza pubblicate siano disponibili
per gli utenti HR da applicare ai propri documenti HR.

1.  In **Microsoft Edge** andare a `https://purview.microsoft.com` e
    accedi come **Patti Fernandez** utilizzando il nome utente
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` e la password utente fornita
    nella scheda delle risorse.

&nbsp;

1.  Nel portale di Microsoft Purview, nel riquadro di spostamento
    sinistro, selezionare **Solutions \> Information Protection**.

![](./media/image13.png)

3.  Nella barra di spostamento secondaria selezionare **Sensitivity
    Labels \> Publish Labels**.

![](./media/image41.png)

4.  Verrà avviata la pubblicazione guidata delle etichette di
    riservatezza.

5.  Nella pagina **Choose sensitivity labels to publish,** selezionare
    il collegamento **Choose sensitivity labels to publish**.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

Uno screenshot di un computer Descrizione generata automaticamente

6.  Sulla destra verrà visualizzata una barra laterale denominata
    **Sensitivity labels to publish**.

7.  Selezionare le caselle di controllo **Internal** e
    **Internal/Employee Data (HR).**

![A screenshot of a computer Description automatically
generated](./media/image43.png)

Uno screenshot di un computer Descrizione generata automaticamente

8.  Selezionare **Add**.

![A screenshot of a computer Description automatically
generated](./media/image44.png)

Uno screenshot di un computer Descrizione generata automaticamente

9.  Nella pagina **Choose sensitivity labels to publish,** selezionare
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

Uno screenshot di un computer Descrizione generata automaticamente

10. Nella pagina **Publish to users and groups,** selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

Uno screenshot di un computer Descrizione generata automaticamente

11. Nella pagina **Policy settings,** selezionare **Next**.

![BrokenImage](./media/image47.png)

Immagine rotta

12. Nella pagina **Apply a default label to documents,** selezionare
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

Uno screenshot di un computer Descrizione generata automaticamente

13. Nella pagina **Apply a default label to emails,** selezionare
    **Next**.

14. In **Default settings for meetings and calendar events,**
    selezionare **Next**.

15. Nella pagina **Default settings for Fabric and Power BI content,**
    selezionare **Next**.

&nbsp;

13. Nella pagina **Name your policy,** immettere le informazioni
    seguenti:

    - Name: `Internal HR employee data`

    - Enter a description for your sensitivity label policy:
      `This HR label is to be applied to internal HR employee data.`

![Graphical user interface, text, application, email Description
automatically generated](./media/image49.png)

Interfaccia utente grafica, testo, applicazione, e-mail Descrizione
generata automaticamente

17. Selezionare **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image50.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

18. Nella pagina **Review and finish,** selezionare **Submit**.

![Graphical user interface, text, application Description automatically
generated](./media/image51.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

19. Il criterio verrà creato e, al termine, verrà visualizzato un
    messaggio **New policy created**.

20. Selezionare **Done and proceed to next task without closing the
    window**.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

Uno screenshot di un computer Descrizione generata automaticamente

Le etichette di riservatezza Interno e HR sono state pubblicate
correttamente. Si noti che possono essere necessarie fino a 24 ore prima
che le modifiche vengano replicate a tutti gli utenti e i servizi.

## Esercizio 4 - Utilizzo delle etichette di riservatezza

In questa attività verranno create etichette di riservatezza nei
messaggi di posta elettronica di Word e Outlook. Il documento creato
verrà archiviato in OneDrive e inviato a un dipendente delle risorse
umane via e-mail.

1.  Andare su `https://portal.office.com` e accedi come **Patti
    Fernandez**.

2.  Se viene visualizzato il messaggio **Get your work done with Office
    365**, chiuderlo.

![Graphical user interface Description automatically
generated](./media/image53.png)

Interfaccia utente grafica Descrizione generata automaticamente

3.  Selezionare il simbolo di **Microsoft Word** dal riquadro laterale
    sinistro per aprire Word Online.

![Graphical user interface, website Description automatically
generated](./media/image54.png)

Interfaccia utente grafica, sito web Descrizione generata
automaticamente

4.  Selezionare **New blank document** per creare un nuovo documento.

![Graphical user interface, website Description automatically
generated](./media/image55.png)

Interfaccia utente grafica, sito web Descrizione generata
automaticamente

5.  Se viene visualizzato un messaggio **Your privacy options**,
    chiudilo selezionando **Close**.

![BrokenImage](./media/image56.png)

Immagine rotta

6.  Inserire i seguenti contenuti nel documento word:

`Important HR employee document.`

![Graphical user interface, application, Word Description automatically
generated](./media/image57.png)

Interfaccia utente grafica, applicazione, descrizione Word generata
automaticamente

7.  Selezionare **Sensitivity** dal riquadro superiore per aprire il
    menu a discesa.

![Graphical user interface, application, Word Description automatically
generated](./media/image58.png)

Interfaccia utente grafica, applicazione, descrizione Word generata
automaticamente

8.  Selezionare **Internal \> Employee data (HR)** per applicare
    l'etichetta.

**Nota**: Tenere presente che lo script eseguito nell'attività 1 di
questo esercizio ha attivato le etichette di riservatezza in Word per il
tenant. A volte può essere necessaria un'ora prima che l'attivazione
venga realizzata in Microsoft Word online. Se non viene visualizzato il
menu Etichetta di riservatezza in Word, potrebbe essere necessario
tornare a questo lab in un secondo momento o assicurarsi di aver
completato correttamente l'attività 1 di questo esercizio.

![BrokenImage](./media/image59.png)

Immagine rotta

9.  Selezionare **Document – Saved** in alto a sinistra della finestra,
    inserire **HR Document** come nome del file e premere il tasto
    **Enter**.

![Graphical user interface, application, Word Description automatically
generated](./media/image60.png)

Interfaccia utente grafica, applicazione, descrizione Word generata
automaticamente

10. Chiudere la scheda delle parole per tornare alla scheda **Office
    365**. Selezionare il simbolo di **Outlook** dal riquadro di
    sinistra per aprire **Outlook** sul Web.

![Graphical user interface, text, application Description automatically
generated](./media/image61.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

11. Se viene visualizzato un messaggio di benvenuto, chiuderlo
    selezionando la **X**.

12. In Outlook sul Web, selezionare **New message** in alto a sinistra
    nella finestra.

![A screenshot of a computer Description automatically
generated](./media/image62.png)

Uno screenshot di un computer Descrizione generata automaticamente

13. Nel campo **To**, immettere il nome: **Adele** e selezionare **Adele
    Vance** dall'elenco a discesa.

![](./media/image63.png)

14. Nel campo dell'oggetto inserire: Employee data for HR.

15. All'interno del messaggio di posta elettronica (il pannello dei
    contenuti di grandi dimensioni nella parte inferiore della pagina),
    inserire il seguente messaggio:

&nbsp;

    DearMs. Adele,
    Please find attached the important HR employee document.
    Kind regards,
    Patti Fernandez

![A screenshot of a computer Description automatically
generated](./media/image64.png)

Uno screenshot di un computer Descrizione generata automaticamente

16. Selezionare **il simbolo della** **graffetta** dal menu in basso.

![](./media/image65.png)

17. Selezionare **HR Document.docx** sotto **Suggested attachments** per
    allegare il documento.

18. Selezionare **Send** per inviare il messaggio e-mail con il
    documento allegato.

19. Lasciare aperta la finestra del browser.

È stato creato un documento Word HR con un'etichetta di riservatezza,
che è stato salvato in OneDrive. È stato quindi inviato un messaggio di
posta elettronica al documento a un membro del personale in cui è stato
impostato anche il messaggio di posta elettronica con un'etichetta di
riservatezza.

Nell'account di prova, tieni presente che sarai in grado di inviare la
posta, ma verrà respinta e non sarà in grado di raggiungere il
destinatario dal tuo attuale inquilino.

## Esercizio 5 - Configurazione dell'etichettatura automatica

In questa attività, verrà creata un **Sensitivity Label** che
etichetterà automaticamente i documenti e le e-mail che contengono
informazioni relative al **European General Data Protection Regulation
(GPDR).**

1.  In **Microsoft Edge**, la scheda del portale di Microsoft Purview
    dovrebbe essere ancora aperta.

2.  Dovresti aver effettuato l'accesso al portale come **Patti
    Fernandez**.

3.  In **Information protection**, selezionare **Label**, evidenziare
    (senza selezionare) l' etichetta **Internal** esistente e
    selezionare i tre puntini. Selezionare la voce di menu **+ Create
    sublabel**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

Uno screenshot di un computer Descrizione generata automaticamente

4.  Verrà avviata la procedura guidata **New sensitivity label**. Nella
    pagina **label details**, inserire le seguenti informazioni:

    - Name: `GDPR Germany`

    - Display name: `GDPR Germany`

    - Description for users:
      `This document or email contains data related to the European General Data Protection Regulation(GPDR) for the region Germany.`

    - Description for admins:
      `This label is auto applied to German GDPR documents.`

5.  Selezionare **Next**.

![BrokenImage](./media/image67.png)

Immagine rotta

6.  Nella pagina **Define the scope for this label,** selezionare
    l'opzione **Items,** che protegge gli elementi File, E-mail e
    Riunioni. Quindi selezionare **Next**.

![BrokenImage](./media/image68.png)

Immagine rotta

7.  Nella pagina **Choose protection settings for labeled items,**
    selezionare **Next**.

![BrokenImage](./media/image69.png)

Immagine rotta

8.  Nella pagina **Auto-labeling for files and emails**, impostare
    **Auto-labeling for files and emails** su abilitata.

![Graphical user interface, text, application Description automatically
generated](./media/image70.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

9.  Nella sezione **Detect content that matches these conditions**,
    selezionare **+Add condition**, quindi selezionare **Content
    contains**.

![BrokenImage](./media/image71.png)

Immagine rotta

10. Nella sezione **Content contains,** selezionare **Add** testo,
    quindi selezionare **Sensitive info types**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

Uno screenshot di un computer Descrizione generata automaticamente

11. Sulla destra verrà visualizzato un pannello **Sensitive info
    types**.

12. Nel pannello di ricerca **Search for sensitive info types**,
    inserire le seguenti informazioni:

`German`

13. Premere il tasto Invio sulla tastiera, i risultati mostreranno i
    tipi di informazioni sulla sensibilità relative alla Germania.
    Premere la casella di controllo **Select all**.

![BrokenImage](./media/image73.png)

Immagine rotta

14. Selezionare **Add**.

![BrokenImage](./media/image74.png)

Immagine rotta

15. Selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

Uno screenshot di un computer Descrizione generata automaticamente

16. Nella pagina **Define protection settings for groups and sites,**
    selezionare **Next**.

![A screenshot of a computer Description automatically
generated](./media/image76.png)

Uno screenshot di un computer Descrizione generata automaticamente

17. Nella pagina **Auto-labeling for schematized data assets
    (preview),** selezionare **Next**.

18. Se si viene reindirizzati alla pagina **Default settings for Fabric
    and Power BI content page**, selezionare **Next**.

&nbsp;

17. Nella pagina **Review your settings and finish,** selezionare
    **Create label**.

18. L'etichetta verrà creata e al termine, verrà visualizzato un
    messaggio: **Your sensitivity label was created**. In Passaggi
    successivi selezionare **Don’t create a policy yet**. Quindi
    seleziona **Done**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image77.png)

Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente

21. Nella barra di spostamento secondaria selezionare **Sensitivity
    Labels \> Publish Labels**.

![](./media/image41.png)

22. Verrà avviata **Publish sensitivity labels wizard**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image78.png)

Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente

23. Nella pagina **Choose sensitivity labels to publish,** selezionare
    il collegamento **Choose sensitivity labels to publish**.

![A screenshot of a computer Description automatically
generated](./media/image79.png)

Uno screenshot di un computer Descrizione generata automaticamente

24. Sulla destra verrà visualizzata una barra laterale denominata
    **Sensitivity labels to publish**.

![Graphical user interface, application, Word Description automatically
generated](./media/image80.png)

Interfaccia utente grafica, applicazione, descrizione Word generata
automaticamente

25. Selezionare la casella di controllo **Internal** e **Internal/GDPR
    Germany** e selezionare **Add**.

![Graphical user interface, application, Word Description automatically
generated](./media/image81.png)

Interfaccia utente grafica, applicazione, descrizione Word generata
automaticamente

26. Nella pagina **Choose sensitivity labels to publish,** selezionare
    **Next**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image82.png)

Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente

27. Nella pagina **Publish to users and groups,** selezionare **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image83.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

28. Nella pagina **Policy settings,** selezionare **Next**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image84.png)

Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente

29. Nella pagina **Apply a default label to documents,** selezionare
    **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image85.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

30. Nella pagina **Apply a default label to emails,** selezionare
    **Next**.

31. In **Default settings for meetings and calendar events,**
    selezionare **Next**.

32. Nella pagina **Default settings for Fabric and Power BI content,**
    selezionare **Next**.

&nbsp;

34. Nella pagina **Name your policy,** immettere le informazioni
    seguenti:

    - Name: `GDPR Germany policy`

    - Enter a description for your sensitivity label policy:
      `This auto apply sensitivity labels policy is for the GDPR region of Germany.`

35. Selezionare **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image86.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

35. Nella pagina **Review and finish,** selezionare **Submit**.

![Graphical user interface, application Description automatically
generated](./media/image87.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

36. Il criterio verrà creato e, al termine, verrà visualizzato il
    messaggio **New policy created**.

37. Selezionare **Done**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image88.png)

Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente

## Sommario:

È stata creata e pubblicata un'etichetta di riservatezza di applicazione
automatica per i documenti GDPR nell'area Germania.

Tenere presente che l'applicazione delle etichette di riservatezza
applicate automaticamente può richiedere fino a 24 ore, poiché questa
durata sarà più lunga se applicata a più di 25.000 documenti (ovvero il
limite giornaliero).
