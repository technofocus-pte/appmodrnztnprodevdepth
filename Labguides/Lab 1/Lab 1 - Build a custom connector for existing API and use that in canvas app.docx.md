# **Lab 1 - Build a custom connector for existing API and use that in canvas app**

**Estimated Duration:** 35 min

**Objective:** In this lab, you will learn to create your first custom
connector for an existing API called Contoso Invoicing, to create a
canvas app and how to use the connector in the canvas app.

### **Task 1: Review the API**

To review the API, follow these steps:

1.  Go to +++**https://contosoinvoicing.azurewebsites.net/**+++.

2.  To select the documentation link, click on **here** next to ‘You can
    find the API documentation’.

     ![](./media/image1.png)

3.  Review the available operations.

     ![A screenshot of a computer Description automatically generated](./media/image2.png)

4.  Close the documentation browser tab or window.

5.  Select the **Open API definition** link.

     ![A screenshot of a computer Description automatically generated](./media/image3.png)

6.  The following image shows an example of the OpenAPI version. Right-click and select **Select all**. Again right-click and select **Copy**. 

     ![Screenshot of an arrow pointing to the save as button.](./media/image4.png)

7.  Open Notepad on your VM, paste the code into the Notepad and save the file with the name **swagger.json**, locally on VM’s Desktop. You'll use this file later in
    the exercise.

8.  Close the definition browser tab or window.

9.  Select the **API Key** link.

     ![A screenshot of a computer Description automatically generated](./media/image5.png)

10. Open other new Notepad document. Copy and save your API key to the notepad on your VM because you'll
    need it later.

     ![](./media/image6.png)

11. Select **Return to home**.

     ![A screenshot of a computer Description automatically generated](./media/image7.png)

12. Select **Download Logo**.

     ![A screenshot of a computer Description automatically generated](./media/image8.png)

13. Save the logo image locally on VM’s Desktop; you'll use it later.

### **Task 2: Create a new solution**

To create a new solution, follow these steps:

1.  Go to +++**https://make.powerapps.com/**+++ and make sure that you are in
    **Dev One** environment.

     ![](./media/image9.png)

2.  From left navigation pane, select **Solutions**.

     ![A screenshot of a computer Description automatically generated](./media/image10.png)

3.  Select **+New solution** from the upper ribbon.

     ![A screenshot of a computer Description automatically generated](./media/image11.png)

4.  Enter +++**Contoso invoicing**+++ for the **Display name** and
    select **+ New publisher**.

     ![A screenshot of a computer Description automatically generated](./media/image12.png)

5.  Enter +++**Contoso**+++ for Display name, +++**Contoso**+++ for
    Name, +++**contoso**+++ for Prefix, and then select **Save**.

     ![A screenshot of a computer Description automatically generated](./media/image13.png)
    
     **Note:** If you get an error message as ‘A record with matching key values already exists’, ignore it and close the ‘New publisher’ window.

    ![](./media/image14.png)

6.  Now, on **New solution** window,
    select **Contoso** for **Publisher**, and then select **Create**.
    When you're working on a real project, it's best to create your own
    publisher.

     ![A screenshot of a computer Description automatically generated](./media/image15.png)

7.  Don't navigate away from this page after selecting **Create**. You
    will be automatically navigated to the ‘Contoso invoicing’ solution.

### **Task 3: Create a new connector**

To create a new connector, follow these steps:

1.  Make sure that you are in **Contoso invoicing** solution that you
    created.

     ![A screenshot of a computer Description automatically generated](./media/image16.png)

2.  Select **+ New** | **Automation** | **Custom connector**.

     ![A screenshot of a computer Description automatically generated](./media/image17.png)

3.  Enter +++**Contoso invoicing**+++ for the **Connector name**.

     ![](./media/image18.png)

4.  Select **Upload** to upload the image.

     ![A screenshot of a computer Description automatically generated](./media/image19.png)

5.  Select the connector logo image that you downloaded in **Task 1:
    Review the API**.

6.  Enter +++**\#175497**+++ for **Icon background color**.

7.  Enter +++**Custom connector for Contoso Invoicing
    API**+++ for **Description**.

8.  Enter +++**contosoinvoicingtest.azurewebsites.net**+++ for **Host**.

     ![](./media/image20.png)

9.  Select **Create connector**.

     ![A screenshot of a computer Description automatically generated](./media/image21.png)

10. Don't navigate away from this page.

### **Task 4: Import the OpenAPI definition**

To import the OpenAPI definition, follow these steps:

1.  Select the arrow next to **Connector Name**.

     ![A screenshot of a computer screen Description automatically generated](./media/image22.png)

2.  Select the ellipsis (**...**) button of the connector and then
    select **Update from OpenAPI file**.

     ![A screenshot of a computer Description automatically generated](./media/image23.png)

3.  Select **Import**.

     ![A screenshot of a computer Description automatically generated](./media/image24.png)

4.  Select the **swagger.json** file that you downloaded in **Task 1:
    Review the API** and then select **Open**.

     ![A screenshot of a computer Description automatically generated](./media/image25.png)

5.  Select **Continue**.

     ![A screenshot of a computer Description automatically generated](./media/image26.png)

6.  Fill in the host URL
    as +++**contosoinvoicingtest.azurewebsites.net**+++ and then
    select **Security** from the bottom right corner.

     ![A screenshot of a computer Description automatically generated](./media/image27.png)

7.  Notice that the fields are filled out from the imported file.

     ![A screenshot of a computer Description automatically generated](./media/image28.png)

8.  Don't navigate away from this page.

### **Task 5: Review and adjust definitions**

To review and adjust definitions, follow these steps:

1.  Select the **Definition** tab.

     ![A screenshot of a computer Description automatically generated](./media/image29.png)

2.  Take a few minutes to review the operations that were imported.

3.  Notice the blue information circle next to **GetInvoice**.

     ![A screenshot of a computer Description automatically generated](./media/image30.png)

4.  Select the **GetInvoice** operation.

     ![A screenshot of a computer Description automatically generated](./media/image31.png)

5.  Notice that the operation indicates a missing **Summary**.

     ![A screenshot of a phone Description automatically generated](./media/image32.png)

6.  Enter +++Get Invoice+++ as the **Summary** to improve the usability.

     ![A screenshot of a computer Description automatically generated](./media/image33.png)

7.  Notice the blue information circle next to
    the **PayInvoice** operation and that it indicates a
    missing **Description**.

     ![A screenshot of a computer Description automatically generated](./media/image34.png)

8.  Select **PayInvoice** operation.

     ![A screenshot of a computer Description automatically generated](./media/image35.png)

9.  Enter +++**Pay an invoice**+++ as the **Description**.

     ![A screenshot of a computer Description automatically generated](./media/image36.png)

10. Delete both **NewInvoice** operations because you won't use them.

     ![Screenshot showing the delete action button.](./media/image37.png)

11. Select the **GetInvoiceSchema** operation.

     ![](./media/image38.png)

12. Modify the **Visibility** option to **internal** so that people
    don't see it in their action list and then select **Update
    connector**.

     ![](./media/image39.png)

13. Don't navigate away from this page.

### **Task 6: Test the connector**

To test the connector, follow these steps:

1.  Select the **Test** tab.

     ![A screenshot of a computer Description automatically generated](./media/image40.png)

2.  Select **+ New connection**.

     ![A screenshot of a computer Description automatically generated](./media/image41.png)

3.  Paste in the **API Key** that you saved in **Task 1: Review the
    API** and then select **Create connection**.

     ![A screenshot of a computer Description automatically generated](./media/image42.png)

4.  Select the **Refresh** button.

     ![A screenshot of a computer Description automatically generated](./media/image43.png)

5.  Select **ListInvoiceTypes | Test Operation**.

     ![A screenshot of a computer Description automatically generated](./media/image44.png)

6.  You should see the invoice types data in the body area.

     ![A screenshot of a computer Description automatically generated](./media/image45.png)

7.  Select **Close** to close the custom connector window.

     ![](./media/image46.png)

### **Task 7: Use custom connector in canvas app**

In this task, you'll create a canvas application and use the custom
connector you created to display a list of invoices.

1.  Come back to Power Apps maker portal. Select **Done** on pop-up that
    says ‘Currently creating a new custom connector’. Make sure that you
    are in the **Dev One** environment.

     ![](./media/image47.png)

     **Note:** If the portal is not already opened, navigate
     to +++**https://make.powerapps.com/**+++ and make sure that you are in
     the **Dev One** environment.

2.  Make sure you are in **Contoso invoicing** solution you created. If
    not, select **Solutions** and open the **Contoso
    invoicing** solution you created.

     ![A screenshot of a computer Description automatically generated](./media/image48.png)

3.  Select **+ New** and then select **App > Canvas app**.

     ![](./media/image49.png)

4.  Enter +++**Contoso invoicing app**+++ for App name, select **Phone** for
    Format, and then select **Create**.

     ![A screenshot of a computer Description automatically generated](./media/image50.png)

5.  Select **Skip** on welcome window.

     ![](./media/image51.png)

6.  Select the **Data** tab, select **+ Add data**.

     ![A screenshot of a computer Description automatically generated](./media/image52.png)

7.  expand **Connectors**, and then select the **Contoso
    invoicing** custom connector you created.

     ![A screenshot of a computer Description automatically generated](./media/image53.png)

8.  Select the **+ Add a connection**.

     ![A screenshot of a computer Description automatically generated](./media/image54.png)

9.  Paste in the API Key that you saved in **Task 1: Review the API**
    and then select **Connect**.

     ![A screenshot of a login box Description automatically generated](./media/image55.png)

10. Select **Got it** on the premium warning popup.

     ![A screenshot of a phone Description automatically generated](./media/image56.png)

11. Select the **Tree view** tab.

     ![A screenshot of a computer Description automatically generated](./media/image57.png)

12. Select **+ Insert** and then select **Vertical gallery**.

     ![A screenshot of a computer Description automatically generated](./media/image58.png)

13. Select **ContosoInvoicing** for Data.

     ![A screenshot of a computer Description automatically generated](./media/image59.png)

14. Set the **Items** to the value below.

     +++**ContosoInvoicing.ListInvoices().invoices**+++

     ![A screenshot of a computer Description automatically generated](./media/image60.png)

15. Select **Tree view**, expand the gallery and select the **Subtitle**.

     ![A screenshot of a computer Description automatically generated](./media/image61.png)

16. Set the **Text** value of the Subtitle to +++**ThisItem.amount**+++.

     ![A screenshot of a computer Description automatically generated](./media/image62.png)

17. Expand the gallery and select the **Title** inside the gallery.

     ![A screenshot of a computer Description automatically generated](./media/image63.png)

18. Set the **Text** value of the Title
    to +++**ThisItem.accountName**+++.

     ![A screenshot of a computer Description automatically generated](./media/image64.png)

19. The gallery should now look like the image below.

     ![A screenshot of a computer Description automatically generated](./media/image65.png)

20. Select **Save** icon from upper right corner to save the app.

**Summary:** In this lab, you have learnt to create custom connector for
an existing API, to import the API definition and to use that connector
in the canvas app to display a list of invoices. Custom connectors are
function-based, they call specific functions in the underlying service
of the API to return the corresponding data.
