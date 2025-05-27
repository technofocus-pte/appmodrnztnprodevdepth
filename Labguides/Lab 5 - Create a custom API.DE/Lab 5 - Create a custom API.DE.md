**Lab 5: Erstellen einer benutzerdefinierten API**

**Geschätzte Dauer:** 35 Minuten

**Ziele:** In diesem Lab werden Sie lernen, eine benutzerdefinierte
Dataverse-API zu erstellen, um eine benutzerdefinierte Logik
auszuführen. Anschließend werden Sie die benutzerdefinierte API von
einem Schritt in einem Power Automate-Ablauf aus verwenden.

**Aufgabe 1: Erstellen des benutzerdefinierten API-Projekts**

1.  Klicken Sie auf das **Start** menü der VM, geben Sie Command Prompt
    in das Suchfeld ein und wählen Sie dann **Open** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Führen Sie den folgenden Befehl aus, um einen neuen Ordner mit dem
    Namen **CustomAPILab** zu erstellen.

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  Wechseln Sie das Verzeichnis in den erstellten Ordner.

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  Sie sollten sich jetzt im Ordner CustomAPIlAB befinden. Führen Sie
    den folgenden Befehl aus, um eine neue Dataverse plugin class
    library zu initialisieren.

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Die Erstellung von Dataverse plugin class library sollte erfolgreich
    sein.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Führen Sie den folgenden Befehl aus, um das Projekt in Visual Studio
    zu öffnen.

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  Wenn Sie dazu aufgefordert werden, wählen Sie **Microsoft Visual
    Studio 2022** und wählen Sie dann **Just once**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  Wenn Sie aufgefordert werden, sich bei Visual Studio anzumelden,
    wählen Sie auf der Anmeldeseite **Skip this for now** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  Wählen Sie **General** als Development settings, wählen Sie **Dark**
    als color theme und wählen Sie dann **Start Visual Studio** aus.

> **Notiz:** Ignorieren Sie diesen Schritt, wenn Sie direkt zum Projekt
> navigiert werden.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. Das Projekt sollte in Visual Studio geöffnet werden.

> ![](./media/image10.png)

11. Klicken Sie mit der rechten Maustaste auf die Datei Plugin1.cs und
    benennen Sie sie als **MatchPlugin.cs** um.

> ![](./media/image11.png)

12. Wählen Sie „**Yes**“ für den Dialog you're renaming a file.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Klicken Sie mit der rechten Maustaste auf das CustomAPILab-Projekt
    und wählen Sie **Manage NuGet Packages** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. Suchen Sie nach **System.Text.RegularExpressions** und wählen Sie
    **Install**.

> ![](./media/image14.png)

15. Wählen Sie im Fenster Preview changes, die Option „**Apply**“ aus,
    um Visual Studio das Vornehmen von Änderungen an der Lösung zu
    gestatten.

> ![](./media/image15.png)

16. Wählen Sie **I Accept**, um die Lizenzbedingungen zu akzeptieren.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17. Öffnen Sie die Datei **MatchPlugin.cs**.

> ![](./media/image17.png)

18. Fügen Sie die folgende Anweisung unter der Anweisung „using System;“
    hinzu, d. h. in Zeile 3.

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. Fügen Sie die folgenden Zeilen innerhalb
    ExecuteDataversePlugin-Methode und nach var context line hinzu.
    Diese Zeilen rufen den Wert aus input parameters ab, die beim Aufruf
    der benutzerdefinierten API übergeben wurden.

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. Fügen Sie die folgende Zeile hinzu, um tracing service abzurufen.

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. Fügen Sie die folgende Zeile hinzu, um input value in trace zu
    schreiben.

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. Fügen Sie die folgende Zeile hinzu, um die Methode Regex.Match
    aufzurufen.

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. Schreiben Sie das Ergebnis in trace.

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. Und schließlich fügen Sie die folgende Zeile hinzu, um den output
    parameter Matched festzulegen.

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. Ihre Execute-Methode sollte jetzt wie folgt aussehen.

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. Wählen Sie **Build | Build Solution** aus.

> ![](./media/image26.png)

27. Das Projekt sollte erfolgreich erstellt werden.

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**Aufgabe 2: Registrieren des benutzerdefinierten API-Plugins**

1.  Öffnen Sie die Eingabeaufforderung und führen Sie den folgenden
    Befehl aus, um das Plugin Registration Tool zu starten.

+++pac tool prt+++

> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  Wählen Sie **+ Create New Connection**.

> ![](./media/image29.png)

3.  Wählen Sie **Office 365** aus, geben Sie Ihre Anmeldeinformationen
    ein und wählen Sie **Login** aus.

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  Melden Sie sich mit Ihrer **M365 Admin tenant Id** an und wählen Sie
    dann **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Geben Sie das Kennwort Ihrer **M365 Admin tenant Id’s** ein und
    wählen Sie dann **Sign in** aus.

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  Überprüfen Sie, ob die **Dev One**-Umgebung ausgewählt ist.

7.  Wählen Sie **Register | Register New Assembly**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  Wählen Sie unter Schritt 1 ... aus und navigieren Sie dann zum
    Ordner **CustomAPILab\bin\Debug\net462**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  Wählen Sie **CustomAPILab.dll** und dann **Open** aus.

> ![](./media/image35.png)

10. Wählen Sie **Register Selected Plugins** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. Klicken Sie in der Erfolgsmeldung auf „**OK**“. Ihr Plug-In ist
    bereit für die Verbindung mit der benutzerdefinierten API, die wir
    in der nächsten Aufgabe erstellen werden.

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**Aufgabe 3: Erstellen der benutzerdefinierten API**

1.  Navigieren Sie mit zum Power Apps Maker-Portal mit +++
    <https://make.powerapps.com/>+++ und stellen Sie sicher, dass Sie
    sich in der **Dev One**-Umgebung befinden.

2.  Wählen Sie in der linken Navigation **Solutions** aus. Wählen Sie
    **+ New Solution** aus.

> ![](./media/image38.png)

3.  Geben Sie als Display Name +++**Custom API Lab**+++ ein.

4.  Wählen Sie **CDS Default Publisher** im Dropdown-Menü Publisher aus.

5.  Wählen Sie **Create**. Dadurch wird eine benutzerdefinierte Lösung
    erstellt, die unsere Komponenten enthält.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Wählen Sie **+ New | More | Other | Custom API**.

> ![](./media/image40.png)

7.  Geben Sie die folgenden Informationen ein:

    - **Unique Name:** +++contoso_match+++

    &nbsp;

    - **Name**: +++Match+++

    &nbsp;

    - **Display Name:** +++Match+++

    &nbsp;

    - **Description**: +++Match a string+++

    &nbsp;

    - **Binding Type**: +++Global+++

    &nbsp;

    - ![A screenshot of a computer Description automatically
      generated](./media/image41.png)

8.  Wählen Sie unter „Plugin Type“ das **Search** symbol aus und suchen
    Sie Ihr Plugin – **CustomAPILab.MatchPlugin**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  Wählen Sie **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. Wählen Sie **Done** aus.

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11. Wählen Sie **+** **New | More| Other | Custom API Request
    Parameter**.

> ![](./media/image44.png)

12. Wählen Sie für **Custom API,** das **Search** symbol und wählen Sie
    **Match** (Ihre benutzerdefinierte API) aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. Geben Sie der Einfachheit halber +++**StringIn**+++ für Unique Name,
    Name, Display Name and Description ein.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. Wählen Sie **String** als Type aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. Wählen Sie **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. Wählen Sie **Done** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. Um weiteren Custom API Request Parameter hinzuzufügen, wählen Sie
    **+ New | More| Other | Custom API Request Parameter**.

> ![](./media/image50.png)

18. Wählen Sie für **Custom API**, das **Search** symbol und wählen Sie
    **Match** (your Custom API) aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. Geben Sie der Einfachheit halber **Pattern** für Unique Name, Name,
    Display Name and Description ein.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. Wählen Sie **String** als Type aus.

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. Wählen Sie **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. Wählen Sie **Done** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. Wählen Sie **New | More | Other| Custom API Response Property.**

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. Wählen Sie für **Custom API,** das **Search** symbol und wählen Sie
    **Match** (your Custom API) aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. Geben Sie der Einfachheit halber +++**Matched**+++ für **Unique
    Name**, **Name, Display Name** und **Description** ein.

26. Wählen Sie „**Boolean**“ für „**Type**“.

> ![](./media/image58.png)

27. Wählen Sie **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. Wählen Sie **Done** aus.

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. Ihre Lösungskomponentenliste sollte wie folgt aussehen.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**Aufgabe 4: Benutzerdefinierte API von Power Automate verwenden**

1.  Wählen Sie in solution **+ New | Automation | Cloud Flow |
    Instant**.

> ![](./media/image62.png)

2.  Geben Sie +++**String match**+++ als Flow name ein, wählen Sie
    „**Manually trigger a flow** “ und dann „**Create**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  Wählen Sie **+ New Step** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  Suchen Sie nach perform und wählen Sie **Perform an unbound
    action**.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  Suchen Sie in der Liste „Action Name“ nach „**contoso_match**“ und
    wählen Sie es aus.

> ![](./media/image66.png)

6.  Geben Sie die E-Mail-Adresse **myemail@outlook.com** in **StringIn**
    ein. Hier können Sie jede gültige einfache E-Mail-Adresse eingeben.

> ![](./media/image67.png)

7.  Geben Sie den folgenden regulären Ausdruck in Pattern ein. Dies ist
    ein einfaches E-Mail-Pattern. Andere
    [*examples*](https://regexlib.com/DisplayPatterns.aspx/)  sind
    verfügbar.

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  Ihr Ablauf sollte wie folgt aussehen.

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  Wählen Sie **Save** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. Wählen Sie nach Abschluss des Speichervorgangs „**Test**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. Wählen Sie „**Manually**“ und dann „**Test**“ aus.

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. Wählen Sie **Run flow** aus.

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. Wählen Sie **Done** aus.

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. Wählen Sie nach Abschluss Ihres Flows **Perform an unbound
    action** aus, um ihn zu erweitern und die Ergebnisse anzuzeigen.

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**Zusammenfassung:** In diesem Lab, haben Sie gelernt, wie man eine
benutzerdefinierte Aktion erstellt und sie in einem Power
Automate-Ablauf verwendet. Die benutzerdefinierte API-Aktion
contoso_match ist jetzt auch für den direkten Aufruf über die
Plattform-API verfügbar.
