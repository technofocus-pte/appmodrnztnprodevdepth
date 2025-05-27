**Laboratorio 3 - Instale y use los developer tools**

**Duración estimada:** 15 minutos

**Objetivo:** En este laboratorio, aprendera a instalar unos developer
tools desde NuGet.

**Tarea 1: Instale los developer tools**

En esta tarea, usará un Power Platform CLI para instalar las
herramientas.

1.  Para iniciar **Command Prompt**, vaya al menú **Start** del VM,
    tecle Command Prompt en el search box y seleccione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Ejecute el siguiente command para instalar el **Configuration
    Manager Tool**.

> +++pac tool cmt+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Se debería instalar e iniciar Configuration Manager Tool. Cierre el
    Configuration Manager Tool.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Ejecute el siguiente command para instalar el **Package Deployer
    Tool**.

> +++pac tool pd+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Se debe instalar e iniciar Package deployer tool. Cierre el Package
    Deployer Tool.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Ejecute el siguiente command para instalar el **Plugin Registration
    Tool**.

> +++pac tool prt+++
>
> ![](./media/image6.png)

7.  Se debe instalar e iniciar Plugin Registration. No cierre el Plugin
    Registration Tool.

> ![](./media/image7.png)

**Tarea 2: Explore un plug-in registrado con el plug-in registration
tool**

1.  Seleccione **Create New Connection.**

> ![](./media/image8.png)

2.  Seleccione la casilla **Display list of available organizations**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  Seleccione **Login.** 

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Inicie sesión con sus Dataverse environment credentials, o sea,
    Office 365 Admin credentials. Haga clic en **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  Introduzca su Admin tenant password y haga clic en **Sign in**.

> ![A screenshot of a login box Description automatically
> generated](./media/image12.png)

6.  En este caso, puede ver que el **Dev One** environment ya está
    seleccionado. En el caso de que aparezca una lista de entornos,
    elija su entorno – **Dev One** y seleccione **Login** de nuevo.

> ![](./media/image13.png)

7.  Verá una lista de system plug-ins. Si tiene plugins personalizados
    en su entorno, también los verá en la lista. Los (Assembly) son los
    .NET DLLs que implementan los plug-ins.

> **Ojo:** Tiene que expandir la sección para ver la lista completa.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

8.  Ubique **Microsoft.CDS.DataLakeDataProvider.Plugins** y expándalo.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

9.  Cada uno de los elementos secundarios se implementan en el conjunto.
    Expanda uno de los elementos para ver los step registrations para
    dicho plug-in.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

10. Step registration conecta al plug-in como el event handler al
    evento. En el ejemplo anterior, está gestionando un create en la
    tabla insightsstorevirtualentity.

> ![](./media/image17.png)

11. Haga doble clic en cualquier paso para ver los detalles de step
    configuration incluyendo el mensaje y la entidad en la que está
    registrado, la etapa del pipeline en la que se invocará el plugin,
    si la ejecución es sincrónica o asincrónica, etc.

> ![](./media/image18.png)

**Resumen:** En este laboratorio, ha aprendido a instalar los developer
tools. Cuando crea su propio plug-in personalizado, usará Plugin
Registration Tool para cargar el assembly y registrar los pasos de los
eventos que quiere manejar.
