# **Atelier 8 : Création d'un modèle web extensible**

**Durée estimée :** 25 min

**Objectif :** Dans cet atelier, vous apprendrez à étendre les modèles
Liquid à l'aide des balises extend et block, à réutiliser les modèles
Liquid à l'aide de la balise include et à appliquer des autorisations de
table aux résultats du nouveau modèle.

**Tâche 1 : Créer un modèle partiel**

Votre première tâche consiste à créer un modèle partiel qui ne sera pas
utilisé pour afficher une page, mais qui sera inséré dans un autre
modèle.

1.  Connectez-vous à Power Pages
    +++<https://make.powerpages.microsoft.com/>+++.

2.  Sélectionnez l'environnement cible **Dev One** dans le coin
    supérieur droit.

> ![](./media/image1.png)

3.  Sous l'onglet **Active sites**, vous pouvez voir votre site –
    **Finance Advisor Search**. Sélectionnez **Edit**.

> ![](./media/image2.png)

4.  développez le menu d'extension (points de suspension), puis
    sélectionnez **Portal management**  pour ouvrir l'application
    Gestion du portail.

> ![](./media/image3.png)

5.  Sélectionnez **Web Templates**..

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image4.png)

6.  Sélectionnez +**New**.

> ![Une capture d'écran d'une page web Description générée
> automatiquement](./media/image5.png)

7.  Entrez les valeurs suivantes :

    - **Name** - +++Annuaire+++

    &nbsp;

    - **Website** - Sélectionnez votre site Web actuel - Recherche de
      conseillers financiers

    &nbsp;

    - **Source** : entrez le contenu suivant :

> {% fetchxml accounts %}
>
> \<fetch\>
>
> \<entity name="account"\>
>
> \<attribute name="name" /\>
>
> \</entity\>
>
> \</fetch\>
>
> {% endfetchxml %}
>
> {% if accounts.global_permission_granted %}
>
> \<ul\>
>
> {% for account in accounts.results.entities %}
>
> \<li\>{{ account.name }}\</li\>
>
> {%- endfor -%}
>
> \</ul\>
>
> {% else %}
>
> \<div class="alert alert-warning"\>You do not have permissions to
> access the directory.\</div\>
>
> {% endif %}
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image6.png)

8.  Sélectionnez **Save & Close**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image7.png)

**Tâche 2 : Étendre un modèle existant**

Ensuite, vous allez créer un nouveau modèle qui étend un modèle Liquid
existant, puis insérer le modèle que vous avez précédemment créé.

1.  Dans le volet de navigation de gauche, sélectionnez **Web
    Templates**.. Sélectionnez +**New**.

> ![](./media/image8.png)

2.  Entrez les valeurs suivantes :

    - **Name** - +++Modèle d'annuaire+++

    &nbsp;

    - **Website** - Sélectionnez votre site Web actuel - Recherche de
      conseillers financiers

    &nbsp;

    - **Source** : entrez le contenu suivant :

> {% extends "Layout 2 Column Wide Left" %}
>
> {% block aside %}
>
> \<h2\>Directory\</h2\>
>
> {% include 'Directory' %}
>
> {% endblock %}
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image9.png)

3.  Sélectionnez **Save & Close**.

> ![Une capture d'écran d'un modèle Web Description générée
> automatiquement](./media/image10.png)

**Tâche 3 : Créer un modèle de page et l'associer à cette page**

Dans cette tâche, vous allez créer un modèle de page qui utilise votre
nouveau modèle Web et qui inclura la sortie du Répertoire.

1.  Dans le volet de navigation de gauche, sélectionnez **Page
    Templates**. Sélectionnez +**New**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image11.png)

2.  Entrez les valeurs suivantes :

    - **Name** - +++Modèle de page d'annuaire+++

    &nbsp;

    - **Website** - Sélectionnez le site Web actuel - Recherche de
      conseillers financiers

    &nbsp;

    - **Type** - Sélectionner **un modèle Web**

    &nbsp;

    - **Web Template**  - Sélectionnez **Directory Template**

    &nbsp;

    - **Nom de la table** - Sélectionner **Web page**

3.  **Facultatif :** Ajoutez un élément de texte au contenu de la page,
    puis saisissez le texte de votre choix.

4.  Sélectionnez **Save & Close**..

> ![Une capture d'écran d'une page web Description générée
> automatiquement](./media/image12.png)

**Tâche 4 : Tester le modèle de page**

L'étape suivante consiste à tester que votre nouveau modèle fonctionne :

1.  Revenez à l'onglet Accueil du studio de design Power Pages.

2.  Sélectionnez **Sync** pour synchroniser les modifications.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image13.png)

3.  Sélectionnez l' espace de travail Pages. Sélectionnez **+ Page**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image14.png)

4.  Dans la boîte de dialogue **Add a page** , procédez comme suit :

    1.  Entrez +++**Directory+++** comme nom de page.

    &nbsp;

    1.  Sélectionnez **Custom layouts** , puis Sélectionnez Modèle
        **Directory Page Template**.

    &nbsp;

    1.  Sélectionnez **Add**.

> ![Une capture d'écran d'un site web Description générée
> automatiquement](./media/image15.png)
>
> La page vide s'affichera avec le message “Vous n'avez pas les
> autorisations pour accéder au repertoire” dans le panneau de droite.
>
> ![](./media/image16.png)

**Tâche 5 : Ajouter des autorisations de table**

**Avertissement :** L'octroi d'une autorisation de lecture globale à des
utilisateurs anonymes n'est fourni qu'à titre d'illustration. Faites
attention à ne pas exposer involontairement des informations sensibles
en accordant des autorisations excessives et en n'incluant pas les
filtres appropriés dans vos vues ou expressions FetchXML.

Suivez ces étapes pour ajouter des autorisations de table.

1.  Sélectionnez **Security workspace** , puis Autorisations **Table
    Permissions**.

> ![Une capture d'écran d'une sécurité informatique Description générée
> automatiquement](./media/image17.png)

2.  Sélectionnez **+ New Permissions**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image18.png)

3.  Entrez les valeurs suivantes :

    - **Name**- +++Répertoire des comptes+++

    &nbsp;

    - **Table** - Sélectionnez la **Table** Compte (compte)

    &nbsp;

    - **Access Type** : sélectionnez **global Access**

    &nbsp;

    - **Permission to** - Sélectionnez **Read**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image19.png)

4.  Sélectionnez **Add roles**.

5.  Sélectionnez **Anonymous users** et **Authenticated users**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image20.png)

6.  Sélectionnez **Save**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image21.png)

7.  Sélectionnez **Save**.

> ![Une capture d'écran d'un message d'erreur d'ordinateur Description
> générée automatiquement](./media/image22.png)

**Tâche 6 : Tester le modèle**

Votre dernière tâche consiste à tester votre nouveau modèle :

1.  Sélectionnez l'espace de **t**ravail **Pages**, puis la page
    Sélectionnez **Directory**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image23.png)

2.  Sélectionnez **Preview | Desktop**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image24.png)
>
> **Remarque :** Une simple actualisation de la page du navigateur ne
> suffira pas à mettre à jour les données. L'utilisation de cette
> commande à la place reconstruit le cache du site.
>
> La page devrait maintenant s'afficher et inclure la liste des comptes
> dans le panneau de droite.
>
> ![Une capture d'écran d'un moteur de recherche Description générée
> automatiquement](./media/image25.png)

**Résumé :** Dans cet atelier, vous avez appris à créer et à étendre des
modèles Liquid. Vous avez créé un nouveau modèle de page qui inclut un
panneau latéral qui répertorie tous les comptes dans Dataverse.
