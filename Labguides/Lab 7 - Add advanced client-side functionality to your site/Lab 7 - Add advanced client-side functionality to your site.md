# **Laboratorio 7: Agregue un advanced client-side functionality a su sitio**

**Duración estimada:** 35 minutos

**Objetivo:** En este laboratorio, aprenderá a agregar un JavaScript
code a una página para rederizar datos de Microsoft Dataverse como un
gráfico.

### **Tarea 1: Cree un sitio con la ayuda de AI**

1.  Vaya a Power Pages en
    +++<https://make.powerpages.microsoft.com/>+++. Asegure que está en
    el **Dev One** environment.

> ![](./media/image1.png)

2.  Seleccione **Skip** en la página **Tell us about yourself**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Introduzca la siguiente descripción para crear un sitio y haga clic
    en el ícono **generate**.

> +++**Create a site for customers to find financial advisors at a bank
> based on their qualifications, and areas of expertise**+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Copilot genera un nombre de sitio y una dirección web en función de
    su descripción. En este caso, el nombre del sitio es ‘**Finance
    Advisor Search’**. Mantenga el nombre y la dirección generados y
    seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Copilot genera un home page layout, lo que puede explorar.
    Seleccione **Next** para aceptar el layout sugerido.

> **Ojo:** Puede seleccionar **Try again** para generar un nuevo layout.
>
> ![A screenshot of a website Description automatically
> generated](./media/image5.png)

6.  Copilot genera más páginas que se pueden usar en el sitio en función
    de su descripción. En este ejemplo, están seleccionadas las páginas
    Contact us, Advisor search, Advisor profile y Advisor contact y
    seleccione **Done** para completar la creación del sitio.

> **Ojo:** Si su copilot genera varias páginas para su sitio además de
> las mencionadas anteriormente, puede seleccionarlas.
>
> ![](./media/image6.png)

7.  La creación del sitio puede llevar unos minutos. Cuando termine, se
    le lleva al sitio en el design studio que puede seguir
    personalizando.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

### **Tarea 2: Cree las configuraciones del sitio**

Para crear los site settings, siga estos pasos.

1.  Seleccione los tres puntos (**...**) y seleccione **Portal
    management**.

> Se abre el Portal Management app en una nueva pestaña.
>
> ![](./media/image8.png)

2.  Seleccione **Site Settings**. Seleccione **+ New.** 

> ![](./media/image9.png)

3.  Introduzca la siguiente información y seleccione **Save**.

    - **Name** - +++Webapi/account/enabled+++

    &nbsp;

    - **Website** – Seleccione su sitio

    &nbsp;

    - **Value** - +++true+++

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Seleccione **+ New.** 

> ![](./media/image11.png)

5.  Introduzca la siguiente información y seleccione **Save & Close**.

    - **Name** - +++Webapi/account/fields+++

    &nbsp;

    - **Website** - Select your website

    &nbsp;

    - **Value** - +++name,numberofemployees,revenue+++

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

### **Tarea 3: Cree los permisos de la tabla**

Para crear los table permissions, siga estos pasos.

1.  Cambie a Power Pages design studio, donde se abre el sitio recién
    creado.

> **Ojo:** Puede cerrar el panel de Copilot para mayor visibilidad.
>
> ![](./media/image13.png)

2.  Seleccione el **Security** workspace y seleccione **Table
    permissions**.

> ![A screenshot of a computer security Description automatically
> generated](./media/image14.png)

3.  Seleccione **+ New permission.**

> ![](./media/image15.png) 

4.  Introduzca la siguiente información:

    - **Name** - +++Account+++

    &nbsp;

    - **Table** - +++Account (account)+++

    &nbsp;

    - **Access type** - Global

    &nbsp;

    - **Permission to** – Read

> ![](./media/image16.png)

5.  Seleccione **Add roles** y agregue **Anonymous
    Users** y **Authenticated Users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

6.  Seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

7.  Elija **Save** paraque los datos sean visibles a todos.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image19.png)

8.  Puede ver el mensaje ‘The table permission ‘Account’ have
    successfully been saved’.

> ![](./media/image20.png)

### **Tarea 4: Pruebe el Web API**

1.  Para probar el Web API, abra el siguiente URL después de agregar su
    sitio
    +++[https://**yourwebsite**.powerappsportals.com/\_api/accounts?$select=name,numberofemployees,revenue](https://yourwebsite.powerappsportals.com/_api/accounts?$select=name,numberofemployees,revenue)+++

2.  SI aparece el diálogo permissions requested, seleccione **Accept**.

> ![A screenshot of a application Description automatically
> generated](./media/image21.png)

3.  Si salida se debe ver así.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

### **Tarea 5: Cree una página del contenido y recupere datos**

Para crear un content page y agregar JavaScript code que recupera y
transforma los datos, siga estos pasos:

1.  En design studio, seleccione el **Pages** workspace y seleccione **+
    Page**.

> ![](./media/image23.png)

2.  Introduzca +++**Chart**+++ como el **Page name**.

3.  Asegúrese de que esté seleccionado la opción **Add page to main
    navigation**.

4.  Seleccione el **Start from blank** layout.

5.  Seleccione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

6.  Seleccione **Edit code**.

> ![](./media/image25.png)

7.  En el diálogo pop-up, seleccione **Open Visual Studio Code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

8.  Si aparece un pop-up y le pide que el extension Power Platform tool
    inicie sesión mediante Microsoft, seleccione **Allow**.

> ![A black screen with white text Description automatically
> generated](./media/image27.png)

9.  Buscará sus datos.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

10. En el Visual Studio Code editor, seleccione
    el **Chart.en-US.customjs.js** file.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

11. Agregue el siguiente script:

> function makeChart(rawData) {
>
> // transform raw data into plotting array
>
> var rData = rawData.value.map(({
>
> name,
>
> revenue,
>
> numberofemployees
>
> }) =\> ({
>
> "x": numberofemployees,
>
> "y": revenue,
>
> "z": (!revenue) ? 1 : numberofemployees / revenue,
>
> "name": name
>
> }));
>
> console.log(rData);
>
> }
>
> // retrieve accounts data using portals Web API
>
> $(document).ready(function() {
>
> $.get('/\_api/accounts?$select=name,numberofemployees,revenue',
> makeChart, 'json');
>
> });

12. Presione el **Ctrl + S** keyboard shortcut (**⌘ + S** en Mac) para
    guardar el archivo.

> ![A screen shot of a computer program Description automatically
> generated](./media/image30.png)

13. Cierre la pestaña **Visual Studio Code**. Seleccione **Sync** cuando
    se le pide sincronizar los cambios.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

14. Seleccione **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

15. Cuando aparece la página, presione el **F12** key para mostrar los
    browser developer tools.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

16. Seleccione la pestaña **Console**.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

17. Verifique que el console output contiene los mismos datos
    recuperados anteriormente, salvo que ahora se ve como transformed.

> ![A screenshot of a computer program Description automatically
> generated](./media/image36.png)

18. EL data structure ahora está preparado para plotting. Asigne los
    labels adecuados a data points:

    - **name** - Company name

    &nbsp;

    - **x** - Number of employees

    &nbsp;

    - **y** - Company revenue in thousands

    &nbsp;

    - **z** - Revenue for each employee (calculated)

### **Tarea 6: Agregue external library functionality**

Este ejercicio usa Highcharts.js library (gratis para el uso personal o
no lucrativo) para crear un bubble chart en función de los datos.

1.  Cambie a design studio.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

2.  Seleccione el page footer y seleccione **Edit code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

3.  En el diálogo pop-up, seleccione **Open Visual Studio Code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

4.  Agregue el siguiente código al final del archivo.

> \<script src="https://code.highcharts.com/highcharts.js"\>\</script\>
>
> \<script
> src="https://code.highcharts.com/highcharts-more.js"\>\</script\>
>
> ![](./media/image40.png)

5.  Presione el **Ctrl + S** keyboard shortcut (**⌘ + S** en Mac) para
    guardar el archivo.

6.  Cierre la pestaña **Visual Studio Code**.

7.  Seleccione **Edit code** en el toolbar para abrir Visual Studio Code
    para la página.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  Seleccione **Open Visual Studio Code** en Edit in Visual Studio Code
    for the Web pop-up.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

9.  Seleccione el **Chart.en-US.customjs.js** file.

> ![A screen shot of a computer program Description automatically
> generated](./media/image42.png)

10. Reemplace el archivo para cambiar la función **makeChart** así:

> Ojo: Aquí, reemplazar el archivo significa modificar el archivo
> existente.
>
> function makeChart(data) {
>
> console.log(data);
>
> var rData = data.value.map(({
>
> name,
>
> revenue,
>
> numberofemployees
>
> }) =\> ({
>
> "x": numberofemployees,
>
> "y": revenue,
>
> "z": (!revenue) ? 1 : numberofemployees / revenue,
>
> "name": name
>
> }));
>
> console.log(rData);
>
> // new code to plot the data
>
> Highcharts.chart($('.mychart')\[0\], {
>
> title: {
>
> text: "Customers efficiency"
>
> },
>
> legend: {
>
> enabled: false
>
> },
>
> xAxis: {
>
> title: {
>
> text: "Number of employees"
>
> }
>
> },
>
> yAxis: {
>
> title: {
>
> text: "Turnover ($K)"
>
> }
>
> },
>
> tooltip: {
>
> pointFormat: '\<strong\>{point.name}\</strong\>\<br/\>Employed:
> {point.x}\<br\>Turnover ($K): ${point.y}',
>
> headerFormat: ''
>
> },
>
> series: \[{
>
> type: 'bubble',
>
> data: rData
>
> }\]
>
> });
>
> }
>
> // retrieve accounts data using portals Web API
>
> $(document).ready(function() {
>
> $.get('/\_api/accounts?$select=name,numberofemployees,revenue',
> makeChart, 'json');
>
> });
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image43.png)

11. Presione el **Ctrl + S** keyboard shortcut (**⌘ + S** en Mac) para
    guardar el archivo.

12. Seleccione el **Chart.en-US.webpage.copy.html** file.

> ![A screenshot of a computer program Description automatically
> generated](./media/image44.png)

13. Inserte el siguiente code in el elemente \<div\> interior:

> \<figure\>
>
> \<div class="mychart"\>\</div\>
>
> \</figure\>
>
> ![A screen shot of a computer Description automatically
> generated](./media/image45.png)

14. Presione **Ctrl + S** keyboard shortcut (**⌘ + S** en Mac) para
    guardar el archivo.

15. Cierre la pestaña **Visual Studio Code** y seleccione **Sync** para
    sincronizar los cambios.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

16. Seleccione **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

17. El output ahora debe incluir el bubble chart. Flote su cursor sobre
    las burbujas para verificar los datos.

> ![A screenshot of a search engine Description automatically
> generated](./media/image48.png)

**Resumen:** En este laboratorio, ha aprendido a agregar JavaScript code
a una página para renderizar los daos de Microsoft Dataverse como un
gráfico con un external charting library con los datos recuperados de
Dataverse mediante los portals Web API.
