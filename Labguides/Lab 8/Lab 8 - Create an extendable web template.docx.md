# **Lab 8: Create an extendable web template**

**Estimated Duration:** 25 min

**Objective:** In this lab, you will learn how to extend Liquid
templates by using extend and block tags, how to reuse Liquid templates
by using the include tag and how to apply table permissions to the
results of the new template.

### **Task 1: Create a partial template**

Your first task is to create a partial template that won't be used to
render a page but will instead be inserted into another template.

1.  Sign in to Power Pages
    +++**https://make.powerpages.microsoft.com/**+++. If your site is already open, you can skip Steps 1 through 3.

2.  Select the target environment **Dev One** in the upper-right corner.

     ![](./media/image1.png)

3.  Under **Active sites** tab, you can see your site – **Finance
    Advisor Search**. Select **Edit**.

     ![](./media/image2.png)

4.  Expand the extension menu (ellipsis), and then select **Portal
    management** to open the Portal Management app.

     ![](./media/image3.png)

5.  Select **Web Templates**.

     ![A screenshot of a computer Description automatically generated](./media/image4.png)

6.  Select +**New**.

     ![A screenshot of a web page Description automatically generated](./media/image5.png)

7.  Enter the following values:

    **Note**: Delete any extra characters that may appear after pasting the code.

    - **Name** - +++Directory+++

    &nbsp;

    - **Website** - Select your current website - Finance Advisor Search

    &nbsp;

    - **Source** - Enter the following content:

    ```  

     {% fetchxml accounts %}
    
     <fetch>
    
     <entity name="account">
    
     <attribute name="name" />
    
     </entity>
    
     </fetch>
    
     {% endfetchxml %}
    
     {% if accounts.global_permission_granted %}
    
     <ul>
    
     {% for account in accounts.results.entities %}
    
     <li>{{ account.name }}</li>
    
     {%- endfor -%}
    
     </ul>
    
     {% else %}
    
    <div class="alert alert-warning">You do not have permissions to access the directory.</div>
    
     {% endif %}

    ```
    
     ![A screenshot of a computer Description automatically generated](./media/image6.png)

8.  Select **Save & Close**.

     ![A screenshot of a computer Description automatically generated](./media/image7.png)

### **Task 2: Extend an existing template**

Next, you'll create a new template that extends an existing Liquid
template and then insert the template that you previously created.

1.  On the **Web Templates** page,
    select **+New**.

     ![](./media/image8.png)

2.  Enter the following values:

    **Note**: Delete any extra characters that may appear after pasting the code.

    - **Name** - +++Directory Template+++

    &nbsp;

    - **Website** - Select your current website - Finance Advisor Search

    &nbsp;

    - **Source** - Enter the following content:
  
    ```

    {% extends "Layout 2 Column Wide Left" %}

    {% block aside %}
      <h2>Directory</h2>
      {% include 'Directory' %}
    {% endblock %}

    ```
    
     ![A screenshot of a computer Description automatically generated](./media/image9.png)

3.  Select **Save & Close**.

     ![A screenshot of a web template Description automatically generated](./media/image10.png)

### **Task 3: Create a page template and associate with that page**

In this task, you'll create a page template that uses your new web
template and will include the Directory output.

1.  From the left navigation pane, select **Page Templates**.
    Select +**New**.

     ![A screenshot of a computer Description automatically generated](./media/image11.png)

2.  Enter the following values:

    - **Name** - +++Directory Page Template+++

    &nbsp;

    - **Website** - Select the current website - Finance Advisor Search

    &nbsp;

    - **Type** - Select **Web Template**

    &nbsp;

    - **Web Template** - Select **Directory Template**

    &nbsp;

    - **Table Name** - Select **Web Page**

3.  Select **Save & Close**.

     ![A screenshot of a web page Description automatically generated](./media/image12.png)

### **Task 4: Test the page template**

Your next step is to test that your new template works:

1.  Return to the Power Pages design studio Home tab.

2.  Select **Sync** to synchronize the changes.

     ![A screenshot of a computer Description automatically generated](./media/image13.png)

3.  Select the **Pages** workspace. Select **+ Page**.

     ![A screenshot of a computer Description automatically generated](./media/image14.png)

4.  When prompted with the **Describe a page to design it** window, click on **Other ways to add a page**.

   ![A screenshot of a computer Description automatically generated](./media/image5.2.png)
   
6.  In the **Add a page** dialog, complete the following steps:

    a.  Enter +++**Directory**+++ as the page name.

    &nbsp;

    b.  Select **Custom layouts** and then select **Directory Page
        Template**.

    &nbsp;

    c.  Select **Add**.

     ![A screenshot of a website Description automatically generated](./media/image15.png)

     The empty page will display with the message "You don't have
     permissions to access the directory" in the right panel.

     ![](./media/image16.png)

### **Task 5: Add table permissions**

**Warning:** Granting global read permission to anonymous users is for
illustrative purposes only. Exercise caution to avoid unintentionally
exposing sensitive information by granting excessive permissions and not
including appropriate filters in your views or FetchXML expressions.

Follow these steps to add table permissions.

1.  If you've already completed Lab 7, you may skip Task 5 entirely. If not, Select **Security workspace** and then select **Table Permissions**.

     ![A screenshot of a computer security Description automatically generated](./media/image17.png)

2.  Select **+ New permission**.

     ![A screenshot of a computer Description automatically generated](./media/image18.png)

3.  Enter the following values:

    - **Name** - +++Account Directory+++

    &nbsp;

    - **Table** - Select the **Account (account)** table

    &nbsp;

    - **Access type** - Select **Global access**

    &nbsp;

    - **Permission to** - Select **Read**

     ![A screenshot of a computer Description automatically generated](./media/image19.png)

4.  Select **Add roles**.

5.  Select **Anonymous users** and **Authenticated users**.

     ![A screenshot of a computer Description automatically generated](./media/image20.png)

6.  Select **Save**.

     ![A screenshot of a computer Description automatically generated](./media/image21.png)

7.  Select **Save**.

     ![A screenshot of a computer error message Description automatically generated](./media/image22.png)

### **Task 6: Test the template**

Your final task is to test your new template:

1.  Select the **Pages** workspace and then select
    the **Directory** page.

     ![A screenshot of a computer Description automatically generated](./media/image23.png)

2.  Select **Preview | Desktop**.

     ![A screenshot of a computer Description automatically generated](./media/image24.png)

     **Note:** A simple browser page refresh won't be sufficient to update the data. Using this command instead rebuilds the site cache.

     The page should now be displayed and include the list of accounts in the right panel.

     ![A screenshot of a search engine Description automatically generated](./media/image25.png)

**Summary:** In this lab, you have learnt building and extending Liquid
templates. You built a new page template that includes a side panel that
lists all accounts in Dataverse.
