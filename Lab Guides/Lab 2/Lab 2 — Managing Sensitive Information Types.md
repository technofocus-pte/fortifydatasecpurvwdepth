# Lab 2 — Gestione dei tipi di informazioni sensibili

## Obiettivo:

In precedenza, Contoso Ltd. aveva problemi con i dipendenti che
inviavano accidentalmente informazioni personali dai clienti durante
l'utilizzo di ticket di supporto nella soluzione di ticketing.

Per informare gli utenti in futuro, è necessario un tipo di informazioni
riservate personalizzato per identificare gli ID dei dipendenti nei
messaggi di posta elettronica e nei documenti, costituiti da tre
caratteri maiuscoli e sei numeri, usando i tipi di informazioni
riservate. Per ridurre il tasso di falsi positivi, verranno utilizzate
le parole chiave " Employee" e "ID".

In questo Lab creerai:

- Un nuovo tipo di informazioni riservate personalizzato

- un database per la classificazione basata su EDM

- Dizionario delle parole chiave

## Esercizio 1 – Creazione di tipi di informazioni riservate personalizzati

In questo esercizio si userà il modulo **Security & Compliance Center
PowerShell** per creare un nuovo tipo di informazioni riservate
personalizzato che riconosce il modello di ID dipendente vicino alle
parole chiave " Employee" e "ID".

1.  In **Microsoft Edge** aprire una **nuova finestra InPrivate
    Window**, passare a `https://purview.microsoft.com` e accedere come
    **Patti Fernandez** utilizzando il nome utente
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` e la password utente
    specificata nella scheda delle risorse. Se richiesto, accetta i
    termini e le condizioni e selezionare **Get started**.

2.  Nel riquadro di spostamento a sinistra, selezionare **Solutions \>
    Data Loss Prevention**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  Selezionare **Classifiers** nel riquadro sinistro. Selezionare
    **Sensitive info types** dal riquadro di navigazione secondario.
    Selezionare **+Create sensitive info type** per aprire la procedura
    guidata per un nuovo tipo di informazioni riservate.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image2.png)

Uno screenshot di un computer Descrizione generata automaticamente

4.  Nella pagina **Name your sensitive info type,** immettere le
    informazioni seguenti:

    - **Name**: `ID dipendente Contoso`

    - **Description**: `modello per gli ID dipendente di Contoso.`

5.  Selezionare **Next**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image3.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

6.  Nella pagina **Define patterns for this sensitive info type**
    selezionare **Create pattern**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image4.png)

Uno screenshot di un computer Descrizione generata automaticamente

7.  Nel riquadro **New pattern** a destra**,** selezionare **Add primary
    element** e selezionare **Regular expression**.

![Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente](./media/image5.png)

Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente

8.  Nel nuovo riquadro di destra **Add a regular expression**, immettere
    quanto segue:

    - **ID**: `ID Contoso`

    - **Regular expression**: `\s[A-Z]{3}[0-9]{6}\s`

    - Selezionare **String match**

9.  Selezionare **Done**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image6.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

10. Nel riquadro **New pattern** a destra, sotto **Supporting
    elements**, selezionare **+ Add supporting elements or group of
    elements** e selezionare **Keyword list**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image7.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

10. Nel nuovo riquadro di destra **Add a keyword list**, inserire quanto
    segue:

    - **ID**: Employee ID keywords

    - **Case insensitive**:

&nbsp;

    Employee 
    ID 

11. Selezionare il radiale per ***Word match*** nel campo **Case
    Sensitive**

12. Selezionare **Done**.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image8.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

13. Nelle finestre Nuovo modello, ridurre il valore di **Character
    proximity** a ***100*** caratteri.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image9.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

14. Selezionare il pulsante **Create**.

15. Tornare alla pagina **Define patterns for this sensitive info type**
    e selezionare **Next**.

![Interfaccia utente grafica, testo, applicazione, descrizione di Teams
generata automaticamente](./media/image10.png)

Interfaccia utente grafica, testo, applicazione, descrizione di Teams
generata automaticamente

16. Nella pagina **Choose the recommended confidence level to show in
    compliance policies**, usare il valore predefinito e selezionare
    **Next**.

![Immagine rotta](./media/image11.png)

Immagine rotta

17. Nella pagina **Review settings and finish,** esaminare le
    impostazioni e selezionare **Create**. Una volta creato
    correttamente, selezionare **Done**.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image12.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

18. Lascia aperta la finestra del browser.

È stato creato un nuovo tipo di informazioni riservate per identificare
gli ID dei dipendenti nello schema di tre caratteri maiuscoli, sei
numeri e le parole chiave "Employee" o "ID" entro un intervallo di 100
caratteri.

## Esercizio 2 - Creazione di un tipo di informazioni di classificazione basato su EDM

Come modello di ricerca aggiuntivo, verrà creata una classificazione
basata su EDM con uno schema di database di dati dei dipendenti. Il file
di origine del database verrà formattato con i seguenti campi dati dei
dipendenti: Nome, Data di nascita, Indirizzo e ID dipendente.

1.  Selezionare **Solutions \> Data Loss Prevention \> Classifiers**,
    passare a **EDM classifiers**, disattivare **New EDM experience** e
    da Schema EDM, selezionare **+ Create EDM schema** per creare una
    nuova definizione di schema.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image13.png)

Uno screenshot di un computer Descrizione generata automaticamente

2.  Nel campo **Name**, immettere `employeedb`.

3.  Nel campo **Description,** immettere Employee Database schema..

4.  Abilitare **Employee Database schema**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image14.png)

Uno screenshot di un computer Descrizione generata automaticamente

5.  Fare clic sul menu a discesa **Choose delimiters and punctuation to
    ignore** e selezionare **Hyphen, Period, Space, Open parenthesis** e
    **Close parenthesis**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image15.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

6.  Nel primo nome del campo Schema, immettere **Name** e contrassegnare
    la casella **Field is searchable**.

7.  Selezionare **+ Add schema data field** dall'estremità inferiore.

![Immagine rotta](./media/image16.png)

Immagine rotta

8.  In **Schema field name**, sotto **Schema field \#2**, inserire
    Birthdate.

9.  Selezionare **+ Add schema data field** dall'estremità inferiore.

10. In **Schema field name**, sotto **Schema field \#3**, inserire
    `StreetAddress`.

11. Selezionare **+ Add schema data field** dall'estremità inferiore
    un'ultima volta.

12. In **Schema field name**, sotto **Schema field \#4**, immettere
    `EmployeeID`.

13. Selezionare **Field is searchable**.

14. Selezionare **Save**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image17.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

15. Selezionare **EDM sensitive info types** nel riquadro sinistro e
    selezionare **+ Create EDM sensitive info type** per aprire la
    procedura guidata del **EDM rule package**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

16. Nella pagina **Define data store schema,** selezionare **Choose an
    existing EDM schema**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image19.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

17. Selezionare **employeedb** e selezionare **Add**.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image20.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

18. Esaminare lo schema dell'archivio dati e selezionare **Next**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image21.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

19. Nella pagina **Define patterns for this EDM sensitive info type,**
    selezionare **+ Create pattern**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image22.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

20. Nel riquadro **New pattern** sul lato destro, nel campo **Primary
    element**, selezionare ***EmployeeID***.

21. Sotto **Primary element’s sensitive info type**, selezionare
    **Choose sensitive info type**.

![Uno screenshot di un modello Descrizione generato
automaticamente](./media/image23.png)

Uno screenshot di un modello Descrizione generato automaticamente

22. Nella barra di **Search**, immettere ***Contoso*** e premere il
    tasto INVIO.

23. Selezionare **Contoso Employee IDs** e selezionare **Done**.

24. Selezionare **Done**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image24.png)

Uno screenshot di un computer Descrizione generata automaticamente

25. Selezionare **Next,** nella schermata **Define patterns for this EDM
    sensitive info type**.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image25.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

26. In **Choose the recommended confidence level and character
    proximity**, lasciare che il valore predefinito venga mantenuto e
    selezionare **Next**.

![Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente](./media/image26.png)

Interfaccia utente grafica, testo, applicazione, descrizione Word
generata automaticamente

27. Nella pagina **Name and describe your EDM sensitive info type,**
    immettere `Contoso Employee EDM` per il nome.

28. Nel campo **Description for admins,** immettere **EDM-based
    sensitive information type for employee personal information.**.
    Selezionare **Next.**

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image27.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

29. Rivedere le impostazioni e selezionare **Submit**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image28.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

30. Nella pagina **Your EDM sensitive info type was created,**
    selezionare **Done**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image29.png)

Uno screenshot di un computer Descrizione generata automaticamente

31. Lasciare aperto il browser con il portale di Microsoft Purview.

È stato creato un nuovo tipo di informazioni riservate di
classificazione basata su EDM per l'identificazione dei dati dei
dipendenti da un'origine file di database.

## Esercizio 3 - Creazione di un'origine dati di classificazione basata su EDM

Per associare la classificazione basata su EDM a un database contenente
dati sensibili, è necessario eseguire l'hashing e il caricamento dei
dati effettivi per il tipo di informazioni riservate tramite lo
strumento EDM Upload Agent.

1.  In **Microsoft Edge** passare a
    `https://go.microsoft.com/fwlink/?linkid=2088639` per accedere
    all'agente di download EDM.

2.  Selezionare **Run** per scaricare e installare lo strumento.

![Immagine rotta](./media/image30.png)

Immagine rotta

3.  Nella configurazione guidata **Microsoft Exact Data Match Upload
    Agent Setup,** selezionare **Next**.

    - Selezionare **I accept the terms in the License Agreement** e
      selezionare **Next**.

    - Non modificare il percorso predefinito **Destination Folder** e
      selezionare **Next**.

    - Selezionare **Install** per eseguire l'installazione.

    - Quando si apre la finestra **User Account Control**, selezionare
      **Yes**.

    - Se ti viene chiesto di accedere, accedere tramite l'account di
      **Patti** .

    - Al termine dell'installazione, selezionare **Finish**.

    - Selezionare il simbolo di Windows in basso a sinistra per aprire
      il menu di avvio, accedere a **Notepad** e selezionare **Notepad**
      dal menu di avvio.

    - Immettere il testo seguente nella prima riga della finestra del
      blocco note (assicurarsi di immettere tutti i tre seguenti in
      nuove righe).

&nbsp;

    Name,Birthdate,StreetAddress,EmployeeID 
    Patti Fernandez,01.06.1980,1Main Street,CSO123456 
    Christie Cline,31.01.1985,2Secondary Street,CSO654321

4.  Selezionare File e Salva con nome: `EmployeeData.csv`

5.  Selezionare l'elenco a discesa in **Save as type:** e selezionare
    **All Files (*.*).**

6.  Selezionare l'elenco a discesa in **Encoding:** e selezionare
    **UTF-8** e selezionare **Save**.

![Immagine rotta](./media/image31.png)

Immagine rotta

7.  Chiudere la finestra Notepad.

8.  Selezionare il simbolo di Windows nella barra delle applicazioni con
    il tasto destro del mouse e selezionare **Windows PowerShell
    (Admin)** ed eseguire come amministratore.

![Immagine rotta](./media/image32.png)

Immagine rotta

9.  Quando si apre la finestra **User Account Control**, selezionare
    **Yes**.

10. Passare alla directory dell'agente di caricamento EDM:

cd "C:\Program Files\Microsoft\EdmUploadAgent"

![Descrizione del testo generata automaticamente](./media/image33.png)

Descrizione del testo generata automaticamente

11. Autorizzare con l'account a caricare il database nel tenant
    eseguendo il cmdlet seguente:

.\EdmUploadAgent.exe /Authorize

![Immagine rotta](./media/image34.png)

Immagine rotta

12. Quando viene visualizzata la finestra **Pick an account**, accedere
    come **Patti Fernandez** utilizzando il nome utente
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` e la password utente fornita
    nella scheda delle risorse (o la nuova password reimpostata).

**Nota**: per i passaggi successivi, assicurati che il percorso dei file
sia simile al percorso della tua VM. Potrebbe essere diverso dalle
istruzioni o dagli screenshot. In tal caso, si prega di modificare il
percorso del file nei comandi di conseguenza.

13. Scaricare la definizione dello schema del database del tipo di
    informazioni riservate di classificazione basata su EDM eseguendo lo
    script seguente in PowerShell

.\EdmUploadAgent.exe /SaveSchema /DataStoreName employeedb /OutputDir
"C:\Users\Admin\Documents\\

**Nota**: se l'ultimo comando non riesce, è possibile che sia necessario
più tempo prima che venga applicata l'appartenenza al gruppo
**EDM_DataUploaders**. Può essere necessaria fino a un'ora prima che sia
possibile scaricare il file di schema. In caso di errore, passare
all'attività successiva e tornare a questo passaggio in un secondo
momento. In alternativa, controllare il percorso della cartella dei
documenti nella macchina virtuale.

![Immagine rotta](./media/image35.png)

Immagine rotta

14. Eseguire l'hashing del file di database e caricarlo nel tipo di
    informazioni riservate di classificazione basato su EDM eseguendo lo
    script seguente in PowerShell:

.\EdmUploadAgent.exe /UploadData /DataStoreName employeedb /DataFile
"C:\Users\Admin\Documents\EmployeeData.csv" /HashLocation
"C:\Users\Admin\Documents\\ /Schema
"C:\Users\Admin\Documents\employeedb.xml" 

![Immagine rotta](./media/image36.png)

Immagine rotta

**Nota:** se ricevi i seguenti errori

Tipo di errore: System.IO.FileNotFoundException

Messaggio di errore: Impossibile trovare il file specificato.

Controllare il percorso in cui hai salvato il file EmployeeData.csv

![Descrizione del testo generata automaticamente](./media/image37.png)

Descrizione del testo generata automaticamente

15. Controllare l'avanzamento del caricamento fino a quando lo stato non
    diventa completato, quindi eseguire il comando di PowerShell
    seguente:

`.\EdmUploadAgent.exe /GetSession /DataStoreName employeedb`

![Immagine rotta](./media/image38.png)

Immagine rotta

L'hashing e il caricamento di un file di database per un tipo di
informazioni riservate di classificazione basate su EDM sono stati
completati.

## Esercizio 4 – Creazione di un dizionario di parole chiave

Diverse violazioni della perdita di informazioni personali si sono
verificate quando gli utenti hanno inviato e-mail dopo che i colleghi
hanno segnalato un congedo per malattia. Quando ciò accadeva, veniva
diffusa la ragione della malattia o della malattia. Non vogliamo che ciò
accada.

1.  In **Microsoft Edge,** aprire una **New InPrivate Window**, passare
    a `https://purview.microsoft.com` e accedere come **Patti
    Fernandez** utilizzando il nome utente
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` e la password utente
    specificata nella scheda delle risorse.

2.  Nel riquadro di spostamento a sinistra, selezionare **Solutions \>
    Data Loss Prevention**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image1.png)

Uno screenshot di un computer Descrizione generata automaticamente

3.  Selezionare **Classifiers** nel riquadro sinistro. Selezionare
    **Sensitive info types** dal riquadro di navigazione secondario.
    Selezionare **+Create sensitive info type** per aprire la procedura
    guidata per un nuovo tipo di informazioni riservate.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image2.png)

Uno screenshot di un computer Descrizione generata automaticamente

4.  Nella pagina **Name your sensitive info type,** immettere quanto
    segue:

- Name: Contoso Diseases List 

&nbsp;

- Description: List of possible diseases of employees. 

![Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente](./media/image39.png)

Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente

5.  Selezionare **Next**.

6.  Nella pagina **Define patterns for this sensitive info type,**
    selezionare **+ Create pattern**.

![Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente](./media/image40.png)

Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente

7.  Selezionare il campo a discesa sotto **Primary element** e
    selezionare **Keyword dictionary**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image41.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

8.  Nella pagina **Add a keyword dictionary**, inserire il nome Diseases
    Dictionary.

9.  Nell'area **Keywords,** immettere le seguenti parole chiave,
    ciascuna in una riga separata

flu   
influenza   
cold   
bronchitis   
otitis 

![Immagine rotta](./media/image42.png)

Immagine rotta

10. Selezionare **Done**.

11. Sotto **Supporting elements**, selezionare **+ Add supporting
    elements or group of elements** a discesa e selezionare **keyword
    list** per aggiungere ulteriore supporto per il dizionario di parole
    chiave.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image43.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

12. Nella pagina **Add a keyword list**, immettere **Employee absence**
    nel campo **ID**. Nella casella **Case insensitive**, immettere le
    parole chiave seguenti, ciascuna in una riga separata

employee   
absence   
reason 

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image44.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

13. Selezionare **Done**.

14. Nella pagina **New pattern,** esaminare la configurazione e
    selezionare **Create**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image45.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

15. Nel **Define patterns for this sensitive info type,** selezionare
    **Next**.

![Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente](./media/image46.png)

Interfaccia utente grafica, applicazione, Teams Descrizione generata
automaticamente

16. In **Choose the recommended confidence level to show in compliance
    policies**, lasciare che il valore predefinito venga mantenuto e
    selezionare **Next**.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image47.png)

Uno screenshot di un computer Descrizione generata automaticamente

17. Nella pagina **Review settings and finish,** controllare le
    impostazioni e selezionare **Create**. Al termine del processo,
    selezionare **Done**.

![Immagine rotta](./media/image48.png)

Immagine rotta

18. Lasciare aperta la finestra del browser nel portale di Microsoft
    Purview.

È stato creato un nuovo tipo di informazioni riservate basato su un
dizionario di parole chiave e sono state aggiunte altre parole chiave
per ridurre il tasso di falsi positivi. Procedi con l'attività
successiva.

## Esercizio 5 - Utilizzo di tipi di informazioni riservate personalizzati

I tipi di informazioni riservate personalizzate devono essere sempre
testati prima di usarli nei criteri, altrimenti potrebbero verificarsi
perdite di dati a causa di un modello di ricerca personalizzato
malfunzionante.

1.  Selezionare il simbolo di Windows in basso a sinistra per aprire il
    menu di avvio, accedere a **Notepad** e selezionare **Notepad** dal
    menu di avvio.

2.  Immettere il testo seguente nella finestra del blocco note

Employee Patti Fernandez EMP123456 is on absence because of the
flu/influenza 

3.  Selezionare **File** e salvare come `SickTestData` e selezionare
    **Save**.

4.  Chiudere la finestra Notepad.

5.  In **Microsoft Edge**, la scheda del portale di Microsoft Purview
    dovrebbe essere ancora aperta. In tal caso, selezionalo e procedi al
    passaggio successivo. Se l'hai chiuso, in una nuova scheda vai a
    `https://purview.microsoft.com`. Accedere come **Patti Fernandez**
    utilizzando il nome utente `PattiF@{TENANTPREFIX}.onmicrosoft.com` e
    la password utente fornita nella scheda delle risorse.

6.  Nel riquadro di spostamento a sinistra selezionare **Solutions \>
    Data Loss Prevention**, quindi selezionare **Sensitive info types**
    in **Classifiers**. Nella casella di **ricerca** in alto a destra
    immettere ***Contoso*** e premere **Enter**. Selezionare **Contoso
    Employee IDs** per aprire il riquadro laterale destro.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image49.png)

Uno screenshot di un computer Descrizione generata automaticamente

7.  Selezionare **Test** nel riquadro a destra.

![Uno screenshot di un computer Descrizione generata
automaticamente](./media/image50.png)

Uno screenshot di un computer Descrizione generata automaticamente

8.  Nella pagina **Upload file to test,** selezionare **Upload file**.

![Immagine rotta](./media/image51.png)

Immagine rotta

9.  Selezionare **Documents** nel riquadro sinistro, selezionare il file
    con il nome **SickTestData** e selezionare **Open**.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image52.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

10. Selezionare **Test** per avviare l'analisi.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image53.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

11. Nella pagina **Match results**, controlla la corrispondenza trovata.

![Immagine rotta](./media/image54.png)

Immagine rotta

12. Selezionare **Finish** e chiudere la pagina del test facendo clic
    sul pulsante **X**.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image55.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

13. Tornare alla pagina **Data classification** e selezionare il tipo di
    informazioni riservate con il nome **Contoso Diseases List**.

14. Nel riquadro laterale destro selezionare **Test**.

![Immagine rotta](./media/image56.png)

Immagine rotta

15. Nella pagina **Upload file to test,** selezionare **Upload file**.

![Immagine rotta](./media/image57.png)

Immagine rotta

16. Selezionare **Documents** nel riquadro sinistro, selezionare il file
    con il nome *SickTestData* e selezionare **Open**.

17. Selezionare **Test** per avviare l'analisi.

![Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente](./media/image58.png)

Interfaccia utente grafica, testo, applicazione Descrizione generata
automaticamente

18. Nella pagina **Match results**, controllare la corrispondenza
    trovata. Al termine, rivedere, selezionare **Finish**.

![Interfaccia utente grafica, applicazione Descrizione generata
automaticamente](./media/image59.png)

Interfaccia utente grafica, applicazione Descrizione generata
automaticamente

## Sommario:

I due tipi di informazioni riservate personalizzate sono stati testati
correttamente e il modello di ricerca riconosce i modelli desiderati. La
creazione dei tipi di informazioni riservate è stata completata e può
procedere con l'esercizio successivo.
