# **Lab 6 - Write your first plug-in using Visual Studio**

**Estimated Duration:** 30 min

**Objective:** In this scenario, an organization needs to ensure that
phone number data is entered in a consistent format. To achieve this
objective, you'll create a plug-in to run on create/update that strips
out all non-numeric characters from a phone number before saving to
Dataverse.

In this lab, you will learn to create a plug-in that will run on create
and update. This plug-in will strip out all non-numeric characters from
a phone number.

### **Task 1: Create a new solution and a model-driven app**

1.  Navigate to Power Apps using
    +++**https://make.powerapps.com/**+++. Make sure you are in **Dev
    One** environment.

     ![A screenshot of a computer Description automatically generated](./media/image1.png)

2.  In the left navigation pane, select **Solutions** and then
    select **New solution**.

     ![A screenshot of a computer Description automatically generated](./media/image2.png)

3.  In the fly-out dialog, specify **Display name** – +++Plugin
    Lab+++, **Name** – +++PluginLab+++, **Publisher** – CDS Default
    publisher and then select **Create**.

     ![A screenshot of a computer Description automatically generated](./media/image3.png)

4.  To create a new model-driven app in your solution,
    select **New** | **App** | **Model-driven app**.

     ![A screenshot of a computer Description automatically generated](./media/image4.png)

5.  Give the **Name** to your model -driven app as +++**Fundraiser**+++
    and then select **Create**.

     ![](./media/image5.png)

6.  In the model driven app, select **+Add page**.

     ![A screenshot of a computer Description automatically generated](./media/image6.png)

7.  Select **Dataverse table** on the pop-up that appears.

     ![A screenshot of a computer Description automatically generated](./media/image7.png)

8.  Select **Contact** table and then select **Add**.

     ![](./media/image8.png)

     **Note:** For this lab, we are using Contact table.

9.  Now, your model-driven app which is named as ‘Funraiser’ is ready.

     ![](./media/image9.png)

10. Select **Save** from the upper right corner.

     ![A screenshot of a computer Description automatically generated](./media/image10.png)

11. Select **Publish**.

     ![A purple and white rectangle Description automatically generated](./media/image11.png)

12. Click on **back arrow** to come back in your solution.

     ![A screenshot of a browser Description automatically generated](./media/image12.png)

13. Click on **back arrow** and you will be on solution page where all
    the solutions are listed.

     ![A screenshot of a computer Description automatically generated](./media/image13.png)

### **Task 2: Create a plug-in**

1.  Start **Visual Studio 2022**. To open that, click on Start menu of
    the VM, type Visual Studio in the search box and select **Open**.

     ![](./media/image14.png)

2.  Select **File | New | Project**.

     ![](./media/image15.png)

3.  Select **Class Library (.NET Framework)** and select **Next**.

     ![A screenshot of a computer Description automatically generated](./media/image16.png)

4.  Enter **D365PackageProject** for **Project Name**, select a location
    to save the project,

     ![](./media/image17.png)

5.  select **.NET Framework 4.7.1** for **Framework**, and then
    select **Create**.

     ![](./media/image18.png)

6.  Right-click the project and select **Manage NuGet Packages**.

     ![A screenshot of a computer Description automatically generated](./media/image19.png)

7.  Select the **Browse** tab, search for and
    select **microsoft.crmsdk.coreassemblies**, and then
    select **Install**.

     ![](./media/image20.png)

8.  On Preview changes window, select **Apply** to allow Visual Studio
    to make changes to the solution.

     ![A screenshot of a computer program Description automatically generated](./media/image21.png)

9.  Select **I Accept** to accept the license terms.

     ![A screenshot of a computer Description automatically generated](./media/image22.png)

10. Close the NuGet package manager.

     ![A screenshot of a computer program Description automatically generated](./media/image23.png)

11. Right-click **Class1.cs** and **Delete**.

     ![A screenshot of a computer Description automatically generated](./media/image24.png)

12. Select **OK** to delete Class1.cs permanently.

     ![A screenshot of a computer Description automatically generated](./media/image25.png)

13. Right-click the project and then select **Add | Class**.

     ![A screenshot of a computer Description automatically generated](./media/image26.png)

14. Name the new class **PreOperationFormatPhoneCreateUpdate** and
    select **Add**.

     ![](./media/image27.png)

15. Add the using statements to the new class as follows:

    ```
     using Microsoft.Xrm.Sdk;

     using System.Text.RegularExpressions;

    ```

     ![](./media/image28.png)

17. To make the class **public**, replace the internal by public and
    type **:** **IPlugin** at the end of the step to add IPlugin
    interface as shown in the below image.

     ![A screenshot of a computer program Description automatically generated](./media/image29.png)

17. Hover the mouse over IPlugin interface, click on the quick action
    icon that appears and then select **Implement interface**.

     ![](./media/image30.png)

     Your class should now look like the following image.

     ![A screen shot of a computer program Description automatically generated](./media/image31.png)

### **Task 3: Format a phone number**

1.  Get the execution context from the service provider. Replace the
    exception in the Execute method with the following snippet.

    ```
    
     IPluginExecutionContext context =
    
     (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

    ```

     ![](./media/image32.png)

2.  Check the input parameter for Target. Add the following snippet to
    the Execute method.

    ```
    
    if (!context.InputParameters.ContainsKey("Target"))

     throw new InvalidPluginExecutionException("No target found");

    ```

     ![](./media/image33.png)

4.  Add the following snippet to the Execute method. This snippet will
    get the target entity from the input parameter and then check if its
    attributes contain telephone1 (Business Phone for Contacts, Phone
    for Accounts).

    ```

    var entity = context.InputParameters\["Target"\] as Entity;

     if (!entity.Attributes.Contains("telephone1"))

     return;

    ```

     ![A screen shot of a computer program Description automatically generated](./media/image34.png)

4.  Add the following snippet to the Execute function. This snippet will
    remove all non-numeric characters from the user-provided phone
    number.

    ```

     string phoneNumber = (string)entity\["telephone1"\];

     var formattedNumber = Regex.Replace(phoneNumber, @"\[^\d\]", "");

    ```

     ![A screen shot of a computer program Description automatically generated](./media/image35.png)

5.  Set telephone1 to the formatted phone number. Add the following
    snippet to the Execute method.

     +++entity\["telephone1"\] = formattedNumber;+++

     ![A screen shot of a computer program Description automatically generated](./media/image36.png)

     The Execute method should now look like the following image.

     ![Screenshot of the execute method.](./media/image37.png)

6.  Right-click the project and select **Properties**.

     ![A screenshot of a computer Description automatically generated](./media/image38.png)

7.  Select the **Signing** tab and select \<**New…\>** Key File.

     ![A screenshot of a computer Description automatically generated](./media/image39.png)

8.  Enter +++**contoso.snk**+++ in the **Key file name** field, clear
    the **Protect my key file with a password** check box, and then
    select **OK**.

     ![](./media/image40.png)

9.  Close the **Properties** tab.

     ![](./media/image41.png)

10. Select **Build** tab and click on **Build Project**.

     ![A screenshot of a computer program Description automatically generated](./media/image42.png)

11. Make sure that the build succeeds.

     ![A screenshot of a video game Description automatically generated](./media/image43.png)

### **Task 4: Register a plug-in and steps**

1.  Go to **Start** menu of the VM, type plug-in registration tool in
    the search box and click **Open**.

     ![](./media/image44.png)

2.  Select **Create New Connection**.

     ![A screenshot of a computer Description automatically generated](./media/image45.png)

3.  Select **Office 365,** select the **Show Advanced** check box, in
    the Online Region field, select **Don’t Know**, provide your
    credentials (M365 Admin tenant), and then select **Login**.

     ![](./media/image46.png)

4.  Select **Register** and then select **Register New Assembly**.

     ![](./media/image47.png)

5.  Select **...** under Step 1 and then browse to the **Bin |
    Debug** folder of the class library that you created.

     ![A white background with black text Description automatically generated](./media/image48.png)

6.  Select **D365PackageProject.dll**, and then select **Open**.

     ![](./media/image49.png)

7.  Select **Register Selected Plugins**.

     ![A screenshot of a computer Description automatically generated](./media/image50.png)

8.  Select **OK**.

     ![](./media/image51.png)

9.  Expand the newly registered assembly – **(Assembly)
    D365PackageProject**.

     ![](./media/image52.png)

10. Right-click the plug-in and select **Register New Step**.

     ![](./media/image53.png)

11. Select **Create** for **Message** and
    select **contact** for **Primary Entity**.

     ![](./media/image54.png)

12. Select **PreOperation** for **Event Pipeline Stage of
    Execution** and then select **Register New Step**.

     ![A screenshot of a computer Description automatically generated](./media/image55.png)

13. Select **Close** on the Warning page which states that no filters on
    attributes detected.

     ![](./media/image56.png)

14. If you get error message i.e. Error occurred while registering the
    step, select **No** to see the details.

     ![A screenshot of a computer error Description automatically generated](./media/image57.png)

15. Check that, create step has got created under the Plugin.

     ![A red line with black text Description automatically generated](./media/image58.png)

16. Right-click the plug-in and select **Register New Step** again.

     ![](./media/image59.png)

17. Select **Update** for **Message**, select **contact** for **Primary
    Entity**, and then select the **Attributes** lookup.

     ![](./media/image60.png)

18. Clear the **Select All** check box, select the **Business
    Phone** check box, and then select **OK**.

     ![](./media/image61.png)

19. Select **PreOperation** for **Event Pipeline Stage of
    Execution** and then select **Register New Step**.

     ![A screenshot of a computer Description automatically generated](./media/image62.png)

20. If you get error message i.e. Error occurred while registering the
    step, select **No** to see the details.

     ![A screenshot of a computer error Description automatically generated](./media/image57.png)

21. Check that, create step has got created under the Plugin.

     ![A screenshot of a computer Description automatically generated](./media/image63.png)

### **Task 5: Test the plug-in**

1.  Go to your Maker Portal +++**https://make.powerapps.com/**+++ and make
    sure you are in **Dev One** environment selected.

2.  Select **Apps** and launch the **Fundraiser** application.

     ![A screenshot of a computer Description automatically generated](./media/image64.png)

3.  Select **+ New**.

     ![A screenshot of a computer Description automatically generated](./media/image65.png)

4.  Enter +++**Test**+++ for **First
    Name**, +++**Contact**+++ for **Last
    Name**, +++**(123)-555-0100**+++ for **Business Phone**, and then
    select **Save**.

     ![A screenshot of a contact form Description automatically generated](./media/image66.png)

     The record should be saved, and the **Business Phone** should show
     only the numeric values.

     ![](./media/image67.png)

5.  Change the **Business Phone** to **001-123-555-0100** and click on
    **Save**. The record should be updated, and the **Business
    Phone** should show only the numeric values.

     ![A screenshot of a contact form Description automatically generated](./media/image68.png)

**Summary:** In this lab, you have learnt how to create a plug-in that
will run on create and update and how to strip out all non-numeric
characters from a phone number using this plug-in.
