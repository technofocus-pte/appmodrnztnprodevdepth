**Laboratório 5: Criar uma API personalizada**

**Duração estimada:** 35 minutos

**Objetivo:** Neste laboratório, você aprenderá a criar uma API
personalizada do Dataverse para executar lógicas personalizadas. Em
seguida, você usará a API personalizada a partir de uma etapa em um
fluxo do Power Automate.

**Tarefa 1: Criar o projeto de API personalizado**

1.  Clique no menu **Start** da VM, digite o Prompt de Comando na caixa
    de pesquisa e selecione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Execute o comando abaixo para criar uma nova pasta chamada
    **CustomAPILab**.

> +++md CustomAPILab+++
>
> ![](./media/image2.png)

3.  Mude o diretório para a pasta que você criou.

> +++cd CustomAPILab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image3.png)

4.  Agora você deve estar na pasta CustomAPIlAB. Execute o comando
    abaixo para inicializar uma nova biblioteca de classes de plug-in do
    Dataverse.

> +++pac plugin init+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  A criação da biblioteca de classes do plugin Dataverse deve ser
    bem-sucedida.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Execute o comando abaixo para abrir o projeto no Visual Studio.

> +++start CustomAPILab.csproj+++
>
> ![](./media/image6.png)

7.  Se solicitado, selecione **Microsoft Visual Studio 2022** e depois
    selecione **Just once**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  Se você for solicitado a entrar no Visual Studio, selecione **Skip
    this for now** na página de login.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  Selecione **General** como Development settings, escolha **Dark**
    como tema de cor e selecione **Start Visual Studio**.

> **Observação:** ignore esta etapa se você for direcionado diretamente
> para o projeto.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

10. O projeto deve abrir no Visual Studio.

> ![](./media/image10.png)

11. Clique com o botão direito do mouse no arquivo Plugin1.cs e
    renomeie-o para **MatchPlugin.cs**.

> ![](./media/image11.png)

12. Selecione **Yes** para a caixa de diálogo que deseja renomear um
    arquivo.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Clique com o botão direito do mouse no Projeto CustomAPILab e
    selecione **Manage NuGet Packages**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

14. Procure por **System.Text.RegularExpressions** e selecione
    **Install**.

> ![](./media/image14.png)

15. Na janela Visualizar alterações, selecione **Apply** para permitir
    que o Visual Studio faça alterações na solução.

> ![](./media/image15.png)

16. Selecione **I Accept** para aceitar os termos da licença.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

17. Abra o arquivo **MatchPlugin.cs**.

> ![](./media/image17.png)

18. Adicione a seguinte declaração abaixo da instrução i.e. 'using
    System;', na linha nº 3.

> +++using System.Text.RegularExpressions;+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

19. Adicione as seguintes linhas dentro do método ExecuteDataversePlugin
    e após a linha var context. Essas linhas obtêm o valor dos
    parâmetros de entrada passados na invocação da API personalizada.

> string input = (string)context.InputParameters\["StringIn"\];
>
> string pattern = (string)context.InputParameters\["Pattern"\];
>
> ![](./media/image19.png)

20. Adicione a seguinte linha para obter o serviço de rastreamento.

> ITracingService tracingService =
> (ITracingService)localPluginContext.ServiceProvider.GetService(typeof(ITracingService));
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image20.png)

21. Adicione a linha abaixo para escrever o valor de entrada no
    rastreamento.

> tracingService.Trace("Provided input: " + input);
>
> ![](./media/image21.png)

22. Adicione a seguinte linha depois para chamar o método Regex.Match.

> var result = Regex.Match(input, pattern);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image22.png)

23. Escreva o resultado a ser rastreado.

> tracingService.Trace("Matching result: " + result.Success);
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image23.png)

24. E, por fim, adicione a seguinte linha para definir o parâmetro de
    saída Matched.

> context.OutputParameters\["Matched"\] = result.Success;
>
> ![A screen shot of a computer program Description automatically
> generated](./media/image24.png)

25. Seu método execute deve se parecer com o seguinte.

> ![A screen shot of a computer program Description automatically
> generated](./media/image25.png)

26. Selecione **Build | Build Solution**.

> ![](./media/image26.png)

27. O projeto deve ser criado com sucesso.

> ![A screenshot of a computer program Description automatically
> generated](./media/image27.png)

**Tarefa 2: Registre o plugin de API personalizado**

1.  Abra o prompt de comando e execute o comando abaixo para iniciar a
    Ferramenta de Registro de Plug-in.

> +++pac tool prt+++
>
> ![A black screen with white text Description automatically
> generated](./media/image28.png)

2.  Selecione **+ Create New Connection**.

> ![](./media/image29.png)

3.  Selecione **Office 365**, forneça suas credenciais e selecione
    **Login.**

> ![A screenshot of a login box Description automatically
> generated](./media/image30.png)

4.  Entre com seu **M365 Admin tenant Id** e selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Insira sua **senha ID do locatário de administrador do M365** e
    selecione **Sign in**.

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

6.  Verifique se o ambiente **Dev One** está selecionado.

7.  Selecione **Register | Register New Assembly**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

8.  Selecione ... na Etapa 1 e navegue até a pasta
    **CustomAPILab\bin\Debug\net462**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

9.  Selecione **CustomAPILab.dll** e depois selecione **Open**.

> ![](./media/image35.png)

10. Selecione **Register Selected Plugins**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

11. Selecione **OK** na mensagem de sucesso. Seu plugin está pronto para
    se conectar à API personalizada que criaremos na próxima tarefa.

> ![A screenshot of a computer error Description automatically
> generated](./media/image37.png)

**Tarefa 3: Criar a API personalizada**

1.  Navegue até o portal do criador do Power Apps usando
    +++<https://make.powerapps.com/>+++ e verifique se você está no
    ambiente **Dev One.**

2.  Selecione **Solutions** no painel de navegação à esquerda. Selecione
    **+ New Solution**.

> ![](./media/image38.png)

3.  Digite +++**Custom API Lab**+++ no Display Name.

4.  Selecione **CDS Default Publisher** no Publisher dropdown.

5.  Selecione **Create**. Isso criará uma solução personalizada que
    conterá nossos componentes.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Selecione **+ New | More | Other | Custom API.**

> ![](./media/image40.png)

7.  Insira as seguintes informações:

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

8.  Em Tipo de plug-in, selecione o ícone de pesquisa e localize seu
    plugin - **CustomAPILab.MatchPlugin**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

9.  Selecione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

10. Selecione **Done**.

> ![A screenshot of a website Description automatically
> generated](./media/image43.png)

11. Selecione **+** **New | More| Other | Custom API Request
    Parameter**.

> ![](./media/image44.png)

12. Para **Custom API**, selecione o ícone **Search** e selecione
    **Match** (sua API personalizada).

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. Insira +++**StringIn**+++ para Unique Name, Name, Display Name e
    Description para simplificar.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

14. Selecione **String** para Tipo.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

15. Selecione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

16. Selecione **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

17. Para adicionar mais um, Parâmetro de solicitação de API
    personalizado, selecione **+** **New | More| Other | Custom API
    Request Parameter.**

> ![](./media/image50.png)

18. Para **Custom API**, selecione o ícone **Search** e selecione
    **Match** (sua API personalizada).

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

19. Insira **Pattern** para Unique Name, Name, Display Name e
    Description para simplificar.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

20. Selecione **String** para Type.

> ![A screenshot of a string Description automatically
> generated](./media/image53.png)

21. Selecione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

22. Selecione **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

23. Selecione **New | More | Other| Custom API Response Property**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

24. Para **Custom API**, selecione o ícone **Search** e selecione
    **Match** (sua API personalizada).

> ![A screenshot of a computer Description automatically
> generated](./media/image57.png)

25. Insira +++**Matched**+++ para **Unique Name**, **Name, Display
    Name** e **Description** para simplificar.

26. Selecione **Boolean** para **Type**.

> ![](./media/image58.png)

27. Selecione **Save and Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

28. Selecione **Done**.

> ![A screenshot of a white text Description automatically
> generated](./media/image60.png)

29. Sua lista de componentes da solução deve se parecer com a seguinte.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

**Tarefa 4: Usar API personalizada do Power Automate**

1.  Na solução, selecione **+ New | Automation | Cloud Flow | Instant**.

> ![](./media/image62.png)

2.  Insira +++**String match**+++ para Flow name, selecione o acionador
    **Manually trigger a flow** e selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image63.png)

3.  Selecione **+ New Step**.

> ![A screenshot of a computer Description automatically
> generated](./media/image64.png)

4.  Pesquise por executar e escolha **Perform an unbound action**.

> ![A screenshot of a computer Description automatically
> generated](./media/image65.png)

5.  Na lista Nome da ação, localize e selecione **contoso_match**.

> ![](./media/image66.png)

6.  Insira o endereço de e-mail **myemail@outlook.com** em **StringIn**.
    Aqui, você pode digitar qualquer endereço de e-mail simples válido.

> ![](./media/image67.png)

7.  Insira a seguinte expressão regular em Padrão. Este é um padrão de
    e-mail simples. Outros
    [*exemplos*](https://regexlib.com/DisplayPatterns.aspx/) estão
    disponíveis.

> +++^\w+@\[a-zA-Z\_\]+?\\\[a-zA-Z\]{2,3}$+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image68.png)

8.  Seu fluxo deve ficar parecido com o seguinte.

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

9.  Selecione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

10. Após a conclusão do salvamento, selecione **Test**.

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

11. Selecione **Manually** e depois **Test**.

> ![A screenshot of a phone Description automatically
> generated](./media/image72.png)

12. Selecione **Run flow**.

> ![A white background with black dots Description automatically
> generated](./media/image73.png)

13. Selecione **Done**.

> ![A screenshot of a phone Description automatically
> generated](./media/image74.png)

14. Após a conclusão do fluxo, selecione **Perform an unbound action**
    para expandir e ver os resultados.

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)
>
> ![Screenshot showing the results of running the
> flow.](./media/image76.png)

**Resumo:** Neste laboratório, você aprendeu a criar uma ação
personalizada e usá-la a partir de um fluxo do Power Automate. A ação de
API personalizada contoso_match agora também está disponível para
chamada diretamente usando a API da plataforma.
