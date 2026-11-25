---
layout: default
lang: pt_PT
title: Plugin Mérite
description: Documentação do plugin Mérite (deserve)
---

## Apresentação

O plugin **Mérite** é um semáforo para o Jeedom. Cada equipamento, chamado «Merecedor», tem um contador e um objetivo. Cenários ou ações adicionam pontos (**Mérito**) ou retiram-nos (**Demérito**). Quando o contador atinge o objetivo, o equipamento torna-se merecedor e as suas ações de mérito são executadas. Quando volta a ficar abaixo do objetivo, deixa de o ser e as suas ações de demérito são executadas.

O objetivo é simplificar os cenários. Em vez de escrever uma condição que tem de conhecer o estado de todos os elementos envolvidos, cada cenário limita-se a adicionar ou retirar os seus pontos. Toda a lógica de «o que acontece quando o limiar é ultrapassado» fica reunida num único sítio: o equipamento Merecedor.

## Configuração do plugin

O plugin não tem dependências nem serviços em segundo plano. Basta ativá-lo.

## Configuração de um equipamento

Em **Plugins → Automatização → Mérite**, clique em **Adicionar** e dê um nome ao seu Merecedor.

### Parâmetros gerais

- **Nome do equipamento**, **Objeto pai**, **Categoria**, **Ativar**, **Visível**: parâmetros habituais do Jeedom.
- **Reinício**: se esta caixa estiver marcada, o contador volta a 0 assim que o objetivo é atingido, logo após a execução das ações de mérito. *É merecedor* volta então também a 0, **sem** executar as ações de demérito. Cada vez que o objetivo é atingido comporta-se assim como um impulso, o que se adequa bem a um sistema de níveis ou de recompensas.
- **Onde são utilizados os comandos**: lista de cenários, vistas, designs, etc., que utilizam os comandos deste equipamento.

### Níveis

Os níveis permitem executar ações **antes** de atingir o objetivo, por exemplo para avisar que uma manutenção se aproxima.

- Cada nível tem um **limiar em percentagem do objetivo** (por exemplo 80 %), uma condição opcional e ações, como os eventos descritos abaixo.
- Um nível é executado quando a percentagem ultrapassa o seu limiar **a subir**. Se voltar a descer abaixo do limiar e subir de novo, o nível é executado outra vez.
- Se vários níveis forem ultrapassados de uma vez, são executados do mais baixo para o mais alto, e sempre antes das ações de mérito.
- Como o limiar é expresso em percentagem, os níveis acompanham automaticamente uma mudança de objetivo. Baixar o objetivo pode até fazer ultrapassar um nível.
- É possível que o valor ultrapasse os 100 %, uma vez que pode exceder o objetivo.

### Ações de mérito e de demérito

- As **ações de mérito** são executadas quando o contador **atinge ou ultrapassa** o objetivo (*É merecedor* passa de 0 para 1).
- As **ações de demérito** são executadas quando o contador **volta a ficar abaixo** do objetivo (*É merecedor* passa de 1 para 0).

As ações só são executadas ao **ultrapassar** o objetivo. Adicionar pontos a um equipamento já merecedor não volta a executar as ações de mérito.

As ações estão agrupadas em **eventos**:

- Cada evento tem uma **condição** opcional. Se for falsa, todo o evento é ignorado. Se for deixada em branco, o evento é sempre executado.
- Cada evento contém uma ou mais **ações**. Para cada uma delas, é possível escolher um comando de ação (botão «Lista») ou uma palavra-chave de cenário: mensagem, variável, cenário, esperar, alerta… (botão «Palavra-chave»).
- É possível desativar uma ação sem a eliminar, bastando para isso desmarcar a respetiva caixa de seleção.
- Os eventos são executados na ordem apresentada, assim como as ações de cada evento. As ações podem ser reordenadas com o controlador.

## Comandos

| Comando | Tipo | Descrição |
|---|---|---|
| **Valor** | informação numérica | Valor atual do contador (nunca negativo). |
| **Requer** | informação numérica | Objetivo a atingir (100 por predefinição). |
| **É merecedor** | informação binária | 1 se Valor ≥ Requer, 0 caso contrário. |
| **Percentagem do objetivo** | informação numérica (%) | Valor / Requer × 100, arredondado. Pode ultrapassar os 100 %. |
| **Em falta** | informação numérica | Pontos em falta para atingir o objetivo (Requer − Valor, mínimo 0). |
| **Mérito** | ação deslizante | Adiciona o valor do cursor ao contador. |
| **Demérito** | ação deslizante | Retira o valor do cursor ao contador (mínimo 0). |
| **Deve requerer** | ação deslizante | Altera o objetivo (mínimo 1). |
| **Ganhar** | ação | Coloca diretamente o contador no valor do objetivo. |
| **Reposição a zero** | ação | Repõe o contador a 0. |

Observações:

- Mérito e Demérito sem valor, ou com 0, não fazem nada.
- Os cursores do widget vão de 0 a 100. A partir de um cenário, pode enviar-se um valor maior (por exemplo *Deve requerer* a 150).
- Se a meta for reduzida para um valor inferior ao atual, o valor é ajustado à nova meta. Não é reposto se a meta for posteriormente aumentada.
- *Reposição a zero* e *Demérito* executam as ações de demérito se o equipamento era merecedor. *Ganhar* executa as ações de mérito se ainda não o era.
- *É merecedor* também pode servir de acionador ou de condição nos seus cenários.

## Exemplos de utilização

### Redução do consumo elétrico

Queremos evitar que demasiados grandes consumidores funcionem ao mesmo tempo: forno, máquina de lavar roupa, máquina de secar, máquina de lavar loiça, posto de carregamento.

- Crie um Merecedor «Grandes consumidores» com um objetivo de **3**.
- Para cada aparelho, um pequeno cenário faz **Mérito 1** quando a sua potência ultrapassa um limiar e **Demérito 1** quando volta a descer. Pode-se ponderar: o posto de carregamento pode contar como 2.
- Ações de mérito: pausar o posto de carregamento, desligar o termoacumulador, enviar uma notificação.
- Ações de demérito: reativar tudo.

Cada dispositivo gere apenas o seu +1 e o seu −1. Adicionar um dispositivo não requer a alteração dos outros cenários.

### Contador de manutenção

Para o filtro de um sistema de ventilação mecânica controlada (VMC), de um descalcificador ou de um exaustor, ou para o depósito de um aspirador robô.

- O objetivo é o limiar de manutenção (por exemplo, 50 ciclos).
- Em cada ciclo, um cenário faz **Mérito**, eventualmente ponderado: ciclo curto +1, ciclo longo +3.
- Um nível a 80 % envia a notificação «Manutenção necessária em breve».
- Ações de mérito: notificação «Não se esqueça de trocar o filtro». *É merecedor* fica a 1 enquanto a manutenção não for feita, o que o torna um lembrete persistente no dashboard.
- Após a manutenção, um clique em **Reposição a zero** a partir do dashboard.

### Pontos de mérito

- Cada tarefa concluída dá pontos (**Mérito 10**, **Mérito 20**…) através de um botão, de uma interação ou de um cenário.
- Um esquecimento detetado retira pontos (**Demérito 5**).
- Objetivo de 100, com **Reinício** marcado: cada vez que o objetivo é atingido é acionada uma recompensa (ligar uma tomada, enviar uma notificação…).
- Um cenário semanal faz **Reposição a zero** para recomeçar.

## Registos

O registo `deserve` indica, no nível **info**, cada vez que o objetivo é atingido. No nível **debug**, também detalha cada alteração de valor, cada condição avaliada e cada ação executada.
