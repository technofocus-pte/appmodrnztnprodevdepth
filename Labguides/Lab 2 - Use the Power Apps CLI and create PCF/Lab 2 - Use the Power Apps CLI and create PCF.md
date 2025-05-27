# **Laboratorio 2: Use el Power Apps CLI y cree Power Apps Component Framework (PCF)** 

**Duración estimada:** 30 minutos

**Objetivo:** En este laboratorio, aprenderá a instalar Power Platform
Tools y cree su primer componente Power Apps Component Framework (PCF).

## **Tarea 1: Instale el Power Platform Tools**

1.  Abra Visual Studio Code mediante el acceso directo en el Desktop VM,
    seleccione el ícono **Extensions** en la barra de navegación.

> ![A screenshot of a computer program Description automatically
> generated](./media/image1.png)

2.  Busque +++**power platform tools**+++. Seleccioneel
    botón **Install** en los resultados de búsqueda.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Espere a que se complete la instalación.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Seleccione **más opciones (…),** **Terminal** y seleccione **New
    Terminal**.

> **Ojo:** Si no ve (… 3 puntos), seleccione **tres líneas | Terminal |
> New Terminal.**
>
> ![](./media/image4.png)
>
> ![](./media/image5.png)

5.  Ejecute el pac command para ver cúales commands están disponibles:

> +++pac+++
>
> ![A black screen with white text and red rectangle with yellow and
> black text Description automatically generated](./media/image6.png)
>
> ![](./media/image7.png)
>
> ![Screenshot showing a list of commands.](./media/image8.png)

6.  Puede introducir pac y un command para ver cúales opciones hay, por
    ejemplo, pruebe lo siguiente:

> +++pac admin+++
>
> ![](./media/image9.png)
>
> **Ojo:** Si ve un popup diciendo, ‘Some keybindings don’t got to the
> terminal by default and are handled by Visual Studio Code instead’,
> pues seleccione **Configure Terminal Settings**.
>
> ![A black background with white text Description automatically
> generated](./media/image10.png)

7.  Puede ver cúales opciones admin tiene.

> ![](./media/image11.png)

8.  Navegue a Power Apps maker portal
    mediante <https://make.powerapps.com/> y asegúrese de tener
    seleccionado el **Dev One** environment.

9.  En la esquina superior derecha de la pantalla, seleccione el
    ícono **Settings** y elija **Session details**.

> ![](./media/image12.png)

10. En el diálogo Power Apps session details, seleccione el
    valor **Instance url** y copie para usarlo más tarde en el
    ejercicio.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. Vuelva al Visual Studio Code terminal, tecle el siguiente command
    para establecer una conexión del CLI e inicie sesión en su test
    environment cuando se le pide.

> +++pac auth create --name Lab --url **\<Your Instance URL\>**+++
>
> ![](./media/image14.png)

12. Inicie sesión con sus M365 Admin credentials.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

13. Introduzca la **contraseña** y haga clic en **Sign in**.

> ![A screenshot of a login page Description automatically
> generated](./media/image16.png)

14. Puede ver el mensaje de que la autenticación fue exitosa.

> ![A screenshot of a computer program Description automatically
> generated](./media/image17.png)

15. Tecle el siguiente who command que mostrará su entorno y el user
    information. Esto sirve para asegurar si está en el entorno
    correcto.

> +++pac org who+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

## **Tarea 2: Cree un PCF component**

1.  Ejecute el siguiente command para crear una nueva carpeta
    llamada **labPCF** dentro de la carpeta de su usuario.

> +++md labPCF+++
>
> ![](./media/image19.png)

2.  Puede ver que se ha creado la carpeta labPCF.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

3.  Cambie el directorio a la carpeta que acaba de crear.

> +++cd labPCF+++
>
> ![A black and white image of a person's hand Description automatically
> generated](./media/image21.png)

4.  Ejecute el siguiente command para iniciar el component project.

> +++pac pcf init --namespace lab --name FirstControl --template
> field+++
>
> ![A screen shot of a computer Description automatically
> generated](./media/image22.png)

5.  Tecle el siguiente command y presione enter. Esto elimina las
    dependencias del repositorio npm.

> +++npm install+++
>
> ![](./media/image23.png)

6.  Si se le pide actualizar el npm, use el siguiente command como se ve
    en la imagen. En este caso, se usa npm install -g npm@10.8.2.

> ![](./media/image24.png)

7.  Abra la carpeta en Visual Studio Code con el siguiente command.

> +++code .+++

8.  Si ve un popup diciendo Do you trust the authors of the file, haga
    clic en **Yes, I trust the authors**.

> ![](./media/image25.png)

9.  Si se le pide elegir un color theme, haga clic en Brows Color
    Themes, pero puede ignorar eso y continuar con el siguiente paso.

> ![](./media/image26.png)

10. Seleccione **Dark Modern** color theme.

> ![](./media/image27.png)

11. Explore los archivos que se crearon.

12. Expanda el **FirstControl** folder y seleccione **Index.ts**.

> ![](./media/image28.png)
>
> **Ojo:** En el popup diciendo, ‘Do you want to allow untrusted files
> in this window’, seleccione **Allow**.
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

13. Pegue las siguientes dos variables en el export.

> ![A screen shot of a computer Description automatically
> generated](./media/image30.png)

14. Pegue lo siguiente dentro de la función **init()** para crear los
    controles HTML y establecer el label value.

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
> ![A screenshot of a computer program Description automatically
> generated](./media/image31.png)

15. Para guardar el archivo, vaya a la pestaña **File** y seleccione
    **Save**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image32.png)

16. Vaya al terminal e introduzca el siguiente command y presione enter.
    Esto iniciará un test harness con el code más reciente como se ve en
    la tercera captura de pantalla de este paso.

> +++npm start+++
>
> ![](./media/image33.png)
>
> **Ojo:** Si recibe un mensaje como Windows Defender Firewall has
> blocked some features, seleccione Allow access.
>
> ![A screenshot of a computer security alert Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

17. El test harness es eficaz para usar más temprano en el proyecto para
    ver cómo se ve sin tener que implementarlo en un entorno. Puede
    establecer valores del property para cambiar el tamaño del control
    area. Después de terminar de explorar el test harness, vuelva al
    terminal y presione Ctrl-C para terminar la ejecución del test
    harness.

> ![A screenshot of a computer program Description automatically
> generated](./media/image36.png)

18. Tecle **Y** y presione \[ENTER\].

> ![](./media/image37.png)

19. Ejecute el siguiente command para enlistar soluciones en su entorno.

> +++pac solution list+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

20. Estas son las soluciones actuales en su entorno. El siguiente paso
    añadirá una para el componente.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

21. Tecle el siguiente push command para introducir nuestro control al
    entorno.

> +++pac pcf push --publisher-prefix lab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image39.png)

## **Tarea 3: Use el component en una aplicación** 

1.  Navegue al Microsoft Power Platform Admin Center mediante
    +++<https://admin.powerplatform.microsoft.com/home>+++.

2.  Cierre la ventana welcome.

> ![](./media/image40.png)

3.  Seleccione el **Dev One** environment que está utilizando para el
    laboratorio.

> ![](./media/image41.png)

4.  Seleccione **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

5.  Expanda **Product** y seleccione **Features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

6.  En la parte derecha, habilite el feature **Allow publishing of
    canvas apps with code components**.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

7.  Seleccione **Save** en la parte inferior.

> ![](./media/image45.png)

8.  Navegue a [Power Apps maker portal](https://make.powerapps.com/) con
    +++<https://make.powerapps.com/>+++ y asegúrese de estar en el
    entorno correcto **Dev One**.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

9.  Seleccione **Solutions** desde el panel de navegación izquierdo, y
    seleccione **Import solution**.

> ![](./media/image47.png)

10. Seleccione **Browse** en el diálogo Import a solution.

> ![A white background with black text Description automatically
> generated](./media/image48.png)

11. Seleccione el zip file de la solución desde el path -
    labPCF\obj\PowerAppsToolsTemp_lab\bin\Debug y seleccione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

12. Después de importar el zip file, haga clic en **Next**.

> ![](./media/image50.png)

13. Seleccione **Import**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

14. Espere a que aparece el mensaje, Solution
    “**PowerAppsToolsTemp_lab**” imported successfully.

> ![](./media/image52.png)

15. Haga doble clic en la solución recién importada -
    **PowerAppsTools_lab** para abrirla.

> ![](./media/image53.png)

16. Debería ver su componente enlistado.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

17. Seleccione **+ New | App | Canvas app**.

> ![](./media/image55.png)

18. Seleccione **Phone** como Format, introduzca **First PCF** como App
    name, y seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

19. Seleccione **Skip** en la ventana welcome.

> ![](./media/image57.png)

20. En el panel izquierdo, seleccione **Add (+)**, y luego seleccione el
    ícono **Get more components** encima de la lista de Popular
    components y debajo del search box como se ve en la imagen.

> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

21. Seleccione la pestaña **Code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

22. Seleccione su componente – **FirstControl**. Seleccione **Import**.

> ![](./media/image59.png)

23. En la barra izquierda, seleccione **+** y expanda **Code
    components**.

> ![](./media/image60.png)

24. Seleccione **FirstControl**. Ahora debería ver el control con el
    texto **My First PCF** en el canvas.

> ![](./media/image61.png)

25. Seleccione **Save** para guardar la aplicación.

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

Ha construido su primer PCF component y lo ha usado en un canvas app.

**Resumen:** En este laboratorio, ha aprendido a construir su primer PCF
component y lo ha usado en un canvas app. Power Apps component framework
crea los code components para aplicaciones canvas y basadas en modelos.
Estos code components se pueden usar a mejorar la experiencia del
usuario que trabaja con los datos en formularios, visualizaciones,
dashboards y pantallas de canvas apps.
