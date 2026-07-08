[← Voltar ao README](../../README.pt-br.md)

# Documento de Visão: CalcEngine API de Calculadora Científica


**Author:** Raja SP, AWS Labs <br>
**Source:** https://github.com/awslabs/aidlc-workflows <br>
**Adaptation:** Ricardo de Luna Galdino, EngSoft Learn<br>
**Download:** [example-vision-scientific-calculator-api.pt-br.pdf](../pdf/writing-inputs/example-vision-scientific-calculator-api.pt-br.pdf)

## Sumário Executivo

CalcEngine é uma biblioteca de calculadora científica hospedada entregue como uma API REST que permite que equipes de desenvolvimento de software integrem computação matemática precisa e em conformidade com padrões em suas próprias aplicações, sem precisar construir ou manter a lógica de cálculo por conta própria. O produto resolve o problema recorrente de equipes de engenharia que gastam meses implementando, testando e depurando funções matemáticas periféricas ao seu produto principal. O resultado esperado é um serviço de API por assinatura gerando $2M ARR em 24 meses, ao capturar desenvolvedores que atuam em tecnologia educacional, modelagem financeira, simulação de engenharia e análise de dados.

---

## Contexto de Negócio

### Declaração do Problema

Equipes de software que constroem produtos nas áreas de educação, finanças, engenharia e ciência precisam regularmente de computação matemática além da aritmética básica. Elas enfrentam uma escolha: usar uma biblioteca local (frequentemente específica de linguagem, inconsistente entre plataformas e um fardo de manutenção) ou construir as funções matemáticas elas mesmas (caro, sujeito a erros e lento).

Os problemas específicos são:

- **Risco de precisão**: Equipes sem expertise em matemática introduzem erros sutis de ponto flutuante, tratamento incorreto de casos extremos (divisão por zero, overflow, erros de domínio) e comportamento de arredondamento inconsistente que corrói a confiança em seus produtos.
- **Esforço duplicado**: Cada equipe que precisa de funções trigonométricas, distribuições estatísticas, operações matriciais ou conversões de unidades as constrói de forma independente. Esse trabalho é repetido em milhares de empresas.
- **Inconsistência entre plataformas**: Um cálculo realizado em um backend Python pode produzir um resultado diferente do mesmo cálculo em um frontend JavaScript. Clientes que operam em múltiplas plataformas não conseguem garantir consistência.
- **Conformidade e auditabilidade**: Em setores regulados (finanças, saúde, engenharia), os cálculos devem ser rastreáveis, versionados e validados. Implementações ad-hoc raramente atendem aos requisitos de auditoria.

### Fatores de Negócio

- **Economia API-first**: Desenvolvedores preferem cada vez mais consumir APIs hospedadas em vez de incorporar bibliotecas. Stripe (pagamentos), Twilio (comunicações) e SendGrid (e-mail) já provaram o modelo. Nenhum equivalente existe para computação matemática.
- **Crescimento do EdTech**: O mercado global de tecnologia educacional está se expandindo rapidamente, e a funcionalidade de calculadora é um requisito universal em cursos de matemática, ciências e engenharia.
- **Pressão regulatória**: Empresas de serviços financeiros enfrentam escrutínio crescente sobre a precisão dos cálculos. Uma API certificada e auditável reduz sua carga de conformidade.
- **Pré-processamento de IA/ML**: Equipes de ciência de dados precisam de transformações matemáticas confiáveis como etapas de pré-processamento. Uma API que garante precisão e reprodutibilidade tem valor claro em pipelines de ML.

### Usuários-Alvo e Partes Interessadas

| Tipo de Usuário                        | Descrição                                                          | Necessidade Principal                                                                      |
| -------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| Desenvolvedor de Aplicações            | Engenheiro backend ou frontend integrando matemática em um produto | API confiável e bem documentada com resultados consistentes entre chamadas                 |
| Gerente de Produto EdTech              | Parte interessada não técnica em uma empresa de educação           | Confiança de que os resultados de cálculo apresentados aos alunos estão corretos           |
| Analista Financeiro / Desenvolvedor Quant | Desenvolvedor construindo modelos financeiros ou sistemas de negociação | Aritmética de precisão arbitrária com histórico de cálculo auditável e versionado     |
| Desenvolvedor de Simulação de Engenharia | Engenheiro construindo ferramentas de CAD, física ou modelagem    | Operações de alta performance com matrizes, vetores e equações diferenciais                |
| Cientista de Dados                     | Analista construindo pipelines de pré-processamento               | Funções estatísticas consistentes chamáveis de qualquer linguagem ou plataforma            |
| Engenheiro de DevOps / Plataforma      | Engenheiro responsável por uptime e integração                    | API de baixa latência e alta disponibilidade com SLAs claros e monitoramento               |

### Restrições de Negócio

- **Orçamento bootstrap**: Desenvolvimento inicial financiado a partir de receita existente. Nenhum investimento externo planejado para o MVP. O orçamento total do MVP é de $150K (cobrindo desenvolvimento, infraestrutura e marketing inicial).
- **Equipe pequena**: Dois desenvolvedores backend, um desenvolvedor frontend (para o portal de documentação), um engenheiro de QA. Sem PhD em matemática dedicado na fase de MVP.
- **Tempo para o mercado**: O MVP deve estar publicamente disponível em 6 meses para validar a demanda antes de se comprometer com o investimento da Fase 2.
- **Modelo de precificação**: Deve suportar um plano gratuito (para impulsionar a adoção) e planos pagos baseados em uso. Infraestrutura de precificação necessária no lançamento.
- **Padrões de precisão**: Todas as funções devem igualar ou superar a precisão da aritmética de dupla precisão IEEE 754. O modo de precisão arbitrária é um recurso da Fase 2, não do MVP.

### Métricas de Sucesso

| Métrica                                     | Estado Atual   | Estado-Alvo (12 meses pós-MVP)          | Método de Medição                                         |
| ------------------------------------------- | -------------- | --------------------------------------- | --------------------------------------------------------- |
| Contas de API registradas                   | 0              | 5.000                                   | Contagem de registros de chaves de API                    |
| Consumidores de API mensais ativos          | 0              | 1.200                                   | Chaves de API únicas realizando ao menos 1 chamada/mês    |
| Chamadas de API por mês                     | 0              | 10 milhões                              | Métricas do CloudWatch API Gateway                        |
| Assinantes pagos                            | 0              | 200                                     | Registros do sistema de cobrança                          |
| Receita recorrente mensal                   | $0             | $80K                                    | Registros do sistema de cobrança                          |
| Uptime da API                               | N/A            | 99,9%                                   | Monitoramento de disponibilidade do CloudWatch            |
| Tempo médio de resposta (p50)               | N/A            | < 50ms                                  | Métricas de latência do CloudWatch                        |
| Bugs de precisão relatados por clientes     | N/A            | < 5 por trimestre                       | Rastreamento de tickets de suporte                        |
| Satisfação com a documentação para desenvolvedores | N/A   | > 4,2 / 5,0                             | Pesquisa trimestral com desenvolvedores registrados       |

---

## Visão Completa do Escopo

### Declaração da Visão do Produto

CalcEngine torna-se a camada de computação padrão para qualquer aplicação que precise de operações matemáticas além da aritmética básica, da mesma forma que o Stripe se tornou o padrão para pagamentos, ao oferecer uma API mais precisa, mais consistente e mais fácil de integrar do que construir por conta própria.

### Áreas de Funcionalidade

#### Área de Funcionalidade 1: Aritmética e Álgebra Básica

- **Descrição**: Operações matemáticas fundamentais que vão além do que as bibliotecas matemáticas padrão de linguagens fornecem de forma confiável.
- **Capacidades Principais**:
  - Aritmética de inteiros e decimais de precisão arbitrária (precisão configurável de até 1.000 dígitos)
  - Análise e avaliação de expressões (aceitar expressões em string como "2 * sin(pi/4) + log(100)")
  - Operações com polinômios (avaliação, localização de raízes, fatoração)
  - Resolução de equações (linear, quadrática, cúbica, sistemas de equações lineares)
  - Aritmética com frações e números racionais (representação exata, simplificação)
  - Aritmética com números complexos (adição, multiplicação, conversão polar/retangular)
- **Valor para o Usuário**: Desenvolvedores enviam uma expressão matemática como string e obtêm um resultado preciso e verificado sem implementar um parser ou se preocupar com precedência de operadores, deriva de ponto flutuante ou casos extremos.

#### Área de Funcionalidade 2: Trigonometria e Geometria

- **Descrição**: Capacidades completas de cálculo trigonométrico e geométrico.
- **Capacidades Principais**:
  - Todas as seis funções trigonométricas e seus inversos (sin, cos, tan, csc, sec, cot)
  - Funções hiperbólicas e inversas
  - Conversão graus/radianos/gradianos
  - Conversões de sistemas de coordenadas (Cartesiano, polar, esférico, cilíndrico)
  - Cálculos geométricos (área, volume, perímetro para formas padrão)
  - Cálculos de distância e ângulo em espaço 2D e 3D
- **Valor para o Usuário**: Elimina a necessidade de implementar casos extremos trigonométricos (valores exatos em ângulos especiais, tratamento de quadrantes, validação de domínio).

#### Área de Funcionalidade 3: Estatística e Probabilidade

- **Descrição**: Funções de análise estatística e distribuição de probabilidade.
- **Capacidades Principais**:
  - Estatística descritiva (média, mediana, moda, variância, desvio padrão, quartis, percentis)
  - Distribuições de probabilidade (normal, binomial, Poisson, qui-quadrado, distribuição t, distribuição F) com PDF, CDF e CDF inversa
  - Análise de regressão (linear, polinomial, exponencial, logarítmica)
  - Testes de hipótese (teste t, teste qui-quadrado, ANOVA)
  - Combinatória (permutações, combinações, fatorial, coeficientes binomiais)
  - Geração de números aleatórios com distribuições e sementes configuráveis
- **Valor para o Usuário**: Uma única chamada de API substitui a importação e configuração de bibliotecas estatísticas. Os resultados são reprodutíveis e auditáveis.

#### Área de Funcionalidade 4: Álgebra Linear e Operações Matriciais

- **Descrição**: Computação com matrizes e vetores para engenharia, gráficos e ciência de dados.
- **Capacidades Principais**:
  - Aritmética matricial (adição, multiplicação, operações escalares)
  - Decomposições matriciais (LU, QR, SVD, Cholesky, autovalor)
  - Determinante, inversa, rank, traço
  - Operações com vetores (produto escalar, produto vetorial, normalização)
  - Sistemas de equações lineares (eliminação Gaussiana, mínimos quadrados)
  - Suporte a matrizes esparsas para problemas de grande escala
- **Valor para o Usuário**: Equipes que constroem aplicações de simulação, ML ou gráficos obtêm álgebra linear validada sem vincular ao LAPACK ou manter bindings nativos.

#### Área de Funcionalidade 5: Cálculo

- **Descrição**: Operações de cálculo simbólico e numérico.
- **Capacidades Principais**:
  - Diferenciação numérica (derivadas de primeira e ordem superior)
  - Integração numérica (integrais definidas com métodos configuráveis: trapezoidal, Simpson, quadratura gaussiana)
  - Diferenciação e integração simbólica (para tipos de expressão suportados)
  - Limites e expansão em série (Taylor, Maclaurin)
  - Resolvedores de equações diferenciais ordinárias (Euler, Runge-Kutta)
- **Valor para o Usuário**: Engenheiros e cientistas obtêm operações de cálculo via API sem incorporar um sistema de álgebra computacional.

#### Área de Funcionalidade 6: Conversão de Unidades e Constantes Físicas

- **Descrição**: Conversão padrão de unidades e acesso a constantes físicas e matemáticas verificadas.
- **Capacidades Principais**:
  - Conversão de unidades em todas as unidades SI e imperiais comuns (comprimento, massa, temperatura, tempo, energia, pressão, velocidade, etc.)
  - Conversão de moedas (com atualizações diárias de taxas de um provedor de dados financeiros)
  - Constantes físicas (velocidade da luz, constante de Planck, número de Avogadro, etc.) com fontes citadas e valores de incerteza
  - Constantes matemáticas com precisão configurável (pi, e, razão áurea, etc.)
  - Análise dimensional (validar que combinações de unidades são fisicamente significativas)
- **Valor para o Usuário**: Uma API substitui múltiplas bibliotecas de conversão e valores de constantes hardcoded, com a garantia de que as constantes são provenientes de fontes confiáveis e atuais.

#### Área de Funcionalidade 7: Matemática Financeira

- **Descrição**: Funções de cálculo financeiro para empréstimos, investimentos e análise de risco.
- **Capacidades Principais**:
  - Valor do dinheiro no tempo (valor presente, valor futuro, anuidades, perpetuidades)
  - Tabelas de amortização de empréstimos
  - Precificação de títulos e cálculos de rendimento
  - Precificação de opções (Black-Scholes, modelo binomial)
  - Taxa interna de retorno (IRR) e valor presente líquido (NPV)
  - Métodos de depreciação (linear, saldo decrescente, soma dos anos)
- **Valor para o Usuário**: Empresas FinTech obtêm cálculos financeiros auditáveis e prontos para regulação sem construir motores matemáticos proprietários.

#### Área de Funcionalidade 8: Experiência do Desenvolvedor e Plataforma

- **Descrição**: A plataforma de API, documentação, SDKs e ferramentas de desenvolvedor que tornam o CalcEngine fácil de adotar.
- **Capacidades Principais**:
  - Documentação de API interativa com sandbox "experimente agora"
  - SDKs clientes para Python, JavaScript/TypeScript, Java, C#, Go e Ruby
  - Suporte a webhooks para cálculos de longa duração (processamento em lote)
  - Histórico de cálculos e log de auditoria por chave de API
  - Limitação de taxa com cotas claras e tratamento de excedentes
  - Versionamento de API com política de depreciação de 12 meses
  - Recurso de espaço de trabalho para equipes (chaves de API compartilhadas, painéis de uso, gerenciamento de cobrança)
- **Valor para o Usuário**: Desenvolvedores podem ir do cadastro à primeira chamada de API bem-sucedida em menos de 5 minutos.

### Pontos de Integração

- **Processador de pagamentos** (Stripe) - Cobrança de assinatura e medição baseada em uso
- **Provedor de identidade** (Auth0 ou Cognito) - Autenticação de contas de desenvolvedores
- **Provedor de dados financeiros** (para taxas de câmbio) - Feeds diários de taxas de câmbio
- **NIST / CODATA** - Fonte confiável para constantes físicas
- **Sistemas de CI/CD** (GitHub Actions, GitLab CI) - Publicação de SDK e gerenciamento de versões
- **Monitoramento** (Datadog ou CloudWatch) - Desempenho da API, taxas de erro, painéis de uso

### Jornadas do Usuário (Visão Completa)

#### Jornada 1: Desenvolvedor EdTech Adiciona Cálculo a uma Plataforma de Cursos

1. Desenvolvedor descobre o CalcEngine por meio de uma busca por "API de calculadora científica" e chega ao site de documentação.
2. Desenvolvedor cria uma conta gratuita e obtém uma chave de API em menos de 2 minutos.
3. Desenvolvedor navega pela documentação interativa, encontra o endpoint de trigonometria e testa `sin(pi/4)` no sandbox.
4. Desenvolvedor instala o SDK Python via pip e escreve uma integração de 3 linhas que envia expressões inseridas por alunos ao CalcEngine e exibe o resultado.
5. Desenvolvedor configura a API para retornar detalhamentos passo a passo das soluções para que os alunos possam ver como a resposta foi derivada.
6. A plataforma de cursos entra no ar. Milhares de alunos enviam cálculos diariamente. O desenvolvedor monitora o uso pelo painel do CalcEngine e faz upgrade para um plano pago quando os limites do plano gratuito são atingidos.

**Resultado**: A plataforma educacional lança um recurso de calculadora confiável em uma tarde, em vez de gastar semanas construindo e testando análise matemática.

#### Jornada 2: Startup FinTech Constrói uma Ferramenta de Comparação de Empréstimos

1. A equipe de produto de uma startup de empréstimos precisa de tabelas de amortização, cálculos de APR e computações de valor presente para uma ferramenta de comparação de empréstimos voltada ao cliente.
2. O desenvolvedor se cadastra no CalcEngine e navega até a seção de Matemática Financeira.
3. O desenvolvedor usa o endpoint de amortização de empréstimos para gerar um cronograma de pagamento para uma hipoteca de 30 anos a 6,5% de juros. A API retorna detalhamentos mês a mês de principal, juros e saldo.
4. O desenvolvedor integra os endpoints de NPV e IRR para permitir que os clientes comparem diferentes ofertas de empréstimos lado a lado.
5. A equipe de conformidade revisa a certificação de precisão e o log de auditoria do CalcEngine. Cada cálculo é rastreável até uma chamada de API versionada com entradas e saídas com carimbo de data/hora.
6. A ferramenta de comparação de empréstimos é lançada. O CalcEngine lida com 500K cálculos por mês. A startup paga com base no uso e evita contratar um desenvolvedor quant.

**Resultado**: A startup FinTech lança uma ferramenta financeira em conformidade e auditável sem construir lógica de cálculo proprietária.

#### Jornada 3: Cientista de Dados Usa o CalcEngine em um Pipeline de ML

1. Uma cientista de dados em uma empresa de saúde precisa normalizar dados de medições de pacientes usando transformações estatísticas (z-scores, rankings percentis, transformações logarítmicas) como pré-processamento antes do treinamento do modelo.
2. A cientista de dados instala o SDK Python do CalcEngine e chama os endpoints de estatísticas a partir de um notebook Jupyter.
3. O SDK aceita arrays de valores e retorna estatísticas descritivas e conjuntos de dados transformados.
4. A cientista de dados configura o modo em lote para processar 100K registros. O CalcEngine retorna os resultados via webhook quando o processamento é concluído.
5. Como o CalcEngine garante resultados reprodutíveis (mesmas entradas, mesmas saídas, entre versões), a cientista pode citar a versão da API em seu artigo de pesquisa para fins de reprodutibilidade.

**Resultado**: A cientista obtém transformações estatísticas validadas e reprodutíveis sem escrever e depurar código de estatísticas personalizado.

### Escalabilidade e Crescimento

- **Expansão geográfica**: Implantação inicial em US-East. Expandir para EU-West e AP-Southeast em até 12 meses do MVP com base em dados de geografia de usuários.
- **Crescimento de volume**: Arquitetar para 1 bilhão de chamadas de API/mês em 3 anos. Começar serverless, migrar endpoints de alto tráfego para contêineres se a latência exigir.
- **Crescimento de funcionalidades**: Novas áreas de funcionalidade adicionadas com base nos dados de demanda dos clientes. Candidatos incluem: teoria dos números, teoria dos grafos, processamento de sinais, resolvedores de otimização.
- **Expansão empresarial**: Introduzir opção de implantação local para setores regulados que não podem enviar dados a uma API compartilhada. Meta para a Fase 3.
- **Presença em marketplace**: Listar no AWS Marketplace, Azure Marketplace e RapidAPI para canais de distribuição adicionais.

### Roadmap de Longo Prazo

| Fase    | Foco                                                                                                                                                                        | Prazo          |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| MVP     | Aritmética básica, trigonometria, estatísticas básicas, avaliação de expressões, plataforma de API, portal de documentação, planos gratuito e pago                          | Meses 1-6      |
| Fase 2  | Álgebra linear, cálculo, matemática financeira, modo de precisão arbitrária, SDKs clientes (5 linguagens), log de auditoria de cálculos, espaços de trabalho para equipes   | Meses 7-14     |
| Fase 3  | Conversão de unidades, constantes físicas, soluções passo a passo, processamento em lote, recursos empresariais, opção local                                                | Meses 15-22    |
| Fase 4  | Estatística avançada (testes de hipótese, regressão), computação simbólica, resolvedores de otimização, listagens em marketplace                                            | Meses 23-30    |

---

## Escopo do MVP

### Objetivo do MVP

Provar que desenvolvedores pagarão por uma API de calculadora científica hospedada ao lançar com funções matemáticas básicas, validando a adoção por meio de cadastros no plano gratuito e convertendo ao menos 50 contas para planos pagos em 6 meses após o lançamento.

### Critérios de Sucesso do MVP

- [ ] 1.000 contas de desenvolvedor registradas em 3 meses após o lançamento
- [ ] 300 consumidores de API mensais ativos (ao menos 1 chamada/mês) em 3 meses
- [ ] 50 assinantes pagos em 6 meses
- [ ] $15K MRR em 6 meses
- [ ] Uptime da API de 99,9% nos primeiros 3 meses
- [ ] Tempo médio de resposta (p50) abaixo de 50ms para todos os endpoints do MVP
- [ ] Zero bugs críticos de precisão relatados (cálculos retornando resultados errados)
- [ ] Net Promoter Score de 40+ na pesquisa de desenvolvedores na marca de 3 meses

### Funcionalidades no Escopo (MVP)

| Funcionalidade                             | Descrição                                                                                                                                                                                                  | Prioridade      | Justificativa para Inclusão                                                                                                   |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Operações aritméticas básicas              | Adição, subtração, multiplicação, divisão, módulo, potência, raiz quadrada, raiz n-ésima, valor absoluto, piso, teto, arredondamento                                                                       | Must Have       | Base para todos os outros cálculos. Requisito mínimo para qualquer API de calculadora.                                        |
| Avaliação de expressões                    | Aceitar uma expressão matemática em string (ex.: "2 * (3 + 4)^2 / sin(pi)") e retornar o resultado avaliado. Suportar precedência de operadores, parênteses e funções aninhadas.                           | Must Have       | O diferenciador de maior valor. Desenvolvedores enviam expressões como strings em vez de construir parsers.                   |
| Funções trigonométricas                    | sin, cos, tan, asin, acos, atan, atan2 com modo graus e radianos                                                                                                                                           | Must Have       | Requisito universal em casos de uso de EdTech, engenharia e gráficos.                                                        |
| Funções logarítmicas e exponenciais        | log (base 10), ln (logaritmo natural), log com base arbitrária, exp, potência                                                                                                                              | Must Have       | Necessário para cálculos financeiros, científicos e estatísticos.                                                             |
| Estatísticas básicas                       | Média, mediana, moda, desvio padrão, variância, mínimo, máximo, soma, contagem, percentil                                                                                                                  | Must Have       | Necessidade de alta frequência. Valida demanda dos segmentos de ciência de dados e EdTech.                                    |
| Constantes matemáticas                     | pi, e, razão áurea (phi), sqrt(2), sqrt(3), ln(2), ln(10) com dupla precisão IEEE 754                                                                                                                      | Must Have       | Baixo custo de implementação, alta utilidade. Evita que desenvolvedores hardcodem valores imprecisos.                         |
| Fatorial, permutações, combinações         | n!, nPr, nCr com suporte a números grandes                                                                                                                                                                 | Must Have       | Necessário para casos de uso de probabilidade e combinatória em EdTech.                                                       |
| Tratamento de erros e validação de domínio | Respostas de erro claras para erros de domínio (raiz de negativo, log de zero, divisão por zero), overflow e expressões inválidas. Formato de erro estruturado com códigos de erro.                        | Must Have       | Qualidade profissional de API. Tratamento de erros ruim é o principal motivo pelo qual desenvolvedores abandonam APIs.        |
| Gerenciamento de chaves de API             | Cadastro de desenvolvedor, geração de chave de API, rotação de chave, revogação de chave                                                                                                                   | Must Have       | Infraestrutura mínima de autenticação para uma API comercial.                                                                 |
| Medição de uso e limitação de taxa         | Rastrear chamadas por chave de API. Plano gratuito: 10.000 chamadas/mês. Plano pago: 1M chamadas/mês. Cabeçalhos claros de limite de taxa nas respostas.                                                    | Must Have       | O modelo de receita depende de precificação baseada em uso. Deve estar presente no lançamento.                                |
| API REST com JSON                          | Todos os endpoints aceitam JSON e retornam JSON. Convenções REST padrão. Especificação OpenAPI 3.x publicada.                                                                                              | Must Have       | Padrão esperado para APIs modernas.                                                                                           |
| Portal de documentação da API              | Site de documentação hospedado com referência de endpoints, exemplos de código em 3 linguagens (Python, JavaScript, cURL) e sandbox interativo "experimente agora".                                        | Must Have       | A adoção por desenvolvedores depende inteiramente da qualidade da documentação.                                               |
| Integração de cobrança                     | Cobrança de assinatura baseada em Stripe. Plano gratuito, Starter ($29/mês), Professional ($99/mês). Cobrança de excedente de uso.                                                                         | Must Have       | A coleta de receita deve ser automatizada desde o primeiro dia.                                                               |

### Funcionalidades Explicitamente Fora do Escopo (MVP)

| Funcionalidade                              | Motivo do Adiamento                                                                                                                                 | Fase-Alvo      |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Aritmética de precisão arbitrária           | Adiciona complexidade significativa a cada endpoint. A dupla precisão padrão IEEE 754 é suficiente para validação do MVP.                           | Fase 2         |
| Operações matriciais e álgebra linear       | Grande superfície de funcionalidade. Não é necessário para validar a hipótese central do negócio.                                                   | Fase 2         |
| Cálculo (diferenciação, integração)         | Requer expertise em métodos numéricos e testes extensivos de casos extremos.                                                                        | Fase 2         |
| Matemática financeira                       | Domínio especializado. Validar primeiro a demanda geral de desenvolvedores.                                                                         | Fase 2         |
| Computação simbólica                        | Requer um sistema de álgebra computacional. Fora do escopo para uma equipe pequena e o prazo do MVP.                                                | Fase 3         |
| Detalhamentos de soluções passo a passo     | Alto valor para EdTech, mas esforço de implementação significativo. Validar demanda por meio de entrevistas com clientes durante o MVP.             | Fase 3         |
| Conversão de unidades                       | Útil, mas não central à proposta de valor da calculadora. Muitas alternativas gratuitas existem.                                                    | Fase 3         |
| Banco de dados de constantes físicas        | Baixo custo de implementação, mas baixa urgência. Incluir na Fase 3 com conversão de unidades.                                                      | Fase 3         |
| SDKs clientes (Python, JS, Java, etc.)      | Documentação com cURL e exemplos de código é suficiente para o MVP. SDKs aceleram a adoção, mas não são necessários para validar a demanda.         | Fase 2         |
| Processamento em lote / webhooks            | Necessário para usuários de alto volume. O MVP foca em chamadas síncronas de cálculo único.                                                         | Fase 3         |
| Log de auditoria de cálculos                | Importante para setores regulados. Não necessário para a adoção inicial de desenvolvedores.                                                         | Fase 2         |
| Espaços de trabalho para equipes            | Recurso empresarial. Contas individuais de desenvolvedores são suficientes para o MVP.                                                              | Fase 3         |
| Implantação local                           | Recurso empresarial que requer esforço significativo de empacotamento.                                                                              | Fase 3+        |
| Distribuições de probabilidade (PDF, CDF)   | Útil, mas não central à validação do MVP. Estatísticas básicas cobrem a demanda inicial.                                                            | Fase 2         |
| Análise de regressão                        | Recurso estatístico especializado. Adiar até que a demanda por estatísticas seja validada.                                                          | Fase 4         |
| Aritmética com números complexos            | Caso de uso de nicho. Validar demanda de usuários de engenharia primeiro.                                                                           | Fase 2         |

### Jornadas do Usuário do MVP

#### Jornada 1: Desenvolvedor Descobre e Integra o CalcEngine

1. Desenvolvedor pesquisa por "API de avaliação de expressões matemáticas" e encontra a documentação do CalcEngine.
2. Desenvolvedor clica em "Obter Chave de API" e preenche um formulário de cadastro de uma página (e-mail, senha, nome da empresa opcional).
3. Desenvolvedor recebe a chave de API imediatamente na página de confirmação e em um e-mail de boas-vindas.
4. Desenvolvedor copia um exemplo cURL da documentação e executa no terminal: `curl -X POST https://api.calcengine.io/v1/evaluate -H "Authorization: Bearer {key}" -d '{"expression": "sin(pi/4) * 2 + sqrt(16)"}'`
5. Desenvolvedor recebe uma resposta JSON: `{"result": 5.414213562373095, "expression": "sin(pi/4) * 2 + sqrt(16)", "precision": "double"}`
6. Desenvolvedor lê o exemplo de código Python no site de documentação, copia na sua aplicação e substitui a string de expressão pela entrada do usuário.
7. Aplicação entra no ar. Desenvolvedor monitora o uso no painel do CalcEngine.

**Resultado**: Desenvolvedor vai da descoberta à integração funcional em menos de 15 minutos.
**Limitação vs Visão Completa**: Sem SDK (chamadas HTTP brutas), sem detalhamentos passo a passo, sem log de auditoria.

#### Jornada 2: Empresa EdTech Avalia o CalcEngine para Uso por Alunos

1. Gerente de produto de EdTech pede ao desenvolvedor que avalie o CalcEngine para um recurso de verificação de tarefas.
2. Desenvolvedor se cadastra no plano gratuito e testa 20 cálculos comuns de alunos (fórmula quadrática, identidades trigonométricas, estatísticas básicas) usando o sandbox da API.
3. Desenvolvedor verifica os resultados em relação às respostas corretas conhecidas. Todos correspondem.
4. Desenvolvedor integra o CalcEngine ao verificador de tarefas. Alunos digitam expressões matemáticas, o app as envia ao CalcEngine, e o resultado é comparado com a resposta esperada.
5. O plano gratuito suporta o piloto inicial em sala de aula (500 alunos, ~8.000 chamadas/mês). Quando o piloto se expande para todo o distrito escolar, o desenvolvedor faz upgrade para o plano Starter.

**Resultado**: Empresa EdTech lança um recurso de verificação de tarefas sem construir um parser matemático.
**Limitação vs Visão Completa**: Sem soluções passo a passo para alunos, sem suporte a números complexos, sem funções de cálculo para cursos avançados.

### Restrições e Premissas do MVP

- **Premissa**: Desenvolvedores preferem uma API hospedada a uma biblioteca local para operações matemáticas. **Risco se errado**: Baixa adoção apesar da computação precisa. **Mitigação**: O plano gratuito permite validação com baixo comprometimento; pivotar para o modelo de biblioteca open-source se o modelo de API falhar.
- **Premissa**: A avaliação de expressões (string de entrada, resultado de saída) é o recurso de maior valor. **Risco se errado**: Desenvolvedores na verdade preferem endpoints de funções individuais em vez de parsing de expressões. **Mitigação**: O MVP inclui tanto a avaliação de expressões quanto endpoints de funções individuais; os dados de uso revelarão qual é preferido.
- **Premissa**: A dupla precisão IEEE 754 é suficiente para usuários do MVP. **Risco se errado**: Adotantes iniciais em finanças ou ciência exigem maior precisão imediatamente. **Mitigação**: Precisão arbitrária é prioridade da Fase 2 e pode ser acelerada se os sinais de demanda forem fortes.
- **Premissa**: 10.000 chamadas gratuitas/mês é suficiente para avaliar o produto, mas baixo o suficiente para impulsionar a conversão para o plano pago. **Risco se errado**: O plano gratuito é generoso demais (sem conversão) ou restritivo demais (usuários saem antes de avaliar). **Mitigação**: Ajustar o limite com base nos dados de conversão na marca de 2 meses.
- **Limitação Aceita**: Sem SDKs clientes no MVP. Desenvolvedores devem fazer chamadas HTTP brutas. Isso adiciona atrito, mas SDKs são caros de construir e manter em múltiplas linguagens antes de o product-market fit ser validado.
- **Limitação Aceita**: Implantação em região única (US-East-1). A latência para usuários na Europa e Ásia será maior. Aceitável para o MVP porque os payloads de cálculo são pequenos (baixa sensibilidade à largura de banda).

### Definição de Pronto do MVP

- [ ] Todas as 13 funcionalidades "Must Have" implementadas, testadas e implantadas
- [ ] API responde corretamente a um conjunto de validação de 500+ casos de teste matemáticos cobrindo todas as funções do MVP
- [ ] Casos extremos tratados adequadamente: divisão por zero, overflow, underflow, expressões inválidas, erros de domínio (ex.: log(-1))
- [ ] Uptime da API demonstrado em 99,9% ao longo de um período de burn-in de 2 semanas antes do lançamento público
- [ ] Tempo de resposta p50 abaixo de 50ms, p99 abaixo de 200ms medido durante o período de burn-in
- [ ] Portal de documentação no ar com referência de endpoints, exemplos de código (Python, JavaScript, cURL) e sandbox interativo
- [ ] Integração de cobrança funcional: plano gratuito aplicado, plano pago disponível para compra, uso rastreado com precisão
- [ ] Especificação OpenAPI 3.x publicada e disponível para download
- [ ] Revisão de segurança concluída: autenticação por chave de API, limitação de taxa, validação de entrada, sem vulnerabilidades de injeção
- [ ] Teste de carga concluído: API suporta 1.000 requisições simultâneas sem degradação
- [ ] Demonstração para partes interessadas concluída e aprovação recebida

---

## Riscos e Dependências

### Principais Riscos

| Risco                                                                                             | Probabilidade | Impacto  | Mitigação                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------- | ------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Baixa adoção de desenvolvedores: mercado prefere bibliotecas locais a APIs hospedadas para matemática | Médio     | Alto     | O plano gratuito reduz a barreira. Enfatizar consistência entre plataformas e avaliação de expressões como diferenciais que bibliotecas locais não têm. Monitorar conversão de cadastro para uso ativo. |
| Bugs de precisão prejudicam a credibilidade: um resultado de cálculo errado reportado publicamente | Baixo        | Crítico  | Conjunto de testes abrangente (500+ casos por função), comparação com implementações de referência (Wolfram Alpha, Python mpmath), testes de regressão automatizados a cada implantação.                |
| Casos extremos do parser de expressões: entrada inesperada causa travamentos ou resultados errados | Médio        | Alto     | Teste de fuzz com expressões aleatórias, definição explícita de gramática, isolar o parser para prevenir injeção.                                                                                       |
| Abuso do plano gratuito: bots ou scrapers consomem recursos sem converter                         | Médio         | Médio    | Limitação de taxa por chave de API, CAPTCHA no cadastro, detecção de anomalias nos padrões de uso. Ajustar o limite do plano gratuito se necessário.                                                    |
| Atrasos na integração de cobrança com Stripe atrasam o lançamento do MVP                          | Baixo         | Médio    | Iniciar a integração de cobrança no mês 2. Usar faturamento manual como alternativa temporária se necessário.                                                                                           |
| Falha em região única derruba todo o serviço                                                      | Baixo         | Alto     | Implantar em duas zonas de disponibilidade dentro do US-East-1. Multi-região é Fase 2, mas redundância de AZ fornece resiliência básica.                                                                |
| Concorrente lança API similar durante nosso desenvolvimento                                       | Baixo         | Médio    | A velocidade de chegada ao mercado é a principal defesa. Prazo de MVP de 6 meses. Focar na experiência do desenvolvedor como vantagem competitiva: qualidade da documentação, tempo de resposta, mensagens de erro. |

### Dependências Externas

- **Stripe** - Processamento de pagamentos e gerenciamento de assinaturas - API disponível e bem documentada
- **Auth0 ou AWS Cognito** - Autenticação de desenvolvedores - Disponível, avaliar durante o mês 1
- **Registrador de domínio** - domínio calcengine.io (ou similar) - Deve ser adquirido antes de o site de documentação entrar no ar
- **Provedor de nuvem (AWS)** - Computação, API Gateway, banco de dados - Disponível, sem necessidade de aprovação
- **Provedor de certificado SSL** - TLS para API e site de documentação - Disponível via AWS Certificate Manager

### Perguntas em Aberto

- [ ] O avaliador de expressões deve suportar atribuição de variáveis (ex.: "x = 5; 2*x + 3") ou apenas avaliação de expressão única no MVP?
- [ ] Qual é o comprimento máximo de expressão que o parser deve aceitar? 1KB? 10KB? É necessário equilibrar flexibilidade contra potencial de abuso.
- [ ] A API deve retornar resultados como strings (preservando a representação de precisão) ou como números JSON (arriscando problemas de serialização de ponto flutuante)?
- [ ] Precisamos suportar multiplicação implícita (ex.: "2pi" significando "2 * pi") ou exigir operadores explícitos?
- [ ] O plano gratuito deve exigir cartão de crédito cadastrado para reduzir abuso, ou o cadastro apenas com e-mail é melhor para adoção?
- [ ] Qual é a política de cancelamento e reembolso para assinaturas pagas?
- [ ] Devemos publicar benchmarks de precisão comparando os resultados do CalcEngine com Wolfram Alpha e Python mpmath no site de documentação?
