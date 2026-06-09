# Visão: CalcEngine — API de Calculadora Científica


**Author:** Raja SP, AWS Labs <br>
**Source:** https://github.com/awslabs/aidlc-workflows <br>
**Adaptation:** Ricardo de Luna Galdino, EngSoft Learn<br>
**Download:** [example-minimal-vision-scientific-calculator-api.pt-br.pdf](../pdf/writing-inputs/example-minimal-vision-scientific-calculator-api.pt-br.pdf)

## Resumo Executivo

O CalcEngine é uma API REST que permite aos desenvolvedores enviar expressões matemáticas como strings e receber resultados precisos. Em vez de cada equipe construir seu próprio parser matemático e funções trigonométricas, elas chamam nossa API. Vendemos como um serviço de assinatura com um plano gratuito para impulsionar a adoção e planos pagos para volume.

## Funcionalidades No Escopo (MVP)

- Avaliação de expressões: aceitar uma string como `"2 * sin(pi/4) + sqrt(16)"` e retornar o resultado numérico
- Aritmética básica: adição, subtração, multiplicação, divisão, potência, raiz quadrada, módulo, valor absoluto, piso, teto, arredondamento
- Trigonometria: sin, cos, tan, asin, acos, atan, atan2 (modos graus e radianos)
- Logaritmos: log base 10, logaritmo natural, log com base arbitrária, exp
- Estatísticas básicas: média, mediana, moda, desvio padrão, variância, mínimo, máximo, soma, percentil (aceita arrays)
- Constantes matemáticas: pi, e, phi, sqrt(2)
- Combinatória: fatorial, permutações (nPr), combinações (nCr)
- Tratamento de erros: códigos de erro claros para divisão por zero, erros de domínio (log de negativo), overflow, expressões malformadas
- Autenticação por chave de API com plano gratuito (10K chamadas/mês) e planos pagos
- Portal de documentação da API com sandbox interativo e exemplos de código

## Funcionalidades Explicitamente Fora do Escopo (MVP)

- Aritmética de precisão arbitrária (Fase 2)
- Matrizes e álgebra linear (Fase 2)
- Cálculo — derivadas, integrais (Fase 2)
- Matemática financeira — amortização, VPL, TIR (Fase 2)
- SDKs de cliente para Python/JS/Java (Fase 2 — HTTP bruto é suficiente para o MVP)
- Detalhamentos passo a passo da solução (Fase 3)
- Conversão de unidades e constantes físicas (Fase 3)
- Processamento em lote / webhooks assíncronos (Fase 3)
- Computação simbólica (Fase 3)
- Deploy on-premises (Fase 3+)

## Usuários-Alvo

- Desenvolvedores de aplicações que precisam de matemática em seus produtos, mas não querem construir/manter isso
- Empresas de EdTech que precisam de um backend de calculadora para ferramentas voltadas a alunos
- Startups de FinTech que precisam de cálculos auditáveis (plano pago, foco na Fase 2)

## Métricas de Sucesso Principais

- 1.000 contas de desenvolvedor registradas em 3 meses
- 50 assinantes pagos em 6 meses
- Uptime da API de 99,9%
- Tempo de resposta p50 abaixo de 50ms
- Zero bugs críticos de precisão (resultados de cálculo incorretos)

## Perguntas Abertas

- O avaliador de expressões deve suportar atribuição de variáveis (`x = 5; 2*x + 3`) ou apenas expressões únicas?
- Os resultados devem ser retornados como strings (preservando a precisão) ou como números JSON?
- A multiplicação implícita deve ser suportada (`2pi` significando `2 * pi`)?
