# Atelier 3 – Gestion des classifieurs entraînables

## Objectif :

Le locataire Contoso Ltd. contient des collections de sites SharePoint
qui seront utilisées à l'avenir pour stocker plusieurs documents et
états financiers. En raison de la nature de ces documents, vous devez
créer un classifieur pouvant être entraîné pour reconnaître et étiqueter
ces fichiers. À cette fin, vous allez activer des classifieurs
personnalisés pouvant être entraînés et en créer un nouveau dans cet
atelier.

## Exercice 1 – Création d'un classifieur pouvant être entraîné

Dans cette tâche, Patti va créer un classifieur pouvant être entraîné et
sélectionner différents sites SharePoint pour identifier les données
typiques créées et stockées par Contoso Ltd.

1.  Dans **Microsoft Edge**, ouvrez **New InPrivate Window**, accédez à
    `https://purview.microsoft.com` et connectez-vous en tant que
    **Patti Fernandez** à l'aide du nom d'utilisateur
    `PattiF@``WWLx``{``TENANTPREFIX``}.onmicrosoft.com` et du mot de
    passe utilisateur indiqué dans votre onglet ressources.

2.  Dans le volet de navigation gauche, sélectionnez **Solutions** \>
    **Data Loss Prevention**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

3.  Développez **Classifiers** dans le volet gauche. Sélectionnez
    **Trainable Classifiers** dans le sous-volet de navigation.
    Sélectionnez **+ Create trainable classifier** pour créer un
    classifieur.

![](./media/image2.png)

4.  Entrez les informations suivantes sur la page **Name and describe
    your trainable classifier**

    - Name: `Contoso Company Data`

    - Description:
      `Trainable classifier for company data produced and stored by Contoso Ltd``.`

5.  Sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

8.  Sélectionnez **Choose sites** pour ouvrir le volet latéral droit.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image4.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

9.  Sélectionnez les sites SharePoint suivants, puis **Add**.

    - Marque

    - Relations publiques de l'initiative numérique

    - Travail

    - Ventes et marketing

    - Équipe du projet Mark 8

![](./media/image5.png)

10. Attendez que le site choisi s'affiche dans la liste et sélectionnez
    **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

11. Sur la **Source of the negative sample content page**, sélectionnez
    le site **Learn**, puis sélectionnez **Next**.

12. Vérifiez les paramètres et sélectionnez **Create trainable
    classifier**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image7.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

13. Lorsque le message Votre classifieur entraînable a été créé
    s'affiche, sélectionnez **Done**.

Les documents et les fichiers du site SharePoint choisi sont en cours
d'analyse, ce qui peut prendre jusqu'à 24 heures. Une fois qu'il est
prêt, vous pouvez effectuer les opérations suivantes.

- Tester le classifieur

- Examiner le classifieur

- Publier le classifieur

Vous pouvez explorer les classifieurs déjà existants pour un examen plus
approfondi.

## Résumé :

Vous avez créé un classifieur apprit personnaliser qui correspond aux
fichiers stockés sur les sites SharePoint existants de Contoso Ltd.
