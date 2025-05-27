**Lab 3 - Installare e utilizzare gli strumenti di sviluppo**

**Durata stimata:** 15 min

**Obiettivo:** In questo lab si apprenderà come installare alcuni degli
strumenti di sviluppo di NuGet.

**Attività 1: Installare gli strumenti di sviluppo**

In questa attività, utilizzerai un'interfaccia della riga di comando di
Power Platform per installare gli strumenti.

1.  Per avviare il **Command Prompt**, vai al menu **Start** della VM,
    digita Prompt dei comandi nella casella di ricerca e seleziona
    **Open**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image1.png)

2.  Eseguire il comando seguente per installare lo **Configuration
    Manager Tool**.

> +++pac tool cmt+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image2.png)

3.  Lo strumento Configuration Manager deve essere installato e avviato.
    Chiudere lo strumento Configuration Manager.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image3.png)

4.  Esegui il comando seguente per installare lo **Package Deployer
    Tool**.

> +++pac tool pd+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image4.png)

5.  Lo strumento Package deployer deve essere installato e avviato.
    Chiudere lo strumento **Package Deployer**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image5.png)

6.  Esegui il comando seguente per installare lo **Plugin Registration
    Tool**.

> +++pac tool prt+++
>
> ![](./media/image6.png)

7.  La registrazione del plug-in deve essere installata e avviata. Non
    chiudere lo **Plugin Registration Tool**.

> ![](./media/image7.png)

**Attività 2: Esplorare un plug-in registrato con lo strumento di
registrazione dei plug-in**

1.  Seleziona **Create New Connection.**

> ![](./media/image8.png)

2.  Selezionare la casella di controllo Visualizza **Display list of
    available organizations**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image9.png)

3.  Seleziona **Login.**

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image10.png)

4.  Accedi con le credenziali dell'ambiente Common Data Service, ad
    esempio le credenziali di amministratore di Office 365. Fare clic su
    **Next**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image11.png)

5.  Immettere la password del tenant amministratore e fare clic su
    **Sign in**.

> ![Uno screenshot di una casella di accesso Descrizione generata
> automaticamente](./media/image12.png)

6.  In questo caso, puoi vedere che l**'**ambiente **Dev One** è già
    selezionato. Nel caso, se viene visualizzato l'elenco degli
    ambienti, scegli il suoi ambiente - **Dev One** e seleziona di nuovo
    **Login**.

> ![](./media/image13.png)

7.  Verrà visualizzato un elenco di plug-ins di sistema. Se
    nell'ambiente sono presenti plug-in personalizzati, nell'elenco
    verranno visualizzati anche questi. Gli assembly sono .NETDLLs che
    implementano i plug-ins.

> **Nota:** è necessario espandere la sezione per visualizzare l'elenco
> completo.
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image14.png)

8.  Individua **Microsoft.CDS.DataLakeDataProvider. Plugins** ed
    espandilo.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image15.png)

9.  Ognuno degli elementi figlio viene implementato nell'assembly.
    Espandere uno degli elementi per visualizzare le registrazioni dei
    passaggi per il singolo plug-in.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image16.png)

10. La registrazione del passaggio connette il plug-in come gestore
    eventi all'evento. Nell'esempio precedente, si tratta della gestione
    di una creazione nella tabella insightsstorevirtualentity.

> ![](./media/image17.png)

11. Fare doppio clic su qualsiasi passaggio per visualizzare i dettagli
    di configurazione del passaggio, incluso il messaggio e l'entità in
    cui è registrato, la fase della pipeline in cui verrà richiamato il
    plug-in, se l'esecuzione è sincrona o asincrona, ecc.

> ![](./media/image18.png)

**Riepilogo:** in questo laboratorio hai imparato a installare gli
strumenti di sviluppo. Quando si crea un plug-in personalizzato, si
utilizzerà lo strumento di registrazione dei plug-in per caricare l'
assembly e registrare i passaggi per gli eventi che si desidera gestire.
