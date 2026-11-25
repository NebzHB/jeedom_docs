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

Proteção Global
-----------------------
- **Estado da proteção**: Valor binário que indica o estado da proteção global
- **Ativar a proteção**: Ação que permite ativar a proteção global
- **Desativar a proteção**: Ação que permite desativar a proteção global

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

**Configurações do AdGuard** (Definições > Definições gerais > Reforçar a pesquisa segura):

![imagem](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Serviços Globais
-----------------------
- **Serviços bloqueados**: Canal que indica os serviços bloqueados globalmente
- **Bloquear um serviço**: Ação que permite bloquear um serviço da lista
- **Desbloquear um serviço**: Ação que permite desbloquear um serviço da lista
- **Bloquear todos os serviços**: Ação que permite bloquear todos os serviços da lista
- **Desbloquear todos os serviços**: Ação que permite desbloquear todos os serviços da lista

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
- **Ativar «Utilizar os serviços bloqueados globalmente»**: Ação que permite ativar «Utilizar os serviços bloqueados globalmente»
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

Internet bloqueada através do DNS
-----------------------
- **Estado «Internet bloqueada via DNS»**: Valor binário que indica se a Internet foi bloqueada via DNS para este cliente
- **Bloquear todo o acesso à Internet através do DNS**: Ação que permite bloquear o acesso à Internet através do DNS para este cliente
- **Desbloquear todo o acesso à Internet através do DNS**: Ação que permite desbloquear o acesso à Internet através do DNS para este cliente

**Correspondência AdGuard** (Filtros > Regras de filtragem personalizadas > adicionar a regra: `||*^$client='NomeDoCliente',importante` em primeiro lugar)

![imagem](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Dados de acesso
-----------------------
- **Identificador(es)**: Cadeia que contém os identificadores atuais do cliente
- **Adicionar um identificador**: Ação que permite adicionar um identificador ao cliente (sem aspas à volta!!)
- **Remover um identificador**: Ação que permite remover um identificador do cliente (sem aspas à volta!!)

> **Atenção: se já existir noutro cliente, é necessário removê-lo primeiro deste cliente! O AdGuard não permite que dois clientes partilhem as mesmas credenciais (faz sentido ;))**

**Correspondência do AdGuard** (Definições > Definições do cliente > Editar cliente > Identificador):

![imagem](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
