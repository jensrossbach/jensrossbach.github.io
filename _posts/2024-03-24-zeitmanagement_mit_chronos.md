---
title: "Zeitmanagement mit Chronos"
date: 2024-03-24 18:20:00 +0001
categories:
  - Projekte
  - Smart-Home
tags:
  - smarthome
  - nodered
  - zeit
  - zeitmanagement
  - zeitschaltuhr
  - sonnenzeit
  - sonnenaufgang
  - sonnenuntergang
---

Im Jahr 2020 war ich auf der Suche nach Node-RED Nodes, um eine automatisierte Steuerung für meine Lampen anhand des Sonnenstands zu realisieren. Und obwohl es dafür bereits Nodes (fast) im Überfluss gab, hatte ich mich trotzdem dazu entschlossen, eigene Nodes zu entwickeln, da mir die damals existierenden Implementierungen alle nicht gefallen hatten. Entweder hatten sie nicht die Funktionalität, die ich brauchte oder die Benutzeroberfläche war zu puristisch oder aber die Nodes waren wiederum viel zu überfrachtet mit Funktionalität. Ich habe im Laufe der Zeit zwar auch immer mehr Funktionalität hinzugefügt, aber ebenso darauf geachtet, dass das User Interface nicht aus allen Nähten geplatzt ist.

![Chronos](/assets/img/posts/chronos.png)

Der erste Node war der Scheduler Node zum geplanten Versenden von Nachrichten. Kurz darauf folgten der Time Switch Node (das zeitbasierte Äquivalent zum Node-RED Switch Node), der Time Filter Node und der Delay Node (damals noch Delay Until Node, um den Unterschied zum Node-RED Delay Node auszudrücken). Einige Releases später folgte dann der Time Change Node (das zeitbasierte Äquivalent zum Node-RED Change Node), danach der Repeat Node und zuletzt dann der State Node (der mehr oder weniger eine zustandsbehaftete Variante des zustandslosen Scheduler Nodes ist). Somit enstand über die Jahre ein umfangreiches Node-Paket zum zeitbasierten Planen, Wiederholen, Verzögern, Leiten, Filtern und Manipulieren von Nachrichten.

Falls du Node-RED verwendest und solche Nodes gebrauchen könntest, schau doch einfach mal auf der GitHub-Seite oder den entsprechenden Seiten in der NPM-Registry oder der Node-RED Library vorbei. Die Links findest du auf der Projektseite im Abschnitt [Chronos]({% link _tabs/projects.md %}#chronos).
