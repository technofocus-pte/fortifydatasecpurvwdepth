# Lab 2 — Verwalten vertraulicher Informationstypen

## Ziel:

Contoso Ltd. hatte zuvor Probleme mit Mitarbeitern, die versehentlich
persönliche Informationen von Kunden sendeten, wenn sie an
Supporttickets in der Ticketlösung arbeiteten.

Um Benutzer in Zukunft zu schulen, ist ein benutzerdefinierter Typ
vertraulicher Informationen erforderlich, um Mitarbeiter-IDs in E-Mails
und Dokumenten zu identifizieren, die aus drei Großbuchstaben und sechs
Ziffern bestehen, wobei vertrauliche Informationstypen verwendet werden.
Um die False-Positive-Rate zu senken, werden die Schlüsselwörter
"Mitarbeiter" und "IDs" verwendet.

In diesem Lab erstellen Sie:

1.  Ein neuer benutzerdefinierter Typ vertraulicher Informationen

2.  eine Datenbank für die EDM-basierte Klassifizierung

3.  Stichwort-Wörterbuch

## Übung 1 – Erstellen benutzerdefinierter Typen vertraulicher Informationen

In dieser Übung verwenden Sie das **Security & Compliance Center**
PowerShell-Modul, um einen neuen benutzerdefinierten Typ vertraulicher
Informationen zu erstellen, der das Muster von Mitarbeiter-IDs in der
Nähe der Schlüsselwörter "Mitarbeiter" und "ID" erkennt”.

1.  Öffnen Sie in **Microsoft Edge** ein **neues InPrivate-Fenster**,
    navigieren Sie zu `https://purview.microsoft.com,` und melden Sie
    sich als **Patti Fernandez** mit dem Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerkennwort an,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben. Wenn Sie
    dazu aufgefordert werden, stimmen Sie den Allgemeinen
    Geschäftsbedingungen zu und wählen Sie **Get Started**.

2.  Wählen Sie im linken Navigationsbereich **Solutions** \> **Data Loss
    Prevention**.

![](./media/image1.png)

3.  Wählen Sie **Classifiers** aus dem linken Fensterbereich. Wählen Sie
    **Sensitive Info Types** aus dem Unternavigationsbereich. Wählen Sie
    **+Create Sensitive Info Type** So öffnen Sie den Assistenten für
    einen neuen Typ vertraulicher Informationen.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

> Ein Screenshot eines Computers Beschreibung wird automatisch generiert

4.  Auf der **Name your sensitive Info Type** Seite, Geben Sie die
    folgenden Informationen ein:

    - **Name**: `Contoso Employee IDs`

    - **Description**: `Pattern for Contoso Employee IDs.`

5.  Wählen Sie **Next** aus.

![Graphical user interface, application Description automatically
generated](./media/image3.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

6.  Auf der **Define Patterns for this Sensitive Info Type** Seite,
    wählen Sie **Create pattern**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

> Ein Screenshot eines Computers Beschreibung wird automatisch generiert

7.  Wählen Sie im Bereich **New Pattern** auf der rechten Seite **Add**
    **Primary Element hinzufügen** und dann **Regular expression** aus.

![Graphical user interface, application, Teams Description automatically
generated](./media/image5.png)

Grafische Benutzeroberfläche, Anwendung, Teams Beschreibung automatisch
generiert

8.  Im neuen rechten Fensterausschnitt **Add a regular expression**,
    geben Sie Folgendes ein:

    - **ID**: `Contoso IDs`

    - **Regular expression**: `\s\[A-Z\]{3}\[0-9\]{6}\s`

    - Select **String match**

9.  Wählen Sie **Done**.

![Graphical user interface, application Description automatically
generated](./media/image6.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

10. Wählen Sie im **rechten** Bereich **New pattern** unter **Supporting
    Elements** die Option + **Add supporting elements or group of
    elements** oder Gruppe von Elementen aus, und wählen Sie **Keyword
    List** aus.

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

10. Im neuen rechten Fensterausschnitt wählen Sie **Add a Keyword
    List**, geben Sie Folgendes ein:

    - **ID**: `Employee ID keywords`

    - **Case insensitive**:

&nbsp;

    Employee
    ID

11. Wählen Sie das Radial für ***Word match*** unter **Case Sensitive**
    aus.

12. Wählen Sie **Done** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image8.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

1.  Verringern Sie in den Fenstern Neues Muster den **Wert** für
    **Character Proximity** auf **100** Zeichen.

![Graphical user interface, text, application Description automatically
generated](./media/image9.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

14. Wählen Sie die Schaltfläche **Create** aus.

15. Zurück auf der **Define patterns for this sensitive info type**
    Seite wählen Sie **Next**.

![Graphical user interface, text, application, Teams Description
automatically generated](./media/image10.png)

Grafische Benutzeroberfläche, Text, Anwendung, Teams Beschreibung
automatisch generiert

16. Auf der **Choose the recommended confidence level to show in
    compliance policies** Seite verwenden Sie den Standardwert und
    wählen Sie **Next**.

![BrokenImage](./media/image11.png)


17. Auf der **Review Settings and Finish** Seite überprüfen Sie die
    Einstellungen und wählen Sie **Create**. Bei erfolgreicher
    Erstellung wählen Sie **Done**.

![Graphical user interface, text, application Description automatically
generated](./media/image12.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

18. Lassen Sie das Browserfenster geöffnet.

Sie haben erfolgreich einen neuen vertraulichen Informationstyp
erstellt, um Mitarbeiter-IDs in einem Muster aus drei Großbuchstaben,
sechs Ziffern und den Schlüsselwörtern "Mitarbeiter" oder "IDs"
innerhalb eines Bereichs von 100 Zeichen zu identifizieren.

## Übung 2 – Erstellen eines EDM-basierten Klassifizierungsinformationstyps

Als zusätzliches Suchmuster erstellen Sie eine EDM-basierte
Klassifizierung mit einem Datenbankschema von Mitarbeiterdaten. Die
Quelldatei der Datenbank wird mit den folgenden Datenfeldern der
Mitarbeiter formatiert: Name, Birthdate, StreetAddress, and EmployeeID.

1.  Wählen Sie **Solutions** \> **Data Loss Prevention** \>
    **Classifiers**, navigieren Sie zu **EDM classifiers**, schalten Sie
    **New EDM experience** aus, und im EDM-Schema, wählen Sie **+ Create
    EDM schema** und so erstellen Sie eine neue Schemadefinition.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

2.  Auf dem **Name** Feld, geben Sie `employeedb`` ein`.

3.  Im **Description** Feld, geben Sie `Employee Database schema` ein.

4.  Aktivieren Sie **Ignore delimiters and punctuation for all schema
    fields**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

5.  Klicken Sie auf das Dropdown-Menü für **Choose delimiters and
    punctuation to ignore** und wählen Sie **Hyphen**, **Period**,
    **Space**, **Open parenthesis** und **Close parenthesis** aus.

![Graphical user interface, application Description automatically
generated](./media/image15.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

6.  Geben Sie im ersten Schemafeldnamen `Name ``ein,` und markieren Sie
    das Symbol **Field is searchable** box.

7.  Wählen Sie **+ Add Schema Data Field** vom unteren Ende aus.

![BrokenImage](./media/image16.png)


8.  In **Schema Field Name**, unter **Schema Field \#2**, geben Sie ihr
    `Birthdate`` ein`.

9.  Wählen Sie **+ Add Schema Data Field** wieder vom unteren Ende.

10. In **Schema Field Name**, unter **Schema Field \#3**, geben Sie
    ihren `StreetAddress`.

11. Wählen Sie **+ Add Schema Data Field** aus dem unteren Ende und
    **Add** aus.

12. In **Schema Field Name**, unter **Schema field \#4**, geben Sie ihre
    `EmployeeID`` ein`.

13. Wählen Sie **Field is searchable**.

14. Wahlen Sie **Save** aus.

![Graphical user interface, application Description automatically
generated](./media/image17.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

15. Wählen Sie **EDM sensitive info types** im linken Fensterbereich,
    und wählen Sie **+ Create EDM sensitive info type**, um den **EDM
    rule package** Assistenten zu öffnen.

![](./media/image18.png)

16. Auf der **Define data store schema** Seite, wählen Sie **Choose an
    existing EDM schema** aus.

![Graphical user interface, application Description automatically
generated](./media/image19.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

17. Wählen Sie employeedb und wählen Sie **Add**.

![Graphical user interface, text, application Description automatically
generated](./media/image20.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

18. Überprüfen Sie das Data-Store-Schema, und wählen Sie **Next**.

![Graphical user interface, application Description automatically
generated](./media/image21.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

19. Auf der **Define patterns for this EDM sensitive info type** Seite,
    wählen Sie **+ Create pattern**.

![Graphical user interface, application Description automatically
generated](./media/image22.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

20. Auf **New Pattern** auf der rechten Seite, in der Spalte **Primary
    Element** Feld, wählen Sie ***EmployeeID***.

21. Unter **Primary Element’s Sensitive Info Type**, wählen Sie **Choose
    Sensitive Info Type**.

![A screenshot of a pattern Description automatically
generated](./media/image23.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

22. Im **Search** Bar, geben Sie ***Contoso*** ein und drücken Sie
    Enter.

23. Wählen Sie **Contoso Employee IDs** aus und wählen Sie **Done**.

24. Wählen Sie **Done**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

25. Wählen Sie **Next** im **Define Patterns for this EDM Sensitive Info
    Type** Fenster aus.

![Graphical user interface, text, application Description automatically
generated](./media/image25.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

26. In **Choose the recommended confidence level and character
    proximity** behalten Sie den Standardwert und wählen Sie **Next**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image26.png)

Grafische Benutzeroberfläche, Text, Anwendung, Word Beschreibung werden
automatisch generiert

27. Auf der **Name and Describe your EDM Sensitive Info Type** Seite,
    geben Sie `Contoso Employee EDM` für den Namen ein.

28. Im **Description for Admins** Feld, geben Sie
    `EDM-based sensitive information type for employee personal information`` ei``n``.`` `Wählen
    Sie **Next** aus**.**

![Graphical user interface, text, application Description automatically
generated](./media/image27.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

29. Überprüfen Sie die Einstellungen und wählen Sie **Submit**.

![Graphical user interface, application Description automatically
generated](./media/image28.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

30. In **Your EDM Sensitive Info Type was created** Seite, wählen Sie
    **Done**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

31. Lassen Sie den Browser mit dem Azure Purview-Portal geöffnet.

Sie haben erfolgreich einen neuen EDM-basierten Klassifizierungstyp für
vertrauliche Informationen zur Identifizierung von Mitarbeiterdaten aus
einer Datenbankdateiquelle erstellt.

## Übung 3 – Erstellen einer EDM-basierten Klassifizierungsdatenquelle

Um die EDM-basierte Klassifizierung mit einer Datenbank zu verknüpfen,
die vertrauliche Daten enthält, ist als Nächstes das Hashing und
Hochladen der tatsächlichen Daten für den vertraulichen Informationstyp
über das EDM-Upload-Agent-Tool erforderlich.

1.  In **Microsoft Edge**, navigieren Sie zu
    `https://go.microsoft.com/fwlink/?linkid=2088639` to access the EDM
    download agent.

2.  Wählen Sie **Run** aus, um das Tool herunterzuladen und zu
    installieren.

![BrokenImage](./media/image30.png)


3.  In **Microsoft Exact Data Match Upload Agent Setup** Assistenten,
    wählen Sie **Next**.

    - Wählen Sie **I accept the Terms in the License Agreement** aus und
      wählen Sie **Next**.

    - Ändern Sie nicht die Standardeinstellung **Destination Folder**
      Pfad und wählen Sie **Next**.

    - Wählen Sie **Install** aus, um die Installation durchzuführen.

    - Wenn die Option **User Account Control** öffnet, wählen Sie
      **Yes**.

    1.  Wenn Sie aufgefordert werden, sich anzumelden, melden Sie sich
        über **Pattis** Konto an.

    - Wenn die Installation abgeschlossen ist, wählen Sie **Finish**.

    1.  Wählen Sie das Windows-Symbol unten links, um das Startmenü zu
        öffnen, geben Sie **Notepad** ein und wählen Sie **Notepad** aus
        dem Startmenü.

    &nbsp;

    1.  Geben Sie den folgenden Text in die erste Zeile des
        Editor-Fensters ein (Stellen Sie sicher, dass Sie alle folgenden
        drei Zeilen in neue Zeilen eingeben).

&nbsp;

    Name,Birthdate,StreetAddress,EmployeeID
    Patti Fernandez,01.06.1980,1Main Street,CSO123456
    Christie Cline,31.01.1985,2Secondary Street,CSO654321

4.  Datei auswählen und speichern unter: `EmployeeData.csv`

5.  Wählen Sie die Dropdown-Liste unter **Save as type** aus**:** und
    wählen Sie **All Files (*.*)**

6.  Wählen Sie das Dropdown-Menü bei **Encoding** aus**:** und wählen
    Sie **UTF-8** und wählen Sie **Save** aus.

![BrokenImage](./media/image31.png)


7.  Schließen des Editor-Fensters.

8.  Wählen Sie mit der rechten Maustaste das Windows-Symbol in der
    Taskleiste aus und wählen Sie **Windows PowerShell (Admin)** und
    führen Sie es als Administrator aus.

![BrokenImage](./media/image32.png)


9.  Wenn das Fenster **User Account Control** geöffnet wird, wählen Sie
    **Yes** aus.

10. Navigate to the EDM Upload Agent directory:

`cd "C:\Program Files\Microsoft\EdmUploadAgent"`

![Text Description automatically generated](./media/image33.png)

Text Beschreibung wird automatisch generiert

1.  Autorisieren Sie mit Ihrem Konto das Hochladen der Datenbank in
    Ihren Mandanten, indem Sie das folgende Cmdlet ausführen:

`.\EdmUploadAgent.exe /Authorize`

![BrokenImage](./media/image34.png)


1.  Wenn das Fenster **Pick an Account** angezeigt wird, melden Sie sich
    als **Patti Fernandez** mit dem Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerkennwort an,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben. (Oder
    das neue Kennwort, das Sie zurückgesetzt haben.)

**Anmerkung**: Stellen Sie für die nächsten Schritte sicher, dass der
Pfad der Dateien dem Pfad in Ihrer VM ähnelt. Es kann anders sein als in
der Anleitung oder in den Screenshots. In diesem Fall ändern Sie bitte
den Pfad Ihrer Datei in den Befehlen entsprechend.

13. Download the database schema definition of the EDM-based
    classification sensitive information type by running the following
    script in PowerShell

`.\EdmUploadAgent.exe /SaveSchema /DataStoreName employeedb /OutputDir "C:\Users\Admin\Documents\"`

**Anmerkung**: Wenn der letzte Befehl fehlschlägt, dauert es
möglicherweise länger, bis die **EDM_DataUploaders**
Gruppenmitgliedschaft angewendet wird. Es kann bis zu einer Stunde
dauern, bis die Schemadatei heruntergeladen werden kann. Wenn dies
fehlschlägt, fahren Sie mit der nächsten Aufgabe fort, und kehren Sie
später zu diesem Schritt zurück. Oder überprüfen Sie den Pfad des
Ordners "Dokumente" auf Ihrer VM.

![BrokenImage](./media/image35.png)


1.  Hashen Sie die Datenbankdatei, und laden Sie sie in den
    EDM-basierten Klassifizierungstyp vertraulicher Informationen hoch,
    indem Sie das folgende Skript in PowerShell ausführen:

`.\EdmUploadAgent.exe /UploadData /DataStoreName employeedb /DataFile "C:\Users\Admin\Documents\EmployeeData.csv" /HashLocation "C:\Users\Admin\Documents\" /Schema "C:\Users\Admin\Documents\employeedb.xml"`

![BrokenImage](./media/image36.png)


**Anmerkung:** Wenn Sie die folgenden Fehler erhalten

Art des Fehlers: System.IO.FileNotFoundException

Fehlermeldung: Unable to find the specified file.

Überprüfen Sie den Pfad, in dem Sie die Datei gespeichert haben -
EmployeeData.csv

![Text Description automatically generated](./media/image37.png)

Text Beschreibung wird automatisch generiert

1.  Überprüfen Sie den Uploadfortschritt, bis sich der Status in
    Abgeschlossen ändert, und führen Sie dann den folgenden
    PowerShell-Befehl aus:

`.\EdmUploadAgent.exe /GetSession /DataStoreName employeedb`

![BrokenImage](./media/image38.png)


Sie haben erfolgreich eine Datenbankdatei für einen EDM-basierten
Klassifizierungstyp vertraulicher Informationen gehasht und hochgeladen.

## Übung 4 – Erstellen eines Keyword-Wörterbuchs

Mehrere Verstöße gegen das Durchsickern personenbezogener Daten
ereigneten sich, als Benutzer E-Mails verschickten, nachdem sich
Kollegen krankgeschrieben hatten. Als das geschah, wurde der Grund für
Krankheit oder Krankheit ausgesandt. Das wollen wir nicht.

1.  In **Microsoft Edge**, Öffnen Sie ein **New InPrivate Window**,
    navigate to `https://purview.microsoft.com` und melden Sie sich an
    als **Patti Fernandez** verwenden Sie den Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und das Benutzerkennwort,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben.

&nbsp;

1.  Wählen Sie im linken Navigationsbereich **Solutions** \> **Data Loss
    Prevention**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

3.  Wählen Sie **Classifiers** aus dem linken Fensterbereich. Wählen Sie
    **Sensitive Info Types** aus dem Unternavigationsbereich. Wählen Sie
    **+Create Sensitive Info Type** so öffnen Sie den Assistenten für
    einen neuen Typ vertraulicher Informationen aus.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

4.  Auf der **Name your Sensitive Info Type** Seite, geben Sie Folgendes
    ein:

    - Name: `Contoso Diseases List`

    - Description: `List of possible diseases of employees.`

![Graphical user interface, application, Teams Description automatically
generated](./media/image39.png)

Grafische Benutzeroberfläche, Anwendung, Teams Beschreibung automatisch
generiert

5.  Wählen Sie **Next**.

6.  Auf der **Define patterns for this sensitive info type** Seite,
    wählen Sie**+ Create pattern** aus.

![Graphical user interface, application, Teams Description automatically
generated](./media/image40.png)

Grafische Benutzeroberfläche, Anwendung, Teams Beschreibung automatisch
generiert

7.  Wählen Sie das Dropdown-Feld unten aus **Primary Element** und
    wählen Sie **Keyword Dictionary**.

![Graphical user interface, application Description automatically
generated](./media/image41.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

8.  Auf der **Add a keyword dictionary** Seite geben sie den Namen
    `Diseases Dictionary`` ein`.

9.  Auf **Keywords** geben Sie die folgenden Schlüsselwörter in einer
    separaten Zeile ein

&nbsp;

    flu
    influenza
    cold
    bronchitis
    otitis

![BrokenImage](./media/image42.png)


10. Wählen Sie **Done**.

11. Unter **Supporting Elements**, wählen Sie **+ Add Supporting
    Elements or Group of Elements** im Drop-Down Menu aus und wählen Sie
    **Keyword List**, um zusätzliche Unterstützung für das
    Schlüsselwortwörterbuch hinzuzufügen.

![Graphical user interface, application Description automatically
generated](./media/image43.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

12. Auf der **Add a Keyword List** Seite geben Sie `Employee absence` in
    das **ID**-Feld ein. In der **Case Insensitive** Box, geben Sie die
    folgenden Schlüsselwörter in einer separaten Zeile ein

&nbsp;

    employee
    absence
    reason

![Graphical user interface, application Description automatically
generated](./media/image44.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

13. Wählen Sie **Done**.

14. Auf der **New Pattern** Seite, Überprüfen Sie die Konfiguration, und
    wählen Sie Create aus.

![Graphical user interface, application Description automatically
generated](./media/image45.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

15. Auf **Define Patterns for this Sensitive Info Type** wählen Sie
    **Next**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image46.png)

Grafische Benutzeroberfläche, Anwendung, Teams Beschreibung automatisch
generiert

16. Auf **Choose the Recommended Confidence Level to show in Compliance
    Policies** lassen Sie den Standardwert bestehen und wählen Sie
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

17. Auf der **Review Settings and Finish** Seite, Überprüfen Sie Ihre
    Einstellungen, und wählen Sie Create aus. Wenn der Vorgang
    abgeschlossen ist, wählen Sie **Done**.

![BrokenImage](./media/image48.png)


18. Lassen Sie das Browserfenster im Azure Purview-Portal geöffnet.

Sie haben erfolgreich einen neuen Typ vertraulicher Informationen
basierend auf einem Schlüsselwortwörterbuch erstellt und weitere
Schlüsselwörter hinzugefügt, um die Falsch-Positiv-Rate zu verringern.
Fahren Sie mit der nächsten Aufgabe fort.

## Übung 5 – Arbeiten mit benutzerdefinierten Typen vertraulicher Informationen

Benutzerdefinierte Typen vertraulicher Informationen sollten immer
getestet werden, bevor sie in Richtlinien verwendet werden, da es sonst
aufgrund eines fehlerhaften benutzerdefinierten Suchmusters zu
Datenverlusten oder -lecks kommen kann.

1.  Wählen Sie das Windows-Symbol unten links, um das Startmenü zu
    öffnen, geben Sie **Notepad ein** und wählen Sie **Notepad** aus dem
    Startmenü.

&nbsp;

1.  Geben Sie den folgenden Text in das Editor-Fenster ein

`Employee Patti Fernandez EMP123456 is on absence because of the flu/influenza`

3.  **File** auswählen und speichern unter `SickTestData` und wählen Sie
    **Save**.

4.  Schließen des Editor-Fensters.

&nbsp;

1.  In **Microsoft Edge** sollte die Registerkarte "Microsoft
    Purview-Portal" weiterhin geöffnet sein. Wenn ja, wählen Sie es aus
    und fahren Sie mit dem nächsten Schritt fort. Wenn Sie es
    geschlossen haben, navigieren Sie in einem neuen Tab zu
    `https://purview.microsoft.com`. Melden Sie sich als **Patti
    Fernandez** mit dem Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerpasswort an,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben.

&nbsp;

5.  Wählen Sie im linken Navigationsbereich **Solutions** \> **Data Loss
    Prevention**, wählen Sie dann die Schaltfläche **Sensitive Info
    Types** unter **Classifiers**. In der **Search** Box von der oberen
    rechten Seite und geben Sie ***Contoso*** und drücken Sie **Enter**.
    Wählen Sie **Contoso Employee IDs**, um den rechten Seitenbereich zu
    öffnen.

![A screenshot of a computer Description automatically
generated](./media/image49.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

7.  Wählen Sie **Test** aus dem rechten Fensterbereich aus.

![A screenshot of a computer Description automatically
generated](./media/image50.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

8.  Auf der **Upload File to Test** Seite, wählen Sie **Upload file**.

![BrokenImage](./media/image51.png)


9.  Wählen Sie **Documents** wählen Sie im linken Fensterbereich die
    Datei mit dem Namen **SickTestData** aus, und wählen Sie **Open**.

![Graphical user interface, text, application Description automatically
generated](./media/image52.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

10. Wählen Sie **Test** aus, um die Analyse zu starten.

![Graphical user interface, text, application Description automatically
generated](./media/image53.png)

Übersichtliche Benutzeroberfläche, Text, Anwendung Beschreibung
automatisch generiert

11. Überprüfen Sie auf der **Seite** **Match results** die gefundene
    Übereinstimmung.

![BrokenImage](./media/image54.png)

12. Wählen Sie **Finish** und schließen Sie die Testseite, indem Sie auf
    die Schaltfläche **X** klicken.

![Graphical user interface, text, application Description automatically
generated](./media/image55.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

1.  Wählen Sie auf der Seite **Data classification** den Typ
    vertrauliche Informationen mit dem Namen **Contoso Diseases List**
    aus.

&nbsp;

13. Wählen Sie im rechten Seitenbereich **Test** aus.

![BrokenImage](./media/image56.png)

15. Auf der **Upload File to Test** Seite, wählen Sie **Upload File**.

![BrokenImage](./media/image57.png)


16. Wählen Sie im linken Fensterbereich **Documents** aus, wählen Sie
    die Datei mit dem Namen *SickTestData* aus und wählen Sie **Open**.

17. Wählen Sie **Test** aus, um die Analyse zu starten.

![Graphical user interface, text, application Description automatically
generated](./media/image58.png)

Graphical user interface, text, application Description automatically
generated

1.  Überprüfen Sie auf der **Seite Match Results** die gefundene
    Übereinstimmung. Wenn die Überprüfung abgeschlossen ist, wählen Sie
    **Finish** stellen aus.

![Graphical user interface, application Description automatically
generated](./media/image59.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

## Zusammenfassung:

Sie haben die beiden benutzerdefinierten Typen vertraulicher
Informationen erfolgreich getestet und überprüft, ob das Suchmuster die
gewünschten Muster erkennt. Sie haben die Erstellung vertraulicher
Informationstypen abgeschlossen und können mit der nächsten Übung
fortfahren.
