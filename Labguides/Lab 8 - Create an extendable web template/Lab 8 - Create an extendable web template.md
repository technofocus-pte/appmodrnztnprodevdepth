# **實驗 8：創建可擴展的 Web 模板**

**預計持續時間：** 25 分鐘

**目標：**在本實驗中，您將學習如何使用 extend 和 block 標簽擴展 Liquid
模板，如何使用 include 標簽重複使用 Liquid
模板，以及如何將表權限應用於新模板的結果。

**任務 1：創建部分模板**

您的第一個任務是創建一個部分模板，該模板不會用於呈現頁面，而是將插入到另一個模板中。

1.  登錄到 Power Pages +++<https://make.powerpages.microsoft.com/>+++。

2.  在右上角選擇目標環境 **Dev One**。

> ![](./media/image1.png)

3.  在 **Active sites** （活動站點） 選項卡下，您可以看到您的網站 –
    **Finance Advisor Search**（財務顧問搜索）。選擇 **Edit**（編輯）。

> ![](./media/image2.png)

4.  展開 擴展 菜單（省略號），然後選擇 **Portal management** 打開
    門戶管理 應用。

> ![](./media/image3.png)

5.  選擇 **Web Templates**。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  選擇 +**New**。

> ![A screenshot of a web page Description automatically
> generated](./media/image5.png)

7.  輸入以下值：

    - **名稱 -** +++Directory+++

    &nbsp;

    - **網站 -** 選擇您當前的網站 - Finance Advisor Search

    &nbsp;

    - **源 -** 輸入以下內容：

> {% fetchxml accounts %}
>
> \<fetch\>
>
> \<entity name="account"\>
>
> \<attribute name="name" /\>
>
> \</entity\>
>
> \</fetch\>
>
> {% endfetchxml %}
>
> {% if accounts.global_permission_granted %}
>
> \<ul\>
>
> {% for account in accounts.results.entities %}
>
> \<li\>{{ account.name }}\</li\>
>
> {%- endfor -%}
>
> \</ul\>
>
> {% else %}
>
> \<div class="alert alert-warning"\>You do not have permissions to
> access the directory.\</div\>
>
> {% endif %}
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

8.  選擇 **Save & Close**。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

**任務 2：擴展現有模板**

接下來，您將創建一個擴展現有 Liquid
模板的新模板，然後插入您之前創建的模板。

1.  從左側導航窗格中，選擇 **Web Templates**。選擇 **+New**。

> ![](./media/image8.png)

2.  輸入以下值：

    - **名稱 -** +++Directory Template+++

    &nbsp;

    - **網站 -** 選擇您當前的網站 - Finance Advisor Search

    &nbsp;

    - **源 -** 輸入以下內容：

> {% extends "Layout 2 Column Wide Left" %}
>
> {% block aside %}
>
> \<h2\>Directory\</h2\>
>
> {% include 'Directory' %}
>
> {% endblock %}
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  選擇 **Save & Close**。

> ![A screenshot of a web template Description automatically
> generated](./media/image10.png)

**任務 3：創建頁面模板並與該頁面關聯**

在此任務中，您將創建一個頁面模板，該模板使用您的新 Web 模板，並將包含
Directory 輸出。

1.  從左側導航窗格中，選擇 **Page Templates**。選擇 **+New**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

2.  輸入以下值：

    - **名稱 -** +++Directory Page Template+++

    &nbsp;

    - **網站 -** 選擇當前網站 - Finance Advisor Search

    &nbsp;

    - **類型 -** 選擇**Web Template**

    &nbsp;

    - **Web Template** – 選擇**Directory Template**

    &nbsp;

    - **表名稱 -** 選擇 **網頁**

3.  **可選：**將文本元素添加到頁面內容中，然後輸入您選擇的文本。

4.  選擇 **Save & Close**。

> ![A screenshot of a web page Description automatically
> generated](./media/image12.png)

**任務 4：測試頁面模板**

下一步是測試新模板是否正常工作：

1.  返回到 Power Pages 設計工作室的主頁選項卡。

2.  選擇 **Sync** 以同步更改。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  選擇 **Pages** 工作區。選擇 **+ Page**。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

4.  在 **Add a page** （添加頁面） 對話框中，完成以下步驟：

    1.  輸入 +++**Directory**+++ 作為頁面名稱。

    &nbsp;

    1.  選擇 **Custom layouts** ，然後選擇 **Directory Page Template**。

    &nbsp;

    1.  選擇 **Add**。

> ![A screenshot of a website Description automatically
> generated](./media/image15.png)
>
> 空頁面將在右側面板中顯示消息 “You don't have permissions to access the
> directory” 。
>
> ![](./media/image16.png)

**任務 5：添加表權限**

**警告：**向匿名用戶授予全域讀取權限僅用於說明目的。請謹慎行事，以避免通過授予過多權限以及未在視圖或
FetchXML 表達式中包含適當的篩選器來無意中暴露敏感信息。

按照以下步驟添加表權限。

1.  選擇 “**Security workspace**” ，然後選擇 “**Table Permissions**” 。

> ![A screenshot of a computer security Description automatically
> generated](./media/image17.png)

2.  選擇 **+ New permission**。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

3.  輸入以下值：

    - **名稱 -** +++Account Directory+++

    &nbsp;

    - **表 -** 選擇 **Account (account)** 表

    &nbsp;

    - **訪問類型 -** 選擇 **Global access**

    &nbsp;

    - **權限 -** 選擇 **Read**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

4.  選擇 **Add roles**（添加角色）。

5.  選擇 **Anonymous users** （匿名用戶） 和 **Authenticated users**
    （經過身份驗證的用戶）。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  選擇 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  選擇 **Save** （保存）。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image22.png)

**任務 6：測試模板**

您的最後一項任務是測試您的新模板：

1.  選擇 **Pages** 工作區，然後選擇 **Directory** 頁面。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

2.  選擇 **Preview | Desktop**。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> **注意：**簡單的瀏覽器頁面刷新不足以更新數據。請改用此命令重新構建站點緩存。
>
> 現在應顯示該頁面，並在右側面板中包含帳戶列表。
>
> ![A screenshot of a search engine Description automatically
> generated](./media/image25.png)

**摘要：**在本實驗中，您學習了構建和擴展 Liquid
模板。您構建了一個新的頁面模板，其中包括一個列出 Dataverse
中所有客戶的側面板。
