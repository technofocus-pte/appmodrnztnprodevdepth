# **Laboratorio 8: Cree una plantilla web extensible**

**Duración estimada:** 25 minutos

**Objetivo:** en este laboratorio, aprenderá a extender los Liquid
templates con los extend y block tags, reusar las Liquid templates con
el include tag y aplicar los table permissions a los resultados de la
nueva plantilla.

**Tarea 1: Cree un template parcial**

Su primera tarea es crear un partial template que no será usado para
renderizar una página, pero será insertado en otra plantilla.

1.  Inicie sesión en Power Pages
    +++<https://make.powerpages.microsoft.com/>+++.

2.  Seleccione el target environment **Dev One** en la esquina superior
    derecha.

> ![](./media/image1.png)

3.  En la pestaña **Active sites**, puede ver su sitio – **Finance
    Advisor Search**. Seleccione **Edit**.

> ![](./media/image2.png)

4.  Expanda su extension menu (tres puntos), y seleccione **Portal
    management** para abrir el Portal Management app.

> ![](./media/image3.png)

5.  Seleccione **Web Templates**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Seleccione +**New**.

> ![A screenshot of a web page Description automatically
> generated](./media/image5.png)

7.  Introduzca los siguientes valores:

    - **Name** - +++Directory+++

    &nbsp;

    - **Website** – Seleccione su sitio actual - Finance Advisor Search

    &nbsp;

    - **Source** – introduzca el siguiente contenido:

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

8.  Seleccione **Save & Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

**Tarea 2: Extender un template existente**

A continuación, creará un nuevo template que extiende un existing Liquid
template y insertára el template que creó.

1.  Desde el panel de navegación, seleccione **Web Templates**.
    Seleccione +**New**.

> ![](./media/image8.png)

2.  Introduzca los siguientes valores:

    - **Name** - +++Directory Template+++

    &nbsp;

    - **Website** – Seleccione su sitio actual - Finance Advisor Search

    &nbsp;

    - **Source** – introduzca el siguiente contenido:

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

3.  Seleccione **Save & Close**.

> ![A screenshot of a web template Description automatically
> generated](./media/image10.png)

**Tarea 3: Cree un page template y vínculelo con l página**

En esta tarea, creará un page template que usa su nuevo web template e
incluirá Directory output.

1.  Desde el panel de navegación, seleccione **Page Templates**.
    Seleccione +**New**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

2.  Introduzca los siguientes valores:

    - **Name** - +++Directory Page Template+++

    &nbsp;

    - **Website** – Seleccione el sitio actual - Finance Advisor Search

    &nbsp;

    - **Type** - Seleccione **Web Template**

    &nbsp;

    - **Web Template** - Seleccione **Directory Template**

    &nbsp;

    - **Table Name** - Seleccione **Web Page**

3.  **Opcional:** Agregue un elemento de texto al contenido de la página
    e introduzca un texto.

4.  Seleccione **Save & Close**.

> ![A screenshot of a web page Description automatically
> generated](./media/image12.png)

**Tarea 4: Pruebe el page template**

Su siguiente paso es probar su nuevo template:

1.  Vuelva a la pestaña de inicio de Power Pages design studio.

2.  Seleccione **Sync** para sincronizar los cambios.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Seleccione el **Pages** workspace. Seleccione **+ Page**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

4.  En el diálogo **Add a page**, complete los siguientes pasos:

    1.  Introduzca +++**Directory**+++ como el nombre de la página.

    &nbsp;

    1.  Seleccione **Custom layouts** y luego seleccione **Directory
        Page Template**.

    &nbsp;

    1.  Seleccione **Add**.

> ![A screenshot of a website Description automatically
> generated](./media/image15.png)
>
> La página vacía mostrará el mensaje "You don't have permissions to
> access the directory" en el panel derecho.
>
> ![](./media/image16.png)

**Tarea 5: Agregue los permisos de tabla**

**Atención:** La concesión de permisos de lectura global a usuarios
anónimos es solo para fines ilustrativos. Tenga cuidado para evitar
exponer involuntariamente información confidencial concediendo permisos
excesivos y no incluyendo los filtros adecuados en las vistas o
expresiones FetchXML.

Siga estos pasos para agregar permisos de tabla.

1.  Seleccione **Security workspace** y luego seleccione **Table
    Permissions**.

> ![A screenshot of a computer security Description automatically
> generated](./media/image17.png)

2.  Seleccione **+ New permission**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

3.  Introduzca los siguientes valores:

    - **Name** - +++Account Directory+++

    &nbsp;

    - **Table** – Seleccione la tabla **Account (account)**

    &nbsp;

    - **Access type** - Seleccione **Global access**

    &nbsp;

    - **Permission to** - Seleccione **Read**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

4.  Seleccione **Add roles**.

5.  Seleccione **Anonymous users** y **Authenticated users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  Seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  Seleccione **Save**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image22.png)

**Tarea 6: Pruebe el template**

Su tarea final es probar su nuevo template:

1.  Seleccione el **Pages** workspace y seleccione la
    página **Directory**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

2.  Seleccione **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> **Ojo:** Una simple actualización de la página del navegador no será
> suficiente para actualizar los datos. En su lugar, el uso de este
> command reconstruye la caché del sitio.
>
> Ahora debería mostrarse la página e incluir la lista de cuentas en el
> panel derecho.
>
> ![A screenshot of a search engine Description automatically
> generated](./media/image25.png)

**Resumen:** En este laboratorio, ha aprendido a crear y ampliar Liquid
template. Ha creado una nueva plantilla de página que incluye un panel
lateral que enumera todas las cuentas en Dataverse.
