# Lab 8 – Erkunden der Funktionen von Adaptive Protection

## Übung 1 – Einrichten des adaptiven Schutzes

### Aufgabe 1 – Einrichten von Risikostufen für Adaptive Protection

1.  Öffnen Sie in Microsoft Edge ein neues InPrivate-Fenster, navigieren
    Sie zu `https://purview.microsoft.com, ` und melden Sie sich mit dem
    Administratormandanten an.

2.  Gehen Sie in der Navigationsleiste zu **Solutions** \> **Insider
    risk** **management**.

![](./media/image1.png)

1.  Wählen Sie in der Unternavigation die Option **Adaptive Protection
    (Preview)** aus.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

4.  Da wir die Schnellstartoption beim Aktivieren des **Adaptive
    Protection** verwendet haben, können wir sehen, dass 2
    DLP-Richtlinien erstellt wurden.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

5.  Klicken Sie nun im Untermenü auf **Risk levels for Adaptive
    Protection** und wählen Sie aus dem Dropdown-Menü **Data leaks by a
    user** aus.

![BrokenImage](./media/image4.png)


6.  Wählen Sie unter **Define conditions for risk levels**, die Option
    **User performs at least 3 data exfiltration activities,
    each…** für **Elevated** Risiko.

> Wählen Sie **User performs at least 2 data exfiltration activities,
> each…** für **Moderate** Risiko. **Select User performs at least 1
> data exfiltration activities, each…** für **Minor** Risiko. Klicken
> Sie dann auf **Save**.

![BrokenImage](./media/image5.png)


7.  Auf ähnliche Weise können Sie die Bedingungen für alle verfügbaren
    Policen unter Insider risk management anpassen.

8.  Jetzt können wir die DLP-Richtlinie für jede Ebene anpassen.

### Aufgabe 2 – Untersuchen von DLP-Standardrichtlinien für jede der Risikostufen von

Adaptiver Schutz

1.  Wählen Sie unter Adaptive Protection, wählen sie DLP Polices und
    dann wählen Sie Adaptive Protection Policy for Endpoint DLP aus.

![BrokenImage](./media/image6.png)


2.  Wählen Sie **Edit** aus.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image7.png)

Ein Screenshot einer Computerbildschirmbeschreibung, die automatisch mit
mittlerer Zuverlässigkeit generiert wird

3.  Klicken Sie auf Weiter, bis Sie **Customize advanced DLP rules**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

1.  Überprüfen Sie die Regeln und Bedingungen, die für jede Risikostufe
    festgelegt wurden. Klicken Sie auf **Next**.

&nbsp;

4.  Wählen Sie auf der Seite **Policy mode** das Optionsfeld neben
    **Turn it on right away**. Klicken Sie auf **Next**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

6.  Wählen Sie dann **Submit** aus.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

Ein Screenshot einer automatisch generierten Computerbeschreibung.

7.  Wiederholen Sie die Schritte, um die Richtlinie für adaptiven Schutz
    für Teams und Exchange DLP zu aktivieren.

8.  Wir werden derzeit keine Regeln oder Richtlinien erstellen, aber Sie
    können verschiedene verfügbare Optionen erkunden, nachdem Sie das
    Lab abgeschlossen haben.
