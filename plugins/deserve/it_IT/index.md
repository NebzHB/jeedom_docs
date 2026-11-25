---
layout: default
lang: it_IT
title: Plugin Mérite
description: Documentazione del plugin Mérite (deserve)
---

## Presentazione

Il plugin **Merito** è un semaforo per Jeedom. Ogni dispositivo, denominato «Meritevole», possiede un contatore e un obiettivo. Gli scenari o le azioni aggiungono punti (**Merito**) o ne sottraggono (**Demerito**). Quando il contatore raggiunge l’obiettivo, il dispositivo diventa «meritevole» e vengono eseguite le sue azioni meritorie. Quando scende al di sotto dell’obiettivo, non è più «meritevole» e vengono eseguite le sue azioni demeritorie.

Il vantaggio è quello di semplificare gli scenari. Anziché scrivere una condizione che deve conoscere lo stato di tutti gli elementi coinvolti, ogni scenario si limita ad aggiungere o rimuovere i propri punti. Tutta la logica relativa a «cosa succede quando viene superata la soglia» è raggruppata in un unico punto: il dispositivo Méritant.

## Configurazione del plugin

Il plugin non ha dipendenze né processi in background. È sufficiente attivarlo.

## Configurazione di un dispositivo

In **Plugins → Automazione → Merito**, clicca su **Aggiungi** e assegna un nome al tuo Meritevole.

### Impostazioni generali

- **Nome del dispositivo**, **Oggetto padre**, **Categoria**, **Attiva**, **Visibile**: impostazioni standard di Jeedom.
- **Azzeramento**: se questa casella è spuntata, il contatore torna a 0 non appena l'obiettivo viene raggiunto, subito dopo l'esecuzione delle azioni meritevoli. Anche *È meritevole* torna quindi a 0, **senza** avviare le azioni demeritevoli. Ogni volta che si supera l'obiettivo, si verifica quindi un impulso, il che si adatta bene a un sistema a livelli o a ricompense.
- **Dove vengono utilizzati i comandi**: elenco degli scenari, delle viste, dei design, ecc. che utilizzano i comandi di questo dispositivo.

### Livelli

I livelli consentono di attivare delle azioni **prima** di raggiungere l'obiettivo, ad esempio per avvisare che si avvicina un intervento di manutenzione.

- Ogni livello ha una **soglia espressa in percentuale dell'obiettivo** (ad esempio l'80%), una condizione facoltativa e delle azioni, come gli eventi descritti di seguito.
- Un livello viene attivato quando la percentuale supera la soglia **in aumento**. Se scende nuovamente al di sotto della soglia e poi risale, il livello viene attivato nuovamente.
- Se vengono superati più livelli contemporaneamente, questi vengono eseguiti dal più basso al più alto, e sempre prima delle azioni meritevoli.
- Poiché la soglia è espressa in percentuale, i livelli si adeguano automaticamente a una modifica dell'obiettivo. Abbassando l'obiettivo è possibile, tra l'altro, superare un livello.
- È possibile che il valore superi il 100%, poiché può andare oltre l'obiettivo.

### Azioni di merito e di demerito

- Le **azioni di merito** vengono eseguite quando il contatore **raggiunge o supera** l'obiettivo (*È meritevole* passa da 0 a 1).
- Le **azioni di demerito** vengono eseguite quando il contatore **torna sotto** l'obiettivo (*È meritevole* passa da 1 a 0).

Le azioni vengono eseguite solo al **superamento** dell'obiettivo. Aggiungere punti a un'attrezzatura che ne ha già diritto non riattiva le azioni meritevoli.

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

- I meriti e i demeriti senza valore, o con valore pari a 0, non hanno alcun effetto.
- I cursori del widget vanno da 0 a 100. Da uno scenario è possibile inviare un valore più alto (ad esempio *Doit Nécessiter* a 150).
- Se si abbassa l'obiettivo al di sotto del valore attuale, il valore viene riportato al nuovo obiettivo. Non viene ripristinato se successivamente si aumenta nuovamente l'obiettivo.
- *Azzeramento* e *Demerito* eseguono le azioni di demerito se il dispositivo era meritevole. *Vincere* esegue le azioni di merito se non lo era ancora.
- *È meritevole* può anche essere usato come trigger o condizione nei vostri scenari.

## Esempi di utilizzo

### Riduzione del carico elettrico

Si vuole evitare che troppi elettrodomestici ad alto consumo funzionino contemporaneamente: forno, lavatrice, asciugatrice, lavastoviglie, stazione di ricarica.

- Crea un Merito «Grandi consumatori» con un obiettivo pari a **3**.
- Per ogni dispositivo, un piccolo scenario assegna **1 punto** quando la sua potenza supera una soglia e **-1 punto** quando scende al di sotto di essa. È possibile applicare una ponderazione: il terminale può valere 2 punti.
- Azioni di merito: mettere in pausa la colonnina di ricarica, spegnere lo scaldabagno, inviare una notifica.
- Azioni di demerito: riattivare tutto.

Ogni dispositivo gestisce solo il proprio +1 e il proprio −1. L'aggiunta di un dispositivo non richiede la modifica degli altri scenari.

### Contatore di manutenzione

Per il filtro di un sistema di ventilazione meccanica controllata (VMC), di un addolcitore o di una cappa aspirante, oppure per il contenitore di un robot aspirapolvere.

- L'obiettivo è la soglia di manutenzione (ad esempio 50 cicli).
- Ad ogni ciclo, uno scenario ottiene **Merito**, eventualmente ponderato: ciclo breve +1, ciclo lungo +3.
- Quando il livello scende all'80%, viene inviata una notifica «Manutenzione necessaria a breve».
- Azioni di merito: notifica «Ricordati di sostituire il filtro». *È meritevole* resta a 1 finché la manutenzione non viene fatta, il che lo rende un promemoria persistente sulla dashboard.
- Dopo la manutenzione, clicca su **Azzeramento** dalla dashboard.

### Punti di merito

- Ogni attività completata assegna dei punti (**Merito 10**, **Merito 20**…) tramite un pulsante, un'interazione o uno scenario.
- Ogni dimenticanza riscontrata comporta una penalità (**5 punti di penalità**).
- Obiettivo a 100, con l'opzione **Azzeramento** selezionata: ogni livello raggiunto attiva una ricompensa (accendere una presa, inviare una notifica…).
- Uno scenario settimanale esegue il **reset** per ricominciare da zero.

## Registri

Il log `deserve` segnala, a livello **info**, ogni volta che viene raggiunto l'obiettivo. A livello **debug**, riporta inoltre in dettaglio ogni variazione di valore, ogni condizione valutata e ogni azione eseguita.
