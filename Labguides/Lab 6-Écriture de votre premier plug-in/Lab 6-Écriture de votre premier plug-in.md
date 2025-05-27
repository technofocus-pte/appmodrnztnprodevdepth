**Atelier 6 - Écriture de votre premier plug-in**

**Durée estimée :** 30 min

**Objectif :** Dans ce scénario, une organisation doit s'assurer que les
données du numéro de téléphone sont saisies dans un format cohérent.
Pour atteindre cet objectif, vous allez créer un plug-in à exécuter lors
de la création/mise à jour qui supprime tous les caractères non
numériques d'un numéro de téléphone avant de l'enregistrer dans
Dataverse.

Dans cet atelier, vous allez apprendre à créer un plug-in qui
s'exécutera lors de la création et de la mise à jour. Ce plug-in
supprimera tous les caractères non numériques d'un numéro de téléphone.

**Tâche 1 : Créer une solution et une application pilotée par modèle**

1.  Accédez à [Power Apps](https://make.powerapps.com/) à l'aide de
    +++<https://make.powerapps.com/>+++. Assurez-vous que vous êtes dans
    l' environnement **Dev One**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image1.png)

2.  Dans le volet de navigation de gauche, sélectionnez **Solutions**,
    puis sélectionnez **Nouvelle** **solution**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image2.png)

3.  Dans la boîte de dialogue contextuelle, spécifiez **Display name** –
    +++Plugin Lab+++, **Name** – +++PluginLab+++, **PUblisher** – CDS
    Éditeur par défaut, puis sélectionnez **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image3.png)

4.  Pour créer une application pilotée par modèle dans votre solution,
    sélectionnez **New** | **App** | **Model-driven app.**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image4.png)

5.  Donnez le **name** à votre application pilotée par modèle sous la
    forme +++Fundraiser+++, puis sélectionnez **Create**.

> ![](./media/image5.png)

6.  Dans l'application pilotée par modèle, sélectionnez **+Add page**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image6.png)

7.  Sélectionnez **Dataverse** **Table** dans la fenêtre contextuelle
    qui s'affiche.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image7.png)

8.  Sélectionnez Table des **contact**, puis Sélectionnez Add.

> ![](./media/image8.png)
>
> **Remarque :** Pour cet atelier, nous utilisons la table Contact.

9.  Maintenant, votre application pilotée par modèle, nommée
    ‘Funraiser’, est prête.

> ![](./media/image9.png)

10. Sélectionnez **Save** dans le coin supérieur droit.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image10.png)

11. Sélectionnez **Publish**.

> ![Un rectangle violet et blanc Description générée
> automatiquement](./media/image11.png)

12. Cliquez sur **back arrow** pour revenir dans votre solution.

> ![Une capture d'écran d'un navigateur Description générée
> automatiquement](./media/image12.png)

13. Cliquez sur **back arrow** et vous serez sur la page de la solution
    où toutes les solutions sont répertoriées.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image13.png)

**Tâche 2 : Créer un plug-in**

1.  Démarrez **Visual Studio 2022**. Pour l'ouvrir, cliquez sur le menu
    Démarrer de la machine virtuelle, tapez Visual Studio dans la zone
    de recherche et sélectionnez **Open**.

> ![](./media/image14.png)

2.  Sélectionnez Fichier **| New | Project.**

> ![](./media/image15.png)

3.  Sélectionnez **Class Library (.NET Framework)** puis Sélectionnez
    **Next**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image16.png)

4.  Entrez **D365PackageProject** Pour **Project Name**, sélectionnez un
    emplacement pour enregistrer le projet,

> ![](./media/image17.png)

5.  sélectionnez **.NET Framework 4.7.1** pour **Framework**, puis
    sélectionnez **Create**.

> ![](./media/image18.png)

6.  Cliquez avec le bouton droit sur le projet et sélectionnez **Manage
    NuGet Packages**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image19.png)

7.  Sélectionnez l' onglet **Browse**, recherchez et sélectionnez
    **microsoft.crmsdk.coreassemblies**, puis sélectionnez **Install**.

> ![](./media/image20.png)

8.  Dans la fenêtre Aperçu des modifications, sélectionnez **Apply**
    pour permettre à Visual Studio d'apporter des modifications à la
    solution.

> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image21.png)

9.  Sélectionnez **I accepte** pour accepter les termes du contrat de
    licence.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image22.png)

10. Fermez le gestionnaire de packages NuGet.

> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image23.png)

11. Cliquez avec le bouton droit **Class1.cs** et **Delete**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image24.png)

12. Sélectionnez **OK** pour Class1.cs supprimer définitivement.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image25.png)

13. Cliquez avec le bouton droit sur le projet, puis sélectionnez **Add
    | Class**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image26.png)

14. Nommez la nouvelle classe **PreOperationFormatPhoneCreateUpdate** et
    sélectionnez **Add**.

> ![](./media/image27.png)

15. Ajoutez les instructions using à la nouvelle classe comme suit :

> using Microsoft.Xrm.Sdk;
>
> using System.Text.RegularExpressions;
>
> ![](./media/image28.png)

16. Pour rendre la classe **public**, remplacez l'interne par public et
    tapez **: IPlugin** à la fin de l'étape pour ajouter l'interface
    IPlugin comme indiqué dans l'image ci-dessous.

> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image29.png)

17. Passez la souris sur l'interface IPlugin, cliquez sur l'icône
    d'action rapide qui apparaît, puis sélectionnez **Implement
    interface**.

> ![](./media/image30.png)
>
> Votre classe doit maintenant ressembler à l'image suivante.
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image31.png)

**Tâche 3 : Mettre en forme un numéro de téléphone**

1.  Obtenez le contexte d'exécution auprès du fournisseur de services.
    Remplacez l'exception dans la méthode Execute par l'extrait de code
    suivant.

> IPluginExecutionContext context =
>
> (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext)) ;
>
> ![](./media/image32.png)

2.  Vérifiez le paramètre d'entrée pour Target. Ajoutez l'extrait de
    code suivant à la méthode Execute.

> if (!context.InputParameters.ContainsKey("Target"))
>
> throw new InvalidPluginExecutionException("No target found");
>
> ![](./media/image33.png)

3.  Ajoutez l'extrait de code suivant à la méthode Execute. Cet extrait
    de code va récupérer l'entité cible à partir du paramètre d'entrée,
    puis vérifier si ses attributs contiennent telephone1 (Business
    Phone pour les contacts, Phone pour les comptes).

> var entity = context.InputParameters\["Target"\] as Entity;
>
> if (!entity.Attributes.Contains("telephone1"))
>
> return;
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image34.png)

4.  Ajoutez l'extrait de code suivant à la fonction Exécuter. Cet
    extrait de code supprimera tous les caractères non numériques du
    numéro de téléphone fourni par l'utilisateur.

> string phoneNumber = (string)entity\["telephone1"\];
>
> var formattedNumber = Regex.Replace(phoneNumber, @"\[^\d\]", "");
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image35.png)

5.  Définissez telephone1 sur le numéro de téléphone formaté. Ajoutez
    l'extrait de code suivant à la méthode Execute.

> entity\["telephone1"\] = formattedNumber;
>
> ![Capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image36.png)
>
> La méthode Execute doit maintenant ressembler à l'image suivante.
>
> ![Capture d'écran de la méthode execute.](./media/image37.png)

6.  Cliquez avec le bouton droit sur le projet et sélectionnez
    **Properties**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image38.png)

7.  Sélectionnez l' onglet **Signing** et sélectionnez \<**New... \>**
    fichier clé.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image39.png)

8.  Entrez +++**contoso.snk**+++ dans le champ **Key file name** ,
    désactivez la case **Protect my key file with a password**  puis
    sélectionnez **OK**.

> ![](./media/image40.png)

9.  Fermez l' onglet **Properties.**

> ![](./media/image41.png)

10. Sélectionnez l'onglet **Build** et cliquez sur **Build Project**

> ![Une capture d'écran d'un programme informatique Description générée
> automatiquement](./media/image42.png)

11. Assurez-vous que la build réussit.

> ![Une capture d'écran d'un jeu vidéo Description générée
> automatiquement](./media/image43.png)

**Tâche 4 : Enregistrer un plug-in et étapes**

1.  Allez dans le menu **Start** de la machine virtuelle, tapez outil
    d'enregistrement de plug-in dans la zone de recherche et cliquez sur
    **Open**.

> ![](./media/image44.png)

2.  Sélectionnez **Create New connection**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image45.png)

3.  Sélectionnez **Office 365,** cochez la case **Show Advanced** , dans
    le champ Région en ligne, sélectionnez **Don’t know** , fournissez
    vos informations d'identification (M365 Admin tenant), puis
    sélectionnez **Login**.

> ![](./media/image46.png)

4.  Sélectionnez **Register**, puis Sélectionnez **Register New
    Assembly**

> ![](./media/image47.png)

5.  Sélectionnez **...** à l'étape 1, puis accédez à la **Bin |
    Debug** de la bibliothèque de classes que vous avez créée.

> ![Un fond blanc avec du texte noir Description générée
> automatiquement](./media/image48.png)

6.  Sélectionnez **D365PackageProject.dll**, puis Sélectionnez **Open**.

> ![](./media/image49.png)

7.  Sélectionnez **Register Selected Plugins**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image50.png)

8.  Sélectionnez **OK**.

> ![](./media/image51.png)

9.  Développez l'assembly nouvellement enregistré – **(Assembly)
    D365PackageProject**.

> ![](./media/image52.png)

10. Cliquez avec le bouton droit de la souris sur le plug-in et
    sélectionnez **Register New Step**

> ![](./media/image53.png)

11. Sélectionnez **Create** pour **Message** et sélectionnez **Contact**
    pour **Primary Entity**.

> ![](./media/image54.png)

12. Sélectionnez **PreOperation** pour **Event Pipeline Stage of
    Execution**  puis sélectionnez **Register New Step**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image55.png)

13. Sélectionnez **Close** sur la page Avertissement qui indique
    qu'aucun filtre sur les attributs n'a été détecté.

> ![](./media/image56.png)

14. Si vous obtenez un message d'erreur, c'est-à-dire qu'une erreur
    s'est produite lors de l'enregistrement de l'étape, sélectionnez
    **No** pour afficher les détails.

> ![Une capture d'écran d'une erreur informatique Description générée
> automatiquement](./media/image57.png)

15. Vérifiez que l'étape de création a été créée sous le plugin.

> ![Une ligne rouge avec du texte noir Description générée
> automatiquement](./media/image58.png)

16. Cliquez avec le bouton droit sur le plug-in et sélectionnez à
    nouveau **Register New Step** .

> ![](./media/image59.png)

17. Sélectionnez **Update** pour **Message**, sélectionnez **Contact**
    pour **Primary Entity** ,puis sélectionnez la recherche
    **Attributs.**

> ![](./media/image60.png)

18. Décochez la case **Select All**, cochez la case **Business phone**,
    puis sélectionnez **OK**.

> ![](./media/image61.png)

19. Sélectionnez **PreOperation**  pour **Event Pipeline Stage of
    Execution**  puis sélectionnez **Register New Step**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image62.png)

20. Si vous obtenez un message d'erreur, c'est-à-dire qu'une erreur
    s'est produite lors de l'enregistrement de l'étape, sélectionnez
    **No** pour afficher les détails.

> ![Une capture d'écran d'une erreur informatique Description générée
> automatiquement](./media/image57.png)

21. Vérifiez que l'étape de création a été créée sous le plugin.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image63.png)

**Tâche 5 : Tester le plug-in**

1.  Accédez à votre Maker Portal +++<https://make.powerapps.com/>+++ et
    assurez-vous que vous êtes dans l' environnement **Dev One**
    sélectionné.

2.  Sélectionnez **Apps** et lancez l' application **Fundraiser**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image64.png)

3.  Sélectionnez **+ New**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image65.png)

4.  Entrez +++**Test+++** pour **first name** , +++**Contact+++** pour
    **last name**, +++**(123)-555-0100+++** pour **Business Phone**,
    puis sélectionnez **Save**.

> ![Une capture d'écran d'un formulaire de contact Description générée
> automatiquement](./media/image66.png)
>
> L'enregistrement doit être sauvegardé et le **t Business Phone** ne
> doit afficher que les valeurs numériques.
>
> ![](./media/image67.png)

5.  Changez le **Business Phone** pour **001-123-555-0100** et cliquez
    sur **Save**. L'enregistrement doit être mis à jour et le **Business
    Phone** ne doit afficher que les valeurs numériques.

> ![Une capture d'écran d'un formulaire de contact Description générée
> automatiquement](./media/image68.png)

**Résumé :** Dans cet atelier, vous avez appris à créer un plug-in qui
s'exécutera lors de la création et de la mise à jour, ainsi qu'à
supprimer tous les caractères non numériques d'un numéro de téléphone à
l'aide de ce plug-in.
