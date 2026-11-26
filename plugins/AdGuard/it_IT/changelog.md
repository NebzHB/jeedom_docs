---
layout: default
lang: it_IT
title: Plugin AdGuard Home - Registro delle modifiche
description: Registro delle modifiche del plugin AdGuard Home
---
Se non è specificato nulla, probabilmente si tratta di un piccolo aggiornamento ortografico o per la compatibilità con Jeedom V4.x

# Registro delle modifiche

## In versione beta
- Nuovo widget per il dispositivo AdGuard Home (dashboard e versione mobile), ispirato alla dashboard di AdGuard Home: protezione con menu delle durate di pausa e conto alla rovescia, statistiche, icone cliccabili (filtraggio, sicurezza di navigazione, controllo parentale, ricerca sicura, Internet bloccato)
- Nuovo widget per i dispositivi dei clienti (dashboard e dispositivi mobili): Internet autorizzato o bloccato tramite pulsante, icone cliccabili (impostazioni generali, filtraggio, sicurezza di navigazione, controllo parentale, ricerca sicura, servizi bloccati in generale), credenziali e servizi bloccati
- Widget: impostazioni tramite interruttori con tooltip, azioni integrate su una riga (servizi, gruppi, regole, credenziali, test di dominio con relativo risultato, manutenzione), aggiornamento di AdGuard Home dal badge del widget. Vedi la [documentazione beta](index-beta#widgets-en-beta)
- Widget: servizi bloccati visualizzati sotto forma di icone, sia sul server che sui client
- Elenco dei servizi con icone, funzione di ricerca e servizi raggruppati per categoria; selezionando un gruppo si blocca o sblocca l'intero gruppo
- Widget: conferma prima di disattivare la connessione a Internet, disattivare il filtro o il controllo parentale, bloccare o sbloccare tutti i servizi e prima delle operazioni di manutenzione (cache DNS, filtri, statistiche)
- Widget: larghezza minima di 320 px sulla dashboard con layout adattivo, a tutta larghezza sui dispositivi mobili
- Widget: altezza automatica in base al contenuto, con un'opzione «Altezza del widget: fissa» sul dispositivo per mantenere quella della modalità di modifica
- Nuova informazione «Pausa rimanente»: tempo rimanente (in secondi) prima della ripresa della protezione
- Nuove azioni «Svuota la cache DNS» e «Aggiorna i filtri»
- Nuova azione «Verifica un dominio» (e l'informazione «Risultato della verifica del dominio») sul dispositivo AdGuard Home, e «Verifica un dominio per questo client» sui client
- Nuove azioni «Blocca un gruppo di servizi» e «Sblocca un gruppo di servizi», globali e per cliente (AdGuard Home v0.107.68 o superiore)
- La pianificazione dei servizi bloccati definita in AdGuard Home non viene più cancellata quando si blocca o si sblocca un servizio da Jeedom
- Ricerca sicura (globale e per cliente): cambia solo lo stato (attivato/disattivato), i motori di ricerca selezionati in AdGuard Home vengono mantenuti (Ecosia inclusa)
- La sicurezza di navigazione e il controllo parentale utilizzano le chiamate dell'API più recente di AdGuard Home, con il ripiego sulle chiamate precedenti per le versioni più vecchie
- Le operazioni «Aggiorna filtri» e «Aggiornamento AdGuard» attendono fino a 120 s la risposta da AdGuard Home (in precedenza, il comando falliva e lo stato «Online» passava a 0)
- Affidabilità: le azioni visualizzano un messaggio chiaro quando AdGuard Home non risponde, quando il client non è raggiungibile o quando la regola è vuota, invece di fallire in silenzio. Le regole personalizzate non possono più essere cancellate per errore e bloccare due volte Internet non crea più un duplicato
- Correzione dei clienti il cui nome contiene un trattino
- Correzione del rilevamento degli errori di rete (PHP 8)
- La modifica di un cliente invia ad AdGuard Home solo i campi modificabili
- Correzione dell'errore «globlaux» nei nomi dei comandi cliente («Utilizza i servizi globali bloccati»)
- Testi di aiuto dei comandi tradotti

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

