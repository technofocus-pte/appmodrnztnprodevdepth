**Lab 6 - Scrivi il suoi primo plug-in**

**Durata stimata:** 30 min

**Obiettivo:** In questo scenario, un'organizzazione deve assicurarsi
che i data del numero di telefono vengano immessi in un formato
coerente. Per raggiungere questo obiettivo, creerai un plug-in da
eseguire durante la creazione/aggiornamento che elimina tutti i
caratteri non numerici da un numero di telefono prima di salvarlo in
Common Data Service.

In questa esercitazione verrà illustrato come creare un plug-in che
verrà eseguito durante la creazione e l'aggiornamento. Questo plug-in
eliminerà tutti i caratteri non numerici da un numero di telefono.

**Attività 1: Creare una nuova soluzione e un'app basata su modello**

1.  Passa a [Power Apps](https://make.powerapps.com/) usando
    +++<https://make.powerapps.com/>+++. Assicurati di essere nell'
    ambiente **Dev One**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image1.png)

2.  Nel riquadro di spostamento a sinistra selezionare **Solutions** e
    quindi selezionare **New solution**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image2.png)

3.  Nella finestra di dialogo a comparsa, specifica **Display name** –
    +++Plugin Lab+++, **Name** – +++PluginLab+++, **Publisher** – CDS
    Default publisher e quindi seleziona **Create**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image3.png)

4.  Per creare una nuova app basata su modello nella soluzione,
    selezionare **New** | **App** | **Model-driven** **app**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image4.png)

5.  Assegna il **Name** alla tua app basata su modello come
    +++**Fundraiser**+++ e quindi seleziona **Create**.

> ![](./media/image5.png)

6.  Nell'app basata su modello selezionare **+Add page**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image6.png)

7.  Seleziona **Dataverse table** nella finestra popup visualizzata.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image7.png)

8.  Seleziona Tabella **contact**, quindi seleziona **Add**.

> ![](./media/image8.png)
>
> **Nota:** Per questo lab, stiamo utilizzando la tabella dei contatti.

9.  Ora, la tua app basata su modello denominata "**Fundraiser**" è
    pronta.

> ![](./media/image9.png)

10. Seleziona **Save** nell'angolo in alto a destra.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image10.png)

11. Seleziona **Publish**.

> ![Un rettangolo viola e bianco Descrizione generata
> automaticamente](./media/image11.png)

12. Fare clic sulla **back arrow** per tornare alla soluzione.

> ![Uno screenshot di un browser Descrizione generata
> automaticamente](./media/image12.png)

13. Fai clic sulla **back arrow** e sarai sulla pagina della soluzione
    in cui sono elencate tutte le soluzioni.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image13.png)

**Attività 2: Creare un plug-in**

1.  Avviare **Visual Studio 2022**. Per aprirlo, fai clic sul menu Start
    della VM, digita Visual Studio nella casella di ricerca e seleziona
    **Open**.

> ![](./media/image14.png)

2.  Seleziona **File | New | Project**.

> ![](./media/image15.png)

3.  Selezionare **Class Library(.NET Framework)** e selezionare
    **Next**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image16.png)

4.  Immettere **D365PackageProject** per **Project Name**, selezionare
    una posizione in cui salvare il progetto,

> ![](./media/image17.png)

5.  selezionare **.NET Framework 4.7.1** per **Framework** e quindi
    selezionare **Create**.

> ![](./media/image18.png)

6.  Fare clic con il pulsante destro del mouse sul progetto e scegliere
    **Manage NuGet Packages**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image19.png)

7.  Selezionare la scheda **Browse**, cercare e selezionare
    **microsoft.crmsdk.coreassemblies**, quindi selezionare **Install**.

> ![](./media/image20.png)

8.  Nella finestra Anteprima modifiche selezionare **Apply** per
    consentire a Visual Studio di apportare modifiche alla soluzione.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image21.png)

9.  Selezionare **I Accept** per accettare le condizioni di licenza.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image22.png)

10. Chiudere Gestione pacchetti NuGet.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image23.png)

11. Fare clic con il pulsante destro del mouse su **Class1.cs** ed
    **Delete**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image24.png)

12. Selezionare **OK** per eliminare Class1.cs definitivamente.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image25.png)

13. Fare clic con il pulsante destro del mouse sul progetto e quindi
    selezionare **Add | Class**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image26.png)

14. Assegnare alla nuova classe il nome
    **PreOperationFormatPhoneCreateUpdate** e selezionare **Add**.

> ![](./media/image27.png)

15. Aggiungere le istruzioni using alla nuova classe come indicato di
    seguito:

> using Microsoft.Xrm.Sdk;
>
> using System.Text.RegularExpressions;
>
> ![](./media/image28.png)

16. Per rendere **public** la classe, sostituire l'interno con pubblico
    e digitare**: IPlugin** alla fine del passaggio per aggiungere
    l'interfaccia IPlugin come mostrato nell'immagine seguente.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image29.png)

17. Passa il mouse sull'interfaccia IPlugin, fai clic sull'icona di
    azione rapida che appare e quindi seleziona **Implement interface**.

> ![](./media/image30.png)
>
> La tua classe dovrebbe ora assomigliare all'immagine seguente.
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image31.png)

**Attività 3: Formattare un numero di telefono**

1.  Ottenere il contesto di esecuzione dal provider di servizi.
    Sostituire l'eccezione nel metodo Execute con il frammento di codice
    seguente.

> IPluginExecutionContext context =
>
> (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
>
> ![](./media/image32.png)

2.  Controllare il parametro di input per Target. Aggiungere il
    frammento di codice seguente al metodo Execute.

> if (!context. InputParameters.ContainsKey("Target"))
>
> throw new InvalidPluginExecutionException("No target found");
>
> ![](./media/image33.png)

3.  Aggiungere il frammento di codice seguente al metodo Execute. Questo
    frammento di codice otterrà l'entità di destinazione dal parametro
    di input e quindi verificherà se i relativi attributi contengono
    telephone1 (Telefono aziendale per i contatti, Telefono per gli
    account).

> Var entity= context.InputParameters\["Target"\] as Entity;
>
> if (!entity. Attributes.Contains("telephone1"))
>
> return;
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image34.png)

4.  Aggiungere il frammento di codice seguente alla funzione Execute.
    Questo frammento di codice rimuoverà tutti i caratteri non numerici
    dal numero di telefono fornito dall'utente.

> string phoneNumber = (string)entity\["telephone1"\];
>
> var formattedNumber = Regex.Replace(phoneNumber, @"\[^\d\]", "");
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image35.png)

5.  Impostare telephone1 sul numero di telefono formattato. Aggiungere
    il frammento di codice seguente al metodo Execute.

> entity\["telephone1"\] = formattedNumber;
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image36.png)
>
> Il metodo Execute dovrebbe ora essere simile all'immagine seguente.
>
> ![Screenshot del metodo execute.](./media/image37.png)

6.  Fare clic con il pulsante destro del mouse sul progetto e scegliere
    **Properties**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image38.png)

7.  Seleziona la scheda **Signing** e seleziona \<**New... \>** file
    chiave.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image39.png)

8.  Immettere +++**contoso.snk**+++ nel campo **Key file name**,
    deselezionare la casella di **Protect my key file with a password**
    e quindi selezionare **OK**.

> ![](./media/image40.png)

9.  Chiudere la scheda **Properties**.

> ![](./media/image41.png)

10. Seleziona la scheda **Build** e fai clic su **Build Project.**

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image42.png)

11. Assicurarsi che la compilazione abbia esito positivo.

> ![Uno screenshot di un videogioco Descrizione generata
> automaticamente](./media/image43.png)

**Attività 4: Registrare un plug-in e procedura**

1.  Vai al menu **Start** della VM, digita plug-in registration tool
    nella casella di ricerca e fai clic su **Open**.

> ![](./media/image44.png)

2.  Seleziona **Create New connection**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image45.png)

3.  Selezionare **Office 365,** selezionare la casella di **Show
    Advanced**, nel campo Area online selezionare **Don’t Know**,
    specificare le credenziali (tenant amministratore M365) e quindi
    selezionare **Login**.

> ![](./media/image46.png)

4.  Selezionare **Register,** quindi **Register New Assembly**.

> ![](./media/image47.png)

5.  Seleziona **...** nel passaggio 1 e quindi vai al **Bin | Debug**
    Cartella della libreria di classi creata.

> ![Uno sfondo bianco con testo nero Descrizione generata
> automaticamente](./media/image48.png)

6.  Seleziona **D365PackageProject.dll**, quindi seleziona **Open**.

> ![](./media/image49.png)

7.  Seleziona **Register Selected Plugins**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image50.png)

8.  Selezionare **OK.**

> ![](./media/image51.png)

9.  Espandere l'assembly appena registrato: **(Assembly)
    D365PackageProject**.

> ![](./media/image52.png)

10. Fare clic con il pulsante destro del mouse sul plug-in e selezionare
    **Register New Step**.

> ![](./media/image53.png)

11. Seleziona **Create** per **Message** e seleziona **Contact** per
    **Primary Entity**.

> ![](./media/image54.png)

12. Selezionare **PreOperation** per **Event Pipeline Stage of
    Execution**, quindi selezionare **Register New Step**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image55.png)

13. Selezionare **Close** nella pagina Avviso che indica che non sono
    stati rilevati filtri sugli attributi.

> ![](./media/image56.png)

14. Se viene visualizzato il messaggio di errore, ad esempio si è
    verificato un errore durante la registrazione del passaggio,
    selezionare **No** per visualizzare i dettagli.

> ![Uno screenshot di un errore del computer Descrizione generata
> automaticamente](./media/image57.png)

15. Verifica che il passaggio di creazione sia stato creato nel plug-in.

> ![Una linea rossa con testo nero Descrizione generata
> automaticamente](./media/image58.png)

16. Fare clic con il pulsante destro del mouse sul plug-in e selezionare
    nuovamente **Register New Step**.

> ![](./media/image59.png)

17. Seleziona **Update** per **Message**, seleziona **Contact** per
    **Primary Entity**, quindi seleziona la ricerca **Attributes**.

> ![](./media/image60.png)

18. Deselezionare la casella di controllo **Select All**, selezionare la
    casella di controllo **Business Phone** e quindi selezionare **OK**.

> ![](./media/image61.png)

19. Selezionare **PreOperation** per **Event Pipeline Stage of
    Execution**, quindi selezionare **Register New Step**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image62.png)

20. Se viene visualizzato il messaggio di errore, ad esempio **Error
    occured while registering the step**, selezionare **No** per
    visualizzare i dettagli.

> ![Uno screenshot di un errore del computer Descrizione generata
> automaticamente](./media/image57.png)

21. Verifica che il passaggio di creazione sia stato creato nel plug-in.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image63.png)

**Attività 5: Testare il plug-in**

1.  Vai al suoi Maker Portal +++<https://make.powerapps.com/>+++ e
    assicurati di essere nell'ambiente **Dev One** selezionato.

2.  Seleziona **Apps** e avvia l' applicazione **Fundraiser**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image64.png)

3.  Seleziona **+ New**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image65.png)

4.  Immettere +++**Test**+++ per **First** **Name**, +++**Contact**+++
    per **Last Name**, +++**(123)-555-0100+++** per **Business Phone**,
    quindi selezionare **Save**.

> ![Uno screenshot di un modulo di contatto Descrizione generata
> automaticamente](./media/image66.png)
>
> Il record deve essere salvato e il **Business Phone** deve mostrare
> solo i valori numerici.
>
> ![](./media/image67.png)

5.  Cambia il **Business phone** in **001-123-555-0100** e fai clic su
    **Save**. Il record deve essere aggiornato e il **Business Phone**
    deve mostrare solo i valori numerici.

> ![Uno screenshot di un modulo di contatto Descrizione generata
> automaticamente](./media/image68.png)

**Riepilogo:** in questa esercitazione si è appreso come creare un
plug-in che verrà eseguito durante la creazione e l'aggiornamento e come
eliminare tutti i caratteri non numerici da un numero di telefono
utilizzando questo plug-in.
