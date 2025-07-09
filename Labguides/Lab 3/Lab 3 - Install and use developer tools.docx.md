# **Lab 3 - Install and use developer tools**

**Estimated Duration:** 15 min

**Objective:** In this lab, you will learn to install some of the
developer tools from NuGet.

### **Task 1: Install developer tools**

In this task, you'll use a Power Platform CLI to install tools.

1.  To launch **Command Prompt**, go to **Start** menu of the VM, type
    Command Prompt in the search box and select **Open**.

     ![A screenshot of a computer Description automatically generated](./media/image1.png)

2.  Run the command below to install the **Configuration Manager Tool**.

     +++pac tool cmt+++

     ![A screenshot of a computer Description automatically generated](./media/image2.png)

3.  The Configuration Manager Tool should be installed and launched.
    Close the Configuration Manager Tool.

    ![A screenshot of a computer Description automatically generated](./media/image3.png)

5.  Run the command below to install the **Package Deployer Tool**.

     +++pac tool pd+++

    ![A screenshot of a computer Description automatically generated](./media/image3.1.5.png)

6.  The Package deployer tool should be installed and launched. Close
    the Package Deployer Tool.

     ![A screenshot of a computer Description automatically generated](./media/image5.png)

7.  Run the command below to install the **Plugin Registration Tool**.

     +++pac tool prt+++

     ![](./media/image6.png)

8.  The Plugin Registration should be installed and launched. Don't
    close the Plugin Registration Tool.

     ![](./media/image7.png)

**Task 2: Explore a registered plug-in with the plug-in registration
tool**

1.  Select **Create New Connection.**

     ![](./media/image8.png)

2.  Select Office 365. Check the checkbox for **Display list of available organizations**.

     ![A screenshot of a computer Description automatically generated](./media/image9.png)

3.  Select **Login.** 

    ![A screenshot of a computer Description automatically generated](./media/image10.png)

4.  Sign in with your Dataverse environment credentials i.e. Office 365
    Admin credentials. Click **Next**.

    ![A screenshot of a computer Description automatically generated](./media/image11.png)

5.  Enter your Admin tenant password and click **Sign in**.

    ![A screenshot of a login box Description automatically generated](./media/image12.png)

6.  In this case, you can see that **Dev One** environment is already
    selected. In case, if the list of environments appears, pick your
    environment – **Dev One** and select **Login** again.

    ![](./media/image13.png)

7.  You'll see a list of system plug-ins. If you have custom plug-ins in
    your environment you would see them in the list as well. The
    (Assembly) are .NET DLLs that implement the plug-ins.

     **Note:** You need to expand the section to see the complete list.

    ![A screenshot of a computer Description automatically generated](./media/image14.png)

9.  Locate **Microsoft.CDS.DataLakeDataProvider.Plugins** and expand it.

    ![A screenshot of a computer Description automatically generated](./media/image15.png)

10.  Each of the child items is implemented in the assembly. Expand one
    of the items to see the step registrations for that individual
    plug-in.

     ![A screenshot of a computer Description automatically generated](./media/image16.png)

11. Step registration connects the plug-in as an event handler to the
    event. In the above example, this is handling a create on the
    insightsstorevirtualentity table.

    ![](./media/image17.png)

12. Double-click on any step to see the step configuration details
    including what message and entity, it's registered on, the pipeline
    stage when the plugin will be invoked, whether execution is
    synchronous or asynchronous, etc.

    ![](./media/image18.png)

**Summary:** In this lab, you have learnt how to install developer
tools. When you create your own custom plug-in, you will use Plugin
Registration Tool to load the assembly and register the steps for the
events that you want to handle.
