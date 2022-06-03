# event-driven-architecture
This repository stores the content of an online meeting on Balta.io platform about Event-Driven Architecture

## Objetivos:

- Entender sobre messageria
- Microserviços e eventos
- Arquitetura orientada a eventos
- Eventos como fonte de verdade

<hr>

## Cenário:

### O que nossa empresa faz?
- Produção
- Vendas
- Entregas

### Esperado
- Mensagens, eventos e comandos
- Benefícios
- Drawbacks (malefícios)
- Event Storming (dos eventos ao DDD)

<sub> A aplicação de arquiteturas (EDA, por exemplo) devem ser realizadas para suprir uma demanda e resolver um problema. </sub>

<hr>

## Monolíticos, Microsserviços e EDA

### Mololíticos
- Camada de Apresentação (User interface)
- Camada de Negócios (Lógica de negógio: pedidos, notas, vendas, usuários, pagamentos, envios e etc..)
- Camada de Dados (Banco de dados)

<sub> Ponto negativo: aplicação engessada </sub>

### Microsserviços
- Interface
- API Gateway
- Serviços

<sub> Ponto negativo: service hell, muita coisa espalhada pra manter </sub>

### EDA (Event Driven Architecture)
- Arquitetura orientada a eventos
- Padrão de arquitetura
- Provome:
    - Produção
    - Detecção
    - Consumo
    - Reação
- Tudo gira em torno de eventos, não de daods

<sub>Serve para: microsserviços, serverless, FaaS, Streaming, Event Sourcing, CQRS</sub>

<hr>

## EDA e Microsserviços

### Cenário de microsserviços
- Cada MS responde por um pipe de eventos
- Estes grupos são desacoplados
- Utilizam intermediadores, por isso a infra deve ser bem pensada

<hr>

## Messages, Events, Commands

### Message
- Unidade básica de comunicação
- Pode ser literalmente qualquer coisa (string, int, objeto)

### Evento
- Uma mensgem que informa diversos "listeners" que algo aconteceu
- Quem publica o evento é chamado de "Producer"
- Quem ouve o evento é chamado de "Custoemr"
    - Reagem ao evento
- Criamos evento sempre no passado
    - Order_created
    - Account_Updated
- Já aconteceu, já foi disparado

### Commands
- Representa uma ação direcionada
- Possui uma conexão 1x1
  - Entre producer e consumer
- CriarConta, RealizarPedido

<hr>

## Prós
- Desacoplamento
  - Utilizam um Broker para se comunicar (Broker é um middleware que abstrai a comunicação entre os serviços)
- Encapsulamento
  - Podemos trabalhar de forma independente atuando no context correto
- Performance
  - Quase em real-time
  - Escalável

<hr>

## Contras
- Curva de aprendizado
  - Como definir o SOT (source of truth)
  - E quando dá errado?
  - SAGAS (transações de longas durações)
- Complexo
  - Fluxos ficam complexos
  - Recortes nunca ficam corretos
- Não tem transação
- Versionamento
  - Mudanças nos objetos dos eventos

<hr>

## Event Storming

### Modelo Tradicional
  - Centralizado em Dados
  - Normalmente feito por uma DBA

### EDA
  - Centralizado em Eventos
  - Combina bem com DDD
  - Feito através de um time
    - Evento chamado Event Storming

### Finalidade
  - Modelar o domínio com base em eventos
  - Resultado da colaboração de diversos membros

### Boas práticas
- Convide as pessoas certas
    - Facilitador, técnicos, arquitetos, negócio
- Tenha um board com post-its

<hr>

## Como funciona o Event Storming

### Domain Event
  - Algo que acontece no sistema e é relevante para o negócio
  - Provoca reações (ex: envio de e-mail após criação da conta)
  - Outros eventos respondem a eles

### Policies
  - Ocorre após um evento ser disparado
  - "Sempre que"
    - Sempre que uma conta for criada, nós enviados um E-mail

### Externo (External Systems)
  - Algo que acontece externo ao sistema
  - Não temos controle sobre
    - Pagamentos, envio de E-mails

### Commands (comandos)
  - Iniciados pelo usuário ou outro sistema (job)

### Aggregate (Agregados)
  - Agrupam comportamentos em comum

### Bounded Context
  - Agrupam significados em comum

<hr>

## Mapeando Eventos:

- Um comando dispara um evento
- Cada evento é uma ação realizada pelo comando
- Tomadas de decisões / validações durante o processo do evento são feitas através das políticas

<hr>

