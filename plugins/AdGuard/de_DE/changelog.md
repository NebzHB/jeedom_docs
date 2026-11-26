---
layout: default
lang: de_DE
title: AdGuard Home-Plugin – Änderungsprotokoll
description: Änderungsprotokoll des AdGuard Home-Plugins
---
Sofern nichts angegeben ist, handelt es sich wahrscheinlich um ein kleines Update zur Rechtschreibung oder zur Kompatibilität mit Jeedom V4.x

# Änderungsprotokoll

## In der Beta-Phase
- Neues Widget für AdGuard Home (Dashboard und Mobilversion), inspiriert vom AdGuard Home-Dashboard: Schutz mit Menü für Pausenlängen und Countdown, Statistiken, anklickbare Kacheln (Filterung, sichere Navigation, Kindersicherung, sichere Suche, gesperrtes Internet)
- Neues Widget für Client-Geräte (Dashboard und Mobilgeräte): Internetzugang freigegeben oder gesperrt mit Schaltfläche, anklickbare Kacheln (allgemeine Einstellungen, Filterung, Browsersicherheit, Kindersicherung, sichere Suche, allgemein gesperrte Dienste), gesperrte Anmeldedaten und Dienste
- Widgets: Einstellungen über Schalter mit Tooltip, integrierte Aktionen in einer Zeile (Dienste, Gruppen, Regeln, Anmeldedaten, Domain-Test mit Ergebnis, Wartung), Aktualisierung von AdGuard Home über das Widget-Symbol. Siehe [Beta-Dokumentation](index-beta#widgets-en-beta)
- Widgets: Ausgefallene Dienste werden als Symbole angezeigt, sowohl auf dem Server als auch auf den Clients
- Liste der Dienste mit Symbolen, Suchfunktion und nach Gruppen geordneten Diensten; durch Auswahl einer Gruppe wird die gesamte Gruppe gesperrt oder entsperrt
- Widgets: Bestätigung vor dem Trennen der Internetverbindung, Deaktivieren der Filterung oder der Kindersicherung, Sperren oder Entsperren aller Dienste sowie vor Wartungsmaßnahmen (DNS-Cache, Filter, Statistiken)
- Widgets: Mindestbreite von 320 px auf dem Dashboard mit responsivem Layout, volle Breite auf Mobilgeräten
- Widgets: Automatische Anpassung der Höhe an den Inhalt, mit der Option „Widget-Höhe: Fest“ am Gerät, um die Höhe aus dem Bearbeitungsmodus beizubehalten
- Neue Anzeige „Verbleibende Pause“: verbleibende Zeit (in Sekunden) bis zur Wiederaufnahme des Schutzes
- Neue Aktionen „DNS-Cache leeren“ und „Filter aktualisieren“
- Neue Aktion „Domain testen“ (und die Information „Ergebnis des Domain-Tests“) auf dem AdGuard Home-Gerät sowie „Domain für diesen Client testen“ auf den Clients
- Neue Funktionen „Dienstgruppe blockieren“ und „Dienstgruppe entsperren“, global und pro Kunde (mindestens AdGuard Home v0.107.68)
- Der in AdGuard Home festgelegte Zeitplan für gesperrte Dienste wird nicht mehr gelöscht, wenn ein Dienst über Jeedom gesperrt oder entsperrt wird
- Sichere Suche (global und pro Kunde): Es ändert sich lediglich der Status „aktiviert/deaktiviert“, die in AdGuard Home ausgewählten Suchmaschinen bleiben erhalten (einschließlich Ecosia)
- Die Funktionen „Sicheres Surfen“ und „Kindersicherung“ nutzen die neuen API-Aufrufe von AdGuard Home, wobei für ältere Versionen weiterhin die bisherigen Aufrufe verwendet werden.
- „Filter aktualisieren“ und „AdGuard aktualisieren“ warten bis zu 120 Sekunden auf die Antwort von AdGuard Home (zuvor schlug der Befehl fehl und „Online“ sprang auf 0)
- Zuverlässigkeit: Die Aktionen zeigen eine klare Meldung an, wenn AdGuard Home nicht reagiert, der Client nicht gefunden wird oder die Regel leer ist, anstatt stillschweigend zu scheitern. Benutzerdefinierte Regeln können nicht mehr versehentlich gelöscht werden, und das zweimalige Blockieren des Internets führt nicht mehr zu einem Duplikat.
- Korrektur bei Kunden, deren Name einen Bindestrich enthält
- Korrektur der Erkennung von Netzwerkfehlern (PHP 8)
- Bei der Bearbeitung eines Kunden werden nur noch die bearbeitbaren Felder an AdGuard Home gesendet
- Korrektur des Rechtschreibfehlers „globlaux“ in den Bezeichnungen der Kundenaufträge („Globale gesperrte Dienste verwenden“)
- Übersetzte Hilfe-Texte zu den Befehlen

## 26-11-2026
- Kompatibel mit AdGuard Home v1.0.0

## 12-11-2026
- Für die Konfiguration sind Administratorrechte erforderlich

## 30-01-2025
- Übersetzung der Befehlsnamen
- Behebung einer PHP-Warnung, wenn keine Benutzerregeln vorhanden sind
- (Danke @TomiTomas): Deaktivierungszeit für den Schutz hinzugefügt (wie bei AdGuardHome)

## 07-10-2024
- „Community“-Schaltfläche hinzugefügt, um leichter Hilfe zu erhalten

## 12-08-2024
- Übersetzungen und Aktualisierung der Übersetzungen ins Englische, Deutsche, Spanische, Italienische und Portugiesische

## 11-09-2023
- Version v0.107.37 erforderlich!
- Änderungen an den gesperrten Diensten ab Version v0.107.37

## 24-05-2023

- Änderungen für die neuen API-Elemente in Version 0.107.28 (Schutz aktiviert + Safesearch)
- Derzeit gibt es keine Möglichkeit, die Suchmaschine für den Safesearch-Schutz auszuwählen (ist das überhaupt notwendig??)
- Derzeit gibt es keine Möglichkeit, einen Zeitpunkt für die Deaktivierung des Schutzes festzulegen (ist das bei Jeedom überhaupt notwendig? Da man ihn ja über ein Szenario oder auf andere Weise wieder aktivieren kann...)
- Korrektur des Befehls „Update“
- Verschlüsselung Ihrer AdGuard-Passwörter in der Jeedom-Datenbank
- **Erfordert daher mindestens die Version AdGuard v0.107.28!**


## 14-11-2022

- Internet-Sperre/Entsperrung und benutzerdefinierte Regeln (ab Version v0.107.14), Update auf v0.107.17+
- Erfordert daher mindestens die Version AdGuard v0.107.17!

## 04-11-2022

- Seit Version 0.107.17 unterstützt AdGuard neue Dienste (iCloud Private Relay usw.). Diese Version fordert die Liste der Dienste von AdGuard an und aktualisiert die Befehle bei Bedarf.

## 08-09-2022

- Der Dienst BiliBili wurde in Version 0.107.12 hinzugefügt
- Der Fehler tritt nicht mehr auf, wenn die Datei „version.json“ bei AdGuard nicht mehr verfügbar ist (aufgrund eines Fehlers auf deren Seite).

## 28-06-2022

- Hinzufügen des https-Protokolls für diejenigen, die einen Proxy oder Ähnliches verwenden

## 08-04-2021

- Die aktuelle und die neue Version wurden zu den Befehlen hinzugefügt. Wenn zum Zeitpunkt des Updates eine neue Version verfügbar ist, sendet AdGuard mir die alte Versionsnummer nicht zu, sodass das Feld leer bleibt … Sobald Sie jedoch das Update durchführen, wird es aktualisiert und dann ist alles in Ordnung.
- Übersetzung ins Englische und Spanische
- Befehle mit der Aktion „Internet über DNS sperren“ verknüpfen

## 21-09-2021

- Behebe den Fehler, wenn ein Gerät bereits im selben Raum wie der Kunde vorhanden und deaktiviert ist

## 15-09-2021

- Initialisierung

