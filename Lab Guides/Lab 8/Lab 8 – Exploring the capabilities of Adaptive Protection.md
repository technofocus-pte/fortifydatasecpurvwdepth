# Atelier 8 – Exploration des fonctionnalités de la protection adaptative

## Exercice 1 – Configuration de la protection adaptative

### Tâche 1 – Configuration des niveaux de risque pour la protection adaptative

1.  Dans Microsoft Edge, ouvrez une nouvelle fenêtre InPrivate, accédez
    à `https://purview.microsoft.com` et connectez-vous à l'aide du
    locataire administrateur.

2.  À partir de la barre de navigation, accédez à **Solutions** \>
    **Insider risk management**.

![](./media/image1.png)

3.  Dans la sous-navigation, sélectionnez **Adaptive Protection
    (Preview).**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

4.  Étant donné que nous avons utilisé l'option de démarrage rapide lors
    de l'activation de la **Adaptive Protection**, nous pouvons voir 2
    stratégies DLP créées.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

5.  Cliquez maintenant sur **Risk levels for Adaptive Protection** dans
    le sous-menu et, dans la liste déroulante, sélectionnez **Data leaks
    by a user**.

![BrokenImage](./media/image4.png)



6.  Sous **Define conditions for risk levels**, sélectionnez **User
    performs at least 3 data exfiltration activities, each…** pour
    **Elevated**. Sélectionnez **User performs at least 2 data
    exfiltration activities, each…** pour Risque **Moderate**. **Select
    User performs at least 1 data exfiltration activities, each…** pour
    Risque **Minor**. Cliquez ensuite sur **Save**.

![BrokenImage](./media/image5.png)



7.  De même, vous pouvez personnaliser les conditions de toutes les
    polices disponibles sous la rubrique Gestion des risques internes.

8.  Nous pouvons maintenant personnaliser la politique DLP pour chaque
    niveau.

### Tâche 2 – Explorer les stratégies DLP par défaut pour chacun des niveaux de risque de

Protection adaptative

1.  Sous Protection adaptative, sélectionnez Stratégies DLP, puis
    Stratégie de protection adaptative pour Endpoint DLP.

![BrokenImage](./media/image6.png)



2.  Sélectionnez **Edit**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image7.png)

Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen

3.  Cliquez sur Suivant jusqu'à ce que vous atteigniez **Customize
    advanced DLP rules**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image8.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

4.  Vérifiez les règles et les conditions établies pour chaque niveau de
    risque. Cliquez sur **Next**.

5.  Sur la page **Policy mode**, sélectionnez la case d'option à côté de
    **Turn it on right away.** Cliquez sur **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

6.  Sélectionnez **Submit**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

7.  Répétez les étapes pour activer la stratégie de protection
    adaptative pour Teams et Exchange DLP.

8.  Nous ne créerons pas de règles ou de politiques pour l'instant, mais
    vous pourrez explorer les différentes options disponibles une fois
    l'atelier terminé.
