# Visão: Módulo de Devoluções e Reembolsos — Plataforma OrderFlow


**Author:** Raja SP, AWS Labs <br>
**Source:** https://github.com/awslabs/aidlc-workflows <br>
**Adaptation:** Ricardo de Luna Galdino, EngSoft Learn<br>
**Download:** [example-minimal-vision-brownfield.pt-br.pdf](../pdf/writing-inputs/example-minimal-vision-brownfield.pt-br.pdf)

> **Projeto brownfield.** Este documento descreve uma mudança em um sistema existente.
> A seção Estado Atual é obrigatória. Ela fornece ao AIDLC o contexto necessário para
> entender o que já existe antes de gerar requisitos e design.

---

## Estado Atual

O OrderFlow é uma plataforma de gestão de pedidos de e-commerce existente, construída em TypeScript
sobre Node.js. Ela lida com criação de pedidos, captura de pagamentos, roteamento de atendimento e
notificações de envio. Atualmente não possui nenhuma capacidade de devoluções ou reembolsos.
Clientes que querem devolver um item entram em contato com o suporte por e-mail, e os reembolsos são
processados manualmente pela equipe de finanças no painel do provedor de pagamentos.

A plataforma existente tem três serviços backend (order-service, payment-service,
notification-service) e um frontend React. Todos os serviços são implantados no AWS ECS
Fargate. PostgreSQL é o armazenamento de dados primário.

---

## O Que Estamos Adicionando

Um módulo de devoluções e reembolsos que permite aos clientes fazer solicitações de devolução
de forma autônoma pelo storefront existente, e permite que a equipe de operações revise, aprove
e processe reembolsos sem sair da plataforma.

---

## Funcionalidades No Escopo (esta iteração)

- Formulário de solicitação de devolução voltado ao cliente: selecionar pedido, selecionar itens, selecionar motivo da devolução
- Rastreamento do status da solicitação de devolução para clientes (submetida, aprovada, rejeitada, reembolsada)
- Painel de operações: visualizar solicitações de devolução abertas, aprovar ou rejeitar com uma observação
- Processamento automatizado de reembolso via integração do payment-service existente
- Notificações por e-mail aos clientes em cada mudança de status via notification-service
- Códigos de motivo de devolução: danificado, item errado, mudança de ideia, outro

## Funcionalidades Explicitamente Fora do Escopo (esta iteração)

- Geração de etiqueta de frete para devolução (processo manual por enquanto, Fase 2)
- Reembolsos parciais no nível do item (apenas reembolsos completos do pedido no MVP)
- Integração de reposição ou gestão de estoque (Fase 2)
- Detecção de fraude ou prevenção de abuso de devoluções (Fase 3)
- Trocas autônomas (devolução + novo pedido em um único fluxo, Fase 2)
- Dashboard de análises ou relatórios de devoluções (Fase 2)

---

## O Que Não Deve Mudar

- Fluxos de criação de pedidos, captura de pagamentos e atendimento — não modifique estes
- O schema PostgreSQL existente para pedidos, pagamentos e clientes — apenas mudanças aditivas
- O contrato de API do notification-service — consuma-o como está, não o modifique
- A biblioteca de componentes React existente e o design system do frontend

---

## Perguntas Abertas

- As solicitações de devolução devem ter uma etapa de aprovação, ou devoluções elegíveis devem ser aprovadas automaticamente com base em regras de política (ex.: dentro de 30 dias, item não marcado como venda final)?
- Quem é responsável pela solicitação de devolução no painel de operações — equipe de suporte ao cliente, equipe de armazém ou ambas com visões diferentes?
- Os reembolsos devem ser emitidos imediatamente na aprovação, ou processados em lote no final do dia?
- Existe uma política de prazo de devolução (ex.: 30 dias a partir da entrega) que o sistema deve aplicar, ou é caso a caso por enquanto?
