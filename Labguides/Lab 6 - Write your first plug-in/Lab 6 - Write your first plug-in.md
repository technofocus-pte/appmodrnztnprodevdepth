**ラボ６：最初のプラグインを作成する**

**所要時間:** 30 分

**目的:**
この件では、組織が電話番号データを一貫した形式で入力できるようにする必要があります。この目的を達成するために、作成・更新時に実行されるプラグインを作成し、Dataverse
に保存される前に電話番号から数値以外のすべての文字を削除します。

このラボでは、作成および更新イベントで実行されるプラグインの作成方法を学習します。このプラグインは電話番号から数字以外の文字を全て削除します。

**タスク1：新しいソリューションとモデル駆動型アプリの作成**

1.  +++<https://make.powerapps.com/>+++で[Power
    Apps](https://make.powerapps.com/)に移動します。 **Dev
    One**環境にいることを確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  左側のナビゲーション[ペイン](https://context.reverso.net/translation/japanese-english/%E3%83%8A%E3%83%93%E3%82%B2%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%BB%E3%83%9A%E3%82%A4%E3%83%B3)から**Solutions** を選択して、**New
    solution**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  フライアウトダイアログで**Display name** に– +++Plugin
    Lab+++と、**Name**に – +++PluginLab+++、**Publisher**に – CDS
    Default publisher を入力して、**Create**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  ソリューション内で新しいモデル駆動型アプリを作成するため、**New** | **App** | **Model-driven
    app**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  駆動型アプリ**Name**に+++**Fundraiser**+++という名前を付けて、**Create**を選択します。

> ![](./media/image5.png)

6.  モデル駆動型アプリで**+Add page**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  表示されているポップアップで**Dataverse table**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  **Contact** テーブルを選択して、**Add**を選択します。

> ![](./media/image8.png)
>
> **注意：** このラボではContactテーブルを使用します。

9.  なお、「Funraiser」という名前のモデル駆動型アプリが完成します。

> ![](./media/image9.png)

10. 右上の**Save**をクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

11. **Publish**をクリックします。

> ![A purple and white rectangle Description automatically
> generated](./media/image11.png)

12. **back arrow**をクリックして、ソリューション画面に戻ります。

> ![A screenshot of a browser Description automatically
> generated](./media/image12.png)

13. **back arrow**
    をクリックして、全てのソリューションが表示されるページに戻ります。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

**タスク２：プラグインの作成**

1.  **Visual Studio
    2022**を起動します。VMのスタートメニューから検索ボックスにVisual
    Studio を入力して、**Open**にクリックします。

> ![](./media/image14.png)

2.   **File | New | Project**を選択します。

> ![](./media/image15.png)

3.  **Class Library (.NET
    Framework)** を選択して、**Next**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  **Project
    Name**に**D365PackageProject** を入力して、保存先を選択します。

> ![](./media/image17.png)

5.  **Framework**に**.NET Framework
    4.7.1**を選択し、**Create**を選択します。

> ![](./media/image18.png)

6.  プロジェクトを右クリックし、**Manage NuGet Packages**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

7.  **Browse**タブ を選択し、**microsoft.crmsdk.coreassemblies**を検討して選択します。そして**Install**を選択します。

> ![](./media/image20.png)

8.  プレビュー変更ウィンドウで**Apply** をクリックし、Visual
    Studioがソリューションに変更することを承認します。

> ![A screenshot of a computer program Description automatically
> generated](./media/image21.png)

9.  **I Accept**にクリックして、ライセンス条項を同意するます。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. NuGet package managerを閉じます。

> ![A screenshot of a computer program Description automatically
> generated](./media/image23.png)

11. **Class1.cs** を右クリックして**Delete**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

12. **OK** にクリックして、Class1.csが完全に削除します。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

13. プロジェクトを右クリックし、**Add | Class**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

14. 新しいクラス名を**PreOperationFormatPhoneCreateUpdate**と付けて、**Add**を選択します。

> ![](./media/image27.png)

15. 以下の usingステートメントを新しいクラスに追加します：

> using Microsoft.Xrm.Sdk;
>
> using System.Text.RegularExpressions;
>
> ![](./media/image28.png)

16. クラスを**public**にするには、internal をpublic
    に置き換え、手順の最後に**IPlugin** を入力して、下の画像に示すようにIPlugin
    インターフェースを追加します。

> ![A screenshot of a computer program Description automatically
> generated](./media/image29.png)

17. IPlugin
    インターフェースの上にマウスを移動し、表示されるクイックアクションアイコンをクリックして、**Implement
    interface**を選択します。

> ![](./media/image30.png)
>
> クラスは次の画像のようになります。
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image31.png)

**タスク３：電話番号の整形**

1.  サービスプロバイダーから実行コンテキストを取り得します。Execute
    方法内の例外を次のスニペットに置き換えます。

> IPluginExecutionContext context =
>
> (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
>
> ![](./media/image32.png)

2.  Targetのinput
    parameterを確認します。Execute方法に次のスニペットを追加してください。

> if (!context.InputParameters.ContainsKey("Target"))
>
> throw new InvalidPluginExecutionException("No target found");
>
> ![](./media/image33.png)

3.  次のスニペットをExecute方法に追加します。このスニペットは、入力パラメーターからターゲットエンティティを取得し、次にその属性にtelephone1(Business
    Phone for Contacts, Phone for
    Accounts)が含まれているかどうかを確認します。

> var entity = context.InputParameters\["Target"\] as Entity;
>
> if (!entity.Attributes.Contains("telephone1"))
>
> return;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image34.png)

4.  次のスニペットをExecute方法に追加します。これはユーザーから提供された電話番号から数値以外を削除します。

> string phoneNumber = (string)entity\["telephone1"\];
>
> var formattedNumber = Regex.Replace(phoneNumber, @"\[^\d\]", "");
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image35.png)

5.  整形済みの電話番号を
    telephone1に設定します。次のスニペットをExecute方法に追加します。

> entity\["telephone1"\] = formattedNumber;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image36.png)
>
> Execute方法は現在、以下の画像のように見えます。
>
> ![Screenshot of the execute method.](./media/image37.png)

6.  プロジェクトを右クリックし、**Properties**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

7.  **Signing**タブを選択し、\<**New…\>** キーファイルを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

8.  **Key file name**に+++**contoso.snk**+++ と入力し、**Protect my key
    file with a password** からチェックを外して**OK**を選択します。

> ![](./media/image40.png)

9.  **Properties**タブを閉じます。

> ![](./media/image41.png)

10. **Build** タブを選択し、**Build Project**にクリックします。

> ![A screenshot of a computer program Description automatically
> generated](./media/image42.png)

11. Buildが成功に完了することを確認します。

> ![A screenshot of a video game Description automatically
> generated](./media/image43.png)

**タスク４：プラグインの登録とステップス**

1.  VMの**Start**メニューを開き、検索ボックスにPlug-in Registration
    Toolと入力して**Open**をクリックします。

> ![](./media/image44.png)

2.  **Create New Connection**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

3.  **Office 365**を選択し、**Show
    Advanced**チェックボックスをオンにします。Online Region
    フィールドで**Don’t Know**を選択し、「M365 Admin
    tenant」の資格情報を入力して、**Login**を選択します。

> ![](./media/image46.png)

4.  **Register**を選択し、次に **Register New Assembly**を選択します。

> ![](./media/image47.png)

5.  Selectステップ１の下にある**...**
    をクリックし、作成したクラスライブラリの**Bin |
    Debug** フォルダを参照します。

> ![A white background with black text Description automatically
> generated](./media/image48.png)

6.  **D365PackageProject.dll**を選択し、**Open**をクリックします。

> ![](./media/image49.png)

7.  **Register Selected Plugins**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  **OK**をクリックします。

> ![](./media/image51.png)

9.  新しく登録されたアセンブリ－**(Assembly)
    D365PackageProject**を展開します。

> ![](./media/image52.png)

10. プラグインを右クリックし、**Register New Step** を選択します。

> ![](./media/image53.png)

11. **Message**に**Create** を選択し、**Primary
    Entity**に**contact**を選択します。

> ![](./media/image54.png)

12. **Event Pipeline Stage of
    Execution**に**PreOperation**を選択し、**Register New
    Step**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

13. 属性にフィルターが検出されなかったことを示す警告ページで、**Close**をクリックします。

> ![](./media/image56.png)

14. エラーメッセージつまり、ステップの登録中にエラーが発生しましたというメッセージが表示された場合は、**No**を選択して詳細を確認します。

> ![A screenshot of a computer error Description automatically
> generated](./media/image57.png)

15. プラグインの下にCreate ステップが作成されていることを確認します。

> ![A red line with black text Description automatically
> generated](./media/image58.png)

16. プラグインを右クリックして、再度 **Register New Step**を選択します。

> ![](./media/image59.png)

17. **Message**に**Update**を選択し、**Primary
    Entity**に**contact** を選択、**Attributes**のルックアップをクリックします。

> ![](./media/image60.png)

18. **Select All**チェックボックスをオフにし、**Business
    Phone**チェックボックスを選択し、**OK**にクリックします。

> ![](./media/image61.png)

19. **Event Pipeline Stage of
    Execution**に**PreOperation**を選択し、**Register New
    Step**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

20. 「ステップの登録中にエラーが発生しました。」、つまりエラーメッセージが出た場合は、**No**を選択して詳細を確認します。

> ![A screenshot of a computer error Description automatically
> generated](./media/image57.png)

21. プラグインの下にステップが作成されていることを確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

**タスク５：プラグインをテストする**

1.  +++<https://make.powerapps.com/>+++にクリックしてMakerポータルに移動し、**Dev
    One**環境にいることをを確認します。

2.  **Apps**を選択し、**Fundraiser** アプリケーションを起動します。

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

3.  **+ New**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

4.  **First Name**に**+++Test+++**、**Last
    Name**に**+++Contact+++**、**Business
    Phone**に**+++(123)-555-0100+++**を入力し、**Save**をクリックします。

> ![A screenshot of a contact form Description automatically
> generated](./media/image66.png)
>
> レコードが保存する必要であり、**Business
> Phone**は数値のみが表示されます。.
>
> ![](./media/image67.png)

5.  **Business Phone**
    を「**001-123-555-0100**」に変更して、**Save**をクリックします。レコードが更新され、**Business
    Phone**は数値のみが表示されます。

> ![A screenshot of a contact form Description automatically
> generated](./media/image68.png)

**まとめ：**このラボでは、作成および
更新時に実行されるプラグインの作成方法と、そのプラグインを使用して電話番号から数字以外の文字を削除方法を学びました。
