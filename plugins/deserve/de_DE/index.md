---
layout: default
lang: de_DE
title: Plugin „Mérite“
description: Dokumentation zum Plugin „Mérite“ (deserve)
---

## Übersicht

Das Plugin **Mérite** ist ein Semaphor für Jeedom. Jedes Gerät, das als „Méritant“ bezeichnet wird, verfügt über einen Zähler und ein Ziel. Szenarien oder Aktionen fügen Punkte hinzu (**Mérite**) oder ziehen sie ab (**Démérite**). Wenn der Zähler das Ziel erreicht, wird das Gerät „verdienstvoll“ und seine verdienstvollen Aktionen werden ausgeführt. Wenn der Zähler wieder unter das Ziel fällt, ist das Gerät nicht mehr „verdienstvoll“ und seine verwerflichen Aktionen werden ausgeführt.

Der Vorteil besteht darin, die Szenarien zu vereinfachen. Anstatt eine Bedingung zu schreiben, die den Status aller betroffenen Elemente kennen muss, beschränkt sich jedes Szenario darauf, seine Punkte hinzuzufügen oder abzuziehen. Die gesamte Logik „Was passiert, wenn der Schwellenwert überschritten wird?“ ist an einer einzigen Stelle zusammengefasst: dem Gerät „Méritant“.

## Einrichtung des Plugins

Das Plugin hat weder Abhängigkeiten noch einen Daemon. Sie müssen es lediglich aktivieren.

## Einrichtung eines Geräts

Klicken Sie unter **Plugins → Automatisierung → Auszeichnung** auf **Hinzufügen** und geben Sie Ihrem Preisträger einen Namen.

### Allgemeine Einstellungen

- **Gerätename**, **Übergeordnetes Objekt**, **Kategorie**, **Aktivieren**, **Sichtbar**: übliche Jeedom-Einstellungen.
- **Zurücksetzen**: Wenn dieses Kästchen angekreuzt ist, wird der Zähler auf 0 zurückgesetzt, sobald das Ziel erreicht ist, unmittelbar nach der Ausführung der verdienstvollen Aktionen. *Verdienst* wird dann ebenfalls auf 0 zurückgesetzt, **ohne** dass die verwerflichen Aktionen ausgelöst werden. Jedes Erreichen des Ziels wirkt somit wie ein Impuls, was sich gut für ein System mit Stufen oder Belohnungen eignet.
- **Wo werden die Befehle verwendet?**: Liste der Szenarien, Ansichten, Designs usw., in denen die Befehle dieses Geräts verwendet werden.

### Stufen

Stufen ermöglichen es, Aktionen **vor** dem Erreichen des Ziels auszulösen, beispielsweise um darauf hinzuweisen, dass eine Wartung ansteht.

- Jede Stufe verfügt über einen **Schwellenwert in Prozent des Ziels** (z. B. 80 %), eine optionale Bedingung und Aktionen, wie die unten beschriebenen Ereignisse.
- Eine Stufe wird ausgeführt, wenn der Prozentsatz **nach oben** seinen Schwellenwert überschreitet. Wenn er wieder unter den Schwellenwert fällt und dann erneut ansteigt, wird die Stufe erneut ausgeführt.
- Werden mehrere Stufen auf einmal durchlaufen, werden sie von der niedrigsten zur höchsten ausgeführt, und zwar immer vor den verdienten Aktionen.
- Da der Schwellenwert in Prozent angegeben wird, passen sich die Stufen automatisch an eine Änderung des Zielwerts an. Eine Senkung des Zielwerts kann übrigens dazu führen, dass eine Stufe überschritten wird.
- Ein Schwellenwert über 100 % ist möglich, da der Wert das Ziel überschreiten kann.

### Verdienst- und Abzugs-Aktionen

- **Verdienst-Aktionen** werden ausgeführt, wenn der Zähler das Ziel **erreicht oder überschreitet** (*Ist verdienstvoll* wechselt von 0 auf 1).
- **Abzugs-Aktionen** werden ausgeführt, wenn der Zähler wieder **unter** das Ziel fällt (*Ist verdienstvoll* wechselt von 1 auf 0).

Aktionen werden erst beim **Überschreiten** des Ziels ausgeführt. Das Hinzufügen von Punkten zu einer bereits verdienten Ausrüstung löst keine neuen verdienten Aktionen aus.

Die Aktionen sind in **Ereignisse** zusammengefasst:

- Jedes Ereignis verfügt über eine optionale **Bedingung**. Ist diese falsch, wird das gesamte Ereignis ignoriert. Wird sie leer gelassen, wird das Ereignis immer ausgeführt.
- Jedes Ereignis enthält eine oder mehrere **Aktionen**. Für jede davon kann man einen Aktionsbefehl (Schaltfläche „Liste“) oder ein Szenario-Schlüsselwort auswählen: Nachricht, Variable, Szenario, Warten, Alarm… (Schaltfläche „Schlüsselwort“).
- Eine Aktion kann deaktiviert werden, ohne gelöscht zu werden, indem man das entsprechende Kontrollkästchen deaktiviert.
- Die Ereignisse werden in der angezeigten Reihenfolge ausgeführt, ebenso wie die Aktionen der einzelnen Ereignisse. Die Reihenfolge der Aktionen kann mithilfe des Ziehbalkens geändert werden.

## Steuerungen

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

- Verdienste und Verfehlungen ohne Wert oder mit dem Wert 0 haben keine Auswirkungen.
- Die Schieberegler des Widgets reichen von 0 bis 100. Über ein Szenario kann ein höherer Wert gesendet werden (z. B. *Muss erforderlich sein* auf 150).
- Wird das Ziel unter den aktuellen Wert gesenkt, wird der Wert auf das neue Ziel zurückgesetzt. Er wird nicht wiederhergestellt, wenn das Ziel anschließend wieder angehoben wird.
- *Auf Null setzen* und *Abzug* lösen die Abzugs-Aktionen aus, wenn das Gerät verdienstvoll war. *Gewinnen* löst die Verdienst-Aktionen aus, wenn es das noch nicht war.
- *Ist verdienstvoll* kann auch als Auslöser oder Bedingung in Ihren Szenarien dienen.

## Anwendungsbeispiele

### Stromlastabwurf

Wir möchten vermeiden, dass zu viele Großverbraucher gleichzeitig in Betrieb sind: Backofen, Waschmaschine, Wäschetrockner, Geschirrspüler, Ladestation.

- Erstellen Sie einen „Großverbraucher“-Empfänger mit einem Zielwert von **3**.
- Für jedes Gerät wird in einem kleinen Szenario **1 Pluspunkt** vergeben, wenn seine Leistung einen Schwellenwert überschreitet, und **1 Minuspunkt**, wenn sie wieder darunter fällt. Eine Gewichtung ist möglich: Der Anschluss kann mit dem Faktor 2 gewichtet werden.
- Verdienst-Aktionen: die Ladestation pausieren, den Warmwasserbereiter ausschalten, eine Benachrichtigung senden.
- Abzugs-Aktionen: alles wieder aktivieren.

Jedes Gerät verwaltet nur sein +1 und sein −1. Das Hinzufügen eines Geräts erfordert keine Änderung der anderen Szenarien.

### Wartungszähler

Für den Filter einer Lüftungsanlage, eines Wasserenthärters oder einer Dunstabzugshaube oder für den Behälter eines Roboterstaubsaugers.

- Das Ziel ist die Wartungsschwelle (z. B. 50 Zyklen).
- In jedem Zyklus wird ein Szenario mit **Punkten** bewertet, gegebenenfalls gewichtet: kurzer Zyklus +1, langer Zyklus +3.
- Bei einem Auslastungsgrad von 80 % wird eine Benachrichtigung „Wartung bald erforderlich“ gesendet.
- Verdienst-Aktionen: Benachrichtigung „Denken Sie daran, den Filter zu wechseln“. *Ist verdienstvoll* bleibt auf 1, solange die Wartung nicht durchgeführt wurde, und dient so als dauerhafte Erinnerung auf dem Dashboard.
- Nach der Wartung klicken Sie im Dashboard auf **Zurücksetzen**.

### Leistungspunkte

- Für jede erledigte Aufgabe gibt es Punkte (**10 Punkte**, **20 Punkte**…) über eine Schaltfläche, eine Interaktion oder ein Szenario.
- Ein festgestelltes Versäumnis führt zu Punktabzug (**5 Strafpunkte**).
- Ziel bei 100, wenn **Zurücksetzen** angekreuzt ist: Jede erreichte Stufe löst eine Belohnung aus (eine Steckdose einschalten, eine Benachrichtigung senden …).
- Ein wöchentliches Szenario führt einen **Reset** durch, um wieder bei Null anzufangen.

## Protokolle

Das Protokoll `deserve` zeigt auf der Stufe **info** jedes Erreichen des Ziels an. Auf der Stufe **debug** werden zudem jede Wertänderung, jede ausgewertete Bedingung und jede ausgeführte Aktion detailliert aufgeführt.
