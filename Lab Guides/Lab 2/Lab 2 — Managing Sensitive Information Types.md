# Atelier 2 — Gestion des types d'informations sensibles

## Objectif :

Contoso Ltd. rencontrait auparavant des problèmes avec des employés qui
envoyaient accidentellement des informations personnelles de clients
lorsqu'ils travaillaient sur des tickets de support dans la solution de
gestion des tickets.

Pour éduquer les utilisateurs à l'avenir, un type d'informations
sensibles personnalisé est nécessaire pour identifier les ID d'employé
dans les e-mails et les documents, qui se composent de trois caractères
majuscules et de six chiffres, à l'aide des types d'informations
sensibles. Pour réduire le taux de faux positifs, les mots-clés
« Employé » et « IDs » seront utilisés.

Dans cet atelier, vous allez créer :

- Un nouveau type d'informations sensibles personnalisé

- une base de données pour la classification basée sur la GED

- dictionnaire de mots-clés

## Exercice 1 – Création de types d'informations sensibles personnalisés

Dans cet exercice, vous allez utiliser le module **Security & Compliance
Center PowerShell** pour créer un nouveau type d'informations sensibles
personnalisé qui reconnaît le modèle des ID d'employé à proximité des
mots-clés « Employé » et « ID ».

1.  Dans **Microsoft Edge**, ouvrez **New InPrivate Window**, accédez à
    `https://purview.microsoft.com` et connectez-vous en tant que
    **Patti Fernandez** à l'aide du nom d'utilisateur
    `PattiF``@{TENANTPREFIX``}.onmicrosoft.com` et du mot de passe
    utilisateur indiqué dans votre onglet ressources. Si vous y êtes
    invité, acceptez les conditions générales et sélectionnez **Get
    started**.

2.  Dans le volet de navigation gauche, sélectionnez **Solutions** \>
    **Data Loss Prevention**.

![](./media/image1.png)

3.  Sélectionnez **Classifiers** dans le volet gauche. Sélectionnez
    **Sensitive info types** dans le volet de sous-navigation.
    Sélectionnez **+Create sensitive info type** pour ouvrir l'assistant
    pour un nouveau type d'informations sensibles.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

4.  Sur la page **Name your sensitive info type**, entrez les
    informations suivantes :

    - **Name**: `Contoso Employee IDs`

    - **Description** : `Pattern for Contoso Employee IDs``.`

5.  Sélectionnez **Next**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image3.png)

Interface utilisateur graphique, application Description générée
automatiquement

6.  Sur la page **Define patterns for this sensitive info type page,**
    sélectionnez **Create pattern**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image4.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

7.  Dans le volet de droite **New pattern**, sélectionnez **Add primary
    element**, puis Expression **Regular expression**.

![Interface utilisateur graphique, application, Teams Description
générée automatiquement](./media/image5.png)

Interface utilisateur graphique, application, Teams Description générée
automatiquement

8.  Dans le nouveau volet de droite **Add a regular expression**, entrez
    ce qui suit :

    - **ID** : `ID Contoso`

    - **Expression régulière** : `\s\[A-Z\]{``3}\``[0-9\]{``6}\``s`

    - Sélectionnez **String match**

9.  Sélectionnez **Done**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image6.png)

Interface utilisateur graphique, application Description générée
automatiquement

10. Dans le volet de droite **New pattern**, sous **Supporting
    elements**, sélectionnez **+ + Add supporting elements or group of
    elements**, puis sélectionnez **Keyword list**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image7.png)

Interface utilisateur graphique, application Description générée
automatiquement

10. Dans le nouveau volet de droite **Add a keyword list**, entrez ce
    qui suit :

    - **ID** : `Employee`` ID keywords`

    - **Case insensitive**:

&nbsp;

    Employee
    ID

11. Sélectionnez le radial pour la ***Word match*** sous le champ **Case
    Sensitive**

12. Sélectionnez **Done**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image8.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

13. Dans les fenêtres Nouveau modèle, réduisez la valeur **Character
    proximity** à ***100*** caractères.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image9.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

14. Sélectionnez le bouton **Create**.

15. De retour sur la page **Define patterns for this sensitive info
    type**, sélectionnez **Next**.

![Interface utilisateur graphique, texte, application, Teams Description
générée automatiquement](./media/image10.png)

Interface utilisateur graphique, texte, application, Teams Description
générée automatiquement

16. Sur la page **Choose the recommended confidence level to show in
    compliance policies**, utilisez la valeur par défaut et sélectionnez
    **Next**.

![BrokenImage](./media/image11.png)


17. Sur la page **Review settings and finish**, passez en revue les
    paramètres et sélectionnez **Create**. Une fois la création réussie,
    sélectionnez **Done**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image12.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

18. Laissez la fenêtre du navigateur ouverte.

Vous avez créé un nouveau type d'informations sensibles pour identifier
les ID d'employé dans le modèle de trois caractères majuscules, six
chiffres et les mots-clés « Employé » ou « ID » dans une plage de 100
caractères.

## Exercice 2 – Création d'un type d'information de classification basé sur l'EDM

En tant que modèle de recherche supplémentaire, vous allez créer une
classification basée sur EDM avec un schéma de base de données de
données d'employé. Le fichier source de la base de données sera formaté
avec les champs de données suivants des employés : Nom, Date de
naissance, Adresse postale et ID de l'employé.

1.  Sélectionnez **Solutions** \> **Data Loss Prevention** \>
    **Classifiers**, accédez aux **EDM classifiers**, désactivez **New
    EDM experience** et, à partir de Schéma EDM, sélectionnez **+ Create
    EDM schema** pour créer une nouvelle définition de schéma.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image13.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

2.  Dans le champ **Name**, entrez `employeedb`.

3.  Dans le champ **Description**, entrez
    `Employee`` ``Database`` ``schema``.``.`.

4.  Activez **Ignore delimiters and punctuation for all schema fields**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image14.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

5.  Cliquez sur le menu déroulant Choisir **Choose delimiters and
    punctuation to ignore** et sélectionnez **Hyphen, Period, Space,
    Open parenthesis and Close parenthesis**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image15.png)

Interface utilisateur graphique, application Description générée
automatiquement

6.  Dans le premier nom du champ Schema, saisissez `Nom` et cochez la
    case Le **Field is searchable**.

7.  Sélectionnez **+ Add schema data field** à partir de l'extrémité
    inférieure.

![BrokenImage](./media/image16.png)


8.  Dans **Schema field name**, sous **Schema field name 2**, entrez
    `Birthdate`.

9.  Sélectionnez **+ Add schema data field** à partir de l'extrémité
    inférieure.

10. Dans **Schema field name**, sous **Schema field \#3**, entrez
    `StreetAddress`.

11. Sélectionnez **+ Add schema data field** à partir de l'extrémité
    inférieure.

12. Dans **Schema field name**, sous **Schema field \#4**, entrez
    `EmployeeID``.`

13. Sélectionnez **Field is searchable**.

14. Sélectionnez **Save**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image17.png)

Interface utilisateur graphique, application Description générée
automatiquement

15. Sélectionnez **EDM sensitive info types** dans le volet gauche, puis
    sélectionnez **+ + Create EDM sensitive info type** pour ouvrir
    l’Assistant **EDM rule package**.

![](./media/image18.png)

16. Sur la page **Define data store schema**, sélectionnez **Choose an
    existing EDM schema**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image19.png)

Interface utilisateur graphique, application Description générée
automatiquement

17. Sélectionnez **employeedb** et sélectionnez **Add**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image20.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

18. Examinez le schéma du magasin de données et sélectionnez **Next**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image21.png)

Interface utilisateur graphique, application Description générée
automatiquement

19. Sur la page **Define patterns for this EDM sensitive info type page,
    select + Create pattern**, sélectionnez **+ Create pattern**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image22.png)

Interface utilisateur graphique, application Description générée
automatiquement

20. Dans le volet **New pattern** sur le côté droit, dans le champ
    **Primary element**, sélectionnez ***EmployeeID.***

21. Sous **Primary element’s sensitive info type**, sélectionnez
    **Choose sensitive info type**.

![Une capture d'écran d'un motif Description générée
automatiquement](./media/image23.png)

Une capture d'écran d'un motif Description générée automatiquement

22. Dans la barre **Search**, entrez ***Contoso*** et appuyez sur la
    touche Entrée.

23. Sélectionnez **Contoso Employee IDs**, puis **Done**.

24. Sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image24.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

25. Sélectionnez **Next** dans l’écran **Define patterns for this EDM
    sensitive info type**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image25.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

26. Dans Choisir **Choose the recommended confidence level and character
    proximity**, laissez la valeur par défaut persister et sélectionnez
    **Next**.

![Interface utilisateur graphique, texte, application, description de
mot générée automatiquement](./media/image26.png)

Interface utilisateur graphique, texte, application, description de mot
générée automatiquement

27. Sur la page **Name and describe your EDM sensitive info type**,
    entrez `Contoso`` ``Employee`` EDM` pour le nom.

28. Dans le champ **Description for admins**, saisissez le
    `type d'informations sensibles basé sur EDM pour les informations personnelles des ``employés.`
    Sélectionnez **Next.**

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image27.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

29. Vérifiez les paramètres et sélectionnez **Submit**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image28.png)

Interface utilisateur graphique, application Description générée
automatiquement

30. Sur la page **Your EDM sensitive info type was created**,
    sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image29.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

31. Laissez le navigateur ouvert avec le portail Microsoft Purview.

Vous avez créé un nouveau type d'informations sensibles de
classification basé sur l'EDM pour identifier les données des employés à
partir d'une source de fichier de base de données.

## Exercice 3 – Création d'une source de données de classification basée sur l'EDM

Pour associer la classification basée sur l'EDM à une base de données
contenant des données sensibles, il est nécessaire d'effectuer le
hachage et le téléchargement des données réelles pour le type
d'informations sensibles via l'outil EDM Upload Agent.

1.  Dans **Microsoft Edge**, accédez à
    `https://go.microsoft.com/fwlink/?linkid=2088639` pour accéder à
    l'agent de téléchargement EDM.

2.  Sélectionnez **Run** pour télécharger et installer l'outil.

![BrokenImage](./media/image30.png)



3.  Dans l'Assistant **Microsoft Exact Data Match Upload Agent Setup**,
    sélectionnez **Next**.

    - Sélectionnez **I accept the terms in the License Agreement** et
      sélectionnez **Next**.

    - Ne modifiez pas le chemin d'accès par défaut du **Destination
      Folder** et sélectionnez **Next**.

    - Sélectionnez **Install** pour effectuer l'installation.

    - Lorsque la fenêtre **User Account Control** s'ouvre, sélectionnez
      **Yes**.

    - Si vous êtes invité à vous connecter, connectez-vous via le compte
      de **Patti**.

    - Une fois l'installation terminée, sélectionnez **Finish**.

    - Sélectionnez le symbole Windows en bas à gauche pour ouvrir le
      menu Démarrer, entrez **Notepad** et sélectionnez **Notepad** dans
      le menu Démarrer.

    - Entrez le texte suivant sur la première ligne de la fenêtre du
      bloc-notes (Assurez-vous d'entrer les trois suivants sur de
      nouvelles lignes).

&nbsp;

    Name,Birthdate,StreetAddress,EmployeeID
    Patti Fernandez,01.06.1980,1Main Street,CSO123456
    Christie Cline,31.01.1985,2Secondary Street,CSO654321

4.  Sélectionnez Fichier et Enregistrer sous : `EmployeeData.csv`

5.  Sélectionnez la liste déroulante **Save as type:** et sélectionnez
    **All Files (.).**

6.  Sélectionnez la liste déroulante **Encoding,** puis **UTF-8,** puis
    **Save**.

![BrokenImage](./media/image31.png)



7.  Fermez la fenêtre du Bloc-notes.

8.  Sélectionnez le symbole Windows dans la barre des tâches avec le
    bouton droit de la souris, sélectionnez **Windows PowerShell
    (Admin)** et exécutez-le en tant qu'administrateur.

![BrokenImage](./media/image32.png)



9.  Lorsque la fenêtre **User Account Control** s'ouvre, sélectionnez
    **Yes**.

10. Accédez au répertoire de l'agent de téléchargement EDM :

`cd ``"C:\Program Files\Microsoft\``EdmUploadAgent``"`

![Description textuelle générée automatiquement](./media/image33.png)

Description textuelle générée automatiquement

11. Autorisez avec votre compte à télécharger la base de données sur
    votre locataire en exécutant l'applet de commande suivante :

`.\EdmUploadAgent.exe /``Autoriser`

![BrokenImage](./media/image34.png)



12. Lorsque la fenêtre **Pick an account** s'affiche, connectez-vous en
    tant que **Patti Fernandez** en utilisant le nom d'utilisateur
    `PattiF``@{TENANTPREFIX``}.onmicrosoft.com` et le mot de passe
    utilisateur indiqué dans l'onglet de vos ressources (ou le nouveau
    mot de passe que vous réinitialisez).

**Remarque** : Pour les étapes suivantes, assurez-vous que le chemin
d'accès des fichiers ressemble au chemin d'accès de votre machine
virtuelle. Il peut être différent des instructions ou des captures
d'écran. Dans ce cas, veuillez modifier le chemin de votre fichier dans
les commandes en conséquence.

13. Téléchargez la définition du schéma de base de données du type
    d'informations sensibles de classification basé sur EDM en exécutant
    le script suivant dans PowerShell

.\EdmUploadAgent.exe /SaveSchema /DataStoreName employeedb /OutputDir
"C:\Users\Admin\Documents\\

**Remarque** : Si la dernière commande échoue, il se peut que
l'application de l' appartenance **au groupe EDM_DataUploaders** prenne
plus de temps. Le téléchargement du fichier de schéma peut prendre
jusqu'à une heure. En cas d'échec, passez à la tâche suivante et revenez
à cette étape plus tard. Ou vérifiez le chemin d'accès au dossier
documents sur votre machine virtuelle.

![BrokenImage](./media/image35.png)



14. Hachez le fichier de base de données et téléchargez-le dans le type
    d'informations sensibles de classification basé sur EDM en exécutant
    le script suivant dans PowerShell :

`.\EdmUploadAgent.exe /``UploadData`` /``DataStoreName`` ``employeedb`` /``DataFile`` "C:\Users\Admin\Documents\EmployeeData.csv" /``HashLocation`` "C:\Users\Admin\Documents\" /``Schema`` "C:\Users\Admin\Documents\employeedb.xml"`![BrokenImage](./media/image36.png)



**Remarque :** Si vous obtenez les erreurs suivantes

Type d'erreur : System.IO.FileNotFoundException

Message d'erreur : Impossible de trouver le fichier spécifié.

Vérifiez le chemin d'accès où vous avez enregistré le fichier
EmployeeData.csv

![Description textuelle générée automatiquement](./media/image37.png)

Description textuelle générée automatiquement

15. Vérifiez la progression du chargement jusqu'à ce que l'état passe à
    terminer, puis exécutez la commande PowerShell suivante :

`.\EdmUploadAgent.exe /``GetSession`` /``DataStoreName`` ``employeedb`

![BrokenImage](./media/image38.png)



Vous avez haché et téléchargé avec succès un fichier de base de données
pour un type d'informations sensibles de classification basé sur EDM.

## Exercice 4 – Création d'un dictionnaire de mots-clés

Plusieurs violations de la fuite d'informations personnelles se sont
produites lorsque des utilisateurs ont envoyé des e-mails après que des
collègues aient signalé un congé de maladie. Lorsque cela se produisait,
la raison de la maladie ou de la maladie était envoyée. Nous ne voulons
pas que cela se produise.

1.  Dans **Microsoft Edge**, ouvrez une **New InPrivate Window**,
    accédez à `https://purview.microsoft.com` et connectez-vous en tant
    que **Patti Fernandez** à l'aide du nom d'utilisateur
    `PattiF``@{TENANTPREFIX``}.onmicrosoft.com` et du mot de passe
    utilisateur indiqué dans votre onglet ressources.

2.  Dans le volet de navigation gauche, sélectionnez **Solutions** \>
    **Data Loss Prevention**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

3.  Sélectionnez **Classifiers** dans le volet gauche. Sélectionnez
    **Sensitive info types** dans le volet de sous-navigation.
    Sélectionnez **+Create sensitive info type** pour ouvrir l'assistant
    pour un nouveau type d'informations sensibles.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

4.  Sur la page **Name your sensitive info type**, entrez ce qui suit :

    - Name: Contoso Diseases List

    - Description: List of possible diseases of employees`.`

![Interface utilisateur graphique, application, Teams Description
générée automatiquement](./media/image39.png)

Interface utilisateur graphique, application, Teams Description générée
automatiquement

5.  Sélectionnez **Next**.

6.  Sur la page **Define patterns for this sensitive info type**,
    sélectionnez **+ Create pattern**.

![Interface utilisateur graphique, application, Teams Description
générée automatiquement](./media/image40.png)

Interface utilisateur graphique, application, Teams Description générée
automatiquement

7.  Sélectionnez le champ déroulant sous **Primary element** et
    sélectionnez **Keyword dictionary**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image41.png)

Interface utilisateur graphique, application Description générée
automatiquement

8.  Sur la page **Add a keyword dictionary**, entrez le nom Dictionnaire
    des `maladies`.

9.  Dans la zone **Keywords**, entrez les mots-clés suivants, chacun sur
    une ligne distincte

&nbsp;




    flu
    influenza
    cold
    bronchitis
    otitis 

![BrokenImage](./media/image42.png)



10. Sélectionnez **Done**.

11. Sous **Supporting elements**, sélectionnez **+ Add supporting
    elements or group of elements**, puis sélectionnez **keyword list**
    pour ajouter une prise en charge supplémentaire du dictionnaire de
    mots-clés.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image43.png)

Interface utilisateur graphique, application Description générée
automatiquement

12. Sur la page **Add a keyword list,** saisissez `Absence` de l'employé
    dans le champ **ID**. Dans la zone **Case insensitive**, entrez les
    mots-clés suivants, chacun sur une ligne distincte

`employee`

`absence`

`reason`` `  
  
![Interface utilisateur graphique, application Description générée
automatiquement](./media/image44.png)

Interface utilisateur graphique, application Description générée
automatiquement

13. Sélectionnez **Done**.

14. Sur la page **New pattern**, vérifiez la configuration et
    sélectionnez **Create**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image45.png)

Interface utilisateur graphique, application Description générée
automatiquement

15. Dans la section **Define patterns for this sensitive info type**,
    sélectionnez **Next**.

![Interface utilisateur graphique, application, Teams Description
générée automatiquement](./media/image46.png)

Interface utilisateur graphique, application, Teams Description générée
automatiquement

16. Dans la section **Choose the recommended confidence level to show in
    compliance policies**, laissez la valeur par défaut persister et
    sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image47.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

17. Sur la page **Review settings and finish**, vérifiez vos paramètres
    et sélectionnez **Create**. Une fois le processus terminé,
    sélectionnez **Done**.

![BrokenImage](./media/image48.png)



18. Laissez la fenêtre du navigateur du portail Microsoft Purview
    ouverte.

Vous avez réussi à créer un nouveau type d'informations sensibles basé
sur un dictionnaire de mots-clés et ajouté d'autres mots-clés pour
réduire le taux de faux positifs. Passez à la tâche suivante.

## Exercice 5 – Utilisation de types d'informations sensibles personnalisés

Les types d'informations sensibles personnalisées doivent toujours être
testés avant d'être utilisés dans des stratégies, sinon des pertes ou
des fuites de données peuvent se produire en raison d'un modèle de
recherche personnalisé défectueux.

1.  Sélectionnez le symbole Windows en bas à gauche pour ouvrir le menu
    Démarrer, entrez **Notepad** et sélectionnez **Notepad** dans le
    menu Démarrer.

2.  Entrez le texte suivant dans la fenêtre du bloc-notes

`Employee Patti Fernandez EMP123456 ``is on absence`` because of the flu/influenza`

3.  Sélectionnez **File** et Enregistrer sous `SickTestData``, `puis
    sélectionnez **Save**.

4.  Fermez la fenêtre du Bloc-notes.

5.  Dans **Microsoft Edge**, l'onglet du portail Microsoft Purview doit
    toujours être ouvert. Si c'est le cas, sélectionnez-le et passez à
    l'étape suivante. Si vous l'avez fermé, dans un nouvel onglet,
    accédez à `https://purview.microsoft.com`. Connectez-vous en tant
    que **Patti Fernandez** en utilisant le nom d'utilisateur
    `PattiF``@{TENANTPREFIX``}.onmicrosoft.com` et le mot de passe de
    l'utilisateur indiqué dans l'onglet de vos ressources.

6.  Dans le volet de navigation de gauche, sélectionnez **Solutions** \>
    **Data Loss Prevention**, puis sélectionnez les **Sensitive info
    types** sous **Classifiers**. Dans la zone **Search** en haut à
    droite, entrez ***Contoso*** et appuyez sur **Enter**. Sélectionnez
    **Contoso Employee IDs** pour ouvrir le volet latéral droit.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image49.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

7.  Sélectionnez **Test** dans le volet de droite.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image50.png)

Une capture d'écran d'un ordinateur Description générée automatiquement

8.  Sur la page **Upload file to test**, sélectionnez **Upload file**.

![BrokenImage](./media/image51.png)



9.  Sélectionnez **Documents** dans le volet gauche, sélectionnez le
    fichier portant le nom **SickTestData** et sélectionnez **Open**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image52.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

10. Sélectionnez **Test** pour démarrer l'analyse.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image53.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

11. Sur la page **Match results**, vérifiez la correspondance trouvée.

![BrokenImage](./media/image54.png)


12. Sélectionnez **Finish** et fermez la page de test en cliquant sur le
    **bouton X**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image55.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

13. De retour sur la page **Data classification**, sélectionnez le type
    d'informations sensibles sous le nom **Contoso Diseases List**.

14. Dans le volet latéral droit, sélectionnez **Test**.

![BrokenImage](./media/image56.png)



15. Sur la page **Upload file to test**, sélectionnez **Upload file**.

![BrokenImage](./media/image57.png)



16. Sélectionnez **Documents** dans le volet gauche, sélectionnez le
    fichier portant le nom *SickTestData* et sélectionnez **Open**.

17. Sélectionnez **Test** pour démarrer l'analyse.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image58.png)

Interface utilisateur graphique, texte, application Description générée
automatiquement

18. Sur la page **Match results**, vérifiez la correspondance trouvée.
    Une fois l'examen terminé, sélectionnez **Finish**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image59.png)

Interface utilisateur graphique, application Description générée
automatiquement

## Résumé :

Vous avez testé avec succès les deux types d'informations sensibles
personnalisées et validé que le modèle de recherche reconnaît les
modèles souhaités. Vous avez terminé la création des types
d'informations sensibles et vous pouvez passer à l'exercice suivant.
