# **实验 7：向站点添加高级客户端功能**

**预计持续时间：** 35 分钟

**目标：**在本实验中，您将学习如何将 JavaScript 代码添加到页面，以将
Microsoft Dataverse 中的数据呈现为图表。

### **任务 1：在 AI 的帮助下创建站点**

1.  使用 +++<https://make.powerpages.microsoft.com/>+++转到 Power
    Pages。确保您处于 **Dev One** 环境中。.

> ![](./media/image1.png)

2.  选择 **Skip** on **Tell us about yourself**
    page（告诉我们关于您自己的页面）。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  输入给定的描述以创建站点，然后单击 **generate** 图标。

> +++**Create a site for customers to find financial advisors at a bank
> based on their qualifications, and areas of expertise**+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Copilot 会根据您的描述生成站点名称和 Web 地址。在本例中，站点名称为
    **'Finance Advisor Search'**。保留生成的站点名称和地址，然后选择
    **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Copilot 会生成一个主页布局，您可以滚动浏览和浏览生成的页面。选择
    **Next** 接受建议的布局。

> **注：** 您可以选择 **Try again** （重试） 以生成新布局。
>
> ![A screenshot of a website Description automatically
> generated](./media/image5.png)

6.  Copilot 会根据描述生成更多可在站点中使用的页面。在此示例中，选中了
    Contact us， Advisor search， Advisor profile 和 Advisor contact
    pages，然后选择 **Done** 以完成站点创建。

> **请注意：** 如果您的 copilot
> 为您的网站生成的页面与上述页面不同，那么您可以选择其中的一些页面。
>
> ![](./media/image6.png)

7.  站点创建可能需要几分钟时间。完成后，您将被重定向到在设计工作室中打开的站点，您可以进一步自定义该站点。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

### **任务 2：创建站点设置**

要创建站点设置，请执行以下步骤。

1.  选择省略号 （...） 菜单，然后选择 **Portal management**。

> 门户管理应用程序将在新选项卡中打开。
>
> ![](./media/image8.png)

2.  选择 **Site Settings**（站点设置）。选择 **+ New**。**.**

> ![](./media/image9.png)

3.  输入以下信息，然后选择 **Save** （保存）。

    - **名称 -** +++Webapi/account/enabled+++

    &nbsp;

    - **网站 -** 选择您的网站

    &nbsp;

    - **值**- +++true+++

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  选择 **+ New。**

> ![](./media/image11.png)

5.  输入以下信息，然后选择 **Save & Close**。

    - **名称 -** +++Webapi/account/fields+++

    &nbsp;

    - **网站 -** 选择您的网站

    &nbsp;

    - **值 -** +++name,numberofemployees,revenue+++

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

### **任务 3：创建表权限**

要创建表权限，请执行以下步骤。

1.  切换到 Power Pages 设计工作室，新创建的网站将在其中打开。

> **注意：**您可以关闭 Copilot 窗格以获得更好的可见性。
>
> ![](./media/image13.png)

2.  选择 **Security** workspace，然后选择 **Table permissions**。

> ![A screenshot of a computer security Description automatically
> generated](./media/image14.png)

3.  选择 **+ New permission。**

> ![](./media/image15.png) 

4.  填写以下信息：

    - **名称 -** +++Account+++

    &nbsp;

    - **表** - +++Account (account)+++

    &nbsp;

    - **访问类型 -** Global

    &nbsp;

    - **权限 –** Read

> ![](./media/image16.png)

5.  选择 **Add roles**（添加角色），然后添加 **Anonymous
    Users**（匿名用户）和 **Authenticated
    Users**（经过身份验证的用户）。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

6.  选择 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

7.  选择 **Save** （保存） 以使此数据对任何人可见。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image19.png)

8.  您可以看到 ‘The table permission ‘Account’ have successfully been
    saved’。

> ![](./media/image20.png)

### **任务 4：测试 Web API** 

1.  要测试 Web API，请在添加网站地址后打开以下 URL
    +++[https://**yourwebsite**.powerappsportals.com/\_api/accounts?$select=name,numberofemployees,revenue](https://yourwebsite.powerappsportals.com/_api/accounts?$select=name,numberofemployees,revenue)+++

2.  如果出现 IF permission requested 对话框，请选择 **Accept** 。

> ![A screenshot of a application Description automatically
> generated](./media/image21.png)

3.  您的输出应类似于下图。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

### **任务 5：创建内容页面并检索数据**

若要创建内容页并添加用于检索和转换数据的 JavaScript
代码，请执行以下步骤：

1.  在 design studio 中，选择 **Pages** 工作区，然后选择 **+ Page**。

> ![](./media/image23.png)

2.  输入 +++**Chart**+++ 作为**页面名称**。

3.  确保 **Add page to main navigation** （将页面添加到主导航） 选项。

4.  选择 **Start from blank** （从空白开始） 布局。

5.  选择 **Add**。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

6.  选择 **Edit code** （编辑代码）。

> ![](./media/image25.png)

7.  在弹出对话框中，选择 **Open Visual Studio Code**。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

8.  如果出现弹出窗口并要求您允许扩展 Power Platform 工具使用 Microsoft
    登录，请选择 **Allow**。

> ![A black screen with white text Description automatically
> generated](./media/image27.png)

9.  它将获取您的数据。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

10. 在 Visual Studio Code 编辑器中，选择 **Chart.en-US.customjs.js**
    文件。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

11. 附加以下脚本：

> function makeChart(rawData) {
>
> // transform raw data into plotting array
>
> var rData = rawData.value.map(({
>
> name,
>
> revenue,
>
> numberofemployees
>
> }) =\> ({
>
> "x": numberofemployees,
>
> "y": revenue,
>
> "z": (!revenue) ? 1 : numberofemployees / revenue,
>
> "name": name
>
> }));
>
> console.log(rData);
>
> }
>
> // retrieve accounts data using portals Web API
>
> $(document).ready(function() {
>
> $.get('/\_api/accounts?$select=name,numberofemployees,revenue',
> makeChart, 'json');
>
> });

12. 按 **Ctrl + S** 键盘快捷键（在 Mac 上为 **⌘ + S**）保存文件。

> ![A screen shot of a computer program Description automatically
> generated](./media/image30.png)

13. 关闭 **Visual Studio Code** 选项卡。当系统提示同步更改时，选择
    **Sync** （同步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

14. 选择 **Preview | Desktop**。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

15. 显示页面时，按 **F12** 键可显示浏览器开发人员工具。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

16. 选择 **Console** （控制台） 选项卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

17. 验证控制台输出是否包含与之前检索的数据相同的数据，只是它现在显示为已转换。

> ![A screenshot of a computer program Description automatically
> generated](./media/image36.png)

18. 现在，数据结构已准备好进行绘图。为数据点分配适当的标签：

    - **name** - 公司名称

    &nbsp;

    - **x** - 员工人数

    &nbsp;

    - **y** - 公司收入（单位：千）

    &nbsp;

    - **z** - 每个员工的收入（计算）

### **任务 6：添加外部库功能**

本练习使用 Highcharts.js
库（免费供个人或非营利组织使用）根据数据创建气泡图。

1.  切换到 design studio。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

2.  选择页脚，然后选择 **Edit code** （编辑代码）。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

3.  在弹出对话框中，选择 **Open Visual Studio Code**。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

4.  将以下代码附加到文件末尾。

> \<script src="https://code.highcharts.com/highcharts.js"\>\</script\>
>
> \<script
> src="https://code.highcharts.com/highcharts-more.js"\>\</script\>
>
> ![](./media/image40.png)

5.  按 **Ctrl + S** 键盘快捷键（在 Mac 上为 **⌘ + S**）保存文件。

6.  关闭 **Visual Studio Code** 选项卡。

7.  选择工具栏上的 **Edit code** （编辑代码） 以打开页面的 Visual Studio
    Code。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  在 Visual Studio Code for the Web 弹出窗口中选择 “编辑时 **Open
    Visual Studio Code**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

9.  选择 **Chart.en-US.customjs.js** 文件。

> ![A screen shot of a computer program Description automatically
> generated](./media/image42.png)

10. 替换文件以更改 **makeChart** 函数，如下所示：

> 备注：此处，替换文件意味着您仅修改现有文件。.
>
> function makeChart(data) {
>
> console.log(data);
>
> var rData = data.value.map(({
>
> name,
>
> revenue,
>
> numberofemployees
>
> }) =\> ({
>
> "x": numberofemployees,
>
> "y": revenue,
>
> "z": (!revenue) ? 1 : numberofemployees / revenue,
>
> "name": name
>
> }));
>
> console.log(rData);
>
> // new code to plot the data
>
> Highcharts.chart($('.mychart')\[0\], {
>
> title: {
>
> text: "Customers efficiency"
>
> },
>
> legend: {
>
> enabled: false
>
> },
>
> xAxis: {
>
> title: {
>
> text: "Number of employees"
>
> }
>
> },
>
> yAxis: {
>
> title: {
>
> text: "Turnover ($K)"
>
> }
>
> },
>
> tooltip: {
>
> pointFormat: '\<strong\>{point.name}\</strong\>\<br/\>Employed:
> {point.x}\<br\>Turnover ($K): ${point.y}',
>
> headerFormat: ''
>
> },
>
> series: \[{
>
> type: 'bubble',
>
> data: rData
>
> }\]
>
> });
>
> }
>
> // retrieve accounts data using portals Web API
>
> $(document).ready(function() {
>
> $.get('/\_api/accounts?$select=name,numberofemployees,revenue',
> makeChart, 'json');
>
> });
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image43.png)

11. 按 **Ctrl + S** 键盘快捷键（在 Mac 上为 **⌘ + S**）保存文件。

12. 选择 **Chart.en-US.webpage.copy.html** 文件。

> ![A screenshot of a computer program Description automatically
> generated](./media/image44.png)

13. 将以下代码插入内部\<div\>元素：

> \<figure\>
>
> \<div class="mychart"\>\</div\>
>
> \</figure\>
>
> ![A screen shot of a computer Description automatically
> generated](./media/image45.png)

14. 按 **Ctrl + S** 键盘快捷键（在 Mac 上为 **⌘ + S**）保存文件。

15. 关闭 **Visual Studio Code** 选项卡，然后选择 **Sync** 同步更改。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

16. 选择 **Preview | Desktop**。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

17. 输出现在应包含气泡图。将光标悬停在气泡上以验证数据。

> ![A screenshot of a search engine Description automatically
> generated](./media/image48.png)

**摘要：**在本实验中，您学习了如何将 JavaScript
代码添加到页面，以使用外部图表库将 Microsoft Dataverse
中的数据呈现为图表，其中包含使用门户 Web API 从 Dataverse 检索的数据。
