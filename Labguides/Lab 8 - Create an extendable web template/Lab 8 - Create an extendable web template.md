# **ラボ8：拡張可能なWebテンプレートの作成**

**所要時間:** 25 分

**目的:**
このラボでは、extendおよびblockタグを使用してLiquidテンプレートを拡張する方法、includeタグでテンプレートを再利用する方法、および新しいテンプレートの結果にテーブル権限を適用する方法を学習します。

**タスク１：パーシャルテンプレートの作成**

最初のタスクとしては、ページのレンダリングには使用されず、別のテンプレートに挿入されるパーシャルテンプレートを作成します。

1.  +++<https://make.powerpages.microsoft.com/>+++にサインインします。

2.  右上から対象の環境**Dev One**を選択します。

> ![](./media/image1.png)

3.  **Active sites**タブの下で、「**Finance Advisor
    Search**」として自分のサイトを確認し、**Edit**を選択します。

> ![](./media/image2.png)

4.  拡張メニュー（省略記号）を展開し、**Portal
    management**を選択してPortal Managementアプリを開きます。

> ![](./media/image3.png)

5.  **Web Templates**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  \+**New**にクリックします。

> ![A screenshot of a web page Description automatically
> generated](./media/image5.png)

7.  以下の値を入力します：

    - **Name** - +++Directory+++

    &nbsp;

    - **Website** - Select your current website - Finance Advisor Search

    &nbsp;

    - **Source** - Enter the following content:

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

8.  **Save & Close**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

**タスク２：既存テンプレートの拡張**

次に、既存のLiquidテンプレートを拡張し、新しいテンプレートを作成し、以前に作成したテンプレートを挿入します。

1.  左ナビゲーションペインから**Web
    Templates**を選択し、+**New**を選択します。

> ![](./media/image8.png)

2.  以下の値を入力します：

    - **Name** - +++Directory Template+++

    &nbsp;

    - **Website** - Select your current website - Finance Advisor Search

    &nbsp;

    - **Source** - Enter the following content:

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

3.  **Save & Close**を選択します。

> ![A screenshot of a web template Description automatically
> generated](./media/image10.png)

**タスク３：ページテンプレートの作成と関連付け**

このタスクでは、新しいWebテンプレートを使用したページテンプレートを作成し、Directory出力を含めます。

1.  左ナビゲーションペインから**Page
    Templates**を選択し、**+New**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

2.  以下の値を入力します：

    - **Name** - +++Directory Page Template+++

    &nbsp;

    - **Website** - Select the current website - Finance Advisor Search

    &nbsp;

    - **Type** - Select **Web Template**

    &nbsp;

    - **Web Template** - Select **Directory Template**

    &nbsp;

    - **Table Name** - Select **Web Page**

3.  **オプション：**
    ページコンテンツにテキスト要素を追加し、次にお好きなテキストを入力してください。

4.  **Save & Close**を選択します。

> ![A screenshot of a web page Description automatically
> generated](./media/image12.png)

**タスク４：ページテンプレートのテスト**

新しいテンプレートが機能するかどうかをテストします：

1.  Power Pagesのデザインスタジオのホームタブに戻ります。

2.  **Sync**を選択して変更を同期します。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  **Pages** ワークスペースを選択し、**+ Page**をクリックします。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

4.  **Add a page**を追加ダイアログで以下のステップを実行：

    1.  ページ名は+++**Directory**+++ を入力します。

    &nbsp;

    1.  **Custom layouts** を選択し、**Directory Page
        Template**を選択します。

    &nbsp;

    1.  **Add**を選択します。

> ![A screenshot of a website Description automatically
> generated](./media/image15.png)
>
> 右ペインに「You don't have permissions to access the
> directory」というメッセージが表示される空のページが表示されます。
>
> ![](./media/image16.png)

**タスク５：テーブル権限の追加**

**注意：**
匿名ユーザーに対してグローバルな読み取り権限を付与することは、あくまで説明目的のためです。過剰な権限を付与したり、ビューやFetchXML表現に適切なフィルターを含めないことで、意図せずに機密情報を公開しないよう注意してください。

テーブル権限を追加するには、次の手順に従います。

1.  **Security workspace**を開き、**Table Permissions**を選択します。![A
    screenshot of a computer security Description automatically
    generated](./media/image17.png)

2.  **+ New permission**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

3.  以下を入力します：

    - **Name** - +++Account Directory+++

    &nbsp;

    - **Table** - Select the **Account (account)** table

    &nbsp;

    - **Access type** - Select **Global access**

    &nbsp;

    - **Permission to** - Select **Read**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

4.  **Add roles**を選択します。

5.  **Anonymous users** と**Authenticated users**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  **Save**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  **Save**を選択します。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image22.png)

**タスク６：テンプレートをテストする**

自分の最終タスクは、新しいテンプレートをテストすることです：

1.  **Pages**ワークスペースを選択し**Directory** ページを選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

2.   **Preview | Desktop**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> **注意：**
> 簡単なブラウザページのリフレッシュではデータを更新するのに不十分です。このコマンドを使用することで、サイトキャッシュが再構築されます。
>
> ページは今現在表示され、右パネルにアカウントのリストが含まれています。
>
> ![A screenshot of a search engine Description automatically
> generated](./media/image25.png)

**まとめ：**このラボでは、Liquidテンプレートの構築と拡張について学びました。Dataverse内のすべてのアカウントをリスト表示するサイドパネルを含む新しいページテンプレートを作成しました。
