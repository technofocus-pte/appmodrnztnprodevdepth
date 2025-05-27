**Laboratorio 5: Cree un custom API**

**Duración estimada:** 35 minutos

**Objetivo:** En este laboratorio, aprenderá a construir un Dataverse
custom API para ejecutar un logic personalizado. Usará un API
personalizado en un paso en un Power Automate flow.

**Tarea 1: Cree un API project personalizado**

1.  Haga clic en el **Start** menu del VM, tecle Command Prompt en el
    search box y seleccione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Ejecute el siguiente commad para crear una nueva carpeta
    llamada **CustomAPILab**.

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  Cambie el directory a la carpeta que acaba de crear.

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  Debe estar en la carpeta CustomAPIlAB. Ejecute el siguiente command
    para iniciar un nuevo Dataverse plugin class library.

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Dataverse plugin class library creation debería haber completado de
    forma exitosa.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Jecute el siguiente command para abrir el proyecto en Visual Studio.

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  Si se le pide, seleccione **Microsoft Visual Studio 2022** y
    seleccione **Just once**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  Si le pide iniciar sesión en Visual Studio, seleccione **Skip this
    for now** en la página sign in.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  Seleccione **General** como Development settings elija **Dark** como
    el color theme y seleccione **Start Visual Studio**.

> **Ojo:** Ignore este paso si ya está en el proyecto.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. Se debe abrir el proyecto en Visual Studio.

> ![](./media/image10.png)

11. Haga clic derecho en Plugin1.cs file y renombre
    como **MatchPlugin.cs**.

> ![](./media/image11.png)

12. Seleccione **Yes** para el diálogo You are renaming a file.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Haga clic derecho en el CustomAPILab Project y seleccione **Manage
    NuGet Packages**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. Busque **System.Text.RegularExpressions** y seleccione **Install**.

> ![](./media/image14.png)

15. En la ventana Preview changes, seleccione **Apply** para permitir
    que Visual Studio haga cambios a la solución.

> ![](./media/image15.png)

16. Seleccione **I Accept** para aceptar los license terms.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17. Abra el **MatchPlugin.cs** file.

> ![](./media/image17.png)

18. Agregue el siguiente statement debajo de ‘using System;’ statement
    i.e. en la línea 3.

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. Agregue las siguientes líneas dentro del ExecuteDataversePlugin
    method y después de var context line. Estas líneas obtienen el valor
    del input parameters introducidos en API invocation personalizado.

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. Agregue la siguiente línea para obtener el service.

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. Agregue la siguiente línea para escribir el input value en trace.

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. Agregue la siguiente línea para llamar el Regex.Match method.

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. Escriba el result para trace.

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. Y finalmente, agregue la siguiente línea para establecer el output
    parameter Matched.

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. Su execute method se debe ver así.

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. Seleccione **Build | Build Solution**.

> ![](./media/image26.png)

27. Se debe haber construido el proyecto.

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**Tarea 2: Registre el API plugin personalizado**

1.  Abra command prompt y ejecute el siguiente command para iniciar
    Plugin Registration Tool.

> +++pac tool prt+++
>
> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  Seleccione **+ Create New Connection**.

> ![](./media/image29.png)

3.  Seleccione **Office 365**, proporcione sus credenciales y
    seleccione **Login**.

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  Inicie seción **M365 Admin tenant Id** y seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Introduzca su contraseña **M365 Admin tenant Id** y seleccione
    **Sign in**.

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  Averigüe que está seleccionado **Dev One** environment.

7.  Elija **Register | Register New Assembly**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  Seleccione ... en Step 1 y navegue a la
    carpeta **CustomAPILab\bin\Debug\net462**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  Seleccione **CustomAPILab.dll** y seleccione **Open**.

> ![](./media/image35.png)

10. Seleccione **Register Selected Plugins**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. Seleccione **OK** al mensaje de éxito. Su plugin está listo para
    conectar al custom API que vamos a crear en la próxima tarea.

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**Tarea 3: Cree el custom API**

1.  Navegue al Power Apps maker portal
    en +++<https://make.powerapps.com/>+++ y asegúerese que esté en
    **Dev One** environment.

2.  Seleccione **Solutions** en la navegación izquierda. Seleccione **+
    New Solution**.

> ![](./media/image38.png)

3.  Introduzca +++**Custom API Lab**+++ en el Display Name.

4.  Seleccione **CDS Default Publisher** en el menu de Publisher.

5.  Seleccione **Create**. Esto crea una solución personalizada que
    contenga nuestros componentes.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Seleccione **+ New | More | Other | Custom API.**

> ![](./media/image40.png)

7.  Introduzca la siguiente información:

    - **Unique Name:** +++contoso_match+++

    &nbsp;

    - **Name**: +++Match+++

    &nbsp;

    - **Display Name:** +++Match+++

    &nbsp;

    - **Description**: +++Match a string+++

    &nbsp;

    - **Binding Type**: +++Global+++

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  En Plugin Type seleccione el ícono de búsqueda y ubique su plugin -
    **CustomAPILab.MatchPlugin**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  Seleccione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. Seleccione **Done**.

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11. Seleccione **+** **New | More| Other | Custom API Request
    Parameter**.

> ![](./media/image44.png)

12. Para **Custom API**, seleccione el ícono **Search** y
    seleccione **Match** (su Custom API).

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. Introduzca +++**StringIn**+++ para Unique Name, Name, Display Name y
    Description para sencillez.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. Seleccione **String** para Type.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. Seleccione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. Seleccione **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. Para añadir otro, Custom API Request Parameter,
    Seleccione **+** **New | More| Other | Custom API Request
    Parameter**.

> ![](./media/image50.png)

18. Para **Custom API**, seleccione el ícono **Search** y
    seleccione **Match** (su Custom API).

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. Introduzca **Pattern** para Unique Name, Name, Display Name y
    Description para sencillez.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. Seleccione **String** para Type.

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. Seleccione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. Seleccione **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. Seleccione **New | More | Other| Custom API Response Property**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. Para **Custom API**, seleccione el ícono **Search** y
    seleccione **Match** (su Custom API).

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. Introduzca +++**Matched**+++ como **Unique Name**, **Name, Display
    Name** y **Description** para sencillez.

26. Seleccione **Boolean** para **Type**.

> ![](./media/image58.png)

27. Seleccione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. Seleccione **Done**.

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. Su solution component list se debe ver así.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**Tarea 4: Use el custom API de Power Automate**

1.  En la solución, seleccione **+ New | Automation | Cloud Flow |
    Instant**.

> ![](./media/image62.png)

2.  Introduzca +++**String match**+++ para Flow name,
    seleccione **Manually trigger a flow** trigger, y
    seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  Seleccione el **+ New Step**.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  Busque perform y elija **Perform an unbound action**.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  En Action Name list, ubique y seleccione **contoso_match**.

> ![](./media/image66.png)

6.  Introduzca el **myemail@outlook.com** email address en **StringIn**.
    Aquí, puede teclar cualquier email address sencillo.

> ![](./media/image67.png)

7.  Introduzca el siguiente following Regular expression en Pattern.
    Esto es un email pattern sencillo. Están disponibles
    otros [*examples*](https://regexlib.com/DisplayPatterns.aspx/).

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  Se debe ver su flow así.

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  Seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. Después de que se guarde, seleccione **Test**.

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. Seleccione **Manually**, y seleccione **Test**.

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. Seleccione **Run flow**.

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. Seleccione **Done**.

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. Después de que complete el flow, seleccione el **Perform an unbound
    action** para expandir y ver resultados.

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**Resumen:** En este laboratorio, ha aprendido a construir un custom
action y usarlo en un Power Automate flow. El custom API action
contoso_match también está disponible para llamar directamente mediante
el platform API.
