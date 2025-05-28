---
title: "Steuere deine Sony HT-XT3"
date: 2022-02-22 10:00:00 +0001
categories:
  - Projekte
  - Smart-Home
tags:
  - smarthome
  - nodered
  - sony
  - htxt3
  - soundbar
  - sounddeck
---

Alles fing im Jahr 2019 an, als ich eine Möglichkeit suchte, meine Soundbar Sony HT-XT3 über Node-RED anzusteuern. Damals hatte ich noch ausschließlich auf Node-RED als Plattform für mein Smart-Home gesetzt und für diese Soundbar gab es noch keine Nodes.

Also beschloss ich, meine eigenen Nodes zu implementieren und das Ergebnis war die erste Generation meines Node-Pakets, bekannt unter dem Namen Node-RED Sony Audio Control. Da ich noch relativ neu bei Node-RED war und insbesondere noch nie vorher eigene Nodes entwickelt hatte, war das Ergebnis alles andere als optimal. Deshalb beschloss ich drei Monate später, die Implementierung komplett zu überarbeiten und die Flow-Nodes von vier auf nur noch zwei zu reduzieren. Das Ergebnis war das Paket Node-RED Sony Audio. Jetzt, drei Jahre später, entschied ich mich erneut, eine grundlegende Änderung an den Nodes vorzunehmen.

Das aktuelle Paket liegt also bereits in der dritten Generation vor. Da ich die Implementierung zweimal komplett überarbeitet habe und dadurch Inkompatibilitäten entstanden sind, hatte ich jeweils beschlossen, ein neues Repository (und damit auch NPM-Paket) zu erstellen. Dadurch wurden die Flows der Nutzer, die die alten Nodes verwendet hatten, nicht beeinflusst und jeder konnte selbst über eine Migration entscheiden.

Falls du Node-RED verwendest und eine Sony HT-XT3 dein Eigen nennst, schau doch einfach mal auf der GitHub-Seite oder den entsprechenden Seiten in der NPM-Registry oder der Node-RED Library vorbei. Die Links findest du auf der Projektseite im Abschnitt [Sony Audio]({% link _tabs/projects.md %}#sony-audio).
