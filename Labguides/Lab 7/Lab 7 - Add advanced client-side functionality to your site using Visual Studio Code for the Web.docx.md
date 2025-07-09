# **Lab 7: Add advanced client-side functionality to your site using Visual Studio Code for the Web** 

**Estimated Duration:** 35 min

**Objective:** In this lab, you will learn how to add JavaScript code to
a page to render data from Microsoft Dataverse as a chart.

### **Task 1: Create a site with the help of AI**

1.  Go to Power Pages using
    +++**https://make.powerpages.microsoft.com/**+++. Make sure that you
    are in **Dev One** environment. Select **Get started**.

     ![](./media/image1.png)

2.  Select **Skip** on **Tell us about yourself** page.

     ![A screenshot of a computer Description automatically generated](./media/image2.png)

3.  Enter the given description to create a site and then click on the
    **generate** icon.

 +++**Create a site for customers to find financial advisors at a bank based on their qualifications, and areas of expertise**+++ 

   ![A screenshot of a computer Description automatically generated](./media/image3.png)

4.  Copilot generates a site name and a web address based on your
    description. In this case, the site name is ‘**Finance Advisor
    Search’**. Keep the generated site name and address and then
    select **Next**.

     ![A screenshot of a computer Description automatically generated](./media/image4.png)

5.  Copilot generates a home page layout, which you can scroll through
    and browse the page generated. Select **Next** to accept the
    suggested layout.

     **Note:** You can select **Try again** to generate a new layout.

     ![A screenshot of a website Description automatically generated](./media/image5.png)

6.  Copilot generates more pages that could be used in the site based on
    the description. In this example, Contact us, Advisor search,
    Advisor profile and Advisor contact pages are selected and then
    select **Done** to complete the site creation.

     **Note 1:** If you copilot generates different pages for your site than the above mentioned pages then you can select some of them.

     **Note 2**: IF you get any error at this point then refresh the page and select **Edit** under **Active sites** from the Home page of **Power Pages** portal.

     ![](./media/image6.png)

7.  Site creation can take a few minutes. When finished, you're
    redirected to the site opened in the design studio that you can
    customize further.

    **Note**: For the better view, you can close the pop-up windows if appear.

     ![A screenshot of a computer Description automatically generated](./media/image7.png)

### **Task 2: Create site settings**

To create site settings, follow these steps.

1.  Select the ellipsis (**...**) menu and then select **Power Pages
    Management**.

     The Portal Management app will open in a new tab.

     ![](./media/image8.png)

2.  Select **Site Settings**. Select **+ New.** 

     ![](./media/image9.png)

3.  Enter the following information and then select **Save**.

    - **Name** - +++Webapi/account/enabled+++

    &nbsp;

    - **Website** - Select your website

    &nbsp;

    - **Value** - +++true+++

     ![A screenshot of a computer Description automatically generated](./media/image10.png)

4.  Select **+ New.** 

     ![](./media/image11.png)

5.  Enter the following information and then select **Save & Close**.

    - **Name** - +++Webapi/account/fields+++

    &nbsp;

    - **Website** - Select your website

    &nbsp;

    - **Value** - +++name,numberofemployees,revenue+++

     ![A screenshot of a computer Description automatically generated](./media/image12.png)

### **Task 3: Create table permissions**

To create table permissions, follow these steps.

1.  Switch to Power Pages design studio, where the newly created website
    is opened.

     **Note:** You can close the Copilot pane for better visibility.

     ![](./media/image13.png)

2.  Select the **Security** workspace and then select **Table
    permissions**.

     ![A screenshot of a computer security Description automatically generated](./media/image14.png)

3.  Select **+ New permission.**

     ![](./media/image15.png) 

4.  Fill in the following information:

    - **Name** - +++Account+++

    &nbsp;

    - **Table** - Select Account 

    &nbsp;

    - **Access type** - Global

    &nbsp;

    - **Permission to** – Read

     ![](./media/image16.png)

5.  Select **Add roles** and then add **Anonymous
    Users** and **Authenticated Users**.

     ![A screenshot of a computer Description automatically generated](./media/image17.png)

6.  Select **Save**.

     ![A screenshot of a computer Description automatically generated](./media/image18.png)

7.  Choose **Save** to keep this data visible to anyone.

     ![A screenshot of a computer error message Description automatically generated](./media/image19.png)

8.  You can see the message that ‘The table permission ‘Account’ have
    successfully been saved’.

     ![](./media/image20.png)

### **Task 4: Test the Web API**

1.  To test the Web API, open the following URL after adding your
    website address. To get the website address, select **Set up** from the left navigation pane, select **Site detals** and you can find url there.  

    +++https://**yourwebsite**.powerappsportals.com/_api/accounts?$select=name,numberofemployees,revenue+++

2.  If permission requested dialog appears, select **Accept**.

     ![A screenshot of a application Description automatically generated](./media/image21.png)

3.  Your output should resemble the following image.

     ![A screenshot of a computer Description automatically generated](./media/image22.png)

### **Task 5: Create a content page and retrieve data**

To create a content page and add JavaScript code that retrieves and
transforms the data, follow these steps:

1.  In design studio, select the **Pages** workspace then select **+Page**.

     ![](./media/image23.png)

2.  On the **Describe a page to design it** window, select **Other ways to add a page** option.

     ![A screenshot of a computer Description automatically generated](./media/image5.2.png)

3. Enter +++**Chart**+++ as the **Page name**.

4.  Make sure that the **Add page to main navigation** option is
    selected.

5.  Select the **Start from blank** layout.

6.  Select **Add**.

     ![A screenshot of a computer Description automatically generated](./media/image24.png)

7.  Select **Edit code**.

     ![](./media/image25.png)

8.  In the pop-up dialog, select **Open Visual Studio Code**.

     ![A screenshot of a computer Description automatically generated](./media/image26.png)

9.  If pop-up appears and ask you to allow the extension Power Platform
    tool to sign in using Microsoft, select **Allow**.

     ![A black screen with white text Description automatically generated](./media/image27.png)

10.  It will fetch your data.

     ![A screenshot of a computer Description automatically generated](./media/image28.png)

11. In the Visual Studio Code editor, select
    the **Chart.en-US.customjs.js** file.

     ![A screenshot of a computer Description automatically generated](./media/image29.png)

12. Append the following script:

    **Note**: You can copy the script into Notepad on your VM, then paste it from there into Visual Studio Code.

    ```

     function makeChart(rawData) {

     // transform raw data into plotting array
    
     var rData = rawData.value.map(({
    
    
     revenue,
    
     numberofemployees
    
     }) => ({
    
     "x": numberofemployees,
    
     "y": revenue,
    
     "z": (!revenue) ? 1 : numberofemployees / revenue,
    
     "name": name
    
     }));
    
     console.log(rData);
    
     }
    
     // retrieve accounts data using portals Web API
    
     $(document).ready(function() {
    
     $.get('/_api/accounts?$select=name,numberofemployees,revenue', makeChart, 'json');
    
     });

    ```

    **Note:** If you see extra braces (in red colour) at the end of the code, delete them.

13. Press the **Ctrl + S** keyboard shortcut (**⌘ + S** on Mac) to save
    the file.

     ![A screen shot of a computer program Description automatically generated](./media/image30.png)

14. Close the **Visual Studio Code** tab. Select **Sync** when prompted
    to synchronize the changes.

     ![A screenshot of a computer Description automatically generated](./media/image31.png)

15. Select **Preview | Desktop**.

     ![A screenshot of a computer Description automatically generated](./media/image32.png)

16. When the page is displayed, press the **CTRL + SHIFT + I** key to display browser
    developer tools.

     ![A screenshot of a computer Description automatically generated](./media/image33.png)

     ![A screenshot of a computer Description automatically generated](./media/image34.png)

17. Select **Console** tab.

     ![A screenshot of a computer Description automatically generated](./media/image35.png)

18. Verify that the console output contains the same data as previously retrieved, except that it's now showing as transformed. 

     ![A screenshot of a computer program Description automatically generated](./media/image36.png)

19. The data structure is now prepared for plotting. 

    - **name** - Company name

    &nbsp;

    - **x** - Number of employees

    &nbsp;

    - **y** - Company revenue in thousands

    &nbsp;

    - **z** - Revenue for each employee (calculated)

### **Task 6: Add external library functionality**

This exercise uses Highcharts.js library (free for personal or
non-profit use) to create a bubble chart based on the data.

1.  Switch to the design studio.

     ![A screenshot of a computer Description automatically generated](./media/image37.png)

2.  Select the page footer and then select **Edit code**.

     ![A screenshot of a computer Description automatically generated](./media/image38.png)

3.  In the pop-up dialog, select **Open Visual Studio Code**.

     ![A screenshot of a computer Description automatically generated](./media/image39.png)

4.  Append the following code at the end of the file.

    ```

    <script src="https://code.highcharts.com/highcharts.js"></script>
    <script src="https://code.highcharts.com/highcharts-more.js"></script>

    ```

     ![](./media/image40.png)

5.  Press the **Ctrl + S** keyboard shortcut (**⌘ + S** on Mac) to save
    the file.

6.  Close the **Visual Studio Code** tab then select **Sync** to
    synchronize the changes on the design studio.

7.  Select **Edit code** on the toolbar to open Visual Studio Code for
    the page.

     ![A screenshot of a computer Description automatically generated](./media/image41.png)

8.  Select **Open Visual Studio Code** on Edit in Visual Studio Code for
    the Web pop-up.

     ![A screenshot of a computer Description automatically generated](./media/image26.png)

9.  Select the **Chart.en-US.customjs.js** file.

     ![A screen shot of a computer program Description automatically generated](./media/image42.png)

10. Replace the file to change the **makeChart** function as follows:

    **Note 1**: Here, replacing the file means you are modifying the existing file only.

    **Note 2**: You can copy the script into Notepad on your VM, then paste it from there into Visual Studio Code.

    ```    

     function makeChart(data) {
    
     console.log(data);
    
     var rData = data.value.map(({
    
     name,
    
     revenue,
    
     numberofemployees
    
     }) => ({
    
     "x": numberofemployees,
    
     "y": revenue,
    
     "z": (!revenue) ? 1 : numberofemployees / revenue,
    
     "name": name

     }));
    
     console.log(rData);
    
     // new code to plot the data
    
     Highcharts.chart($('.mychart')[0], {
    
     title: {
    
     text: "Customers efficiency"
    
     },
    
     legend: {
    
     enabled: false
    
     },
    
     xAxis: {
    
         title: {
    
             text: "Number of employees"
    
     }
    
     },
    
     yAxis: {
    
         title: {

             text: "Turnover ($K)"
    
     }
    
     },
    
     tooltip: {
    
     pointFormat:'<strong>{point.name}</strong><br/>Employed: {point.x}<br>Turnover ($K): ${point.y}',

     headerFormat: ''
    
     },
    
     series: [{
    
     type: 'bubble',
    
         data: rData
    
     }]
    
     });
    
     }
    
     // retrieve accounts data using portals Web API
    
     $(document).ready(function() {
    
        $.get('/_api/accounts?$select=name,numberofemployees,revenue', makeChart, 'json');
    
     });

    ```

     ![A screen shot of a computer program Description automatically generated](./media/image43.png)

11. Press the **Ctrl + S** keyboard shortcut (**⌘ + S** on Mac) to save
    the file.

12. Select the **Chart.en-US.webpage.copy.html** file.

     ![A screenshot of a computer program Description automatically generated](./media/image44.png)

13. Insert the following code into the inner 'div' element:

    **Note 2**: You can copy the script into Notepad on your VM, then paste it from there into Visual Studio Code.

    ```

    <figure>
        <div class="mychart"></div>
    </figure>

    ```

     ![A screen shot of a computer Description automatically generated](./media/image45.png)

14. Press the **Ctrl + S** keyboard shortcut (**⌘ + S** on Mac) to save
    the file. If you get an error message that says failed to save and asks you to compare or overwrite the content of the file with the new changes then slelct **Overwrite**.

    ![A screenshot of a computer Description automatically generated](./media/image6.14.png)

15. Close the **Visual Studio Code** tab then select **Sync** to
    synchronize the changes.

     ![A screenshot of a computer Description automatically generated](./media/image46.png)

16. Select **Preview | Desktop**.

     ![A screenshot of a computer Description automatically generated](./media/image47.png)

17. The output should now include the bubble chart. Hover your cursor
    over the bubbles to verify the data.

     ![A screenshot of a search engine Description automatically generated](./media/image48.png)

**Summary:** In this lab, you have learnt how to add JavaScript code to
a page to render data from Microsoft Dataverse as a chart by using an
external charting library with the data that's retrieved from Dataverse
by using portals Web API.
