**Atelier 1 - Création d'un connecteur personnalisé pour l'API existante
et utilisation de celui-ci dans l'application canvas**

**Durée estimée :** 35 min

**Objectif :** Dans cet atelier, vous allez apprendre à créer votre
premier connecteur personnalisé pour une API existante appelée Contoso
Invoicing, à créer une application canevas et à utiliser le connecteur
dans l'application canevas.

**Tâche 1 : Examiner l'API**

Pour examiner l'API, procédez comme suit :

1.  Allez à +++<https://contosoinvoicing.azurewebsites.net/>+++.

2.  Pour sélectionner le lien de la documentation, cliquez **Here** à
    côté de ‘ Vous pouvez trouver la documentation de l'API ‘.

> ![](./media/image1.png)

3.  Passez en revue les opérations disponibles.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image2.png)

4.  Fermez l'onglet ou la fenêtre du navigateur de documentation.

5.  Sélectionnez le lien **Open API definition** .

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image3.png)

6.  L'image suivante montre un exemple de la version OpenAPI de ce qui a
    été montré sur la page de documentation. Cliquez avec le bouton
    droit de la souris et sélectionnez **Save as** .

> ![Capture d'écran d'une flèche pointant vers le bouton Enregistrer
> sous.](./media/image4.png)

7.  Enregistrez le fichier localement sur le bureau de la machine
    virtuelle. Vous utiliserez ce fichier plus loin dans l'exercice.

8.  Fermez l'onglet ou la fenêtre du navigateur de définitions.

9.  Sélectionnez le lien **API Key** .

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image5.png)

10. Copiez et enregistrez votre clé API dans le bloc-notes de votre
    machine virtuelle, car vous en aurez besoin plus tard.

> ![](./media/image6.png)

11. Sélectionnez **Return to home**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image7.png)

12. Sélectionnez **Download Logo**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image8.png)

13. Enregistrez l'image du logo localement sur le bureau de la machine
    virtuelle ; Vous l'utiliserez plus tard.

**Tâche 2 : Créer une solution**

Pour créer une solution, procédez comme suit :

1.  Accédez à <https://make.powerapps.com/> et assurez-vous que vous
    êtes dans l' environnement **Dev One**.

> ![](./media/image9.png)

2.  Dans le volet de navigation de gauche, sélectionnez **Solutions**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image10.png)

3.  Sélectionnez **+New solution** dans le ruban supérieur.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image11.png)

4.  Entrez +++**Contoso invoicing**+++ pour le **Display name**  et
    sélectionnez **+ New publisher**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image12.png)

5.  Entrez +++**Contoso**+++ pour Nom d'affichage, +++**Contoso**+++
    pour Nom, +++**contoso**+++ pour Préfixe, puis sélectionnez
    **Save**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image13.png)
>
> **Remarque :** Si vous recevez un message ‘d'erreur indiquant qu'il
> existe déjà un enregistrement avec des valeurs de clé
> correspondantes‘, ignorez-le et fermez la fenêtre ‘Nouvel éditeur ‘.
>
> ![](./media/image14.png)

6.  Maintenant, dans la fenêtre **New solution**, sélectionnez
    **Contoso** pour **Publisher**, puis Créer. Lorsque vous travaillez
    sur un vrai projet, il est préférable de créer votre propre éditeur.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image15.png)

7.  Ne quittez pas cette page après avoir sélectionné **Create**. Vous
    serez automatiquement redirigé vers la solution de facturation
    Contoso.

**Tâche 3 : Créer un connecteur**

Pour créer un connecteur, procédez comme suit :

1.  Assurez-vous que vous êtes dans la **s**olution **Contoso
    invoicing**  que vous avez créée.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image16.png)

2.  Sélectionnez **+ New** | **Automation** | **Custom connector**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image17.png)

3.  Entrez +++**Contoso invoicing**+++ pour le **connector name**.

> ![](./media/image18.png)

4.  Sélectionnez **Télécharger** pour télécharger l'image.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image19.png)

5.  Sélectionnez l'image du logo du connecteur que vous avez téléchargée
    dans **Task 1: Review the API**.

6.  Entrez +++**\#175497+++** pour **Icon background color**.

7.  Entrez +++**Custom connector for Contoso Invoicing
    API**+++ pour **Description**.

8.  Entrez +++**contosoinvoicingtest.azurewebsites.net+++** pour
    **Host**.

> ![](./media/image20.png)

9.  Sélectionnez **Create connector**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image21.png)

10. Ne vous éloignez pas de cette page.

**Tâche 4 : Importer la définition OpenAPI**

Pour importer la définition OpenAPI, procédez comme suit :

1.  Sélectionnez la flèche en regard de **Connector Name**.

> ![Une capture d'écran d'un écran d'ordinateur Description générée
> automatiquement](./media/image22.png)

2.  Sélectionnez les points de suspension (**...**) du connecteur, puis
    sélectionnez **Update from OpenAPI file**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image23.png)

3.  Sélectionnez **Import**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image24.png)

4.  Sélectionnez le **swagger.json**  que vous avez téléchargé dans
    **Task 1: Review the API** , puis sélectionnez **Open**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image25.png)

5.  Sélectionnez **Continue**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image26.png)

6.  Renseignez l'URL de l'hôte sous la forme
    +++**contosoinvoicingtest.azurewebsites.net+++,** puis sélectionnez
    **Security**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image27.png)

7.  Notez que les champs sont remplis à partir du fichier importé.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image28.png)

8.  Ne vous éloignez pas de cette page.

**Tâche 5 : Examiner et ajuster les définitions**

Pour examiner et ajuster les définitions, procédez comme suit :

1.  Sélectionnez l' onglet **Définition**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image29.png)

2.  Prenez quelques minutes pour passer en revue les opérations qui ont
    été importées.

3.  Remarquez le cercle d'information bleu à côté de **GetInvoice**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image30.png)

4.  Sélectionnez l' opération **GetInvoice**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image31.png)

5.  Notez que l'opération indique un **summary** manquant.

> ![Une capture d'écran d'un téléphone Description générée
> automatiquement](./media/image32.png)

6.  Entrez **Get Invoice**  comme **summary** pour améliorer la
    convivialité.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image33.png)

7.  Notez le cercle d'information bleu en regard de l' opération
    **PayInvoice** et qu'il indique une **description** manquante.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image34.png)

8.  Sélectionnez l 'opération **PayInvoice.**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image35.png)

9.  Entrez **Pay an invoice**  comme **Description**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image36.png)

10. Supprimez les deux opérations **NewInvoice**, car vous ne les
    utiliserez pas.

> ![Capture d'écran montrant le bouton d'action de
> suppression.](./media/image37.png)

11. Sélectionnez l' opération **GetInvoiceSchema**.

> ![](./media/image38.png)

12. Modifiez l' option **Visibility**sur **internal** afin que les
    utilisateurs ne la voient pas dans leur liste d'actions, puis
    sélectionnez **Update connector**.

> ![](./media/image39.png)

13. Ne vous éloignez pas de cette page.

**Tâche 6 : Tester le connecteur**

Pour tester le connecteur, procédez comme suit :

1.  Sélectionnez l' onglet **Test**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image40.png)

2.  Sélectionnez **+ New connection**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image41.png)

3.  Collez la **API key** que vous avez enregistrée dans **Task 1:
    Review the API** , puis sélectionnez **Create connection**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image42.png)

4.  Sélectionnez le bouton **Refresh**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image43.png)

5.  Sélectionnez **ListInvoiceTypes | Test Operation**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image44.png)

6.  Vous devriez voir les données des types de factures dans la zone du
    corps.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image45.png)

7.  Sélectionnez **Close** pour fermer la fenêtre du connecteur
    personnalisé.

> ![](./media/image46.png)

**Tâche 7 : Utiliser un connecteur personnalisé dans l'application
canevas**

Dans cette tâche, vous allez créer une application canevas et utiliser
le connecteur personnalisé que vous avez créé pour afficher une liste de
factures.

1.  Revenez au portail du créateur Power Apps. Sélectionnez la fenêtre
    Qui surgit **Done** sur qui indique « En cours de création d'un
    connecteur personnalisé ». Assurez-vous que vous êtes dans l'
    environnement **Dev One**.

> ![](./media/image47.png)
>
> **Remarque :** Si le portail n'est pas déjà ouvert, accédez à
> +++<https://make.powerapps.com/>+++ et assurez-vous que vous êtes dans
> l' **environnement Dev One**.

2.  Assurez-vous que vous êtes dans la **solution de facturation
    Contoso** que vous avez créée. Si ce n'est pas le cas, sélectionnez
    **Solutions** et ouvrez la solution **Contoso invoicing**  que vous
    avez créée.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image48.png)

3.  Sélectionnez **+ New**, puis \> **App \> Canvas app**.

> ![](./media/image49.png)

4.  Entrez **Contoso invoicing app**  pour Nom de l'application,
    sélectionnez **Phone**  pour Format, puis **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image50.png)

5.  Sélectionnez **Skip** dans la fenêtre d'accueil.

> ![](./media/image51.png)

6.  Sélectionnez l' onglet **Data**, sélectionnez **+ Add data**..

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image52.png)

7.  développez **Connectors**, puis sélectionnez le connecteur
    personnalisé **de Contoso invoicing**  que vous avez créé.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image53.png)

8.  Sélectionnez le **+ Add a connector**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image54.png)

9.  Collez la clé API que vous avez enregistrée dans la **Task 1: Review
    the API** , puis sélectionnez **connect**.

> ![Une capture d'écran d'une boîte de connexion Description générée
> automatiquement](./media/image55.png)

10. Sélectionnez **Got it** dans la fenêtre contextuelle d'avertissement
    premium.

> ![Une capture d'écran d'un téléphone Description générée
> automatiquement](./media/image56.png)

11. Sélectionnez l' onglet **Tree view** 

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image57.png)

12. Sélectionnez **+ Insert**, puis Sélectionnez **Vertical gallery**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image58.png)

13. Sélectionnez **ContosoInvoicing** pour les données.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image59.png)

14. Définissez les **Items**  sur la valeur ci-dessous.

> +++ContosoInvoicing.ListInvoices().invoices+++
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image60.png)

15. Développez la galerie et sélectionnez le **subtitle**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image61.png)

16. Définissez la valeur **Text** du sous-titre sur
    +++**ThisItem.amount**+++.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image62.png)

17. Développez la galerie et sélectionnez le **title** à l'intérieur de
    la galerie.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image63.png)

18. Définissez la valeur **Texte** du titre sur
    +++**ThisItem.accountName**+++.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image64.png)

19. La galerie doit maintenant ressembler à l'image ci-dessous.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image65.png)

**Résumé :** Dans cet atelier, vous avez appris à créer un connecteur
personnalisé pour une API existante, à importer la définition d'API et à
utiliser ce connecteur dans l'application canevas pour afficher une
liste de factures. Les connecteurs personnalisés sont basés sur des
fonctions, ils appellent des fonctions spécifiques dans le service
sous-jacent de l'API pour retourner les données correspondantes.
