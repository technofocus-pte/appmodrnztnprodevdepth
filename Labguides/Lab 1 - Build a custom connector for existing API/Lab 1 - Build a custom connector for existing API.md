**Laboratório 1 - Crie um conector personalizado para uma API existente
e use-o no aplicativo Canvas**

**Duração estimada:** 35 minutos

**Objetivo:** Neste laboratório, você aprenderá a criar seu primeiro
conector personalizado para uma API existente chamada Contoso Invoicing,
a criar um aplicativo Canvas e como usar o conector no aplicativo
Canvas.

**Tarefa 1: Revisar a API**

Para revisar a API, siga estas etapas:

1.  Acesse +++<https://contosoinvoicing.azurewebsites.net/>+++.

2.  Para selecionar o link da documentação, clique em **here** ao lado
    de "You can find the API documentation".

> ![](./media/image1.png)

3.  Revise as operações disponíveis.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Feche a aba ou janela do navegador de documentação.

5.  Selecione o link **Open API definition**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  A imagem a seguir mostra um exemplo da versão OpenAPI do que foi
    mostrado na página de documentação. Clique com o botão direito e
    selecione **Save as**.

> ![Screenshot of an arrow pointing to the save as
> button.](./media/image4.png)

7.  Salve o arquivo localmente no Desktop da VM. Você usará este arquivo
    mais tarde no exercício.

8.  Feche a aba ou janela do navegador de definições.

9.  Selecione o link **API Key**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. Copie e salve sua chave de API no bloco de notas da sua VM porque
    você precisará dela mais tarde.

> ![](./media/image6.png)

11. Selecione **Return to home**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. Selecione **Download Logo**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. Salve a imagem do logotipo localmente no Desktop da VM; você a usará
    mais tarde.

**Tarefa 2: Criar uma nova solução**

Para criar uma nova solução, siga estas etapas:

1.  Acesse <https://make.powerapps.com/> e certifique-se de que você
    está no ambiente **Dev One.**

> ![](./media/image9.png)

2.  No painel de navegação esquerdo, selecione **Solutions**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  Selecione **+New solution** na faixa superior.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

4.  Insira +++**Contoso invoicing**+++ para **Display name** e selecione
    **+ New publisher**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

5.  Digite +++**Contoso**+++ para Nome de exibição, +++**Contoso**+++
    para Nome, +++**contoso**+++ para Prefixo e selecione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> **Observação:** se você receber uma mensagem de erro como " A record
> with matching key values already exists ", ignore-a e feche a janela "
> New publisher ".
>
> ![](./media/image14.png)

6.  Agora, na janela **New solution**, selecione **Contoso** para
    **Publisher** e, em seguida, selecione **Create**. Quando estiver
    trabalhando em um projeto real, é melhor criar seu próprio editor.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  Não saia desta página após selecionar **Create**. Você será
    automaticamente direcionado para a solução ‘Contoso invoicing’.

**Tarefa 3: Criar um novo conector**

Para criar um novo conector, siga estas etapas:

1.  Certifique-se de que você está na solução **Contoso invoicing** que
    você criou.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

2.  Selecione **+ New** | **Automation** | **Custom connector**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

3.  Insira +++**Contoso invoicing**+++ para o **Connector name**.

> ![](./media/image18.png)

4.  Selecione **Upload** para carregar a imagem.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

5.  Selecione a imagem do logotipo do conector que você baixou na **Task
    1: Review the API**.

6.  Digite +++**\#175497**+++ para **Icon background color**.

7.  Insira +++**Custom connector for Contoso Invoicing API**+++ para
    **Description**.

8.  Digite +++**contosoinvoicingtest.azurewebsites.net**+++ para
    **Host**.

> ![](./media/image20.png)

9.  Selecione **Create connector**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

10. Não saia desta página.

**Tarefa 4: Importar a definição OpenAPI**

Para importar a definição do OpenAPI, siga estas etapas:

1.  Selecione a seta ao lado de **Connector Name**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image22.png)

2.  Selecione o botão de reticências ( **...** ) do conector e selecione
    **Update from OpenAPI file**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  Selecione **Import**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

4.  Selecione o arquivo **swagger.json** que você baixou na **Task 1:
    Review the API** e selecione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

5.  Selecione **Continue**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  Preencha a URL do host como
    +++**contosoinvoicingtest.azurewebsites.net**+++ e selecione
    **Security**.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

7.  Observe que os campos são preenchidos a partir do arquivo importado.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  Não saia desta página.

**Tarefa 5: Revisar e ajustar as definições**

Para revisar e ajustar as definições, siga estas etapas:

1.  Selecione a aba **Definition**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

2.  Reserve alguns minutos para revisar as operações que foram
    importadas.

3.  Observe o círculo de informações azul ao lado de **GetInvoice**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  Selecione a operação **GetInvoice**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Observe que a operação indica um **Summary** ausente.

> ![A screenshot of a phone Description automatically
> generated](./media/image32.png)

6.  Insira **Get Invoice** como **Summary** para melhorar a usabilidade.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

7.  Observe o círculo de informações azul ao lado da operação
    **PayInvoice** e que indica uma **Description** ausente.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

8.  Selecione a operação **PayInvoice**.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

9.  Insira **Pay an invoice** como **Description**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

10. Exclua ambas as operações **NewInvoice** pois você não as utilizará.

> ![Screenshot showing the delete action button.](./media/image37.png)

11. Selecione a operação **GetInvoiceSchema**.

> ![](./media/image38.png)

12. Modifique a opção **Visibility** para **internal** para que as
    pessoas não a vejam em sua lista de ações e selecione **Update
    connector**.

> ![](./media/image39.png)

13. Não saia desta página.

**Tarefa 6: Teste o conector**

Para testar o conector, siga estas etapas:

1.  Selecione a aba **Test**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

2.  Selecione **+ New connection**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

3.  Cole a **API Key** que você salvou na **Task 1: Review the API** e
    selecione **Create connection**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

4.  Selecione o botão **Refresh**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

5.  Selecione **ListInvoiceTypes | Test Operation**.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

6.  Você deverá ver os dados dos tipos de fatura na área body.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

7.  Selecione **Close** para fechar a janela do conector personalizado.

> ![](./media/image46.png)

**Tarefa 7: Usar conector personalizado no aplicativo Canvas**

Nesta tarefa, você criará um aplicativo Canvas e usará o conector
personalizado criado para exibir uma lista de faturas.

1.  Retorne ao portal do criador do Power Apps. Selecione **Done** no
    pop-up que diz ‘Currently creating a new custom connector’.
    Certifique-se de estar no ambiente **Dev One.**

> ![](./media/image47.png)
>
> **Observação:** Se o portal ainda não estiver aberto, navegue até
> +++<https://make.powerapps.com/>+++ e certifique-se de que você está
> no ambiente **Dev One.**

2.  Certifique-se de estar na solução **Contoso invoicing** que você
    criou. Caso contrário, selecione **Solutions** e abra a solução
    **Contoso invoicing** que você criou.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

3.  Selecione **+ New** e depois selecione **App \> Canvas app**.

> ![](./media/image49.png)

4.  Digite **Contoso invoicing app** como Nome do aplicativo, selecione
    **Phone** como Formato e, em seguida, selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

5.  Selecione **Skip** na janela de boas-vindas.

> ![](./media/image51.png)

6.  Selecione a aba **Data**, selecione **+ Add data**.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

7.  Expanda **Connectors** e selecione o conector personalizado
    **Contoso invoicing** que você criou.

> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

8.  Selecione **+ Add a connector**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

9.  Cole a chave de API que você salvou na **Task 1: Review the API** e
    selecione **Connect**.

> ![A screenshot of a login box Description automatically
> generated](./media/image55.png)

10. Selecione **Got it** no pop-up de aviso premium.

> ![A screenshot of a phone Description automatically
> generated](./media/image56.png)

11. Selecione a aba **Tree view**.

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

12. Selecione **+ Insert** e depois selecione **Vertical gallery**.

> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

13. Selecione **ContosoInvoicing** para dados.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

14. Defina os **itens** para o valor abaixo.

> +++ContosoInvoicing.ListInvoices().invoices+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image60.png)

15. Expanda a galeria e selecione a **Subtitle**.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

16. Defina o valor do **Text** do subtítulo como
    +++**ThisItem.amount**+++.

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

17. Expanda a galeria e selecione o **Title** dentro da galeria.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

18. Defina o valor de **Text** do Título como
    +++**ThisItem.accountName**+++.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

19. A galeria agora deve ficar como na imagem abaixo.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

**Resumo:** Neste laboratório, você aprendeu a criar um conector
personalizado para uma API existente, a importar a definição da API e a
usar esse conector no aplicativo Canvas para exibir uma lista de
faturas. Conectores personalizados são baseados em funções; chamando
operações específicas do serviço subjacente da API para retornar os
dados correspondentes.
