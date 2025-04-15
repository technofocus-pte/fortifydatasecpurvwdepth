# Lab 4 – Arbeiten mit Vertraulichkeitsbezeichnungen

## Ziel:

In dieser Übung schlüpfen Sie in die Rolle von Patti Fernandez, einer
Systemadministratorin für Contoso Ltd. Ihr Unternehmen hat seinen Sitz
in Rednitzhembach, Deutschland, und implementiert derzeit einen
Sensibilitätsplan, um sicherzustellen, dass alle Mitarbeiterdokumente in
der Personalabteilung im Rahmen der Datenschutzrichtlinien Ihres
Unternehmens mit einem Vertraulichkeitslabel gekennzeichnet wurden.

## Übung 1 – Aktivieren der Unterstützung für Vertraulichkeitsbezeichnungen

In dieser Aufgabe installieren Sie das MSOnline-Modul und das SharePoint
Online PowerShell-Modul und aktivieren die Unterstützung für
Vertraulichkeitsbezeichnungen auf Ihrem Mandanten.

1.  Wählen Sie mit der rechten Maustaste das Windows-Symbol in der
    Taskleiste aus und wählen Sie **Windows PowerShell (Admin)** und
    führen Sie es als Administrator aus.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

2.  Bestätigen Sie das **User Account Control** mit **Yes** und drücken
    Sie die Enter.

3.  Geben Sie das folgende Cmdlet ein, um die neueste Version des
    Microsoft Online PowerShell-Moduls zu installieren:

`Install-Module -Name MSOnline`

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

4.  Bestätigen Sie das Dialogfeld "NuGet-Sicherheit" und das Dialogfeld
    "Nicht vertrauenswürdiges Repository" mit Y für Ja, und drücken Sie
    Enter. Es kann eine Weile dauern, bis die Verarbeitung abgeschlossen
    ist.

![BrokenImage](./media/image3.png)

BrokenImage

5.  Geben Sie das folgende Cmdlet ein, um die neueste Version des
    SharePoint Online PowerShell-Moduls zu installieren.:

`Install-Module -Name Microsoft.Online.SharePoint.PowerShell`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

6.  Bestätigen Sie den Sicherheitsdialog für nicht vertrauenswürdige
    Repositorys mit **Y** für Ja und drücken Sie die Enter.

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

7.  Geben Sie das folgende Cmdlet ein, um eine Verbindung mit dem
    Microsoft Online-Dienst herzustellen:

`Connect-MsolService`

![BrokenImage](./media/image6.png)

BrokenImage

8.  Melden Sie sich im Formular **Sign in to your account** als **Patti
    Fernandez** mit dem Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerkennwort an,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben.

![A screenshot of a computer screen Description automatically
generated](./media/image7.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

9.  Nachdem Sie sich angemeldet haben, gehen Sie zum **PowerShell
    window**.

10. Geben Sie das folgende Cmdlet ein, um die Domäne abzurufen:

`$domain = get-msoldomain`

![BrokenImage](./media/image8.png)

BrokenImage

11. Geben Sie das folgende Cmdlet ein, um die
    SharePoint-Administrator-URL zu erstellen:

`$adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"`

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

12. Geben Sie das folgende Cmdlet ein, um sich beim SharePoint Online
    Admin Center anzumelden:

`Connect-SPOService -url $adminurl`

![A screenshot of a computer screen Description automatically
generated](./media/image10.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

13. Melden Sie sich im **Formular Sign in to your account** als
    **MOD-Administrator** mit den Anmeldeinformationen an, die Sie auf
    der Registerkarte "Ressourcen" Ihrer Lab-Umgebung angegeben haben.

14. Wählen Sie nach der Anmeldung das PowerShell-Fenster aus.

15. Geben Sie das folgende Cmdlet ein, um die Unterstützung für
    Vertraulichkeitsbezeichnungen zu aktivieren:

`Set-SPOTenant -EnableAIPIntegration $true`

![BrokenImage](./media/image11.png)

BrokenImage

16. Bestätigen Sie die Änderungen mit **Y** für Ja und drücken Sie die
    Enter.

![BrokenImage](./media/image12.png)

BrokenImage

17. Schließen des PowerShell-Fensters.

Sie haben die Unterstützung für Vertraulichkeitsbezeichnungen mit Teams-
und SharePoint-Websites erfolgreich aktiviert.

## Übung 2 – Erstellen von Vertraulichkeitsbezeichnungen

In dieser Aufgabe hat Ihre Personalabteilung eine
Vertraulichkeitsbezeichnung angefordert, die auf HR-Mitarbeiterdokumente
angewendet werden soll. Sie erstellen eine Vertraulichkeitsbezeichnung
für interne Dokumente und eine untergeordnete Bezeichnung für die
Personalabteilung.

1.  Navigieren Sie in **Microsoft
    Edge**` ``zu https://purview.microsoft.com` und melden Sie sich als
    **Patti Fernandez** mit dem Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerkennwort an,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben.

2.  Wählen Sie im Azure Purview-Portal im linken Navigationsbereich die
    Option **Solutions** \> **Information Protection**.

![](./media/image13.png)

3.  Wählen Sie in der Unternavigation **Sensitivity Labels** \> **Create
    Labels** aus.

![](./media/image14.png)

4.  Der Assistent für **New Sensitivity Label** wird gestartet. Auf der
    Seite **Label** **Details** für den **Name** geben Sie,
    **Description for Admins** und **Description for Users**, die
    folgenden Informationen ein:

    - Name: `Internal`

    - Display name: `Internal`

    - Description for users: `Internal sensitivity label`

    - Description for admins: `Internal sensitivity label for Contoso.`

![Graphical user interface, text, application, email Description
automatically generated](./media/image15.png)

Grafische Benutzeroberfläche, Text, Anwendung, E-Mail-Beschreibung wird
automatisch generiert

5.  Wählen Sie **Next** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image16.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

6.  Wählen Sie auf der Seite **Define the scope for this label** die
    Option **Items** aus, die E-Mails, Dateien und Power BI-Elemente
    schützen. Deaktivieren Sie das Kontrollkästchen neben **Meetings**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

7.  Wählen Sie **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

8.  Wählen Sie auf der Seite **Choose Protection Settings for Labeled
    Items** die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

1.  Wählen Sie auf der Seite **Auto-labeling** für Dateien und E-Mails
    die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

10. Wählen Sie auf der Seite **Define Protection Settings for Groups and
    Sites** die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

11. Wählen Sie auf der Seite **Auto-labeling for schematized data assets
    (preview)** die Option **Next** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image22.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

12. Wählen Sie auf der Seite **Review your settings and finish** die
    Option **Create Lable** aus.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

13. Die Beschriftung wird erstellt und wenn der Vorgang abgeschlossen
    ist, wird eine Meldung angezeigt: **Your sensitivity label was
    created**

14. Wählen Sie **Don’t create a policy yet** und dann **Done** aus.

![A screenshot of a computer screen Description automatically
generated](./media/image24.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

15. Markieren Sie auf der Seite **Information Protection** das neu
    erstellte Label "Intern" (ohne Auswahl zu treffen), und wählen Sie
    die vertikale Beschriftung aus….

16. Wählen Sie **im Dropdown-Menü die** Beschriftung + **Add sub label**
    aus.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

17. Der Assistent für **New sensitivity label** wird gestartet. Geben
    Sie auf der Seite **Lable Details** die folgenden Informationen ein:

    - Name: `Employee data (HR)`

    - Display name: `Employee data (HR)`

    - Description for users:
      `This HR label is the default label for all specified documents in the HR Department.`

    - Description for admins:
      `This label is created in consultation with Ms.Jones (Head of HR department). Contact ``her when`` you want to change settings of the label.`

![](./media/image26.png)

18. Wählen Sie **Next** aus.

![](./media/image27.png)

19. Wählen Sie auf der Seite **Define the scope for this label** die
    Option **Items** aus, die E-Mails, Dateien und Besprechungen
    schützen. Wählen Sie **Next** aus.

![](./media/image28.png)

20. Wählen Sie auf der Seite **Choose protection settings for labeled
    items** auswählen die Option **Control access** aus. Wählen Sie
    **Next** aus.

![](./media/image29.png)

21. Wählen Sie auf der Seite **Control Access** die Option **Configure
    Access Control Settings** aus.

![](./media/image30.png)

22. Geben Sie die folgenden Informationen in die
    Verschlüsselungseinstellungen ein:

    - Assign permissions now or let users decide?: **Assign permissions
      now**

    - User access to content expires: **Never**

    - Allow offline access: **Only for a number of days**

    - Users have offline access to the content for this many days:
      **15**

![A screenshot of a computer Description automatically
generated](./media/image31.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

23. Wählen Sie den Link **Assign Permissions** aus.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

24. Wählen Sie im Bereich **Assign Permissions** die Option **+ Add any
    authenticated users** aus.

![BrokenImage](./media/image33.png)

BrokenImage

25. Wählen Sie **Save** aus.

![BrokenImage](./media/image34.png)

BrokenImage

26. Wählen Sie auf der Seite **Encryption** die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

1.  Wählen Sie auf der Seite **Auto-Labeling for Files and Emails** die
    Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

28. Wählen Sie auf der Seite **Define protection settings for groups and
    sites** die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

29. Wählen Sie auf der Seite **Auto-Labeling for Schematized Data
    Assests (Preview)** die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

30. Wählen Sie auf der Seite **Review your settings and finish** die
    Option **Create Label** aus.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibun*

31. Die Bezeichnung wird erstellt, und wenn der Vorgang abgeschlossen
    ist, wird eine Meldung angezeigt**: Your sensitivity label was
    created**.

32. Wählen Sie **Don’t create a policy yet** und dann **Done** aus.

![A screenshot of a computer screen Description automatically
generated](./media/image40.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

33. Lassen Sie die Registerkarte geöffnet, um mit der nächsten Aufgabe
    fortzufahren.

Sie haben erfolgreich eine Vertraulichkeitsbezeichnung für die internen
Richtlinien Ihrer Organisation und eine untergeordnete
Vertraulichkeitsbezeichnung für die Personalabteilung erstellt...

## Übung 3 – Veröffentlichen von Vertraulichkeitsbezeichnungen

Sie veröffentlichen nun die Vertraulichkeitsbezeichnung "Intern" und
"HR", sodass die veröffentlichten Vertraulichkeitsbezeichnungen für die
HR-Benutzer verfügbar sind, die sie auf ihre HR-Dokumente anwenden
können.

1.  Navigieren Sie in **Microsoft
    Edge**` zu https://purview.microsoft.com` und melden Sie sich als
    **Patti Fernandez** mit dem Benutzernamen
    `PattiF@{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerkennwort an,
    das Sie auf der Registerkarte "Ressourcen" angegeben haben.

2.  Wählen Sie im Azure Purview-Portal im linken Navigationsbereich
    **Solutions** \> **Information Protection** aus.

![](./media/image13.png)

3.  Wählen Sie in der Unternavigation **Sensitivity Labels** \>
    **Publish Labels aus**.

![](./media/image41.png)

1.  Der Assistent zum Veröffentlichen von Vertraulichkeitsbezeichnungen
    wird gestartet.

&nbsp;

1.  Wählen Sie auf der Seite **Choose sensitivity labels to publish**
    den Link **Choose sensitivity labels to publish** aus.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

6.  Auf der rechten Seite wird eine Seitenleiste mit dem Namen
    **Sensitivity Labels to Publish** angezeigt.

7.  Aktivieren Sie die Kontrollkästchen Internal und **Internal/Employee
    Data (HR)**.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

8.  Wählen Sie **Add** aus.

![A screenshot of a computer Description automatically
generated](./media/image44.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

9.  Wählen Sie auf der Seite **Choose sensitivity labels to publish**
    die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

10. Wählen Sie auf der Seite **Publish to Users and Groups Page** die
    Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

11. Wählen Sie auf der Seite **Policy settings** die Option **Next**
    aus.

![BrokenImage](./media/image47.png)

BrokenImage

12. Wählen Sie auf der Seite **Apply a default label to documents** die
    Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

13. Wählen Sie auf der Seite **Apply a default label to emails** die
    Option **Next** aus.

14. Wählen Sie in den **Default settings for meetings and calendar
    events** die Option **Next** aus.

15. Wählen Sie auf der Seite **Default settings for Fabric and Power BI
    content** die Option **Next** aus.

16. Geben Sie auf der Seite **Name your Policy** die folgenden
    Informationen ein:

    - Name: `Internal HR employee data`

    - Enter a description for your sensitivity label policy:
      `This HR label is to be applied to internal HR employee data.`

![Graphical user interface, text, application, email Description
automatically generated](./media/image49.png)

Grafische Benutzeroberfläche, Text, Anwendung, E-Mail-Beschreibung wird
automatisch generiert

17. Wählen Sie **Next** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image50.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

18. Wählen Sie auf der Seite **Review and Finish** die Option **Submit**
    aus.

![Graphical user interface, text, application Description automatically
generated](./media/image51.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

1.  Die Richtlinie wird erstellt, und wenn der Vorgang abgeschlossen
    ist, wird in der Meldung **New policy created** angezeigt.

&nbsp;

19. Wählen Sie **Done and proceed to next task without closing the
    window** aus.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

Sie haben die Vertraulichkeitsbezeichnungen "Intern" und
"Personalabteilung" erfolgreich veröffentlicht. Beachten Sie, dass es
bis zu 24 Stunden dauern kann, bis Änderungen auf alle Benutzer und
Dienste repliziert werden.

## Übung 4 – Arbeiten mit Vertraulichkeitsbezeichnungen

In dieser Aufgabe erstellen Sie Vertraulichkeitsbezeichnungen in Word-
und Outlook-E-Mails. Das erstellte Dokument wird in OneDrive gespeichert
und per E-Mail an einen HR-Mitarbeiter gesendet.

1.  Navigieren Sie zu `https://portal.office.com` and Melden Sie sich an
    als **Patti Fernandez** an.

&nbsp;

1.  Wenn die Meldung **" Get your work done with Office 365** **"**
    angezeigt wird, schließen Sie sie.

![Graphical user interface Description automatically
generated](./media/image53.png)

Grafische Benutzeroberfläche Beschreibung wird automatisch generiert

3.  Wählen Sie im linken Seitenbereich das **Microsoft Word-Symbol**
    aus, um Word Online zu öffnen.

![Graphical user interface, website Description automatically
generated](./media/image54.png)

Grafische Benutzeroberfläche, Website-Beschreibung wird automatisch
generiert

4.  Wählen Sie **New blank document** aus, um ein neues Dokument zu
    erstellen.

![Graphical user interface, website Description automatically
generated](./media/image55.png)

Grafische Benutzeroberfläche, Website-Beschreibung wird automatisch
generiert

5.  Wenn die Meldung **Your privacy options** angezeigt wird, schließen
    Sie sie, indem Sie **Close** auswählen.

![BrokenImage](./media/image56.png)

BrokenImage

6.  Geben Sie folgenden Inhalt in das Word-Dokument ein:

`Important HR employee document.`

![Graphical user interface, application, Word Description automatically
generated](./media/image57.png)

Grafische Benutzeroberfläche, Anwendung, Word Beschreibung automatisch
generiert

7.  Wählen Sie im oberen Fensterbereich **Sensitivity** aus, um das
    Dropdown-Menü zu öffnen.

![Graphical user interface, application, Word Description automatically
generated](./media/image58.png)

Grafische Benutzeroberfläche, Anwendung, Word Beschreibung automatisch
generiert

8.  Wählen Sie **Internal** \> **Employee data (HR)** um die Bezeichnung
    anzuwenden.

**Anmerkung**: Beachten Sie, dass das Skript, das Sie in Aufgabe 1
dieser Übung ausgeführt haben, Vertraulichkeitsbezeichnungen in Word für
Ihren Mandanten aktiviert hat. Es kann manchmal eine Stunde dauern, bis
diese Aktivierung in Microsoft Word online realisiert wird. Wenn das
Menü Vertraulichkeitsbezeichnung in Word nicht angezeigt wird, müssen
Sie möglicherweise später zu dieser Übung zurückkehren oder
sicherstellen, dass Sie Aufgabe 1 dieser Übung ordnungsgemäß
abgeschlossen haben.

![BrokenImage](./media/image59.png)

BrokenImage

9.  Wählen Sie das **Document – Saved** oben links im Fenster aus, geben
    Sie **HR-Document** als Dateinamen ein und drücken Sie **Enter**.

![Graphical user interface, application, Word Description automatically
generated](./media/image60.png)

Grafische Benutzeroberfläche, Anwendung, Word Beschreibung automatisch
generiert

10. Schließen Sie die Registerkarte "Word", um zur Registerkarte
    **Office 365** zurückzukehren. Wählen Sie im linken Seitenbereich
    das **Outlook-Symbol** aus, um **Outlook** im Web zu öffnen.

![Graphical user interface, text, application Description automatically
generated](./media/image61.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

11. Wenn eine Begrüßungsnachricht angezeigt wird, schließen Sie sie,
    indem Sie die Taste **X**.

12. In Outlook im Web, wählen Sie oben links im Fenster **New Message**
    aus.

![A screenshot of a computer Description automatically
generated](./media/image62.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

1.  Geben Sie im Feld **To** den Namen **Adele** ein, und wählen Sie
    **Adele Vance** aus der Dropdown-Liste aus.

![](./media/image63.png)

14. Geben Sie im Betrefffeld: `Employee data for HR`.

15. Fügen Sie in der E-Mail-Nachricht (dem großen Inhaltsbereich am
    unteren Rand der Seite) die folgende Nachricht ein:

&nbsp;

    DearMs. Adele,
    Please find attached the important HR employee document.
    Kind regards,
    Patti Fernandez

![A screenshot of a computer Description automatically
generated](./media/image64.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

16. Wählen Sie das **Büroklammersymbol** aus dem unteren Menü aus.

![](./media/image65.png)

17. Wählen Sie die **HR-Document.docx** unter **Suggested attachments**
    aus, um das Dokument anzuhängen.

18. Wählen Sie **Send** aus, um die E-Mail-Nachricht mit dem angehängten
    Dokument zu senden.

19. Lassen Sie das Browserfenster geöffnet.

Sie haben erfolgreich ein HR-Word-Dokument mit einer
Vertraulichkeitsbezeichnung erstellt, das auf Ihrem OneDrive gespeichert
wurde. Anschließend haben Sie eine E-Mail an ein Dokument an einen
Mitarbeiter gesendet, bei dem die E-Mail ebenfalls mit einer
Vertraulichkeitsbezeichnung versehen war.

Beachten Sie, dass Sie im Testkonto die E-Mail senden können, sie jedoch
zurückprallt und den Empfänger Ihres aktuellen Mieters nicht erreichen
kann.

## Übung 5 – Konfigurieren der automatischen Beschriftung

In dieser Aufgabe erstellen Sie eine **Sensitivity Label**, die
Dokumente und E-Mails, die Informationen im Zusammenhang mit der
**European General Data Protection Regulation (GPDR)**.

1.  In **Microsoft Edge** sollte die Registerkarte "Microsoft
    Purview-Portal" weiterhin geöffnet sein.

2.  Sie sollten im Portal als **Patti Fernandez** angemeldet sein.

3.  Wählen Sie unter dem **Information Protection** die Option **Label**
    aus, markieren Sie (ohne Auswahl) die vorhandene **interne**
    Bezeichnung, und wählen Sie die drei Punkte aus. Wählen Sie den
    Menüpunkt **+ Create sublabel** aus.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

4.  Der Assistent für neue **New Sensitivity Label** wird gestartet.
    Geben Sie auf der Seite mit den **Label Details** die folgenden
    Informationen ein:

    - Name: `GDPR Germany`

    - Display name: `GDPR Germany`

    - Description for users:
      `This document or email contains data related to the European General Data Protection Regulation(GPDR) for the region Germany.`

    - Description for admins:
      `This label is auto applied to German GDPR documents.`

5.  Wählen Sie **Next** aus.

![BrokenImage](./media/image67.png)

BrokenImage

6.  Wählen Sie auf der Seite **Define the Scope for this Label** die
    Option **Items** aus, die Datei-, E-Mail- und Besprechungselemente
    schützt. Wählen Sie dann **Next**.

![BrokenImage](./media/image68.png)

BrokenImage

7.  Wählen Sie auf der Seite **Choose Protection Settings for Labeled
    Items** die Option **Next** aus.

![BrokenImage](./media/image69.png)

BrokenImage

8.  Legen Sie auf der Seite **Auto-Labeling for Files and Emails** die
    **Option Auto-Labeling for Files and Emails** auf aktiviert fest.

![Graphical user interface, text, application Description automatically
generated](./media/image70.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

9.  Wählen Sie im Abschnitt **Detect content that matches these
    conditions** die Option **+Add Contiditon** und dann **Content
    contains** aus.

![BrokenImage](./media/image71.png)

BrokenImage

10. Wählen Sie im Abschnitt **Content contains** die Option Text **Add**
    und dann **Sensitive info types** aus.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

11. Auf der rechten Seite wird ein Bereich für **Sensitive Info Types**
    angezeigt.

12. Geben Sie im Suchbereich **Search for Sensitive Info Types** die
    folgenden Informationen ein:

`German`

13. Drücken Sie die Eingabetaste auf Ihrer Tastatur, die Ergebnisse
    zeigen Vertraulichkeitsinformationstypen an, die sich auf
    Deutschland beziehen. Klicken Sie auf das Kontrollkästchen **Select
    all**.

![BrokenImage](./media/image73.png)

BrokenImage

14. Wählen Sie **Add**.

![BrokenImage](./media/image74.png)

BrokenImage

15. Wählen Sie **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

16. Wählen Sie auf der Seite **Define protection settings for groups and
    sites** die Option **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image76.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

17. Wählen Sie auf der Seite **Auto-Labeling for Schematized Data Assets
    (Preview)** die Option **Next** aus.

18. Wenn Sie zur Seite **Default Settings for Fabric and Power BI
    Content Page** werden, wählen Sie **Next** aus.

19. Wählen Sie auf der Seite **Review your settings and finish** die
    Option **Create Label** aus.

20. Die Beschriftung wird erstellt und wenn der Vorgang abgeschlossen
    ist, wird eine Meldung angezeigt: **Your sensitivity label was
    created**. Wählen Sie unter Nächste Schritte **Don’t create a policy
    yet**. Wählen Sie dann **Done**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image77.png)

Grafische Benutzeroberfläche, Text, Anwendung, Word Beschreibung werden
automatisch generiert

21. Wählen Sie in der Unternavigation **Sensitivity Labels** \>
    **Publish Labels** aus.

![](./media/image41.png)

22. Das **Publish sensitivity labels wizard** wird beginnen.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image78.png)

Grafische Benutzeroberfläche, Text, Anwendung, Word Beschreibung werden
automatisch generiert

23. Auf der **Choose sensitivity labels to publish** Seite, wählen Sie
    **Choose sensitivity labels to publish** Link.

![A screenshot of a computer Description automatically
generated](./media/image79.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

24. Auf der rechten Seite wird eine **Sensitivity Labels to Publish**
    Vertraulichkeitsbezeichnungen für die Veröffentlichung angezeigt.

![Graphical user interface, application, Word Description automatically
generated](./media/image80.png)

Grafische Benutzeroberfläche, Anwendung, Word Beschreibung automatisch
generiert

25. Aktivieren Sie das Kontrollkästchen **Internal** und **Internal/GDPR
    Germany** und wählen Sie **Add** aus.

![Graphical user interface, application, Word Description automatically
generated](./media/image81.png)

Grafische Benutzeroberfläche, Anwendung, Word Beschreibung automatisch
generiert

26. Wählen Sie auf der Seite **Choose Sensitivity Labels to Publish**
    die Option **Next** aus.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image82.png)

Grafische Benutzeroberfläche, Text, Anwendung, Word Beschreibung werden
automatisch generiert

27. Wählen Sie auf der Seite **Publish to Users and Groups** die Option
    **Next** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image83.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

28. Wählen Sie auf der Seite **Policy settings** die Option **Next**
    aus.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image84.png)

Grafische Benutzeroberfläche, Text, Anwendung, Word Beschreibung werden
automatisch generiert

29. Wählen Sie auf der Seite **Apply a default label to documents** die
    Option **Next** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image85.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

30. Wählen Sie auf der Seite **Apply a Default Label to Emails** die
    Option **Next** aus.

31. Wählen Sie in den **Default Settings for Meetings and Calendar
    Events** die Option **Next** aus.

32. Wählen Sie auf der Seite **Default Settings for Fabric and Power BI
    Content Page** die Option **Next** aus.

33. Geben Sie auf der Seite **Name your Policy** die folgenden
    Informationen ein:

    - Name: `GDPR Germany policy`

    - Enter a description for your sensitivity label policy:
      `This auto apply sensitivity labels policy is for the GDPR region of Germany.`

34. Wählen Sie **Next** aus.

![Graphical user interface, text, application Description automatically
generated](./media/image86.png)

Grafische Benutzeroberfläche, Text, Anwendung Beschreibung wird
automatisch generiert

35. Wählen Sie auf der Seite **Review and finish** die Option **Submit**
    aus.

![Graphical user interface, application Description automatically
generated](./media/image87.png)

Grafische Benutzeroberfläche, Anwendung Beschreibung wird automatisch
generiert

36. Die Richtlinie wird erstellt, und wenn der Vorgang abgeschlossen
    ist, wird die Meldung **New policy created angezeigt**.

37. Wählen Sie **Done** aus.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image88.png)

Grafische Benutzeroberfläche, Text, Anwendung, Word Beschreibung werden
automatisch generiert

## Zusammenfassung:

Sie haben erfolgreich eine automatisch angewendete
Vertraulichkeitsbezeichnung für DSGVO-Dokumente in der Region
Deutschland erstellt und veröffentlicht.

Beachten Sie, dass es bis zu 24 Stunden dauern kann, bis automatisch
angewendete Vertraulichkeitsbezeichnungen angewendet werden. Diese Dauer
ist länger, wenn sie auf mehr als 25.000 Dokumente angewendet wird (d.
h. das tägliche Limit).
