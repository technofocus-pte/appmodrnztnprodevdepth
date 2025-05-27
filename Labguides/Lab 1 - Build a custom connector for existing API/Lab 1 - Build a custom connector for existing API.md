**实验 1 - 为现有 API 构建自定义连接器并在画布应用中使用该连接器**

**预计持续时间：** 35 分钟

**目标：**在本实验中，您将学习为名为 Contoso Invoicing 的现有 API
创建第一个自定义连接器，以创建画布应用，以及如何在画布应用中使用连接器。

**任务 1：查看 API**

要查看 API，请执行以下步骤：

1.  转到 +++<https://contosoinvoicing.azurewebsites.net/>+++。

2.  要选择文档链接，请单击“您可以找到 API 文档”旁边的 **here**。

> ![](./media/image1.png)

3.  查看可用的作。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  关闭文档浏览器选项卡或窗口。

5.  选择 **Open API definition** （打开 API 定义） 链接。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  下图显示了文档页面上显示的 OpenAPI 版本的示例。右键单击并选择 **Save
    as** （另存为）。

> ![Screenshot of an arrow pointing to the save as
> button.](./media/image4.png)

7.  将文件本地保存在 VM 的桌面上。您将在稍后的练习中使用此文件。

8.  关闭定义浏览器选项卡或窗口。

9.  选择 **API Key** 链接。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. 将 API 密钥复制并保存到 VM 上的记事本，因为以后需要它。

> ![](./media/image6.png)

11. 选择 **Return to home**（返回主页）。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. 选择 **Download Logo** （下载徽标）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. 将徽标图像本地保存在 VM 的桌面上;您稍后会用到它。

**任务 2：创建新解决方案**

要创建新解决方案，请执行以下步骤：

1.  转到  <https://make.powerapps.com/> 并确保您处于 **Dev One**
    环境中。

> ![](./media/image9.png)

2.  从左侧导航窗格中，选择 **Solutions**（解决方案）。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  从上部功能区中选择 **+New solution**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

4.  输入 +++**Contoso invoicing**+++ 作为 **显示名称**，然后选择 **+ New
    publisher**。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

5.  输入 +++**Contoso**+++ 作为 显示名称，输入 +++**Contoso**+++ 作为
    名称，+++**contoso**+++ 作为 前缀，然后选择 **Save**。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> **注意：**如果您收到“已存在具有匹配键值的记录”的错误消息，请忽略该消息并关闭“新建发布者”窗口。
>
> ![](./media/image14.png)

6.  现在，在 **New solution** 窗口上，为 “**Publisher**” 选择
    “**Contoso**” ，然后选择 “**Create**”
    。当您从事实际项目时，最好创建自己的发布者。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  选择 **Create** （创建） 后，请勿离开此页面。您将自动导航到“Contoso
    invoicing”解决方案。

**任务 3：创建新连接器**

要创建新的连接器，请执行以下步骤：

1.  确保您使用的是您创建的 **Contoso invoicing** 解决方案。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

2.  选择 **+ New** | **Automation** | **Custom connector**。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

3.  输入 +++**Contoso invoicing**+++ 作为**连接器名称**。

> ![](./media/image18.png)

4.  选择 **Upload** 上传图像。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

5.  选择您在**任务 1：查看 API** 中下载的连接器徽标图像。

6.  输入 +++**\#175497**+++ 作为**图标背景颜色**。

7.  输入 +++**Custom connector for Contoso Invoicing API**+++ for
    **Description** （描述）。

8.  输入 +++**contosoinvoicingtest.azurewebsites.net**+++ 作为**主机**。

> ![](./media/image20.png)

9.  选择 **Create connector**（创建连接器）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

10. 请勿离开此页面。

**任务 4：导入 OpenAPI 定义**

要导入 OpenAPI 定义，请执行以下步骤：

1.  选择 **Connector Name** 旁边的箭头。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image22.png)

2.  选择连接器的省略号 （...） 按钮，然后选择 **Update from OpenAPI
    file**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  选择 **Import**。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

4.  选择您在 **任务 1：查看 API** 中下载的 **swagger.json**
    文件，然后选择 **Open**。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

5.  选择 **Continue**（继续）。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  将主机 URL
    填写为 +++**contosoinvoicingtest.azurewebsites.net**+++，然后选择
    “**Security**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

7.  请注意，这些字段是从导入的文件中填写的。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  请勿离开此页面。

**任务 5：查看和调整定义**

要查看和调整定义，请执行以下步骤：

1.  选择 **Definition** 选项卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

2.  请花几分钟时间查看导入的作。

3.  请注意 **GetInvoice** 旁边的蓝色信息圆圈。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  选择 **GetInvoice**作。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  请注意，该作指示缺少 **Summary**。

> ![A screenshot of a phone Description automatically
> generated](./media/image32.png)

6.  输入 **Get Invoice** 作为 **Summary** 以提高可用性。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

7.  请注意 **PayInvoice**作旁边的蓝色信息圆圈，它表示缺少
    **Description**。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

8.  选择 **PayInvoice**作。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

9.  输入 **Pay an invoice** （支付发票） 作为 **Description**（描述）。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

10. 删除这两个 **NewInvoice**作，因为您不会使用它们。

> ![Screenshot showing the delete action button.](./media/image37.png)

11. 选择 **GetInvoiceSchema**作。

> ![](./media/image38.png)

12. 将 **Visibility** （可见性） 选项修改为 **internal**
    （内部），以便用户不会在其作列表中看到它，然后选择 **Update
    connector** （更新连接器）。

> ![](./media/image39.png)

13. 请勿离开此页面。

**任务 6：测试连接器**

要测试连接器，请执行以下步骤：

1.  选择 **Test** （测试） 选项卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

2.  选择 **+ New connection**。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

3.  粘贴您在 **任务 1：查看 API** 中保存的 **API Key**，然后选择
    **Create connection** （创建连接）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

4.  选择 **Refresh** （刷新） 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

5.  选择 **ListInvoiceTypes | Test Operation**。

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

6.  您应该会在正文区域看到发票类型数据。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

7.  选择 **Close** 关闭自定义连接器窗口。

> ![](./media/image46.png)

**任务 7：在画布应用中使用自定义连接器**

在此任务中，您将创建一个画布应用程序，并使用您创建的自定义连接器来显示发票列表。

1.  返回 Power Apps
    制作者门户。在显示“当前创建新的自定义连接器”的弹出窗口中选择
    “**Done**”。确保您位于 **Dev One** 环境中。

> ![](./media/image47.png)
>
> **注意：**如果门户尚未打开，请导航到
> +++<https://make.powerapps.com/>+++， 并确保您处于 **Dev One**
> 环境中。

2.  确保您使用的是您创建的 **Contoso 开票**解决方案。如果没有，请选择
    **Solutions** 并打开您创建的 **Contoso 开票**解决方案。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

3.  选择 **+ New**，然后选择 **App \> Canvas app**。

> ![](./media/image49.png)

4.  在 “应用程序名称” 中输入 **Contoso invoicing app**，为 “格式” 选择“
    **Phone**” ，然后选择 “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

5.  选择 **Skip** on welcome window（在欢迎窗口跳过）。

> ![](./media/image51.png)

6.  选择 **Data** 选项卡，选择 **+ Add data**。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

7.  展开 **Connectors**，然后选择您创建的 **Contoso invoicing**
    自定义连接器。

> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

8.  选择  **+ Add a connector**。

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

9.  粘贴您在 **任务 1：查看 API** 中保存的 API 密钥，然后选择
    **Connect**。

> ![A screenshot of a login box Description automatically
> generated](./media/image55.png)

10. 在高级警告弹出窗口中选择 **Got it** （知道了）。

> ![A screenshot of a phone Description automatically
> generated](./media/image56.png)

11. 选择 **Tree view** 选项卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

12. 选择 **+ Insert**，然后选择 **Vertical gallery**。

> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

13. 为数据选择 **ContosoInvoicing**。

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

14. 将 **Items** （项目） 设置为下面的值。

> +++ContosoInvoicing.ListInvoices().invoices+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image60.png)

15. 展开库并选择 **Subtitle**。

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

16. 将 Subtitle 的 **Text** 值设置为 +++**ThisItem.amount**+++。

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

17. 展开库，然后选择 **Title** 在库内。

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

18. 将 Title 的 **Text** 值设置为 +++**ThisItem.accountName**+++。

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

19. 库现在应如下图所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

**摘要：**在本实验中，您学习了如何为现有 API 创建自定义连接器、导入 API
定义以及在画布应用程序中使用该连接器显示发票列表。自定义连接器是基于函数的，它们调用
API 底层服务中的特定函数来返回相应的数据。
