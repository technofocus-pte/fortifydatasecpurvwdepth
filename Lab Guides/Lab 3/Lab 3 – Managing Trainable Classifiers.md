# Lab 3 – Verwalten von trainierbaren Klassifikatoren

## Ziel:

Der Mandant Contoso Ltd. enthält SharePoint-Websitesammlungen, die in
Zukunft zum Speichern mehrerer finanzbezogener Dokumente und Berichte
verwendet werden. Aufgrund der Art dieser Dokumente müssen Sie einen
trainierbaren Klassifizierer erstellen, um diese Dateien zu erkennen und
zu bezeichnen. Zu diesem Zweck aktivieren Sie benutzerdefinierte
trainierbare Klassifikatoren und erstellen in diesem Lab einen neuen
Klassifikator.

## Übung 1 – Erstellen eines trainierbaren Klassifikators

In dieser Aufgabe erstellt Patti einen neuen trainierbaren
Klassifizierer und wählt verschiedene SharePoint-Websites aus, um
typische Daten zu identifizieren, die von Contoso Ltd erstellt und
gespeichert werden.

1.  Öffnen Sie in **Microsoft Edge** ein **New InPrivate Window**,
    navigieren Sie zu `https://purview.microsoft.com, ` und melden Sie
    sich als **Patti Fernandez** mit dem Benutzernamen
    `PattiF@WWLx{TENANTPREFIX}.onmicrosoft.com` und dem Benutzerkennwort
    an, das auf der Registerkarte "Ressourcen" angegeben ist.

2.  Wählen Sie im linken Navigationsbereich **Solutions** \> **Data Loss
    Prevention**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

*Ein Screenshot einer automatisch generierten Computerbeschreibung*

3.  Erweitern Sie **Classifiers** aus dem linken Fensterbereich. Wählen
    Sie **Trainable Classifiers** aus dem Unternavigationsbereich.
    Wählen Sie **+ Create Trainable Classifier,** um einen neuen
    Klassifikator zu erstellen.

![](./media/image2.png)

4.  Geben Sie die folgenden Informationen auf der Seite **Name and
    describe your trainable classifier**:

    - Name: `Contoso Company Data`

    - Description:
      `Trainable classifier for company data produced and stored by Contoso Ltd.`

5.  Wählen Sie **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

8.  Wählen Sie **Choose sites**, um den rechten Seitenbereich zu öffnen.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

9.  Wählen Sie die folgenden SharePoint-Websites aus, und klicken Sie
    auf **Add**.

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

![](./media/image5.png)

10. Warten Sie, bis die ausgewählte Site in der Liste angezeigt wird,
    und wählen Sie **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

11. Wählen Sie auf der Seite **Source of the Negative Sample Content**
    die Website **Learn** aus, und klicken Sie dann auf **Next**.

12. Überprüfen Sie die Einstellungen und wählen Sie **Create trainable
    classifier**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung

13. Wenn die Meldung Ihr trainierbarer Klassifikator wurde erstellt,
    angezeigt wird, wählen Sie **Done** aus.

Die Dokumente und Dateien auf der ausgewählten SharePoint-Website werden
nun analysiert, was bis zu 24 Stunden dauern kann. Sobald es fertig ist,
können Sie die folgenden Schritte ausführen.

- Test the classifier

- Review the classifier

- Publish the classifier

Sie können die bereits vorhandenen Klassifikatoren zur weiteren
Überprüfung untersuchen.

## Zusammenfassung:

Sie haben erfolgreich eine benutzerdefinierte trainierbare
Klassifizierung erstellt, die mit den Dateien übereinstimmt, die auf den
vorhandenen SharePoint-Websites von Contoso Ltd gespeichert sind.
