**Atelier 9 : Automatiser le déploiement de solutions à l'aide de GitHub
Actions pour Microsoft Power Platform**

## **Tâche 1 : Créer l'inscription de l'application**

1.  Connectez-vous au portail Microsoft Azure à l'aide [de
    https://portal.azure.com/#home](https://portal.azure.com/#home) avec
    vos informations d'identification de Office 365 tenant.

2.  Sélectionnez **Get started**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image1.png)

3.  Sélectionnez **Skip** sur la page ’Comment prévoyez-vous d'utiliser
    Azure’.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image2.png)

4.  Sélectionnez **Skip** sur la page ‘Maintenant, nous allons vous
    faire visiter Azure ‘.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image3.png)

5.  Sur **Home** page du portail, tapez **Microsoft Entra ID** dans la
    zone de recherche et sélectionnez-le dans la liste de services
    suggérée ci-dessous.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image4.png)

6.  Dans le volet de navigation de gauche, développez **Manage** , puis
    sélectionnez **App registrations**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image5.png)

7.  Sélectionnez **+ New registration**  sur la page **App
    registrations** .

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image6.png)

8.  Sur la page **App registrations** , entrez les informations
    d'inscription de votre application comme décrit dans le tableau.

[TABLE]

> ![Capture d'écran d'une application informatique Description générée
> automatiquement](./media/image7.png)

9.  Sélectionnez **Register**  pour créer l'inscription de
    l'application.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image8.png)

10. La page de présentation de l'inscription de l'application s'affiche.
    Ajoutez une clé secrète client en sélectionnant **Certificates &
    secrets**  dans le volet de navigation de gauche. Sélectionnez
    l'onglet **Client secrets**, puis sélectionnez **+New client
    secret**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image9.png)

11. Ajoutez une **description** donnée pour votre clé secrète client –
    **My sample client secret**. Sélectionnez une date **d'expiration**
    pour la clé secrète comme **Recommended: 180 days (6 months),** puis
    sélectionnez **Add**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image10.png)

12. Enregistrez la **secret's value and ID**  dans le bloc-notes pour
    l'utiliser dans le code de votre application cliente. Cette valeur
    secrète ne s'affiche plus jamais une fois que vous avez quitté cette
    page.

> **Important :** Ne quittez pas la page de clé secrète du client tant
> que vous n'avez pas copié la valeur de secret (et non l'ID), car vous
> n'aurez plus accès à la valeur de secret.
>
> ![](./media/image11.png)

## **Tâche 2 : Créer un nouvel utilisateur de l'application**

Suivez ces étapes pour créer un utilisateur d'application et le lier à
votre inscription d'application.

1.  Connectez-vous au centre d'administration [Power Platform admin
    center 
    https://admin.powerplatform.microsoft.com/](%20Power%20Platform%20admin%20center %20https://admin.powerplatform.microsoft.com/)
    l'aide de vos informations d'identification de Office 365 tenant.

2.  Sélectionnez **Environnements** dans le volet de navigation de
    gauche, puis sélectionnez l' environnement **Dev One** dans la liste
    pour afficher les informations d'environnement.

> ![](./media/image12.png)

3.  Sélectionnez le lien **See all** sous **S2S apps** sur le côté droit
    de la page.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image13.png)

4.  Sélectionnez + **New app user**.

> ![](./media/image14.png)

5.  Dans le menu déroulant **Create a new app user** , sélectionnez **+
    Add an app**.

> ![Une capture d'écran d'une page de connexion Description générée
> automatiquement](./media/image15.png)

6.  Commencez à taper le nom de votre inscription d'application -
    **Mytestingapp** dans le champ de recherche, puis sélectionnez-le
    (cochez-le) dans la liste des résultats. Ensuite, sélectionnez
    **Add**.

> ![](./media/image16.png)

7.  De retour dans le menu déroulant **Create a new app user** ,
    sélectionnez le **Business unit**  cible dans la liste déroulante.
    Sélectionnez **pencil icon** devant les **Security roles**,,
    sélectionnez **System Administrator** pour l'utilisateur de
    l'application (également appelé principe de service) et sélectionnez
    **Save.**

> ![Une capture d'écran d'une page de connexion Description générée
> automatiquement](./media/image17.png)

8.  Sélectionnez **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image18.png)

9.  Vous devez voir votre nouvel utilisateur d'application dans la liste
    affichée des utilisateurs de l'application.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image19.png)

## **Tâche 3 : Créer une application pilotée par modèle**

Suivez les étapes ci-dessous pour créer une application pilotée par
modèle.

1.  Dans votre navigateur, accédez à
    [https://make.powerapps.com](https://make.powerapps.com/) et
    connectez-vous avec vos informations d'identification. Cliquez sur
    la liste déroulante du sélecteur d'environnement dans l'en-tête et
    sélectionnez votre environnement de développement.

> ![](./media/image20.png)

2.  Cliquez sur la zone **Solutions** dans le volet de navigation de
    gauche, puis cliquez sur le bouton **New solution** pour créer une
    solution.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image21.png)

3.  Entrez le **Display name** de la solution **GitHub Lab**, **Name**–
    **GitHubLab**. Sélectionnez **+New publisher** sous Éditeur.

> ![](./media/image22.png)

4.  Pour les besoins de cet atelier, entrez **‘ GitHub Lab ‘**pour le
    **Display name**, **‘ GitHubLab ‘** pour **Name** et **‘gitlab ‘**
    comme **prefix**, puis choisissez **Save** et **Close**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image23.png)

5.  Dans le panneau Nouvelle solution, sélectionnez le **publisher –
    GitHub Lab** que vous venez de créer et cliquez sur **Créer** pour
    créer une solution non gérée dans l'environnement.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image24.png)

6.  Votre nouvelle solution sera vide et vous devrez y ajouter des
    composants. Dans cet atelier, nous allons créer une table
    personnalisée. Cliquez sur la liste déroulante **+ New**  dans la
    barre de navigation supérieure et sélectionnez **Table \> Set
    advanced properties.**

> ![](./media/image25.png)

7.  Entrez un **display name – Time Off Request**, le nom au pluriel
    sera généré pour vous. Cliquez sur **Save** pour créer le tableau.

> ![](./media/image26.png)

8.  Une fois votre table créée, sélectionnez la table dans la navigation
    du fil d'Ariane pour revenir à la vue de la solution et ajouter un
    autre composant.

> ![](./media/image27.png)

9.  Cliquez sur la liste déroulante + **New**, puis sur **App**, puis
    sélectionnez sur **Model-driven app**..

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image28.png)

10. Entrez un nom d'application – **Time Off Requests**, puis cliquez
    sur le bouton **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image29.png)

11. Dans le concepteur d'applications, cliquez sur **+ Add page**.

> ![](./media/image30.png)

12. Sélectionnez **Dataverse Table**.

> ![](./media/image31.png)

13. Sélectionnez **Time Off Request**, cochez la case **Show in
    navigation**. Sélectionnez **Add**.

> ![](./media/image32.png)

14. Cliquez sur **Publish**, une fois l'action de publication terminée,
    cliquez sur **Play**.

> ![](./media/image33.png)

15. Cela vous amènera à l'application afin que vous puissiez voir à quoi
    elle ressemble. Vous pouvez utiliser l'application et fermer
    l'onglet lorsque vous êtes satisfait.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image34.png)

## **Tâche 4 : Créer un compte GitHub**

**Remarque :** Si vous avez déjà un compte GitHub, vous pouvez ignorer
cette tâche et passer à la tâche suivante.

1.  Allez dans [https://github.com](https://github.com/) et cliquez sur
    **Sign up**  ou **Start a free trial**  (ou connectez-vous si vous
    avez un compte existant).

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image35.png)

2.  Entrez votre **email id** , puis cliquez sur **Continue**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image36.png)

3.  Conservez le mot de passe généré automatiquement ou créez votre
    propre mot de passe, puis cliquez sur **Continue**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image37.png)

4.  Entrez le nom **Username – Labtesting1**, puis cliquez sur
    **Continue**. Si le nom d'utilisateur donné n'est pas disponible,
    entrez un autre nom d'utilisateur.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image38.png)

5.  Sélectionnez **Continue**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image39.png)

6.  Sur la page ‘Vérifier votre compte ‘, sélectionnez **Verify**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image40.png)

7.  Terminez le processus de vérification et utilisez le code de
    lancement qui est reçu sur votre adresse e-mail.

8.  Sélectionnez **Sign in** dans la fenêtre ‘ Se connecter à GitHub ‘
    qui s'affiche.

> ![](./media/image41.png)

9.  Sélectionnez **Skip personalization**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image42.png)

## **Tâche 5 : Création d'un nouveau code secret pour l'authentification du principal de service**

1.  Après avoir créé votre compte, créez un référentiel en sélectionnant
    **Create repository**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image43.png)
>
> L'écran d'accueil alternatif suivant peut s'afficher :
>
> ![Créer un nouveau référentiel](./media/image44.png)

2.  Créez votre nouveau dépôt et nommez-le ‘ **poweractionslab** ‘.
    Veillez à sélectionner **Add a README file** pour lancer le dépôt,
    puis choisissez **Create repository**..

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image45.png)

3.  Accédez à votre référentiel et cliquez sur **Settings**.

> ![](./media/image46.png)

4.  Dans le volet latéral gauche, développez **Secrets and variables**,
    puis cliquez sur **Actions**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image47.png)

5.  Faites défiler l'écran vers le bas, puis sélectionnez **New
    repository secret**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image48.png)

6.  Sur la page Secrets, nommez le secret '**PowerPlatformSPN**'.
    Utilisez la valeur de clé secrète client de l'inscription de
    l'application créée dans Microsoft Entra (que vous avez enregistrée
    dans le bloc-notes) et entrez-la dans le champ **Secret**, puis
    sélectionnez **Add secret**. La clé secrète client sera référencée
    dans les fichiers YML utilisés pour définir les flux de travail
    GitHub plus loin dans cet atelier.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image49.png)

La clé secrète client est désormais stockée en toute sécurité en tant
que clé secrète GitHub.

## **Tâche 6 : Créer un workflow pour exporter et décompresser le fichier de solution dans une nouvelle branche**

1.  Cliquez sur **Actions** dans la palette horizontale ci-dessus.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image50.png)

2.  Cliquez sur **Configure** dans la zone **Simple workflow**  sous la
    section suggérée pour ce référentiel.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image51.png)

3.  Cela démarrera un nouveau fichier YAML avec un flux de travail de
    base pour vous aider à démarrer avec GitHub actions.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image52.png)

4.  Supprimez le contenu pré-créé, collez-le à partir du fichier
    [export-and-branch-solution-with-spn-auth.yml](https://github.com/microsoft/powerplatform-actions-lab/blob/main/sample-workflows/export-and-branch-solution-with-spn-auth.yml).
    Ouvrez le lien indiqué dans le nouvel onglet de la machine
    virtuelle.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image53.png)

5.  **Rename** le fichier en **export-and-branch-solution.yml**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image54.png)

6.  Mettez à jour \<ENVIRONMENTURL\> en ligne n° 28 avec l'URL de
    l'environnement de développement à partir duquel vous souhaitez
    exporter.

> ![Renommez et remplacez le contenu.](./media/image55.png)
>
> Pour obtenir l'URL de l'environnement, accédez au **Power Platform
> Admin center**. Sélectionnez **Environments** dans le volet de
> navigation de gauche, cliquez sur **Dev One,** puis copiez l'URL de
> l'environnement.
>
> ![](./media/image56.png)

7.  **Paste** de **Environment URL** dans le fichier yml. Assurez-vous
    d'ajouter https://. Your URL should be in the given format -
    https://orgfc5xxxfd.crm.dynamics.com

> ![](./media/image57.png)

8.  Mettez à jour \<APPID\> et \<TENANT ID\> avec vos valeurs. Pour
    obtenir ces deux valeurs, accédez au portail Azure, puis
    sélectionnez **Home** \> **Microsoft Entra ID** \> **App** puis
    sélectionnez l'onglet **All applications**, puis sélectionnez
    **Mytestingapp**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image58.png)
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image59.png)

9.  Collez les valeurs sur les lignes n° 29 et 30.

> ![](./media/image60.png)

10. Sur la ligne n° 12 du code, remplacez la valeur par défaut ALMLab
    par GitHubLab qui est le nom de notre solution dans ce cas.
    Assurez-vous de ne pas laisser d'espace et d'écrire correctement
    comme indiqué. Si vous avez donné un nom différent à votre solution,
    écrivez-le ici.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image61.png)

11. Vous êtes maintenant prêt à valider vos modifications. Sélectionnez
    **Commit changes**, puis dans le volet Valider les modifications qui
    s'ouvre, sélectionnez **Commit changes**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image62.png)
>
> Félicitations, vous venez de créer votre premier workflow GitHub à
> l'aide des actions suivantes :

- **Who Am I** : Garantit que vous pouvez vous connecter à
  l'environnement à partir duquel vous exportez.

- **Export solution** : exporte le fichier de solution à partir de votre
  environnement de développement.

- **Unpack Solution**: : le fichier solution exporté à partir du serveur
  est un fichier compressé (zip) avec des fichiers de configuration
  consolidés. Ces fichiers initiaux ne conviennent pas à la gestion du
  code source, car ils ne sont pas structurés de manière à ce que les
  systèmes de gestion du code source puissent correctement différencier
  les fichiers et capturer les modifications que vous souhaitez valider
  dans le contrôle de code source. Vous devez ‘unpack' les fichiers de
  solution pour les rendre adaptés au contrôle de source, au stockage et
  au traitement.

- **Solution de branche** : crée une nouvelle branche pour stocker la
  solution exportée.

## **Tâche 7 : Tester le workflow d'exportation et de décompression**

1.  Ensuite, pour vérifier que le flux de travail s'exécute,
    sélectionnez **Actions** dans la palette horizontale ci-dessus,
    sélectionnez **export-and-branch-solution** workflow répertorié sous
    **All workflows** le volet latéral gauche.

> ![](./media/image63.png)

2.  Sélectionnez **Run workflow**, puis à nouveau Exécuter le **Run
    workflow**. Si vous avez un nom de solution différent de
    ‘GitHubLab’, modifiez la valeur ici, mais laissez les autres valeurs
    telles quelles.

> ![](./media/image64.png)

3.  Au bout de 5 à 10 secondes, le flux de travail démarre et vous
    pouvez sélectionner le flux de travail en cours d'exécution pour
    surveiller la progression.

> ![](./media/image65.png)
>
> ![](./media/image66.png)

4.  Une fois le flux de travail terminé, vérifiez qu'une nouvelle
    branche a été créée avec la solution décompressée dans le
    **solutions/GitHubLab**. Accédez à l' onglet ***Code***.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image67.png)

5.  Développez la liste déroulante **Branches.**

> ![](./media/image68.png)

6.  Sélectionnez la branche – **GitHubLab-xxxx-xxxx** qui a été créée
    par l'action.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image69.png)

7.  Vérifiez que le dossier **solutions/GitHubLab** a été créé dans la
    nouvelle branche

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image70.png)

8.  Pour créer une demande de tirage afin de fusionner les modifications
    dans la branche principale, cliquez sur **Contribute,** puis dans le
    menu volant, cliquez sur Ouvrir la *demande de tirage*.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image71.png)

9.  Sur l' écran *Ouvrir une demande de tirage*, conservez le titre tel
    quel, puis cliquez sur **Create pull request*.***

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image72.png)

10. L'écran se met à jour et affiche la demande de tirage nouvellement
    créée. Au fur et à mesure de la création de la demande de tirage,
    une confirmation sera fournie montrant que notre branche n'a aucun
    conflit avec la branche principale.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image73.png)

11. Cette confirmation signifie que les modifications peuvent être
    fusionnées automatiquement dans la branche principale. Cliquez sur
    **Merge pull request .**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image74.png)

12. Cliquez sur **Confirm merge**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image75.png)

13. Si vous le souhaitez, cliquez sur Supprimer la branche pour nettoyer
    la branche désormais défunte.

> ![Gros plan d'un message Description générée
> automatiquement](./media/image76.png)

14. Cliquez sur **Code**.

> ![](./media/image77.png)

15. Vous êtes redirigé vers la branche par défaut (principale) et
    vérifiez que la solution est maintenant disponible là également.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image78.png)
