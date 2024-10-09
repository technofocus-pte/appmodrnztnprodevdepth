# **Lab 2: Use the Power Apps CLI and create Power Apps Component Framework (PCF)** 

**Estimated Duration:** 30 min

**Objective:** In this lab, you will learn to install the Power Platform
Tools and create your first Power Apps Component Framework (PCF)
component.

### **Task 1: Install the Power Platform Tools**

1.  Open Visual Studio Code using the shortcut present on VM’s Desktop,
    select the **Extensions** icon in the navigation bar.

     ![A screenshot of a computer program Description automatically generated](./media/image1.png)

2.  Search for +++**power platform tools**+++. Select
    the **Install** button in the search results.

     ![A screenshot of a computer Description automatically generated](./media/image2.png)

3.  Wait till the installation is complete.

     ![A screenshot of a computer Description automatically generated](./media/image3.png)

4.  Select **more option (…),** **Terminal** and then select **New
    Terminal**.

 > **Note:** If you don’t see (… 3 dots), select **hamburger | Terminal | New Terminal.**

 ![](./media/image4.png)

 ![](./media/image5.png)

5.  Run the pac command to see what commands are available:

     +++pac+++

     ![A black screen with white text and red rectangle with yellow and black text Description automatically generated](./media/image6.png)

     ![](./media/image7.png)

     ![Screenshot showing a list of commands.](./media/image8.png)

6.  You can enter pac and then a command to see what options it has, for
    example, try the following:

     +++pac admin+++

     ![](./media/image9.png)

> **Note:** If you see the pop-up saying, ‘Some keybindings don’t got to
> the terminal by default and are handled by Visual Studio Code
> instead’, then select **Configure Terminal Settings**.

 ![A black background with white text Description automatically generated](./media/image10.png)

7.  You can see, what options admin has.

     ![](./media/image11.png)

8.  Navigate to Power Apps maker portal
    using +++**https://make.powerapps.com/**+++ and make sure you have the **Dev
    One** environment selected.

9.  In the upper right corner of the screen, select
    the **Settings** icon and choose **Session details**.

     ![](./media/image12.png)

10. In the Power Apps session details dialog, select **Instance
    url** value and copy it for use later in the exercise.

     ![A screenshot of a computer Description automatically generated](./media/image13.png)

11. Go back to the Visual Studio Code terminal, type the following
    command to establish a connection from the CLI and sign into your
    test environment when prompted.

     +++pac auth create --name Lab --url **\<Your Instance URL\>**+++

     ![](./media/image14.png)

12. Sign in with your M365 Admin credentials.

     ![A screenshot of a computer Description automatically generated](./media/image15.png)

13. Enter the **password** and click on **Sign in**.

     ![A screenshot of a login page Description automatically generated](./media/image16.png)

14. You can see the message that authentication is done successfully.

     ![A screenshot of a computer program Description automatically generated](./media/image17.png)

15. Type the following who command that will display the environment and
    the user information. This is good to ensure you are in the correct
    environment.

     +++pac org who+++

     ![A screenshot of a computer Description automatically generated](./media/image18.png)

### **Task 2: Create a PCF component**

1.  Run the command below to create a new folder named **labPCF** inside
    your user's folder.

     +++md labPCF+++

     ![](./media/image19.png)

2.  You can see that the labPCF folder has created.

     ![A screenshot of a computer Description automatically generated](./media/image20.png)

3.  Change directory to the folder you created.

     +++cd labPCF+++

     ![A black and white image of a person's hand Description automatically generated](./media/image21.png)

4.  Run the command below to initialize the component project.

     +++pac pcf init --namespace lab --name FirstControl --template field+++

     ![A screen shot of a computer Description automatically generated](./media/image22.png)

5.  Type the following command and then press enter. This pulls down any
    dependencies from the npm repository.

     +++npm install+++

     ![](./media/image23.png)

6.  If you are asked to update the npm, use the given command as shown
    in the below image. In this case, npm install -g npm@10.8.2 is used.

     ![](./media/image24.png)

7.  Open the folder in Visual Studio Code using the following command.

     +++code .+++

8.  If you come across a pop-up saying. Do you trust the authors of the
    file then click **Yes, I thrust the authors**.

     ![](./media/image25.png)

9.  If you are asked to choose color theme, click on Brows Color Themes
    otherwise, ignore this and next step.

     ![](./media/image26.png)

10. Select **Dark Modern** color theme.

     ![](./media/image27.png)

11. Explore the files that have been created.

12. Expand **FirstControl** folder and select **Index.ts**.

     ![](./media/image28.png)

> **Note:** On the pop-up asking, ‘Do you want to allow untrusted files in this window’, select **Allow**.

 ![A screenshot of a computer error Description automatically generated](./media/image29.png)

13. Paste the following two variables inside the export.

     ![A screen shot of a computer Description automatically generated](./media/image30.png)

14. Paste the following inside the **init()** function to create the
    HTML controls and set the label value.

     +++this.label = document.createElement("input");+++

     +++this.label.setAttribute("type", "label");+++

     +++this.label.value = "My First PCF";+++

     +++this.\_container = document.createElement("div");+++

     +++this.\_container.appendChild(this.label);+++

     +++container.appendChild(this.\_container);+++

     ![A screenshot of a computer program Description automatically generated](./media/image31.png)

15. To save the file, go to **File** tab and select **Save**.

     ![A screenshot of a computer program Description automatically generated](./media/image32.png)

16. Go to the terminal and input the following command and then enter.
    This will start the test harness with the latest code as shown in
    the thisrd screenshot of this step.

     +++npm start+++

     ![](./media/image33.png)

> **Note:** If you receive message as Windows Defender Firewall has
> blocked some features, select Allow access.

     ![A screenshot of a computer security alert Description automatically generated](./media/image34.png)

     ![A screenshot of a computer Description automatically generated](./media/image35.png)

17. The test harness is effective to use early in the project to see
    what your control looks like visually without having to deploy it to
    an environment. You can set values of property to change the size of
    the control area. After you're done exploring the test harness,
    switch back to the terminal and press Ctrl-C to terminate the
    execution of the test harness.

     ![A screenshot of a computer program Description automatically generated](./media/image36.png)

18. Type **Y** and \[ENTER\].

     ![](./media/image37.png)

19. Run the following command to list solutions in your environment.

     +++pac solution list+++

     ![A screenshot of a computer Description automatically generated](./media/image38.png)

20. These are the current solutions that are in your environment. The
    next step will add one for the component.

     ![A screenshot of a computer Description automatically generated](./media/image38.png)

21. Type the following push command to push our control to the
    environment.

     +++pac pcf push --publisher-prefix lab+++

     ![A screenshot of a computer program Description automatically generated](./media/image39.png)

### **Task 3: Use the component in an app** 

1.  Navigate to the Microsoft Power Platform Admin Center using
    +++**https://admin.powerplatform.microsoft.com/home**+++.

2.  Close the welcome window.

     ![](./media/image40.png)

3.  Select the **Dev One** environment you're using for the lab.

     ![](./media/image41.png)

4.  Select **Settings**.

     ![A screenshot of a computer Description automatically generated](./media/image42.png)

5.  Expand **Product** area and select **Features**.

     ![A screenshot of a computer Description automatically generated](./media/image43.png)

6.  On the right side, enable the **Allow publishing of canvas apps with
    code components** feature.

     ![A screenshot of a computer Description automatically generated](./media/image44.png)

7.  Select **Save** at the bottom.

     ![](./media/image45.png)

8.  Navigate to Power Apps maker
    portal using
    +++**https://make.powerapps.com/**+++ and make sure you are in the
    correct environment i.e. **Dev One**.

     ![A screenshot of a computer Description automatically generated](./media/image46.png)

9.  Select **Solutions** from the left navigation pane, and then select
    **Import solution**.

     ![](./media/image47.png)

10. Select **Browse** on Import a solution dialog.

     ![A white background with black text Description automatically generated](./media/image48.png)

11. Select zip file of the solution from the path -
    labPCF\obj\PowerAppsToolsTemp_lab\bin\Debug and then select
    **Open**.

     ![A screenshot of a computer Description automatically generated](./media/image49.png)

12. After importing zip file, click on **Next**.

     ![](./media/image50.png)

13. Select **Import**.

     ![A screenshot of a computer Description automatically generated](./media/image51.png)

14. Wait till message which states, Solution
    “**PowerAppsToolsTemp_lab**” imported successfully appears.

     ![](./media/image52.png)

15. Double click on the newly imported solution - **PowerAppsTools_lab**
    to open it.

     ![](./media/image53.png)

16. You should see your component listed.

     ![A screenshot of a computer Description automatically generated](./media/image54.png)

17. Select **+ New | App | Canvas app**.

     ![](./media/image55.png)

18. Select **Phone** for Format, enter **First PCF** for App name, and
    select **Create**.

     ![A screenshot of a computer Description automatically generated](./media/image56.png)

19. Select **Skip** on the welcome window.

     ![](./media/image57.png)

20. On the left pane, select **Add (+)**, and then select **Get more
    components** icon situated above the list of Popular components and
    below the search box as shown in the following image.

     ![A screenshot of a computer Description automatically generated](./media/image58.png)

21. Select the **Code** tab.

     ![A screenshot of a computer Description automatically generated](./media/image59.png)

22. Select your component – **FirstControl**. Select **Import**.

     ![](./media/image59.png)

23. On the left tool bar, select **+** and expand **Code components**.

     ![](./media/image60.png)

24. Select the **FirstControl**. You should now see the control with the
    text **My First PCF** on the canvas.

     ![](./media/image61.png)

25. Select **Save** to save the application.

     ![A screenshot of a computer Description automatically generated](./media/image62.png)

You have now built your first PCF component and used it in a canvas app.

**Summary:** In this lab, you have learnt how build to your first PCF
component and used it in a canvas app. Power Apps component framework
creates code components for model-driven and canvas apps. These code
components can be used to enhance the user experience for users working
with data on forms, views, dashboards, and canvas app screens.
