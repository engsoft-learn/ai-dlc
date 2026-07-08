[← Voltar ao README](../../README.pt-br.md)

# Tech Talk | AI-DLC — AI-Driven Development Life Cycle

**Autor:** Ricardo de Luna Galdino — Software Engineer — Jun/2026 </br>
**Source:** [github.com/engsoft-learn/ai-dlc](https://github.com/engsoft-learn/ai-dlc)

---

## Contexto Atual

A engenharia de software está passando por uma nova revolução com a chegada dos **Grandes Modelos de Linguagem (LLMs)**. Metodologias que funcionavam bem antes já não atendem da mesma forma às demandas atuais.

Hoje é possível usar linguagem natural para gerar código, detectar bugs e criar testes automaticamente. Mas a evolução vai além: a IA já começa a participar de etapas como elaboração de requisitos, planejamento, divisão de tarefas, design e colaboração em tempo real.

> Os métodos atuais foram feitos para times humanos em ciclos longos. Precisamos de metodologias criadas **desde o início para trabalhar com IA**.

---

## O que é AI-DLC?

O AI-DLC *(AI-Driven Development Life Cycle)* é uma metodologia de desenvolvimento de software — assim como Scrum e Kanban —, mas construída desde o início para trabalhar com agentes de IA em todo o ciclo de vida do software: desde a intenção de negócio, passando pelo desenvolvimento, até a produção.

Criado em **2025**, mantido pela **AWS (Amazon Web Services)**, a metodologia está em **constante evolução**, acompanhando o avanço das capacidades dos modelos de IA.

O diferencial é que ele **mantém o humano no controle** em todos os momentos. A IA conduz e propõe; o humano valida, escolhe e confirma as decisões.

> O AI-DLC evita os riscos do **"vibe-coding"** — desenvolver sem planejamento, apenas seguindo o fluxo — e traz disciplina de engenharia de software para o desenvolvimento assistido por IA.

📄 White Paper: https://prod.d13rzhkk8cj2z0.amplifyapp.com/

---

## Princípios Fundamentais

Os métodos tradicionais como Scrum e Kanban foram criados para times humanos trabalhando em ciclos longos, de semanas ou meses. **Com o AI-DLC, esses ciclos passam a ser medidos em horas ou dias.**

A metodologia preserva os conceitos que já conhecemos em métodos ágeis (Scrum), mas atualiza a terminologia e os rituais onde necessário para refletir essa nova realidade:

> **Intent** → decompõe em → **Units** → agrupam → **Bolts** → contêm → **User Stories**

### Intent (Intenção)

Uma Intenção é uma declaração de alto nível sobre o que precisa ser alcançado. A IA a decompõe em uma ou mais **Unidades** de trabalho. Pode ser:

- um objetivo de negócio
- uma nova funcionalidade
- um resultado técnico (como melhoria de desempenho ou segurança)
- uma melhoria em sistema existente
- modernização de sistema existente
- correção de defeitos (bugs)

### Units (Unidades) — equivalente aos Épicos do Scrum

Uma Unidade é um bloco de trabalho **coeso e independente**, derivado de uma **Intenção**, criado para entregar valor mensurável. Cada Unidade **agrupa seus Bolts**, que por sua vez contêm as User Stories a serem executadas. As Unidades são **fracamente acopladas** entre si, o que permite que sejam desenvolvidas e implantadas de forma independente.

### Bolts — equivalente aos Sprints do Scrum

Bolts pertencem a uma **Unidade** e **contêm um conjunto definido de User Stories**. São análogos aos Sprints do Scrum, mas com duração medida em **horas ou dias**, não em semanas. Podem ser executados em paralelo ou em sequência com outros Bolts da mesma Unidade.

### User Stories

As User Stories estão dentro de um **Bolt** e alinham o entendimento de humanos e IA sobre o que precisa ser construído — funcionando como um **contrato claro** entre as partes.

---

## Técnicas de Design Integradas

O AI-DLC já traz, em seu núcleo, técnicas consolidadas de design de software. A IA as aplica **automaticamente** durante o planejamento; o desenvolvedor valida e ajusta.

| Técnica | Descrição |
|---|---|
| **DDD** — Domain-Driven Design | Para modelar a lógica de negócio de forma independente dos componentes de infraestrutura |
| **TDD** — Test-Driven Development | Para garantir qualidade desde o início do ciclo de desenvolvimento |
| **BDD** — Behavior-Driven Development | Para alinhar o comportamento esperado do sistema com cenários de teste compreensíveis por todos |

> Ao contrário de Scrum e Kanban, o AI-DLC **não deixa as técnicas de design como opcionais**. Elas são parte central do método, visando garantir a qualidade do software produzido.

---

## Classificação de Projetos

### 🟢 Green-field

**Desenvolvimento de sistemas novos, do zero.** A IA parte da Intenção e constrói toda a modelagem, arquitetura e código sem dependências com código existente.

### 🟡 Brown-field

**Evolução de sistemas já existentes.** O AI-DLC se destaca aqui ao fazer **engenharia reversa** do código existente, gerando documentações ricas com modelos estáticos e dinâmicos do sistema antes de evoluí-lo.

---

## Fluxo de Trabalho

### Fases e Rituais

O AI-DLC é organizado em três fases sequenciais, cada uma com seus rituais e artefatos.

> Em todo o processo: **a IA planeja, decompõe e gera — os humanos supervisionam e validam.**

---

### 01 · Inception Phase (Fase de Iniciação)

Captura as Intenções e as transforma em Unidades para desenvolvimento.

#### Rito: Mob Elaboration

Sessão colaborativa com todos na mesma sala, em frente a uma tela compartilhada, conduzida por um facilitador. A IA propõe uma divisão inicial; o time revisa e refina colaborativamente.

**Os resultados desta fase incluem:**

- Histórias de Usuário (User Stories)
- Requisitos Funcionais e Não-Funcionais
- Descrição de Riscos
- Critérios de Aceite
- Sugestão de Bolts para construção das Unidades

---

### 02 · Construction Phase (Fase de Construção)

Execução iterativa das tarefas — transforma as Unidades em código e testes prontos para produção.

#### Rito: Mob Construction

Mesmo formato colaborativo do Mob Elaboration. A IA orienta e gera; o time revisa, valida e toma as decisões técnicas em conjunto.

**Os resultados desta fase incluem:**

- Escolhas tecnológicas e suas justificativas
- Definições arquiteturais
- Regras de negócio, lógica de validação e restrições
- Modelos de domínio com entidades e relacionamentos
- Requisitos de escalabilidade, performance, disponibilidade e segurança
- Relacionamento entre componentes da arquitetura
- Componentes lógicos de infraestrutura (filas, caches, etc.)
- Criação de testes automatizados (funcionais, de segurança e de performance)

---

### 03 · Operations Phase (Fase de Operações)

Cobre **deploy, DevOps, observabilidade e manutenção** dos sistemas, usando a IA para ganhar eficiência operacional.

- **🚀 Deploy** — A IA empacota as Unidades em artefatos prontos para produção (containers, funções serverless, IaC). Os desenvolvedores aprovam e iniciam o rollout.
- **⚙️ DevOps** — Automação de implantação, infraestrutura como código e validação de prontidão para produção. A IA gera e executa os pipelines sob supervisão humana.
- **📊 Observabilidade** — A IA analisa **métricas, logs e rastreamentos** para detectar anomalias e propor ações corretivas — executadas somente após aprovação humana.

> ⚠️ Esta fase ainda está sendo desenvolvida pela AWS e ainda não possui artefatos de resultado definidos.

---

## Fluxo de Planejamento e Validação

### 1. Plano de Nível 1 — antes de tudo

Ao receber o Intent, a IA gera um **Plano de Nível 1**: uma visão geral das etapas que serão executadas. O time revisa, ajusta e aprova antes de qualquer artefato ser gerado. Nenhum trabalho começa sem essa aprovação.

### 2. Dentro de cada etapa — o ciclo se repete

- **IA propõe um plano detalhado** com checkboxes para cada sub-passo — nenhum artefato é gerado até o humano aprovar.
- **IA escreve as dúvidas em arquivo** `requirement-verification-questions.md` — nunca no chat. O time preenche as respostas e avisa a IA para reler.
- **IA executa passo a passo**, marcando os checkboxes conforme conclui cada sub-passo do plano aprovado.
- **Gate de aprovação:** ao final de cada etapa a IA para. O time escolhe *Solicitar Alterações* ou *Aprovar e Continuar*.

> **IA planeja → humano valida → IA executa → humano aprova → próxima etapa**
>
> Cada gate captura erros antes que se propaguem — um erro na modelagem custa muito menos do que no código.

---

## Estrutura de Pastas no Projeto

Ao configurar o AI-DLC, duas pastas principais passam a existir na raiz do seu projeto. É importante entender o papel de cada uma para não mexer onde não deve — e saber onde encontrar tudo que a IA produz.

### 📁 `.aidlc-rule-details/` — Regras — o "motor" do AI-DLC

Esta pasta contém as **instruções que a IA segue** para conduzir todo o fluxo de trabalho. Pense nela como o **manual de operações** que o assistente lê para saber o que fazer em cada fase.

> ⚠️ **Esses arquivos não devem ser editados manualmente.** Eles são mantidos pela AWS e atualizados a cada nova release do AI-DLC. Alterar esses arquivos pode fazer a IA se comportar de forma inesperada ou pular etapas importantes do fluxo.

### 📁 `aidlc-docs/` — onde tudo é gerado

Esta é a pasta onde ficam **todos os artefatos e documentos produzidos** durante o uso do AI-DLC — desde requisitos e User Stories até modelos de domínio e definições arquiteturais.

O código da aplicação **nunca** fica aqui — apenas documentação em Markdown, organizada por fase e por Unidade de trabalho.

> **A pasta de regras ensina a IA o que fazer · A pasta `aidlc-docs/` guarda o que a IA produziu.** Você nunca precisa mexer na primeira, e encontra todo o resultado do trabalho na segunda.

---

## Artefatos Gerados

Todos os artefatos são gerados dentro do diretório **`aidlc-docs/`** na raiz do projeto.

### Inception Phase

Artefatos em `aidlc-docs/inception/`.

| Artefato | Arquivo gerado |
|---|---|
| Requisitos funcionais e não-funcionais | `requirements/requirements.md` |
| Perguntas de esclarecimento com tags `[Answer]:` para o time responder | `requirements/requirement-verification-questions.md` |
| User Stories no padrão INVEST com critérios de aceitação | `user-stories/stories.md` |
| Definição de cada Unidade: nome, responsabilidade, escopo e dependências | `application-design/unit-of-work.md` |
| Mapeamento de User Stories por Unidade, agrupadas em Bolts | `application-design/unit-of-work-story-map.md` |

### Construction Phase

Artefatos em `aidlc-docs/construction/`.

| Artefato | Arquivo gerado |
|---|---|
| Regras de negócio, validação e restrições | `{unit}/functional-design/business-rules.md` |
| Modelos de domínio com entidades, atributos e relacionamentos | `{unit}/functional-design/domain-entities.md` |
| Escolhas tecnológicas com justificativas | `{unit}/nfr-requirements/tech-stack-decisions.md` |
| Requisitos de escalabilidade, performance e segurança | `{unit}/nfr-requirements/nfr-requirements.md` |
| Definições arquiteturais: padrões de resiliência, escalabilidade e segurança | `{unit}/nfr-design/nfr-design-patterns.md` |

### Engenharia Reversa — Brown-field

Quando o projeto é brown-field, a IA gera automaticamente a documentação do sistema existente antes de evoluí-lo:

| Artefato | Arquivo gerado |
|---|---|
| Visão geral de negócio e dicionário | `inception/reverse-engineering/business-overview.md` |
| Arquitetura do sistema, fluxo de dados e relacionamento entre componentes | `inception/reverse-engineering/architecture.md` |
| Documentação de APIs | `inception/reverse-engineering/api-documentation.md` |
| Stack tecnológica identificada | `inception/reverse-engineering/technology-stack.md` |
| Cobertura de testes, indicadores de qualidade e dívida técnica | `inception/reverse-engineering/code-quality-assessment.md` |

---

## Documentos de Input

Antes de iniciar o AI-DLC, é recomendado preparar dois documentos que alimentam a Inception Phase. Eles reduzem as perguntas de esclarecimento da IA e garantem que a decomposição em User Stories e Unidades parta do contexto real do projeto.

### 📄 Documento de Visão *(Vision Document)*

**O que construir e por quê.** Deve conter:

- Descrição do que está sendo construído e para quem
- Funcionalidades em escopo
- Funcionalidades explicitamente **fora** do escopo
- Perguntas abertas — incertezas já conhecidas da equipe

> As perguntas abertas são especialmente valiosas: elas alimentam a Análise de Requisitos como ambiguidades pré-declaradas, sendo resolvidas cedo em vez de surgirem como surpresas no meio do design.

### ⚙️ Documento de Ambiente Técnico *(Technical Environment Document)*

**Ferramentas e restrições do projeto.** Deve conter:

- Linguagem de programação e versão
- Gerenciador de pacotes e framework web
- Provedor cloud e modelo de deploy
- Framework de testes
- Tabela de bibliotecas proibidas (com motivo e alternativa recomendada)
- Requisitos básicos de segurança
- Exemplos de código de um endpoint típico, função e teste

> A tabela de bibliotecas proibidas importa mais do que uma lista simples — as colunas de motivo e alternativa dizem ao AI-DLC *por que* uma biblioteca é proibida, levando a melhores decisões de substituição.

### Como usar com o AI-DLC

Ao iniciar o AI-DLC, indique no Intent que os documentos serão utilizados como base. Exemplo:

> `"Usando AI-DLC, quero construir [intenção]. Utilize o Vision Document em [caminho] e o Technical Environment Document em [caminho] como base."`

A IA carregará os dois documentos antes de iniciar a Inception Phase, reduzindo as perguntas de esclarecimento e partindo do contexto real do projeto.

📚 Guias e modelos: **[github.com/awslabs/aidlc-workflows/tree/main/docs](https://github.com/awslabs/aidlc-workflows/tree/main/docs)**

---

## O AI-DLC Não é Engessado

O AI-DLC não obriga a passar por todas as fases ou etapas em toda execução. **O usuário tem o controle** sobre até onde quer ir em cada sessão.

É possível, por exemplo:

- **Somente Planejamento** — Executar apenas a Inception Phase para criar as User Stories e Unidades, e interromper o workflow — retomando o desenvolvimento em outro momento, com o contexto já documentado
- **Desenvolvimento Direto** — Iniciar direto na Construction Phase a partir de histórias já criadas anteriormente, sem precisar repetir a Iniciação
- **Execução Parcial** — Executar um único Bolt de uma Unidade específica, sem precisar concluir todos os outros

Basta indicar o escopo desejado diretamente no Intent:

> `"Usando AI-DLC, quero apenas criar as User Stories para [intenção]. Pare após a geração das histórias."`

Essa flexibilidade permite que times adaptem o ritmo do AI-DLC à sua realidade — seja uma sessão curta de planejamento, seja um ciclo completo de desenvolvimento.

---

## Como Usar o AI-DLC

### 1. Baixe a release oficial

Acesse a página de releases e baixe o arquivo zip da versão mais recente:

**[https://github.com/awslabs/aidlc-workflows/releases/latest](https://github.com/awslabs/aidlc-workflows/releases/latest)**

Após descompactar o zip, você terá a seguinte estrutura:

```
aidlc-rules/
├── aws-aidlc-rules/
│   └── core-workflow.md      ← este arquivo deve ser renomeado (veja o passo 2)
└── aws-aidlc-rule-details/   ← esta pasta deve ser renomeada para .aidlc-rule-details/
    ├── common/
    ├── inception/
    ├── construction/
    ├── extensions/
    └── operations/
```

### 2. Configure o seu assistente de codificação

O arquivo `aws-aidlc-rules/core-workflow.md` contém as regras do AI-DLC. Ele deve ser **copiado e renomeado** conforme o assistente que você usa. A pasta `aws-aidlc-rule-details/` deve ser copiada para dentro do seu projeto com o nome `.aidlc-rule-details/`.

Escolha o seu assistente:

---

#### Claude Code

Renomeie `core-workflow.md` para **`CLAUDE.md`** na raiz do projeto.

```
<meu-projeto>/
├── CLAUDE.md                  ← core-workflow.md renomeado
└── .aidlc-rule-details/       ← aws-aidlc-rule-details/ renomeada
    ├── common/
    ├── inception/
    ├── construction/
    ├── extensions/
    └── operations/
```

---

#### GitHub Copilot

Renomeie para **`copilot-instructions.md`** e coloque em `.github/`.

```
<meu-projeto>/
├── .github/
│   └── copilot-instructions.md   ← core-workflow.md renomeado
└── .aidlc-rule-details/          ← aws-aidlc-rule-details/ renomeada
    ├── common/
    ├── inception/
    ├── construction/
    ├── extensions/
    └── operations/
```

---

#### OpenAI Codex

Renomeie `core-workflow.md` para **`AGENTS.md`** na raiz do projeto.

```
<meu-projeto>/
├── AGENTS.md                  ← core-workflow.md renomeado
└── .aidlc-rule-details/       ← aws-aidlc-rule-details/ renomeada
    ├── common/
    ├── inception/
    ├── construction/
    ├── extensions/
    └── operations/
```

---

### 3. Inicie o desenvolvimento

Com os arquivos no lugar, abra o seu assistente e inicie com um dos comandos abaixo:

| Idioma | Comando |
|---|---|
| 🇺🇸 Inglês | `Using AI-DLC, [describe your intent]` |
| 🇧🇷 Português (BR) | `Usando AI-DLC, [descreva sua intenção]` |

O fluxo de trabalho será ativado automaticamente.

---

## Encerramento

Uma nova forma de desenvolver software — onde a IA lidera e o humano decide.

| | |
|---|---|
| 📄 White Paper | [prod.d13rzhkk8cj2z0.amplifyapp.com](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) |
| ⚙️ Setup & Docs | [github.com/awslabs/aidlc-workflows](https://github.com/awslabs/aidlc-workflows) |
| 📚 Docs pt-br | [github.com/engsoft-learn/ai-dlc](https://github.com/engsoft-learn/ai-dlc) |

---

*Ricardo de Luna Galdino — Software Engineer — Jun/2026*
