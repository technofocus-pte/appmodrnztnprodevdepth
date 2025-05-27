**實驗 5：創建自定義 API**

**預計持續時間：** 35 分鐘

**目標：**在本實驗中，您將學習構建 Dataverse 自定義 API
來執行一些自定義邏輯。然後，您將使用 Power Automate
流中某個步驟中的自定義 API。

**任務 1：創建自定義 API 項目**

1.  單擊 VM 的 “**Start**” 菜單，在搜索框中鍵入 “命令提示符” ，然後選擇
    **“Open**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  運行以下命令以創建名為 **CustomAPILab** 的新文件夾。

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  將 directory 更改為您創建的文件夾。

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  您現在應該位於 CustomAPIlAB 文件夾中。運行以下命令以初始化新的
    Dataverse 插件類庫。

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Dataverse 插件類庫創建應該成功。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  運行以下命令以在 Visual Studio 中打開項目。

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  如果詢問，請選擇 **Microsoft Visual Studio 2022**，然後選擇 **Just
    once**。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  如果系統要求您登錄到 Visual Studio，請在登錄頁面上選擇“**Skip this
    for now**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  選擇 “**General**” 作為 “開發設置” ，選擇 **“Dar**k”
    作為顏色主題，然後選擇 “**Start Visual Studio**” 。

> **注：** 如果您直接導航到項目，請忽略此步驟。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. 項目應在 Visual Studio 中打開。

> ![](./media/image10.png)

11. 右鍵單擊 Plugin1.cs 文件並將其重命名為 **MatchPlugin.cs**。

> ![](./media/image11.png)

12. 選擇 **Yes** （是） 以重命名文件對話框。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. 右鍵單擊 CustomAPILab 項目，然後選擇 **Manage NuGet Packages**。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. 搜索 **System.Text.RegularExpressions** 並選擇 **Install**
    （安裝）。

> ![](./media/image14.png)

15. 在 “預覽更改”窗口中，選擇 “**Apply**” 以允許 Visual Studio
    對解決方案進行更改。

> ![](./media/image15.png)

16. 選擇 **I Accept** （我接受） 以接受許可條款。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17. 打開 **MatchPlugin.cs** 文件。

> ![](./media/image17.png)

18. 在 'using System;' 語句下面添加以下語句，即第 3 行。

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. 在 ExecuteDataversePlugin 方法內和 var
    上下文行之後添加以下行。這些行從自定義 API
    調用時傳遞的輸入參數中獲取值。

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. 後面添加以下行以獲取跟蹤服務。

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. 添加以下行以將輸入值寫入 trace。

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. 在 After 後添加以下行以調用 Regex.Match 方法。

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. 將結果寫入 trace。

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. 最後，添加以下行以設置輸出參數 Matched。

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. 您的 execute 方法現在應如下所示。

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. 選擇 **Build | Build Solution**。

> ![](./media/image26.png)

27. 項目應該成功構建。

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**任務 2：註冊自定義 API 插件**

1.  打開命令提示符並運行以下命令以啟動插件註冊工具。

> +++pac tool prt+++
>
> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  選擇 **+ Create New Connection**。

> ![](./media/image29.png)

3.  選擇 **Office 365**，提供您的憑據，然後選擇 **Login**。

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  使用 **M365 管理員租戶 ID** 登錄，然後選擇 “**Next**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  輸入 **M365 管理員租戶 ID 的密碼**，然後選擇 “**Sign in**” 。

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  檢查是否選擇了 **Dev One** 環境。

7.  選擇 **Register | Register New Assembly**。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  選擇。。。在步驟 1 下，然後瀏覽到 **CustomAPILab\bin\Debug\net462**
    文件夾。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  選擇 **CustomAPILab.dll** 然後選擇 **Open**。

> ![](./media/image35.png)

10. 選擇 **Register Selected Plugins**（註冊所選插件）。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. 選擇 **OK**
    到成功消息。您的插件已準備好連接到我們將在下一個任務中創建的自定義
    API。

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**任務 3：創建自定義 API**

1.  使用 +++<https://make.powerapps.com/>+++ 導航到 Power Apps
    製作者門戶，確保您位於 **Dev One** 環境中。

2.  選擇 **Solutions** 在左側導航欄中。選擇 **+ New Solution**。

> ![](./media/image38.png)

3.  在 Display Name（顯示名稱）中輸入 +++**Custom API Lab**+++。

4.  在 Publisher 下拉列表中選擇 **CDS Default Publisher**。

5.  選擇 **Create**。這將創建一個包含我們的組件的自定義解決方案。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  選擇 **+ New | More | Other | Custom API。**

> ![](./media/image40.png)

7.  輸入以下信息：

    - **唯一名稱：**+++contoso_match+++

    &nbsp;

    - **名稱：**+++Match+++

    &nbsp;

    - **顯示名稱：**+++Match+++

    &nbsp;

    - **描述：**+++Match a string+++

    &nbsp;

    - **綁定類型：**+++Global+++

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  在 Plugin Type （插件類型） 中，選擇搜索圖標並找到您的插件 -
    **CustomAPILab.MatchPlugin**。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  選擇 **Save and Close** （保存並關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. 選擇 **Done**。

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11. 選擇 **+** **New | More| Other | Custom API Request Parameter**。

> ![](./media/image44.png)

12. 對於 **Custom API** （自定義 API），選擇 **Search** （搜索）
    圖標，然後選擇 **Match** （您的自定義 API）。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. 為簡單起見，請為“唯一名稱”、“名稱”、“顯示名稱”和“描述”輸入
    +++**StringIn**+++。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. 為 Type （類型） 選擇 **String** （字符串）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. 選擇 **Save and Close** （保存並關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. 選擇 **Done**。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. 要再添加一個自定義 API 請求參數，請選擇**+** **New | More| Other |
    Custom API Request Parameter**。

> ![](./media/image50.png)

18. 對於 **Custom API** （自定義 API），選擇 **Search** （搜索）
    圖標，然後選擇 **Match** （您的自定義 API）。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. 為簡單起見，請為 Unique Name、Name、Display Name 和 Description 輸入
    **Pattern**。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. 為 Type （類型） 選擇 **String** （字符串）。

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. 選擇 **Save and Close** （保存並關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. 選擇 **Done**。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. 選擇 **New | More | Other| Custom API Response Property**。

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. 對於 **Custom API** （自定義 API），選擇 **Search** （搜索）
    圖標，然後選擇 **Match** （您的自定義 API）。

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. 為簡單起見，請為“**唯一名稱**”、“**名稱**”、“**顯示名稱**”和“**描述**”輸入
    +++**Matched**+++。

26. 為 **Type** （類型） 選擇 **Boolean** （布爾值）。

> ![](./media/image58.png)

27. 選擇 **Save and Close** （保存並關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. 選擇 **Done**。

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. 您的解決方案組件列表應如下所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**任務 4：使用 Power Automate 中的自定義 API**

1.  在解決方案中，選擇 **+ New | Automation | Cloud Flow | Instant**。

> ![](./media/image62.png)

2.  輸入 +++**String match**+++ 作為 流名稱，選擇 **Manually trigger a
    flow** 觸發器，然後選擇 **Create**。

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  選擇  **+ New Step**。

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  搜索 perform （執行） 並選擇 **Perform an unbound action**
    （執行未綁定的作）。

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  在 Action Name 列表中，找到並選擇 **contoso_match**。

> ![](./media/image66.png)

6.  在 **StringIn** 中輸入 **myemail@outlook.com**
    電子郵件地址。在這裡，您可以鍵入任何有效的簡單電子郵件地址。

> ![](./media/image67.png)

7.  在 Pattern （模式）
    中輸入以下正則表達式。這是一個簡單的電子郵件模式。
    其他 [*examples*](https://regexlib.com/DisplayPatterns.aspx/) （示例）可用。

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  您的流程應如下所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  選擇 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. 保存完成後，選擇 **Test**（測試）。

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. 選擇 **Manually**（手動），然後選擇 **Test**（測試）。

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. 選擇 **Run flow**（運行流）。

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. 選擇 **Done**。

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. 流程完成後，選擇 **Perform an unbound action** （執行未綁定作）
    以展開並查看結果。

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**摘要：**在本實驗中，您學習了如何構建自定義作並從 Power Automate
流中使用它。自定義 API作contoso_match現在也可用於使用平臺 API 直接調用。
