**Laboratório 9: Automatizar a implementação de soluções usando o GitHub
Actions para Microsoft Power Platform**

## **Tarefa 1: Criar o registro do aplicativo**

1.  Entre no portal do Microsoft Azure usando
    [<https://portal.azure.com/#home>](https://portal.azure.com/#home)
    com suas credenciais de locatário do Office 365.

2.  Selecione **Get started**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  Selecione **Skip** na página ‘How do you plan to use Azure’.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Selecione **Skip** na página ‘Now, let’s show you around Azure’.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Na página **Home** do portal, digite **Microsoft Entra ID** na caixa
    de pesquisa e selecione-o na lista de serviços sugeridos abaixo.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  No painel de navegação esquerdo, expanda **Manage** e selecione
    **App registrations**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

7.  Selecione **+ New registration** na página de **App registrations**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

8.  Na página **App registrations**, insira as informações de registro
    do seu aplicativo, conforme descrito na tabela.

[TABLE]

> ![A screenshot of a computer application Description automatically
> generated](./media/image7.png)

9.  Selecione **Register** para criar o registro do aplicativo.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

10. A página de visão geral do registro do aplicativo é exibida.
    Adicione um segredo do cliente selecionando **Certificates &
    secrets** no painel de navegação esquerdo. Selecione a aba **Client
    secrets** e, em seguida, **+ New client secret**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

11. Adicione uma **description** para o seu segredo do cliente – **My
    sample client secret**. Selecione uma **expiration** para o segredo
    como **Recommended: 180 days (6 months)** e, em seguida, selecione
    **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

12. Salve o **secret's value and ID** no bloco de notas para usar no
    código do seu aplicativo cliente. Este valor secreto nunca mais será
    exibido depois que você sair desta página.

> **Importante:** Não saia da página segredo do cliente antes de copiar
> o valor do segredo (e não o ID), pois você não terá acesso a esse
> valor novamente.
>
> ![](./media/image11.png)

## **Tarefa 2: Criar um novo usuário de aplicativo**

Siga estas etapas para criar um usuário de aplicativo e o vincular ao
registro do aplicativo.

1.  Faça login no centro de administração do Power
    Platform Platform <https://admin.powerplatform.microsoft.com/>
    usando suas credenciais de locatário do Office 365.

2.  Selecione **Environments** no painel de navegação esquerdo e, em
    seguida, selecione o ambiente **Dev One** na lista para exibir as
    informações do ambiente.

> ![](./media/image12.png)

3.  Selecione o link **See all** em **S2S apps** no lado direito da
    página.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  Selecione + **New app user**.

> ![](./media/image14.png)

5.  No painel lateral **Create a new app user,** selecione **+ Add an
    app**.

> ![A screenshot of a login page Description automatically
> generated](./media/image15.png)

6.  Comece a digitar o nome do registro do seu aplicativo -
    **Mytestingapp** no campo de pesquisa e selecione (check) na lista
    de resultados. Em seguida, selecione **Add**.

> ![](./media/image16.png)

7.  De volta ao painel lateral **Create a new app user,** selecione a
    **Business unit** no menu suspenso. Selecione o **ícone de lápis**
    ao lado de **Security roles**, selecione **System Administrator**
    para o usuário do aplicativo (também conhecido como princípio de
    serviço) e selecione **Save.** 

> ![A screenshot of a login page Description automatically
> generated](./media/image17.png)

8.  Selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

9.  Você deverá ver o novo usuário do aplicativo na lista exibida de
    usuários de aplicativo.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

## **Tarefa 3: Construir um aplicativo orientado por modelos**

Siga as etapas abaixo para criar um aplicativo orientado por modelo.

1.  No seu navegador, acesse
    [https://make.powerapps.com](https://make.powerapps.com/) e faça
    login com suas credenciais. Clique no menu suspenso do seletor de
    ambientes no cabeçalho e selecione seu ambiente de desenvolvimento.

> ![](./media/image20.png)

2.  Clique na área **Solutions** na navegação à esquerda e, em seguida,
    clique no botão **New solution** para criar uma nova solução.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

3.  Insira o **Display name** da solução como **GitHub Lab** e o
    **name** – **GitHubLab**. Selecione **+ New publisher** em
    Publisher.

> ![](./media/image22.png)

4.  Para os propósitos deste laboratório, insira **'GitHub Lab'** para
    **display name**, **'GitHubLab'** para **name** e **'gitlab'** como
    **prefix** e, em seguida, escolha **Save** e **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  No novo painel de solução, selecione o **publisher – GitHub Lab**
    que você acabou de criar e clique em **Create** para criar uma nova
    solução não gerenciada no ambiente.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

6.  Sua nova solução estará vazia e você precisará adicionar
    componentes. Neste laboratório, criaremos uma tabela personalizada.
    Clique no menu suspenso **+ New** na barra de navegação superior e
    selecione **Table \> Set advanced properties.**

> ![](./media/image25.png)

7.  Insira um **display name – Time Off Request,** o nome no plural será
    gerado para você. Clique em **Save** para criar a tabela.

> ![](./media/image26.png)

8.  Depois que a tabela for criada, selecione Table na navegação de
    localização para voltar à visualização da solução e adicionar outro
    componente.

> ![](./media/image27.png)

9.  Clique no menu suspenso **+ New**, depois em **App** e, por fim,
    clique em **Model-driven app**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

10. Digite um nome para o aplicativo – **Time Off Requests** e clique no
    botão **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

11. No designer do aplicativo, clique em **+ Add page**.

> ![](./media/image30.png)

12. Selecione a **Dataverse table**.

> ![](./media/image31.png)

13. Selecione **Time Off Request**, marque a caixa de seleção **Show in
    navigation**. Selecione **Add**.

> ![](./media/image32.png)

14. Clique em **Publish** e, quando a ação de publicação estiver
    concluída, clique em **Play**.

> ![](./media/image33.png)

15. Isso o levará a aplicação para que você possa ver como ele fica.
    Você pode usar a aplicação e fechar a aba quando estiver satisfeito.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

## **Tarefa 4: Criar uma conta no GitHub**

**Observação:** Se você já tiver uma conta no GitHub, poderá pular esta
tarefa e passar para a próxima.

1.  Acesse [https://github.com](https://github.com/) e clique em **Sign
    up** ou **Start a free trial** (ou faça login se você já tiver uma
    conta).

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

2.  Digite seu **email id** e clique em **Continue**.

> ![A screen shot of a computer Description automatically
> generated](./media/image36.png)

3.  Mantenha a senha gerada automaticamente ou crie sua própria senha e
    clique em **Continue**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

4.  Digite o **Username – Labtesting1** e clique em **Continue**. Se o
    nome de usuário fornecido não estiver disponível, digite um nome de
    usuário diferente.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

5.  Selecione **Continue**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Na página ‘Verify your account’, selecione **Verify**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

7.  Conclua o processo de verificação e use o código de lançamento
    recebido no seu e-mail.

8.  Selecione **Sign in** na janela ‘Sign in to GitHub’ que aparece.

> ![](./media/image41.png)

9.  Selecione **Skip personalization**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

## **Tarefa 5: Criando um novo segredo para autenticação com Service Principal**

1.  Depois de criar sua conta, crie um repositório selecionando **Create
    repository**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> Você verá a seguinte tela como alternativa:
>
> ![Create a new repository](./media/image44.png)

2.  Crie seu novo repositório e nomeie '**poweractionslab**'.
    Certifique-se de selecionar **Add a README file** para iniciar o
    repositório e escolha **Create repository**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

3.  Navegue até seu repositório e clique em **Settings**.

> ![](./media/image46.png)

4.  No painel esquerdo, expanda **Secrets and variables** e clique em
    **Actions**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  Role para baixo e selecione **New repository secret**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  Na página Segredos, nomeie o segredo como '**PowerPlatformSPN**'.
    Use o valor do segredo do cliente do registro do aplicativo criado
    no Microsoft Entra (que você salvou no bloco de notas), insira-o no
    campo **Secret** e selecione **Add secret**. O segredo do cliente
    será referenciado nos arquivos YML usados para definir os fluxos de
    trabalho do GitHub posteriormente neste laboratório.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

O segredo do cliente agora está armazenado com segurança como um segredo
do GitHub.

## **Tarefa 6: Criar um fluxo de trabalho para exportar e descompactar o arquivo de solução em um novo branch**

1.  Clique em **Actions** na barra horizontal acima.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

2.  Clique em **Configure** na caixa **Simple workflow**, na seção
    sugerida para este repositório.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

3.  Isso iniciará um novo arquivo YAML com um fluxo de trabalho básico
    para ajudar você a começar a usar as ações do GitHub.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)

4.  Exclua o conteúdo pré-criado e cole o conteúdo do arquivo
    [export-and-branch-solution-with-spn-auth.yml](https://github.com/microsoft/powerplatform-actions-lab/blob/main/sample-workflows/export-and-branch-solution-with-spn-auth.yml).
    Abra o link fornecido na nova aba da VM.

> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

5.  **Rename** o arquivo para **export-and-branch-solution.yml**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

6.  Atualize \<ENVIRONMENTURL\> na linha 28 com a URL do ambiente de
    desenvolvimento do qual você deseja exportar.

> ![Rename and replace content.](./media/image55.png)
>
> Para obter a URL do ambiente, acesse o **Power Platform Admin
> center**. Selecione **Environments** na barra de navegação à esquerda,
> clique em **Dev One** e copie a URL do ambiente.
>
> ![](./media/image56.png)

7.  **Paste** a **Environment URL** no arquivo yml. Certifique-se de
    adicionar https://. Sua URL deve estar no formato fornecido -
    https://orgfc5xxxfd.crm.dynamics.com

> ![](./media/image57.png)

8.  Atualize \<APPID\> e \<TENANT ID\> com seus valores. Para obter
    esses dois valores, acesse o portal do Azure e selecione **Home** \>
    **Microsoft Entra ID** \> **App** Registro**,** selecione a aba
    **All applications** e, em seguida, **Mytestingapp**.

> ![A screen shot of a computer Description automatically
> generated](./media/image58.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image59.png)

9.  Cole os valores nas linhas 29 e 30.

> ![](./media/image60.png)

10. Na linha 12 do código, altere o valor padrão ALMLab para GitHubLab,
    que é o nome da nossa solução neste caso. Certifique-se de não
    deixar espaços e escreva-o corretamente como fornecido. Se você deu
    um nome diferente para a sua solução , escreva-o aqui.

> ![A screenshot of a computer Description automatically
> generated](./media/image61.png)

11. Agora você está pronto para confirmar suas alterações. Selecione
    **Commit changes** e, no painel Confirmar alterações que se abre,
    selecione **Commit changes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image62.png)
>
> Parabéns, você acabou de criar seu primeiro fluxo de trabalho do
> GitHub usando as seguintes ações:

- **Quem sou eu**: Garante que você possa se conectar com sucesso ao
  ambiente do qual está exportando.

- **Exportar solução** : Exporta o arquivo de solução do seu ambiente de
  desenvolvimento.

- **Descompactar Solução** : O arquivo de solução exportado do servidor
  é um arquivo compactado (zip) com arquivos de configuração
  consolidados. Esses arquivos iniciais não são adequados para o
  gerenciamento de código-fonte, pois não são estruturados para que os
  sistemas de gerenciamento de código-fonte possam diferenciar
  adequadamente os arquivos e capturar as alterações que você deseja
  enviar para o controle de origem. Você precisa ‘unpack’ os arquivos de
  solução para torná-los adequados para armazenamento e processamento no
  controle de origem.

- **Solução de Branch**: Cria uma nova branch para armazenar a solução
  exportada.

## **Tarefa 7: Testar o fluxo de trabalho de exportação e descompactação**

1.  Em seguida, para testar se o fluxo de trabalho é executado,
    selecione **Actions** na barra horizontal acima e selecione o fluxo
    de trabalho de **export-and-branch-solution** listado em **All
    workflows** no painel lateral esquerdo.

> ![](./media/image63.png)

2.  Selecione **Run workflow** e, novamente, escolha **Run workflow**.
    Se o nome da solução for diferente de 'GitHubLab', altere o valor,
    mas deixe os outros valores como estão.

> ![](./media/image64.png)

3.  Após 5 a 10 segundos, o fluxo de trabalho será iniciado e você
    poderá selecionar o fluxo de trabalho em execução para monitorar o
    progresso.

> ![](./media/image65.png)
>
> ![](./media/image66.png)

4.  Após a conclusão do fluxo de trabalho, confirme se uma nova branch
    foi criada com a solução descompactada na pasta
    **solutions/GitHubLab**. Navegue até** **a aba ***Code***.

> ![A screenshot of a computer Description automatically
> generated](./media/image67.png)

5.  Expanda o menu suspenso **Branches**.

> ![](./media/image68.png)

6.  Selecione o branch – **GitHubLab-xxxx-xxxx** que foi criado pela
    ação.

> ![A screenshot of a computer Description automatically
> generated](./media/image69.png)

7.  Valide se a pasta **solutions/GitHubLab** foi criada na nova branch

> ![A screenshot of a computer Description automatically
> generated](./media/image70.png)

8.  Para criar uma solicitação de pull para mesclar as alterações no
    branch principal, clique em **Contribute** e no flyout clique
    em** ***Open Pull request*.

> ![A screenshot of a computer Description automatically
> generated](./media/image71.png)

9.  Na tela *Open Pull request*, mantenha o título como está e clique em
    **Create pull request*.***

> ![A screenshot of a computer Description automatically
> generated](./media/image72.png)

10. A tela será atualizada mostrando a pull request recém- criada. Assim
    que a pull request for criada, será fornecida uma confirmação
    indicando que nossa branch não tem conflito com a branch principal.

> ![A screenshot of a computer Description automatically
> generated](./media/image73.png)

11. Esta confirmação significa que as alterações podem ser mescladas
    automaticamente na branch principal. Clique em **Merge pull
    request.** 

> ![A screenshot of a computer Description automatically
> generated](./media/image74.png)

12. Clique em **Confirm merge**.

> ![A screenshot of a computer Description automatically
> generated](./media/image75.png)

13. Opcionalmente, clique em excluir branch para limpar o branch
    extinto.

> ![A close up of a message Description automatically
> generated](./media/image76.png)

14. Clique em **Code**.

> ![](./media/image77.png)

15. Você será direcionado de volta para o branch padrão (principal) e
    validará se a solução agora está disponível lá também.

> ![A screenshot of a computer Description automatically
> generated](./media/image78.png)
