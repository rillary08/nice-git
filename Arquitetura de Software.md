## 1. Módulos principais

A aplicação pode ser quebrada em módulos:

1. Autenticação/Usuário
2. Colaboradores
3. Questionários e Respostas
4. Feedbacks
5. Situações Reportadas
6. Sugestões
7. Dashboard/Relatórios



Cada módulo tem: **Model(s)**, **Controller(s)** e **Views**.

---

## 2. Models (camada de dados/regra de negócio básica)

### 2.1. Autenticação / Usuário

* `Usuario`

  * id
  * nome
  * email
  * senhaHash
  * tipo (ADMIN, GESTOR, COLABORADOR, PSICOLOGO)
  * status (ATIVO, INATIVO, BLOQUEADO)
  * tentativasLogin
  * dataUltimoAcesso

### 2.2. Colaboradores

* `Colaborador`

  * id
  * nome
  * email
  * cpf
  * cargo
  * tipoColaborador (ADMIN, COLABORADOR, GESTOR, PSICOLOGO)
  * status
  * dataCadastro

### 2.3. Questionários

* `Questionario`

  * id
  * titulo
  * descricao
  * categoria
  * autorId (Psicólogo)
  * dataCriacao
  * status

* `Questao`

  * id
  * questionarioId
  * texto
  * tipoResposta (ESCALA_1_5, MULTIPLA_ESCOLHA, TEXTO_LIVRE)
  * obrigatoria (bool)

* `RespostaQuestionario`

  * id
  * questionarioId
  * colaboradorId
  * dataEnvio
  * ciclo (opcional)
  * status (ENVIADO)

* `RespostaQuestao`

  * id
  * respostaQuestionarioId
  * questaoId
  * valor

### 2.4. Feedbacks

* `Feedback`

  * id
  * titulo
  * descricao
  * categoria
  * tipoEnvio (ANONIMO, IDENTIFICADO)
  * remetenteId (pode ser null se anônimo)
  * destinatarioColaboradorId (ou equipe, se tiver)
  * dataEnvio

* `RespostaFeedback`

  * id
  * feedbackId
  * colaboradorId
  * textoResposta
  * dataResposta

### 2.5. Situações Reportadas

* `SituacaoReportada`

  * id
  * colaboradorId
  * titulo
  * descricao
  * categoria
  * dataOcorrido
  * status
  * psicologoId

### 2.6. Sugestões

* `Sugestao`

  * id
  * colaboradorId
  * texto
  * dataEnvio

### 2.7. Logs (opcional, mas útil)

* `LogAuditoria`

  * id
  * usuarioId
  * acao
  * entidade
  * entidadeId
  * dataHora
  * detalhes

---

## 3. Controllers (onde você encaixa os casos de uso)

Vou colocar só os principais métodos (ações) para bater com seus fluxos.

### 3.1. AuthController

* `exibirLogin()` → GET `/login`
* `login(email, senha)` → POST `/login`

  * Caso de uso: **Realizar Login**
* `logout()` → POST `/logout`

Regras aqui:

* contar tentativas
* bloquear após 3
* checar se usuário está ativo e dentro dos 90 dias

### 3.2. ColaboradorController

* `index(filtros)` → GET `/colaboradores`

  * Caso: **Consultar Colaborador**
* `show(id)` → GET `/colaboradores/{id}`
* `create()` → GET `/colaboradores/novo`
* `store(dados)` → POST `/colaboradores`

  * **Cadastrar Colaboradores**
* `edit(id)` → GET `/colaboradores/{id}/editar`
* `update(id, dados)` → POST/PUT `/colaboradores/{id}`

  * **Editar Colaborador**
* `destroy(id)` → POST/DELETE `/colaboradores/{id}`

  * **Excluir Colaborador**

Regra extra: validar CPF único, não excluir último ADMIN, tipo obrigatório.

### 3.3. QuestionarioController

* `index(filtros)` → GET `/questionarios`

  * **Consultar questionário**, **Visualizar Questionário**
* `show(id)` → GET `/questionarios/{id}`
* `create()` → GET `/questionarios/novo`
* `store(dados)` → POST `/questionarios`

  * **Cadastrar Questionário / Criar Questionário**
* `edit(id)` → GET `/questionarios/{id}/editar`
* `update(id, dados)` → POST/PUT `/questionarios/{id}`

  * **Editar questionário**
* `destroy(id)` → POST/DELETE `/questionarios/{id}`

  * **Excluir questionário**

Fluxo de resposta:

* `responderForm(id)` → GET `/questionarios/{id}/responder`

  * **Responder questionário / Preencher questionário**
* `enviarResposta(id, respostas)` → POST `/questionarios/{id}/respostas`

  * **Enviar questionário**

Regras:

* título único
* mínimo 5, máximo 20 questões
* só psicólogo cria
* colaborador só responde os que forem pra ele
* não salvar se tiver questão obrigatória sem resposta
* só enviar uma vez por ciclo
* depois de enviado, só leitura

### 3.4. FeedbackController

* `index(filtros)` → GET `/feedbacks`

  * **Consultar Feedback**
* `show(id)` → GET `/feedbacks/{id}`
* `create()` → GET `/feedbacks/novo`
* `store(dados)` → POST `/feedbacks`

  * pode cobrir:

    * **Criar Feedback**
    * **Enviar Feedback (admin → colaborador/equipe)**
* `edit(id)` → GET `/feedbacks/{id}/editar`
* `update(id, dados)` → POST/PUT `/feedbacks/{id}`

  * **Editar Feedback**
* `destroy(id)` → POST/DELETE `/feedbacks/{id}`

  * **Excluir Feedback**

Fluxo de resposta:

* `meus()` → GET `/meus-feedbacks`
* `responderForm(id)` → GET `/meus-feedbacks/{id}/responder`
* `responder(id, texto)` → POST `/meus-feedbacks/{id}/resposta`

  * **Responder Feedback**

Regras:

* admin envia feedback
* colaborador/gestor respondem
* feedback anônimo não mostra remetente
* feedback anônimo não pode ser editado
* log de auditoria nas edições e exclusões
* colaborador só vê feedback dele

### 3.5. SituacaoReportadaController

* `index(filtros)` → GET `/situacoes`

  * **Consultar Situação Reportada**, **Visualizar situações reportadas**
* `show(id)` → GET `/situacoes/{id}`
* `create()` → GET `/situacoes/nova`
* `store(dados)` → POST `/situacoes`

  * **Cadastrar Situação Reportada**
* `edit(id)` → GET `/situacoes/{id}/editar`
* `update(id, dados)` → POST/PUT `/situacoes/{id}`

  * **Editar Situação Reportada**
* `destroy(id)` → POST/DELETE `/situacoes/{id}`

  * **Excluir Situação Reportada**

Regras:

* só psicólogo acessa tudo
* não pode alterar colaborador vinculado
* data do ocorrido não pode ser futura
* se estiver vinculada a relatório/investigação, não exclui
* registrar log

### 3.6. SugestaoController

* `create()` → GET `/sugestoes/nova`
* `store(dados)` → POST `/sugestoes`

  * **Publicar sugestão sobre dinâmica da empresa**
* `index()` → GET `/sugestoes`

  * **Visualizar sugestões** (psicólogo/gestor)

Regra: mínimo 10 caracteres, ordem cronológica.

### 3.7. FeedbackSistemaController (se quiser separar)

* `create()` → GET `/feedback-sistema/nova`
* `store(dados)` → POST `/feedback-sistema`

  * **Publicar feedback sobre o sistema**

Regra: mínimo 10 caracteres.

### 3.8. DashboardController / RelatorioController

* `DashboardController.index()` → GET `/dashboard`

  * **Acessar dashboard**

* `RelatorioController.questionariosForm()` → GET `/relatorios/questionarios`

* `RelatorioController.gerarQuestionarios(filtros)` → POST `/relatorios/questionarios`

  * **Gerar relatório dos Questionários**

Se quiser deixar mais simples, pode fazer tudo em `DashboardController`.

---

## 4. Views (telas principais)

Resumo das telas mais importantes:

* `/login`
* `/painel/admin`, `/painel/gestor`, `/painel/colaborador`, `/painel/psicologo`
* `/colaboradores/lista`, `/novo`, `/editar`, `/detalhes`
* `/questionarios/lista`, `/novo`, `/editar`, `/detalhes`, `/responder`
* `/feedbacks/lista`, `/novo`, `/editar`, `/detalhes`
* `/meus-feedbacks/lista`, `/meus-feedbacks/{id}`, `/responder`
* `/situacoes/lista`, `/nova`, `/editar`, `/detalhes`
* `/sugestoes/lista`, `/nova`
* `/feedback-sistema/nova`
* `/dashboard`
* `/relatorios/questionarios`

---

Se você quiser, no próximo passo eu posso pegar um desses módulos (por exemplo, só “Questionários”) e desenhar a estrutura de pastas tipo:

* `models/Questionario.js`
* `controllers/QuestionarioController.js`
* `views/questionarios/*.php`

