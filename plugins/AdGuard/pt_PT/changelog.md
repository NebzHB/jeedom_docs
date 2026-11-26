---
layout: default
lang: pt_PT
title: Plugin AdGuard Home - Registo de alterações
description: Registo de alterações do plugin AdGuard Home
---
Se não for indicado nada, trata-se provavelmente de uma pequena atualização ortográfica ou para compatibilidade com o Jeedom V4.x

# Registo de alterações

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

