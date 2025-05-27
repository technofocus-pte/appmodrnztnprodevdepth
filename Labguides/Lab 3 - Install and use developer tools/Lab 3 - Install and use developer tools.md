**实验 3 - 安装和使用开发人员工具**

**预计持续时间：** 15 分钟

**目标：**在本实验中，您将学习如何从 NuGet 安装一些开发人员工具。

**任务 1：安装开发人员工具**

在此任务中，您将使用 Power Platform CLI 安装工具。

1.  要启动**命令提示符**，请转到 VM
    的“**Start**”菜单，在搜索框中键入“命令提示符”，然后选择“**Open**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  运行以下命令以安装 **Configuration Manager Tool**。

> +++pac tool cmt+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  应安装并启动 Configuration Manager Tool。关闭 Configuration Manager
    工具。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  运行以下命令以安装 **Package Deployer Tool**。

> +++pac tool pd+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  应安装并启动 Package Deployer 工具。关闭 Package Deployer 工具。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  运行以下命令以安装 **Plugin Registration Tool**。

> +++pac tool prt+++
>
> ![](./media/image6.png)

7.  应安装并启动 Plugin Registration。不要关闭 Plugin Registration
    Tool。

> ![](./media/image7.png)

**任务 2：使用插件注册工具浏览已注册的插件**

1.  选择 **Create New Connection** （创建新连接）。

> ![](./media/image8.png)

2.  选中 **Display list of available organizations**
    （显示可用组织列表） 复选框。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  选择 **Login**（登录）。 

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  使用您的 Dataverse 环境凭据（即 Office 365 管理员凭据）登录。单击
    **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  输入您的管理员租户密码，然后单击 **Sign in** （登录）。

> ![A screenshot of a login box Description automatically
> generated](./media/image12.png)

6.  在这种情况下，您可以看到 **Dev One**
    环境已被选中。如果显示环境列表，请选择您的环境 – **Dev
    One**，然后再次选择 **Login**。

> ![](./media/image13.png)

7.  您将看到系统插件列表。如果您的环境中有自定义插件，您也会在列表中看到它们。（程序集）是实现插件的
    .NET DLL。

> **注意：** 您需要展开该部分才能查看完整列表。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

8.  找到 **Microsoft.CDS.DataLakeDataProvider.Plugins** 并展开它。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

9.  每个子项都在程序集中实现。展开其中一个项目以查看该单个插件的步骤注册。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

10. 步骤注册将插件作为事件处理程序连接到事件。在上面的示例中，这是在
    insightsstorevirtualentity 表上处理创建作。

> ![](./media/image17.png)

11. 双击任何步骤可查看步骤配置详细信息，包括它注册的消息和实体、调用插件的管道阶段、执行是同步还是异步等。

> ![](./media/image18.png)

**摘要：**在本实验中，您学习了如何安装开发人员工具。在创建自己的自定义插件时，您将使用
Plugin Registration Tool 加载程序集并注册要处理的事件的步骤。
