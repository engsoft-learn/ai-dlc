# Guia do Documento de Visão


**Author:** Raja SP, AWS Labs <br>
**Source:** https://github.com/awslabs/aidlc-workflows <br>
**Adaptation:** Ricardo de Luna Galdino, EngSoft Learn<br>
**Download:** [vision-document-guide.pt-br.pdf](../pdf/writing-inputs/vision-document-guide.pt-br.pdf)

## Propósito

Um Documento de Visão define os **objetivos de negócio**, os **resultados esperados** e os **limites de escopo** de um projeto antes de entrar no workflow do AI-DLC. Ele serve como input primário para a Fase Inception, dando ao modelo de IA e à equipe uma compreensão compartilhada do que o projeto pretende alcançar e por quê é importante.

Um Documento de Visão bem escrito reduz a ambiguidade durante a Análise de Requisitos, melhora a qualidade das User Stories e evita o aumento de escopo durante a Construction.

## Quando Escrever um Documento de Visão

- Antes de iniciar qualquer novo projeto ou iniciativa importante
- Ao propor um novo produto, conjunto de funcionalidades ou plataforma
- Ao mudar de direção um produto existente
- Quando múltiplos stakeholders precisam de alinhamento sobre objetivos antes do início do desenvolvimento

## Estrutura do Documento

### 1. Resumo Executivo

Um breve parágrafo (3-5 frases) que captura a essência do projeto. Qualquer pessoa que leia apenas esta seção deve entender o que é o projeto, a quem serve e por que existe.

**Modelo:**

```markdown
## Resumo Executivo

[Nome do Projeto] é um(a) [tipo de sistema/produto] que permite [usuários-alvo] a [capacidade central].
Ele aborda [problema ou oportunidade de negócio] por meio de [abordagem ou diferenciação].
O resultado esperado é [resultado de negócio mensurável].
```

**Exemplo:**

```markdown
## Resumo Executivo

O OrderFlow é uma plataforma de gestão de pedidos baseada na web que permite a varejistas de médio
porte rastrear estoque, processar pedidos de clientes e gerenciar relacionamentos com fornecedores
em uma única interface. Ele aborda o problema de ferramentas fragmentadas que causam atrasos no
atendimento e divergências de estoque. O resultado esperado é uma redução de 30% no tempo de
processamento de pedidos e a eliminação da reconciliação manual de estoque.
```

---

### 2. Contexto de Negócio

Descreva o ambiente de negócio, o problema sendo resolvido e por que resolvê-lo importa agora.

**Seções a incluir:**

```markdown
## Contexto de Negócio

### Problema
[Qual problema de negócio específico ou ponto de dor este projeto aborda?
Seja concreto. Evite afirmações vagas como "melhorar a eficiência."]

### Motivadores de Negócio
[Por que este projeto está sendo feito agora? Que condições de mercado, pressões
competitivas, mudanças regulatórias ou necessidades internas o tornam oportuno?]

### Usuários-Alvo e Stakeholders
[Quem vai usar o sistema? Quem tem interesse no seu sucesso?
Liste os tipos de usuário com uma breve descrição de cada um.]

| Tipo de Usuário | Descrição | Necessidade Principal |
|-----------------|-----------|----------------------|
| [Perfil]        | [Quem é]  | [O que precisa do sistema] |

### Restrições de Negócio
[Limites de orçamento, requisitos regulatórios, políticas organizacionais, pressões
de prazo ou outros limites não negociáveis.]

### Métricas de Sucesso
[Como o negócio medirá se este projeto teve sucesso?
Use critérios específicos e mensuráveis.]

| Métrica | Estado Atual | Estado Alvo | Método de Medição |
|---------|-------------|-------------|-------------------|
| [Nome da métrica] | [Baseline] | [Meta] | [Como medir] |
```

---

### 3. Visão do Escopo Completo

Esta seção descreve a **visão de longo prazo completa** para o produto ou sistema. É deliberadamente aspiracional e cobre tudo o que o projeto poderia se tornar, não apenas o que será construído primeiro.

**Seções a incluir:**

```markdown
## Visão do Escopo Completo

### Declaração da Visão do Produto
[Uma única frase ou parágrafo curto que captura o estado aspiracional de longo prazo
do produto. Como será o mundo quando este produto estiver totalmente realizado?]

### Áreas de Funcionalidades
[Organize o conjunto completo de funcionalidades em grupos lógicos. Para cada área,
descreva o que o sistema fará na maturidade total.]

#### Área de Funcionalidade 1: [Nome]
- **Descrição**: [O que esta área abrange]
- **Capacidades Principais**:
  - [Capacidade 1]
  - [Capacidade 2]
  - [Capacidade 3]
- **Valor para o Usuário**: [Por que isso importa para os usuários]

#### Área de Funcionalidade 2: [Nome]
[Mesma estrutura]

### Pontos de Integração
[Com quais sistemas externos, APIs ou fontes de dados o sistema completo se integrará
na maturidade?]

- [Sistema/Serviço] - [Propósito da integração]

### Jornadas do Usuário (Visão Completa)
[Descreva 2-3 jornadas de usuário end-to-end que representam a experiência completa
do produto. Estas devem refletir o escopo completo, não o MVP.]

#### Jornada 1: [Nome]
1. [Passo]
2. [Passo]
3. [Passo]
**Resultado**: [O que o usuário alcança]

### Escalabilidade e Crescimento
[Como o produto deve crescer? Novos mercados, tipos de usuário, geografias,
volumes de dados ou categorias de funcionalidades?]

### Roadmap de Longo Prazo (Opcional)
[Se conhecido, esboce as fases ou marcos de alto nível além do MVP.
Isto é direcional, não definitivo.]

| Fase | Foco | Prazo (se conhecido) |
|------|------|--------------------|
| MVP | [Escopo central] | [Alvo] |
| Fase 2 | [Área de expansão] | [Alvo] |
| Fase 3 | [Expansão adicional] | [Alvo] |
```

---

### 4. Escopo do MVP

Esta seção define o **produto mínimo viável**: o menor conjunto de funcionalidades que entrega valor mensurável e valida a hipótese central de negócio. Tudo listado aqui deve ser construído antes que o produto possa ser lançado ou avaliado.

**Seções a incluir:**

```markdown
## Escopo do MVP

### Objetivo do MVP
[Qual é a coisa mais importante que o MVP deve provar ou entregar?
Mantenha em 1-2 frases.]

### Critérios de Sucesso do MVP
[Como você saberá que o MVP teve sucesso? Estes devem ser testáveis e específicos.]

- [ ] [Critério 1]
- [ ] [Critério 2]
- [ ] [Critério 3]

### Funcionalidades No Escopo (MVP)
[Liste cada funcionalidade que está incluída no MVP. Seja explícito. Se não
estiver listado aqui, não está no MVP.]

| Funcionalidade | Descrição | Prioridade | Justificativa para Inclusão |
|----------------|-----------|------------|----------------------------|
| [Nome da funcionalidade] | [Breve descrição] | Must Have | [Por que não pode ser adiada] |

### Funcionalidades Explicitamente Fora do Escopo (MVP)
[Liste as funcionalidades da Visão do Escopo Completo que são deliberadamente excluídas
do MVP. Declare por que cada uma é adiada. Isso evita o aumento de escopo.]

| Funcionalidade | Motivo do Adiamento | Fase Alvo |
|----------------|--------------------|-----------| 
| [Nome da funcionalidade] | [Por que pode esperar] | [Fase 2/3/A definir] |

### Jornadas do Usuário do MVP
[Descreva as jornadas de usuário que o MVP deve suportar. Estas são subconjuntos
ou versões simplificadas das jornadas da Visão Completa.]

#### Jornada 1: [Nome]
1. [Passo]
2. [Passo]
3. [Passo]
**Resultado**: [O que o usuário alcança]
**Limitação vs Visão Completa**: [O que é simplificado ou falta em comparação com o escopo completo]

### Restrições e Premissas do MVP
[Quais premissas o MVP é construído? Quais limitações conhecidas são aceitas?]

- **Premissa**: [Afirmação] - **Risco se errada**: [Consequência]
- **Limitação Aceita**: [O que é intencionalmente limitado e por quê]

### Definição de Pronto do MVP
[O que deve ser verdadeiro para que o MVP seja considerado completo e pronto para
avaliação ou lançamento?]

- [ ] Todas as funcionalidades "Must Have" implementadas e testadas
- [ ] [Critérios adicionais específicos deste projeto]
- [ ] [Requisito de deploy ou acessibilidade]
- [ ] [Requisito de aprovação de stakeholder]
```

---

### 5. Riscos e Dependências

```markdown
## Riscos e Dependências

### Riscos Principais
| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|-----------|
| [Descrição do risco] | Alta/Média/Baixa | Alto/Médio/Baixo | [Estratégia de mitigação] |

### Dependências Externas
[Liste tudo fora do controle da equipe do qual o projeto depende.]

- [Dependência] - [Responsável] - [Status]

### Perguntas Abertas
[Liste perguntas não resolvidas que precisam de respostas antes ou durante o desenvolvimento.
Estas alimentam diretamente as perguntas de esclarecimento da Análise de Requisitos.]

- [ ] [Pergunta]
- [ ] [Pergunta]
```

---

## Diretrizes de Escrita

### Faça

- Seja específico e mensurável. "Reduzir o tempo de processamento de pedidos em 30%" é melhor do que "tornar as coisas mais rápidas."
- Separe claramente a visão completa do MVP. Misturá-los causa aumento de escopo.
- Inclua listas de "fora do escopo". Elas são tão valiosas quanto as listas de "dentro do escopo".
- Escreva para a equipe, não para executivos. Evite linguagem de marketing.
- Declare suposições explicitamente para que possam ser questionadas.
- Inclua critérios de sucesso que possam realmente ser testados.

### Não Faça

- Use linguagem vaga: "de classe mundial," "sem fricção," "intuitivo," "o melhor do mercado."
- Liste tecnologias ou detalhes de implementação. Isso pertence ao Documento de Ambiente Técnico.
- Ignore a seção do MVP. Todo projeto precisa de um limite inicial definido.
- Combine funcionalidades e jornadas de usuário. Funcionalidades descrevem o que o sistema faz; jornadas descrevem como os usuários o experimentam.
- Assuma que os leitores conhecem o contexto de negócio. Escreva o Problema mesmo que pareça óbvio.

---

## Como Este Documento Se Alimenta no AI-DLC

| Seção do Documento de Visão           | Etapa do AI-DLC                       | Como é Usado                                            |
| ------------------------------------- | ------------------------------------- | ------------------------------------------------------- |
| Resumo Executivo                      | Detecção do Workspace                 | Contexto inicial para classificação do projeto          |
| Contexto de Negócio                   | Análise de Requisitos                 | Orienta perguntas de esclarecimento e profundidade dos requisitos |
| Visão do Escopo Completo              | User Stories, Design da Aplicação     | Informa a criação de personas, identificação de componentes |
| Escopo do MVP                         | Planejamento do Workflow              | Determina quais etapas executar, limites de escopo      |
| Funcionalidades Dentro/Fora do Escopo | Geração de Código                     | Define o que é construído nesta iteração                |
| Riscos e Dependências                 | Todas as etapas                       | Informa a avaliação de riscos e o tratamento de erros   |
| Perguntas Abertas                     | Análise de Requisitos                 | Tornam-se perguntas de esclarecimento nos arquivos de perguntas |
