---
layout: default
lang: pt_PT
title: Plugin Mérite
description: Documentação do plugin Mérite (deserve)
---

## Apresentação

O plugin **Mérito** é um semáforo para o Jeedom. Cada equipamento, denominado «Meritório», possui um contador e uma meta. Os cenários ou as ações atribuem pontos (**Mérito**) ou retiram-nos (**Demérito**). Quando o contador atinge a meta, o equipamento torna-se «meritante» e as suas ações meritantes são executadas. Quando volta a ficar abaixo da meta, deixa de o ser e as suas ações deméritantes são executadas.

O objetivo é simplificar os cenários. Em vez de definir uma condição que tenha de conhecer o estado de todos os elementos envolvidos, cada cenário limita-se a adicionar ou a retirar os seus pontos. Toda a lógica de «o que acontece quando o limiar é ultrapassado» está reunida num único local: o equipamento Méritant.

## Configuração do plugin

O plugin não tem dependências nem serviços em segundo plano. Basta ativá-lo.

## Configuração de um equipamento

Em **Plugins → Automatização → Mérito**, clique em **Adicionar** e atribua um nome ao seu «Meritante».

### Parâmetros gerais

- **Nome do equipamento**, **Objeto pai**, **Categoria**, **Ativar**, **Visível**: parâmetros habituais do Jeedom.
- **Reinício**: se esta opção estiver marcada, o contador volta a 0 assim que o objetivo for atingido, logo após a execução das ações meritórias. *É Meritório* volta então também a 0, **sem** iniciar as ações deméritórias. Cada vez que o objetivo é atingido funciona, portanto, como um impulso, o que se adequa bem a um sistema de níveis ou de recompensas.
- **Onde são utilizados os comandos**: lista de cenários, vistas, designs, etc., que utilizam os comandos deste equipamento.

### Níveis

Os níveis permitem desencadear ações **antes** de atingir o objetivo, por exemplo, para avisar que está a aproximar-se uma manutenção.

- Cada nível tem um **limiar em percentagem da meta** (por exemplo, 80 %), uma condição opcional e ações, tais como os eventos descritos abaixo.
- Uma condição é executada quando a percentagem ultrapassa o seu limiar **em subida**. Se voltar a descer abaixo do limiar e depois voltar a subir, a condição é executada novamente.
- Se forem ultrapassados vários níveis de uma só vez, estes são executados do mais baixo para o mais alto, e sempre antes das ações meritórias.
- Como o limiar é expresso em percentagem, os níveis ajustam-se automaticamente a uma alteração do objetivo. Reduzir o objetivo pode, aliás, fazer com que se ultrapasse um nível.
- É possível que o valor ultrapasse os 100 %, uma vez que pode exceder o objetivo.

### Ações meritórias e desmeritórias

- As **ações meritórias** são executadas quando o contador **atinge ou ultrapassa** a meta (*É Meritório* passa de 0 para 1).
- As **ações de demérito** são executadas quando o contador **volta a ficar abaixo** do objetivo (*É Meritório* passa de 1 para 0).

As ações só são executadas quando se **ultrapassa** o objetivo. Adicionar pontos a um equipamento que já cumpre os requisitos não reativa as ações que dão direito a pontos.

As ações estão agrupadas em **eventos**:

- Cada evento tem uma **condição** opcional. Se for falsa, todo o evento é ignorado. Se for deixada em branco, o evento é sempre executado.
- Cada evento contém uma ou mais **ações**. Para cada uma delas, é possível escolher um comando de ação (botão «Lista») ou uma palavra-chave de cenário: mensagem, variável, cenário, esperar, alerta… (botão «Palavra-chave»).
- É possível desativar uma ação sem a eliminar, bastando para isso desmarcar a respetiva caixa de seleção.
- Os eventos são executados na ordem apresentada, assim como as ações de cada evento. As ações podem ser reordenadas com o controlador.

## Comandos

| Comando | Tipo | Descrição |
|---|---|---|
| **Valor** | informação numérica | Valor atual do contador (nunca negativo). |
| **Requisitos** | informação digital | Objetivo a atingir (100 por predefinição). |
| **É merecedor** | informação binária | 1 se o valor for ≥ ao necessário, 0 caso contrário. |
| **Percentagem da meta** | informação numérica (%) | Valor / Necessidade × 100, arredondado. Pode ultrapassar os 100 %. |
| **Falta** | informação digital | Pontos em falta para atingir o objetivo (Requer − Valor, mínimo 0). |
| **Mérito** | controlo deslizante de ação | Adiciona o valor do controlo deslizante ao contador. |
| **Desmerito** | controlo deslizante de ação | Retira o valor do controlo deslizante do contador (mínimo 0). |
| **Deve exigir** | barra deslizante de ação | Alterar o objetivo (mínimo 1). |
| **Ganhar** | ação | Coloca diretamente o marcador no valor do objetivo. |
| **Zerar** | ação | Repõe o contador a 0. |

Observações:

- Os méritos e deméritos sem valor, ou com valor 0, não têm qualquer efeito.
- Os controles deslizantes do widget variam de 0 a 100. A partir de um cenário, é possível enviar um valor superior (por exemplo, *Deve ser necessário* a 150).
- Se a meta for reduzida para um valor inferior ao atual, o valor é ajustado à nova meta. Não é reposto se a meta for posteriormente aumentada.
- *Zerar* e *Desmerecer* desencadeiam as ações desmerecedoras se o equipamento fosse merecedor. *Ganhar* desencadeia as ações merecedoras se ainda não o fosse.
- *É Merecedor* também pode servir como desencadeador ou condição nos seus cenários.

## Exemplos de utilização

### Redução do consumo elétrico

Queremos evitar que demasiados aparelhos de elevado consumo estejam a funcionar ao mesmo tempo: forno, máquina de lavar roupa, secadora, máquina de lavar louça e estação de carregamento.

- Crie um «Grandes consumidores» com um objetivo de **3**.
- Para cada aparelho, um pequeno cenário atribui **1 ponto positivo** quando a sua potência ultrapassa um limiar e **1 ponto negativo** quando volta a descer. É possível ponderar: o terminal pode valer 2 pontos.
- Ações recomendadas: colocar o terminal em pausa, desligar o aquecedor de água, enviar uma notificação.
- Ações indesejáveis: reativar tudo.

Cada dispositivo gere apenas o seu +1 e o seu −1. Adicionar um dispositivo não requer a alteração dos outros cenários.

### Contador de manutenção

Para o filtro de um sistema de ventilação mecânica controlada (VMC), de um descalcificador ou de um exaustor, ou para o depósito de um aspirador robô.

- O objetivo é o limiar de manutenção (por exemplo, 50 ciclos).
- Em cada ciclo, um cenário recebe **Pontos**, eventualmente ponderados: ciclo curto +1, ciclo longo +3.
- Quando o nível atinge os 80 %, é enviada uma notificação a indicar «Manutenção necessária em breve».
- Ações merecedoras: notificação «Não se esqueça de trocar o filtro». *É merecedora* permanece em 1 enquanto a manutenção não for realizada, o que a torna um lembrete persistente no painel de controlo.
- Após a manutenção, clique em **Reiniciar** no painel de controlo.

### Pontos de mérito

- Cada tarefa concluída dá pontos (**Mérito 10**, **Mérito 20**…) através de um botão, uma interação ou um cenário.
- Cada esquecimento constatado implica a perda de pontos (**5 pontos de penalização**).
- Objetivo de 100, com a opção **Reiniciar** marcada: cada meta alcançada desencadeia uma recompensa (ligar uma tomada, enviar uma notificação…).
- Um cenário semanal executa a função **Reiniciar** para começar do zero.

## Registos

O registo `deserve` indica, no nível **info**, cada vez que o objetivo é atingido. No nível **debug**, também detalha cada alteração de valor, cada condição avaliada e cada ação executada.
