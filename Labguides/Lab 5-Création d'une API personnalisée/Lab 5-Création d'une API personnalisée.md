**Atelier 5 : Création d'une API personnalisée**

**Durée estimée :** 35 min

**Objectif :** Dans cet atelier, vous allez apprendre à créer une API
personnalisée Dataverse pour exécuter une logique personnalisée. Vous
utiliserez ensuite l'API personnalisée à partir d'une étape d'un Power
Automate flow.

**Tâche 1 : Créer le projet d'API personnalisé**

1.  Cliquez sur le menu **Start** de la machine virtuelle, tapez un
    prompt de commande dans la zone de recherche, puis sélectionnez
    **Open**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image1.png)

2.  Exécutez la commande ci-dessous pour créer un nouveau dossier nommé
    **CustomAPILab**.

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  Changez de répertoire pour le dossier que vous avez créé.

> +++cd CustomAPILab+++
>
> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image3.png)

4.  Vous devez maintenant être dans le dossier CustomAPIlAB. Exécutez la
    commande ci-dessous pour initialiser une nouvelle bibliothèque de
    classes de plug-in Dataverse.

> +++plugin pac init+++
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image4.png)

5.  La création de la bibliothèque de classes du plugin Dataverse doit
    être réussie.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image5.png)

6.  Exécutez la commande ci-dessous pour ouvrir le projet dans Visual
    Studio.

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  Si vous y êtes invité, sélectionnez **Microsoft Visual Studio
    2022**, puis une **just once**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image7.png)

8.  Si vous êtes invité à vous connecter à Visual Studio , sélectionnez
    **Skip this for now** sur la page de connexion.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image8.png)

9.  Sélectionnez **General** comme Paramètres de développement,
    choisissez **Dark** comme thème de couleur, puis sélectionnez
    **Start Visual Studio**.

> **Remarque :** Ignorez cette étape si vous êtes directement dirigé
> vers le projet.
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image9.png)

10. Le projet doit s'ouvrir dans Visual Studio.

> ![](./media/image10.png)

11. Faites un clic droit sur le fichier Plugin1.cs et renommez-le
    **MatchPlugin.cs**.

> ![](./media/image11.png)

12. Sélectionnez **Yes** si vous renommez une boîte de dialogue de
    fichier.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image12.png)

13. Faites un clic droit sur le projet CustomAPILab et sélectionnez
    **Manage NuGet Packages**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image13.png)

14. Recherchez **System.Text.RegularExpressions** et sélectionnez
    **Install**.

> ![](./media/image14.png)

15. Dans la fenêtre Aperçu des modifications, sélectionnez **Apply**
    pour permettre à Visual Studio d'apporter des modifications à la
    solution.

> ![](./media/image15.png)

16. Sélectionnez **I accept** pour accepter les termes du contrat de
    licence.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image16.png)

17. Ouvrez le fichier **MatchPlugin.cs**.

> ![](./media/image17.png)

18. Ajouter l'instruction suivante sous l'affirmation « utilisation du
    système », c'est-à-dire sur la ligne n° 3.

> +++using System.Text.RegularExpressions;+++
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image18.png)

19. Ajoutez les lignes suivantes à l'intérieur de la méthode
    ExecuteDataversePlugin et après la ligne de contexte var. Ces lignes
    récupèrent la valeur des paramètres d'entrée passés lors de l'appel
    de l'API personnalisée.

> string input = (string)context.InputParameters\["StringIn"\];
>
> String pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. Ajoutez la ligne suivante après pour obtenir le service de traçage.

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image20.png)

21. Ajoutez la ligne ci-dessous pour écrire la valeur d'entrée dans
    trace.

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. Ajoutez la ligne suivante après pour appeler la méthode Regex.Match.

> var result = Regex.Match(input, pattern);
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image22.png)

23. Écrivez le résultat à tracer.

> tracingService.Trace("Matching result: " + result.Success);
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image23.png)

24. Et enfin, ajoutez la ligne suivante pour définir le paramètre de
    sortie Matched.

> context.OutputParameters\["Matched"\] = résultat.Success;
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image24.png)

25. Votre méthode d'exécution doit maintenant ressembler à ce qui suit.

> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image25.png)

26. Sélectionnez **Build | Build Solution**.

> ![](./media/image26.png)

27. Le projet doit se construire avec succès.

> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image27.png)

**Tâche 2 : Enregistrer le plug-in API personnalisé**

1.  Ouvrez l la commande prompt et exécutez la commande ci-dessous pour
    lancer l'outil d'enregistrement du plugin.

> +++pac tool prt+++
>
> ![Un écran noir avec du texte blanc Description générée
> automatiquement](./media/image28.png)

2.  Sélectionnez **+Create New Connection**.

> ![](./media/image29.png)

3.  Sélectionnez **Office 365**, fournissez vos informations
    d'identification et sélectionnez **Login**.

> ![Une capture d'écran d'une boîte de connexion Description générée
> automatiquement](./media/image30.png)

4.  Connectez-vous à l'aide de votre **ID de M365 Admin tenant** puis
    sélectionnez **Next**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image31.png)

5.  Entrez le **mot de passe de votre ID M365 Admin tenant**, puis
    sélectionnez **sign in** .

> ![Une capture d'écran d'une boîte de connexion Description générée
> automatiquement](./media/image32.png)

6.  Vérifiez que l' environnement **Dev One** est sélectionné.

7.  Choisissez **Register | Register New Assembly**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image33.png)

8.  Choisir... sous l'étape 1, puis accédez au dossier
    **CustomAPILab\bin\Debug\net462**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image34.png)

9.  Sélectionnez **CustomAPILab.dll** puis Sélectionnez **Open**.

> ![](./media/image35.png)

10. Sélectionnez **Register Selected Plugins**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image36.png)

11. Sélectionnez **OK** pour le message de réussite. Votre plugin est
    prêt à se connecter à l'API personnalisée que nous allons créer dans
    la tâche suivante.

> ![Une capture d'écran d'une erreur informatique Description générée
> automatiquement](./media/image37.png)

**Tâche 3 : Créer l'API personnalisée**

1.  Accédez au portail du créateur Power Apps à l'aide de
    +++<https://make.powerapps.com/>+++ et assurez-vous que vous êtes
    dans l' environnement **Dev One**.

2.  Sélectionnez **Solutions** dans le volet de navigation de gauche.
    Sélectionnez **+ New solution**.

> ![](./media/image38.png)

3.  Entrez +++**Custom API Lab**+++ dans le nom d'affichage.

4.  Sélectionnez **CDS Default Publisher** dans la liste déroulante
    Publisher.

5.  Sélectionnez **Create**. Cela crée une solution personnalisée qui
    contiendra nos composants.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image39.png)

6.  Sélectionnez **+ New | More | Other | Custom API.**

> ![](./media/image40.png)

7.  Entrez les informations suivantes :

    - **Nom unique :** +++contoso_match+++

    &nbsp;

    - **Nom** : +++Match+++

    &nbsp;

    - **Nom d'affichage :** +++Match+++

    &nbsp;

    - **Description** : +++Match a string+++

    &nbsp;

    - **Type de reliure** : +++Global+++

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image41.png)

8.  Dans Type de plugin, sélectionnez l'icône de recherche et localisez
    votre plugin - **CustomAPILab.MatchPlugin**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image41.png)

9.  Sélectionnez **Save and Close**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image42.png)

10. Sélectionnez **Done**.

> ![Une capture d'écran d'un site web Description générée
> automatiquement](./media/image43.png)

11. Sélectionnez **+ New | More| Other | Custom API Request Parameter.**

> ![](./media/image44.png)

12. Pour **Custom API**,sélectionnez l'icône **Search** , puis
    électionnez **Match** (votre API personnalisée).

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image45.png)

13. Entrez +++**StringIn**+++ pour Nom unique, Nom, Nom d'affichage et
    Description pour plus de simplicité.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image46.png)

14. Sélectionnez **String** pour Type.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image47.png)

15. Sélectionnez **Save and Close**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image48.png)

16. Sélectionnez **Done**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image49.png)

17. Pour en ajouter un autre, Paramètre de demande d'API personnalisé,
    sélectionnez **+ New | More| Other | Custom API Request Parameter**

> ![](./media/image50.png)

18. Pour **Custom API** , sélectionnez l'icône **Search** , puis
    sélectionnez **Match** (votre API personnalisée).

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image51.png)

19. Entrez **Pattern** pour Nom unique, Nom, Nom d'affichage et
    Description pour plus de simplicité.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image52.png)

20. Sélectionnez **String** pour Type.

> ![Une capture d'écran d'une chaîne Description générée
> automatiquement](./media/image53.png)

21. Sélectionnez **Save and Close**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image54.png)

22. Sélectionnez **Done**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image55.png)

23. Sélectionnez **New | More | Other| Custom API Response Property**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image56.png)

24. Pour **Custom API**,sélectionnez l'icône **Search** , puis **Match**
    sélectionnez (votre API personnalisée).

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image57.png)

25. Entrez +++**Matched+++** pour **Unique Name**, **Name, Display
    Name** et **Description** pour plus de simplicité.

26. Sélectionnez **Boolean** pour **Type**.

> ![](./media/image58.png)

27. Sélectionnez **Save and Close.**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image59.png)

28. Sélectionnez **Done**.

> ![Une capture d'écran d'un texte blanc Description générée
> automatiquement](./media/image60.png)

29. La liste des composants de votre solution doit ressembler à ce qui
    suit.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image61.png)

**Tâche 4 : Utiliser l'API personnalisée de Power Automate**

1.  Dans la solution, sélectionnez **+ New | Automation | Cloud Flow |
    Instant**.

> ![](./media/image62.png)

2.  Entrez +++**String match+++** pour Nom du flux, sélectionnez
    **Manually trigger a flow** , puis sélectionnez **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image63.png)

3.  Sélectionnez **+ New Step**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image64.png)

4.  Recherchez perform et choisissez **Perform an unbound action**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image65.png)

5.  Dans la liste Nom de l'action, recherchez et sélectionnez
    **contoso_match**.

> ![](./media/image66.png)

6.  Entrez **myemail@outlook.com** adresse e-mail dans **StringIn**.
    Ici, vous pouvez saisir n'importe quelle adresse e-mail simple
    valide.

> ![](./media/image67.png)

7.  Entrez l'expression régulière suivante dans Modèle. Il s'agit d'un
    modèle d'e-mail simple. D'autres
    [*exemples*](https://regexlib.com/DisplayPatterns.aspx/) sont
    disponibles.

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image68.png)

8.  Votre flux doit ressembler à ce qui suit.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image69.png)

9.  Sélectionnez **Save**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image70.png)

10. Une fois l'enregistrement terminé, sélectionnez **Test**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image71.png)

11. Sélectionnez **Manually**, puis sélectionnez **Test**.

> ![Une capture d'écran d'un téléphone Description générée
> automatiquement](./media/image72.png)

12. Sélectionnez **Run flow**.

> ![Un fond blanc avec des points noirs Description générée
> automatiquement](./media/image73.png)

13. Sélectionnez **Done**.

> ![Une capture d'écran d'un téléphone Description générée
> automatiquement](./media/image74.png)

14. Une fois votre flux terminé, sélectionnez l'action **Perform an
    unbound action**  pour développer et afficher les résultats.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image75.png)
>
> ![Capture d'écran montrant les résultats de l'exécution du
> flux.](./media/image76.png)

**Résumé :** Dans cet atelier, vous avez appris à créer une action
personnalisée et à l'utiliser à partir d'un Power Automate flow. Le
contoso_match d'action d'API personnalisé est désormais également
disponible pour l'appel direct à l'aide de l'API de la plateforme.
