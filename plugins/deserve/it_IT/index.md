---
layout: default
lang: it_IT
title: Plugin Mérite
description: Documentazione del plugin Mérite (deserve)
---

## Presentazione

Il plugin **Mérite** è un semaforo per Jeedom. Ogni dispositivo, chiamato «Meritevole», ha un contatore e un obiettivo. Scenari o azioni aggiungono punti (**Merito**) o ne tolgono (**Demerito**). Quando il contatore raggiunge l'obiettivo, il dispositivo diventa meritevole e vengono eseguite le sue azioni di merito. Quando torna sotto l'obiettivo, non lo è più e vengono eseguite le sue azioni di demerito.

Lo scopo è semplificare gli scenari. Invece di scrivere una condizione che deve conoscere lo stato di tutti gli elementi coinvolti, ogni scenario si limita ad aggiungere o togliere i propri punti. Tutta la logica di «cosa succede quando la soglia viene superata» è riunita in un unico punto: il dispositivo Meritevole.

## Configurazione del plugin

Il plugin non ha dipendenze né processi in background. È sufficiente attivarlo.

## Configurazione di un dispositivo

In **Plugins → Automazione → Mérite**, cliccate su **Aggiungi** e date un nome al vostro Meritevole.

### Impostazioni generali

- **Nome del dispositivo**, **Oggetto padre**, **Categoria**, **Attiva**, **Visibile**: impostazioni standard di Jeedom.
- **Reset**: se questa casella è spuntata, il contatore torna a 0 non appena l'obiettivo è raggiunto, subito dopo l'esecuzione delle azioni di merito. *È meritevole* torna quindi anch'esso a 0, **senza** eseguire le azioni di demerito. Ogni raggiungimento dell'obiettivo si comporta quindi come un impulso, adatto a un sistema di livelli o di ricompense.
- **Dove vengono utilizzati i comandi**: elenco degli scenari, delle viste, dei design, ecc. che utilizzano i comandi di questo dispositivo.

### Livelli

I livelli permettono di eseguire azioni **prima** di raggiungere l'obiettivo, ad esempio per avvisare che una manutenzione si avvicina.

- Ogni livello ha una **soglia in percentuale dell'obiettivo** (ad esempio 80%), una condizione facoltativa e delle azioni, come gli eventi descritti più sotto.
- Un livello viene eseguito quando la percentuale supera la sua soglia **in salita**. Se scende di nuovo sotto la soglia e poi risale, il livello viene eseguito di nuovo.
- Se più livelli vengono superati in una volta, vengono eseguiti dal più basso al più alto, e sempre prima delle azioni di merito.
- Poiché la soglia è espressa in percentuale, i livelli seguono automaticamente un cambio di obiettivo. Abbassare l'obiettivo può persino far superare un livello.
- È possibile che il valore superi il 100%, poiché può andare oltre l'obiettivo.

### Azioni di merito e di demerito

- Le **azioni di merito** vengono eseguite quando il contatore **raggiunge o supera** l'obiettivo (*È meritevole* passa da 0 a 1).
- Le **azioni di demerito** vengono eseguite quando il contatore **torna sotto** l'obiettivo (*È meritevole* passa da 1 a 0).

Le azioni vengono eseguite solo al **superamento** dell'obiettivo. Aggiungere punti a un dispositivo già meritevole non riesegue le azioni di merito.

Le azioni sono raggruppate in **eventi**:

- Ogni evento ha una **condizione** facoltativa. Se è falsa, l'intero evento viene ignorato. Se viene lasciata vuota, l'evento viene sempre eseguito.
- Ogni evento contiene una o più **azioni**. Per ciascuna di esse è possibile scegliere un comando di azione (pulsante "Elenco") o una parola chiave di scenario: messaggio, variabile, scenario, attesa, avviso… (pulsante "Parola chiave").
- È possibile disattivare un'azione senza eliminarla deselezionando la relativa casella.
- Gli eventi vengono eseguiti nell'ordine visualizzato, così come le azioni di ciascun evento. Le azioni possono essere riordinate utilizzando la maniglia.

## Comandi

| Comando | Tipo | Descrizione |
|---|---|---|
| **Valore** | info numerica | Valore attuale del contatore (mai negativo). |
| **Richiede** | info numerica | Obiettivo da raggiungere (100 per impostazione predefinita). |
| **È meritevole** | info binaria | 1 se Valore ≥ Richiede, 0 altrimenti. |
| **Percentuale dell'obiettivo** | info numerica (%) | Valore / Richiede × 100, arrotondato. Può superare il 100%. |
| **Mancante** | info numerica | Punti mancanti per raggiungere l'obiettivo (Richiede − Valore, minimo 0). |
| **Merito** | azione cursore | Aggiunge il valore del cursore al contatore. |
| **Demerito** | azione cursore | Sottrae il valore del cursore dal contatore (minimo 0). |
| **Deve richiedere** | azione cursore | Modifica l'obiettivo (minimo 1). |
| **Vincere** | azione | Porta direttamente il contatore al valore dell'obiettivo. |
| **Azzeramento** | azione | Riporta il contatore a 0. |

Note:

- Merito e Demerito senza valore, o con 0, non fanno nulla.
- I cursori del widget vanno da 0 a 100. Da uno scenario si può inviare un valore più grande (ad esempio *Deve richiedere* a 150).
- Se si abbassa l'obiettivo al di sotto del valore attuale, il valore viene riportato al nuovo obiettivo. Non viene ripristinato se successivamente si aumenta nuovamente l'obiettivo.
- *Azzeramento* e *Demerito* eseguono le azioni di demerito se il dispositivo era meritevole. *Vincere* esegue le azioni di merito se non lo era ancora.
- *È meritevole* può anche essere usato come trigger o condizione nei vostri scenari.

## Esempi di utilizzo

### Riduzione del carico elettrico

Si vuole evitare che troppi grandi consumatori funzionino contemporaneamente: forno, lavatrice, asciugatrice, lavastoviglie, colonnina di ricarica.

- Create un Meritevole «Grandi consumatori» con un obiettivo di **3**.
- Per ogni apparecchio, un piccolo scenario fa **Merito 1** quando la sua potenza supera una soglia e **Demerito 1** quando scende di nuovo. Si può ponderare: la colonnina di ricarica può contare 2.
- Azioni di merito: mettere in pausa la colonnina di ricarica, spegnere lo scaldabagno, inviare una notifica.
- Azioni di demerito: riattivare tutto.

Ogni dispositivo gestisce solo il proprio +1 e il proprio −1. L'aggiunta di un dispositivo non richiede la modifica degli altri scenari.

### Contatore di manutenzione

Per il filtro di un sistema di ventilazione meccanica controllata (VMC), di un addolcitore o di una cappa aspirante, oppure per il contenitore di un robot aspirapolvere.

- L'obiettivo è la soglia di manutenzione (ad esempio 50 cicli).
- A ogni ciclo, uno scenario fa **Merito**, eventualmente ponderato: ciclo corto +1, ciclo lungo +3.
- Un livello all'80% invia la notifica «Manutenzione necessaria a breve».
- Azioni di merito: notifica «Ricordati di sostituire il filtro». *È meritevole* resta a 1 finché la manutenzione non viene fatta, il che lo rende un promemoria persistente sulla dashboard.
- Dopo la manutenzione, un clic su **Azzeramento** dalla dashboard.

### Punti merito

- Ogni compito svolto dà punti (**Merito 10**, **Merito 20**…) tramite un pulsante, un'interazione o uno scenario.
- Una dimenticanza constatata toglie punti (**Demerito 5**).
- Obiettivo 100, con **Reset** spuntato: ogni raggiungimento dell'obiettivo attiva una ricompensa (accendere una presa, inviare una notifica…).
- Uno scenario settimanale fa **Azzeramento** per ripartire da zero.

## Registri

Il log `deserve` segnala, a livello **info**, ogni volta che viene raggiunto l'obiettivo. A livello **debug**, riporta inoltre in dettaglio ogni variazione di valore, ogni condizione valutata e ogni azione eseguita.
