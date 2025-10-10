# 📝 Especificação de Caso de Uso

## 1. Introdução
O objetivo da especificação é definir as espeficiações de cada caso de uso do sistema para implementação.

## 2. Casos de uso

| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Realizar login |
| **Ator Principal**    | Gestor, Administrador, Colaborador, Psicólogo |
| **Pré-condições**     | Ator principal já cadastrado no sistema |
| **Fluxo Principal**   | 1. Ator principal insere login e senha <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso |
| **Fluxos Alternativos** | Senha incorreta → Sistema exibe mensagem de erro |
| **Pós-condições**     | 1. Ator principal autenticado no sistema <br> 2. Usuário visualiza a tela principal |
| **Regras de negócio** | Senha deve ter no mínimo 8 caracteres |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Acessar questionário |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | Colaborador já autenticado no sistema |
| **Fluxo Principal**   | 1. Sistema redireciona à página inicial <br> 2. Colaborador clica no botão “Acessar questionário” <br> 3. Sistema abre modal mostrando os campos para responder ao questionário |
| **Pós-condições**     | Colaborador visualiza questionário |
| **Regras de negócio** | O colaborador só pode acessar o questionário uma vez |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Preencher questionário |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | 1. Colaborador já autenticado no sistema <br> 2. Questionário aberto no sistema |
| **Fluxo Principal**   | 1. Colaborador visualiza questionário  <br> 2. Colaborador responde questões presentes no questionário <br> 3. Colaborador envia <br> 4. Sistema salva respostas |
| **Fluxos Alternativos** | Questão sem resposta → Sistema exibe mensagem de pergunta obrigatória |
| **Pós-condições**     | Questionário enviado |
| **Regras de negócio** | O questionário não pode ser enviado com respostas em branco |

| Item                  | Descrição |
|-----------------------|-----------|
| Nome | Enviar questionário |
| Ator Principal | Colaborador |
| Pré-condições | Questionário foi preenchido |
| Fluxo Principal | 1. Colaborador clica em “Enviar” <br> 2. Sistema valida dados e armazena respostas <br> 3. Sistema mostra confirmação de envio |
| Pós-condições | Questionário enviado e registrado no sistema |
| Regras de negócio | 1. Questionário só pode ser enviado uma vez por colaborador por ciclo. <br> 2. Após envio, questionário torna-se apenas leitura. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Publicar sugestão sobre dinâmica da empresa  |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | Colaborador já autenticado no sistema |
| **Fluxo Principal**   | 1. Colaborador acessa seção de sugestões <br> 2. Colaborador preenche campo de texto com suas sugestões <br> 3. Colaborador envia o texto de sugestão <br> 4. Sistema registra sugestão e exibe confirmação |
| **Fluxos Alternativos** | Campo vazio → Sistema não permite envio e expõe alerta com indicação do problema |
| **Pós-condições**     | Nova sugestões sobre dinâmica da empresa armazenada no sistema |
| **Regras de negócio** | Sugestão deve conter no mínimo 10 caracteres |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Publicar feedback sobre o sistema |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | Colaborador já autenticado no sistema |
| **Fluxo Principal**   | 1. Colaborador seleciona a opção ‘Enviar feedback’ <br> 2. Colaborador preenche o campo de texto com sua experiência <br> 3. Colaborador clica no botão “Enviar” <br> 4. Sistema armazena novo feedback e alerta Administrador | 
| **Fluxos Alternativos** | Campo vazio → Sistema não permite o envio e exibe alerta com a indicação do problema |
| **Pós-condições**     | Novo feedback armazenado no sistema e mensagem enviada ao Administrador |
| **Regras de negócio** | Feedback deve conter no mínimo 10 caracteres |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Reportar situações |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | Colaborador já autenticado no sistema |
| **Fluxo Principal**   | 1. Colaborador seleciona a opção ‘Reportar situação’ <br> 2. Colaborador preenche o campo de texto com situação <br> 3. Colaborador clica no botão “Enviar” <br> 4. Sistema armazena nova situação reportada e alerta Psicólogo e Gestor da Equipe | 
| **Fluxos Alternativos** | Campo vazio → Sistema não permite o envio e exibe alerta com a indicação do problema |
| **Pós-condições**     | Nova situação armazenada no sistema e mensagem enviada ao Psicólogo |
| **Regras de negócio** | Situação reportada deve conter no mínimo 10 caracteres; publicação anônima |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**  | Visualizar Questionário  | 
| **Ator Principal** | Gestor de Equipe, Psicólogo |
| **Pré-condições** | 1. Ator Principal já está autenticado no sistema |
| **Fluxo Principal** | 1. Ator Principal acessa a interface principal do sistema <br> 2. Sistema valida as informações e libera acesso ao usuário. <br> 3. O sistema apresenta a opção "Visualizar Questionário" <br> 4. O Ator Principal clica na opção proposta. <br> 5. O sistema exibe o questionário disponível para visualização. | 
| **Pós-condições** | Ator Principal visualizou os questionários disponíveis no sistema |

| Item                  | Descrição |
|-----------------------|-----------|
| **Nome** | Gerar relatório dos Questionários  | 
| **Ator Principal** | Gestor de Equipe, Psicólogo |
| **Pré-condições** | 1. Ator Principal já está autenticado no sistema. <br> 2. Questionários devem ter sido preenchidos anteriormente pelos usuários. |
| **Fluxo Principal** | 1. O sistema notifica o ator sobre a disponibilidade de novos dados para relatório. <br>  2. Ator Principal clica no botão ‘Gerar relatório’ <br> 3. O sistema processa os dados dos questionários preenchidos. <br> 4. O sistema apresenta o relatório consolidado (ex: últimos 3 meses).|
| **Fluxos Alternativos** | Se não houver dados suficientes, o sistema exibe uma mensagem de erro indicando que não é possível gerar o relatório. |
| **Pós-condições** | Um relatório consolidado dos questionários foi gerado e disponibilizado ao Ator Principal | 


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Visualizar situações reportadas |
| **Ator Principal**    | Psicólogo |
| **Pré-condições**     | Psicólogo já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Psicólogo se autentica no sistema administrativo <br> 2. Sistema direciona o usuário a página principal <br> 3. Psicólogo clica na aba situações reportadas <br> 4.Sistema direciona usuário para a tela de situações reportadas. |
| **Fluxos Alternativos** | Não é possível realizar a consulta → Sistema exibe mensagem de erro |.
| **Pós-condições** | Psicólogo consulta as situações reportadas |
| **Regras de negócio** | Apenas psicólogos podem visualizar relatos individuais |



| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Visualizar sugestões |
| **Ator Principal**    | Psicólogo, Gestor de equipe |
| **Pré-condições**     | Ator principal já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Ator principal se autentica no sistema administrativo <br> 2. Sistema direciona o usuário a página principal. <br>  3. Ator principal clica na aba sugestões publicadas <br> 4. Sistema redireciona usuário a tela de sugestões.|
| **Fluxos Alternativos** | Não é possível realizar a consulta → Sistema exibe mensagem de erro |
| **Pós-condições**  | Ator principal consulta as sugestões dos colaboradores |
| **Regras de negócio** | Sugestões são exibidas em ordem cronológica |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Criar o questionário |
| **Ator Principal**    | Psicólogo |
| **Pré-condições**     | Psicólogo já está autenticado no sistema e com autorização para criar questionários |
| **Fluxo Principal**   | 1. Psicólogo se autentica no sistema administrativo <br> 2. Sistema direciona o usuário a página principal. <br> 3. Psicólogo clica na aba Questionários <br> 4. Psicólogo direciona o usuário a página principal <br> 5. Psicólogo clica no botão “Criar questionário” <br> 6. Psicólogo escreve questões. <br> 7. Psicólogo clica no botão salvar o questionário. <br> 8. Sistema salva o questionário no sistema
| **Fluxos Alternativos** | Erro na criação do sistema → Sistema exibe mensagem de erro |
| **Pós-condições**     | Psicólogo visualiza questionário criado na aba Questionários |
| **Regras de negócio** | Questionário deve ter 5 questões |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Visualizar Feedback  |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa o menu “Feedbacks” no canto superior esquerdo <br> 5. Administrador clica no botão “Feedbacks”. <br> 6. Sistema abre interface de “Feedbacks”. <br> 7. Sistema exibe a lista de feedbacks enviados pelos colaboradores (identificados ou anônimos). <br> 8. Sistema apresenta tela com os seguintes elementos barra de busca , filtros (período e  tipo) , Listagem (Id , Nome/Anônimo , Data, Resumo, Status), botões de navegação (Anterior/ Próxima), opções (Ordenar, Selecionar, Múltiplos feedbacks) <br> 9. Administrador seleciona um feedback <br> 10. Sistema abre tela <br> 11. Administrador seleciona opção “ver detalhes” <br> 12. Sistema apresenta conteúdo completo <br> 13. Administrador visualiza informações <br> 14.  Sistema valida que foi visualizado <br> 15.  Administrador volta a pagina menu <br> 16. Sistema fecha pagina de feedbacks. |
| **Fluxos Alternativos** | F1. Caso não existam feedbacks na lista, o sistema exibe a mensagem “Nenhum feedback disponível no momento”. <br> F2. Caso ocorra falha na conexão, o sistema exibe a mensagem “Erro de conexão. Tente novamente mais tarde” |
| **Pós-condições**| O administrador tem acesso ao histórico de feedbacks dos colaboradores. |
| **Regras de negócio** | 1. Feedbacks anônimos não podem exibir informações que identifiquem o colaborador. <br> 2. O sistema deve permitir filtragem de feedbacks por período (ex: mensal ou semanal) <br> 3. Apenas usuários com perfil de Administrador podem acessar o módulo de feedbacks |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Cadastrar Colaboradores|
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administradorjá está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa  o menu “Gestão de Colaboradores” no canto superior esquerdo <br> 5. Sistema exibe a tela de colaboradores. <br> 6. Administrador clica em “Novo Cadastro”. <br> 7. Sistema exibe formulário de cadastro <br> 8. Administrador insere dados obrigatórios (Nome, E-mail, CPF, Cargo) <br> 9.  Administrador escolhe o Tipo de Colaborador: Administrador, Colaborador, Gestor ou Psicólogo <br> 10. Administrador confirma em “Salvar” <br> 11. Sistema valida os dados e registra o colaborador. |
| **Fluxos Alternativos** | 1. Dados inválidos → Sistema exibe mensagem de erro <br> 2. CPF já cadastrado → Sistema exibe mensagem de duplicidade. |
| **Pós-condições**     | O colaborador/administrador/gestor/psicólogo é incluído no sistema |
| **Regras de negócio** | 1. O campo “Tipo de Colaborador” deve ser obrigatório <br> 2.  Cada CPF deve ser único no sistema  |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Editar Colaborador |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | O administrador já está autenticado no sistema e o colaborador já deve ter sido cadastrado |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa  o menu “Gestão de Colaboradores” no canto superior esquerdo <br> 5. Sistema exibe a tela de colaboradores. <br> 6. Administrador seleciona um colaborador existente <br> 7. Administrador clica no botão “Editar” <br> 8. Sistema exibe formulário com dados preenchidos. <br> 9. Administrador altera as informações desejadas. <br> 10. Administrador clica em “Salvar Alterações”. <br> Sistema atualiza os dados do colaborador.  |
| **Fluxos Alternativos** | 1. Dados inválidos → Sistema exibe mensagem de erro |
| **Pós-condições**     | O colaborador tem seus dados atualizados no sistema |
| **Regras de negócio** | 1. Não é permitido alterar o CPF <br> 2. Alteração de tipo (Administrador, Colaborador, Gestor, Psicólogo) deve ser registrada em log de auditoria|


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Excluir Colaborador |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | O administrador já está autenticado no sistema e o colaborador já deve ter sido cadastrado |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa  o menu “Gestão de Colaboradores” no canto superior esquerdo <br> 5. Sistema exibe a tela de colaboradores. <br> 6. Administrador seleciona um colaborador existente <br> 7. Administrador clica no botão “Excluir” <br> 8. Sistema exibe mensagem de confirmação “Deseja realmente excluir ?” 9. Administrador confirma exclusão. <br> 6. Sistema remove o colaborador do banco de dados  | 
| **Fluxos Alternativos** | Administrador cancela a exclusão → Sistema mantém colaborador ativo |
| **Pós-condições**     | O colaborador é removido do sistema |
| **Regras de negócio** | Não é permitido excluir o último Administrador ativo no sistema |



| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Consultar Colaborador |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema e existir colaboradores cadastrados. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa  o menu “Gestão de Colaboradores” no canto superior esquerdo <br> 5 . Sistema exibe a tela de colaboradores. <br> 6. Administrador usa a barra de busca para pesquisar por nome, CPF, e-mail ou tipo de colaborador ou pode aplicar filtros (tipo : Administrador, Colaborador, Gestor ou Psicólogo) <br> 7. Sistema exibe os resultados da pesquisa/lista filtrada. <br> 8. Administrador seleciona um colaborador para visualizar informações detalhadas. <br> 9. Sistema apresenta uma tela/modal com os dados completos do colaborador (nome, e-mail, tipo, status, data de cadastro). |
| **Fluxos Alternativos** | 1. Nenhum colaborador encontrado → Sistema exibe mensagem “Nenhum resultado encontrado” <br> 2. Falha de conexão → Sistema exibe mensagem “Erro de conexão. Tente novamente mais tarde” |
| **Pós-condições**     | O administrador visualiza informações completas do colaborador selecionado. |
| **Regras de negócio** | 1.  A consulta deve permitir busca por múltiplos critérios (nome, CPF, e-mail, tipo) <br> 2. Somente administradores podem visualizar todos os dados do colaborador . |
