# **Lab 8: Erstellen einer erweiterbaren Webvorlage**

**Geschätzte Dauer:**25 Minuten

**Ziele:** In diesem Lab lernen Sie, wie Sie Liquid-Vorlagen mithilfe
von Extend- und Block-Tags erweitern, wie Sie Liquid-Vorlagen mithilfe
des Include-Tags wiederverwenden und wie Sie Tabellenberechtigungen auf
die Ergebnisse der neuen Vorlage anwenden.

**Aufgabe 1: Erstellen einer Teilvorlage**

Ihre erste Aufgabe besteht darin, eine Teilvorlage zu erstellen, die
nicht zum Rendern einer Seite verwendet, sondern in eine andere Vorlage
eingefügt wird.

1.  Melden Sie sich bei Power Pages an
    +++<https://make.powerpages.microsoft.com/>+++.

2.  Wählen Sie oben rechts die Zielumgebung **Dev One** aus.

> ![](./media/image1.png)

3.  Unter der Registerkarte **Active sites** wird Ihre Website –
    **Finance Advisor Search** – angezeigt. Wählen Sie „**Edit**“ aus.

> ![](./media/image2.png)

4.  Erweitern Sie das Erweiterungsmenü (Auslassungspunkte) und wählen
    Sie dann **Portal management** aus, um die Portal Management App zu
    öffnen.

> ![](./media/image3.png)

5.  Wählen Sie **Web Templates** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Wählen Sie +**New** aus.

> ![A screenshot of a web page Description automatically
> generated](./media/image5.png)

7.  Geben Sie die folgenden Werte ein:

    - **Name** - +++Directory+++

    &nbsp;

    - **Website** - Wählen Sie Ihre aktuelle Website- Finance Advisor
      Search

    &nbsp;

    - **Source** - Geben Sie den folgenden Inhalt ein:

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
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

8.  Wählen Sie **Save & Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

**Aufgabe 2: Erweitern einer vorhandenen Vorlage**

Als Nächstes erstellen Sie eine neue Vorlage, die eine vorhandene
Liquid-Vorlage erweitert, und fügen dann die zuvor erstellte Vorlage
ein.

1.  Wählen Sie im linken Navigationsbereich **Web Templates** aus.
    Wählen Sie +**New** aus.

> ![](./media/image8.png)

2.  Geben Sie die folgenden Werte ein:

    - **Name** - +++Directory Template+++

    &nbsp;

    - **Website** - Wählen Sie Ihre aktuelle Website- Finance Advisor
      Search

    &nbsp;

    - **Source** - Geben Sie den folgenden Inhalt ein:

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
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  Wählen Sie **Save & Close**.

> ![A screenshot of a web template Description automatically
> generated](./media/image10.png)

**Aufgabe 3: Erstellen Sie eine Seiten Vorlage und verknüpfen Sie sie
mit dieser Seite**

In dieser Aufgabe erstellen Sie eine Seitenvorlage, die Ihre neue
Webvorlage verwendet und die Verzeichnisausgabe enthält.

1.  Wählen Sie im linken Navigationsbereich **Page Templates** aus.
    Wählen Sie +**New** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

2.  Geben Sie die folgenden Werte ein:

    - **Name** - +++Directory Page Template+++

    &nbsp;

    - **Website** - Wählen Sie die aktuelle Website- Finance Advisor
      Search

    &nbsp;

    - **Type** - Wählen Sie **Web Template**

    &nbsp;

    - **Web Template** - Wählen Sie **Directory Template**

    &nbsp;

    - **Table Name** - Wählen Sie **Web Page**

3.  **Optional:** Fügen Sie ein Text-Element zum Seiteninhalt hinzu und
    geben Sie dann einen Text Ihrer Wahl ein.

4.  Wählen Sie **Save & Close**.

> ![A screenshot of a web page Description automatically
> generated](./media/image12.png)

**Aufgabe 4: Testen der Seitenvorlage**

Ihr nächster Schritt besteht darin, zu testen, ob Ihre neue Vorlage
funktioniert:

1.  Kehren Sie zur Registerkarte „Home“ der Power Pages
    Designstudio-Seite zurück.

2.  Wählen Sie **Sync**, um die Änderungen zu synchronisieren.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Wählen Sie den Arbeitsbereich **Pages** aus. Wählen Sie + **Page**
    aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

4.  Führen Sie im Dialogfeld **Add a page** die folgenden Schritte aus:

    1.  Geben Sie als page name +++ **Directory** +++ ein.

    &nbsp;

    1.  Wählen Sie **Custom layouts** und dann **Directory Page
        Template** aus.

    &nbsp;

    1.  Wählen Sie **Add**.

> ![A screenshot of a website Description automatically
> generated](./media/image15.png)
>
> Die leere Seite wird mit der Meldung „You don't have permissions to
> access the directory“ im rechten Bereich angezeigt.
>
> ![](./media/image16.png)

**Aufgabe 5: Berechtigungen für Tabellen hinzufügen**

**Warnung:** Die Gewährung einer globalen Leseberechtigung für anonyme
Benutzer dient nur zu Illustrationszwecken. Seien Sie vorsichtig, um zu
vermeiden, dass Sie unbeabsichtigt sensible Informationen preisgeben,
indem Sie übermäßige Berechtigungen gewähren und keine geeigneten Filter
in Ihre Ansichten oder FetchXML-Ausdrücke aufnehmen.

Befolgen Sie diese Schritte, um Tabellenberechtigungen hinzuzufügen.

1.  Wählen Sie den **Security workspace** und dann **Table Permissions**
    aus.

> ![A screenshot of a computer security Description automatically
> generated](./media/image17.png)

2.  Wählen Sie + **New permission**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

3.  Geben Sie die folgenden Werte ein:

    - **Name** - +++Account Directory+++

    &nbsp;

    - **Table** - Wählen Sie **Account (account)** Tabelle

    &nbsp;

    - **Access type** - Wählen Sie **Global access**

    &nbsp;

    - **Permission to** - Wählen Sie **Read**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

4.  Wählen Sie **Add roles** aus.

5.  Wählen Sie **Anonymous users** und **Authenticated users** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  Wählen Sie **Save** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  Wählen Sie **Save** aus.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image22.png)

**Aufgabe 6: Testen der Vorlage**

Ihre letzte Aufgabe besteht darin, Ihre neue Vorlage zu testen:

1.  Wählen Sie den Arbeitsbereich „**Pages**“ und dann die Seite
    „**Directory**“ aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

2.  Wählen Sie **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> **Notiz:** Ein einfaches Aktualisieren der Browserseite reicht nicht
> aus, um die Daten zu aktualisieren. Mit diesem Befehl wird stattdessen
> der Site-Cache neu erstellt.
>
> Die Seite sollte jetzt angezeigt werden und die Liste der Konten im
> rechten Bereich enthalten.
>
> ![A screenshot of a search engine Description automatically
> generated](./media/image25.png)

**Zusammenfassung:** In diesem Lab haben Sie gelernt, Liquid-Vorlagen zu
erstellen und zu erweitern. Sie haben eine neue Seitenvorlage erstellt,
die ein Seitenfenster enthält, in dem alle Konten in Dataverse
aufgelistet sind.
