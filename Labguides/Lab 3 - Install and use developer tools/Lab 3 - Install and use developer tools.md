**Laboratório 3 - Instalar e usar ferramentas de desenvolvedor**

**Duração estimada:** 15 minutos

**Objetivo:** Neste laboratório, você aprenderá a instalar algumas das
ferramentas de desenvolvedor do NuGet.

**Tarefa 1: Instalar ferramentas de desenvolvedor**

Nesta tarefa, você usará uma CLI do Power Platform para instalar
ferramentas.

1.  Para iniciar o **Command Prompt**, vá ao menu **Start** da VM,
    digite Prompt de Comando na caixa de pesquisa e selecione **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Execute o comando abaixo para instalar a **Ferramenta**
    **Configuration Manager**.

> +++pac tool cmt+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  A Ferramenta Configuration Manager deve ser instalada e iniciada.
    Feche a Ferramenta Configuration Manager.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Execute o comando abaixo para instalar a **Ferramenta** **Package
    Deployer**.

> +++pac tool pd+++
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  A ferramenta Package Deployer deve ser instalada e iniciada. Feche a
    ferramenta Package Deployer.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Execute o comando abaixo para instalar a **Ferramenta Plugin
    Registration**.

> +++pac tool prt+++
>
> ![](./media/image6.png)

7.  O Plugin Registration deve ser instalado e iniciado. Não feche a
    Ferramenta Plugin Registration.

> ![](./media/image7.png)

**Tarefa 2: Explorar um plug-in registrado com a ferramenta plug-in
registration**

1.  Selecione **Create New Connection.**

> ![](./media/image8.png)

2.  Marque a caixa de seleção para **Display list of available
    organizations**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  Selecione **Login.** 

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Entre com suas credenciais do ambiente Dataverse, ou seja,
    credenciais de administrador do Office 365. Clique em **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  Digite a senha do seu administrador de locatário e clique em **Sign
    in**.

> ![A screenshot of a login box Description automatically
> generated](./media/image12.png)

6.  Neste caso, você pode ver que o ambiente **Dev One** já está
    selecionado. Caso a lista de ambientes apareça, selecione o seu
    ambiente – **Dev One** – e selecione **Login** novamente.

> ![](./media/image13.png)

7.  Você verá uma lista de plug-ins do sistema . Se você tiver plug-ins
    personalizados em seu ambiente, também os verá na lista. Os
    (Assembly) são DLLs .NET que implementam os plug-ins.

> **Observação:** Você precisa expandir a seção para ver a lista
> completa.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

8.  Localize **Microsoft.CDS.DataLakeDataProvider.Plugins** e expanda-o.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

9.  Cada um dos itens filhos é implementado no assembly. Expanda um dos
    itens para ver os registros de etapas daquele plug-in específico.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

10. O registro de etapas conecta o plug-in como um manipulador de
    eventos ao evento. No exemplo acima, isso está manipulando uma
    criação na tabela insightsstorevirtualentity.

> ![](./media/image17.png)

11. Clique duas vezes em qualquer etapa para ver os detalhes de
    configuração da etapa, incluindo a mensagem e a entidade em que ela
    está registrada, o estágio do pipeline em que o plug-in será
    invocado, se a execução é síncrona ou assíncrona, etc.

> ![](./media/image18.png)

**Resumo:** Neste laboratório, você aprendeu a instalar ferramentas de
desenvolvedor. Ao criar seu próprio plug-in personalizado, você usará a
Ferramenta Plugin Registration para carregar o assembly e registrar as
etapas dos eventos que deseja manipular.
