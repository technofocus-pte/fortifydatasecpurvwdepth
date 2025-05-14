Atelier 7 – Configuration de la gestion des risques internes

Objectif :

Dans cet atelier, nous allons apprendre à configurer la gestion des
risques internes à l'aide des stratégies de gestion des risques
internes. Nous utiliserons les types d'informations sensibles que nous
avons créés dans le laboratoire 2 et les politiques DLP que nous avons
créées dans le laboratoire 5 pour créer des politiques qui protégeront
l'organisation contre l'utilisation à risque du navigateur ou contre
tout vol ou fuite de données.

Pour ce faire, nous allons créer une infrastructure dans Azure qui
représentera les appareils d'une organisation. Nous allons apprendre à
intégrer ces appareils dans Azure AD et Intune, et à installer un agent
MDM sur ceux-ci, afin qu'ils puissent être utilisés pour obtenir les
alertes de ces machines.

Exercice 1 : Synchroniser l'horloge de la machine virtuelle

1.  Après vous être connecté à la machine virtuelle, sélectionnez
    l'icône Windows. Recherchez ensuite **Date and time**, puis
    sélectionnez **Date and time settings**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.jpg)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

2.  Sur l'écran Paramètres qui s’ouvrent, cliquez sur Synchroniser
    **Sync now** sous Paramètres supplémentaires.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.jpg)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

3.  Cela permet de synchroniser l'heure au cas où la synchronisation
    automatique ne fonctionnerait pas.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image3.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

Exercice 2 : Créer des politiques de gestion des risques internes.

Conditions préalables

*Étape 1 – Ajouter des utilisateurs au groupe de rôles Gestion des
risques internes*

1.  Si le portail Microsoft Purview est ouvert, passez à l'étape 2,
    sinon ouvrez le https://purview.microsoft.com et connectez-vous avec
    les **MOD Administrator** de l'administrateur MOD.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image4.png)

2.  Dans la navigation, sélectionnez **Settings**, puis **Role groups**
    sous **Role groups**, sélectionnez **Insider Risk Management**.
    Sélectionnez ensuite **Edit**. Dans le volet latéral, sélectionnez à
    nouveau **Edit**

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image5.png)

3.  Sur la page **Edit Members of the role group**, sélectionnez
    **Choose users**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

4.  Cochez la case près **de MOD Admin**, **Patti**, **Megan** et
    **Alex**. Choisissez ensuite **Select.**![Une capture d'écran d'un
    ordinateur Le contenu généré par l'IA peut être
    incorrect.](./media/image7.png)

&nbsp;

5.  Sélectionnez ensuite **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image8.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

6.  Sélectionnez **Save** pour ajouter les utilisateurs au groupe de
    rôles.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

7.  Sélectionnez **Done** pour terminer les étapes.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image10.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

*Étape 2 – Activer les informations d'analyse des risques internes*

1.  Dans le portail Microsoft Purview. Accédez à **Settings**, puis à
    **Insider risk management**. Allez dans **Analytics**, activez la
    case d'option, puis cliquez sur **Save**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image11.png)

*Étape 3 – Intégration d'un appareil*

Dans ce scénario de déploiement, vous allez intégrer des appareils qui
n'ont pas encore été intégrés et vous souhaitez simplement détecter les
activités à risque interne sur les appareils Windows 10.

Nous devons enregistrer notre appareil/machine virtuelle dans Microsoft
Entra ID comme condition préalable à la création d'une politique de
risque interne.

1.  Ouvrez les fenêtres **Setting** sur votre machine virtuelle.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

2.  Accédez à **Accounts \> Access work or school**. Sur la page
    **Access work or school**, cliquez sur **Connect**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image13.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

3.  Dans l'invite **Set up a work or school account**, cliquez sur
    **Join this device to Microsoft Entra ID**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image14.png)

4.  Dans l'invite de connexion, connectez-vous avec les informations
    d'identification **MOD Administrator** indiquées dans l'onglet
    ressources de votre environnement de laboratoire.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image15.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

![Interface utilisateur graphique, application, PowerPoint Description
générée automatiquement](./media/image16.png)

*Interface utilisateur graphique, application, PowerPoint Description
générée automatiquement*

5.  Appuyez sur **Join** dans l'invite **Make sure this is your
    organisation**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image17.png)

*Interface utilisateur graphique, texte, application Description générée
automatiquement*

6.  Une fois cela fait, vous verrez une fenêtre de confirmation **You’re
    all set !**. Cliquez sur **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image18.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

7.  Allez à nouveau dans **Accounts \> Access work or school**. Sur la
    page **Access work or school**, cliquez sur **Connect**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image13.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

8.  Dans l'invite **Set up a work or school account**, utilisez les
    informations d'identification d'administrateur MOD pour vous
    connecter.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image19.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

9.  Sur la page **Setting up your device**, sélectionnez **Got it.**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image20.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

10. Accédez maintenant aux **windows settings \> Accounts \> Access work
    or school \> Connected to Contoso MDM \> Info \> Sync**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image21.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image22.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

11. Cliquez sur le symbole de la fenêtre sur votre machine virtuelle.
    Sélectionnez l'utilisateur **Admin** et sélectionnez **Sign out**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image23.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

12. Sur l'écran de l'utilisateur, sélectionnez **Other user**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image24.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

13. Entrez vos informations d'identification O365 indiquées sur la page
    d'accueil de votre environnement de labo et connectez-vous à la
    machine virtuelle en tant que **MOD Administrator**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image25.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

14. Fermez l'application Paramètres Windows. Connectez-vous à
    https://purview.microsoft.com à l'aide de votre compte **MOD
    Administrator** sur votre machine virtuelle de laboratoire.

15. Sélectionnez **Settings \> Device onboarding \> Devices**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image26.png)

16. Cliquez sur **Turn on Device onboarding**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image27.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

17. À partir des **Settings \> Device onboarding \> Onboarding.**
    Cliquez sur **Download package**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image28.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

18. Faites un clic droit sur le fichier et **Extract all...**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image29.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image30.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

19. Une fois cela fait, ouvrez le dossier et exécutez le fichier avec
    les **Administrator**.

![Un écran d'ordinateur avec un écran d'ordinateur Description générée
automatiquement](./media/image31.png)

*Un écran d'ordinateur avec un écran d'ordinateur Description générée
automatiquement*

20. Cliquez sur **More info**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image32.png)

*Interface utilisateur graphique, application Description générée
automatiquement*

21. Cliquez quand même sur **Run anyway**.

![Une capture d'écran d'une erreur informatique Description générée
automatiquement](./media/image33.png)

*Une capture d'écran d'une erreur informatique Description générée
automatiquement*

22. Dans l'invite de commande, appuyez sur **Y** et appuyez sur Entrée
    pour confirmer et continuer lorsque vous y êtes invité.

![Une capture d'écran d'une erreur informatique Description générée
automatiquement](./media/image34.png)

*Une capture d'écran d'une erreur informatique Description générée
automatiquement*

23. Vous recevrez un message indiquant que l'appareil est intégré. Dans
    l'invite de commande, une fois que vous obtenez le message, **Press
    any key to continue ...**, appuyez sur n'importe quelle touche.

24. Une fois l'invite de commande fermée, ouvrez l'invite de commande en
    mode administrateur pour exécuter un test de détection et, à
    l'invite, copiez et exécutez la commande ci-dessous. La fenêtre
    d'invite de commande se fermera automatiquement.

powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden
$ErrorActionPreference=
'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process
'C:\test-WDATP-test\invoice.exe'

![Description textuelle générée automatiquement](./media/image35.png)

*Description textuelle générée automatiquement*

25. Ouvrez les **settings** en cliquant sur les paramètres dans la
    navigation et choisissez **Devices Onboarding \> Devices**.

**Remarque :** Bien qu'il faille généralement environ 60 secondes pour
que l'intégration de l'appareil soit activée, veuillez prévoir jusqu'à
30 minutes.

26. Vous pourrez consulter la liste **Devices**. La liste sera vide
    jusqu'à ce que vous intégriez des appareils, une fois cela fait,
    vous pourrez voir vos machines virtuelles répertoriées comme le
    périphérique intégré.

Tâche 1 : Création d'une politique à l'échelle de l'organisation pour
détecter et noter l'utilisation à risque du navigateur

*Étape 1 – Créer une nouvelle politique*

1.  Si vous avez fermé la fenêtre du navigateur lors de la tâche
    précédente, ouvrez le https://purview.microsoft.com et
    connectez-vous avec les informations d'identification Admin.

2.  Accédez à **Insider Risk Management** et sélectionnez l'onglet
    **Policies**. Sélectionnez **Create policy** pour ouvrir l'Assistant
    Stratégie.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image36.png)

3.  Sur la page **Choose a policy template**, choisissez **Risky browser
    usage (preview),** sous **Risky browser usage (preview).**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image37.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

4.  Assurez-vous que toutes les conditions préalables sont remplies.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image38.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

5.  Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image39.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

6.  Sur la page **Name and description**, renseignez les champs suivants
    :

    - Nom (obligatoire) : Utilisation à risque du navigateur

Description (facultatif) : Il s'agit d'une politique de test pour
l'utilisation à risque du navigateur.

7.  Sélectionnez **Next** pour continuer.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image40.png)

*Interface utilisateur graphique, texte, application Description générée
automatiquement*

8.  Sur la page **Choose users, groups, & adaptive scopes**,
    sélectionnez **All users, groups, & adaptive scopes**. Sélectionnez
    **Next** pour continuer.

9.  Sur la page **Exclude users and groups**, sélectionnez **Next**.

10. Sur la page **Decide whether to prioritize** établir la priorité,
    sélectionnez **I don’t want to specify priority content right now**
    (vous pourrez le faire après la création de la stratégie).
    Sélectionnez **Next** pour continuer.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image41.png)

*Interface utilisateur graphique, texte, application Description générée
automatiquement*

11. Sur la page **Triggers for this policy**, sélectionnez **Turn on
    indicators**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image42.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

12. Dans **Choose indicators to turn on**, sélectionnez **Select all
    under Risky browsing indicators (preview),** puis décochez le reste
    des cases.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image43.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

13. Faites défiler l'écran vers le bas et sélectionnez **Save**.

14. Dans **Triggers for this policy**, sous **Select which activities
    will trigger this policy**. Sélectionnez toutes les options et
    cliquez sur **Next**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image44.png)

*Interface utilisateur graphique, texte, application Description générée
automatiquement*

15. Dans **Triggering thresholds for this policy**, sélectionnez **Use
    custom thresholds (Recommended),** remplacez tous les seuils par
    **1** par jour, puis sélectionnez **Next**.

![Interface utilisateur graphique, application Description générée
automatiquement](./media/image45.png)

*Interface utilisateur graphique, application Description générée
automatiquement*

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image46.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

16. Sur la page **indicators**, sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image47.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

17. Dans **Decide whether to use default or custom indicator
    thresholds**, sélectionnez **Use default thresholds for all
    indicators**, puis sélectionnez **Next**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image48.png)

*Interface utilisateur graphique, texte, application Description générée
automatiquement*

18. Dans **Review settings and finish**, sélectionnez **Submit**.

![Interface utilisateur graphique, texte, application Description
générée automatiquement](./media/image49.png)

*Interface utilisateur graphique, texte, application Description générée
automatiquement*

19. Dans **Your policy was created**, sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image50.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

20. Gardez l'onglet ouvert et passez à la tâche suivante.

*Étape 2 – Noter la politique*

1.  Cliquez sur la nouvelle politique nommée **Risky usage of browser**.
    Sélectionnez **Start scoring activity for users**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image51.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

2.  Dans le champ **Reason** du volet **Add users to multiple
    policies**, tapez **Testing the policy**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image52.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

3.  Dans le champ **This should last for (choose between 5 and 30
    days),** sélectionnez **10** jours.

4.  Utilisez le champ **Search user to add to policies**. Ajouter **MOD
    Admin**. Cliquez ensuite sur **Start scoring activity**.

5.  Une fois que vous avez reçu la confirmation que vous avez commencé
    **Scoring activity for 1 users**, cliquez sur **Close**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image53.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

Tâche 2 : Vol de données par les utilisateurs qui quittent l'entreprise

*Étape 1 – Créer une nouvelle politique*

1.  Si vous avez fermé la fenêtre du navigateur lors de la tâche
    précédente, ouvrez le https://purview.microsoft.com et
    connectez-vous avec les informations d'identification
    d'administrateur.

2.  Accédez à **Insider Risk Management** et sélectionnez **Policies**.
    Sélectionnez **Create policy** pour ouvrir l'Assistant Stratégie.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image36.png)

3.  Sur la page Choisir un modèle de stratégie, choisissez Vol de
    données par les utilisateurs sortants, sous Vol de données.
    Sélectionnez Next pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image54.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

4.  Sur la page **Name and description**, renseignez les champs suivants
    :

    - Name (required): `Data theft by a user`

    - Description
      (optional): `This is a test policy for the preventing data theft`.

5.  Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image55.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

6.  Sur la page **Choose users, groups, & adaptive scopes**,
    sélectionnez **All users, groups, & adaptive scopes**. Sélectionnez
    **Next** pour continuer.

7.  Sur la page **Exclude users, groups, & adaptive scopes**,
    sélectionnez **Next**.

8.  Sur la page **Decide whether to prioritize**, sélectionnez **I want
    to specify priority content**. Cochez la case **Sensitivity labels**
    et **Sensitive info types**. Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image56.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

9.  Sur la page **Sensitivity labels to prioritize**, sélectionnez **Add
    or edit sensitivity labels**. Dans le volet volant, sélectionnez
    **Internal/Employee data (HR),** puis **Add**. Cliquez ensuite sur
    **Next**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image57.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

10. Sur la page **Sensitive info types to prioritize**, sélectionnez
    **Add or edit sensitive info types**. Dans le volet volant,
    recherchez et sélectionnez **Credit Card Number, Contoso Employee
    ID** et **Contoso Employee EDM**. Sélectionnez **Add**. Cliquez
    ensuite sur **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image58.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

11. Dans **Decide whether to score only activity with priority
    content**, sélectionnez **Get alerts for all activity**.
    Sélectionnez **Next**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image59.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

12\. Sur les déclencheurs de cette page de stratégie, sélectionnez la
valeur par défaut, puis sélectionnez Suivant.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image60.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

13. Sur la page **Indicators**, sélectionnez **Turn on indicators** à
    partir de l'invite  
    ![Une capture d'écran d'un ordinateur Description générée
    automatiquement avec un niveau de confiance
    moyen](./media/image61.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

14. Sélectionnez **Select all under Office indicators** et cliquez sur
    **Save**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image62.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

15. Sélectionnez toutes les options et cliquez sur **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image63.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

16. Sur la page **Detection options**, sélectionnez la valeur par
    défaut, puis sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image64.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

17. Sur la page **indicators**, sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image47.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

18. Dans **Decide whether to use default or custom indicator
    thresholds**, sélectionnez **Customise thresholds**, utilisez
    respectivement **1**, **2** et **3** événements pour chaque étape,
    puis sélectionnez Next.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement](./media/image65.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement*

19. Dans **Review settings and finish**, sélectionnez **Submit**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image66.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

20. Dans **Your policy was created**, sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image67.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

21. Gardez l'onglet ouvert et passez à la tâche suivante.

*Étape 2 – Noter la politique*

1.  Cliquez sur la nouvelle politique nommée **Data theft by a user**.
    Sélectionnez **Start scoring activity for users**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image68.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

2.  Dans le champ **Reason field in the Add users to multiple
    policies**, tapez **Testing the policy**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image52.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

3.  Dans le champ **This should last for (choose between 5 and 30
    days),** sélectionnez **10** jours.

4.  Utilisez le champ **Search user to add to policies**. Ajouter **MOD
    Admin**. Cliquez ensuite sur Commencer à **Start scoring activity**.

5.  Une fois que vous avez reçu la confirmation que vous avez commencé
    **Scoring activity for 1 users**, cliquez sur **Close**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image69.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

Tâche 3 : Fuites de données par les utilisateurs

*Étape 1 – Créer une nouvelle politique*

1.  Si vous avez fermé la fenêtre du navigateur lors de la tâche
    précédente, ouvrez le https://purview.microsoft.com et
    connectez-vous avec vos informations d'identification
    d'administrateur.

2.  Accédez à **Insider Risk Management** et sélectionnez **Policies**.
    Sélectionnez **Create policy** pour ouvrir l'Assistant Stratégie.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image36.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

3.  Sur la page **Choose a policy template**, choisissez **Data leaks**,
    sous **Data leaks**. Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image70.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

4.  Sur la page **Name and description**, renseignez les champs suivants
    :

    - Name (required): Data leaks by a user

    - Description (optional): This is a test policy for preventing data
      leaks.

5.  Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image71.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

6.  Sur la page **Choose users and groups**, sélectionnez **Include all
    users and groups**. Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image72.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

7.  Sur la page **Exclude users and groups**, sélectionnez **Next**.

8.  Sur la page **Decide whether to prioritize**, sélectionnez **I want
    to specify priority content**. Activez la case à cocher pour les
    **SharePoint sites, Sensitivity labels** et **Sensitive info
    types**. Sélectionnez **Next** pour continuer.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image73.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

9.  Sur la page **SharePoint sites to prioritize**, sélectionnez **Add
    or edit SharePoint sites**. Dans le volet volant, sélectionnez
    https://{TENANTPREFIX}.sharepoint.com/sites/ContosoWeb1 et
    sélectionnez **Add**. Cliquez ensuite sur **Next**.

10. Sur la page **Sensitivity labels to prioritize**, sélectionnez **Add
    or edit sensitivity labels**. Dans le volet volant, sélectionnez
    **Internal/Employee data (HR),** puis Ajouter. Cliquez ensuite sur
    **Next**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image57.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

11. Sur la page **Sensitive info types to prioritize**, sélectionnez
    **Add or edit sensitive info types**. Dans le volet volant,
    recherchez et sélectionnez **Credit Card Number, Contoso Employee
    EDM** et **EDM d'employé Contoso**. Sélectionnez **Ajouter**.
    Cliquez ensuite sur **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image58.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

12. Dans **Decide whether to score only activity with priority
    content**, sélectionnez **Get alerts for all activity**.
    Sélectionnez **Next**.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image59.png)

*Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement avec un niveau de confiance moyen*

13. Sur la page **Triggers for this policy**, sélectionnez Bouton radio
    à côté de **User performs an exfiltration activity**. Sous
    Sélectionner les activités qui déclencheront cette stratégie,
    sélectionnez toutes les options disponibles, en particulier
    Télécharger le **Download content from SharePoint**, puis
    sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image74.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

14. Dans **Triggering thresholds for this policy**, sélectionnez **Use
    custom thresholds**. Définissez chaque seuil sur **1** et
    sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image75.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

15. Sélectionnez les paramètres par défaut sur la page **Indicators**,
    puis sélectionnez **Next**.

16. Dans **Decide whether to use default or custom indicator
    thresholds**, sélectionnez **Customise thresholds**, utilisez
    respectivement **1**, **2** et **3** événements pour chaque étape,
    puis sélectionnez **Next**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image76.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

17. Dans **Review settings and finish**, sélectionnez **Submit**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image77.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

18. Dans **Your policy was created**, sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image78.png)

*Une capture d'écran d'un ordinateur Description générée
automatiquement*

19. Gardez l'onglet ouvert et passez à la tâche suivante.

*Étape 2 – Noter la politique*

1.  Cliquez sur la nouvelle politique nommée **Data leaks by a user**.
    Sélectionnez **Start scoring activity for users**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image79.png)

*Une capture d'écran d'un ordinateur Description générée automatiquement
avec un niveau de confiance moyen*

2.  Dans le champ **Reason field in the Add users to multiple
    policies**, tapez Test de la stratégie. Dans le champ **This should
    last for (choose between 5 and 30 days),** sélectionnez **10**
    jours. Utilisez le champ **Search user to add to policies**. Ajouter
    **MOD Admin**. Cliquez ensuite sur Commencer à **Start scoring
    activity**.

3.  Une fois que vous avez reçu la confirmation que vous avez commencé
    **Scoring activity for 1 user**, cliquez sur **Close**.

Vous avez créé avec succès les politiques de gestion des risques
internes.

Résumé :

Dans cet atelier, nous avons exploré la mise en place de la gestion des
risques internes de bout en bout. Avec votre propre abonnement et vos
propres licences, vous pouvez également utiliser ce guide pratique pour
créer une configuration Azure qui peut également être utilisée pour
créer diverses alertes (ce qui inclut l'envoi d'e-mails avec des données
restreintes, ce qui n'est pas possible à partir d'un abonnement d'essai)
pour les stratégies de gestion des risques internes que vous pouvez
utiliser pour explorer la fonctionnalité de protection adaptative sur
Purview.
