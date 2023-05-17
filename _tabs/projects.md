---
# the default layout is 'page'
title: Projekte
icon: fas fa-code-branch
order: 2
---

Hier findest du Information zu einer Auswahl an privaten Projekten (sowohl Software als auch Hardware), an denen ich in den letzten Jahren gearbeitet habe. Die Seite ist noch nicht vollständig und wird nach und nach erweitert.

# Smart Home

## Node-RED

Die folgenden Projekte sind in der Zeit entstanden, als ich noch hauptsächlich auf Node-RED für meine Heimautomatisierung gesetzt hatte. Mittlerweile bin ich ja komplett auf Home Assistant umgestiegen (ja ich weiß, man kann Home Assistant auch sehr gut mit Node-RED kombinieren). Im Gegensatz zu anderen Home Assistant Benutzern, die Node-RED für Automatisierungen verwenden, habe ich aber alle meine Automatisierungen in Home Assistant direkt laufen. Nichtsdestotrotz pflege ich meine Node-RED Projekte weiter für all diejenigen, die meine Nodes verwenden und auf Unterstützung angewiesen sind. Ich habe zwei Node-Pakete entwickelt, die ich im Folgenden kurz vorstelle. Weitere Details findet ihr in den jeweiligen GitHub Repositories, insbesondere den Wikis.

#### Chronos

Chronos (vollständiger NPM/Node-RED Paketname: _node-red-contrib-chronos_) ist ein Node-Paket, bei dem sich alles um die Zeit dreht. Es enthält Nodes zum zeitbasierten Planen, Wiederholen, Verzögern, Abzweigen und Filtern von Nachrichten.

Obwohl es ähnliche Nodes (fast) im Überfluss bereits gibt, hatte ich mich trotzdem dazu entschlossen, eigene Nodes zu entwickeln, da mir die damals existierenden Implementierungen alle nicht gefallen hatten. Entweder hatten sie nicht die Funktionalität, die ich brauchte oder die Benutzeroberfläche war zu puristisch oder aber die Nodes waren wiederum viel zu überfrachtet mit Funktionalität. Ich habe im Laufe der Zeit zwar auch immer mehr Funktionalität hinzugefügt, aber ebenso darauf geachtet, dass das User Interface nicht aus allen Nähten geplatzt ist.

Der erste Node war der Scheduler Node zum geplanten Versenden von Nachrichten. Kurz darauf folgten der Time Switch Node (das zeitbasierte Äquivalent zum Node-RED Switch Node), der Time Filter Node und der Delay Node (damals noch Delay Until Node, um den Unterschied zum Node-RED Delay Node auszudrücken). Einige Releases später folgte dann der Time Change Node (das zeitbasierte Äquivalent zum Node-RED Change Node) und zuletzt dann der Repeat Node.

Unter folgendem Link findest du die Paketbeschreibung in der Node-RED Library:

* [node-red-contrib-chronos (Node-RED)](https://flows.nodered.org/node/node-red-contrib-chronos)

Das NPM-Paket findest du unter folgendem Link in der NPM Registry:

* [node-red-contrib-chronos (NPM)](https://www.npmjs.com/package/node-red-contrib-chronos)

Den Quellcode findest du im Repository auf GitHub:

* [node-red-contrib-chronos (GitHub)](https://github.com/jensrossbach/node-red-contrib-chronos)

#### Sony Audio

Sony Audio (vollständiger NPM/Node-RED Paketname: _@jens\_rossbach/node-red-sony-audio_) ist ein Node-Paket mit Nodes zur Steuerung und Abfrage von Sony Audiogeräten, die die Sony Audio Control API unterstützen.

Das Projekt hatte ich begonnen, weil ich eine Möglichkeit gesucht hatte, meine Soundbar Sony HT-XT3 über Node-RED anzusteuern und es keine Nodes dafür gab. Das aktuelle Paket liegt bereits in der dritten Generation vor. Da ich die Implementierung zweimal komplett überarbeitet habe und dadurch Inkompatibilitäten entstanden sind, hatte ich jeweils beschlossen, ein neues Repository (und damit auch NPM-Paket) zu erstellen. Dadurch wurden die Flows der Nutzer, die die alten Nodes verwendet hatten, nicht beeinflusst und jeder konnte selbst über eine Migration entscheiden.

Unter folgendem Link findest du die Paketbeschreibung in der Node-RED Library:

* [@jens_rossbach/node-red-sony-audio (Node-RED)](https://flows.nodered.org/node/@jens_rossbach/node-red-sony-audio)

Das NPM-Paket findest du unter folgendem Link in der NPM Registry:

* [@jens_rossbach/node-red-sony-audio (NPM)](https://www.npmjs.com/package/@jens_rossbach/node-red-sony-audio)

Den Quellcode findest du im Repository auf GitHub:

* [@jens_rossbach/node-red-sony-audio (GitHub)](https://github.com/jensrossbach/node-red-sony-audio)

# Sonstiges

## ClockIn

ClockIn (zu deutsch: "stechen"/"einstechen"/"stempeln") ist ein kleines Windows-Programm zum Erfassen und Überwachen der eigenen Arbeitszeit. Es merkt sich die Zeit, zu der du deine Arbeit begonnen hast, benachrichtigt dich, wenn du deine reguläre Arbeitszeit erreicht hast und warnt dich, bevor du deine maximale Arbeitszeit überschreitest. Das Tool ist hauptsächlich für deutsche Arbeitnehmer interessant, die in Büros arbeiten und sich an das deutsche Arbeitszeitgesetz halten müssen.

![ClockIn](/assets/img/projects/clockin.png)

Hier findest du den Quellcode des Programms auf GitHub:

* [ClockIn (GitHub)](https://github.com/jensrossbach/clock-in)
