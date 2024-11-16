---
title: "Auslesen eines analogen Ferraris-Stromzählers"
date: 2024-09-14 10:30:00 +0001
categories:
  - Projekte
  - Elektronik
tags:
  - smarthome
  - elektronik
  - esphome
  - homeassistant
  - energie
  - strom
  - stromzähler
  - stromverbrauch
  - ferraris
---

Ich habe in meinem Haus zwei Stromzähler - einen für den normalen Hausstrom und einen für die Wärmepumpe. Letzterer wurde kürzlich vom Netzbetreiber gegen eine sogenannte "Moderne Messeinrichtung" ausgetauscht. Diese verfügt über eine Infrarotschnittstelle, über die man den aktuellen Stromverbrauch und den Zählerstand auslesen kann. Mithilfe eines entsprechenden Geräts von Homematic IP kann ich diese Werte erfassen und im Smart-Home weiter verarbeiten. Das gleiche wollte ich auch für meinen Hausstrom machen. Da eine Anfrage beim Netzbetreiber, wann denn der alte Ferraris-Stromzähler ausgetauscht werden würde, ergab, dass dies erst für 2028 geplant sei, musste ich mir eine alternative Lösung für den Hausstrom suchen. Ich fand dann Informationen im Internet darüber, wie man mithilfe eines Infrarotsensors die Umdrehungen der Drehscheibe in dem Stromzähler erfassen kann. Die Drehscheibe beschreibt den Stromverbrauch über die Anzahl Umdrehungen innerhalb einer bestimmten Zeit, bei meinem Stromzähler sind es 75 Umdrehungen pro Kilowattstunde. Die Drehscheibe hat eine rote Markierung, die einmal pro Umdrehung an dem Sensor vorbeiläuft. Der Sensor erkennt die rote Markierung und dadurch ist es möglich, die Umdrehungen zu erfassen. Indem man die Zeit misst, die eine Umdrehung benötigt, kann so der aktuelle Stromverbrauch berechnet werden. Und indem man die Umdrehungen zählt, kann man den Zählerstand berechnen.

Um mein Projekt zu realisieren, habe ich lediglich einen ESP-Mikrocontroller (inkl. Spannungsversorgung), einen Infrarotsensor, eine Halterung für den Sensor und etwas doppelseitiges Klebeband benötigt. Für das Auslesen des Stromzählers reicht ein ESP8266 als Mikrocontroller völlig aus, weshalb ich mich für diesen entschieden habe (zumal ich noch ungenutzte D1 Mini Boards zuhause herumliegen hatte). Für den Infrarotsensor gibt es fertige TCRT5000-basierte Breakout-Module mit 3,3V-5V Eingangsspannung, die über einen regelbaren Widerstand (Potentiometer) verfügen, um die Empfindlichkeit des Sensors einzustellen. Ein solches Modul habe ich mit drei Leitungen (VCC, GND und ein digitales Signal) mit dem ESP-Mikrocontroller verbunden.

![Ferraris Meter](/assets/img/posts/ferraris_meter.jpg)

Beim Platzieren des Sensors auf der Abdeckplatte des Ferraris-Stromzählers war ein wenig Geschick und Präzisionsarbeit gefragt. Das Infrarot Sender/Empfänger-Paar des Sensors musste mittig millimetergenau über der Drehscheibe ausgerichtet werden und geradlinig auf die Drehscheibe zeigen. Bei den ersten versuchen hatte ich ein Schaumstoffkissen und Kreppband zum Befestigen verwendet, allerdings mit mäßigem Erfolg, da der Sensor immer wieder verrutscht ist und die Umdrehung dann nicht mehr erfassen konnte. Nach intensivem Durchsuchen des Kellers nach einer brauchbaren Halterung für den Sensor, habe ich schließlich etwas gefunden, das ich nicht wirklich beschreiben kann, da ich keine Ahnung habe, wofür das Kunststoffteil eigentlich gut ist. Es hat sich aber in Verbindung mit starkem doppelseitigem Klebeband als hervorragende Halterung für den Sensor herausgestellt.

Zum Umwandeln der ausgelenen Signale des Infrarotsensors in einen Verbrauchswert und einen Zählerstand habe ich mir eine eigene ESPHome-Komponente geschrieben und auf GitHub zusammen mit einer ausführlichen Dokumentation veröffentlicht. Den Link findest du auf der Projektseite im Abschnitt [Ferraris Meter]({% link _tabs/projects.md %}#ferraris-meter).
