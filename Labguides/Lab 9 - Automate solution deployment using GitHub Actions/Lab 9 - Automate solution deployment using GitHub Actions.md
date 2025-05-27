**實驗 9：使用適用於 Microsoft Power Platform 的 GitHub Actions
自動部署解決方案**

## **任務 1：創建應用程序註冊**

1.  使用  <https://portal.azure.com/#home> 和 Office 365 租戶憑據登錄到
    Microsoft Azure 門戶。

2.  選擇 **Get started**（開始）。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  在“您計劃如何使用 Azure” 頁面上選擇 “**Skip** ”。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  在“現在，讓我們帶你瞭解 Azure”頁面上選擇 “**Skip**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在門戶的**主**頁上，在搜索框中鍵入 **Microsoft Entra
    ID**，然後從下面建議的服務列表中選擇它。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  在左側導航窗格中，展開 **Manage** （管理），然後選擇 **App
    registrations** （應用程序註冊）。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

7.  在 **App registrations** 頁面上選擇 **+ New registration**。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

8.  在 **App registrations** （應用程序註冊）
    頁面上，輸入應用程序的註冊信息，如表中所述。

[TABLE]

> ![A screenshot of a computer application Description automatically
> generated](./media/image7.png)

9.  選擇 **Register** （註冊） 以創建應用程序註冊。.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

10. 此時將顯示應用程序註冊概述頁面。通過在左側導航窗格中選擇**Certificates
    & secrets** 來添加客戶端密鑰。選擇 **Client secrets** （客戶端密鑰）
    選項卡，然後選擇 **+ New client secret**（新建客戶端密鑰）。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

11. 為您的客戶端密鑰添加給定**描述** – **My sample client
    secret**（我的示例客戶端密鑰）。選擇密鑰的**過期時間**，如
    **Recommended： 180 days （6 months）** （建議：180 天（6
    個月）），然後選擇 **Add** （添加）。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

12. 將 **secret's value and ID**
    保存在記事本中，以便在客戶端應用程序代碼中使用。離開此頁面後，此密鑰值將不再顯示。

> **重要提示：**在複製密鑰值（而不是
> ID）之前，請勿離開客戶端密鑰頁面，因為您將無法再次訪問密鑰值。
>
> ![](./media/image11.png)

## **任務 2：創建新的應用程序用戶**

按照以下步驟創建應用程序用戶並將其綁定到您的應用程序註冊。

1.  使用您的 Office 365
    租戶憑據 <https://admin.powerplatform.microsoft.com/> 登錄到 Power
    Platform 管理中心。

2.  在左側導航窗格中選擇 **Environments**，然後在列表中選擇 **Dev One**
    環境以顯示環境信息。

> ![](./media/image12.png)

3.  選擇頁面右側 **S2S 應用程序**下的 **See all** 鏈接。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  選擇 + **New app user**。

> ![](./media/image14.png)

5.  在 **Create a new app user** （創建新應用用戶） 滑出時，選擇 **+ Add
    an app**。

> ![A screenshot of a login page Description automatically
> generated](./media/image15.png)

6.  開始在搜索字段中鍵入應用程序註冊的名稱 -
    **Mytestingapp**，然後在結果列表中選擇（選中）它。接下來，選擇
    **Add**（添加）。

> ![](./media/image16.png)

7.  返回 **Create a new app user** 滑出，從下拉列表中選擇目標 **Business
    unit**。選擇 **Security roles** 前面的 **pencil
    icon**，為應用用戶選擇 **System Administrator**
    （也稱為服務主體），然後選擇 **Save** 。 

> ![A screenshot of a login page Description automatically
> generated](./media/image17.png)

8.  選擇 **Create**。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

9.  您應該在顯示的應用程序用戶列表中看到新的應用程序用戶。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

## **任務 3：構建模型驅動應用**

按照以下步驟構建模型驅動應用。

1.  在瀏覽器中，導航到 [https://make.powerapps.com](https://make.powerapps.com/) 並使用您的憑據登錄。單擊標題中的環境選擇器下拉列表，然後選擇您的開發環境。

> ![](./media/image20.png)

2.  單擊左側導航欄中的 **Solutions** 區域，然後單擊 **New solution**
    按鈕以創建新解決方案。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

3.  輸入解決方案的 **Display name** （顯示名稱） 作為 **GitHub Lab，
    Name – GitHubLab**。在 Publisher 下選擇 **+New publisher**。

> ![](./media/image22.png)

4.  對於此實驗室，請輸入 “**GitHub Lab**” 作為**顯示名稱**，輸入
    “**GitHubLab**” 作為**名稱**，輸入 “**gitlab**”
    作為**前綴**，然後選擇 **Save** and **Close （**保存並關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  在新解決方案面板上，選擇 **publisher – GitHub Lab**
    您剛剛創建的，然後單擊 **Create** （創建）
    以在環境中創建新的非託管解決方案。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

6.  您的新解決方案將為空，您需要向其添加組件。在本實驗中，我們將創建一個自定義表。單擊頂部導航欄中的
    **+ New** 下拉列表，然後選擇 **Table \> Set advanced properties**。

> ![](./media/image25.png)

7.  輸入**顯示名稱 – Time Off Request**，將為您生成複數名稱。單擊
    **Save** 創建表。

> ![](./media/image26.png)

8.  創建表後，選擇 Table from breadcrumb
    導航以返回到解決方案視圖以添加另一個組件。

> ![](./media/image27.png)

9.  單擊 **+ New** 下拉列表，然後單擊 **App**，最後單擊 **Model-driven
    app**。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

10. 輸入應用程序名稱 – **Time Off Requests**，然後單擊 **Create** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

11. 在應用程序設計器中，單擊 **+ Add page**。

> ![](./media/image30.png)

12. 選擇 **Dataverse table**。

> ![](./media/image31.png)

13. 選擇 **Time Off Request**，選中 **Show in navigation** 複選框。選擇
    **Add**。

> ![](./media/image32.png)

14. 單擊 **Publish**，發佈作完成後，單擊 **Play**。

> ![](./media/image33.png)

15. 這將帶您進入應用程序，以便您查看它的外觀。您可以使用該應用程序並在滿意時關閉選項卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

## **任務 4：創建 GitHub 帳戶**

**注意：**如果您已有 GitHub 帳戶，則可以跳過此任務並轉到下一個任務。

1.  轉到  [https://github.com](https://github.com/) 並單擊 **Sign up**
    （註冊） 或 **Start a free trial** （（如果您已有賬戶，請登錄）。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

2.  輸入您的**電子郵件 ID**，然後單擊 **Continue** （繼續）。

> ![A screen shot of a computer Description automatically
> generated](./media/image36.png)

3.  保留自動生成的密碼或創建自己的密碼，然後單擊 **Continue** （繼續）。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

4.  輸入**用戶名** – **Labtesting1**，然後單擊 **Continue**
    （繼續）。如果給定的用戶名不可用，則輸入不同的用戶名。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

5.  選擇 **Continue**（繼續）。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  在“驗證您的帳號”頁面上，選擇 **Verify**。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

7.  完成驗證過程並使用通過電子郵件 ID 收到的啟動代碼。

8.  在出現的 'Sign in to GitHub' 窗口中選擇 **Sign in** （登錄）。

> ![](./media/image41.png)

9.  選擇 **Skip personalization** （跳過個性化）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

## **任務 5：為服務主體身份驗證創建新密鑰**

1.  創建賬戶後，通過 **Select Create repository** （創建存儲庫）
    創建存儲庫。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> 您可能會看到以下備用著陸屏幕：
>
> ![Create a new repository](./media/image44.png)

2.  創建新存儲庫並將其命名為 **'poweractionslab'**。確保選擇 **Add a
    README file** （添加自述文件） 以啟動存儲庫，然後選擇 **Create
    repository** （創建存儲庫）。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

3.  導航到您的存儲庫，然後單擊 **Settings**（設置）。

> ![](./media/image46.png)

4.  在左側窗格中，展開 **Secrets and variables**（密鑰和變量），然後單擊
    **Actions**（作）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  向下滾動，然後選擇 **New repository secret** （新建存儲庫密鑰）。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  在 Secrets （機密） 頁面上，將機密命名為
    '**PowerPlatformSPN**'。使用在 Microsoft Entra
    中創建的應用程序註冊中的客戶端密碼值（您已保存在記事本中），將其輸入到
    **Secret** 字段中，然後選擇 **Add
    secret**。在本實驗的後面部分，用於定義 GitHub 工作流程的 YML
    文件中將引用客戶端密鑰。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

客戶端密鑰現在安全地存儲為 GitHub 密鑰。

## **任務 6：創建工作流以將解決方案文件導出並解壓縮到新分支**

1.  單擊上述水平調色板中的 **Actions**。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

2.  單擊 **Configure** 在 **Simple workflow** 框下的 Recommended for
    this repository 部分。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

3.  這將啟動一個新的 YAML 文件，其中包含一個基本工作流，以幫助您開始使用
    GitHub作。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

4.  刪除預先創建的內容，粘貼 [export-and-branch-solution-with-spn-auth.yml](https://github.com/microsoft/powerplatform-actions-lab/blob/main/sample-workflows/export-and-branch-solution-with-spn-auth.yml) 文件中的內容。在
    VM 上的新選項卡中打開給定的鏈接。

> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

5.  將文件**重命名**為 **export-and-branch-solution.yml。**

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

6.  在\<ENVIRONMENTURL\>第 28 行更新，其中包含要從中導出的開發環境的
    URL。

> ![Rename and replace content.](./media/image55.png)
>
> 要獲取環境 URL，請轉到 **Power Platform 管理中心**。從左側導航中選擇
> **Environments**，單擊 **Dev One**，然後複製 環境 URL。
>
> ![](./media/image56.png)

7.  將 **Environment URL 粘貼**到 yml 文件中。確保添加 https://。您的
    URL 應採用給定格式 **-** https://orgfc5xxxfd.crm.dynamics.com

> ![](./media/image57.png)

8.  更新\<APPID\>和 \<TENANT ID\> 使用您的值。若要獲取這兩個值，請轉到
    Azure 門戶，然後選擇 “**Home \> Microsoft Entra ID \> App** 註冊”
    ，然後選擇 “**All applications**” 選項卡，然後選擇
    “**Mytestingapp**” 。

> ![A screen shot of a computer Description automatically
> generated](./media/image58.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

9.  將值粘貼到第 29 行和第 30 行。.

> ![](./media/image60.png)

10. 在代碼的第 12 行，將默認值 ALMLab 更改為
    GitHubLab，在本例中為我們的解決方案名稱。確保你沒有留下任何空間，並按照給定的方式正確書寫。如果您為解決方案指定了不同的名稱，請在此處寫下該名稱。

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

11. 現在，您可以提交更改了。選擇 “**Commit changes**” ，然後在打開的
    “提交更改” 窗格中，選擇 “**Commit changes**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)
>
> 恭喜，您剛剛使用以下作創建了您的第一個 GitHub 工作流程：

- **我是誰：**確保您可以成功連接到要從中導出的環境。

- **Export Solution：**從開發環境中導出解決方案文件。

- **解壓縮解決方案：**從服務器導出的解決方案文件是包含合併配置文件的壓縮
  （zip）
  文件。這些初始文件不適合源代碼管理，因為它們的結構不便於源代碼管理系統正確地對文件進行差分處理並捕獲要提交到源代碼管理的更改。您需要“解壓縮”解決方案文件，使其適合於源代碼控制存儲和處理。

- **Branch Solution：**創建一個新分支來存儲導出的解決方案。

## **任務 7：測試導出和解包工作流**

1.  接下來，要測試工作流是否運行，請從上面的水平調色板中選擇 **Actions**
    ，然後選擇左側窗格上 **All workflows** 下列出的
    **export-and-branch-solution** 工作流。

> ![](./media/image63.png)

2.   選擇 **Run workflow** （運行工作流程），然後再次選擇 **Run
    workflow**
    （運行工作流程）。如果您的解決方案名稱與“GitHubLab”不同，請更改此處的值，但保持其他值不變。

> ![](./media/image64.png)

3.  5-10 秒後，工作流將啟動，您可以選擇正在運行的工作流來監控進度。

> ![](./media/image65.png)
>
> ![](./media/image66.png)

4.  工作流程完成後，驗證是否已創建一個新分支，並將解決方案解壓縮到
    **solutions/GitHubLab** 文件夾。導航到 **Code** （代碼） 選項卡。 

> ![A screenshot of a computer Description automatically
> generated](./media/image67.png)

5.  展開 **Branches** 下拉列表。

> ![](./media/image68.png)

6.  選擇由作創建的分支 — **GitHubLab-xxxx-xxxx**。

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

7.  驗證是否已在新分支中創建 **solutions/GitHubLab** 文件夾h

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

8.  要創建拉取請求以將更改合併到主分支中，請單擊 “**Contribute** ”
    ，然後在浮出控件中單擊 “打開拉取請求”。

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

9.  在 Open a Pull request（打開拉取請求）屏幕上，保持標題不變，然後單擊
    **Create pull request**（創建拉取請求）。

> ![A screenshot of a computer Description automatically
> generated](./media/image72.png)

10. 屏幕將更新，顯示新創建的拉取請求。創建拉取請求後，將提供確認，表明我們的分支與主分支沒有衝突。

> ![A screenshot of a computer Description automatically
> generated](./media/image73.png)

11. 此確認意味著更改可以自動合併到 main 分支中。單擊 **Merge pull
    request**（合併拉取請求）。 

> ![A screenshot of a computer Description automatically
> generated](./media/image74.png)

12. 單擊** Confirm merge**。

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)

13. （可選）單擊 delete branch （刪除分支） 以清理現已失效的分支。

> ![A close up of a message Description automatically
> generated](./media/image76.png)

14. 單擊 **Code** （代碼）。

> ![](./media/image77.png)

15. 您將導航回默認 （main） 分支，並驗證解決方案現在也在那裡可用。

> ![A screenshot of a computer Description automatically
> generated](./media/image78.png)
