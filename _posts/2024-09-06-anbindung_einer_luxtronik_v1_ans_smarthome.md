---
title: "Anbindung einer Luxtronik V1 ans Smart-Home"
date: 2024-09-06 18:00:00 +0001
categories:
  - Projekte
  - Elektronik
tags:
  - smarthome
  - elektronik
  - esphome
  - homeassistant
  - heizung
  - wärmepumpe
  - alphainnotec
  - ait
  - luxtronik
---

In unserem Haus sorgt eine Alpha Innotec Wärmepumpe für angenehme Temperaturen im Winter. Da die Heizung schon etwas in die Jahre gekommen ist, hat sie eine Heizungssteuerung (Luxtronik V1), die nicht mehr ganz dem aktuellen Stand der Technik entspricht. So verfügt sie über keine Netzwerkschnittstelle, um sie einfach in das Smart-Home einbinden zu können. Zum Glück ist sie aber nicht völlig altertümlich und hat wenigstens eine serielle RS-232-Schnittstelle, sodass es prinzipiell möglich ist, mit dem Gerät zu kommunizieren. Auch wenn diese Schnittstelle eigentlich nur für den Kundendienst gedacht ist, eignet sie sich mit einer kleinen Zusatz-Hardware, die als Gateway zum Netzwerk dient, hervorragend dazu, Daten von der Heizung abzufragen oder diese sogar zu konfigurieren.

Bei der Zusatz-Hardware habe ich mich für einen ESP-Mikrocontroller entschieden, konkret einen ESP32. Den Mikrocontroller konnte ich aufgrund der unterschiedlichen Spannungspegel nicht direkt an die RS-232-Schnittstelle des Luxtronik Heizungssteuergeräts angeschließen. Stattdessen musste ich einen MAX3232-IC verwenden, um zwischen den unterschiedlichen Spannungspegeln auf Luxtronik- und Mikrocontroller-Seite zu konvertieren. Zum Glück gibt es fertige Seriell-zu-TTL Konvertierungsmodulplatinen, die mit einem MAX3232-IC und einem DE-9 (auch D-Sub 9) Stecker ausgestattet sind. Auf der RS-232-Seite haben diese Module einen (meist weiblichen) DE-9-Stecker (an dem aber nur GND, RX und TX verbunden sind) und auf der TTL-Seite haben sie 4 Pins - VCC und GND für die Stromversorgung des Chips sowie RX und TX für die Datenübertragung.

Sinnvollerweise platziert man den Mikrocontroller außerhalb des Wärmepumpengehäuses, um einen besseren Wi-Fi-Empfang und eine einfachere Wartung zu ermöglichen. Es gibt dabei zwei Möglichkeiten, wo die „lange“ Verkabelung zwischen dem Mikrocontroller-Aufbau und der Luxtronik platziert werden kann:

1. Serielles Kabel (fertig oder selbst gebaut), das zwischen dem MAX3232-Modul und der RS-232-Schnittstelle der Luxtronik angeschlossen wird
2. 4-adriges Kabel zwischen dem Mikrocontroller und dem MAX3232-Modul (letzteres wird direkt an die RS-232-Schnittstelle der Luxtronik angeschlossen)

Die meisten im Internet beschriebenen Aufbauten, die ich recherchiert hatte, verwenden Option 1, aber ich habe mich in meinem Fall für Option 2 entschieden. Als Kabel habe ich ein handelsübliches 4-adriges Telefonverlegekabel verwendet. Diese Kabel haben zwei verdrillte Adernpaare (rot + schwarz und weiß + gelb). Die roten und schwarzen Adern sind prädestiniert für VCC bzw. GND. Ich habe dann gelb für RX und weiß für TX gewählt. Die Adern haben jeweils einen Durchmesser von 0,6 mm, sodass der Spannungsabfall bei 3,3V und der sehr geringen Stromstärke bei einer Kabellänge von 2-4 Metern vernachlässigbar ist.

Warum habe ich mich für Option 2 entschieden? Der Grund war, dass fertige serielle Kabel heutzutage schwer zu bekommen und teuer sind und - der wichtigere Grund - die großen DE-9-Steckerenden nicht durch die kleinen Durchlässe im Gehäuse der Wärmepumpe passen. Außerdem wollte ich mir kein eigenes Kabel bauen, denn auch DE-9-Stecker sind schwer zu bekommen und teuer. Für Option 2 habe ich die Drähte an einem Ende des Kabels direkt an die TTL-Pins der MAX3232-Modulplatine gelötet und diese dann direkt an die Luxtronik RS-232-Schnittstelle angeschlossen (mit einem kleinen Nullmodem-Adapter dazwischen, da die RX- und TX-Verbindungen getauscht werden mussten). Für den Mikrocontroller-Aufbau habe ich Buchsenleisten sowie Leiterplatten-Schraubklemmenblöcke auf eine Lochrasterplatine gelötet und die entsprechenden Pins verbunden. An die Buchsenleisten habe ich eine ESP32 NodeMCU-Entwicklungsplatine angeschlossen und konnte dann die Drähte des Telefonkabels einfach an die Schraubklemmen anschließen, nachdem ich das Kabel durch die Durchlässe des Wärmepumpengehäuses geführt hatte.

![Luxtronik V1](/assets/img/posts/luxtronik_v1.jpg)

Zusätzlich zu dem Hardware-Aufbau habe ich mir eine eigene ESPHome-Komponente geschrieben, um die empfangenen Daten besser verarbeiten zu können. Diese ESPHome-Komponente habe ich auf GitHub zusammen mit einer ausführlichen Dokumentation veröffentlicht, damit auch andere davon profitieren können. Den Link findest du auf der Projektseite im Abschnitt [Luxtronik V1]({% link _tabs/projects.md %}#luxtronik-v1).
