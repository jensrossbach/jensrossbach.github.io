---
# the default layout is 'page'
title: Projekte
icon: fas fa-code-branch
order: 3
---

Hier findest du Information zu einer Auswahl an privaten Projekten (sowohl Software als auch Hardware), an denen ich in den letzten Jahren gearbeitet habe. Die Seite ist noch nicht vollständig und wird nach und nach erweitert.

# Smart Home

## ESPHome

Wenn man sich mit Home Assistant beschäftigt, kommt man eigentlich auch nicht um das Thema ESPHome herum. Die folgenden Projekte haben mir dabei geholfen, ältere Geräte in mein Smart-Home zu integrieren.

### Luxtronik V1

Luxtronik V1 ist eine ESPHome-Komponente zur Erstellung einer ESP-Firmware, die die Integration eines Luxtronik V1 Heizungssteuergeräts in das Smart Home ermöglicht. Die Komponente ist primär für die Einbindung in Home Assistant gedacht, aber über MQTT kann auch eine Integration mit einer alternativen Hausautomatisierungs-Software realisiert werden. Die Luxtronik Heizungsregelung in der Version 1 (V1) verfügt nicht über eine Netzwerkschnittstelle, sondern stellt lediglich eine RS-232-Schnittstelle zur Verfügung. Daher ist ein Mikrocontroller als Gateway zwischen Heizungssteuergerät und Netzwerk notwendig.

Den Quellcode und die Dokumentation findest du im Repository auf GitHub:

⇨ [jensrossbach/esphome-luxtronik-v1](https://github.com/jensrossbach/esphome-luxtronik-v1)

### Ferraris Meter

Ferraris Meter ist eine ESPHome-Komponente zur Erstellung einer ESP-Firmware, die mithilfe eines ESP-Mikrocontrollers und eines Infrarotsensors die Geschwindigkeit und die Umdrehungen der Drehscheibe eines analogen Ferraris-Stromzählers ermitteln und daraus den momentanen Stromverbrauch und den Zählerstand berechnen kann. Diese Werte können dann zur weiteren Verarbeitung an eine Hausautomatisierungs-Software wie beispielsweise Home Assistant geschickt werden.

Den Quellcode und die Dokumentation findest du im Repository auf GitHub:

⇨ [jensrossbach/esphome-ferraris-meter](https://github.com/jensrossbach/esphome-ferraris-meter)

## Node-RED

Die folgenden Projekte sind in der Zeit entstanden, als ich noch hauptsächlich auf Node-RED für meine Heimautomatisierung gesetzt hatte. Mittlerweile bin ich ja komplett auf Home Assistant umgestiegen (ja ich weiß, man kann Home Assistant auch sehr gut mit Node-RED kombinieren). Im Gegensatz zu anderen Home Assistant Benutzern, die Node-RED für Automatisierungen verwenden, habe ich aber alle meine Automatisierungen in Home Assistant direkt laufen. Nichtsdestotrotz pflege ich meine Node-RED Projekte weiter für all diejenigen, die meine Nodes verwenden und auf Unterstützung angewiesen sind. Ich habe zwei Node-Pakete entwickelt, die ich im Folgenden kurz vorstelle. Weitere Details findet ihr in den jeweiligen GitHub Repositories, insbesondere den Wikis.

#### Chronos

Chronos (vollständiger NPM/Node-RED Paketname: _node-red-contrib-chronos_) ist ein Node-Paket, bei dem sich alles um die Zeit dreht. Es enthält Nodes zum zeitbasierten Planen, Wiederholen, Verzögern, Abzweigen und Filtern von Nachrichten.

Unter folgendem Link findest du die Paketbeschreibung in der Node-RED Library:

⇨ [node-red-contrib-chronos](https://flows.nodered.org/node/node-red-contrib-chronos)

Das NPM-Paket findest du unter folgendem Link in der NPM Registry:

⇨ [node-red-contrib-chronos](https://www.npmjs.com/package/node-red-contrib-chronos)

Den Quellcode und die Dokumentation findest du im Repository auf GitHub:

⇨ [jensrossbach/node-red-contrib-chronos](https://github.com/jensrossbach/node-red-contrib-chronos)

#### Sony Audio

Sony Audio (vollständiger NPM/Node-RED Paketname: _@jens\_rossbach/node-red-sony-audio_) ist ein Node-Paket mit Nodes zur Steuerung und Abfrage von Sony Audiogeräten, die die Sony Audio Control API unterstützen.

Unter folgendem Link findest du die Paketbeschreibung in der Node-RED Library:

⇨ [@jens_rossbach/node-red-sony-audio](https://flows.nodered.org/node/@jens_rossbach/node-red-sony-audio)

Das NPM-Paket findest du unter folgendem Link in der NPM Registry:

⇨ [@jens_rossbach/node-red-sony-audio](https://www.npmjs.com/package/@jens_rossbach/node-red-sony-audio)

Den Quellcode und die Dokumentation findest du im Repository auf GitHub:

⇨ [jensrossbach/node-red-sony-audio](https://github.com/jensrossbach/node-red-sony-audio)

# Sonstiges

## ClockIn

ClockIn (zu deutsch: "stechen"/"einstechen"/"stempeln") ist ein kleines Windows-Programm zum Erfassen und Überwachen der eigenen Arbeitszeit. Es merkt sich die Zeit, zu der du deine Arbeit begonnen hast, benachrichtigt dich, wenn du deine reguläre Arbeitszeit erreicht hast und warnt dich, bevor du deine maximale Arbeitszeit überschreitest. Das Tool ist hauptsächlich für deutsche Arbeitnehmer interessant, die in Büros arbeiten und sich an das deutsche Arbeitszeitgesetz halten müssen.

![ClockIn](/assets/img/projects/clockin.png)

Den Quellcode findest du im Repository auf GitHub:

⇨ [jensrossbach/clock-in](https://github.com/jensrossbach/clock-in)
