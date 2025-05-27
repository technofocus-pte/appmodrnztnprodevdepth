# **Lab 8: Creare un modello Web estendibile**

**Durata stimata:** 25 min

**Obiettivo:** In questa esercitazione imparerai come estendere i
modelli Liquid utilizzando i tag extend e block, come riutilizzare i
modelli Liquid utilizzando il tag include e come applicare le
autorizzazioni di tabella ai risultati del nuovo modello.

**Attività 1: Creare un modello parziale**

La prima attività consiste nel creare un modello parziale che non verrà
utilizzato per il rendering di una pagina, ma verrà invece inserito in
un altro modello.

1.  Accedi a Power Pages +++<https://make.powerpages.microsoft.com/>+++.

2.  Seleziona l'ambiente di destinazione **Dev One** nell'angolo in alto
    a destra.

> ![](./media/image1.png)

3.  Nella scheda **Active sites**, puoi vedere il Suoi sito: **Finance
    Advisor Search**. Seleziona **Edit**.

> ![](./media/image2.png)

4.  Espandere il menu di estensione (puntini di sospensione), quindi
    selezionare **Portal management** per aprire l'app Gestione portale.

> ![](./media/image3.png)

5.  Seleziona **Web Templates**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image4.png)

6.  Seleziona +**New**.

> ![Uno screenshot di una pagina web Descrizione generata
> automaticamente](./media/image5.png)

7.  Immettere i seguenti valori:

    - **Name** - +++Directory+++

    &nbsp;

    - **Website** - Seleziona il Suoi sito web attuale - Finance Advisor
      Search

    &nbsp;

    - **Source**: immettere il contenuto seguente:

> {% fetchxml accounts%}
>
> \<fetch\>
>
> \<entity name="account"\>
>
> \<attribute name ="name" /\>
>
> \</entity\>
>
> \</fetch\>
>
> {% endfetchxml %}
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
> \<div class="alert alert-warning"\> You do not have permissions to
> access directory.\</div\>
>
> {% endif %}
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image6.png)

8.  Seleziona **Save & Close**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image7.png)

**Attività 2: Estendere un modello esistente**

Successivamente, creerai un nuovo modello che estende un modello Liquid
esistente e quindi inserirai il modello creato in precedenza.

1.  Nel riquadro di spostamento a sinistra, selezionare **Web
    Templates**. Seleziona +**New**.

> ![](./media/image8.png)

2.  Immettere i seguenti valori:

    - **Name** - +++Modello di directory+++

    &nbsp;

    - **Website** - Seleziona il Suoi sito web attuale - Finance Advisor
      Search

    &nbsp;

    - **Source**: immettere il contenuto seguente:

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
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image9.png)

3.  Seleziona **Save & Close**.

> ![Uno screenshot di un modello web Descrizione generata
> automaticamente](./media/image10.png)

**Attività 3: Creare un modello di pagina e associarlo a tale pagina**

In questa attività verrà creato un modello di pagina che utilizza il
nuovo modello Web e includerà l'output della directory.

1.  Nel riquadro di spostamento a sinistra, seleziona **Page
    Templates**. Seleziona +**New**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image11.png)

2.  Immettere i seguenti valori:

    - **Name** - +++Directory Page Template+++

    &nbsp;

    - **Website** - Seleziona il sito web corrente – Finance Advisor
      Search

    &nbsp;

    - **Type** - Seleziona **Web Template**

    &nbsp;

    - **Web Template** - Seleziona **Directory Template**

    &nbsp;

    - **Table Name** - Seleziona **Web Page**

3.  **Optional:** aggiungi un elemento di testo al contenuto della
    pagina e quindi inserisci il testo che preferisci.

4.  Seleziona **Save & Close**.

> ![Uno screenshot di una pagina web Descrizione generata
> automaticamente](./media/image12.png)

**Attività 4: Testare il modello di pagina**

Il passaggio successivo consiste nel verificare il funzionamento del
nuovo modello:

1.  Torna alla scheda Home di Power Pages Design Studio.

2.  Seleziona **Sync** per sincronizzare le modifiche.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image13.png)

3.  Seleziona l' area di lavoro **Pages**. Seleziona **+ Page**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image14.png)

4.  Nella finestra di dialogo **Add a page**, completare i seguenti
    passaggi:

    1.  Immettere +++**Directory**+++ come nome della pagina.

    &nbsp;

    1.  Seleziona **Custom** **Layout,** quindi seleziona **Directory
        Page Template**.

    &nbsp;

    1.  Seleziona **Add**.

> ![Uno screenshot di un sito web Descrizione generata
> automaticamente](./media/image15.png)
>
> La pagina vuota verrà visualizzata con il messaggio "**You don't have
> permissions to access the directory**" nel pannello di destra.
>
> ![](./media/image16.png)

**Attività 5: Aggiungere le autorizzazioni per le tabelle**

**Attenzione:** la concessione dell'autorizzazione di lettura globale
agli utenti anonimi è solo a scopo illustrativo. Prestare attenzione per
evitare di esporre involontariamente informazioni riservate concedendo
autorizzazioni eccessive e non includendo filtri appropriati nelle
visualizzazioni o nelle espressioni FetchXML.

Segui questi passaggi per aggiungere le autorizzazioni della tabella.

1.  Selezionare **Security Workspace**, quindi selezionare **Table
    Permissions**.

> ![Uno screenshot di un computer di sicurezza Descrizione generata
> automaticamente](./media/image17.png)

2.  Seleziona **+ New permission**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image18.png)

3.  Immettere i seguenti valori:

    - **Name** - +++Directory account+++

    &nbsp;

    - **Table**- Seleziona la tabella **Account**(**account**)

    &nbsp;

    - **Access type**: selezionare **Global access**

    &nbsp;

    - **Permission to**- Seleziona **Read**

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image19.png)

4.  Seleziona **Add roles**.

5.  Selezionare **Anonymous** **users** e **Autenticated users**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image20.png)

6.  Seleziona **Save**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image21.png)

7.  Seleziona **Save**.

> ![Uno screenshot di un messaggio di errore del computer Descrizione
> generata automaticamente](./media/image22.png)

**Attività 6: Testare il modello**

Il Suoi compito finale è testare il Suoi nuovo modello:

1.  Selezionare l' area di lavoro **Pages** e quindi selezionare la
    pagina **Directory**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image23.png)

2.  Seleziona **Preview| Desktop**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image24.png)
>
> **Nota:** un semplice aggiornamento della pagina del browser non sarà
> sufficiente per aggiornare i data. L'uso di questo comando
> ricostruisce invece la cache del sito.
>
> La pagina dovrebbe ora essere visualizzata e includere l'elenco degli
> account nel pannello di destra.
>
> ![Uno screenshot di un motore di ricerca Descrizione generata
> automaticamente](./media/image25.png)

**Riepilogo:** in questo laboratorio hai imparato a creare ed estendere
i modelli di Liquid. Hai creato un nuovo modello di pagina che include
un pannello laterale che elenca tutti gli account in Common Data
Service.
