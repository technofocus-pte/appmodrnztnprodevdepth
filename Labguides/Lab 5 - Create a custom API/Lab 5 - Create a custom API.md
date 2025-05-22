**ラボ5：カスタム API の作成**

**所要時間：** 35 分

**目的：** このラボでは、 Dataverseカスタム API
を作成してカスタムロジックを実行する方法を学習します。その後、Power
Automate フローのステップからこのカスタム API を使用します。

**タスク１：カスタム API プロジェクトの作成**

1.  VMの**Start** menuにクリックし、検索ボックスにCommand
    Promptと入力して、**Open**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  以下のコマンドを実行して**CustomAPILab**という新しいフォルダーを作成します。

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  作成したフォルダーに移動します。

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  CustomAPIlAB フォルダー内にいることを確認し、以下のコマンドで新しい
    Dataverse プラグイン クラス ライブラリを初期化します。

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Dataverseプラグイン クラスライブラリの作成が成功するはずです。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  以下のコマンドを実行して、プロジェクトを Visual Studio で開きます。

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  ポップアップが表示された場合は、**Microsoft Visual Studio 2022**
    を選択し、**Just once**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  Visual Studioにサインインを求められた場合は、**Skip this for now**
    を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  開発設定として**General**を選び、カラーテーマに**Dark**を選択してから、**Visual
    Studio**をクリックします。

> **注意：**プロジェクトが自動的に開かれた場合はこのステップは無視してください。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. プロジェクトが Visual Studio に開くことを確認します。

> ![](./media/image10.png)

11. Plugin1.csファイルを右クリックして、名前を**MatchPlugin.cs**に変更します。

> ![](./media/image11.png)

12. ファイル名を変更しますか？のダイアログが表示されたら**Yes**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. CustomAPILabプロジェクトを右クリックし、**Manage NuGet
    Packages**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. **System.Text.RegularExpressions** を検索し、**Install**を選択します。

> ![](./media/image14.png)

15. プレビュー変更ウィンドウで、**Apply** を選択してVisual
    Studioがソリューションへの変更をするように許可します。

> ![](./media/image15.png)

16. ライセンス条項に同意するため**I Accept** を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17.  **MatchPlugin.cs** ファイルを開きます。

> ![](./media/image17.png)

18. 次の行「using
    System;」ステートメントつまり3行目のステートメントを追加します。

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. ExecuteDataversePlugin方法内のvar
    context行の後に、次の行を追加します。これらの行は、カスタム API
    の呼び出しで渡された入力パラメータから値を取得します。

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. 以下の行を追加して、トレースサービスを取得します。

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. 入力値をトレースに書き込むため、以下の行を追加します。tracingService.Trace("Provided
    input: " + input);

> ![](./media/image21.png)

22. Regex.Match 方法を呼び出すため次の行を追加します。

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. 結果をトレースに書き込みます。

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. 最後に、以下の行を入力して、出力パラメーターMatchedを設定します。

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. これでexecute方法は以下のようになります。

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. **Build | Build Solution**を選択します。

> ![](./media/image26.png)

27. プロジェクトが成功に作成されます。

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**タスク２：カスタム API プラグインの登録**

1.  コマンドプロンプトを開き、以下のコマンドを実行して Plugin
    Registration Toolを起動します。

> +++pac tool prt+++
>
> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  **+ Create New Connection**を選択します。

> ![](./media/image29.png)

3.  **Office 365**を選択し、資格情報を入力して**Login**を選択します。

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  **M365 Admin tenant Id**でサインインし、**Next**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  **M365 Admin tenant Id’s** **password**を入力して、**Sign
    in**を選択します。

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  **Dev One** 環境が選択されていることを確認します。

7.  **Register | Register New Assembly**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  ステップ1の下に...をクリックし、**CustomAPILab\bin\Debug\net462** フォルダに移動します。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  **CustomAPILab.dll** を選択し、**Open**をクリックします。

> ![](./media/image35.png)

10. **Register Selected Plugins**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. 成功メッセージが表示されたら**OK** を選択します。プラグインは、次のタスクで作成するカスタムAPIに接続する準備が整っています。

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**タスク３：カスタム API の作成**

1.  +++<https://make.powerapps.com/>+++にアクセスしてPower Apps maker
    portal に移動します。**Dev One**環境にいることを確認します。

2.  左ナビゲーションの**Solutions** を選択し、**+ New
    Solution**をクリックします。

> ![](./media/image38.png)

3.  表示名に+++**Custom API Lab**+++ を入力します。

4.  発行者ドロップダウンで**CDS Default Publisher**を選択します。 

5.  **Create**をクリックします。これでコンポーネントを含むカスタムソリューションが作成されます。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  **+ New | More | Other | Custom API**を選択します。

> ![](./media/image40.png)

7.  次の情報を入力します：

    - **Unique Name:** +++contoso_match+++

    &nbsp;

    - **Name**: +++Match+++

    &nbsp;

    - **Display Name:** +++Match+++

    &nbsp;

    - **Description**: +++Match a string+++

    &nbsp;

    - **Binding Type**: +++Global+++

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  プラグインタイプで検索アイコンをクリックして**CustomAPILab.MatchPlugin**を確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  **Save and Close**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. **Done**にクリックします。

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11.  **+** **New | More| Other | Custom API Request
    Parameter**を選択します。

> ![](./media/image44.png)

12. **Custom
    API**のため、**Search**アイコンをクリックし、**Match**（自分のCustom
    API）を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. 簡潔にするために、Unique Name、Name、Display Name
    とDescriptionでは+++**StringIn**+++ を入力します。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. タイプに**String** を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. **Save and Close**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. **Done**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. さらにもう一つCustom
    APIリクエストパラメーターを追加するには、**+** **New | More| Other |
    Custom API Request Parameter**を選択します。

> ![](./media/image50.png)

18. **Custom
    API**のため**Search** アイコンを検索して**Match**（自部のCustom
    API）を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. 簡潔にするために、Unique Name、Name、Display Name とDescription
    には**Pattern**を入力します。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. タイプに **String** を選択します。

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. **Save and Close**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. **Done**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. **New | More | Other| Custom API Response Property**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. **Custom
    API**のため、**Search** アイコンをクリックして**Match** (自分のCustom
    API) を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. 簡潔にするために、**Unique Name**、**Name**、**Display Name**
    と**Description** には**+++Matched+++** を入力します。

26. タイプに **Boolean** を選択します。

> ![](./media/image58.png)

27. **Save and Close**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. **Done**にクリックします。

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. これでソリューションコンポーネントの一覧が完成し、以下の通り見えます。

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**タスク４： Power Automate からカスタム API を使用する**

1.  ソリューション内で **+ New | Automation | Cloud Flow |
    Instant**を選択します。

> ![](./media/image62.png)

2.  Flow name に+++**String match**+++ を選択し、**Manually trigger a
    flow** にクリックして**Create**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  **+ New Step**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  perform で検索し、**Perform an unbound action**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  Action Nameリストから、検索して**contoso_match**を選択します。

> ![](./media/image66.png)

6.  **StringIn**に**myemail@outlook.com**を入力します。ここで任意の有効なメールアドレスを入力します。

> ![](./media/image67.png)

7.  Patternには以下の正規表現を入力します。これはシンプルなメールパターンです。他の[*例*](https://regexlib.com/DisplayPatterns.aspx/)もあります。

+++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++

> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  フローが次のような形になっていることを確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  **Save**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. 保存が完了したら**Test**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. **Manually**を選択し、**Test**をクリックします。

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. **Run flow**を選択します。

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. **Done**にクリックします。

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. フローが完了したら、**Perform an unbound
    action**を展開して結果を確認します。 

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**Summary:** このラボでは、カスタムアクションの作成方法と、Power
Automate フローからの使用方法を学習しました。custom API
actionのcontoso_matchは、プラットフォーム API
を使用して直接呼び出すこともできるようになりました。
