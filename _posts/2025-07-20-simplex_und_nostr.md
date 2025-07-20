---
title: "Kürzlich entdeckt: SimpleX und Nostr"
date: 2025-07-20 10:30:00 +0001
categories:
  - Empfehlungen
  - Internet
tags:
  - messenger
  - chat
  - protokoll
  - standard
  - client-server architektur
  - netzwerk
  - soziales netzwerk
---

Vor wenigen Wochen habe ich im Internet zwei sehr interessante Dinge entdeckt: SimpleX und Nostr

### SimpleX
[SimpleX](https://simplex.chat/de) ist eine Messenger-Plattform ähnlich wie WhatsApp, Threema oder Signal, die aber einen sehr starken Fokus auf Privatsphäre, Datenschutz und Sicherheit setzt. Die Architektur der Plattform ist von Grund auf und kompromisslos für Privatsphäre und Sicherheit konzipiert. SimpleX verzichtet gänzlich auf Benutzer-IDs, nicht einmal aus Zufallszahlen generierte Kennungen werden verwendet. Dadurch wird ein hohes Maß an Privatsphäre gewährleistet. Die dezentral organisierten Server (genannt "Relays") speichern keinerlei Informationen über die Chat-Teilnehmer und haben keine Kenntnis darüber, wer gerade mit wem kommuniziert. Stattdessen verbleiben sämtliche Informationen über die Benutzer in den Clients. Und falls man den Servern von SimpleX trotz alledem nicht vertraut, ist es auch möglich, eigene Server zu betreiben.

SimpleX unterstützt Messenger-typische Funktionen wie Einzel- und Gruppen-Chats mit Text- und Audio-Nachrichten sowie die Übertragung von Fotos, Videos und beliebigen Dateien. Dazu kommen auch weniger verbreitete Funktionen wie verschwindende Nachrichten und Live-Chats (bei letzterem sieht der Empfänger die Nachricht bereits während sie eingetippt wird). Und natürlich fehlt auch nicht die heutzutage obligatorische Möglichkeit zu Audio- und Video-Anrufen.

In SimpleX ist es möglich, mehrere Profile zu erstellen, um sich verschiedenen Kommunikationspartnern gegenüber unterschiedlich zu präsentieren. Einzigartig ist auch die Möglichkeit, mithilfe des Inkognito-Modus komplett anonym zu agieren. Zusätzliche Anonymisierung bietet zudem noch der unterstützte Zugang über das Tor-Netzwerk.

Sämtlicher Datenaustausch ist durch eine Quantum-resistente Ende-zu-Ende-Verschlüsselung (E2EE) mit Perfect Forward Secrecy und Post-Compromize Security geschützt. SimpleX verwendet dabei den ursprünglich von Signal entwickelten Double-Ratchet Algorithmus, den mittlerweile auch einige andere Messenger wie beispielsweise WhatsApp verwenden. Dazu kommen noch diverse weitere Sicherheitsmaßnahmen, die ich hier aber nicht im Detail beschreiben möchte. Die [Webseite von SimpleX](https://simplex.chat/de) bietet eine ausführliche Dokumentation aller Features und Privatsphäre- sowie Sicherheitskonzepte.

### Nostr
[Nostr](https://nostr.com) (ein Akronym für "Notes and other stuff transmitted by relays") ist ein einfacher Standard, der eine skalierbare Architektur von Clients und Servern definiert, die zur freien Verbreitung von Informationen genutzt werden kann. Er wird von keinem Unternehmen und keiner Regierung kontrolliert, jeder kann auf Nostr aufbauen und jeder kann es nutzen. Einfach gesagt stellt Nostr die Grundlage für offene, freie, dezentrale und Zensur-resistente Netzwerke dar. Nostr wird oft mit dezentralen sozialen Netzwerken wie Mastodon verglichen. Zwar gibt es Gemeinsamkeiten wie den Ansatz der Dezentralisierung, aber Nostr ist viel mehr als das. Nostr ermöglicht den Aufbau verschiedenster Netzwerke im Internet für deren Zugang man aber nur ein einziges Benutzerprofil benötigt.

Ein wichtiger Aspekt bei Nostr ist, dass Nutzer vollständige Kontrolle über ihre Identität (lediglich bestehend aus einem asymmetrischen kryptografischen Schlüsselpaar) haben. Sämtliche Inhalte (sogenannten "Notes") werden mit dem persönlichen privaten Schlüssel signiert, sodass der Ursprung nachgewiesen werden kann und eine Manipulation unmöglich ist. Die dezentral organisierten Server (sogenannte "Relays") sind dabei nur für die Übertragung und Zwischenspeicherung von Inhalten zuständig. Die Server kommunizieren nur mit den Clients, aber nicht untereinander. Sollte man auf einem Server gesperrt werden, kann man die Informationen weiterhin über andere Server übertragen. Und für den extremen Fall, dass man zu keinem Server mehr Zugang bekommt, kann man auf einfache Art und Weise einen eigenen Server betreiben.

Das Nostr-Protokoll ist in vielen kleinen Spezifikationen, den sogenannten NIPs ("Nostr Implementation Possibilities") beschrieben. Das Basis-Protokoll ist in NIP-01 definiert, weitere NIPs spezifizieren zusätzliche, überwiegend optionale Funktionalitäten. Clients und Server können je nach anzubietender Funktion aus verschiedenen Spezifikationen wählen. Dadurch ergibt sich eine vielfältige Client- und Server-Landschaft mit unterschiedlichen Themengebieten.

Auf der [Webseite von Nostr](https://nostr.com) kann man sich ausführlich über die Architektur des Standards informieren. Es gibt bereits eine Vielzahl von Clients für verschiedene Plattformen, die man über die [Nostr Apps Webseite](https://nostrapps.com) oder den [Nostr App Manager](https://nostrapp.link) durchsuchen kann. Einen guten Einstieg in die Welt von Nostr bietet auch die [Njump Webseite](https://njump.me), über die man Profile, Notes und Relays durchsuchen kann.
