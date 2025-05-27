**Lab 3: Installieren und Verwenden von Entwicklertools**

**Geschätzte Dauer:**15 Minuten

**Ziele:** In diesem Lab lernen Sie, einige der Entwicklertools von
NuGet zu installieren.

**Aufgabe 1: Entwicklertools installieren**

In dieser Aufgabe verwenden Sie eine Power Platform-CLI, um Tools zu
installieren.

1.  Um **Command Prompt** zu starten, gehen Sie zum **Start** menü der
    VM, geben Sie „Command Prompt“ in das Suchfeld ein und wählen Sie
    „**Open**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Führen Sie den folgenden Befehl aus, um das **Configuration Manager
    Tool** zu installieren.

> +++pac-Tool cmt+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Das Configuration Manager Tool sollte installiert und gestartet
    sein. Schließen Sie das Configuration Manager Tool.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Führen Sie den folgenden Befehl aus, um das **Package Deployer
    Tool** zu installieren.

> +++Pac-Tool PD+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Das Package Deployer Tool sollte installiert und gestartet sein.
    Schließen Sie das Package Deployer Tool.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Führen Sie den folgenden Befehl aus, um das **Plugin Registration
    Tool** zu installieren.

> +++pac tool prt+++
>
> ![](./media/image6.png)

7.  Die Plugin Registration sollte installiert und gestartet sein.
    Schließen Sie das Plugin Registration Tool nicht.

> ![](./media/image7.png)

**Aufgabe 2: Erkundung von registrierten plug-in mit dem
Plug-in-registration tool**

1.  Wählen Sie „**Create New Connection**“ aus.

> ![](./media/image8.png)

2.  Aktivieren Sie das Kontrollkästchen **Display list of available
    organizations**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  Wählen Sie **Login**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Melden Sie sich mit Ihren
    Dataverse-Umgebungsanmeldeinformationen, d. h. Ihren Office
    365-Administratoranmeldeinformationen, an. Klicken Sie auf **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  Geben Sie Ihr Mandantenadministratorkennwort ein und klicken Sie auf
    **Sign in**.

> ![A screenshot of a login box Description automatically
> generated](./media/image12.png)

6.  In diesem Fall sehen Sie, dass die **Dev One**-Umgebung bereits
    ausgewählt ist. Falls die Liste der Umgebungen angezeigt wird,
    wählen Sie Ihre Umgebung – **Dev One** – und klicken Sie erneut auf
    „**Login**“.

> ![](./media/image13.png)

7.  Sie sehen eine Liste der System-Plugins. Wenn Ihre Umgebung
    benutzerdefinierte Plugins enthält, werden diese ebenfalls in der
    Liste angezeigt. Die Assembly sind .NET DLLs, die die Plugins
    implementieren.

> **Notiz:** Sie müssen den Abschnitt erweitern, um die vollständige
> Liste anzuzeigen.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

8.  Suchen Sie nach **Microsoft.CDS.DataLakeDataProvider.Plugins** und
    erweitern Sie es.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

9.  Jedes der untergeordneten Elemente ist im assembly implementiert.
    Erweitern Sie eines der Elemente, um die Schrittregistrierungen für
    dieses einzelne Plug-in zu sehen.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

10. Die Schrittregistrierung verbindet das Plug-In als Ereignishandler
    mit dem Ereignis. Im obigen Beispiel wird dadurch eine Erstellung in
    der Tabelle „insightsstorevirtualentity“ verarbeitet.

> ![](./media/image17.png)

11. Doppelklicken Sie auf einen beliebigen Schritt, um die
    Konfigurationsdetails des Schritts anzuzeigen, einschließlich der
    Nachricht und Entität, bei der er registriert ist, der
    Pipeline-Phase, in der das Plug-In aufgerufen wird, ob die
    Ausführung synchron oder asynchron ist usw.

> ![](./media/image18.png)

**Zusammenfassung:** In diesem Lab haben Sie gelernt, wie Sie
Entwicklertools installieren. Wenn Sie Ihr eigenes benutzerdefiniertes
Plug-in erstellen, verwenden Sie das Plug-in-Registrierungstool, um die
Assembly zu laden und die Schritte für die zu verarbeitenden Ereignisse
zu registrieren.
