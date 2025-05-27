**Lab 5: Creare un'API personalizzata**

**Durata stimata:** 35 min

**Obiettivo:** In questo laboratorio imparerai a creare un'API
personalizzata Common Data Service per eseguire una logica
personalizzata. Utilizzerai quindi l'API personalizzata da un passaggio
in un flusso di Power Automate.

**Attività 1: Creare il progetto API personalizzato**

1.  Fare clic sul menu **Start** della VM, digitare Prompt dei comandi
    nella casella di ricerca e quindi selezionare **Open**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image1.png)

2.  Eseguire il comando seguente per creare una nuova cartella
    denominata **CustomAPILab**.

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  Cambia directory nella cartella che hai creato.

> +++cd CustomAPILab+++
>
> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image3.png)

4.  A questo punto dovrebbe trovarsi nella cartella CustomAPIlAB. Esegui
    il comando seguente per inizializzare una nuova libreria di classi
    del plug-in Common Data Service.

> +++pac plugin init+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image4.png)

5.  La creazione della libreria di classi del plug-in Common Data
    Service dovrebbe essere riuscita.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image5.png)

6.  Eseguire il comando seguente per aprire il progetto in Visual
    Studio.

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  Se richiesto, selezionare **Microsoft Visual Studio 2022** e quindi
    selezionare **Just once**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image7.png)

8.  Se viene richiesto di accedere a Visual Studio, selezionare **Skip
    this for now** nella pagina di accesso.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image8.png)

9.  Selezionare **General** come Impostazioni di sviluppo, scegliere
    **Dark** come tema colore e quindi selezionare **Start** **Visual
    Studio**.

> **Nota:** Ignorare questo passaggio se si accede direttamente al
> progetto.
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image9.png)

10. Il progetto deve essere aperto in Visual Studio.

> ![](./media/image10.png)

11. Fare clic con il pulsante destro del mouse sul file Plugin1.cs e
    rinominarlo **MatchPlugin.cs**.

> ![](./media/image11.png)

12. Selezionare **Yes** per rinominare una finestra di dialogo di file.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image12.png)

13. Fare clic con il pulsante destro del mouse sul progetto CustomAPILab
    e scegliere **Manage NuGet Packages**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image13.png)

14. Cerca **System.Text.RegularExpressions** e seleziona **Install**.

> ![](./media/image14.png)

15. Nella finestra Anteprima modifiche, selezionare **Apply** per
    consentire a Visual Studio di apportare modifiche alla soluzione.

> ![](./media/image15.png)

16. Selezionare **I Accept** per accettare le condizioni di licenza.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image16.png)

17. Apri il file **MatchPlugin.cs**.

> ![](./media/image17.png)

18. Aggiungere la seguente istruzione sotto l'istruzione **'using
    System**;', ad esempio sulla riga n. 3.

> +++using System.Text.RegularExpressions;+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image18.png)

19. Aggiungi le righe seguenti all'interno del metodo
    ExecuteDataversePlugin e dopo la riga del contesto var. Queste righe
    ottengono il valore dai parametri di input passati alla chiamata API
    personalizzata.

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. Aggiungere la riga seguente dopo per ottenere il servizio di
    tracciamento.

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image20.png)

21. Aggiungere la riga seguente per scrivere il valore di input nella
    traccia.

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. Aggiungere la riga seguente dopo per chiamare il metodo Regex.Match.

> var result = Regex.Match(input, pattern);
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image22.png)

23. Scrivi il risultato per tracciare.

> tracingService.Trace("Matching result: " + result.Success);
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image23.png)

24. Infine, aggiungi la seguente riga per impostare il parametro di
    output Matched.

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image24.png)

25. Il metodo di esecuzione dovrebbe ora essere simile al seguente.

> ![Schermata di un programma per computer Descrizione generata
> automaticamente](./media/image25.png)

26. Seleziona **Build | Build Solution**.

> ![](./media/image26.png)

27. Il progetto dovrebbe essere compilato correttamente.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image27.png)

**Attività 2: Registrare il plug-in API personalizzato**

1.  Apri il prompt dei comandi ed esegui il comando seguente per avviare
    lo strumento di registrazione del plug-in.

> +++pac tool prt+++
>
> ![Una schermata nera con testo bianco Descrizione generata
> automaticamente](./media/image28.png)

2.  Selezionare **+ Create New Connection**.

> ![](./media/image29.png)

3.  Seleziona **Office 365**, fornisci le tue credenziali e seleziona
    **Login**.

> ![Uno screenshot di una casella di accesso Descrizione generata
> automaticamente](./media/image30.png)

4.  Accedere con **M365 Admin tenant Id** e quindi selezionare **Next**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image31.png)

5.  Immettere la **M365 Admin tenant Id’s password,** quindi selezionare
    **Sign in**.

> ![Uno screenshot di una casella di accesso Descrizione generata
> automaticamente](./media/image32.png)

6.  Verificare che l'ambiente **Dev One** sia selezionato.

7.  Scegli **Register| Register New Assembly**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image33.png)

8.  Selezionare... nel passaggio 1 e quindi passare alla cartella
    **CustomAPILab\bin\Debug\net462**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image34.png)

9.  Seleziona **CustomAPILab.dll** quindi seleziona **Open**.

> ![](./media/image35.png)

10. Seleziona **Register Selected Plugins**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image36.png)

11. Selezionare **OK** per il messaggio di esito positivo. Il suoi
    plugin è pronto per connettersi all'API personalizzata che creeremo
    nella prossima attività.

> ![Uno screenshot di un errore del computer Descrizione generata
> automaticamente](./media/image37.png)

**Attività 3: Creare l'API personalizzata**

1.  Passa al portale per sviluppatori di Power Apps utilizzando
    +++<https://make.powerapps.com/>+++ e assicurati di essere nell'
    ambiente **Dev One**.

2.  Seleziona **Solutions** nel riquadro di spostamento a sinistra.
    Selezionare **+ New solution**.

> ![](./media/image38.png)

3.  Inserisci +++**Custom API Lab**+++ nel nome visualizzato.

4.  Selezionare **CDS Default Publisher** nell'elenco a discesa Editore.

5.  Seleziona **Create**. In questo modo viene creata una soluzione
    personalizzata che conterrà i componenti.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image39.png)

6.  Seleziona **+ New | More | Other | Custom API.**

> ![](./media/image40.png)

7.  Inserisci le seguenti informazioni:

    - **Unique Name:** +++contoso_match+++

    &nbsp;

    - **Name**: +++Match+++

    &nbsp;

    - **Display Name :** +++Match+++

    &nbsp;

    - **Description**: +++Match a string+++

    &nbsp;

    - **Binding Type**: +++Global+++

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image41.png)

8.  In Tipo di plug-in selezionare l'icona di ricerca e individuare il
    plug-in**: CustomAPILab.MatchPlugin**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image41.png)

9.  Seleziona **Save and Close**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image42.png)

10. Seleziona **Done**.

> ![Uno screenshot di un sito web Descrizione generata
> automaticamente](./media/image43.png)

11. Seleziona **+ New | More | Other | Custom API Request Parameter**.

> ![](./media/image44.png)

12. Per **Custom** **API**, seleziona l'icona **Search** e seleziona
    **Match** (la tua API personalizzata).

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image45.png)

13. Immettere +++**StringIn**+++ per Nome univoco, Nome, Nome
    visualizzato e Descrizione per semplicità.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image46.png)

14. Selezionare **String** per Tipo.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image47.png)

15. Seleziona **Save and Close**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image48.png)

16. Seleziona **Done**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image49.png)

17. Per aggiungere un altro, Parametro di richiesta API personalizzato,
    selezionare **+ New | More | Other | Custom API Request Parameter**.

> ![](./media/image50.png)

18. Per **Custom API**, seleziona l'icona **Search** e seleziona
    **Match** (la tua API personalizzata).

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image51.png)

19. Immettere **Pattern** per Nome univoco, Nome, Nome visualizzato e
    Descrizione per semplicità.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image52.png)

20. Selezionare **String** per Tipo.

> ![Screenshot di una stringa Descrizione generata
> automaticamente](./media/image53.png)

21. Seleziona **Save and Close**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image54.png)

22. Seleziona **Done**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image55.png)

23. Seleziona **New | More | Other | Custom API Response Property**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image56.png)

24. Per **Custom API**, seleziona l'icona **Search** e seleziona
    **Match** (la tua API personalizzata).

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image57.png)

25. Immettere +++**Matched**+++ per **Unique Name**, **Name, Display
    Name** e **Description** per semplicità.

26. Selezionare **Boolean** per **Type**.

> ![](./media/image58.png)

27. Seleziona **Save and Close.**

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image59.png)

28. Seleziona **Done**.

> ![Uno screenshot di un testo bianco Descrizione generata
> automaticamente](./media/image60.png)

29. L'elenco dei componenti della soluzione dovrebbe essere simile al
    seguente.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image61.png)

**Attività 4: Utilizzare l'API personalizzata di Power Automate**

1.  Nella soluzione, seleziona **+ New | Automation | Cloud Flow |
    Instant**.

> ![](./media/image62.png)

2.  Immetti +++**String match**+++ per Nome flusso, seleziona **Manually
    trigger a flow** e seleziona **Create**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image63.png)

3.  Seleziona il **+New Step**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image64.png)

4.  Cerca perform (esegui) e scegli **Perform an unbound action** ![Uno
    screenshot di un computer Descrizione generata
    automaticamente](./media/image65.png)

5.  Nell'elenco Nome azione individuare e selezionare **contoso_match**.

> ![](./media/image66.png)

6.  Inserisci **myemail@outlook.com** indirizzo e-mail in **StringIn**.
    Qui puoi digitare qualsiasi indirizzo e-mail semplice valido.

> ![](./media/image67.png)

7.  Immettere la seguente espressione regolare in Pattern. Questo è un
    semplice modello di email. Sono disponibili altri examples.

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image68.png)

8.  Il flusso dovrebbe essere simile al seguente.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image69.png)

9.  Seleziona **Save**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image70.png)

10. Al termine del salvataggio, selezionare **Test**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image71.png)

11. Seleziona **Manually**, quindi seleziona **Test**.

> ![Uno screenshot di un telefono Descrizione generata
> automaticamente](./media/image72.png)

12. Seleziona **Run flow**.

> ![Uno sfondo bianco con punti neri Descrizione generata
> automaticamente](./media/image73.png)

13. Seleziona **Done**.

> ![Uno screenshot di un telefono Descrizione generata
> automaticamente](./media/image74.png)

14. Al termine del flusso, seleziona l'opzione **Perform an unbound
    action** per espandere e visualizzare i risultati.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image75.png)
>
> ![Screenshot che mostra i risultati dell'esecuzione del
> flusso.](./media/image76.png)

**Riepilogo:** in questo lab hai appreso come creare un'azione
personalizzata e usarla da un flusso di Power Automate. L'contoso_match
di azione API personalizzata è ora disponibile anche per le chiamate
dirette utilizzando l'API della piattaforma.
