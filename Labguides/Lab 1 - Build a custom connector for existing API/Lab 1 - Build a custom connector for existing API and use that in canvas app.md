**ラボ１-既存の API にカスタムコネクタを作成してCanvas アプリで使う**

**所要時間:** 35分

**目的:　**このラボでは「Contoso Invoicing」という既存の API
に対して、はじめてのカスタムコネクタを作る方法を学んで、そのカスタムコネクタを使って
Canvas アプリを作る方法も学びます。

**タスク１: APIを確認**

API を確認するには、次の手順で行います:

1.   +++<https://contosoinvoicing.azurewebsites.net/>+++にクリックします。

2.  ドキュメント・リンクを選択するため「You can find the API
    documentation」の横にある「**here**」をクリックしてください。

> ![](./media/image1.png)

3.  利用できる操作内容を確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  ドキュメントのブラウザタブまたはウィンドウを閉じます。

5.  「Open API definition」のリンクを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  以下の画像は、ドキュメントページに表示されていた内容の OpenAPI
    バージョンの例を示します。右クリックして「**Save
    as**」を選択します。

> ![Screenshot of an arrow pointing to the save as
> button.](./media/image4.png)

7.  ファイルを VM
    デスクトップにローカル保存します。このファイルは後の演習で使用されます。

8.  定義が表示されているブラウザのタブまたはウィンドウを閉じます。

9.  **API Key** リンクをクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. 後でも使用するためにAPI Keyをコピーして、VM のメモ帳に保存します。

> ![](./media/image6.png)

11. **Return to home**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12.  **Download Logo**を選択します**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. ロゴ画像を VM のデスクトップにローカルで保存して、後で使用します。

**タスク２: 新しいソリューションを作成**

新しいソリューションを作成するため、次の手順に従います:

1.   <https://make.powerapps.com/>　にアクセスし、「**Dev
    One**」環境にいることを確認します。

> ![](./media/image9.png)

2.  右のナビゲーションペインから、**Solutions**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  上のリボンから**+New solution** を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

4.   **Display name**には「+++**Contoso invoicing**+++」と入力し、**+
    New publisher**をします。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

5.  表示名に「+++**Contoso**+++」、名前に「+++**Contoso**+++」、接頭辞に「+++**contoso**+++」を入力して**Save**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> **注意：**「A record with matching key values already
> exists.」というエラーメッセージが表示された場合は、それを無視して「New
> publisher」ウィンドウを閉じます。![](./media/image14.png)

6.  そして、**New solution** ウィンドウで**Publisher**
    に**Contoso** を選択、**Create**にクリックします。実際のプロジェクトで作業する時は、自分のpublisherを作成することをお勧めします。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  「 **Create**」を選択した後、このページから離れることはありません。Contoso
    invoicingソリューションに自動的に移動されます。

**タスク３：新しいコネクタの作成**

新しいコネクタを作成するため以下の手順に従います：

1.  自分から作成された**Contoso
    invoicing** ソリューションにいることを確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

2.  **+ New** |**Automation**| **Custom connector**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

3.  **Connector name**に+++**Contoso invoicing**+++を入力します。

> ![](./media/image18.png)

4.  画像をアップロードするため**Upload** を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

5.  **タスク１:**
    **APIを確認**でダウンロードしたコネクタのロゴ画像を選択します。

6.  **Icon background color**に+++**\#175497**+++ を入力します。

7.  **Description**に+++**Custom connector for Contoso Invoicing
    API**+++ 入力します。

8.  **Host**に+++**contosoinvoicingtest.azurewebsites.net**+++を入力します。

> ![](./media/image20.png)

9.  **Create connector**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

10. このページから離れることはありません。

**タスク4：OpenAPI定義のインポート**

OpenAPI定義をインポートするため以下の手順に従います：

1.  コネクタ名の横にある矢印を選択します。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image22.png)

2.  コネクタでの省略記号（...）ボタンを選択して**Update from OpenAPI
    file**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.   **Import**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

4.  **タスク 1:「API
    の確認」**でダウンロードした**swagger.json** ファイルを選択し、「**Open**」を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

5.   **Continue**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  ホストURL
    として +++**contosoinvoicingtest.azurewebsites.net**+++ を入力して**Security**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

7.  インポートしたファイルからフィールドが自動入力されていることを確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  このページから移動することはありません。

**タスク5：定義の確認と調整**

定義を確認して調整するには、以下の手順に従います：

1.  **Definition** タブを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

2.  インポートされた操作を数分かけて確認します。

3.  **GetInvoice**の横にある青い情報アイコンに注目します。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  **GetInvoice** 操作にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  操作は**Summary**が欠落していることが表示されていることを確認します。

> ![A screenshot of a phone Description automatically
> generated](./media/image32.png)

6.  有用性を向上させるために、**Summary**に**Get Invoice**と入力します。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

7.  **PayInvoice**操作の横にある青い情報アイコン**Description**が欠落していることを示しています。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

8.  **PayInvoice**操作を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

9.  **Description**に**Pay an invoice**と入力します。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

10. 　**NewInvoice**操作は両方が使用しないため削除します。

> ![Screenshot showing the delete action button.](./media/image37.png)

11. **　GetInvoiceSchema** 操作を選択します。

> ![](./media/image38.png)

12. 　アクション一覧に表示されないように**Visibility**オプションを**internal**に変更します。そして**Update
    connector**を選択します。

> ![](./media/image39.png)

13. 　このページから移動することはありません。

**タスク６：コネクタのテスト**

コネクタをテストするには、以下の手順に従います:

1.  **Test**タブを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

2.  **+ New connection**にクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

3.  **タスク１： APIの確認**に保存された**API
    Key** を貼り付け 、**Create connection**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

4.  **Refresh**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

5.   **ListInvoiceTypes| Test Operation**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

6.  BodyエリアにInvoice Typesデータが表示されていることを確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

7.  カスタムコネクタウィンドウを閉じるように**Close** にクリックします。

> ![](./media/image46.png)

**タスク７：canvasアプリでカスタムコネクタを使用する**

このタスクでは、canvasアプリケーションを作成し、作成したカスタムコネクタを使用してinvoicesのリストを表示します。

1.  Power Apps
    メーカーポータルに戻ります。「新しいカスタムコネクタを作成中」というポップアップが表示されたら「Done」を選択します。Dev
    One 環境にいることを確認する必要があります。

> ![](./media/image47.png)
>
> **Note:** ポータルが既に開いていない場合は、**Dev
> One**環境にいることを確認し、+++<https://make.powerapps.com/>+++にアクセスします。

2.  自分が作成したContoso
    invoicingソリューションにいることを確認します。もしない場合は、Solutionsを選択し、作成した
    Contoso invoicingソリューションを開きます。![A screenshot of a
    computer Description automatically generated](./media/image48.png)

3.   **+ New** にクリックして **App \> Canvas app**を選択します。

> ![](./media/image49.png)

4.   アプリ名前に**Contoso invoicing
    app** と入力し、フォーマットに**Phone** を選択します後**Create**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

5.  ウェルカムウィンドウで**Skip** を選択します。

> ![](./media/image51.png)

6.   **Data** タブを選択し、**+ Add data**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

7.  コネクタを拡大し、作成した
    Contoso　invoicingカスタムコネクタを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

8.  **+ Add a connector**選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

9.  **タスク１： API** **の確認**に保存したAPI
    キーを貼り付け**Connect**を選択します。

> ![A screenshot of a login box Description automatically
> generated](./media/image55.png)

10. 　プレミアム警告のポップアップで「**Got it** 」を選択します。

> ![A screenshot of a phone Description automatically
> generated](./media/image56.png)

11. **Tree view** タブを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

12. 　**+ Insert**にクリックして**Vertical gallery**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

13. データに**ContosoInvoicing**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

14. **Items**を以下の値に設定します。

> +++ContosoInvoicing.ListInvoices().invoices+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image60.png)

15. ギャラリーを拡大して**Subtitle**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

16. Subtitleの**Text**値を +++**ThisItem.amount**+++に設定します。

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

17. ギャラリーを展開し、ギャラリーの中から**Title**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

18. Titleの**Text** 値を+++**ThisItem.accountName**+++に設定します。

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

19. ギャラリーは以下の画像のよになります。

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

**まとめ:**このラボでは、既存のAPI用にカスタムコネクタを作成する方法、API定義をインポートする方法、およびそのコネクタをCanvas
Appで使用してinvoicesの一覧を表示する方法を学びました。カスタムコネクタはファンクション・ベースであり、APIの基盤となるサービス内の特定のファンクションを呼び出して対応するデータを返します。
