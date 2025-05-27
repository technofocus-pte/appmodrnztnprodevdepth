**Laboratorio 6 – Escriba su primer plug-in**

**Duración estimada:** 30 minutos

**Objetivo:** en este escenario, una organización necesita asegurar que
los datos de número de teléfono se entran en un formato consistente.
Para lograr este objetivo, va a crear un plug-in para ejecutar en
create/update que filtra todas las letras que no son números desde un
número de teléfono antes de guardar en Dataverse.

En este laboratorio, aprenderá a crear un plug-in que se ejecuta en
create y update. Este plug-in filtra todas las letras que no son números
desde un número de teléfono.

**Tarea 1: Cree una nueva solución y un model-driven app**

1.  Navegue a [Power Apps](https://make.powerapps.com/) en
    +++<https://make.powerapps.com/>+++. Asegure que está en **Dev One**
    environment.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  En la navegación izquierda, seleccione **Solutions** y
    seleccione **New solution**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  En el diálogo emergente, especifique **Display name** – +++Plugin
    Lab+++, **Name** – +++PluginLab+++, **Publisher** – CDS Default
    publisher y seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Para crear un nuevo model-driven app en su solución,
    seleccione **New** | **App** | **Model-driven app**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Dé un **Name** a su model -driven app como +++**Fundraiser**+++ y
    seleccione **Create**.

> ![](./media/image5.png)

6.  En el model driven app, seleccione **+Add page**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  Seleccione **Dataverse table** en el pop-up que aparece.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  Seleccione **Contact** table y seleccione **Add**.

> ![](./media/image8.png)
>
> **Ojo:** para este laboratorio, vamos a usar Contact table.

9.  Ahora, está listo model-driven app que se llama ‘Funraiser’.

> ![](./media/image9.png)

10. Seleccione **Save** desde la esquina superior derecha.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

11. Seleccione **Publish**.

> ![A purple and white rectangle Description automatically
> generated](./media/image11.png)

12. Haga clic en **back arrow** para volver a su solución.

> ![A screenshot of a browser Description automatically
> generated](./media/image12.png)

13. Haga clic en **back arrow** y va a estar en la página de solución
    donde están todas las soluciones.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

**Tarea 2: Cree un plug-in**

1.  Inicie **Visual Studio 2022**. Para abrirlo, haga clic en Start menu
    del VM, tecle Visual Studio en el search box y seleccione **Open**.

> ![](./media/image14.png)

2.  Seleccione **File | New | Project**.

> ![](./media/image15.png)

3.  Seleccione **Class Library (.NET Framework)** y seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  Introduzca **D365PackageProject** para **Project Name**, seleccione
    una ubicación para guardar el proyecto,

> ![](./media/image17.png)

5.  Seleccione **.NET Framework 4.7.1** para **Framework**, y
    seleccione **Create**.

> ![](./media/image18.png)

6.  Haga clic derecho en el proyecto y seleccione **Manage NuGet
    Packages**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

7.  Seleccione la pestaña **Browse**, busque y
    seleccione **microsoft.crmsdk.coreassemblies**, y
    seleccione **Install**.

> ![](./media/image20.png)

8.  En la ventana Preview changes, seleccione **Apply** para permitir
    que Visual Studio haga cambios a la solución.

> ![A screenshot of a computer program Description automatically
> generated](./media/image21.png)

9.  Seleccione **I Accept** para aceptar los license terms.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. Cierre el NuGet package manager.

> ![A screenshot of a computer program Description automatically
> generated](./media/image23.png)

11. Haga clic derecho en **Class1.cs** y **Delete**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

12. Seleccione **OK** para eliminar Class1.cs permanentemente.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

13. Haga clic derecho en el proyecto y seleccione **Add | Class**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

14. Nombre el nuevo class **PreOperationFormatPhoneCreateUpdate** y
    seleccione **Add**.

> ![](./media/image27.png)

15. Agregue los using statements al nuevo class así:

> using Microsoft.Xrm.Sdk;
>
> using System.Text.RegularExpressions;
>
> ![](./media/image28.png)

16. Para hacer el class **public**, reemplace el internal by public y
    tecle**:** **IPlugin** al final de este paso para agregar IPlugin
    interface como se ve aquí en la imagen.

> ![A screenshot of a computer program Description automatically
> generated](./media/image29.png)

17. Flote el mouse sobre el IPlugin interface, haga clic en el ícono
    quick action que aparece y seleccione **Implement interface**.

> ![](./media/image30.png)
>
> Su class ahora se debe ver así.
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image31.png)

**Tarea 3: Formatee un número de teléfono**

1.  Obtenga el execution context desde el service provider. Reemplace el
    exception en el Execute method con el siguiente snippet.

> IPluginExecutionContext context =
>
> (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
>
> ![](./media/image32.png)

2.  Averigüe el the input parameter para Target. Agregue el siguiente
    snippet para ejecutar el Execute method.

> if (!context.InputParameters.ContainsKey("Target"))
>
> throw new InvalidPluginExecutionException("No target found");
>
> ![](./media/image33.png)

3.  Agregue el siguiente snippet al Execute method. Este snippet
    obtendrá el target entity desde el input parameter y luego averigüe
    si sus atributos contienen telephone1 (Business Phone for Contacts,
    Phone for Accounts).

> var entity = context.InputParameters\["Target"\] as Entity;
>
> if (!entity.Attributes.Contains("telephone1"))
>
> return;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image34.png)

4.  Agregue el siguiente snippet al Execute function. Este snippet
    eliminará todas las letras que no son números desde un número de
    teléfono.

> string phoneNumber = (string)entity\["telephone1"\];
>
> var formattedNumber = Regex.Replace(phoneNumber, @"\[^\d\]", "");
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image35.png)

5.  Establezca telephone1 al número de teléfono formateado. Agregue el
    siguiente snippet al Execute method.

> entity\["telephone1"\] = formattedNumber;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image36.png)
>
> El Execute method ahora se debe ver así.
>
> ![Screenshot of the execute method.](./media/image37.png)

6.  Haga clic derecho en el proyecto y seleccione **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

7.  Seleccione la pestaña **Signing** y seleccione \<**New…\>** Key
    File.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

8.  Introduzca +++**contoso.snk**+++ en el campo **Key file name**,
    vacíe el **Protect my key file with a password** check box, y
    seleccione **OK**.

> ![](./media/image40.png)

9.  Cierre la pestaña **Properties**.

> ![](./media/image41.png)

10. Seleccione la pestaña **Build** y haga clic en **Build Project**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image42.png)

11. Asegúrese de que la compilación se realice correctamente.

> ![A screenshot of a video game Description automatically
> generated](./media/image43.png)

**Tarea 4: Registre un plug-in y los pasos**

1.  Vaya al menú **Start** del VM, tecle plug-in registration tool en el
    search box y haga clic en **Open**.

> ![](./media/image44.png)

2.  Seleccione **Create New Connection**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

3.  Seleccione **Office 365,** seleccione el **Show Advanced** check
    box, en el campo Online Region, seleccione **Don’t Know**,
    proporcione sus credenciales (M365 Admin tenant), y
    seleccione **Login**.

> ![](./media/image46.png)

4.  Seleccione **Register** y seleccione **Register New Assembly**.

> ![](./media/image47.png)

5.  Seleccione **...** en Step 1 y navegue a la carpeta **Bin |
    Debug** del class library que creó.

> ![A white background with black text Description automatically
> generated](./media/image48.png)

6.  Seleccione **D365PackageProject.dll**, y seleccione **Open**.

> ![](./media/image49.png)

7.  Seleccione **Register Selected Plugins**.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  Seleccione **OK**.

> ![](./media/image51.png)

9.  Expanda el assembly nueva registrada – **(Assembly)
    D365PackageProject**.

> ![](./media/image52.png)

10. Haga clic derecho en el plug-in y seleccione **Register New Step**.

> ![](./media/image53.png)

11. Seleccione **Create** para **Message** y seleccione **contact** para
    **Primary Entity**.

> ![](./media/image54.png)

12. Seleccione **PreOperation** para **Event Pipeline Stage of
    Execution** y luego seleccione **Register New Step**.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

13. Seleccione **Close** en el Warning page que dice no filters on
    attributes detected.

> ![](./media/image56.png)

14. Si ve un mensaje de error, o sea, Error occurred while registering
    the step, seleccione **No** para ver los detalles.

> ![A screenshot of a computer error Description automatically
> generated](./media/image57.png)

15. Averigüe que, se ha creado el paso create en Plugin.

> ![A red line with black text Description automatically
> generated](./media/image58.png)

16. Haga clic derecho en el plug-in y seleccione **Register New
    Step** de nuevo.

> ![](./media/image59.png)

17. Seleccione **Update** para **Message**,
    seleccione **contact** para **Primary Entity**, y seleccione
    el **Attributes** lookup.

> ![](./media/image60.png)

18. Borre el **Select All** check box, seleccione el **Business
    Phone** check box, y seleccione **OK**.

> ![](./media/image61.png)

19. Seleccione **PreOperation** para **Event Pipeline Stage of
    Execution** y seleccione **Register New Step**.

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

20. Si ve un mensaje de error, o sea, Error occurred while registering
    the step, seleccione **No** para ver los detalles.

> ![A screenshot of a computer error Description automatically
> generated](./media/image57.png)

21. Averigüe que, se ha creado el paso create en Plugin.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

**Tarea 5: Pruebe el plug-in**

1.  Vaya al Maker Portal +++<https://make.powerapps.com/>+++ y asegure
    que está en el **Dev One** environment seleccionado.

2.  Seleccione **Apps** e inicie la aplicación **Fundraiser**.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

3.  Seleccione **+ New**.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

4.  Introduzca +++**Test**+++ para **First
    Name**, +++**Contact**+++ para **Last
    Name**, +++**(123)-555-0100**+++ para **Business Phone**, y
    seleccione **Save**.

> ![A screenshot of a contact form Description automatically
> generated](./media/image66.png)
>
> Se debe guardar el record, y el **Business Phone** debe mostrar solo
> los números.
>
> ![](./media/image67.png)

5.  Cambie el **Business Phone** a **001-123-555-0100** y haga clic en
    **Save**. Se debe actualizar el record, y el **Business Phone** debe
    mostrar sólo los números.

> ![A screenshot of a contact form Description automatically
> generated](./media/image68.png)

**Resumen:** En este laboratorio, ha aprendido cómo crear un plug-in que
se ejecutan en create y update y cómo filtrae todas las letras que no
son números desde un número de teléfono con este plug-in.
