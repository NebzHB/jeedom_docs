---
layout: default
lang: it_IT
title: Plugin AdGuard Home - Registro delle modifiche
description: Registro delle modifiche del plugin AdGuard Home
---
Se non è specificato nulla, probabilmente si tratta di un piccolo aggiornamento ortografico o per la compatibilità con Jeedom V4.x

# Registro delle modifiche

## 26-11-2026
- Compatibile con AdGuard Home v1.0.0

## 12-11-2026
- Per la configurazione è necessario essere amministratore

## 30-01-2025
- Traduzione dei nomi dei comandi
- Correzione di un avviso PHP in assenza di regole utente
- (Grazie @TomiTomas): Aggiunta la durata di disattivazione della protezione (come in AdGuardHome)

## 07-10-2024
- Aggiunta del pulsante "Comunità" per ottenere assistenza più facilmente

## 12-08-2024
- Traduzioni e aggiornamento delle traduzioni in inglese, tedesco, spagnolo, italiano e portoghese

## 11-09-2023
- È richiesta la versione v0.107.37!
- Modifiche ai servizi bloccati a partire dalla versione v0.107.37

## 24-05-2023

- Modifiche relative ai nuovi elementi dell'API nella versione v0.107.28 (protezione abilitata + ricerca sicura)
- al momento non è possibile scegliere il motore di ricerca per la protezione Safesearch (è necessario??)
- al momento non è possibile impostare un intervallo di tempo per la disattivazione della protezione (è necessario con Jeedom? Dato che è possibile riattivarla tramite uno scenario o altro...)
- Correzione del comando Update
- Crittografia delle password AdGuard nel database di Jeedom
- **Richiede quindi almeno la versione v0.107.28 di AdGuard!**


## 14-11-2022

- Blocco/sblocco Internet e regole personalizzate (nelle versioni v0.107.14+), aggiornamento alla versione v0.107.17+
- È quindi necessaria una versione di AdGuard v0.107.17 o superiore!

## 04-11-2022

- A partire dalla versione v0.107.17, AdGuard supporta nuovi servizi (iCloud Private Relay, ecc.). Questa versione richiede l'elenco dei servizi ad AdGuard e aggiorna i comandi se necessario.

## 08-09-2022

- Aggiunta del servizio BiliBili disponibile nella versione v0.107.12
- Nessun errore se il file version.json non è più disponibile su AdGuard (a causa di un bug da parte loro)

## 28-06-2022

- Aggiunta del protocollo https per chi utilizza un proxy o simili

## 08-04-2021

- Aggiunta della versione attuale e della nuova versione nei comandi. Se al momento dell'aggiornamento è disponibile una nuova versione, AdGuard non mi invia il numero di versione precedente, quindi il campo risulterà vuoto... ma non appena si esegue l'aggiornamento, verrà modificato e tutto sarà a posto.
- Traduzione in inglese e spagnolo
- Correggi i collegamenti dei comandi all'azione "Blocca Internet tramite DNS"

## 21-09-2021

- Correggere se un dispositivo è già presente nella stessa stanza del cliente ed è disattivato

## 15-09-2021

- Inizializzazione

