# **Lab 2: Utilizzare l'interfaccia della riga di comando di Power Apps e creare Power Apps Component Framework (PCF)** 

**Durata stimata:** 30 min

**Obiettivo:** In questo laboratorio imparerai a installare gli
strumenti di Power Platform e a creare il suoi primo componente Power
Apps Component Framework (PCF).

## **Attività 1: Installare gli strumenti di Power Platform**

1.  Aprire Visual Studio Code utilizzando il collegamento presente sul
    desktop della macchina virtuale, selezionare l'icona **Extensions**
    nella barra di spostamento.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image1.png)

2.  Cerca +++**power platform tools**+++. Seleziona il pulsante
    **Install** nei risultati della ricerca.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image2.png)

3.  Attendere il completamento dell'installazione.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image3.png)

4.  Selezionare **more option(...), Terminal** e quindi selezionare
    **New terminal**.

> **Nota:** se non vedi (... 3 punti), seleziona **hamburger | Terminal
> | New Terminal.**
>
> ![](./media/image4.png)
>
> ![](./media/image5.png)

5.  Esegui il comando pac per vedere quali comandi sono disponibili:

> +++pac+++
>
> ![Una schermata nera con testo bianco e un rettangolo rosso con testo
> giallo e nero Descrizione generata
> automaticamente](./media/image6.png)
>
> ![](./media/image7.png)
>
> ![Screenshot che mostra un elenco di comandi.](./media/image8.png)

6.  Puoi inserire pac e poi un comando per vedere quali opzioni ha, ad
    esempio, prova quanto segue:

> +++pac admin+++
>
> ![](./media/image9.png)
>
> **Nota:** se viene visualizzato il popup che dice " Some keybindings
> don’t got to the terminal by default and are handled by Visual Studio
> Code instead ", seleziona **Configure Terminal Settings**.
>
> ![Uno sfondo nero con testo bianco Descrizione generata
> automaticamente](./media/image10.png)

7.  Puoi vedere quali opzioni ha l'amministratore.

> ![](./media/image11.png)

8.  Passa al portale di Power Apps Maker utilizzando
    <https://make.powerapps.com/> e assicurati di aver selezionato l'
    ambiente **Dev One**.

9.  Nell'angolo in alto a destra dello schermo, seleziona l'icona
    **Settings** e scegli **Session details**.

> ![](./media/image12.png)

10. Nella finestra di dialogo dei dettagli della sessione di Power Apps,
    seleziona Valore **Instance URL** e copialo per utilizzarlo più
    avanti nell'esercizio.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image13.png)

11. Tornare al terminale di Visual Studio Code, digitare il comando
    seguente per stabilire una connessione dall'interfaccia della riga
    di comando e accedere all'ambiente di test quando richiesto.

> +++pac auth create --name Lab --url **\<Your Instance URL\>+++**
>
> ![](./media/image14.png)

12. Accedere con le credenziali di amministratore di M365.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image15.png)

13. Inserisci la **password** e clicca su **Sign in**.

> ![Uno screenshot di una pagina di accesso Descrizione generata
> automaticamente](./media/image16.png)

14. È possibile visualizzare il messaggio che l'autenticazione è stata
    eseguita correttamente.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image17.png)

15. Digita il seguente comando who che visualizzerà l'ambiente e le
    informazioni sull'utente. Questo è utile per assicurarsi di trovarsi
    nell'ambiente corretto.

> +++pac org who+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image18.png)

## **Attività 2: Creare un componente PCF**

1.  Esegui il comando seguente per creare una nuova cartella denominata
    **labPCF** all'interno della cartella dell'utente.

> +++md labPCF+++
>
> ![](./media/image19.png)

2.  Puoi vedere che la cartella labPCF è stata creata.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image20.png)

3.  Cambia directory nella cartella che hai creato.

> +++cd labPCF+++
>
> ![Un'immagine in bianco e nero della mano di una persona Descrizione
> generata automaticamente](./media/image21.png)

4.  Eseguire il comando seguente per inizializzare il progetto del
    componente.

> +++pac pcf init --namespace lab --name FirstControl --template
> field+++
>
> ![Schermata di un computer Descrizione generata
> automaticamente](./media/image22.png)

5.  Digita il seguente comando e quindi premi invio. In questo modo
    vengono rimosse tutte le dipendenze dal repository npm.

> +++npm install+++
>
> ![](./media/image23.png)

6.  Se ti viene chiesto di aggiornare npm, utilizza il comando fornito
    come mostrato nell'immagine seguente. In questo caso, viene
    utilizzato npm install -g npm@10.8.2.

> ![](./media/image24.png)

7.  Aprire la cartella in Visual Studio Code utilizzando il comando
    seguente.

> +++code .+++

8.  Se ti imbatti in un pop-up che dice. Ti fidi degli autori del file,
    quindi fai clic su **Yes, I thrust the authors**.

> ![](./media/image25.png)

9.  Se ti viene chiesto di scegliere il tema del colore, fai clic su
    **Browse Color** **Themes** altrimenti, ignora questo e il passaggio
    successivo.

> ![](./media/image26.png)

10. Seleziona il tema colore **Dark Modern.**

> ![](./media/image27.png)

11. Esplora i file che sono stati creati.

12. Espandere la cartella **FirstControl** e selezionare **Index.ts**.

> ![](./media/image28.png)
>
> **Nota:** nella finestra pop-up che chiede "Vuoi consentire file non
> attendibili in questa finestra", seleziona **Allow**.
>
> ![Uno screenshot di un errore del computer Descrizione generata
> automaticamente](./media/image29.png)

13. Incolla le seguenti due variabili all'interno dell'esportazione.

> ![Schermata di un computer Descrizione generata
> automaticamente](./media/image30.png)

14. Incolla quanto segue all'interno della funzione **init()** per
    creare i controlli HTML e impostare il valore dell'etichetta.

> this.label = document.createElement("input");
>
> this.label.setAttribute("type", "label");
>
> this.label.value = "My First PCF";
>
> this.\_container = document.createElement("div");
>
> this.\_container.appendChild(this.label);
>
> container.appendChild(this.\_container);
>
> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image31.png)

15. Per salvare il file, vai alla scheda **File** e seleziona **Save**.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image32.png)

16. Vai al terminale e inserisci il seguente comando, quindi invio.
    Verrà avviato il test harness con il codice più recente, come
    illustrato nello screenshot thisrd di questo passaggio.

> +++npm start+++
>
> ![](./media/image33.png)
>
> **Nota:** se ricevi un messaggio quando **Windows Defender Firewall
> has blocked some features of this app**, seleziona **Allow access.**
>
> ![Screenshot di un avviso di sicurezza del computer Descrizione
> generata automaticamente](./media/image34.png)
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image35.png)

17. Il test harness è efficace da usare nelle prime fasi del progetto
    per vedere l'aspetto visivo del controllo senza doverlo distribuire
    in un ambiente. È possibile impostare i valori della proprietà per
    modificare le dimensioni dell'area di controllo. Al termine
    dell'esplorazione del test harness, tornare al terminale e premere
    CTRL-C per terminare l'esecuzione del test harness.

> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image36.png)

18. Digitare **Y** e \[ENTER\].

> ![](./media/image37.png)

19. Eseguire il comando seguente per elencare le soluzioni
    nell'ambiente.

> +++pac solution list+++
>
> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image38.png)

20. Queste sono le soluzioni correnti presenti nell'ambiente. Il
    passaggio successivo ne aggiungerà uno per il componente.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image38.png)

21. Digita il seguente comando push per eseguire il push del controllo
    nell'ambiente.

> +++pac pcf push --publisher-prefix lab+++
>
> ![Uno screenshot di un programma per computer Descrizione generata
> automaticamente](./media/image39.png)

## **Attività 3: Utilizzare il componente in un'app** 

1.  Passa all'interfaccia di amministrazione di Microsoft Power Platform
    utilizzando +++<https://admin.powerplatform.microsoft.com/home>+++.

2.  Chiudere la finestra di benvenuto.

> ![](./media/image40.png)

3.  Selezionare l'ambiente **Dev One** che si sta utilizzando per il
    lab.

> ![](./media/image41.png)

4.  Seleziona **Settings**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image42.png)

5.  Espandere l**'**area **Product** e selezionare **Features**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image43.png)

6.  Sul lato destro, abilita la funzionalità **Allow publishing of
    canvas apps with code components**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image44.png)

7.  Seleziona **Save** in basso.

> ![](./media/image45.png)

8.  Passa al [portale di Power Apps Maker](https://make.powerapps.com/)
    utilizzando +++<https://make.powerapps.com/>+++ e assicurati di
    trovarti nell'ambiente corretto, ad esempio **Dev One**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image46.png)

9.  Selezionare **Solutions** nel riquadro di spostamento a sinistra,
    quindi selezionare **Import solution**.

> ![](./media/image47.png)

10. Selezionare **Browse** nella finestra di dialogo **Import a
    solution.**

> ![Uno sfondo bianco con testo nero Descrizione generata
> automaticamente](./media/image48.png)

11. Selezionare il file zip della soluzione dal percorso:
    labPCF\obj\PowerAppsToolsTemp_lab\bin\Debug e quindi selezionare
    **Open**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image49.png)

12. Dopo aver importato il file zip, fare clic su **Next**.

> ![](./media/image50.png)

13. Seleziona **Import**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image51.png)

14. Attendere fino a quando non viene visualizzato il messaggio che
    indica la Solution "**PowerAppsToolsTemp_lab**" importata
    correttamente.

> ![](./media/image52.png)

15. Fare doppio clic sulla soluzione appena importata -
    **PowerAppsTools_lab** per aprirla.

> ![](./media/image53.png)

16. Dovresti vedere il suoi componente elencato.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image54.png)

17. Seleziona **+ New | App | Canvas app**.

> ![](./media/image55.png)

18. Selezionare **Phone** per Formato, immettere **First PCF** per Nome
    app e selezionare **Create**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image56.png)

19. Seleziona **Skip** nella finestra di benvenuto.

> ![](./media/image57.png)

20. Nel riquadro sinistro selezionare **Add (+)** e quindi selezionare
    l'icona **Get more components** situata sopra l'elenco dei
    componenti più popolari e sotto la casella di ricerca, come
    illustrato nell'immagine seguente.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image58.png)

21. Seleziona la scheda **Code**.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image59.png)

22. Seleziona il suoi componente – **FirstControl**. Seleziona
    **Import**.

> ![](./media/image59.png)

23. Sulla barra degli strumenti a sinistra, seleziona **+** ed espandi
    **Code components**.

> ![](./media/image60.png)

24. Selezionare **FirstControl**. A questo punto dovrebbe essere
    visualizzato il controllo con il testo **My First PCF** nell'area di
    disegno.

> ![](./media/image61.png)

25. Selezionare **Save** per salvare l'applicazione.

> ![Uno screenshot di un computer Descrizione generata
> automaticamente](./media/image62.png)

A questo punto è stato creato il primo componente PCF e lo si è usato in
un'app canvas.

**Riepilogo:** in questo lab hai appreso come creare il suoi primo
componente PCF e usarlo in un'app canvas. Il framework dei componenti
Power Apps crea componenti di codice per app basate su modello e canvas.
Questi componenti di codice possono essere usati per migliorare
l'esperienza utente per gli utenti che lavorano con i data su moduli,
visualizzazioni, dashboard e schermate dell'app canvas.
