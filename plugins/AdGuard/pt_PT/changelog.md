---
layout: default
lang: pt_PT
title: Plugin AdGuard Home - Registo de alterações
description: Registo de alterações do plugin AdGuard Home
---
Se não for indicado nada, trata-se provavelmente de uma pequena atualização ortográfica ou para compatibilidade com o Jeedom V4.x

# Registo de alterações

## Em fase beta
- Novo widget para o equipamento AdGuard Home (painel de controlo e versão móvel), inspirado no painel de controlo do AdGuard Home: proteção com menu de tempos de pausa e contagem regressiva, estatísticas, botões clicáveis (filtragem, segurança de navegação, controlo parental, pesquisa segura, Internet bloqueada)
- Novo widget para os equipamentos do cliente (painel de controlo e dispositivo móvel): Internet autorizada ou bloqueada com botão, ícones clicáveis (parâmetros gerais, filtragem, segurança de navegação, controlo parental, pesquisa segura, serviços bloqueados em geral), credenciais e serviços bloqueados
- Widgets: configurações em interruptores com balão de informação, ações integradas numa única linha (serviços, grupos, regras, credenciais, teste de domínio com o respetivo resultado, manutenção), atualização do AdGuard Home a partir do ícone do widget. Consulte a [documentação beta](index-beta#widgets-en-beta)
- Widgets: serviços bloqueados apresentados sob a forma de ícones, tanto no servidor como nos clientes
- Lista de serviços com ícones, pesquisa e serviços organizados por grupo; ao selecionar um grupo, todo o grupo fica bloqueado ou desbloqueado
- Widgets: confirmação antes de desligar a Internet, desativar a filtragem ou o controlo parental, bloquear ou desbloquear todos os serviços e antes das ações de manutenção (cache DNS, filtros, estatísticas)
- Widgets: largura mínima de 320 px no painel de controlo com layout adaptável, largura total em dispositivos móveis
- Widgets: altura automática consoante o conteúdo, com uma opção «Altura do widget: Fixa» no equipamento para manter a altura do modo de edição
- Nova informação «Pausa restante»: tempo restante (em segundos) até ao reinício da proteção
- Novas ações «Limpar a cache do DNS» e «Atualizar os filtros»
- Nova ação «Testar um domínio» (e a informação «Resultado do teste do domínio») no equipamento AdGuard Home, e «Testar um domínio para este cliente» nos clientes
- Novas ações «Bloquear um grupo de serviços» e «Desbloquear um grupo de serviços», globais e por cliente (AdGuard Home v0.107.68 ou superior)
- A programação de serviços bloqueados definida no AdGuard Home já não é apagada quando se bloqueia ou desbloqueia um serviço a partir do Jeedom
- Pesquisa segura (global e do cliente): apenas o estado ativado/desativado muda; os motores de busca selecionados no AdGuard Home são mantidos (incluindo o Ecosia)
- A segurança de navegação e o controlo parental utilizam as chamadas da API mais recente do AdGuard Home, recorrendo às chamadas antigas para as versões mais antigas
- As opções «Atualizar filtros» e «Atualização do AdGuard» aguardam até 120 s pela resposta do AdGuard Home (anteriormente, o comando falhava e o valor de «Online» passava a 0)
- Fiabilidade: as ações apresentam uma mensagem clara quando o AdGuard Home não responde, quando o cliente não é encontrado ou quando a regra está vazia, em vez de falharem silenciosamente. As regras personalizadas já não podem ser apagadas por engano, e bloquear duas vezes o acesso à Internet já não cria duplicados
- Correção dos clientes cujo nome contém um traço
- Correção da deteção de erros de rede (PHP 8)
- A alteração de um cliente passa a enviar apenas os campos editáveis para o AdGuard Home
- Correção do erro «globlaux» nos nomes dos comandos do cliente («Utilizar os serviços globais bloqueados»)
- Textos de ajuda dos comandos traduzidos

## 26-11-2026
- Compatível com o AdGuard Home v1.0.0

## 12-11-2026
- A configuração requer que seja administrador

## 30-01-2025
- Tradução dos nomes dos comandos
- Correção de um aviso PHP caso não existam regras de utilizador
- (Obrigado @TomiTomas): Adicionada a duração da desativação da proteção (tal como no AdGuardHome)

## 07-10-2024
- Adicionado o botão «Comunidade» para obter ajuda mais facilmente

## 12-08-2024
- Traduções e atualização das traduções em inglês, alemão, espanhol, italiano e português

## 11-09-2023
- É obrigatória a versão v0.107.37!
- Alterações nos serviços bloqueados a partir da versão v0.107.37

## 24-05-2023

- Alterações relativas aos novos elementos da API na versão v0.107.28 (proteção ativada + pesquisa segura)
- De momento, não é possível escolher o motor de busca da proteção Safesearch (será necessário??)
- De momento, não é possível definir um horário para a desativação da proteção (será que isso é necessário com o Jeedom? Já que é possível reativá-la através de um cenário ou de outra forma...)
- Correção do comando «Update»
- Encriptação das suas palavras-passe do AdGuard na base de dados do Jeedom
- **Requer, portanto, uma versão do AdGuard v0.107.28, no mínimo!**


## 14-11-2022

- Corrigir bloqueio/desbloqueio da Internet e regras personalizadas (nas versões v0.107.14+), atualização para v0.107.17+
- Requer, portanto, uma versão do AdGuard v0.107.17, no mínimo!

## 04-11-2022

- Desde a versão v0.107.17, o AdGuard suporta novos serviços (iCloud Private Relay, etc.). Esta versão solicita a lista de serviços ao AdGuard e atualiza os comandos, se necessário.

## 08-09-2022

- Adicionado o serviço BiliBili, disponível na versão v0.107.12
- Já não ocorre o erro se o ficheiro version.json já não estiver disponível no AdGuard (devido a um bug da parte deles)

## 28-06-2022

- Adicionado o protocolo https para quem utilize um proxy ou outro serviço semelhante

## 08-04-2021

- Adicionar a versão atual e a nova versão aos comandos. Se houver uma nova versão no momento da atualização, o AdGuard não me envia o número da versão anterior, pelo que ficará em branco... mas assim que efetuar a atualização, será alterado e, a partir daí, estará tudo em ordem.
- Tradução para o inglês e para o espanhol
- Corrigir ligações de comandos para a ação «Bloquear a Internet através do DNS»

## 21-09-2021

- Corrigir se já existir um equipamento na mesma divisão que o cliente e este estiver desativado

## 15-09-2021

- Inicialização

