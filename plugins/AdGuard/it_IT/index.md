---
layout: default
lang: it_IT
title: Plugin AdGuard Home
description: Documentazione del plugin AdGuard Home
---

Questo plugin consente di monitorare ed eseguire alcune azioni su AdGuard Home.

Configurazione del plugin
=======================

Dopo aver installato il plugin, è sufficiente attivarlo. Non è necessaria alcuna configurazione particolare

Configurazione delle apparecchiature
=============================

È possibile accedere alla configurazione dei dispositivi AdGuard dal menu
plugin e poi Monitoraggio. Qui troverete:

-   un pulsante per creare manualmente un dispositivo

-   un pulsante per visualizzare la configurazione del plugin

-   un pulsante che offre una panoramica completa di tutte le vostre apparecchiature in un determinato momento

-   Infine, qui sotto troverete l'elenco dei vostri dispositivi AdGuard Home e dei client collegati

Cliccando su uno dei vostri dispositivi, si accede alla pagina
configurazione del vostro impianto, che comprende 2 schede: "Impianto" e
comandi.

-   **Scheda "Attrezzature"**:

-   **Nome dell'apparecchio**: nome del vostro apparecchio

-   **Attiva**: consente di attivare il dispositivo

-   **Visibile**: lo rende visibile sulla dashboard

-   **Oggetto padre**: indica l'oggetto padre a cui appartiene l'apparecchio

**Solo per AdGuard**

-   **IP del server**: l'IP del server AdGuard Home.

> Se avete modificato la porta predefinita (80), potete inserire qui la vostra porta nel formato ip:porta

-   **Utente**: Utente di AdGuard Home.

-	**Password**: password dell'utente AdGuard Home.

-	**Aggiornamento automatico (cron)**: intervalli di verifica dei dati su AdGuard Home, 5 minuti per impostazione predefinita.

Una volta aggiunto AdGuard Home ed eseguito il backup dei dispositivi, i client rilevati in AdGuard Home vengono aggiunti come dispositivi separati.

Se in seguito **aggiungete un client**, questo verrà aggiunto **automaticamente durante la notte**; per forzare la sua aggiunta in Jeedom, **salvate nuovamente l'apparecchiatura AdGuard Home**.

Se in seguito **rimuovete un client**, questo verrà disattivato **automaticamente durante la notte**; per forzare la sua disattivazione in Jeedom, **salvate nuovamente l'apparecchiatura AdGuard Home**.

> NB: Un dispositivo di tipo **Client** deve essere **disattivato per poter essere eliminato**.

**Comandi dell'apparecchiatura AdGuard**
================================
- **Aggiorna**: Consente di aggiornare manualmente l'apparecchiatura oltre all'aggiornamento automatico
- **Online**: valore binario che indica se AdGuard risponde correttamente alle richieste
- **Aggiornamento AdGuard disponibile**: file binario che indica se è disponibile un aggiornamento
- **Aggiornamento AdGuard**: operazione che consente di aggiornare AdGuard (se è disponibile un aggiornamento)

Protezione globale
-----------------------
- **Stato protezione**: valore binario che indica lo stato della protezione globale
- **Attiva protezione**: azione che consente di attivare la protezione globale
- **Disattivare la protezione**: azione che consente di disattivare la protezione globale

> Novità: ora è possibile modificare la durata della disattivazione della protezione (come nell'interfaccia di AdGuardHome)

**Corrispondenza AdGuard**:

![immagine](https://user-images.githubusercontent.com/28622481/133206289-810d7a4d-9705-4923-9831-e8e78100f05b.png)

Filtro globale
-----------------------
- **Stato del filtro globale**: valore binario che indica lo stato del filtro globale
- **Attiva il filtro globale**: azione che consente di attivare il filtro globale
- **Disattiva il filtro globale**: azione che consente di disattivare il filtro globale

**Configurazione di AdGuard** (Impostazioni > Impostazioni generali > Blocca domini tramite filtri e file host):

![immagine](https://user-images.githubusercontent.com/28622481/133206778-015af02d-8039-4c78-9732-e048c41cfa21.png)

Sicurezza di navigazione globale
-----------------------
- **Stato della sicurezza di navigazione globale**: valore binario che indica lo stato della sicurezza di navigazione globale
- **Attiva la Sicurezza di navigazione globale**: azione che consente di attivare la Sicurezza di navigazione globale
- **Disattiva la Sicurezza di navigazione globale**: azione che consente di disattivare la Sicurezza di navigazione globale

**Impostazioni AdGuard** (Impostazioni > Impostazioni generali > Utilizza il servizio Sicurezza di navigazione di AdGuard):

![immagine](https://user-images.githubusercontent.com/28622481/133207227-8f9aa942-54c6-4048-8fa1-3711f4ca082c.png)

Controllo parentale globale
-----------------------
- **Stato del controllo parentale globale**: valore binario che indica lo stato del controllo parentale globale
- **Attiva il controllo parentale globale**: azione che consente di attivare il controllo parentale globale
- **Disattivare il controllo parentale globale**: azione che consente di disattivare il controllo parentale globale

**Impostazioni AdGuard** (Impostazioni > Impostazioni generali > Usa il controllo parentale di AdGuard):

![immagine](https://user-images.githubusercontent.com/28622481/133207419-bac0d204-c4fc-414d-b411-c7ec072ab514.png)

Ricerca globale sicura
-----------------------
- **Stato della ricerca sicura globale**: valore binario che indica lo stato della ricerca sicura globale
- **Attiva la Ricerca Sicura Globale**: azione che consente di attivare la Ricerca Sicura Globale
- **Disattiva la Ricerca sicura globale**: azione che consente di disattivare la Ricerca sicura globale

**Impostazioni AdGuard** (Impostazioni > Impostazioni generali > Rafforzare la ricerca sicura):

![immagine](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Servizi globali
-----------------------
- **Servizi bloccati**: Canale che indica i servizi bloccati a livello globale
- **Bloccare un servizio**: azione che consente di bloccare un servizio dall'elenco
- **Sbloccare un servizio**: azione che consente di sbloccare un servizio dall'elenco
- **Blocca tutti i servizi**: azione che consente di bloccare tutti i servizi presenti nell'elenco
- **Sblocca tutti i servizi**: azione che consente di sbloccare tutti i servizi presenti nell'elenco

**Impostazioni AdGuard** (Filtri > Servizi bloccati):

![immagine](https://user-images.githubusercontent.com/28622481/133207917-e813a4d1-42d2-491c-982a-ebabf6510383.png)

Internet bloccato tramite DNS
-----------------------
- **Stato "Internet bloccato tramite DNS"**: file binario che indica se Internet è stato bloccato tramite il DNS
- **Bloccare completamente Internet tramite DNS**: operazione che consente di bloccare Internet tramite il DNS
- **Sbloccare tutti i siti Internet tramite DNS**: operazione che consente di sbloccare Internet tramite il DNS

**Configurazione AdGuard** (Filtri > Regole di filtraggio personalizzate > aggiungi la regola: `||*^$important` per prima):

![immagine](https://user-images.githubusercontent.com/28622481/133210452-4ebbc8b0-836d-43a4-9db9-e01c2534679e.png)

Regola di filtraggio personalizzata
-----------------------
- **Aggiungi una regola di filtraggio personalizzata**: campo che consente di aggiungere per prima una regola di filtraggio personalizzata (ortografia corretta, senza virgolette)
- **Rimuovere una regola di filtraggio personalizzata**: campo che consente di rimuovere una regola di filtraggio personalizzata (ortografia corretta, senza virgolette)

Vedi [qui](https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists){:target="_blank" rel="noopener"}

**Impostazioni AdGuard** (Filtri > Regole di filtraggio personalizzate > aggiungere la regola indicata per prima)

Statistiche
-----------------------
- **Azzeramento statistiche**: consente di azzerare le statistiche
- **Richieste DNS**: indica il numero di richieste DNS elaborate nelle ultime 24 ore
- **Bloccati dai filtri**: indica il numero di richieste DNS bloccate dai filtri adblock e dagli elenchi di host bloccati
- **Tentativi di phishing tramite malware bloccati**: indica il numero di richieste DNS bloccate dal modulo Sicurezza di navigazione di AdGuard
- **Ricerche sicure forzate**: indica il numero di richieste DNS effettuate con la Ricerca sicura
- **Siti con contenuti per adulti bloccati**: indica il numero di siti con contenuti per adulti bloccati
- **Tempo medio di elaborazione**: indica il tempo medio (in millisecondi) necessario per elaborare una richiesta DNS

**Impostazioni AdGuard** (Impostazioni > Impostazioni generali > Configurazione delle statistiche > pulsante Cancella statistiche):

![immagine](https://user-images.githubusercontent.com/28622481/133211167-470e9959-bda7-4810-a02d-8d26363bb981.png)

**e** (Pannello di controllo > Statistiche generali):

![immagine](https://user-images.githubusercontent.com/28622481/133211276-6c24d23c-6647-4b5f-a26c-e5834bd1a657.png)

**Ordini di attrezzature per i clienti**
================================

Utilizzo delle impostazioni generali
--------------------------------
- **Stato "Utilizza impostazioni generali"**: valore binario che indica se è stata attivata l'opzione "Utilizza impostazioni generali"
- **Attiva "Usa impostazioni generali"**: azione che consente di attivare "Usa impostazioni generali"
- **Disattiva "Usa impostazioni generali"**: azione che consente di disattivare "Usa impostazioni generali"

**Configurazione di AdGuard** (Impostazioni > Impostazioni client > Modifica client > Impostazioni > Usa impostazioni generali (1)):

![immagine](https://user-images.githubusercontent.com/28622481/133217292-24f23ed8-8de2-492f-bd83-e9b90715de17.png)

Filtraggio
--------------------------------
- **Stato del filtro**: valore binario che indica lo stato del filtro
- **Attiva il filtro**: azione che consente di attivare il filtro
- **Disattiva il filtro**: azione che consente di disattivare il filtro

**Configurazione di AdGuard** (Impostazioni > Impostazioni client > Modifica client > Impostazioni > Blocca domini tramite filtri e file host (2))

Sicurezza di navigazione
-----------------------
- **Stato della sicurezza di navigazione**: valore binario che indica lo stato della sicurezza di navigazione
- **Attiva la Sicurezza di navigazione**: azione che consente di attivare la Sicurezza di navigazione
- **Disattiva la Sicurezza di navigazione**: azione che consente di disattivare la Sicurezza di navigazione

**Configurazione AdGuard** (Impostazioni > Impostazioni client > Modifica client > Impostazioni > Utilizza il servizio "Navigazione sicura" di AdGuard (3))

Controllo parentale
-----------------------
- **Stato Controllo genitori**: valore binario che indica lo stato del Controllo genitori
- **Attivare il controllo parentale**: azione che consente di attivare il controllo parentale
- **Disattivare il controllo parentale**: azione che consente di disattivare il controllo parentale

**Configurazione di AdGuard** (Impostazioni > Impostazioni client > Modifica client > Impostazioni > Utilizza il controllo parentale di AdGuard (4))

Ricerca sicura
-----------------------
- **Stato Ricerca sicura**: valore binario che indica lo stato della Ricerca sicura
- **Attiva la Ricerca sicura**: azione che consente di attivare la Ricerca sicura
- **Disattiva la Ricerca sicura**: azione che consente di disattivare la Ricerca sicura

**Configurazione AdGuard** (Impostazioni > Impostazioni client > Modifica client > Impostazioni > Rafforza la ricerca sicura (5))

Utilizzo dei servizi globali bloccati
--------------------------------
- **Stato "Utilizza i servizi bloccati globalmente"**: valore binario che indica se è stata attivata l'opzione "Utilizza i servizi bloccati globalmente"
- **Attiva "Utilizza i servizi bloccati globalmente"**: azione che consente di attivare "Utilizza i servizi bloccati globalmente"
- **Disattiva "Utilizza i servizi bloccati globalmente"**: azione che consente di disattivare "Utilizza i servizi bloccati globalmente"

**Configurazione di AdGuard** (Impostazioni > Impostazioni client > Modifica client > Blocca servizi specifici > Utilizza i servizi bloccati globalmente (1)):

![immagine](https://user-images.githubusercontent.com/28622481/133218452-cf994ad7-bf63-4dbd-b727-ff64339b7b31.png)

Servizi specifici
-----------------------
- **Servizi bloccati**: Canale che indica i servizi bloccati specificatamente per questo cliente
- **Bloccare un servizio**: azione che consente di bloccare un servizio dall'elenco specificatamente per quel cliente
- **Sbloccare un servizio**: azione che consente di sbloccare un servizio dall'elenco specificatamente per quel cliente

**Configurazione AdGuard** (Impostazioni > Impostazioni client > Modifica client > Blocca servizi specifici > Servizi (2))

- **Blocca tutti i servizi**: azione che consente di bloccare tutti i servizi presenti nell'elenco specificatamente per questo cliente
- **Sblocca tutti i servizi**: azione che consente di sbloccare tutti i servizi presenti nell'elenco specificatamente per questo cliente

**Impostazioni AdGuard** (Impostazioni > Impostazioni client > Modifica client > Blocca servizi specifici > Blocca tutto/Sblocca tutto (3))

Internet bloccato tramite DNS
-----------------------
- **Stato "Internet bloccato tramite DNS"**: valore binario che indica se Internet è stato bloccato tramite il DNS per questo cliente
- **Bloccare completamente Internet tramite DNS**: operazione che consente di bloccare Internet tramite il DNS per questo cliente
- **Sbloccare l'accesso completo a Internet tramite DNS**: operazione che consente di sbloccare l'accesso a Internet tramite il DNS per questo cliente

**Configurazione AdGuard** (Filtri > Regole di filtraggio personalizzate > aggiungi la regola: `||*^$client='NomeCliente',importante` per prima)

![immagine](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Dati di accesso
-----------------------
- **ID**: stringa contenente gli ID attuali del cliente
- **Aggiungi un identificativo**: azione che consente di aggiungere un identificativo al cliente (senza virgolette!!)
- **Rimuovere un identificativo**: azione che consente di rimuovere un identificativo dal cliente (senza virgolette!!)

> **Attenzione: se esiste già su un altro client, è necessario prima rimuoverlo da questo client! AdGuard non consente a due client di condividere le stesse credenziali (logico ;))**

**Dati di identificazione AdGuard** (Impostazioni > Impostazioni client > Modifica client > ID):

![immagine](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
