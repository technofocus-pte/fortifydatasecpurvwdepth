# Lab 10 – Konfigurieren von Informationsbarrieren

## Ziel:

Contoso verfügt über fünf Abteilungen: *Personal*, *Sales*, *Marketing*,
*Forschung* und *Fertigung*. Um die Einhaltung von Branchenvorschriften
zu gewährleisten, sollten Benutzer in einigen Abteilungen nicht mit
anderen Abteilungen kommunizieren, wie in der folgenden Tabelle
aufgeführt:

[TABLE]

Für diese Struktur enthält der Plan von Contoso drei IB-Richtlinien:

1.  Eine IB-Richtlinie, die den Vertrieb daran hindern soll, mit der
    Forschung zu kommunizieren

&nbsp;

1.  Eine weitere IB-Richtlinie, um zu verhindern, dass die Forschung mit
    dem Vertrieb kommuniziert.

2.  Eine IB-Richtlinie, die es der Fertigung ermöglicht, nur mit der
    Personalabteilung und dem Marketing zu kommunizieren.

## Übung 1 – Voraussetzungen

### Aufgabe 1 – Erstellen eines Segments für Benutzer in Ihrer Organisation

1.  Führen Sie **PowerShel**l auf Ihrer VM als Administrator aus.

![BrokenImage](./media/image1.png)


2.  Führen Sie Folgendes aus:

`Install-Module ExchangeOnlineManagement`

1.  Wenn Sie gefragt werden **Do you want PowerShellGet to install and
    import the NuGet provider now?**’ und " **Are you sure you want to
    install the modules from ‘PSGallery’?**' Geben Sie **Y** ein und
    drücken Sie die Eingabetaste.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

4.  Führen Sie den folgenden Befehl aus, sobald die Installation
    abgeschlossen ist.

`Import-Module ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image3.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

5.  Führen Sie nun den folgenden Befehl aus, um eine Verbindung mit
    Exchange Online herzustellen.

`Connect-IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

1.  Melden Sie sich mit den Anmeldeinformationen des
    **MOD-Administrators** an, die auf der Startseite der Labumgebung
    angegeben sind.

![BrokenImage](./media/image5.png)


1.  Führen Sie den folgenden Befehl nacheinander in der **PowerShell**
    aus, um die Organisationsstruktur zu erstellen.

`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"`

![BrokenImage](./media/image6.png)


`New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"`

`New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"`

`New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"`

`New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"`

### Aufgabe 2 – Aktivieren der bereichsbezogenen Verzeichnissuche in Microsoft Teams

So aktivieren Sie die Suche nach Namen

1.  Wechseln Sie zum Microsoft Teams Admin Center, indem Sie zu
    `https://admin.teams.microsoft.com `gehen, und wählen Sie **Teams**
    \> **Teams-Settings** aus.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

1.  Aktivieren Sie unter **Search by name** neben **Scope directory
    search using an Exchange address book policy** den Schalter **On**.
    Wählen Sie **Save** aus.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

## 

## Übung 2 – Erstellen von IB-Richtlinien

### Aufgabe 1 – Blockieren der Kommunikation zwischen Segmenten

1.  Melden Sie sich beim `https://purview.microsoft.com/` mit den
    Anmeldeinformationen für die MOD-Verwaltung an, die auf der
    Registerkarte "Ressourcen" Ihrer Umgebung angegeben sind.

&nbsp;

1.  Wählen Sie im linken Navigationsbereich **Solutions** \>
    **Information barriers** aus.

![](./media/image9.png)

1.  Wählen Sie in der Unternavigation **Policies** aus. Wählen Sie auf
    der Seite **Policies**die Option **Create Policies** aus, um eine
    neue IB-Richtlinie zu erstellen und zu konfigurieren.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

4.  Geben Sie auf der Seite **Name** einen Namen für die Richtlinie
    ein:` Sales-Research`. Wählen Sie dann **Next**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

5.  Wählen Sie auf der Seite **Assigned segment** die Option **Choose
    segment** aus. **On Select assigned segment for this policy** die
    Option Sales aus. Wählen Sie nun **Add** aus, um das ausgewählte
    Segment zur Richtlinie hinzuzufügen. Sie können nur ein Segment
    auswählen.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

6.  Wählen Sie **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

7.  Wählen Sie unter **Communication and collaboration** die Option
    **Blocked** aus. Wählen Sie **Choose segment** aus, wählen Sie
    **Research** und dann **Add** aus**.**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

1.  Wählen Sie auf der Seite **Communication and collaboration** im Feld
    **Communication and collaboration** den Richtlinientyp blockiert
    aus. Wählen Sie **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

1.  Schalten Sie auf der Seite **Policy Status** den Status der aktiven
    Richtlinie auf **On** um. Wählen Sie **Next** aus, um fortzufahren.

![BrokenImage](./media/image16.png)


10. Überprüfen Sie auf der Seite **Review your settings** die
    Einstellungen, die Sie für die Richtlinie ausgewählt haben, sowie
    alle Vorschläge oder Warnungen für Ihre Auswahl. Wählen Sie **Edit**
    aus, um eines der Richtliniensegmente und den Status zu ändern, oder
    wählen Sie **Submit** aus, um die Richtlinie zu erstellen.

![BrokenImage](./media/image17.png)


11. Wählen Sie **Done** aus, sobald die Richtlinie erstellt wurde.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

### 

### Aufgabe 2 – Erstellen von IB-Richtlinien über PowerShell

1.  Führen Sie **PowerShell** auf Ihrer VM als Administrator aus.

![BrokenImage](./media/image1.png)


2.  Führen Sie Folgendes aus:

`Import-Module ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image19.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

3.  Führen Sie nun den folgenden Befehl aus, um eine Verbindung mit
    Exchange Online herzustellen.

`Connect-IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

1.  Melden Sie sich mit den **MOD-Administratoranmeldeinformationen**
    an, die auf der Ressourcenseite der Labumgebung angegeben sind.

&nbsp;

1.  Führen Sie den folgenden Befehl aus, um eine IB-Richtlinie mit dem
    Namen **Research-Sales** zu erstellen. Wenn diese Richtlinie aktiv
    ist und angewendet wird, hilft sie, zu verhindern, dass Benutzer,
    die sich im Segment **Research** befinden, mit Benutzern im Segment
    **Sales** kommunizieren.

`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive`

![BrokenImage](./media/image20.png)


1.  Führen Sie den folgenden Befehl aus, um eine IB-Richtlinie mit dem
    Namen **Manufacturing-HRMarketing** zu erstellen. Wenn diese
    Richtlinie aktiv ist und angewendet wird, kann die **Manufacturing**
    nur mit **HR** und dem **Marketing** kommunizieren. HR und Marketing
    sind nicht daran gehindert, mit anderen Segmenten zu kommunizieren.

`New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive`

![A computer screen shot of a computer program Description automatically
generated](./media/image21.png)

Ein Computer-Screenshot eines Computerprogramms Beschreibung wird
automatisch generiert

1.  Melden Sie sich bei der `https://purview.microsoft.com/` mit den
    Anmeldeinformationen für die **MOD-Administration** an, die Sie auf
    der Startseite Ihrer Umgebung angegeben haben.

&nbsp;

7.  Wählen Sie im linken Navigationsbereich **Information barriers** \>
    **Policies** aus. Auf der Seite **Policies**. Sie können die
    Richtlinien sehen, die wir erstellt haben.

![](./media/image22.png)

## Übung 3 – Anwenden von IB-Richtlinien

1.  Melden Sie sich beim
    https://purview.microsoft.com/` mit den Anmeldeinformationen für die MOD-Verwaltung an, die Sie auf der Registerkarte "Ressourcen" Ihrer Umgebung angegeben haben`.

2.  Wählen Sie im linken Navigationsbereich **Information barriers**
    aus.

![](./media/image9.png)

3.  Wählen Sie in der Unternavigation die Option **Policy applications**
    aus. Wählen Sie **Apply all policies** aus.

![](./media/image23.png)

**Zusammenfassung:**

In dieser Übung haben wir gelernt, wie Sie die Segmente erstellen, um
die IB-Richtlinien zu implementieren. Wir haben verschiedene Richtlinien
entwickelt, um Informationsbarrieren zu schaffen, indem wir die
Kommunikation und Zusammenarbeit zwischen verschiedenen Segmenten
zulassen oder blockieren.
