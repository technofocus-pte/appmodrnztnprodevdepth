# **Laboratório 8: Criar um modelo web extensível**

**Duração estimada:** 25 minutos

**Objetivo:** Neste laboratório, você aprenderá como estender modelos
Liquid usando tags extend e block, como reutilizar modelos Liquid usando
a tag include e como aplicar permissões de tabela aos resultados do novo
modelo.

**Tarefa 1: Criar um modelo parcial**

Sua primeira tarefa é criar um modelo parcial que não será usado para
renderizar uma página, mas será inserido em outro modelo.

1.  Entre no Power Pages +++<https://make.powerpages.microsoft.com/>+++.

2.  Selecione o ambiente de destino **Dev One** no canto superior
    direito.

> ![](./media/image1.png)

3.  Na aba **Active sites**, você pode ver seu site – **Finance Advisor
    Search**. Selecione **Edit**.

> ![](./media/image2.png)

4.  Expanda o menu de extensão (reticências) e selecione **Portal
    management** para abrir o aplicativo Gerenciamento do Portal.

> ![](./media/image3.png)

5.  Selecione **Web Templates**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Selecione + **New**.

> ![A screenshot of a web page Description automatically
> generated](./media/image5.png)

7.  Insira os seguintes valores:

    - **Name** - +++Directory+++

    &nbsp;

    - **Website** - Selecione seu site atual - Finance Advisor Search

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

8.  Selecione **Save & Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

**Tarefa 2: Estender um modelo existente**

Em seguida, você criará um novo modelo que estende um modelo Liquid
existente e, em seguida, inserirá o modelo criado anteriormente.

1.  No painel de navegação esquerdo, selecione **Web Templates**.
    Selecione + **New**.

> ![](./media/image8.png)

2.  Insira os seguintes valores:

    - **Name** - +++Directory Template+++

    &nbsp;

    - **Website** – Selecione seu site atual - Finance Advisor Search

    &nbsp;

    - **Source** - Digite o conteúdo a seguir:

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

3.  Selecione **Save & Close**.

> ![A screenshot of a web template Description automatically
> generated](./media/image10.png)

**Tarefa 3: Criar um modelo de página e associar a essa página**

Nesta tarefa, você criará um modelo de página que usa seu novo modelo da
web e incluirá a saída do Diretório.

1.  No painel de navegação esquerdo, selecione **Page Templates**.
    Selecione + **New**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

2.  Insira os seguintes valores:

    - **Name** - +++Directory Page Template+++

    &nbsp;

    - **Website** - Selecione o site atual - Finance Advisor Search

    &nbsp;

    - **Type** - Selecione o **Web Template**

    &nbsp;

    - **Web Template** - Selecione o **Directory Template**

    &nbsp;

    - **Table Name** – Selecione **Web Page**

3.  **Opcional:** adicione um elemento de texto ao conteúdo da página e
    insira o texto de sua escolha.

4.  Selecione **Save & Close**.

> ![A screenshot of a web page Description automatically
> generated](./media/image12.png)

**Tarefa 4: Teste o modelo de página**

O próximo passo é testar se o seu novo modelo funciona:

1.  Retorne à aba Início do design studio do Power Pages.

2.  Selecione **Sync** para sincronizar as alterações.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Selecione o workspace **Pages**. Selecione **+ Page**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

4.  Na caixa de diálogo **Add a page**, conclua as seguintes etapas:

    1.  Digite +++**Directory**+++ como nome da página.

    &nbsp;

    1.  Selecione **Custom layouts** e depois **Directory Page
        Template**.

    &nbsp;

    1.  Selecione **Add**.

> ![A screenshot of a website Description automatically
> generated](./media/image15.png)
>
> A página em branco será exibida com a mensagem "You don't have
> permissions to access the directory" no painel direito.
>
> ![](./media/image16.png)

**Tarefa 5: Adicionar permissões de tabela**

**Aviso:** A concessão de permissão global de leitura a usuários
anônimos é apenas para fins ilustrativos. Tenha cuidado para evitar a
exposição acidental de informações confidenciais, concedendo permissões
excessivas e não incluindo filtros apropriados em suas visualizações ou
expressões FetchXML.

Siga estas etapas para adicionar permissões de tabela.

1.  Selecione **Security workspace** e, em seguida, **Table
    Permissions**.

> ![A screenshot of a computer security Description automatically
> generated](./media/image17.png)

2.  Selecione **+ New permission**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

3.  Insira os seguintes valores:

    - **Name** - +++Account Directory+++

    &nbsp;

    - **Table** - Selecione a tabela **Account (account)**

    &nbsp;

    - **Access type** - Selecione **Global access**

    &nbsp;

    - **Permission to** - Selecione **Read**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

4.  Selecione **Add roles**.

5.  Selecione **Anonymous users** e **Authenticated users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  Selecione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  Selecione **Save**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image22.png)

**Tarefa 6: Teste o modelo**

Sua tarefa final é testar seu novo modelo:

1.  Selecione o workspace **Pages** e depois selecione a página
    **Directory**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

2.  Selecione **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> **Observação:** Uma simples atualização da página do navegador não
> será suficiente para atualizar os dados. Usar este comando reconstrói
> o cache do site.
>
> A página agora deve ser exibida e incluir a lista de contas no painel
> direito.
>
> ![A screenshot of a search engine Description automatically
> generated](./media/image25.png)

**Resumo:** Neste laboratório, você aprendeu a criar e estender modelos
Liquid. Você criou um novo modelo de página que inclui um painel lateral
que exibe todas as contas no Dataverse.
