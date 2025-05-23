---
lab:
  task: Configure Retention Policies
  exercise: Exercise 1 - Configure Retention Policies
---

## Locatários do WWL – Termos de uso

Se você estiver recebendo um locatário como parte de uma entrega de treinamento com instrutor, observe que o locatário é disponibilizado com a finalidade de dar suporte aos laboratórios práticos no treinamento com instrutor.

Os locatários não devem ser compartilhados ou usados para fins fora dos laboratórios práticos. O locatário usado neste curso é um locatário de avaliação e não pode ser usado ou acessado após o fim da aula e não está qualificado para extensão.

Os locatários não podem ser convertidos em uma assinatura paga. Os locatários obtidos como parte deste curso permanecem a propriedade da Microsoft Corporation e reservamos o direito de obter acesso e a qualquer momento.

# Exercício 1 – Tarefas de qualificação

Sua tarefa é criar e gerenciar políticas de retenção que atendam aos critérios exigidos:

- **Política de retenção em toda a empresa**: aplique um período de retenção e defina os locais para essa política.
- **Políticas de retenção baseadas na localização**: crie políticas de retenção para locais específicos, como canais e chats do Teams, incluindo usuários específicos.
- **Políticas de retenção do PowerShell**: implemente políticas de retenção usando o PowerShell.
- **Políticas de escopo adaptável**: crie e aplique políticas de retenção com escopos adaptáveis para departamentos como jurídico e de varejo.

## Tarefa 1 – Criar política de retenção em toda a empresa

Aqui, você criará uma política de retenção que se aplica a toda a organização.

1. No Microsoft Edge, navegue até o portal do Microsoft Purview, `https://purview.microsoft.com`, e faça logon.
1. Uma mensagem sobre o novo portal do Microsoft Purview aparecerá na tela. Escolha a opção para concordar com os termos de divulgação de fluxo de dados e a política de privacidade e clique em **Introdução**.

    >![Captura de tela mostrando a tela de Boas-vindas ao novo porta do Microsoft Purview.](./Media/welcome-purview-portal.png)

1. Selecione **Soluções** > **Gerenciamento do Ciclo de Vida dos Dados**.
1. No painel de navegação à esquerda, expanda **Políticas** e selecione **Políticas de retenção**.
1. Clique em **+ Nova política de retenção**.
1. Na página **Nomear política de retenção**, insira o Nome e a Descrição:

   - **Nome**: `Company wide`
   - **Descrição**: `All locations except for teams`

1. Selecione **Avançar**.
1. Na página **Escopo da política**, clique em **Avançar**.
1. Na página **Escolher o tipo de política de retenção para criar**, selecione **Estática** e clique em **Avançar**.
1. Na página **Escolher onde aplicar esta política**, habilite:

   - Caixas de correio do Exchange
   - Sites clássicos e de comunicação do SharePoint
   - Contas do OneDrive
   - Caixas de correio do Grupo do Microsoft 365 e sites

1. Selecione **Avançar**.
1. Na página **Decidir se deseja reter conteúdo, exclui ou ambos**; na seção **Reter itens por um período específico**, insira as seguintes informações:

   - **Reter itens por um período específico**: escolha **Personalizado** na lista suspensa
   - Altere o campo de anos para **3**
   - **Iniciar o período de retenção com base em**: quando os itens foram alterados pela última vez
   - **Ao final do período de retenção**: excluir itens automaticamente

1. Selecione **Avançar**.
1. Na página **Revisar e concluir**, clique em **Enviar**.
1. Depois que sua política for criada, selecione **Concluído**.

Você criou uma política de retenção em toda a empresa que retém itens por três anos a partir da data da última modificação.

## Tarefa 2 – Criar políticas de retenção baseadas em localização com filtro

Aqui, você criará políticas de retenção especificamente para canais e chats do Teams, incluindo filtros para usuários específicos.

1. Você ainda deve estar na tela **Políticas de retenção** no portal do Microsoft Purview.

   Se não estiver, no Microsoft Edge, navegue até o portal do Microsoft Purview, `https://purview.microsoft.com`, e faça logon. Depois que fizer login, selecione o cartão **Gerenciamento do ciclo de vida dos dados** > **Políticas** > **Políticas de retenção**.

1. Clique em **+ Nova política de retenção**.
1. Na página **Nomear política de retenção**, insira o Nome e a Descrição:

   - **Nome**: `Teams Retention`
   - **Descrição**: `Retention for Teams locations`

1. Selecione **Avançar**.
1. Na página **Escopo da política**, clique em **Avançar**.
1. Na página **Escolher o tipo de política de retenção para criar**, selecione **Estática** e clique em **Avançar**.
1. Na seção Escolher locais para aplicar a política, habilite:

   - Mensagens do canal do Teams
   - Chats do Teams e interações do Copilot

   Confirme se todas as outras opções estão desabilitadas.

1. No local **Chats do Teams e Interações do Copilot**, clique no link **Editar** em **Todos os usuários** e adicione dois usuários.

    >![Captura de tela mostrando a opção Adicionar usuários dos Chats do Teams e Interações do Copilot.](./Media/add-users-retention-policy.png)

1. Na página de submenu **Chats do Teams e interações do Copilot**, depois que os usuários forem adicionados, selecione **Concluído** e, em seguida, **Avançar**.
1. Na página **Decidir se deseja reter o conteúdo, excluir ou ambos**, insira:
   - **Reter itens por um período** específico: escolha **Personalizado** na lista suspensa.
   - Altere os anos para 3.
   - **Iniciar o período de retenção com base em**: quando os itens foram modificados pela última vez.

1. Selecione **Avançar**.
1. Na página **Revisar e concluir**, clique em **Enviar**.
1. Depois que sua política for criada, selecione **Concluído**.

Você criou uma política de retenção para locais do Teams com um período de retenção de três anos, aplicando um filtro para usuários específicos.

## Tarefa 3 – Criar uma política de retenção usando o PowerShell

Nesta tarefa, você usará o PowerShell para criar e gerenciar políticas de retenção.

1. Abra uma janela elevada do PowerShell.
1. Execute o seguinte cmdlet para instalar a versão mais recente do módulo PowerShell do Exchange Online:

    ```powershell
    Install-Module ExchangeOnlineManagement
    ```

1. Confirme a caixa de diálogo de segurança do provedor NuGet com **S** para Sim e pressione **Enter**. Esse processo pode levar algum tempo para ser concluído.
1. Confirme a caixa de diálogo Segurança do repositório não confiável com **S** para Sim e pressione **Enter**.  Esse processo pode levar algum tempo para ser concluído.
1. Insira o cmdlet a seguir para alterar sua política de execução e pressione **Enter**. O comando pressupõe que você tenha feito login como usuário com as permissões apropriadas.

    ```powershell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

1. Confirme a alteração da Política de execução com **S** para Sim e pressione **Enter**.
1. Feche a janela do PowerShell.
1. Abra uma janela normal do PowerShell, sem elevação, clicando no botão Windows com o botão direito do mouse e selecione **Windows PowerShell**.
1. Conecte-se ao Centro de Conformidade e Segurança no locatário com o seguinte cmdlet:

    ```powershell
    Connect-IPPSSession
    ```

1. Quando solicitado, entre como um usuário com as permissões apropriadas.
1. Execute o seguinte cmdlet para criar a primeira política de retenção para todos os locais, exceto equipes:

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
    ```

1. Execute o seguinte cmdlet para definir o período de retenção, usando dias como unidades com base na data de modificação:

    ```powershell
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
    ```

Você criou políticas de retenção no PowerShell com um período de retenção de três anos.

<!--- Commenting out until adaptive scope issue is resolved

## Task 4 – Create retention policy with adaptive scope

Here, you will create a retention policy with adaptive scope targeting specific departments like Legal and Retail.

1. In Microsoft Edge, navigate to the Microsoft Purview portal, `https://purview.microsoft.com`, and log in.
1. Select **Settings** from the left navigation bar.
1. Expand **Roles and scopes** then select **Adaptive scopes**.
1. On the **Adaptive scopes** page select **+ Create scope**.
1. On the **Name your adaptive policy scope page**, enter:

   - **Name**: `Legal Documents Retention`
   - **Description**: `Retention for legal related documents`

1. Select **Next**.
1. On the **Assign admin unit page**, select **Next**.
1. On the **What type of scope do you want to create?** page, select **Users** and then **Next**.
1. On the **Create the query to define users** page, under **User attributes**, select:

   - **Attribute**: Department
   - **Operator**: is equal to
   - **Value**: `Legal`

1. Add a second attribute by selecting the **+ Add attribute** button with values:

   - **Query operator**: Or
   - **Attribute**: Department
   - **Operator**: is equal to
   - **Value**: `Retail`

    >![Screenshot showing the query to define users values.](./Media/query-to-define-users.png)

1. Select **Next** and then **Submit** on the **Review and finish** page.
1. Once your scope has been created select **Done** to get back to the **Adaptive scopes** page.
1. Select **Solutions** > **Data Lifecycle Management**.
1. Expand **Policies** then select **Retention policies**.
1. On the **Retention policies** page select **+ New retention policy**.
1. On the **Name your retention policy page**, enter:

   - **Name**: `Legal Data Retention`
   - **Description**: `Retention of all documents within the legal and retail departments.`

1. Select **Next**.
1. On the **Policy Scope** page, select **Next**.
1. On the **Choose the type of retention policy to create** page, select **Adaptive** and then **Next**.
1. On the **Choose adaptive policy scopes and locations** page, select **+ Add scopes** and choose the **Legal Documents Retention** scope.
1. Under **Choose locations to apply the policy** enable:

   - Exchange mailboxes
   - OneDrive accounts

1. Select **Next**.
1. On the **Decide if you want to retain content, delete it, or both** page, enter:

   - **Retain items for a specific period**: 5 years
   - **Start the retention period based on**: When items were created
   - **At the end of the retention period**: Do nothing

1. Select **Next** and then **Submit** on the **Review and finish**.
1. Once your policy is created, select **Done**.

You have successfully applied an adaptive scope to a retention policy.

--->
