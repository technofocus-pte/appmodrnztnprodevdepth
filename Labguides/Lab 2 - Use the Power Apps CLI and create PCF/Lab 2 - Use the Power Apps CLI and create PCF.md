# **Laboratório 2: Usar a CLI do Power Apps e criar o Power Apps Component Framework (PCF)**

**Duração estimada:** 30 minutos

**Objetivo:** Neste laboratório, você aprenderá a instalar o Power
Platform Tools e criar seu primeiro componente do Power Apps Component
Framework (PCF).

## **Tarefa 1: Instalar o Power Platform Tools**

1.  Abra o Visual Studio Code usando o atalho presente no Desktop da VM
    e selecione o ícone **Extensions** na barra de navegação.

> ![A screenshot of a computer program Description automatically
> generated](./media/image1.png)

2.  Pesquise por +++**power platform tools**+++. Selecione o botão
    **Install** nos resultados da pesquisa.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Aguarde até que a instalação esteja concluída.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Selecione **mais opções (…),** **Terminal** e então selecione **New
    Terminal**.

> **Observação:** Se você não vir (… 3 pontos), selecione **hamburger |
> Terminal | New Terminal.**
>
> ![](./media/image4.png)
>
> ![](./media/image5.png)

5.  Execute o comando pac para ver quais comandos estão disponíveis:

> +++pac+++
>
> ![A black screen with white text and red rectangle with yellow and
> black text Description automatically generated](./media/image6.png)
>
> ![](./media/image7.png)
>
> ![Screenshot showing a list of commands.](./media/image8.png)

6.  Você pode digitar pac seguido de um comando para ver quais opções
    ele oferece. Por exemplo, tente o seguinte:

> +++pac admin+++
>
> ![](./media/image9.png)
>
> **Observação:** Se você vir o pop-up dizendo ‘Some keybindings don’t
> got to the terminal by default and are handled by Visual Studio Code
> instead’, selecione **Configure Terminal Settings**.
>
> ![A black background with white text Description automatically
> generated](./media/image10.png)

7.  Você pode ver quais opções o administrador tem.

> ![](./media/image11.png)

8.  Navegue até o portal do criador do Power Apps
    usando <https://make.powerapps.com/> e certifique-se de ter o
    ambiente **Dev One** selecionado**.**

9.  No canto superior direito da tela, selecione o ícone **Settings** e
    escolha **Session details**.

> ![](./media/image12.png)

10. Na caixa de diálogo de detalhes da sessão do Power Apps, selecione
    valor **Instance url** e copie-o para uso posterior no exercício.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. Volte para o terminal do Visual Studio Code, digite o seguinte
    comando para estabelecer uma conexão a partir da CLI e entre no seu
    ambiente de teste quando solicitado.

> +++pac auth create --name Lab --url **\<Your Instance URL\>**+++
>
> ![](./media/image14.png)

12. Entre com suas credenciais de administrador do M365.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

13. Digite a **password** e clique em **Sign in**.

> ![A screenshot of a login page Description automatically
> generated](./media/image16.png)

14. Você verá a mensagem indicando que a autenticação foi realizada com
    sucesso.

> ![A screenshot of a computer program Description automatically
> generated](./media/image17.png)

15. Digite o seguinte comando who, que exibirá o ambiente e as
    informações do usuário. Isso é bom para garantir que você esteja no
    ambiente correto.

> +++pac org who+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

## **Tarefa 2: Criar um componente Power Apps Component Framework (PCF)**

1.  Execute o comando abaixo para criar uma nova pasta chamada
    **labPCF** dentro da pasta do seu usuário.

> +++md labPCF+++
>
> ![](./media/image19.png)

2.  Você pode ver que a pasta labPCF foi criada.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

3.  Altere o diretório para a pasta que você criou.

> +++cd labPCF+++
>
> ![A black and white image of a person's hand Description automatically
> generated](./media/image21.png)

4.  Execute o comando abaixo para inicializar o projeto do componente.

> +++pac pcf init --namespace lab --name FirstControl --template
> field+++
>
> ![A screen shot of a computer Description automatically
> generated](./media/image22.png)

5.  Digite o seguinte comando e pressione Enter. Isso extrairá todas as
    dependências do repositório npm.

> +++npm install+++
>
> ![](./media/image23.png)

6.  Se for solicitado que você atualize o npm, use o comando fornecido,
    conforme mostrado na imagem abaixo. Nesse caso, npm install -g
    npm@10.8.2 é usado.

> ![](./media/image24.png)

7.  Abra a pasta no Visual Studio Code usando o seguinte comando.

> +++code .+++

8.  Se você encontrar uma janela pop-up perguntando Do you trust the
    authors of the file?, clique em **Yes, I trust the authors**.

> ![](./media/image25.png)

9.  Se for solicitado que você escolha o tema de cores, clique em Brows
    Color Themes; caso contrário, ignore esta etapa e a próxima.

> ![](./media/image26.png)

10. Selecione o tema de cor **Dark Modern**.

> ![](./media/image27.png)

11. Explore os arquivos que foram criados.

12. Expanda a pasta **FirstControl** e selecione **Index.ts.**

> ![](./media/image28.png)
>
> **Observação:** Na janela pop-up com a mensagem ‘Do you want to allow
> untrusted files in this window’, selecione **Allow**.
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

13. Cole as duas variáveis a seguir dentro da exportação.

> ![A screen shot of a computer Description automatically
> generated](./media/image30.png)

14. Cole o seguinte dentro da função **init()** para criar os controles
    HTML e definir o valor do rótulo.

> this.label = document.createElement("input");
>
> this.label.setAttribute("type", "label");
>
> this.label.value = "My First PCF";
>
> this.\_container = document.createElement("div");
>
> this.\_container.appendChild(this.label);
>
> container.appendChild(this.\_container);
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image31.png)

15. Para salvar o arquivo, vá até a aba **File** e selecione **Save**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image32.png)

16. Acesse o terminal, digite o seguinte comando e, em seguida,
    pressione Enter. Isso iniciará o teste com o código mais recente,
    conforme mostrado na terceira captura de tela desta etapa.

> +++npm start+++
>
> ![](./media/image33.png)
>
> **Observação:** Se você receber uma mensagem informando que o Firewall
> do Windows Defender bloqueou alguns recursos, selecione Allow access.
>
> ![A screenshot of a computer security alert Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

17. O test harness é eficaz para uso no início do projeto, permitindo
    que você veja a aparência do seu controle visualmente, sem precisar
    implementá-lo em um ambiente. Você pode definir valores de
    propriedade para alterar o tamanho da área de controle. Após
    terminar de explorar o test harness, volte ao terminal e pressione
    Ctrl-C para encerrar a execução do test harness.

> ![A screenshot of a computer program Description automatically
> generated](./media/image36.png)

18. Digite **Y** e \[ENTER\].

> ![](./media/image37.png)

19. Execute o seguinte comando para listar soluções em seu ambiente.

> +++pac solution list+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

20. Estas são as soluções atuais do seu ambiente. O próximo passo será
    adicionar uma para o componente.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

21. Digite o seguinte comando push para enviar nosso controle para o
    ambiente.

> +++pac pcf push --publisher-prefix lab+++
>
> ![A screenshot of a computer program Description automatically
> generated](./media/image39.png)

## **Tarefa 3: Usar o componente em um aplicativo**

1.  Navegue até o Centro de administração do Microsoft Power Platform
    usando +++<https://admin.powerplatform.microsoft.com/home>+++.

2.  Feche a janela welcome.

> ![](./media/image40.png)

3.  Selecione o ambiente **Dev One** que você está usando para o
    laboratório.

> ![](./media/image41.png)

4.  Selecione **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

5.  Expanda a área **Product** e selecione **Features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

6.  No lado direito, ative o recurso **Allow publishing of canvas apps
    with code components**.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

7.  Selecione **Save** na parte inferior.

> ![](./media/image45.png)

8.  Navegue até o portal do criador do Power Apps usando
    +++<https://make.powerapps.com/>+++ e certifique-se de que você está
    no ambiente correto, ou seja, **Dev One**.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

9.  Selecione **Solutions** no painel de navegação esquerdo e depois
    selecione **Import solution**.

> ![](./media/image47.png)

10. Selecione **Browse** na caixa de diálogo Import a solution.

> ![A white background with black text Description automatically
> generated](./media/image48.png)

11. Selecione o arquivo zip da solução no caminho -
    labPCF\obj\PowerAppsToolsTemp_lab\bin\Debug e selecione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

12. Após importar o arquivo zip, clique em **Next**.

> ![](./media/image50.png)

13. Selecione **Import**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

14. Aguarde até que a mensagem que diz: Solução
    “**PowerAppsToolsTemp_lab**” foi importada com sucesso.

> ![](./media/image52.png)

15. Clique duas vezes na solução recém-importada -
    **PowerAppsTools_lab** para abri-la.

> ![](./media/image53.png)

16. Você deverá ver seu componente listado.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

17. Selecione **+ New | App | Canvas app**.

> ![](./media/image55.png)

18. Selecione **Phone** para Formato, insira **First PCF** para Nome do
    aplicativo e selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)

19. Selecione **Skip** na janela de boas-vindas.

> ![](./media/image57.png)

20. No painel esquerdo, selecione **Add (+)** e, em seguida, selecione o
    ícone **Get more components** situado acima da lista de componentes
    populares e abaixo da caixa de pesquisa, conforme mostrado na imagem
    a seguir.

> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

21. Selecione a aba **Code**.

> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

22. Selecione seu componente – **FirstControl**. Selecione **Import**.

> ![](./media/image59.png)

23. Na barra de ferramentas à esquerda, selecione **+** e expanda **Code
    components**.

> ![](./media/image60.png)

24. Selecione o **FirstControl**. Agora você deverá ver o controle com o
    texto **My First PCF** no canvas.

> ![](./media/image61.png)

25. Selecione **Save** para salvar a aplicação.

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)

Agora você criou seu primeiro componente Power Apps Component Framework
(PCF) e o utilizou em um aplicativo Canvas.

**Resumo:** Neste laboratório, você aprendeu a criar seu primeiro
componente Power Apps Component Framework (PCF) e a utilizá-lo em um
aplicativo Canvas. O Power Apps Component Framework cria componentes de
código para aplicativos Canvas e orientados a modelos. Esses componentes
de código podem ser usados para aprimorar a experiência do usuário que
trabalha com dados em formulários, exibições, painéis e telas de
aplicativos Canvas.
