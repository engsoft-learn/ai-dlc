# Tech Talk | AI-DLC — AI-Driven Development Life Cycle

**Autor:** CI&T — Ricardo de Luna Galdino — Software Engineer — Jun/2026 </br>
**Source:** [github.com/engsoft-learn/ai-dlc](https://github.com/engsoft-learn/ai-dlc)

---

## Contexto Atual

A engenharia de software está passando por uma nova revolução com a chegada dos **Grandes Modelos de Linguagem (LLMs)**. Metodologias que funcionavam bem antes já não atendem da mesma forma às demandas atuais.

Hoje é possível usar linguagem natural para gerar código, detectar bugs e criar testes automaticamente. Mas a evolução vai além: a IA já começa a participar de etapas como elaboração de requisitos, planejamento, divisão de tarefas, design e colaboração em tempo real.

---

## O que é AI-DLC?

O AI-DLC *(AI-Driven Development Life Cycle)* é uma metodologia de desenvolvimento de software — assim como Scrum e Kanban —, mas construída desde o início para trabalhar com agentes de IA em todo o ciclo de vida do software: desde a intenção de negócio, passando pelo desenvolvimento, até a produção.

Criado em **2025**, mantido pela **AWS (Amazon Web Services)**, a metodologia está em **constante evolução**, acompanhando o avanço das capacidades dos modelos de IA.

O diferencial é que ele **mantém o humano no controle** em todos os momentos. A IA conduz e propõe; o humano valida, escolhe e confirma as decisões.

> O AI-DLC funciona como um fluxo de trabalho estruturado com fases e artefatos bem definidos, evitando os riscos do **"vibe-coding"** — desenvolver sem planejamento, apenas seguindo o fluxo — e trazendo disciplina de engenharia de software para o desenvolvimento assistido por IA.

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

O AI-DLC já traz, em seu núcleo, técnicas consolidadas de design de software:

| Técnica | Descrição |
|---|---|
| **DDD** — Domain-Driven Design | Para modelar a lógica de negócio |
| **TDD** — Test-Driven Development | Para garantir qualidade desde o início |
| **BDD** — Behavior-Driven Development | Para alinhar comportamento esperado com testes |

A IA aplica essas técnicas automaticamente durante o planejamento; o desenvolvedor valida e ajusta.

---

## Classificação de Projetos

### 🟢 Green-field

Desenvolvimento de sistemas **novos, do zero**.

### 🟡 Brown-field

Evolução de **sistemas já existentes**. O AI-DLC se destaca aqui ao fazer engenharia reversa do código existente, gerando documentações ricas com modelos estáticos e dinâmicos do sistema.

---

## Fluxo de Trabalho

### Fases e Rituais

---

### 01 · Inception Phase (Fase de Iniciação)

A Fase de Iniciação captura as Intenções e as transforma em Unidades para desenvolvimento.

#### Rito: Mob Elaboration

Uma sessão colaborativa de elaboração e decomposição de requisitos, realizada com todos na mesma sala, em frente a uma tela compartilhada, conduzida por um facilitador. A IA propõe uma divisão inicial; o time revisa e refina colaborativamente.

**Os resultados desta fase incluem:**

- Histórias de Usuário (User Stories)
- Definições de Requisitos Funcionais e Não-Funcionais
- Descrição de Riscos
- Critérios de Aceite
- Sugestão de Bolts para construção das Unidades

---

### 02 · Construction Phase (Fase de Construção)

A Fase de Construção é a execução iterativa das tarefas, transformando as Unidades definidas na Iniciação em código e testes automatizados prontos para produção.

#### Rito: Mob Construction

Assim como a Fase de Iniciação tem o Mob Elaboration, a Fase de Construção tem o Mob Construction. O AI-DLC recomenda que todos os desenvolvedores trabalhem no mesmo espaço físico, de forma colaborativa, em frente a uma tela compartilhada. A IA orienta e gera; o time revisa, valida e toma as decisões técnicas em conjunto.

Nessa etapa, a IA recomenda abordagens em cada tarefa — padrões de design, experiência do usuário, testes — e os desenvolvedores validam os resultados.

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

A Fase de Operações cobre a **implantação, observabilidade e manutenção** dos sistemas, usando a IA para ganhar eficiência operacional.

A IA analisa dados de telemetria — métricas, logs e rastreamentos — para detectar padrões, identificar anomalias e prever possíveis problemas, permitindo **resolução proativa** antes que afetem os usuários.

> ⚠️ Esta fase ainda está sendo desenvolvida pela AWS e ainda não possui artefatos de resultado definidos.

---

## Artefatos Gerados

Todos os artefatos são gerados dentro do diretório **`aidlc-docs/`** na raiz do projeto. O código da aplicação nunca fica aqui — apenas documentação em Markdown.

### Inception Phase

| Artefato | Arquivo gerado |
|---|---|
| Requisitos funcionais e não-funcionais | `inception/requirements/requirements.md` |
| Perguntas de esclarecimento (com respostas do time) | `inception/requirements/requirement-verification-questions.md` |
| User Stories com critérios de aceitação | `inception/user-stories/stories.md` |
| Definição das Unidades de trabalho | `inception/application-design/unit-of-work.md` |
| Mapeamento de User Stories por Unidade | `inception/application-design/unit-of-work-story-map.md` |

### Construction Phase

| Artefato | Arquivo gerado |
|---|---|
| Regras de negócio, validação e restrições | `construction/{unit}/functional-design/business-rules.md` |
| Modelos de domínio com entidades e relacionamentos | `construction/{unit}/functional-design/domain-entities.md` |
| Escolhas tecnológicas e justificativas | `construction/{unit}/nfr-requirements/tech-stack-decisions.md` |
| Requisitos de escalabilidade, performance e segurança | `construction/{unit}/nfr-requirements/nfr-requirements.md` |
| Componentes lógicos de infraestrutura (filas, caches, etc.) | `construction/{unit}/nfr-design/logical-components.md` |
| Definições arquiteturais | `construction/{unit}/nfr-design/nfr-design-patterns.md` |

### Engenharia Reversa — Brown-field

Quando o projeto é brown-field, a IA gera automaticamente a documentação do sistema existente antes de evoluí-lo:

| Artefato | Arquivo gerado |
|---|---|
| Visão geral de negócio e dicionário | `inception/reverse-engineering/business-overview.md` |
| Arquitetura do sistema e fluxo de dados | `inception/reverse-engineering/architecture.md` |
| Documentação de APIs | `inception/reverse-engineering/api-documentation.md` |
| Stack tecnológica identificada | `inception/reverse-engineering/technology-stack.md` |
| Qualidade de código e dívida técnica | `inception/reverse-engineering/code-quality-assessment.md` |

---

## Documentos de Input

Antes de iniciar o AI-DLC, é recomendado preparar dois documentos que alimentam a Inception Phase. Eles reduzem as perguntas de esclarecimento da IA e garantem que a decomposição em User Stories e Unidades parta do contexto real do projeto.

### Documento de Visão *(Vision Document)*

Descreve **o que construir e por quê**. Deve conter:

- Um parágrafo descrevendo o que está sendo construído e para quem
- Lista de funcionalidades em escopo
- Lista de funcionalidades explicitamente **fora** do escopo
- Perguntas abertas — incertezas já conhecidas da equipe

> As perguntas abertas são especialmente valiosas: elas alimentam a Análise de Requisitos como ambiguidades pré-declaradas, sendo resolvidas cedo em vez de surgirem como surpresas no meio do design.

### Documento de Ambiente Técnico *(Technical Environment Document)*

Descreve **as ferramentas e restrições que se aplicam ao projeto**. Deve conter:

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

---

> 📚 Para guias completos com modelos e exemplos práticos, acesse a documentação oficial:
> **[github.com/awslabs/aidlc-workflows/tree/main/docs](https://github.com/awslabs/aidlc-workflows/tree/main/docs)**

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

Copie `aws-aidlc-rules/core-workflow.md` para a raiz do seu projeto renomeando-o para **`CLAUDE.md`**. Copie a pasta `aws-aidlc-rule-details/` para dentro do projeto renomeando-a para **`.aidlc-rule-details/`**.

Estrutura esperada:

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

Crie a pasta `.github/` na raiz do projeto. Copie `aws-aidlc-rules/core-workflow.md` para dentro dela renomeando-o para **`copilot-instructions.md`**. Copie a pasta `aws-aidlc-rule-details/` para a raiz do projeto renomeando-a para **`.aidlc-rule-details/`**.

Estrutura esperada:

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

Copie `aws-aidlc-rules/core-workflow.md` para a raiz do seu projeto renomeando-o para **`AGENTS.md`**. Copie a pasta `aws-aidlc-rule-details/` para dentro do projeto renomeando-a para **`.aidlc-rule-details/`**.

Estrutura esperada:

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

Com os arquivos no lugar, abra o seu assistente e inicie com um dos comandos abaixo, dependendo do idioma que deseja usar na conversa com a IA:

| Idioma | Comando |
|---|---|
| 🇺🇸 Inglês | `Using AI-DLC, [describe your intent]` |
| 🇧🇷 Português (BR) | `Usando AI-DLC, [descreva sua intenção]` |

O fluxo de trabalho será ativado automaticamente.

---

## O AI-DLC Não é Engessado

O AI-DLC não obriga a passar por todas as fases ou etapas em toda execução. **O usuário tem o controle** sobre até onde quer ir em cada sessão.

É possível, por exemplo:

- Executar **apenas a Inception Phase** para criar as User Stories e Unidades, e interromper o workflow — retomando o desenvolvimento em outro momento
- Iniciar direto na **Construction Phase** a partir de histórias já criadas anteriormente
- Executar **um único Bolt** de uma Unidade específica, sem precisar concluir todos os outros

A IA propõe e avança conforme o que foi solicitado no Intent. Basta indicar claramente o escopo desejado:

> `"Usando AI-DLC, quero apenas criar as User Stories para [intenção]. Pare após a geração das histórias."`

Essa flexibilidade permite que times adaptem o ritmo do AI-DLC à sua realidade — seja uma sessão curta de planejamento, seja um ciclo completo de desenvolvimento.
