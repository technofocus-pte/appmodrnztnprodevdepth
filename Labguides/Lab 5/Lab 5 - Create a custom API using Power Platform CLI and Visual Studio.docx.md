**Lab 5: Create a custom API**

**Estimated Duration:** 35 min

**Objective:** In this lab, you will learn to build a Dataverse custom
API to execute some custom logic. You'll then use the custom API from a
step in a Power Automate flow.

**Task 1: Create the custom API project**

1.  Click on the **Start** menu of the VM, type Command Prompt in the
    search box and then select **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Run the command below to create a new folder named **CustomAPILab**.

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  Change directory to the folder you created.

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  You should now be in the CustomAPIlAB folder. Run the command below
    to initialize a new Dataverse plugin class library.

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Dataverse plugin class library creation should be successful.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Run the command below to open the project in Visual Studio.

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  If asked, select **Microsoft Visual Studio 2022** and then select
    **Just once**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  If you are asked to sign in to Visual Studio , select **Skip this
    for now** on signing in page.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  Select **General** as Development settings choose **Dark** as your
    color theme and then select **Start Visual Studio**.

> **Note:** Ignore this step if you are directly navigated to the
> project.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. The project should open in Visual Studio.

> ![](./media/image10.png)

11. Right click on the Plugin1.cs file and rename it **MatchPlugin.cs**.

> ![](./media/image11.png)

12. Select **Yes** to you're renaming a file dialog.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Right click on the CustomAPILab Project and select **Manage NuGet
    Packages**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. Search for **System.Text.RegularExpressions** and
    select **Install**.

> ![](./media/image14.png)

15. On Preview changes window, select **Apply** to allow Visual Studio
    to make changes to the solution.

> ![](./media/image15.png)

16. Select **I Accept** to accept the license terms.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17. Open the **MatchPlugin.cs** file.

> ![](./media/image17.png)

18. Add the following statement below ‘using System;’ statement i.e. on
    the line no 3.

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. Add the following lines inside the ExecuteDataversePlugin method and
    after the var context line. These lines get the value from the input
    parameters passed on the custom API invocation.

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. Add the following line after to get the tracing service.

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. Add the below line to write the input value into trace.

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. Add the following line after to call the Regex.Match method.

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. Write the result to trace.

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. And finally, add the following line to set the output parameter
    Matched.

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. Your execute method should now look like the following.

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. Select **Build | Build Solution**.

> ![](./media/image26.png)

27. The project should build successfully.

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**Task 2: Register the custom API plugin**

1.  Open command prompt and run the command below to launch the Plugin
    Registration Tool.

> +++pac tool prt+++
>
> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  Select **+ Create New Connection**.

> ![](./media/image29.png)

3.  Select **Office 365**, provide your credentials and
    select **Login**.

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  Sign in with your **M365 Admin tenant Id** and then select **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Enter your **M365 Admin tenant Id’s** **password** and then select
    **Sign in**.

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  Check that **Dev One** environment is selected.

7.  Choose **Register | Register New Assembly**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  Select ... under the Step 1 and then browse to
    the **CustomAPILab\bin\Debug\net462** folder.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  Select **CustomAPILab.dll** then select **Open**.

> ![](./media/image35.png)

10. Select **Register Selected Plugins**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. Select **OK** to the success message. Your plugin is ready to
    connect to the custom API we'll create in the next task.

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**Task 3: Create the custom API**

1.  Navigate to Power Apps maker portal
    using +++<https://make.powerapps.com/>+++ and make sure you are in
    the **Dev One** environment.

2.  Select **Solutions** on the left navigation. Select **+ New
    Solution**.

> ![](./media/image38.png)

3.  Enter +++**Custom API Lab**+++ in the Display Name.

4.  Select **CDS Default Publisher** in the Publisher dropdown.

5.  Select **Create**. This creates a custom solution that will contain
    our components.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Select **+ New | More | Other | Custom API.**

> ![](./media/image40.png)

7.  Enter the following information:

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

8.  In Plugin Type select the search icon and locate your plugin -
    **CustomAPILab.MatchPlugin**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  Select **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. Select **Done**.

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11. Select **+** **New | More| Other | Custom API Request Parameter**.

> ![](./media/image44.png)

12. For **Custom API**, select the **Search** icon and
    select **Match** (your Custom API).

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. Enter +++**StringIn**+++ for Unique Name, Name, Display Name and
    Description for simplicity.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. Select **String** for Type.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. Select **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. Select **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. To add one more, Custom API Request Parameter, Select **+** **New |
    More| Other | Custom API Request Parameter**.

> ![](./media/image50.png)

18. For **Custom API**, select the **Search** icon and
    select **Match** (your Custom API).

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. Enter **Pattern** for Unique Name, Name, Display Name and
    Description for simplicity.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. Select **String** for Type.

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. Select **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. Select **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. Select **New | More | Other| Custom API Response Property**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. For **Custom API**, select the **Search** icon and
    select **Match** (your Custom API).

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. Enter +++**Matched**+++ for **Unique Name**, **Name, Display
    Name** and **Description** for simplicity.

26. Select **Boolean** for **Type**.

> ![](./media/image58.png)

27. Select **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. Select **Done**.

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. Your solution component list should look like the following.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**Task 4: Use custom API from Power Automate**

1.  In the solution, select **+ New | Automation | Cloud Flow |
    Instant**.

> ![](./media/image62.png)

2.  Enter +++**String match**+++ for Flow name, select **Manually
    trigger a flow** trigger, and select **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  Select the **+ New Step**.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  Search for perform and choose **Perform an unbound action**.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  In the Action Name list, locate and select **contoso_match**.

> ![](./media/image66.png)

6.  Enter **myemail@outlook.com** email address in **StringIn**. Here,
    you can type any valid simple email address.

> ![](./media/image67.png)

7.  Enter the following Regular expression in Pattern. This is a simple
    email pattern.
    Other [*examples*](https://regexlib.com/DisplayPatterns.aspx/) are
    available.

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  Your flow should look like the following.

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  Select **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. After save is complete, select **Test**.

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. Select **Manually**, then select **Test**.

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. Select **Run flow**.

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. Select **Done**.

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. After your flow completes, select the **Perform an unbound
    action** to expand and see results.

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**Summary:** In this lab, you have learnt how to build a custom action
and use it from a Power Automate flow. The custom API action
contoso_match is now also available for calling directly using the
platform API.
