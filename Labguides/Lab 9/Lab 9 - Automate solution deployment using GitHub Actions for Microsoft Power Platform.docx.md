# **Lab 9: Automate solution deployment using GitHub Actions for Microsoft Power Platform**

### **Task 1: Create the app registration**

1.  Sign in to the Microsoft Azure portal
    using +++**https://portal.azure.com/#home**+++ with your Office 365 tenant
    credentials.

2.  Select **Get started**.

     ![A screenshot of a computer Description automatically generated](./media/image1.png)

3.  Select **Skip** on ‘How do you plan to use Azure’ page.

     ![A screenshot of a computer Description automatically generated](./media/image2.png)

4.  Select **Skip** on ‘Now, let’s show you around Azure’ page.

     ![A screenshot of a computer Description automatically generated](./media/image3.png)

5.  On the **Home** page of the portal, type **Microsoft Entra ID** in
    the search box and select it from the below suggested list of
    services.

     ![A screenshot of a computer Description automatically generated](./media/image4.png)

6.  In the left navigation pane, expand **Manage** and then select **App
    registrations**.

     ![A screenshot of a computer Description automatically generated](./media/image5.png)

7.  Select **+ New registration** on the **App registrations** page.

     ![A screenshot of a computer Description automatically generated](./media/image6.png)

8.  On the **App registrations** page, enter your application's
    registration information as described in the table.

    **Name** - +++Mytestingapp+++

    **Supported account types** - Select the Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) option.

     ![A screenshot of a computer application Description automatically generated](./media/image7.png)

10.  Select **Register** to create the application registration.

     ![A screenshot of a computer Description automatically generated](./media/image8.png)

11. The app registration overview page is shown. Add a client secret by
    selecting the **Certificates & secrets** in the left navigation
    pane. Select **Client secrets** tab and then select **+New client
    secret**.

     ![A screenshot of a computer Description automatically generated](./media/image9.png)

12. Add a given **description** for your client secret – +++**My sample
    client secret**+++. Select an **expiration** for the secret as
    **Recommended: 180 days (6 months)** and then select **Add**.

     ![A screenshot of a computer Description automatically generated](./media/image10.png)

13. Save the **secret's value and ID** in the notepad for use in your
    client application code. This secret value is never displayed
    again after you leave this page.

     **Important:** Do not navigate away from the client secret page until after you have copied the secret value (not the ID) as you'll not have access to the secret         value again.

     ![](./media/image11.png)

### **Task 2: Create a new app user**

Follow these steps to create an app user and bind it to your app
registration.

1.  Log into the Power Platform admin
    center +++**https://admin.powerplatform.microsoft.com/**+++ using your
    Office 365 tenant credentials.

2.  Select **Environments** in the left navigation pane, and then select
    the **Dev One** environment in the list to display the environment
    information.

     ![](./media/image12.png)

3.  Select the **See all** link under **S2S apps** on the right side of
    the page.

     ![A screenshot of a computer Description automatically generated](./media/image13.png)

4.  Select + **New app user**.

     ![](./media/image14.png)

5.  On the **Create a new app user** slide-out, select **+ Add an app**.

     ![A screenshot of a login page Description automatically generated](./media/image15.png)

6.  Start typing the name of your app registration - **Mytestingapp** in
    the search field, and then select (check) it within the results
    list. Next, select **Add**.

     ![](./media/image16.png)

7.  Back on the **Create a new app user** slide-out, select the
    target **Business unit** from the drop-down. Select **pencil icon**
    in front of **Security roles**, select **System Administrator** for
    the app user (also known as a service principle) and
    select **Save.** 

     ![A screenshot of a login page Description automatically generated](./media/image17.png)

8.  Select **Create**.

     ![A screenshot of a computer Description automatically generated](./media/image18.png)

9.  You should see your new application user in the displayed list of
    application users.

     ![A screenshot of a computer Description automatically generated](./media/image19.png)

### **Task 3: Build a model-driven app**

Follow the steps below to build a model-driven app.

1.  In your browser, navigate
    to Power Apps portal using +++**https://make.powerapps.com**+++ and
    sign in with your credentials. Click the environment selector
    dropdown in the header and select your development environment - **Dev One**.

     ![](./media/image20.png)

2.  Click the **Solutions** area in the left navigation, and then click
    the **New solution** button to create a new solution.

     ![A screenshot of a computer Description automatically generated](./media/image21.png)

3.  Enter the solution’s **Display name** as +++**GitHub Lab**+++, **Name** –
    +++**GitHubLab**+++. Select **+New publisher** under Publisher.

     ![](./media/image22.png)

4.  For the purposes of this lab, enter +++**GitHub Lab**+++ for
    the **display name**, +++**GitHubLab**+++ for **name**, and +++**gitlab**+++
    as **prefix**, and then choose **Save** and **Close**.

     ![A screenshot of a computer Description automatically generated](./media/image23.png)

5.  On the new solution panel, select the **publisher – GitHub Lab**
    that you just created and click **Create** to create a new unmanaged
    solution in the environment.

     ![A screenshot of a computer Description automatically generated](./media/image24.png)

6.  Your new solution will be empty, and you need to add components to
    it. In this lab we will create a custom table. Click the **+
    New** dropdown from the top navigation and select **Table \> Set
    advanced properties.**

     ![](./media/image25.png)

7.  Enter a **display name** – +++**Time Off Request**+++, plural name will be
    generated for you. Click **Save** to create the table.

     ![](./media/image26.png)

8.  Once your table is created, select the Table from breadcrumb
    navigation to go back to the solution view to add another component.

     ![](./media/image27.png)

9.  Click the **+ New** dropdown, then **App**, and finally
    click **Model-driven app**.

     ![A screenshot of a computer Description automatically generated](./media/image28.png)

10. Enter an app name – +++**Time Off Requests**+++, then click
    the **Create** button.

     ![A screenshot of a computer Description automatically generated](./media/image29.png)

11. In the application designer, click **+ Add page**.

     ![](./media/image30.png)

12. Select **Dataverse table**.

     ![](./media/image31.png)

13. Select **Time Off Request**, check the checkbox **Show in
    navigation**. Select **Add**.

     ![](./media/image32.png)

14. Click **Publish**, once the publish action is complete
    click **Play**.

     ![](./media/image33.png)

15. This will take you to the application so that you can see how it
    looks. You can use the application and close the tab when you are
    satisfied.

     ![A screenshot of a computer Description automatically generated](./media/image34.png)

### **Task 4: Create a GitHub Account**

**Note:** If you have an existing GitHub account then you can skip this
task and got to the next task.

1.  Go to +++**https://github.com**+++ and click **Sign
    up** or **Start a free trial** (or sign in if you have an existing
    account).

     ![A screenshot of a computer Description automatically generated](./media/image35.png)

2.  Enter your **email id** and then click **Continue**.

     ![A screen shot of a computer Description automatically generated](./media/image36.png)

3.  Keep the automatically generated password or create your own
    password and then click **Continue**.

     ![A screenshot of a computer Description automatically generated](./media/image37.png)

4.  Enter the **Username – Labtesting1** and then click **Continue**. If
    the given username is not available then enter different username.

     ![A screenshot of a computer Description automatically generated](./media/image38.png)

5.  Select **Continue**.

     ![A screenshot of a computer Description automatically generated](./media/image39.png)

6.  On ‘Verify your account’ page, select **Verify**.

     ![A screenshot of a computer Description automatically generated](./media/image40.png)

7.  Complete the verification process and use the launch code which is
    received on your email id.

8.  Select **Sign in** on ‘Sign in to GitHub’ window that appears.

     ![](./media/image41.png)

9.  Select **Skip personalization**.

     ![A screenshot of a computer Description automatically generated](./media/image42.png)

### **Task 5: Creating a new secret for Service Principal Authentication**

1.  After you have created your account, create a repository by
    selecting **Create repository**.

     ![A screenshot of a computer Description automatically generated](./media/image43.png)

     You might see the following alternative landing screen:

     ![Create a new repository](./media/image44.png)

2.  Create your new repository and name it +++**poweractionslab**+++. Make
    sure you select **Add a README file** to initiate the repo and
    choose **Create repository**.

     ![A screenshot of a computer Description automatically generated](./media/image45.png)

3.  Navigate to your repository and click **Settings**.

     ![](./media/image46.png)

4.  From the left side pane, expand **Secrets and variables**, and then
    and click **Actions**.

     ![A screenshot of a computer Description automatically generated](./media/image47.png)

5.  Scroll down and then select **New repository secret**.

     ![A screenshot of a computer Description automatically generated](./media/image48.png)

6.  On the Secrets page, name the secret +++**PowerPlatformSPN**+++. Use the
    client secret value from the application registration created in
    Microsoft Entra (Which you have saved in notepad) and enter it into
    the **Secret** field, and then select **Add secret**. The client
    secret will be referenced in the YML files used to define the GitHub
    workflows later in this lab.

     ![A screenshot of a computer Description automatically generated](./media/image49.png)

The client secret is now securely stored as a GitHub secret.

### **Task 6: Create a workflow to export and unpack the solution file to a new branch**

1.  Click on **Actions** from the above horizontal palette.

     ![A screenshot of a computer Description automatically generated](./media/image50.png)

2.  Click **Configure** in the **Simple workflow** box under
    the suggested for this repository section.

     ![A screenshot of a computer Description automatically generated](./media/image51.png)

3.  This will start a new YAML file with a basic workflow to help you
    get started with GitHub actions.

     ![A screenshot of a computer Description automatically generated](./media/image52.png)

4.  Delete the pre-created content, paste the content from
    the +++https://github.com/microsoft/powerplatform-actions-lab/blob/main/sample-workflows/export-and-branch-solution-with-spn-auth.yml+++ file.
    Open the given link in the new tab on the VM.

     ![A screenshot of a computer Description automatically generated](./media/image53.png)

5.  **Rename** the file to +++**export-and-branch-solution.yml**+++.

     ![A screenshot of a computer Description automatically generated](./media/image54.png)

6.  Update **ENVIRONMENTURL** on line no 28 with the URL for the
    development environment you want to export from.

     ![Rename and replace content.](./media/image55.png)

     To get Environment URL, go to **Power Platform Admin center**. Select **Environments** from left navigation, click on **Dev One** and then copy Environment URL.

     ![](./media/image56.png)

7.  **Paste** the **Environment URL** in the yml file. Make sure you add
    https://. Your URL should be in the given format -
    https://orgfc5xxxfd.crm.dynamics.com

     ![](./media/image57.png)

8.  Update **APPID** and **TENANT ID** with your values. To get these
    two values, go to Azure portal and then select **Home** \>
    **Microsoft Entra ID** \> **App** registration then select **All
    applications** tab and then select **Mytestingapp**.

     ![A screen shot of a computer Description automatically generated](./media/image58.png)

     ![A screenshot of a computer Description automatically generated](./media/image59.png)

9.  Paste the values on line no 29 and 30.

     ![](./media/image60.png)

10. On the line no 12 of the code, change the default value ALMLab to
    +++**GitHubLab**+++ which is our solution name in this case. Make sure you
    don’t leave any space and write it correctly as given. If you have
    given a different name to your solution then write that here.

     ![A screenshot of a computer Description automatically generated](./media/image61.png)

11. You are now ready to commit your changes. Select **Commit changes**
    and then on Commit changes pane that opens, select **Commit
    changes**.

     ![A screenshot of a computer Description automatically generated](./media/image62.png)

     Congratulations, you have just created your first GitHub workflow using the following actions:

    - **Who Am I**: Ensures that you can successfully connect to the
      environment you are exporting from.
    
    - **Export Solution**: Exports the solution file from your development
      environment.
    
    - **Unpack Solution**: The solution file that is exported from the
      server is a compressed (zip) file with consolidated configuration
      files. These initial files are not suitable for source code management
      as they are not structured to make it feasible for source code
      management systems to properly do differencing on the files and
      capture the changes you want to commit to source control. You need to
      'unpack' the solution files to make them suitable for source control
      storage and processing.
    
    - **Branch Solution**: Creates a new branch to store the exported
      solution.

### **Task 7: Test the export and unpack workflow**

1.  Next, to test that the workflow runs, select **Actions** from the
    above horizontal palette, select **export-and-branch-solution**
    workflow listed under **All workflows** on left side pane.

     ![](./media/image63.png)

2.   Select **Run workflow** and again choose **Run workflow**. If you
    have a different solution name than 'GitHubLab' then change the
    value here but leave the other values as is.

     ![](./media/image64.png)

3.  After 5–10 seconds the workflow will start, and you can select the
    running workflow to monitor progress.

     ![](./media/image65.png)

     ![](./media/image66.png)

4.  After the workflow has completed, validate that a new branch has
    been created with the solution unpacked to the
    **solutions/GitHubLab** folder. Navigate to the **Code** tab. 

     ![A screenshot of a computer Description automatically generated](./media/image67.png)

5.  Expand the **Branches** drop-down.

     ![](./media/image68.png)

6.  Select the branch – **GitHubLab-xxxx-xxxx** that was created by the
    action.

     ![A screenshot of a computer Description automatically generated](./media/image69.png)

7.  Validate that the **solutions/GitHubLab** folder has been created in
    the new branch

     ![A screenshot of a computer Description automatically generated](./media/image70.png)

8.  To create a Pull request to merge the changes into the main
    branch, Click **Contribute** and in the flyout click **Open Pull
    request**.

     ![A screenshot of a computer Description automatically generated](./media/image71.png)

9.  On the **Open a Pull request** screen, keep the title as is
    then click **Create pull request**.

     ![A screenshot of a computer Description automatically generated](./media/image72.png)

10. The screen will update showing the newly create pull request. As the
    pull request is created confirmation will be provided showing that
    our branch has no conflict with the main branch.

     ![A screenshot of a computer Description automatically generated](./media/image73.png)

11. This confirmation means that the changes can be merged into the main
    branch automatically. Click **Merge pull request**. 

     ![A screenshot of a computer Description automatically generated](./media/image74.png)

12. Click **Confirm merge**.

     ![A screenshot of a computer Description automatically generated](./media/image75.png)

13. Optionally, click delete branch to clean up the now defunct branch.

     ![A close up of a message Description automatically generated](./media/image76.png)

14. Click on **Code**.

     ![](./media/image77.png)

15. You are navigated back to the default (main) branch and validate the
    solution is now available there as well.

     ![A screenshot of a computer Description automatically generated](./media/image78.png)
