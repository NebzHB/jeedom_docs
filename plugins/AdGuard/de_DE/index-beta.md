---
layout: default
lang: de_DE
title: AdGuard Home-Plugin
description: Dokumentation zum AdGuard Home-Plugin
---

Mit diesem Plugin können Sie Ihr AdGuard Home überwachen und bestimmte Aktionen ausführen.

Einrichtung des Plugins
=======================

Nach der Installation des Plugins müssen Sie es lediglich aktivieren. Es sind keine besonderen Einstellungen erforderlich.

Konfiguration der Geräte
=============================

Die Konfiguration der AdGuard-Geräte ist über das Menü zugänglich
Plugins und dann „Monitoring“. Hier finden Sie:

-   Eine Schaltfläche zum manuellen Anlegen eines Geräts

-   Eine Schaltfläche zum Anzeigen der Plugin-Konfiguration

-   Eine Schaltfläche, die Ihnen zu jedem Zeitpunkt einen Überblick über alle Ihre Geräte verschafft

-   Und ganz unten finden Sie die Liste Ihrer AdGuard Home-Geräte und der damit verbundenen Clients

Wenn Sie auf eines Ihrer Geräte klicken, gelangen Sie auf die Seite
Konfiguration Ihrer Geräte mit 2 Registerkarten: „Geräte“ und
Steuerungen.

-   **Registerkarte „Ausstattung“**:

-   **Gerätename**: Name Ihres Geräts

-   **Aktivieren**: Damit können Sie Ihre Geräte aktivieren

-   **Sichtbar**: Macht es auf dem Dashboard sichtbar

-   **Übergeordnetes Objekt**: Gibt das übergeordnete Objekt an, zu dem das Gerät gehört

-   **Widget-Höhe** (in der Beta-Version): Standardmäßig passt sich die Höhe des Widgets seinem Inhalt an. Aktivieren Sie **Fest (wie im Bearbeitungsmodus)**, um die im Bearbeitungsmodus des Dashboards eingestellte Höhe beizubehalten.

**Nur für AdGuard**

-   **IP-Adresse des Servers**: Die IP-Adresse des AdGuard Home-Servers.

> Wenn Sie den Standardport (80) geändert haben, können Sie Ihren Port hier in der Form „ip:port“ hinzufügen.

-   **Benutzer**: AdGuard Home-Benutzer.

-	**Passwort**: Passwort des AdGuard Home-Benutzers.

-	**Automatische Aktualisierung (cron)**: Intervalle zur Überprüfung der Daten auf AdGuard Home, standardmäßig 5 Minuten.

Sobald AdGuard Home hinzugefügt und die Geräte gesichert wurden, werden die in AdGuard Home gefundenen Clients als separate Geräte hinzugefügt.

Wenn Sie später **einen Client hinzufügen**, wird dieser **automatisch über Nacht** hinzugefügt. Um die Hinzufügung in Jeedom zu erzwingen, **speichern Sie die AdGuard Home-Geräte erneut**.

Wenn Sie einen **Client** anschließend **entfernen**, wird dieser **automatisch über Nacht** deaktiviert. Um die Deaktivierung in Jeedom zu erzwingen, **speichern Sie das AdGuard Home-Gerät erneut**.

> Hinweis: Ein Gerät vom Typ **Client** muss **deaktiviert sein, damit es gelöscht werden kann**.

**Bestellungen für AdGuard-Produkte**
================================
- **Aktualisieren**: Ermöglicht die manuelle Aktualisierung der Geräte zusätzlich zur automatischen Aktualisierung
- **Online**: Binärwert, der angibt, ob AdGuard korrekt auf Anfragen reagiert
- **AdGuard-Update verfügbar**: Binärdatei, die angibt, ob ein Update verfügbar ist
- **AdGuard aktualisieren**: Aktion zum Aktualisieren von AdGuard (sofern ein Update verfügbar ist)
- **DNS-Cache leeren** (Beta): Aktion zum Leeren des DNS-Caches von AdGuard Home
- **Filter aktualisieren** (Beta): Aktion, mit der die Aktualisierung der Filterlisten erzwungen werden kann

> Die Aktualisierung von AdGuard und der Filter kann einige Zeit in Anspruch nehmen: Das Plugin wartet bis zu 120 Sekunden auf die Antwort von AdGuard Home.

Widgets (in der Beta-Phase)
-----------------------
Die AdGuard Home- und Client-Anwendungen verfügen über ein eigenes Widget (Dashboard und Mobilversion), das vom AdGuard Home-Dashboard inspiriert ist und in Echtzeit aktualisiert wird.

**AdGuard Home-Geräte-Widget**

- **Schutz**: Status und Schalter. Ist der Schutz aktiv, öffnet ein Klick das Menü für die Pausenzeiten. Während einer Pause wird die verbleibende Zeit bis zur Wiederaufnahme heruntergezählt.
- **Statistiken**: DNS-Anfragen, durch Filter blockierte Anfragen, Bedrohungen und nicht jugendfreie Inhalte (mit prozentualem Anteil an der Gesamtzahl), erzwungene sichere Suchanfragen und durchschnittliche Bearbeitungszeit.
- **Einstellungen** über die grün/grauen Schalter: Filterung, Internetsicherheit, Kindersicherung und sichere Suche. Der Tooltip zeigt an, was durch einen Klick ausgelöst wird. Über die rote Schaltfläche „Internet gesperrt“ kann die Internetverbindung für das gesamte Netzwerk unterbrochen oder wiederhergestellt werden.
- **Gesperrte Dienste** werden als Symbole angezeigt (der vollständige Name ist im Tooltip zu finden).
- **Aktionen in einer Zeile**: Dienste und Dienstgruppen, benutzerdefinierte Filterregeln, Domain-Test mit Ergebnis sowie Wartungsmaßnahmen (DNS-Cache leeren, Filter aktualisieren, Statistiken zurücksetzen).
- **Fußzeile des Widgets**: Online-Status, Version, Update-Symbol (ein Klick startet das Update von AdGuard Home nach Bestätigung), Schaltfläche „Aktualisieren“ und ein Fenster mit den anderen sichtbaren Werten.

**Widget für Kundengeräte**

- **Internet**: „Zugelassen“ oder „Über DNS gesperrt“, mit einem Schalter, der das Internet für diesen Kunden sperrt oder freigibt.
- **Einstellungen** in Schaltflächen: Allgemeine Einstellungen, Filterung, Browsersicherheit, Kindersicherung, sichere Suche und allgemeine Dienste. Wenn der Nutzer die allgemeinen Einstellungen (oder die allgemein gesperrten Dienste) befolgt, werden seine eigenen Einstellungen (oder seine Dienstliste) ausgegraut und mit einem entsprechenden Hinweis versehen.
- **Anmeldedaten** und **gesperrte Dienste** des Kunden (als Symbole).
- **Aktionen auf einer Leitung**: Dienste und Dienstgruppen, Kennungen, Domänentest mit Ergebnis.

**Liste der Dienste**

Die Auswahlliste der Dienste zeigt das Symbol jedes Dienstes an, bietet eine Suchfunktion und ordnet die Dienste nach Gruppen an (Kategorie im Kopfbereich, darunter eingerückte Dienste). Durch Auswahl einer Gruppe („gesamte Gruppe“) werden alle darin enthaltenen Dienste gesperrt oder entsperrt. Für Gruppen ist mindestens AdGuard Home v0.107.68 erforderlich: Bei einer älteren Version enthält die Liste keine Gruppen.

**Bestätigungen**

Vor Maßnahmen, die den Schutz verringern oder nicht ohne Weiteres rückgängig gemacht werden können, wird eine Bestätigung angefordert: Internetverbindung unterbrechen (für einen Client oder das gesamte Netzwerk), Filterung oder Kindersicherung deaktivieren, alle Dienste sperren oder entsperren, den DNS-Cache leeren, Filter aktualisieren, Statistiken zurücksetzen und AdGuard Home aktualisieren.

**Größe des Widgets**

- Auf dem Dashboard ist das Widget mindestens 320 px breit. Ist es schmaler, werden die Schalter in einer Spalte und die Schaltflächen in einer Zeile angezeigt.
- Auf Mobilgeräten nimmt das Widget die gesamte Bildschirmbreite ein.
- Die Höhe richtet sich nach dem Inhalt des Widgets. Um die im Bearbeitungsmodus des Dashboards festgelegte Höhe beizubehalten, aktivieren Sie in den Geräteeinstellungen das Kontrollkästchen **Widget-Höhe: Fest (wie im Bearbeitungsmodus)**.

Befehle, die das Widget nicht kennt, bleiben im Jeedom-Widget erhalten.

Umfassender Schutz
-----------------------
- **Schutzstatus**: Binärwert, der den Status des globalen Schutzes angibt
- **Schutz aktivieren**: Aktion zum Aktivieren des globalen Schutzes
- **Schutz deaktivieren**: Aktion zum Deaktivieren des globalen Schutzes
- **Verbleibende Pause** (in der Beta-Phase): Verbleibende Zeit (in Sekunden) bis zur Wiederaufnahme des Schutzes, wenn dieser für einen bestimmten Zeitraum deaktiviert wurde

> Neu: Sie können nun die Dauer festlegen, für die der Schutz deaktiviert ist (wie in der AdGuardHome-Benutzeroberfläche).

**AdGuard-Korrespondenz**:

![Bild](https://user-images.githubusercontent.com/28622481/133206289-810d7a4d-9705-4923-9831-e8e78100f05b.png)

Globale Filterung
-----------------------
- **Status der globalen Filterung**: Binärwert, der den Status der globalen Filterung angibt
- **Globale Filterung aktivieren**: Aktion zum Aktivieren der globalen Filterung
- **Globale Filterung deaktivieren**: Aktion zum Deaktivieren der globalen Filterung

**AdGuard-Einstellungen** (Einstellungen > Allgemeine Einstellungen > Domänen mithilfe von Filtern und Hosts-Dateien blockieren):

![Bild](https://user-images.githubusercontent.com/28622481/133206778-015af02d-8039-4c78-9732-e048c41cfa21.png)

Allgemeine Sicherheit beim Surfen
-----------------------
- **Status der globalen Navigationssicherheit**: Binärwert, der den Status der globalen Navigationssicherheit angibt
- **Globale Browsersicherheit aktivieren**: Aktion zum Aktivieren der globalen Browsersicherheit
- **Globale Browsersicherheit deaktivieren**: Aktion zum Deaktivieren der globalen Browsersicherheit

**AdGuard-Einstellungen** (Einstellungen > Allgemeine Einstellungen > AdGuard-Dienst „Sicheres Surfen“ verwenden):

![Bild](https://user-images.githubusercontent.com/28622481/133207227-8f9aa942-54c6-4048-8fa1-3711f4ca082c.png)

Umfassende Kindersicherung
-----------------------
- **Status der globalen Kindersicherung**: Binärwert, der den Status der globalen Kindersicherung angibt
- **Globale Kindersicherung aktivieren**: Aktion zum Aktivieren der globalen Kindersicherung
- **Globale Kindersicherung deaktivieren**: Aktion zum Deaktivieren der globalen Kindersicherung

**AdGuard-Einstellungen** (Einstellungen > Allgemeine Einstellungen > AdGuard-Kindersicherung verwenden):

![Bild](https://user-images.githubusercontent.com/28622481/133207419-bac0d204-c4fc-414d-b411-c7ec072ab514.png)

Sichere globale Suche
-----------------------
- **Status der globalen sicheren Suche**: Binärwert, der den Status der globalen sicheren Suche angibt
- **Globale sichere Suche aktivieren**: Aktion zum Aktivieren der globalen sicheren Suche
- **Globale sichere Suche deaktivieren**: Aktion zum Deaktivieren der globalen sicheren Suche

> Es wird lediglich der Status „aktiviert/deaktiviert“ geändert: Die in AdGuard Home ausgewählten Suchmaschinen bleiben erhalten. Ist zum Zeitpunkt der Aktivierung keine Suchmaschine ausgewählt, werden alle ausgewählt.

**AdGuard-Einstellungen** (Einstellungen > Allgemeine Einstellungen > Sichere Suche verstärken):

![Bild](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Globale Dienstleistungen
-----------------------
- **Gesperrte Dienste**: Kanal, der die global gesperrten Dienste anzeigt
- **Einen Dienst sperren**: Aktion zum Sperren eines Dienstes aus der Liste
- **Einen Dienst freischalten**: Aktion zum Freischalten eines Dienstes aus der Liste
- **Alle Dienste sperren**: Aktion zum Sperren aller Dienste in der Liste
- **Alle Dienste freischalten**: Aktion zum Freischalten aller Dienste in der Liste
- **Eine Dienstgruppe sperren** (in der Beta-Phase): Aktion zum Sperren aller Dienste einer Gruppe (Dropdown-Liste)
- **Eine Dienstgruppe freischalten** (in der Beta-Phase): Aktion zum Freischalten aller Dienste einer Gruppe (Dropdown-Liste)

> Für die Dienstgruppen ist mindestens AdGuard Home v0.107.68 erforderlich.

> Der in AdGuard Home festgelegte Zeitplan für gesperrte Dienste bleibt erhalten, wenn Sie Dienste über Jeedom sperren oder entsperren.

**AdGuard-Einstellungen** (Filter > Blockierte Dienste):

![Bild](https://user-images.githubusercontent.com/28622481/133207917-e813a4d1-42d2-491c-982a-ebabf6510383.png)

Internet über DNS gesperrt
-----------------------
- **Status „Internet über DNS gesperrt“**: Binärwert, der angibt, ob das Internet über das DNS gesperrt wurde
- **Das gesamte Internet über DNS sperren**: Aktion zum Sperren des Internets über das DNS
- **Das gesamte Internet über DNS freischalten**: Aktion zum Freischalten des Internets über DNS

**AdGuard-Konfiguration** (Filter > Benutzerdefinierte Filterregeln > Hinzufügen der Regel: `||*^$important` an erster Stelle):

![Bild](https://user-images.githubusercontent.com/28622481/133210452-4ebbc8b0-836d-43a4-9db9-e01c2534679e.png)

Benutzerdefinierte Filterregel
-----------------------
- **Benutzerdefinierte Filterregel hinzufügen**: Feld zum Hinzufügen einer benutzerdefinierten Filterregel an erster Stelle (korrekte Schreibweise, ohne Anführungszeichen)
- **Eine benutzerdefinierte Filterregel entfernen**: Feld zum Entfernen einer benutzerdefinierten Filterregel (Rechtschreibung muss korrekt sein, keine Anführungszeichen)

Siehe [hier](https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists){:target="_blank" rel="noopener"}

**AdGuard-Einstellungen** (Filter > Benutzerdefinierte Filterregeln > die angegebene Regel an erster Stelle hinzufügen)

Eine Domain testen (in der Beta-Phase)
-----------------------
- **Domain testen** (in der Beta-Phase): Aktion (Eingabefeld), mit der überprüft werden kann, ob eine Domain gemäß den globalen Einstellungen gesperrt ist oder nicht
- **Ergebnis des Domain-Tests** (in der Beta-Phase): Zeichenfolge mit dem Ergebnis des letzten Tests, zum Beispiel `example.com: Durch einen Filter blockiert (Regel: ||example.com^)`

Statistiken
-----------------------
- **Statistiken zurücksetzen**: Hiermit können Sie die Statistiken auf Null zurücksetzen
- **DNS-Anfragen**: Gibt die Anzahl der DNS-Anfragen an, die in den letzten 24 Stunden bearbeitet wurden
- **Durch Filter blockiert**: Gibt die Anzahl der DNS-Anfragen an, die durch Adblock-Filter und Host-Sperrlisten blockiert wurden
- **Blockierte Malware-Phishing-Versuche**: Gibt die Anzahl der DNS-Anfragen an, die vom AdGuard-Modul „Browser-Sicherheit“ blockiert wurden
- **Erzwungene sichere Suchanfragen**: Gibt die Anzahl der DNS-Anfragen an, die mit der sicheren Suche durchgeführt wurden
- **Gesperrte Websites mit nicht jugendfreien Inhalten**: Gibt die Anzahl der gesperrten Websites mit nicht jugendfreien Inhalten an
- **Durchschnittliche Bearbeitungszeit**: Gibt die durchschnittliche Zeit (in Millisekunden) an, die für die Bearbeitung einer DNS-Anfrage benötigt wird.

**AdGuard-Einstellungen** (Einstellungen > Allgemeine Einstellungen > Statistiken konfigurieren > Schaltfläche „Statistiken löschen“):

![Bild](https://user-images.githubusercontent.com/28622481/133211167-470e9959-bda7-4810-a02d-8d26363bb981.png)

**und** (Dashboard > Allgemeine Statistiken):

![Bild](https://user-images.githubusercontent.com/28622481/133211276-6c24d23c-6647-4b5f-a26c-e5834bd1a657.png)

**Bestellungen für Kundenausrüstung**
================================

Allgemeine Einstellungen verwenden
--------------------------------
- **Status „Allgemeine Einstellungen verwenden“**: Binärwert, der angibt, ob die Option „Allgemeine Einstellungen verwenden“ aktiviert ist
- **„Allgemeine Einstellungen verwenden“ aktivieren**: Aktion zum Aktivieren der Option „Allgemeine Einstellungen verwenden“
- **„Allgemeine Einstellungen verwenden“ deaktivieren**: Aktion zum Deaktivieren der Option „Allgemeine Einstellungen verwenden“

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Einstellungen > Allgemeine Einstellungen verwenden (1)):

![Bild](https://user-images.githubusercontent.com/28622481/133217292-24f23ed8-8de2-492f-bd83-e9b90715de17.png)

Filterung
--------------------------------
- **Filterstatus**: Binärwert, der den Status der Filterung angibt
- **Filterung aktivieren**: Aktion zum Aktivieren der Filterung
- **Filterung deaktivieren**: Aktion zum Deaktivieren der Filterung

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Einstellungen > Domänen mithilfe von Filtern und Hosts-Dateien blockieren (2))

Sicherheit beim Surfen
-----------------------
- **Status „Navigationssicherheit“**: Binärwert, der den Status der Navigationssicherheit angibt
- **Browser-Sicherheit aktivieren**: Aktion zum Aktivieren der Browser-Sicherheit
- **Browser-Sicherheit deaktivieren**: Aktion zum Deaktivieren der Browser-Sicherheit

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Einstellungen > AdGuard-Dienst „Sicheres Surfen“ verwenden (3))

Kindersicherung
-----------------------
- **Status der Kindersicherung**: Binärwert, der den Status der Kindersicherung angibt
- **Kindersicherung aktivieren**: Aktion zum Aktivieren der Kindersicherung
- **Kindersicherung deaktivieren**: Aktion zum Deaktivieren der Kindersicherung

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Einstellungen > AdGuard-Kindersicherung verwenden (4))

Sichere Suche
-----------------------
- **Status „Sichere Suche“**: Binärwert, der den Status der „Sicheren Suche“ angibt
- **Sichere Suche aktivieren**: Aktion zum Aktivieren der sicheren Suche
- **„Sichere Suche“ deaktivieren**: Aktion zum Deaktivieren der „Sicheren Suche“

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Einstellungen > Sichere Suche verstärken (5))

Globale gesperrte Dienste nutzen
--------------------------------
- **Status „Globale gesperrte Dienste verwenden“**: Binärwert, der angibt, ob „Globale gesperrte Dienste verwenden“ aktiviert ist
- **„Globale gesperrte Dienste verwenden“ aktivieren**: Aktion zum Aktivieren der Option „Globale gesperrte Dienste verwenden“
- **„Globale gesperrte Dienste verwenden“ deaktivieren**: Aktion zum Deaktivieren der Option „Globale gesperrte Dienste verwenden“

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Bestimmte Dienste blockieren > Globale Blockierliste verwenden (1)):

![Bild](https://user-images.githubusercontent.com/28622481/133218452-cf994ad7-bf63-4dbd-b727-ff64339b7b31.png)

Spezifische Dienstleistungen
-----------------------
- **Gesperrte Dienste**: Zeichenfolge, die die speziell für diesen Kunden gesperrten Dienste angibt
- **Einen Dienst sperren**: Aktion, mit der ein Dienst aus der Liste speziell für diesen Kunden gesperrt werden kann
- **Einen Dienst freischalten**: Aktion, mit der ein Dienst aus der Liste speziell für diesen Kunden freigeschaltet werden kann

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Bestimmte Dienste blockieren > Dienste (2))

- **Alle Dienste sperren**: Aktion, mit der alle Dienste in der Liste speziell für diesen Kunden gesperrt werden können
- **Alle Dienste freischalten**: Aktion, mit der alle Dienste in der Liste speziell für diesen Kunden freigeschaltet werden können

**AdGuard-Einstellungen** (Einstellungen > Client-Einstellungen > Client bearbeiten > Bestimmte Dienste blockieren > Alles blockieren/Alles freigeben (3))

- **Eine Dienstgruppe sperren** (in der Beta-Phase): Aktion, mit der alle Dienste einer Gruppe speziell für diesen Kunden gesperrt werden können (Dropdown-Liste)
- **Eine Dienstgruppe freischalten** (in der Beta-Phase): Aktion, mit der alle Dienste einer Gruppe speziell für diesen Kunden freigeschaltet werden können (Dropdown-Liste)

> Für die Dienstgruppen ist mindestens AdGuard Home v0.107.68 erforderlich.

Internet über DNS gesperrt
-----------------------
- **Status „Internet über DNS gesperrt“**: Binärwert, der angibt, ob das Internet für diesen Kunden über das DNS gesperrt wurde
- **Gesamten Internetzugang über DNS sperren**: Aktion, mit der der Internetzugang für diesen Kunden über das DNS gesperrt werden kann
- **Das gesamte Internet über DNS freischalten**: Aktion, mit der das Internet für diesen Kunden über DNS freigeschaltet wird

**AdGuard-Konfiguration** (Filter > Benutzerdefinierte Filterregeln > Hinzufügen der Regel: `||*^$client='Kundenname',wichtig` an erster Stelle)

![Bild](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Eine Domain für diesen Kunden testen (in der Beta-Phase)
-----------------------
- **Eine Domain für diesen Client testen** (in der Beta-Phase): Aktion (Eingabefeld), mit der überprüft werden kann, ob eine Domain gemäß den Einstellungen dieses Clients gesperrt ist oder nicht
- **Ergebnis des Domain-Tests für diesen Kunden** (in der Beta-Phase): Zeichenfolge, die das Ergebnis des letzten Tests für diesen Kunden enthält

> AdGuard Home kann eine Domain nur anhand einer IP-Adresse oder einer Client-ID prüfen. Das Plugin verwendet vorrangig die IP-Adresse des Clients, andernfalls die Adresse aus dessen CIDR-Bereich und sonst seine Client-ID. Ein Client, der nur über MAC-Adressen verfügt, kann nicht geprüft werden: Eine Meldung weist Sie darauf hin.

Anmeldedaten
-----------------------
- **ID(s)**: Zeichenfolge, die die aktuellen IDs des Kunden enthält
- **ID hinzufügen**: Aktion zum Hinzufügen einer ID zum Kunden (ohne Anführungszeichen!!)
- **Eine Kennung entfernen**: Aktion zum Entfernen einer Kennung beim Kunden (ohne Anführungszeichen!!)

> **Achtung: Falls es auf einem anderen Client bereits vorhanden ist, muss es zuerst von diesem Client entfernt werden! AdGuard erlaubt es nicht, dass zwei Clients dieselben Anmeldedaten verwenden (logisch ;))**

**AdGuard-Anmeldung** (Einstellungen > Client-Einstellungen > Client bearbeiten > ID):

![Bild](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
