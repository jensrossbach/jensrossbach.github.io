---
# the default layout is 'page'
title: Projekte
icon: fas fa-code-branch
order: 2
---

Hier findest du Information zu einer Auswahl an privaten Projekten (sowohl Software als auch Hardware), an denen ich in den letzten Jahren gearbeitet habe. Die Seite ist noch nicht vollständig und wird nach und nach erweitert.

# Smart Home

## ESPHome

Wenn man sich mit Home Assistant beschäftigt, kommt man eigentlich auch nicht um das Thema ESPHome herum. Die folgenden Projekte haben mir dabei geholfen, ältere Geräte in mein Smart-Home zu integrieren.

### Luxtronik V1

In unserem Haus sorgt eine Alpha Innotec Wärmepumpe für angenehme Temperaturen im Winter. Da die Heizung schon etwas in die Jahre gekommen ist, hat sie eine Heizungssteuerung (Luxtronik V1), die nicht mehr ganz dem aktuellen Stand der Technik entspricht. So verfügt sie über keine Netzwerkschnittstelle, um sie einfach in das Smart-Home einbinden zu können. Zum Glück ist sie aber nicht völlig altertümlich und hat wenigstens eine serielle RS-232-Schnittstelle, sodass es prinzipiell möglich ist, mit dem Gerät zu kommunizieren. Auch wenn diese Schnittstelle eigentlich nur für den Kundendienst gedacht ist, eignet sie sich mit einer kleinen Zusatz-Hardware, die als Gateway zum Netzwerk dient, hervorragend dazu, Daten von der Heizung abzufragen oder diese sogar zu konfigurieren.

Bei der Zusatz-Hardware habe ich mich für einen ESP-Mikrocontroller entschieden, konkret einen ESP32. Den Mikrocontroller konnte ich aufgrund der unterschiedlichen Spannungspegel nicht direkt an die RS-232-Schnittstelle des Luxtronik Heizungssteuergeräts angeschließen. Stattdessen musste ich einen MAX3232-IC verwenden, um zwischen den unterschiedlichen Spannungspegeln auf Luxtronik- und Mikrocontroller-Seite zu konvertieren. Zum Glück gibt es fertige Seriell-zu-TTL Konvertierungsmodulplatinen, die mit einem MAX3232-IC und einem DE-9 (auch D-Sub 9) Stecker ausgestattet sind. Auf der RS-232-Seite haben diese Module einen (meist weiblichen) DE-9-Stecker (an dem aber nur GND, RX und TX verbunden sind) und auf der TTL-Seite haben sie 4 Pins - VCC und GND für die Stromversorgung des Chips sowie RX und TX für die Datenübertragung.

Sinnvollerweise platziert man den Mikrocontroller außerhalb des Wärmepumpengehäuses, um einen besseren Wi-Fi-Empfang und eine einfachere Wartung zu ermöglichen. Es gibt dabei zwei Möglichkeiten, wo die „lange“ Verkabelung zwischen dem Mikrocontroller-Aufbau und der Luxtronik platziert werden kann:

1. Serielles Kabel (fertig oder selbst gebaut), das zwischen dem MAX3232-Modul und der RS-232-Schnittstelle der Luxtronik angeschlossen wird
2. 4-adriges Kabel zwischen dem Mikrocontroller und dem MAX3232-Modul (letzteres wird direkt an die RS-232-Schnittstelle der Luxtronik angeschlossen)

Die meisten im Internet beschriebenen Aufbauten, die ich recherchiert hatte, verwenden Option 1, aber ich habe mich in meinem Fall für Option 2 entschieden. Als Kabel habe ich ein handelsübliches 4-adriges Telefonverlegekabel verwendet. Diese Kabel haben zwei verdrillte Adernpaare (rot + schwarz und weiß + gelb). Die roten und schwarzen Adern sind prädestiniert für VCC bzw. GND. Ich habe dann gelb für RX und weiß für TX gewählt. Die Adern haben jeweils einen Durchmesser von 0,6 mm, sodass der Spannungsabfall bei 3,3V und der sehr geringen Stromstärke bei einer Kabellänge von 2-4 Metern vernachlässigbar ist.

Warum habe ich mich für Option 2 entschieden? Der Grund war, dass fertige serielle Kabel heutzutage schwer zu bekommen und teuer sind und - der wichtigere Grund - die großen DE-9-Steckerenden nicht durch die kleinen Durchlässe im Gehäuse der Wärmepumpe passen. Außerdem wollte ich mir kein eigenes Kabel bauen, denn auch DE-9-Stecker sind schwer zu bekommen und teuer. Für Option 2 habe ich die Drähte an einem Ende des Kabels direkt an die TTL-Pins der MAX3232-Modulplatine gelötet und diese dann direkt an die Luxtronik RS-232-Schnittstelle angeschlossen (mit einem kleinen Nullmodem-Adapter dazwischen, da die RX- und TX-Verbindungen getauscht werden mussten). Für den Mikrocontroller-Aufbau habe ich Buchsenleisten sowie Leiterplatten-Schraubklemmenblöcke auf eine Lochrasterplatine gelötet und die entsprechenden Pins verbunden. An die Buchsenleisten habe ich eine ESP32 NodeMCU-Entwicklungsplatine angeschlossen und konnte dann die Drähte des Telefonkabels einfach an die Schraubklemmen anschließen, nachdem ich das Kabel durch die Durchlässe des Wärmepumpengehäuses geführt hatte.

Zusätzlich zu dem Hardware-Aufbau habe ich mir eine eigene ESPHome-Komponente geschrieben, um die Daten besser verarbeiten zu können. Diese ESPHome-Komponente habe ich auf GitHub zusammen mit einer ausführlichen Dokumentation veröffentlicht, damit auch andere davon profitieren können:

⇨ [jensrossbach/esphome-luxtronik-v1](https://github.com/jensrossbach/esphome-luxtronik-v1)

### Ferraris Meter

Ich habe in meinem Haus zwei Stromzähler - einen für den normalen Hausstrom und einen für die Wärmepumpe. Letzterer wurde kürzlich vom Netzbetreiber gegen eine sogenannte "Moderne Messeinrichtung" ausgetauscht. Diese verfügt über eine Infrarotschnittstelle, über die man den aktuellen Stromverbrauch und den Zählerstand auslesen kann. Mithilfe eines entsprechenden Geräts von Homematic IP kann ich diese Werte erfassen und im Smart-Home weiter verarbeiten. Das gleiche wollte ich auch für meinen Hausstrom machen. Da eine Anfrage beim Netzbetreiber, wann denn der alte Ferraris-Stromzähler ausgetauscht werden würde, ergab, dass dies erst für 2028 geplant sei, musste ich mir eine alternative Lösung für den Hausstrom suchen. Ich fand dann Informationen im Internet darüber, wie man mithilfe eines Infrarotsensors die Umdrehungen der Drehscheibe in dem Stromzähler erfassen kann. Die Drehscheibe beschreibt den Stromverbrauch über die Anzahl Umdrehungen innerhalb einer bestimmten Zeit, bei meinem Stromzähler sind es 75 Umdrehungen pro Kilowattstunde. Die Drehscheibe hat eine rote Markierung, die einmal pro Umdrehung an dem Sensor vorbeiläuft. Der Sensor erkennt die rote Markierung und dadurch ist es möglich, die Umdrehungen zu erfassen. Indem man die Zeit misst, die eine Umdrehung benötigt, kann so der aktuelle Stromverbrauch berechnet werden. Und indem man die Umdrehungen zählt, kann man den Zählerstand berechnen.

Um mein Projekt zu realisieren, habe ich lediglich einen ESP-Mikrocontroller (inkl. Spannungsversorgung), einen Infrarotsensor, eine Halterung für den Sensor und etwas doppelseitiges Klebeband benötigt. Für das Auslesen des Stromzählers reicht ein ESP8266 als Mikrocontroller völlig aus, weshalb ich mich für diesen entschieden habe (zumal ich noch ungenutzte D1 Mini Boards zuhause herumliegen hatte). Für den Infrarotsensor gibt es fertige TCRT5000-basierte Breakout-Module mit 3,3V-5V Eingangsspannung, die über einen regelbaren Widerstand (Potentiometer) verfügen, um die Empfindlichkeit des Sensors einzustellen. Ein solches Modul habe ich mit drei Leitungen (VCC, GND und ein digitales Signal) mit dem ESP-Mikrocontroller verbunden.

Beim Platzieren des Sensors auf der Abdeckplatte des Ferraris-Stromzählers war ein wenig Geschick und Präzisionsarbeit gefragt. Das Infrarot Sender/Empfänger-Paar des Sensors musste mittig millimetergenau über der Drehscheibe ausgerichtet werden und geradlinig auf die Drehscheibe zeigen. Bei den ersten versuchen hatte ich ein Schaumstoffkissen und Kreppband zum Befestigen verwendet, allerdings mit mäßigem Erfolg, da der Sensor immer wieder verrutscht ist und die Umdrehung dann nicht mehr erfassen konnte. Nach intensivem Durchsuchen des Kellers nach einer brauchbaren Halterung für den Sensor, habe ich schließlich etwas gefunden, das ich nicht wirklich beschreiben kann, da ich keine Ahnung habe, wofür das Kunststoffteil eigentlich gut ist. Es hat sich aber in Verbindung mit starkem doppelseitigem Klebeband als hervorragende Halterung für den Sensor herausgestellt.

Auch für dieses Projekt habe ich mir eine eigene ESPHome-Komponente geschrieben und auf GitHub zusammen mit einer ausführlichen Dokumentation veröffentlicht:

⇨ [jensrossbach/esphome-ferraris-meter](https://github.com/jensrossbach/esphome-ferraris-meter)

## Node-RED

Die folgenden Projekte sind in der Zeit entstanden, als ich noch hauptsächlich auf Node-RED für meine Heimautomatisierung gesetzt hatte. Mittlerweile bin ich ja komplett auf Home Assistant umgestiegen (ja ich weiß, man kann Home Assistant auch sehr gut mit Node-RED kombinieren). Im Gegensatz zu anderen Home Assistant Benutzern, die Node-RED für Automatisierungen verwenden, habe ich aber alle meine Automatisierungen in Home Assistant direkt laufen. Nichtsdestotrotz pflege ich meine Node-RED Projekte weiter für all diejenigen, die meine Nodes verwenden und auf Unterstützung angewiesen sind. Ich habe zwei Node-Pakete entwickelt, die ich im Folgenden kurz vorstelle. Weitere Details findet ihr in den jeweiligen GitHub Repositories, insbesondere den Wikis.

#### Chronos

Chronos (vollständiger NPM/Node-RED Paketname: _node-red-contrib-chronos_) ist ein Node-Paket, bei dem sich alles um die Zeit dreht. Es enthält Nodes zum zeitbasierten Planen, Wiederholen, Verzögern, Abzweigen und Filtern von Nachrichten.

Obwohl es ähnliche Nodes (fast) im Überfluss bereits gibt, hatte ich mich trotzdem dazu entschlossen, eigene Nodes zu entwickeln, da mir die damals existierenden Implementierungen alle nicht gefallen hatten. Entweder hatten sie nicht die Funktionalität, die ich brauchte oder die Benutzeroberfläche war zu puristisch oder aber die Nodes waren wiederum viel zu überfrachtet mit Funktionalität. Ich habe im Laufe der Zeit zwar auch immer mehr Funktionalität hinzugefügt, aber ebenso darauf geachtet, dass das User Interface nicht aus allen Nähten geplatzt ist.

Der erste Node war der Scheduler Node zum geplanten Versenden von Nachrichten. Kurz darauf folgten der Time Switch Node (das zeitbasierte Äquivalent zum Node-RED Switch Node), der Time Filter Node und der Delay Node (damals noch Delay Until Node, um den Unterschied zum Node-RED Delay Node auszudrücken). Einige Releases später folgte dann der Time Change Node (das zeitbasierte Äquivalent zum Node-RED Change Node), danach der Repeat Node und zuletzt dann der State Node (der mehr oder weniger eine zustandsbehaftete Variante des zustandslosen Scheduler Nodes ist).

Unter folgendem Link findest du die Paketbeschreibung in der Node-RED Library:

⇨ [node-red-contrib-chronos](https://flows.nodered.org/node/node-red-contrib-chronos)

Das NPM-Paket findest du unter folgendem Link in der NPM Registry:

⇨ [node-red-contrib-chronos](https://www.npmjs.com/package/node-red-contrib-chronos)

Den Quellcode findest du im Repository auf GitHub:

⇨ [jensrossbach/node-red-contrib-chronos](https://github.com/jensrossbach/node-red-contrib-chronos)

#### Sony Audio

Sony Audio (vollständiger NPM/Node-RED Paketname: _@jens\_rossbach/node-red-sony-audio_) ist ein Node-Paket mit Nodes zur Steuerung und Abfrage von Sony Audiogeräten, die die Sony Audio Control API unterstützen.

Das Projekt hatte ich begonnen, weil ich eine Möglichkeit gesucht hatte, meine Soundbar Sony HT-XT3 über Node-RED anzusteuern und es keine Nodes dafür gab. Das aktuelle Paket liegt bereits in der dritten Generation vor. Da ich die Implementierung zweimal komplett überarbeitet habe und dadurch Inkompatibilitäten entstanden sind, hatte ich jeweils beschlossen, ein neues Repository (und damit auch NPM-Paket) zu erstellen. Dadurch wurden die Flows der Nutzer, die die alten Nodes verwendet hatten, nicht beeinflusst und jeder konnte selbst über eine Migration entscheiden.

Unter folgendem Link findest du die Paketbeschreibung in der Node-RED Library:

⇨ [@jens_rossbach/node-red-sony-audio](https://flows.nodered.org/node/@jens_rossbach/node-red-sony-audio)

Das NPM-Paket findest du unter folgendem Link in der NPM Registry:

⇨ [@jens_rossbach/node-red-sony-audio](https://www.npmjs.com/package/@jens_rossbach/node-red-sony-audio)

Den Quellcode findest du im Repository auf GitHub:

⇨ [jensrossbach/node-red-sony-audio](https://github.com/jensrossbach/node-red-sony-audio)

# Sonstiges

## ClockIn

ClockIn (zu deutsch: "stechen"/"einstechen"/"stempeln") ist ein kleines Windows-Programm zum Erfassen und Überwachen der eigenen Arbeitszeit. Es merkt sich die Zeit, zu der du deine Arbeit begonnen hast, benachrichtigt dich, wenn du deine reguläre Arbeitszeit erreicht hast und warnt dich, bevor du deine maximale Arbeitszeit überschreitest. Das Tool ist hauptsächlich für deutsche Arbeitnehmer interessant, die in Büros arbeiten und sich an das deutsche Arbeitszeitgesetz halten müssen.

![ClockIn](/assets/img/projects/clockin.png)

Hier findest du den Quellcode des Programms auf GitHub:

⇨ [jensrossbach/clock-in](https://github.com/jensrossbach/clock-in)
