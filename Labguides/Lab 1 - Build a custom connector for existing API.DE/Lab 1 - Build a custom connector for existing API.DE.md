**Lab 1: Erstellen Sie einen benutzerdefinierten Connector für die
vorhandene API und verwenden Sie diesen in der Canvas-App**

**Geschätzte Dauer:** 35 Minuten

**Ziele:** In diesem Lab lernen Sie, Ihren ersten benutzerdefinierten
Konnektor für eine vorhandene API namens Contoso Invoicing zu erstellen,
eine Canvas-App zu erstellen und den Connector in der Canvas-App zu
verwenden.

**Aufgabe 1: Überprüfen der API**

Um die API zu überprüfen, führen Sie die folgenden Schritte aus:

1.  Gehen Sie zu +++<https://contosoinvoicing.azurewebsites.net/>+++.

2.  Um den Dokumentationslink auszuwählen, klicken Sie **here** neben
    „You can find the API documentation’.

> ![](./media/image1.png)

3.  Überprüfen Sie die verfügbaren Betriebe.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Schließen Sie die Registerkarte oder das Fenster des
    Dokumentationsbrowsers.

5.  Wählen Sie den Link „**Open API definition**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Das folgende Bild zeigt ein Beispiel der OpenAPI-Version der
    Dokumentationsseite. Klicken Sie mit der rechten Maustaste und
    wählen Sie „**Save as**“.

> ![Screenshot of an arrow pointing to the save as
> button.](./media/image4.png)

7.  Speichern Sie die Datei lokal auf dem Desktop der VM. Sie benötigen
    diese Datei später in der Übung.

8.  Schließen Sie die Registerkarte oder das Fenster des
    Definitionsbrowsers.

9.  Wählen Sie den **API Key**-Link.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. Kopieren Sie Ihren API-Key und speichern Sie ihn im Notizblock Ihrer
    VM, da Sie ihn später benötigen.

> ![](./media/image6.png)

11. Wählen Sie **Return to home**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. Wählen Sie **Download Logo**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. Speichern Sie das Logobild lokal auf dem Desktop der VM. Sie werden
    es später verwenden.

**Aufgabe 2: Erstellen einer neuen Lösung**

Um eine neue Lösung zu erstellen, führen Sie die folgenden Schritte aus:

1.  Gehen Sie zu <https://make.powerapps.com/> und stellen Sie sicher,
    dass Sie sich in der **Dev One**-Umgebung befinden.

> ![](./media/image9.png)

2.  Wählen Sie im linken Navigationsbereich „**Solutions**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  Wählen Sie im oberen Menüband „**+New solution**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

4.  Geben Sie als **Display name** +++**Contoso invoicing**+++ ein und
    wählen Sie **+ New publisher** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

5.  Geben Sie +++**Contoso**+++ für Display name, +++**Contoso**+++ für
    Name und +++**contoso**+++ für Prefix ein, und wählen Sie dann
    **Save** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> **Notiz:** Wenn Sie die Fehlermeldung „A record with matching key
> values already exists“ erhalten, ignorieren Sie diese und schließen
> Sie das Fenster „New publisher’.
>
> ![](./media/image14.png)

6.  Wählen Sie nun im Fenster „**New solution**“ als **Publisher**
    „**Contoso**“ und dann „**Create**“ aus. Wenn Sie an einem echten
    Projekt arbeiten, empfiehlt es sich, einen eigenen Herausgeber zu
    erstellen.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  Verlassen Sie diese Seite nicht, nachdem Sie „**Create**“ ausgewählt
    haben. Sie werden automatisch zur Lösung „Contoso invoicing”
    weitergeleitet.

**Aufgabe 3: Einen neuen Connector erstellen**

Um einen neuen Connector zu erstellen, führen Sie die folgenden Schritte
aus:

1.  Stellen Sie sicher, dass Sie sich in der von Ihnen erstellten
    **Contoso invoicing** lösung befinden.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

2.  Wählen Sie **+ New** | **Automation** | **Custom connector**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

3.  Geben Sie als **Connector name** +++**Contoso invoicing**+++ ein.

> ![](./media/image18.png)

4.  Wählen Sie „**Upload**“, um das Bild hochzuladen.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

5.  Wählen Sie das Connector-Logobild aus, das Sie in **Aufgabe 1:
    Überprüfen der API** heruntergeladen haben.

6.  Geben Sie +++#**175497**+++ als **Icon background color** ein.

7.  Geben Sie als **Description** +++ **Custom connector for Contoso
    Invoicing API** +++ ein.

8.  Geben Sie +++ **contosoinvoicingtest.azurewebsites.net** +++ als
    **Host** ein.

> ![](./media/image20.png)

9.  Wählen Sie „**Create connector**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

10. Verlassen Sie diese Seite nicht.

**Aufgabe 4: Importieren der OpenAPI-Definition**

Um die OpenAPI-Definition zu importieren, führen Sie die folgenden
Schritte aus:

1.  Wählen Sie den Pfeil neben „**Connector-Name**“ aus.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image22.png)

2.  Wählen Sie die Auslassungspunkte-Schaltfläche (...) des Connectors
    und dann „**Update from OpenAPI file**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  Wählen Sie **Import**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

4.  Wählen Sie die Datei **swagger.json** aus, die Sie in **Aufgabe 1:
    Überprüfen der API** heruntergeladen haben, und wählen Sie dann
    **Open** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

5.  Wählen Sie **Continue** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  Geben Sie die Host-URL als
    +++**contosoinvoicingtest.azurewebsites.net**+++ ein und wählen Sie
    dann **Security** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

7.  Beachten Sie, dass die Felder aus der importierten Datei ausgefüllt
    werden.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  Verlassen Sie diese Seite nicht.

**Aufgabe 5: Definitionen überprüfen und anpassen**

Um Definitionen zu überprüfen und anzupassen, gehen Sie folgendermaßen
vor:

1.  Wählen Sie die Registerkarte **Definition** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

2.  Nehmen Sie sich ein paar Minuten Zeit, um die importierten Betriebe
    zu überprüfen.

3.  Beachten Sie den blauen Informationskreis neben **GetInvoice**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  Wählen Sie die Operation **GetInvoice** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Beachten Sie, dass der Vorgang auf eine fehlende **Summary**
    hinweist.

> ![A screenshot of a phone Description automatically
> generated](./media/image32.png)

6.  Geben Sie „**Get Invoice**“ als **Summary** ein, um die
    Benutzerfreundlichkeit zu verbessern.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

7.  Beachten Sie den blauen Informationskreis neben der
    **PayInvoice**-Operation und dass dieser auf eine fehlende
    **Description** hinweist.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

8.  Wählen Sie den Vorgang „**PayInvoice**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

9.  Geben Sie als **Description** „**Pay an invoice**“ ein.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

10. Löschen Sie beide **NewInvoice**-Betriebe, da Sie sie nicht
    verwenden werden.

> ![Screenshot showing the delete action button.](./media/image37.png)

11. Wählen Sie die Operation **GetInvoiceSchema** aus.

> ![](./media/image38.png)

12. Ändern Sie die **Visibility** option in „**internal**“, damit die
    Benutzer sie nicht in ihrer Aktionsliste sehen, und wählen Sie dann
    „**Update connector**“ aus.

> ![](./media/image39.png)

13. Verlassen Sie diese Seite nicht.

**Aufgabe 6: Testen Sie den Connector**

Um den Connector zu testen, führen Sie die folgenden Schritte aus:

1.  Wählen Sie die Registerkarte **Test**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

2.  Wählen Sie **+** **New connection**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

3.  Fügen Sie den **API-Key** ein, den Sie in **Aufgabe 1: Überprüfen
    Sie die API** gespeichert haben, und wählen Sie dann **Create
    connection** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

4.  Wählen Sie die Schaltfläche „**Refresh**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

5.  Wählen Sie **ListInvoiceTypes | Test Operation**.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

6.  Sie sollten die Daten der Rechnungsarten im Body-Bereich sehen.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

7.  Wählen Sie „**Close**“ aus, um das Fenster des benutzerdefinierten
    Connectors zu schließen.

> ![](./media/image46.png)

**Aufgabe 7: Benutzerdefinierten Connector in der Canvas-App verwenden**

In dieser Aufgabe erstellen Sie eine Canvas-Anwendung und verwenden, den
von Ihnen erstellten benutzerdefinierten Connector, um eine Liste von
Rechnungen anzuzeigen.

1.  Kehren Sie zum Power Apps Maker-Portal zurück. Wählen Sie im
    Popup-Fenster „Currently creating a new custom connector“ „**Done**“
    aus. Stellen Sie sicher, dass Sie sich in der **Dev One**-Umgebung
    befinden.

> ![](./media/image47.png)
>
> **Notiz:** Falls das Portal noch nicht geöffnet ist, navigieren Sie zu
> +++<https://make.powerapps.com/>+++ und stellen Sie sicher, dass Sie
> sich in der **Dev One**-Umgebung befinden.

2.  Stellen Sie sicher, dass Sie sich in der von Ihnen erstellten
    **Contoso invoicing** lösung befinden. Wenn nicht, wählen Sie
    „**Solutions**“ aus und öffnen Sie die von Ihnen erstellte **Contoso
    invoicing** lösung.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

3.  Wählen Sie + **New** und dann **App \> Canvas app**

> ![](./media/image49.png)

4.  Geben Sie als App-Nam, die **Contoso invoicing app** ein, wählen Sie
    als Format „**Phone**“ und dann „**Create**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

5.  Wählen Sie im welcome window „**Skip**“ aus.

> ![](./media/image51.png)

6.  Wählen Sie die Registerkarte „**Data**“ und dann **+ Add data** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

7.  Erweitern Sie „**Connectors**“, und wählen Sie dann den
    benutzerdefinierten **Contoso invoicing** connector aus, den Sie
    erstellt haben.

> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

8.  Wählen Sie **+ Add a connector** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

9.  Fügen Sie den API-Key ein, den Sie in **Aufgabe 1: Überprüfen Sie
    die API** gespeichert haben, und wählen Sie dann „**Connect**“ aus.

> ![A screenshot of a login box Description automatically
> generated](./media/image55.png)

10. Wählen Sie im Premium-Warn-Popup „**Got it**“ aus.

> ![A screenshot of a phone Description automatically
> generated](./media/image56.png)

11. Wählen Sie die Registerkarte „**Tree view**“.

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

12. Wählen Sie **+ Insert** und dann **Vertical gallery**.

> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

13. Wählen Sie **ContosoInvoicing** für Daten aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

14. Stellen Sie **Items** auf den unten stehenden Wert ein.

> +++ContosoInvoicing.ListInvoices().invoices+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image60.png)

15. Erweitern Sie die Galerie und wählen Sie **Subtitle** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

16. Setzen Sie den **Text** wert von Subtitle auf
    +++**ThisItem.amount**+++.

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

17. Erweitern Sie die Galerie und wählen Sie den **Title** in der
    Galerie aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

18. Setzen Sie den **Text** wert des Titels auf
    +++**ThisItem.accountName**+++.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

19. Die Galerie sollte jetzt wie im Bild unten aussehen.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

**Zusammenfassung:** In diesem Lab, haben Sie gelernt, einen
benutzerdefinierten Connector für eine bestehende API zu erstellen, die
API-Definition zu importieren und diesen Konnektor in der Canvas-App zu
verwenden, um eine Liste von Rechnungen anzuzeigen. Benutzerdefinierte
Connectoren sind funktionsbasiert, sie rufen bestimmte Funktionen im
zugrunde liegenden Dienst der API auf, um die entsprechenden Daten
zurückzugeben.
