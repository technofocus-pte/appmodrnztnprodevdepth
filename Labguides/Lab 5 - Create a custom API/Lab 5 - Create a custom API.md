**实验 5：创建自定义 API**

**预计持续时间：** 35 分钟

**目标：**在本实验中，您将学习构建 Dataverse 自定义 API
来执行一些自定义逻辑。然后，您将使用 Power Automate
流中某个步骤中的自定义 API。

**任务 1：创建自定义 API 项目**

1.  单击 VM 的 “**Start**” 菜单，在搜索框中键入 “命令提示符” ，然后选择
    **“Open**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  运行以下命令以创建名为 **CustomAPILab** 的新文件夹。

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  将 directory 更改为您创建的文件夹。

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  您现在应该位于 CustomAPIlAB 文件夹中。运行以下命令以初始化新的
    Dataverse 插件类库。

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Dataverse 插件类库创建应该成功。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  运行以下命令以在 Visual Studio 中打开项目。

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  如果询问，请选择 **Microsoft Visual Studio 2022**，然后选择 **Just
    once**。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  如果系统要求您登录到 Visual Studio，请在登录页面上选择“**Skip this
    for now**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  选择 “**General**” 作为 “开发设置” ，选择 **“Dar**k”
    作为颜色主题，然后选择 “**Start Visual Studio**” 。

> **注：** 如果您直接导航到项目，请忽略此步骤。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. 项目应在 Visual Studio 中打开。

> ![](./media/image10.png)

11. 右键单击 Plugin1.cs 文件并将其重命名为 **MatchPlugin.cs**。

> ![](./media/image11.png)

12. 选择 **Yes** （是） 以重命名文件对话框。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. 右键单击 CustomAPILab 项目，然后选择 **Manage NuGet Packages**。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. 搜索 **System.Text.RegularExpressions** 并选择 **Install**
    （安装）。

> ![](./media/image14.png)

15. 在 “预览更改”窗口中，选择 “**Apply**” 以允许 Visual Studio
    对解决方案进行更改。

> ![](./media/image15.png)

16. 选择 **I Accept** （我接受） 以接受许可条款。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17. 打开 **MatchPlugin.cs** 文件。

> ![](./media/image17.png)

18. 在 'using System;' 语句下面添加以下语句，即第 3 行。

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. 在 ExecuteDataversePlugin 方法内和 var
    上下文行之后添加以下行。这些行从自定义 API
    调用时传递的输入参数中获取值。

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. 后面添加以下行以获取跟踪服务。

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. 添加以下行以将输入值写入 trace。

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. 在 After 后添加以下行以调用 Regex.Match 方法。

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. 将结果写入 trace。

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. 最后，添加以下行以设置输出参数 Matched。

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. 您的 execute 方法现在应如下所示。

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. 选择 **Build | Build Solution**。

> ![](./media/image26.png)

27. 项目应该成功构建。

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**任务 2：注册自定义 API 插件**

1.  打开命令提示符并运行以下命令以启动插件注册工具。

> +++pac tool prt+++
>
> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  选择 **+ Create New Connection**。

> ![](./media/image29.png)

3.  选择 **Office 365**，提供您的凭据，然后选择 **Login**。

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  使用 **M365 管理员租户 ID** 登录，然后选择 “**Next**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  输入 **M365 管理员租户 ID 的密码**，然后选择 “**Sign in**” 。

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  检查是否选择了 **Dev One** 环境。

7.  选择 **Register | Register New Assembly**。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  选择。。。在步骤 1 下，然后浏览到 **CustomAPILab\bin\Debug\net462**
    文件夹。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  选择 **CustomAPILab.dll** 然后选择 **Open**。

> ![](./media/image35.png)

10. 选择 **Register Selected Plugins**（注册所选插件）。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. 选择 **OK**
    到成功消息。您的插件已准备好连接到我们将在下一个任务中创建的自定义
    API。

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**任务 3：创建自定义 API**

1.  使用 +++<https://make.powerapps.com/>+++ 导航到 Power Apps
    制作者门户，确保您位于 **Dev One** 环境中。

2.  选择 **Solutions** 在左侧导航栏中。选择 **+ New Solution**。

> ![](./media/image38.png)

3.  在 Display Name（显示名称）中输入 +++**Custom API Lab**+++。

4.  在 Publisher 下拉列表中选择 **CDS Default Publisher**。

5.  选择 **Create**。这将创建一个包含我们的组件的自定义解决方案。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  选择 **+ New | More | Other | Custom API。**

> ![](./media/image40.png)

7.  输入以下信息：

    - **唯一名称：**+++contoso_match+++

    &nbsp;

    - **名称：**+++Match+++

    &nbsp;

    - **显示名称：**+++Match+++

    &nbsp;

    - **描述：**+++Match a string+++

    &nbsp;

    - **绑定类型：**+++Global+++

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  在 Plugin Type （插件类型） 中，选择搜索图标并找到您的插件 -
    **CustomAPILab.MatchPlugin**。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  选择 **Save and Close** （保存并关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. 选择 **Done**。

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11. 选择 **+** **New | More| Other | Custom API Request Parameter**。

> ![](./media/image44.png)

12. 对于 **Custom API** （自定义 API），选择 **Search** （搜索）
    图标，然后选择 **Match** （您的自定义 API）。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. 为简单起见，请为“唯一名称”、“名称”、“显示名称”和“描述”输入
    +++**StringIn**+++。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. 为 Type （类型） 选择 **String** （字符串）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. 选择 **Save and Close** （保存并关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. 选择 **Done**。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. 要再添加一个自定义 API 请求参数，请选择**+** **New | More| Other |
    Custom API Request Parameter**。

> ![](./media/image50.png)

18. 对于 **Custom API** （自定义 API），选择 **Search** （搜索）
    图标，然后选择 **Match** （您的自定义 API）。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. 为简单起见，请为 Unique Name、Name、Display Name 和 Description 输入
    **Pattern**。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. 为 Type （类型） 选择 **String** （字符串）。

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. 选择 **Save and Close** （保存并关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. 选择 **Done**。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. 选择 **New | More | Other| Custom API Response Property**。

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. 对于 **Custom API** （自定义 API），选择 **Search** （搜索）
    图标，然后选择 **Match** （您的自定义 API）。

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. 为简单起见，请为“**唯一名称**”、“**名称**”、“**显示名称**”和“**描述**”输入
    +++**Matched**+++。

26. 为 **Type** （类型） 选择 **Boolean** （布尔值）。

> ![](./media/image58.png)

27. 选择 **Save and Close** （保存并关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. 选择 **Done**。

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. 您的解决方案组件列表应如下所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**任务 4：使用 Power Automate 中的自定义 API**

1.  在解决方案中，选择 **+ New | Automation | Cloud Flow | Instant**。

> ![](./media/image62.png)

2.  输入 +++**String match**+++ 作为 流名称，选择 **Manually trigger a
    flow** 触发器，然后选择 **Create**。

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  选择  **+ New Step**。

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  搜索 perform （执行） 并选择 **Perform an unbound action**
    （执行未绑定的作）。

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  在 Action Name 列表中，找到并选择 **contoso_match**。

> ![](./media/image66.png)

6.  在 **StringIn** 中输入 **myemail@outlook.com**
    电子邮件地址。在这里，您可以键入任何有效的简单电子邮件地址。

> ![](./media/image67.png)

7.  在 Pattern （模式）
    中输入以下正则表达式。这是一个简单的电子邮件模式。
    其他 [*examples*](https://regexlib.com/DisplayPatterns.aspx/) （示例）可用。

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  您的流程应如下所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  选择 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. 保存完成后，选择 **Test**（测试）。

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. 选择 **Manually**（手动），然后选择 **Test**（测试）。

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. 选择 **Run flow**（运行流）。

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. 选择 **Done**。

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. 流程完成后，选择 **Perform an unbound action** （执行未绑定作）
    以展开并查看结果。

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**摘要：**在本实验中，您学习了如何构建自定义作并从 Power Automate
流中使用它。自定义 API作contoso_match现在也可用于使用平台 API 直接调用。
