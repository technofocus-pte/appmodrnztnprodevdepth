# **Laboratório 7: Adicione funcionalidade avançada do lado do cliente ao seu site**

**Duração estimada:** 35 minutos

**Objetivo:** Neste laboratório, você aprenderá como adicionar código
JavaScript a uma página para renderizar dados do Microsoft Dataverse
como um gráfico.

### **Tarefa 1: Criar um site com a ajuda da AI**

1.  Acesse o Power Pages usando
    +++<https://make.powerpages.microsoft.com/>+++. Certifique-se de
    estar no ambiente **Dev One.**

> ![](./media/image1.png)

2.  Selecione **Skip** na página **Tell us about yourself.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Insira a descrição fornecida para criar um site e clique no ícone
    **generate**.

> +++**Create a site for customers to find financial advisors at a bank
> based on their qualifications, and areas of expertise**+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  O Copilot gera um nome de site e um endereço web com base na sua
    descrição. Neste caso, o nome do site é ‘**Finance Advisor
    Search’**. Mantenha o nome e o endereço do site gerados e selecione
    **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  O Copilot gera um layout de página inicial, que você pode percorrer
    e navegar pela página gerada. Selecione **Next** para aceitar o
    layout sugerido.

> **Observação:** você pode selecionar **Try again** para gerar um novo
> layout.
>
> ![A screenshot of a website Description automatically
> generated](./media/image5.png)

6.  O Copilot gera mais páginas que podem ser usadas no site com base na
    descrição. Neste exemplo, as páginas Fale conosco, Busca de
    consultor, Perfil do consultor e Contato do consultor são
    selecionadas e, em seguida, selecione **Done** para finalizar a
    criação do site.

> **Observação:** Se o seu copilot gerar páginas diferentes para o seu
> site além das páginas mencionadas acima, você poderá selecionar
> algumas delas.
>
> ![](./media/image6.png)

7.  A criação do site pode levar alguns minutos. Ao terminar, você será
    redirecionado para o site aberto no design studio, que poderá ser
    personalizado posteriormente.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

### **Tarefa 2: Criar configurações do site**

Para criar as configurações do site, siga estas etapas.

1.  Selecione o menu de reticências ( **...** ) e depois selecione
    **Portal management**.

> O aplicativo Gerenciamento do Portal será aberto em uma nova aba.
>
> ![](./media/image8.png)

2.  Selecione **Site Settings**. Selecione **+ New.** 

> ![](./media/image9.png)

3.  Insira as seguintes informações e selecione **Save**.

    - **Name** - +++Webapi/account/enabled+++

    &nbsp;

    - **Website** - Select your website

    &nbsp;

    - **Value** - +++true+++

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Selecione **+ New.** 

> ![](./media/image11.png)

5.  Insira as seguintes informações e selecione **Save & Close**.

    - **Name** - +++Webapi/account/fields+++

    &nbsp;

    - **Website** – Selecione seu website

    &nbsp;

    - **Value** - +++name,numberofemployees,revenue+++

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

### **Tarefa 3: Criar permissões de tabela**

Para criar permissões de tabela, siga estas etapas.

1.  Mude para o design studio do Power Pages, onde o site recém-criado é
    aberto.

> **Observação:** Você pode fechar o painel do Copilot para melhor
> visibilidade.
>
> ![](./media/image13.png)

2.  Selecione o workspace **Security** e, em seguida, selecione **Table
    permissions**.

> ![A screenshot of a computer security Description automatically
> generated](./media/image14.png)

3.  Selecione **+ New permission.**

> ![](./media/image15.png) 

4.  Preencha as seguintes informações:

    - **Name** - +++Account+++

    &nbsp;

    - **Table** - +++Account (account)+++

    &nbsp;

    - **Access type** - Global

    &nbsp;

    - **Permission to** – Read

> ![](./media/image16.png)

5.  Selecione **Add roles** e depois adicione **Anonymous Users** e
    **Authenticated Users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

6.  Selecione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

7.  Selecione **Save** para manter esses dados visíveis para qualquer
    pessoa.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image19.png)

8.  Você pode ver a mensagem ‘The table permission ‘Account’ have
    successfully been saved’.

> ![](./media/image20.png)

### **Tarefa 4: Testar a Web API**

1.  Para testar a Web API, abra a seguinte URL após adicionar o endereço
    do seu site
    +++[https://**yourwebsite**.powerappsportals.com/\_api/accounts?$select=name,numberofemployees,revenue](https://yourwebsite.powerappsportals.com/_api/accounts?$select=name,numberofemployees,revenue)+++

2.  Se a caixa de diálogo de permissão solicitada for exibida, selecione
    **Accept**.

> ![A screenshot of a application Description automatically
> generated](./media/image21.png)

3.  Sua saída deve ser semelhante à imagem a seguir.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

### **Tarefa 5: Criar uma página de conteúdo e recuperar dados**

Para criar uma página de conteúdo e adicionar código JavaScript que
recupera e transforma os dados, siga estas etapas:

1.  No design studio, selecione o workspace **Pages** e depois selecione
    **+ Page**.

> ![](./media/image23.png)

2.  Digite +++**Chart**+++ como o **Page name**.

3.  Certifique-se de que a opção **Add page to main navigation** esteja
    selecionada.

4.  Selecione o layout **Start from blank**.

5.  Selecione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

6.  Selecione **Edit code**.

> ![](./media/image25.png)

7.  Na caixa de diálogo pop-up, selecione **Open Visual Studio Code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

8.  Se uma janela pop-up aparecer e solicitar que você permita que a
    ferramenta de extensão Power Platform faça login usando o Microsoft,
    selecione **Allow**.

> ![A black screen with white text Description automatically
> generated](./media/image27.png)

9.  Isso buscará seus dados.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

10. No editor do Visual Studio Code, selecione o arquivo
    **Chart.en-US.customjs.js**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

11. Anexe o seguinte script:

> function makeChart(rawData) {
>
> // transform raw data into plotting array
>
> var rData = rawData.value.map(({
>
> name,
>
> revenue,
>
> numberofemployees
>
> }) =\> ({
>
> "x": numberofemployees,
>
> "y": revenue,
>
> "z": (!revenue) ? 1 : numberofemployees / revenue,
>
> "name": name
>
> }));
>
> console.log(rData);
>
> }
>
> // retrieve accounts data using portals Web API
>
> $(document).ready(function() {
>
> $.get('/\_api/accounts?$select=name,numberofemployees,revenue',
> makeChart, 'json');
>
> });

12. Pressione o atalho de teclado **Ctrl + S** ( **⌘ + S** no Mac) para
    salvar o arquivo.

> ![A screen shot of a computer program Description automatically
> generated](./media/image30.png)

13. Feche a aba **Visual Studio Code**. Selecione **Sync** quando
    solicitado para sincronizar as alterações.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

14. Selecione **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

15. Quando a página for exibida, pressione a tecla **F12** para exibir
    as ferramentas do desenvolvedor do navegador.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

16. Selecione a aba **Console.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

17. Verifique se a saída do console contém os mesmos dados recuperados
    anteriormente, exceto que agora eles são exibidos como
    transformados.

> ![A screenshot of a computer program Description automatically
> generated](./media/image36.png)

18. A estrutura de dados agora está preparada para plotagem. Atribua os
    rótulos apropriados aos pontos de dados:

    - **name** - Nome da empresa

    &nbsp;

    - **x** - Número de funcionários

    &nbsp;

    - **y** - Receita da empresa em milhares

    &nbsp;

    - **z** - Receita de cada funcionário (calculada)

### **Tarefa 6: Adicionar funcionalidade de biblioteca externa**

Este exercício usa a biblioteca Highcharts.js (gratuita para uso pessoal
ou sem fins lucrativos) para criar um gráfico de bolhas com base nos
dados.

1.  Altere para o design studio.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

2.  Selecione o rodapé da página e depois selecione **Edit code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

3.  Na caixa de diálogo pop-up, selecione **Open Visual Studio Code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

4.  Anexe o seguinte código no final do arquivo.

> \<script src="https://code.highcharts.com/highcharts.js"\>\</script\>
>
> \<script
> src="https://code.highcharts.com/highcharts-more.js"\>\</script\>
>
> ![](./media/image40.png)

5.  Pressione o atalho de teclado **Ctrl + S** ( **⌘ + S** no Mac) para
    salvar o arquivo.

6.  Feche a aba **Visual Studio Code.**

7.  Selecione **Edit code** na barra de ferramentas para abrir o Visual
    Studio Code para a página.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

8.  Selecione **Open Visual Studio Code** no pop-up Edit in Visual
    Studio Code para a Web.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

9.  Selecione o arquivo **Chart.en-US.customjs.js**.

> ![A screen shot of a computer program Description automatically
> generated](./media/image42.png)

10. Substitua o arquivo para alterar a função **makeChart** da seguinte
    maneira:

> Observação: Aqui, substituir o arquivo significa modificar apenas o
> arquivo existente.
>
> function makeChart(data) {
>
> console.log(data);
>
> var rData = data.value.map(({
>
> name,
>
> revenue,
>
> numberofemployees
>
> }) =\> ({
>
> "x": numberofemployees,
>
> "y": revenue,
>
> "z": (!revenue) ? 1 : numberofemployees / revenue,
>
> "name": name
>
> }));
>
> console.log(rData);
>
> // new code to plot the data
>
> Highcharts.chart($('.mychart')\[0\], {
>
> title: {
>
> text: "Customers efficiency"
>
> },
>
> legend: {
>
> enabled: false
>
> },
>
> xAxis: {
>
> title: {
>
> text: "Number of employees"
>
> }
>
> },
>
> yAxis: {
>
> title: {
>
> text: "Turnover ($K)"
>
> }
>
> },
>
> tooltip: {
>
> pointFormat: '\<strong\>{point.name}\</strong\>\<br/\>Employed:
> {point.x}\<br\>Turnover ($K): ${point.y}',
>
> headerFormat: ''
>
> },
>
> series: \[{
>
> type: 'bubble',
>
> data: rData
>
> }\]
>
> });
>
> }
>
> // retrieve accounts data using portals Web API
>
> $(document).ready(function() {
>
> $.get('/\_api/accounts?$select=name,numberofemployees,revenue',
> makeChart, 'json');
>
> });
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image43.png)

11. Pressione o atalho de teclado **Ctrl + S** ( **⌘ + S** no Mac) para
    salvar o arquivo.

12. Selecione o arquivo **Chart.en-US.webpage.copy.html**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image44.png)

13. Insira o seguinte código no elemento \<div\> interno:

> \<figure\>
>
> \<div class="mychart"\>\</div\>
>
> \</figure\>
>
> ![A screen shot of a computer Description automatically
> generated](./media/image45.png)

14. Pressione o atalho de teclado **Ctrl + S** ( **⌘ + S** no Mac) para
    salvar o arquivo.

15. Feche a aba **Visual Studio Code** e selecione **Sync** para
    sincronizar as alterações.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

16. Selecione **Preview | Desktop**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

17. A saída agora deve incluir o gráfico de bolhas. Passe o cursor sobre
    as bolhas para verificar os dados.

> ![A screenshot of a search engine Description automatically
> generated](./media/image48.png)

**Resumo:** Neste laboratório, você aprendeu como adicionar código
JavaScript a uma página para renderizar dados do Microsoft Dataverse
como um gráfico usando uma biblioteca de gráficos externa com os dados
recuperados do Dataverse usando a Web API de portais.
