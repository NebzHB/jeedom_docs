---
layout: default
lang: pt_PT
title: Plugin AdGuard Home
description: Documentação do plugin AdGuard Home
---

Este plugin permite monitorizar e executar algumas ações no seu AdGuard Home.

Configuração do plugin
=======================

Após a instalação do plugin, basta ativá-lo. Não é necessário efetuar nenhuma configuração específica

Configuração dos equipamentos
=============================

A configuração dos equipamentos AdGuard está acessível a partir do menu
plugins e, em seguida, Monitorização. Aqui encontrará:

-   um botão para criar um equipamento manualmente

-   um botão para visualizar a configuração do plugin

-   um botão que lhe dá uma visão geral de todos os seus equipamentos num determinado momento

-   Por fim, mais abaixo, encontrará a lista dos seus equipamentos AdGuard Home e dos clientes associados

Ao clicar num dos seus equipamentos, é redirecionado para a página
configuração do seu equipamento, que inclui 2 separadores: «Equipamento» e
comandos.

-   **Separador «Equipamento»**:

-   **Nome do equipamento**: nome do seu equipamento

-   **Ativar**: permite ativar o seu equipamento

-   **Visível**: torna-o visível no painel de controlo

-   **Objeto pai**: indica o objeto pai ao qual o equipamento pertence

-   **Altura do widget** (em versão beta): por predefinição, a altura do widget adapta-se ao seu conteúdo. Selecione **Fixo (a do modo de edição)** para manter a altura definida no modo de edição do painel de controlo.

**Apenas para o AdGuard**

-   **IP do servidor**: o IP do servidor do AdGuard Home.

> Se tiver alterado a porta predefinida (80), pode adicionar a sua porta aqui no formato ip:porta

-   **Utilizador**: Utilizador do AdGuard Home.

-	**Palavra-passe**: Palavra-passe do utilizador do AdGuard Home.

-	**Atualização automática (cron)**: intervalos para verificar os dados no AdGuard Home, 5 minutos por predefinição.

Depois de adicionar o AdGuard Home e guardar os dispositivos, os clientes detetados no AdGuard Home são adicionados como dispositivos separados.

Se **adicionar um cliente** posteriormente, este será adicionado **automaticamente durante a noite**; para forçar a sua adição no Jeedom, **volte a guardar o equipamento AdGuard Home**.

Se, posteriormente, **remover um cliente**, este será desativado **automaticamente durante a noite**; para forçar a sua desativação no Jeedom, **volte a guardar o equipamento AdGuard Home**.

> Nota: Um equipamento do tipo **Cliente** tem de estar **desativado para poder ser eliminado**.

**Comandos do equipamento AdGuard**
================================
- **Atualizar**: Permite atualizar manualmente o equipamento, para além da atualização automática
- **Online**: Valor binário que indica se o AdGuard responde corretamente aos pedidos
- **Atualização do AdGuard disponível**: Binário que indica se está disponível uma atualização
- **Atualizar o AdGuard**: ação que permite atualizar o AdGuard (caso haja uma atualização disponível)
- **Limpar a cache DNS** (em fase beta): ação que permite limpar a cache DNS do AdGuard Home
- **Atualizar os filtros** (em fase Beta): Ação que permite forçar a atualização das listas de filtros

> A atualização do AdGuard e dos filtros pode demorar algum tempo: o plugin aguarda até 120 s pela resposta do AdGuard Home.

Widgets (em fase beta)
-----------------------
Os equipamentos AdGuard Home e Client têm o seu próprio widget (painel de controlo e versão móvel), inspirado no painel de controlo do AdGuard Home e atualizado em tempo real.

**Widget do equipamento AdGuard Home**

- **Proteção**: estado e interruptor. Se a proteção estiver ativa, um clique abre o menu dos tempos de pausa. Durante uma pausa, o tempo restante até ao reinício é contado regressivamente.
- **Estatísticas**: pedidos DNS, bloqueados por filtros, ameaças e conteúdos para adultos (com a percentagem do total), pesquisas seguras forçadas e tempo médio de processamento.
- **Definições** nos interruptores verde/cinzento: filtragem, segurança de navegação, controlo parental e pesquisa segura. A bolha de informação indica o que acontecerá ao clicar. Um botão vermelho «Internet bloqueada» permite desativar ou restabelecer a ligação à Internet em toda a rede.
- **Serviços bloqueados** apresentados através de ícones (o nome completo encontra-se na bolha de informação).
- **Ações numa linha**: serviços e grupos de serviços, regras de filtragem personalizadas, teste de domínio com o respetivo resultado e manutenção (esvaziar a cache DNS, atualizar os filtros, reiniciar as estatísticas).
- **Rodapé do widget**: estado de ligação, versão, ícone de atualização (um clique inicia a atualização do AdGuard Home após confirmação), botão «Atualizar» e uma janela com os restantes valores visíveis.

**Widget dos equipamentos do cliente**

- **Internet**: «Autorizada» ou «Bloqueada via DNS», com um botão que bloqueia ou desbloqueia a Internet para este cliente.
- **Configurações** nos botões: parâmetros gerais, filtragem, segurança de navegação, controlo parental, pesquisa segura e serviços gerais. Quando o cliente segue os parâmetros gerais (ou os serviços bloqueados de forma geral), as suas próprias configurações (ou a sua lista de serviços) ficam a cinzento, acompanhadas de uma nota explicativa.
- **Identificadores** e **serviços bloqueados** do cliente (em ícones).
- **Ações numa linha**: serviços e grupos de serviços, identificadores, teste de domínio com o respetivo resultado.

**Lista de serviços**

A lista de seleção de serviços apresenta o ícone de cada serviço, permite efetuar uma pesquisa e organiza os serviços nos respetivos grupos (categoria na barra superior, serviços indentados abaixo). Ao selecionar um grupo («todo o grupo»), todos os serviços desse grupo são bloqueados ou desbloqueados. Os grupos requerem, no mínimo, o AdGuard Home v0.107.68: numa versão mais antiga, a lista não apresenta grupos.

**Confirmações**

É solicitada uma confirmação antes de ações que reduzam a proteção ou que não sejam facilmente revertíveis: desligar a Internet (para um cliente ou para toda a rede), desativar a filtragem ou o controlo parental, bloquear ou desbloquear todos os serviços, esvaziar a cache DNS, atualizar os filtros, reiniciar as estatísticas e atualizar o AdGuard Home.

**Tamanho do widget**

- No painel de controlo, o widget tem, pelo menos, 320 px de largura. Se for mais estreito, os interruptores ficam dispostos numa coluna e os botões passam para a linha seguinte.
- Nos dispositivos móveis, o widget ocupa toda a largura do ecrã.
- A altura adapta-se ao conteúdo do widget. Para manter a altura definida no modo de edição do painel de controlo, assinale a opção **Altura do widget: Fixa (a do modo de edição)** na configuração do equipamento.

Os comandos de ação que o widget não reconhece mantêm o seu widget Jeedom.

Proteção Global
-----------------------
- **Estado da proteção**: Valor binário que indica o estado da proteção global
- **Ativar a proteção**: Ação que permite ativar a proteção global
- **Desativar a proteção**: Ação que permite desativar a proteção global
- **Tempo restante de pausa** (em versão beta): Tempo restante (em segundos) até ao reinício da proteção, quando esta foi desativada por um período determinado

> Novidade: agora já pode alterar o período durante o qual a proteção fica desativada (tal como na interface do AdGuardHome)

**Correspondência AdGuard**:

![imagem](https://user-images.githubusercontent.com/28622481/133206289-810d7a4d-9705-4923-9831-e8e78100f05b.png)

Filtragem global
-----------------------
- **Estado da Filtragem Global**: Valor binário que indica o estado da filtragem global
- **Ativar a filtragem global**: Ação que permite ativar a filtragem global
- **Desativar a filtragem global**: Ação que permite desativar a filtragem global

**Configurações do AdGuard** (Definições > Definições gerais > Bloquear domínios utilizando filtros e ficheiros hosts):

![imagem](https://user-images.githubusercontent.com/28622481/133206778-015af02d-8039-4c78-9732-e048c41cfa21.png)

Segurança global de navegação
-----------------------
- **Estado da Segurança de Navegação Global**: Valor binário que indica o estado da Segurança de Navegação Global
- **Ativar a Segurança de Navegação Global**: Ação que permite ativar a Segurança de Navegação Global
- **Desativar a Segurança de Navegação Global**: Ação que permite desativar a Segurança de Navegação Global

**Configurações do AdGuard** (Definições > Definições gerais > Utilizar o serviço de segurança de navegação do AdGuard):

![imagem](https://user-images.githubusercontent.com/28622481/133207227-8f9aa942-54c6-4048-8fa1-3711f4ca082c.png)

Controlo parental global
-----------------------
- **Estado do Controlo Parental Global**: Valor binário que indica o estado do Controlo Parental Global
- **Ativar o Controlo Parental Global**: Ação que permite ativar o Controlo Parental Global
- **Desativar o Controlo Parental Global**: Ação que permite desativar o Controlo Parental Global

**Configurações do AdGuard** (Definições > Definições gerais > Utilizar o controlo parental do AdGuard):

![imagem](https://user-images.githubusercontent.com/28622481/133207419-bac0d204-c4fc-414d-b411-c7ec072ab514.png)

Pesquisa global segura
-----------------------
- **Estado da Pesquisa Segura Global**: Valor binário que indica o estado da Pesquisa Segura Global
- **Ativar a Pesquisa Segura Global**: Ação que permite ativar a Pesquisa Segura Global
- **Desativar a Pesquisa Segura Global**: Ação que permite desativar a Pesquisa Segura Global

> Apenas o estado «ativado/desativado» é alterado: os motores de busca selecionados no AdGuard Home são mantidos. Se nenhum motor estiver marcado no momento da ativação, todos ficam marcados.

**Configurações do AdGuard** (Definições > Definições gerais > Reforçar a pesquisa segura):

![imagem](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Serviços Globais
-----------------------
- **Serviços bloqueados**: Canal que indica os serviços bloqueados globalmente
- **Bloquear um serviço**: Ação que permite bloquear um serviço da lista
- **Desbloquear um serviço**: Ação que permite desbloquear um serviço da lista
- **Bloquear todos os serviços**: Ação que permite bloquear todos os serviços da lista
- **Desbloquear todos os serviços**: Ação que permite desbloquear todos os serviços da lista
- **Bloquear um grupo de serviços** (em fase beta): Ação que permite bloquear todos os serviços de um grupo (lista suspensa)
- **Desbloquear um grupo de serviços** (em fase beta): Ação que permite desbloquear todos os serviços de um grupo (lista suspensa)

> Os grupos de serviços requerem, no mínimo, o AdGuard Home v0.107.68.

> A programação dos serviços bloqueados definida no AdGuard Home é mantida quando bloqueia ou desbloqueia serviços a partir do Jeedom.

**Configurações do AdGuard** (Filtros > Serviços bloqueados):

![imagem](https://user-images.githubusercontent.com/28622481/133207917-e813a4d1-42d2-491c-982a-ebabf6510383.png)

Internet bloqueada através do DNS
-----------------------
- **Estado da Internet bloqueada via DNS**: Valor binário que indica se a Internet foi bloqueada através do DNS
- **Bloquear todo o acesso à Internet através do DNS**: Ação que permite bloquear o acesso à Internet através do DNS
- **Desbloquear todo o acesso à Internet através do DNS**: Ação que permite desbloquear o acesso à Internet através do DNS

**Correspondência do AdGuard** (Filtros > Regras de filtragem personalizadas > adicionar a regra: `||*^$important` em primeiro lugar):

![imagem](https://user-images.githubusercontent.com/28622481/133210452-4ebbc8b0-836d-43a4-9db9-e01c2534679e.png)

Regra de filtragem personalizada
-----------------------
- **Adicionar uma regra de filtragem personalizada**: Campo que permite adicionar uma regra de filtragem personalizada em primeiro lugar (ortografia correta, sem aspas)
- **Remover uma regra de filtragem personalizada**: Campo que permite remover uma regra de filtragem personalizada (ortografia correta, sem aspas)

Ver [aqui](https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists){:target="_blank" rel="noopener"}

**Configuração do AdGuard** (Filtros > Regras de filtragem personalizadas > adicionar a regra em questão em primeiro lugar)

Testar um domínio (em fase beta)
-----------------------
- **Testar um domínio** (em fase beta): Ação (campo de mensagem) que permite verificar se um domínio está bloqueado ou não de acordo com as definições globais
- **Resultado do teste de domínio** (em versão beta): Cadeia que contém o resultado do último teste, por exemplo, `example.com: Bloqueado por um filtro (regra: ||example.com^)`

Estatísticas
-----------------------
- **Reiniciar estatísticas**: Permite zerar as estatísticas
- **Pedidos DNS**: indica o número de pedidos DNS processados nas últimas 24 horas
- **Bloqueadas por filtros**: indica o número de pedidos DNS bloqueados pelos filtros de bloqueio de anúncios e pelas listas de bloqueio de hosts
- **Tentativas de phishing por malware bloqueadas**: indica o número de pedidos DNS bloqueados pelo módulo de Segurança de Navegação do AdGuard
- **Pesquisas seguras forçadas**: indica o número de consultas DNS efetuadas com a Pesquisa Segura
- **Sites com conteúdo para adultos bloqueados**: indica o número de sites com conteúdo para adultos bloqueados
- **Tempo médio de processamento**: indica o tempo médio (em milissegundos) de processamento de um pedido DNS

**Correspondência do AdGuard** (Definições > Definições gerais > Configuração das estatísticas > botão «Apagar estatísticas»):

![imagem](https://user-images.githubusercontent.com/28622481/133211167-470e9959-bda7-4810-a02d-8d26363bb981.png)

**e** (Painel de controlo > Estatísticas gerais):

![imagem](https://user-images.githubusercontent.com/28622481/133211276-6c24d23c-6647-4b5f-a26c-e5834bd1a657.png)

**Encomendas de equipamento do cliente**
================================

Utilizar as Definições Gerais
--------------------------------
- **Estado «Utilizar as definições gerais»**: Valor binário que indica se a opção «Utilizar as definições gerais» está ativada
- **Ativar «Utilizar as definições gerais»**: Ação que permite ativar «Utilizar as definições gerais»
- **Desativar «Utilizar as definições gerais»**: Ação que permite desativar a opção «Utilizar as definições gerais»

**Configurações do AdGuard** (Definições > Definições do cliente > Editar cliente > Definições > Utilizar as definições gerais (1)):

![imagem](https://user-images.githubusercontent.com/28622481/133217292-24f23ed8-8de2-492f-bd83-e9b90715de17.png)

Filtragem
--------------------------------
- **Estado da filtragem**: Valor binário que indica o estado da filtragem
- **Ativar a filtragem**: Ação que permite ativar a filtragem
- **Desativar a filtragem**: Ação que permite desativar a filtragem

**Correspondência do AdGuard** (Definições > Definições do cliente > Editar cliente > Definições > Bloquear domínios utilizando filtros e ficheiros hosts (2))

Segurança na navegação
-----------------------
- **Estado da Segurança de Navegação**: Valor binário que indica o estado da Segurança de Navegação
- **Ativar a Segurança de navegação**: Ação que permite ativar a Segurança de navegação
- **Desativar a Segurança de navegação**: Ação que permite desativar a Segurança de navegação

**Configuração do AdGuard** (Definições > Definições do cliente > Editar cliente > Definições > Utilizar o serviço «Navegação segura» do AdGuard (3))

Controlo parental
-----------------------
- **Estado do Controlo Parental**: Valor binário que indica o estado do Controlo Parental
- **Ativar o Controlo Parental**: Ação que permite ativar o Controlo Parental
- **Desativar o Controlo Parental**: Ação que permite desativar o Controlo Parental

**Configurações do AdGuard** (Definições > Definições do cliente > Editar cliente > Definições > Utilizar o controlo parental do AdGuard (4))

Pesquisa segura
-----------------------
- **Estado da Pesquisa Segura**: Valor binário que indica o estado da Pesquisa Segura
- **Ativar a Pesquisa Segura**: Ação que permite ativar a Pesquisa Segura
- **Desativar a Pesquisa Segura**: Ação que permite desativar a Pesquisa Segura

**Correspondência AdGuard** (Definições > Definições do cliente > Editar cliente > Definições > Reforçar a pesquisa segura (5))

Utilizar os serviços globais bloqueados
--------------------------------
- **Estado «Utilizar serviços bloqueados globalmente»**: Valor binário que indica se a opção «Utilizar serviços bloqueados globalmente» foi ativada
- **Ativar «Utilizar serviços bloqueados globalmente»**: Ação que permite ativar «Utilizar serviços bloqueados globalmente»
- **Desativar «Utilizar serviços bloqueados globalmente»**: Ação que permite desativar «Utilizar serviços bloqueados globalmente»

**Configurações do AdGuard** (Definições > Definições do cliente > Editar cliente > Bloquear serviços específicos > Utilizar serviços bloqueados globalmente (1)):

![imagem](https://user-images.githubusercontent.com/28622481/133218452-cf994ad7-bf63-4dbd-b727-ff64339b7b31.png)

Serviços específicos
-----------------------
- **Serviços bloqueados**: Cadeia que indica os serviços bloqueados especificamente para este cliente
- **Bloquear um serviço**: Ação que permite bloquear um serviço da lista especificamente para este cliente
- **Desbloquear um serviço**: Ação que permite desbloquear um serviço da lista especificamente para este cliente

**Configurações do AdGuard** (Definições > Definições do cliente > Editar cliente > Bloquear serviços específicos > os serviços (2))

- **Bloquear todos os serviços**: Ação que permite bloquear todos os serviços da lista especificamente para este cliente
- **Desbloquear todos os serviços**: Ação que permite desbloquear todos os serviços da lista especificamente para este cliente

**Configurações do AdGuard** (Definições > Definições do cliente > Editar cliente > Bloquear serviços específicos > Bloquear tudo/Desbloquear tudo (3))

- **Bloquear um grupo de serviços** (em fase beta): Ação que permite bloquear todos os serviços de um grupo especificamente para este cliente (lista suspensa)
- **Desbloquear um grupo de serviços** (em fase beta): Ação que permite desbloquear todos os serviços de um grupo especificamente para este cliente (lista suspensa)

> Os grupos de serviços requerem, no mínimo, o AdGuard Home v0.107.68.

Internet bloqueada através do DNS
-----------------------
- **Estado «Internet bloqueada via DNS»**: Valor binário que indica se a Internet foi bloqueada via DNS para este cliente
- **Bloquear todo o acesso à Internet através do DNS**: Ação que permite bloquear o acesso à Internet através do DNS para este cliente
- **Desbloquear todo o acesso à Internet através do DNS**: Ação que permite desbloquear o acesso à Internet através do DNS para este cliente

**Correspondência AdGuard** (Filtros > Regras de filtragem personalizadas > adicionar a regra: `||*^$client='NomeDoCliente',importante` em primeiro lugar)

![imagem](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Testar um domínio para este cliente (em fase beta)
-----------------------
- **Testar um domínio para este cliente** (em fase Beta): Ação (campo de mensagem) que permite verificar se um domínio está bloqueado ou não de acordo com as definições deste cliente
- **Resultado do teste de domínio para este cliente** (em fase beta): Cadeia que contém o resultado do último teste para este cliente

> O AdGuard Home só consegue testar um domínio com uma morada IP ou um ClientID. O plugin utiliza, em primeiro lugar, a morada IP do cliente; caso contrário, a morada do seu intervalo CIDR; e, se isso também não for possível, o seu ClientID. Um cliente que apenas disponha de moradas MAC não pode ser testado: será exibida uma mensagem a indicar essa situação.

Dados de acesso
-----------------------
- **Identificador(es)**: Cadeia que contém os identificadores atuais do cliente
- **Adicionar um identificador**: Ação que permite adicionar um identificador ao cliente (sem aspas à volta!!)
- **Remover um identificador**: Ação que permite remover um identificador do cliente (sem aspas à volta!!)

> **Atenção: se já existir noutro cliente, é necessário removê-lo primeiro deste cliente! O AdGuard não permite que dois clientes partilhem as mesmas credenciais (faz sentido ;))**

**Correspondência do AdGuard** (Definições > Definições do cliente > Editar cliente > Identificador):

![imagem](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
