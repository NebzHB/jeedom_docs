---
layout: default
lang: de_DE
title: Plugin „Mérite“
description: Dokumentation zum Plugin „Mérite“ (deserve)
---

# Übersicht

Das Plugin **Mérite** ist ein Semaphor für Jeedom. Jedes Gerät, „Verdienstzähler“ genannt, hat einen Zähler und ein Ziel. Szenarien oder Aktionen fügen Punkte hinzu (**Verdienst**) oder ziehen sie ab (**Abzug**). Erreicht der Zähler das Ziel, wird das Gerät verdienstvoll und seine Verdienst-Aktionen werden ausgeführt. Fällt er wieder unter das Ziel, ist es nicht mehr verdienstvoll und seine Abzugs-Aktionen werden ausgeführt.

Der Sinn ist, Szenarien zu vereinfachen. Statt eine Bedingung zu schreiben, die den Zustand aller beteiligten Elemente kennen muss, fügt jedes Szenario nur seine Punkte hinzu oder zieht sie ab. Die gesamte Logik „was passiert, wenn die Schwelle überschritten wird“ liegt an einer einzigen Stelle: dem Verdienstzähler.

# Einrichtung des Plugins

Das Plugin hat weder Abhängigkeiten noch einen Daemon. Sie müssen es lediglich aktivieren.

# Einrichtung eines Geräts

Klicken Sie unter **Plugins → Automatisierung → Mérite** auf **Hinzufügen** und geben Sie Ihrem Verdienstzähler einen Namen.

## Allgemeine Einstellungen

- **Gerätename**, **Übergeordnetes Objekt**, **Kategorie**, **Aktivieren**, **Sichtbar**: übliche Jeedom-Einstellungen.
- **Zurücksetzen**: Ist dieses Kästchen angekreuzt, wird der Zähler auf 0 zurückgesetzt, sobald das Ziel erreicht ist, direkt nach der Ausführung der Verdienst-Aktionen. *Ist verdienstvoll* geht dann ebenfalls auf 0, **ohne** die Abzugs-Aktionen auszuführen. Jedes Erreichen des Ziels wirkt also wie ein Impuls, was gut zu einem Stufen- oder Belohnungssystem passt.
- **Wo werden die Befehle verwendet?**: Liste der Szenarien, Ansichten, Designs usw., in denen die Befehle dieses Geräts verwendet werden.

## Stufen

Mit Stufen lassen sich Aktionen **vor** dem Erreichen des Ziels auslösen, zum Beispiel um anzukündigen, dass eine Wartung bevorsteht.

- Jede Stufe hat einen **Schwellenwert in Prozent des Ziels** (z. B. 80 %), eine optionale Bedingung und Aktionen, wie die unten beschriebenen Ereignisse.
- Eine Stufe wird ausgeführt, wenn der Prozentsatz ihren Schwellenwert **nach oben** überschreitet. Fällt er wieder darunter und steigt erneut, wird die Stufe erneut ausgeführt.
- Werden mehrere Stufen auf einmal überschritten, werden sie von der niedrigsten zur höchsten ausgeführt, und immer vor den Verdienst-Aktionen.
- Da der Schwellenwert in Prozent angegeben ist, folgen die Stufen automatisch einer Änderung des Ziels. Ein Senken des Ziels kann sogar eine Stufe überschreiten lassen.
- Ein Schwellenwert über 100 % ist möglich, da der Wert das Ziel überschreiten kann.

## Verdienst- und Abzugs-Aktionen

- **Verdienst-Aktionen** werden ausgeführt, wenn der Zähler das Ziel **erreicht oder überschreitet** (*Ist verdienstvoll* wechselt von 0 auf 1).
- **Abzugs-Aktionen** werden ausgeführt, wenn der Zähler wieder **unter** das Ziel fällt (*Ist verdienstvoll* wechselt von 1 auf 0).

Die Aktionen werden nur beim **Überschreiten** des Ziels ausgeführt. Punkte zu einem bereits verdienstvollen Gerät hinzuzufügen, führt die Verdienst-Aktionen nicht erneut aus.

Die Aktionen sind in **Ereignisse** zusammengefasst:

- Jedes Ereignis verfügt über eine optionale **Bedingung**. Ist diese falsch, wird das gesamte Ereignis ignoriert. Wird sie leer gelassen, wird das Ereignis immer ausgeführt.
- Jedes Ereignis enthält eine oder mehrere **Aktionen**. Für jede davon kann man einen Aktionsbefehl (Schaltfläche „Liste“) oder ein Szenario-Schlüsselwort auswählen: Nachricht, Variable, Szenario, Warten, Alarm… (Schaltfläche „Schlüsselwort“).
- Eine Aktion kann deaktiviert werden, ohne gelöscht zu werden, indem man das entsprechende Kontrollkästchen deaktiviert.
- Die Ereignisse werden in der angezeigten Reihenfolge ausgeführt, ebenso wie die Aktionen der einzelnen Ereignisse. Die Reihenfolge der Aktionen kann mithilfe des Ziehbalkens geändert werden.

# Steuerungen

| Befehl | Typ | Beschreibung |
|---|---|---|
| **Wert** | numerische Info | Aktueller Zählerstand (nie negativ). |
| **Benötigt** | numerische Info | Zu erreichendes Ziel (standardmäßig 100). |
| **Ist verdienstvoll** | binäre Info | 1, wenn Wert ≥ Benötigt, sonst 0. |
| **Prozent des Ziels** | numerische Info (%) | Wert / Benötigt × 100, gerundet. Kann 100 % überschreiten. |
| **Fehlend** | numerische Info | Fehlende Punkte bis zum Ziel (Benötigt − Wert, mindestens 0). |
| **Verdienst** | Schieberegler-Aktion | Addiert den Wert des Schiebereglers zum Zähler. |
| **Abzug** | Schieberegler-Aktion | Zieht den Wert des Schiebereglers vom Zähler ab (mindestens 0). |
| **Muss benötigen** | Schieberegler-Aktion | Ändert das Ziel (mindestens 1). |
| **Gewinnen** | Aktion | Setzt den Zähler direkt auf den Wert des Ziels. |
| **Auf Null setzen** | Aktion | Setzt den Zähler auf 0 zurück. |

Anmerkungen:

- Verdienst und Abzug ohne Wert oder mit 0 bewirken nichts.
- Die Schieberegler des Widgets reichen von 0 bis 100. Aus einem Szenario kann ein größerer Wert gesendet werden (zum Beispiel *Muss benötigen* auf 150).
- Wird das Ziel unter den aktuellen Wert gesenkt, wird der Wert auf das neue Ziel zurückgesetzt. Er wird nicht wiederhergestellt, wenn das Ziel anschließend wieder angehoben wird.
- *Auf Null setzen* und *Abzug* lösen die Abzugs-Aktionen aus, wenn das Gerät verdienstvoll war. *Gewinnen* löst die Verdienst-Aktionen aus, wenn es das noch nicht war.
- *Ist verdienstvoll* kann auch als Auslöser oder Bedingung in Ihren Szenarien dienen.

# Anwendungsbeispiele

## Stromlastabwurf

Es sollen nicht zu viele Großverbraucher gleichzeitig laufen: Backofen, Waschmaschine, Trockner, Geschirrspüler, Ladestation.

- Erstellen Sie einen Verdienstzähler „Großverbraucher“ mit einem Ziel von **3**.
- Für jedes Gerät führt ein kleines Szenario **Verdienst 1** aus, wenn seine Leistung einen Schwellenwert überschreitet, und **Abzug 1**, wenn sie wieder sinkt. Man kann gewichten: Die Ladestation kann für 2 zählen.
- Verdienst-Aktionen: die Ladestation pausieren, den Warmwasserbereiter ausschalten, eine Benachrichtigung senden.
- Abzugs-Aktionen: alles wieder aktivieren.

Jedes Gerät verwaltet nur sein +1 und sein −1. Das Hinzufügen eines Geräts erfordert keine Änderung der anderen Szenarien.

## Wartungszähler

Für den Filter einer Lüftungsanlage, eines Wasserenthärters oder einer Dunstabzugshaube oder für den Behälter eines Roboterstaubsaugers.

- Das Ziel ist die Wartungsschwelle (z. B. 50 Zyklen).
- Bei jedem Zyklus führt ein Szenario **Verdienst** aus, eventuell gewichtet: kurzer Zyklus +1, langer Zyklus +3.
- Eine Stufe bei 80 % sendet die Benachrichtigung „Wartung bald fällig“.
- Verdienst-Aktionen: Benachrichtigung „Denken Sie daran, den Filter zu wechseln“. *Ist verdienstvoll* bleibt auf 1, solange die Wartung nicht durchgeführt wurde, und dient so als dauerhafte Erinnerung auf dem Dashboard.
- Nach der Wartung ein Klick auf **Auf Null setzen** im Dashboard.

## Verdienstpunkte

- Jede erledigte Aufgabe bringt Punkte (**Verdienst 10**, **Verdienst 20**…) über eine Taste, eine Interaktion oder ein Szenario.
- Eine festgestellte Vergesslichkeit zieht Punkte ab (**Abzug 5**).
- Ziel 100, mit angekreuztem **Zurücksetzen**: Jedes Erreichen des Ziels löst eine Belohnung aus (eine Steckdose einschalten, eine Benachrichtigung senden…).
- Ein wöchentliches Szenario führt **Auf Null setzen** aus, um neu zu beginnen.

# Protokolle

Das Protokoll `deserve` zeigt auf der Stufe **info** jedes Erreichen des Ziels an. Auf der Stufe **debug** werden zudem jede Wertänderung, jede ausgewertete Bedingung und jede ausgeführte Aktion detailliert aufgeführt.
