**ラボ３：****開発者ツールのインストールと使用**

**所要時間の目安:** 15分

**目的：**
このラボでは、NuGetから開発者向けいくつかのツールをインストールする方法を学習します。

**タスク1： 開発者ツールのインストールする**

In このタスクでは、Power Platform
CLIを使用してツールをインストールします。

1.  **Command
    Prompt**を起動し、VMの**Start**メニューから検索ボックスにCommand
    Promptと入力して**Open**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  以下のコマンドを実行して**Configuration Manager
    Tool**インストールします。

> +++pac tool cmt+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Configuration Manager
    Toolをインストールして、実行する必要があります。Configuration
    Manager Toolを閉じます。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  以下のコマンドを実行して、**Package Deployer
    Tool**をインストールします。

> +++pac tool pd+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  The Package deployerツールをインストールして、起動します。Package
    Deployer ツールを閉じます。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  **Plugin Registration
    Tool**をインストールするため以下のコマンドを実行します。

> +++pac tool prt+++
>
> ![](./media/image6.png)

7.  The Plugin Registrationをインストールして、起動します。Plugin
    Registration ツールは閉じず、そのまま開いておきます。

> ![](./media/image7.png)

**タスク２：プラグイン登録ツールで登録済みプラグインを確認する**

1.  **Create New Connection**をクリックします。

> ![](./media/image8.png)

2.  **Display list of available
    organizations**のチェックボックスをオンにします。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.   **Login**にクリックします。 

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Dataverse環境の認証情報、すなわちOffice
    365管理者認証情報でサインインします。**Next**にクリックします**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  管理者テナントのパスワードを入力し、**Sign in**をクリックします。

> ![A screenshot of a login box Description automatically
> generated](./media/image12.png)

6.  この場合は、**Dev One**
    環境がすでに選ばれていることが確認できます。もし環境のリストが表示されたら、自分の環境として–
    **Dev One**を選択し、もう一度**Login** をクリックします。

> ![](./media/image13.png)

7.  システムプラグインの一覧が表示されます。もし自分の環境にカスタムプラグインがあるとそれらも一覧に表示されます。「Assembly」は.NET
    DLLsでプラグインが実装されています。

> **注意：**一覧を完全に表示するにはこのセクションを展開する必要があります。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

8.  **Microsoft.CDS.DataLakeDataProvider.Plugins**を探して展開します。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

9.  各子項目がアセンブリ内で実装されています。さらにいずれかの子項目を展開すると、そのプラグインのステップ登録が表示されます。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

10. ステップ登録は、プラグインがイベントハンドラーとしてイベントに接続されます。
    上記の例では、insightsstorevirtualentityテーブルへの作成を処理しています。

> ![](./media/image17.png)

11. 任意のステップをダブルクリックすると、ステップが登録されたメッセージとエンティティ、プラグインが呼び出されるパイプラインステージ、実行が同期か非同期かなど、ステップ構成の詳細を確認できます。

> ![](./media/image18.png)

**まとめ：**このラボでは、開発者向けのツールのインストール方法を学習しました。将来的にカスタムプラグインを作成する際には、このプラグイン登録ツールを使用してアセンブリを読み込み、イベントに対するステップを登録することになります。
