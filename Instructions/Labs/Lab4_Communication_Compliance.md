---
lab:
  task: Configure Communication Compliance
  exercise: Exercise 4 - Configure Communication Compliance
---
## Locatários do WWL – Termos de uso

Se você estiver recebendo um locatário como parte de uma entrega de treinamento com instrutor, observe que o locatário é disponibilizado com a finalidade de dar suporte aos laboratórios práticos no treinamento com instrutor.

Os locatários não devem ser compartilhados ou usados para fins fora dos laboratórios práticos. O locatário usado neste curso é um locatário de avaliação e não pode ser usado ou acessado após o fim da aula e não está qualificado para extensão.

Os locatários não podem ser convertidos em uma assinatura paga. Os locatários obtidos como parte deste curso permanecem a propriedade da Microsoft Corporation e reservamos o direito de obter acesso e a qualquer momento.

# Exercício 4: tarefas de qualificação

- **Política de modelo predefinido**: crie uma política de conformidade de comunicação usando um modelo predefinido.
- **Política de modelo personalizado**: crie uma política de conformidade de comunicação modificando um modelo predefinido.
- **Política de comunicação personalizada**: crie uma política de conformidade de comunicação exclusiva adaptada às necessidades organizacionais específicas.

## Tarefa 1 – Criar uma política de conformidade de comunicação a partir de um modelo

Nesta tarefa, você criará uma política usando um modelo predefinido para abordar rapidamente cenários comuns de conformidade.

1. No Microsoft Edge, navegue até o portal do Microsoft Purview, `https://purview.microsoft.com`, e faça logon.
1. Selecione **Exibir todas as soluções**.
1. Em **Risco e Conformidade**, selecione o cartão **Conformidade de Comunicação**.
1. Selecione **Políticas** no painel de navegação à esquerda.
1. Selecione **Criar política** e revise os modelos de política disponíveis:

   - **Interações do Copilot**: monitora todas as interações com o Copilot para Microsoft 365.
   - **Conteúdo impróprio**: detecta discurso de ódio, violência, conteúdo sexual e automutilação no Microsoft Teams.
   - **Texto impróprio**: sinaliza ameaças, discriminação e assédio no Exchange Online, Microsoft Teams e Viva Engage.
   - **Imagens impróprias**: identifica imagens de conteúdo adulto e picantes no Exchange Online e no Microsoft Teams.
   - **Informações confidenciais**: monitora informações confidenciais no Exchange Online, Microsoft Teams e Viva Engage com uma porcentagem de revisão mais baixa.
   - **Conformidade regulatória**: garante a conformidade com os regulamentos financeiros no Exchange Online, no Microsoft Teams e no Viva Engage.
   - **Conflito de interesses**: detecta possíveis conflitos de interesses internamente no Exchange Online, no Microsoft Teams e no Viva Engage.

1. Selecione o modelo da política em **Detectar texto inadequado**.
1. Na página do submenu **Detectar comunicações de texto impróprio** à direita, insira o usuário que revisará os alertas de conformidade de comunicação no campo **Revisores**.
1. Selecione **Criar política** na parte inferior da página do submenu e, em seguida, selecione **Fechar** na página **Sua política foi criada**.

Você criou uma política de conformidade de comunicação usando o modelo **Detectar texto impróprio**.

## Tarefa 2 – Criar uma política de conformidade de comunicação a partir de um modelo personalizado

Aqui, você modificará um modelo de política para adaptá-lo às necessidades organizacionais específicas.

1. Você ainda deve estar na página **Políticas** em **Conformidade de Comunicação** no portal do Microsoft Purview.

   Se não estiver, no Microsoft Edge, navegue até o portal do Microsoft Purview, `https://purview.microsoft.com`, e faça logon. Selecione o cartão **Exibir todas as soluções** > **Conformidade de Comunicação** em **Risco e Conformidade**.

1. Selecione **Criar política** > **Detectar imagens impróprias**.
1. Na página do submenu **Detectar comunicações de imagens impróprias** à direita, selecione **Personalizar política** na parte inferior da página do submenu.
1. Selecione **Personalizar política** na parte inferior da página do submenu.
1. Em **Nomear e descrever política**, selecione **Avançar**.
1. Na página **Escolher usuários e revisores**, insira o usuário que revisará os alertas de conformidade de comunicação no campo **Revisores** e selecione **Avançar**.
1. Na página **Escolher locais para detectar comunicações**, habilite os locais para o:

   - Exchange.
   - Equipes.
   - Viva Engage.

1. Selecione **Avançar**.
1. Em **Escolher condições e porcentagem de revisão**, revise as ações padrão para o modelo de imagens impróprias e selecione **Avançar**.
1. Na página **Revisar e concluir**, selecione **Criar política** e, em seguida, selecione **Concluído** na página **Sua política foi atualizada**.

Você personalizou uma política de conformidade de comunicação usando o modelo **Detectar imagens impróprias**.

## Tarefa 3 – Criar uma política de conformidade de comunicação personalizada

Nesta tarefa, você criará uma política de conformidade de comunicação do zero para atender a requisitos de conformidade exclusivos.

1. Você ainda deve estar na página **Políticas** em **Conformidade de Comunicação** no portal do Microsoft Purview.

   Se não estiver, no Microsoft Edge, navegue até o portal do Microsoft Purview, `https://purview.microsoft.com`, e faça logon. Selecione o cartão **Exibir todas as soluções** > **Conformidade de Comunicação** em **Risco e Conformidade**.

1. Selecione **Criar política** > **Política personalizada**.
1. Na página **Nomear e descrever política**, insira:

   - **Nome**: `Global Communication Compliance Policy`
   - **Descrição**: `Monitors emails and Teams messages for policy violations.`

1. Selecione **Avançar**.
1. Na página **Escolher usuários e revisores**:

   - Em **Escolher usuários e grupos**, selecione **Todos os usuários**.
   - Deixe o campo para **Usuários e grupos excluídos** em branco.
   - No campo **Revisores**, insira os revisores que monitorarão os alertas de conformidade.

1. Selecione **Avançar**.
1. Na opção **Escolher locais para detectar comunicações**, habilite apenas o:

   - Exchange
   - Teams

   Verifique se todos os outros locais não estão selecionados.

1. Selecione **Avançar**.
1. Na página **Escolher condições e porcentagem de revisão**, deixe os padrões selecionados para **Direção da comunicação**.
1. Em **Condições**, habilite a opção de usar o **Novo construtor de condições (versão prévia)**.
1. Clique em **+ Adicionar condição** > **O conteúdo corresponde aos classificadores treináveis**.
1. Em **O conteúdo corresponde aos classificadores treináveis**, selecione **Adicionar** > **Classificadores treináveis**.
1. Na página de submenu **Classificadores treináveis** à direita, selecione classificadores para **Conluio regulatório**, **Manipulação de estoque**, **Divulgação não autorizada** e **Sabotagem corporativa**.
1. Selecione **Adicionar** na parte inferior da página de submenu **Classificadores treináveis** à direita.
1. De volta à página **Escolher condições e porcentagem de revisão**, ajuste o controle deslizante **Porcentagem de revisão** para **25%**.
1. Selecione **Avançar** na parte inferior da página **Escolher condições e porcentagem de revisão**.
1. Na página **Revisar e concluir**, selecione **Criar política** e, em seguida, selecione **Concluído** na página **Sua política foi criada**.

Você criou uma política de conformidade de comunicação personalizada chamada _Política de Conformidade de Comunicação Global_.
