---
title: Übersicht über den Aktualisierungsprozess
description: Erfahren Sie, wie die Aktualisierung Ihres Adobe Commerce-Projekts dazu beiträgt, dass Ihre Storefront sicher ist und effizient funktioniert.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Übersicht über den Aktualisierungsprozess

Die Aktualisierung Ihres Adobe Commerce-Projekts ist entscheidend, um sicherzustellen, dass Ihr Store sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird. Dieses Handbuch führt Sie durch die wichtigsten Aspekte bei der Vorbereitung auf ein Upgrade.

Das Handbuch bietet einen Überblick über die typischen Journey und Best Practices für Adobe Commerce-Upgrades, die auf dieser Journey folgen. Außerdem werden technische Details des Aktualisierungsprozesses mit einem zeitnahen Beispiel und schrittweisen Anweisungen für die Aktualisierung auf die neueste Version von Adobe Commerce beschrieben. Es ist wichtig, die Adobe Commerce zu überprüfen [Veröffentlichungszeitplan](../release/schedule.md) und frühzeitig mit der Vorbereitung auf Upgrades beginnen. Adobe veröffentlicht den Veröffentlichungszeitplan jährlich, um den Planungsprozess für Händler zu erleichtern, und empfiehlt, jeden Patch-Versionszyklus zu aktualisieren. Um PCI-konform zu bleiben, müssen Händler auf dem neuesten Patch oder Sicherheits-Patch installiert sein.

## Für wen ist dieser Leitfaden?

Die Zielgruppe für dieses Handbuch umfasst:

- **E-Commerce-Manager und technische Leiter**—Machen Sie sich mit der Upgrade-Journey vertraut, mit der Wichtigkeit einer regelmäßigen Aktualisierung und mit der optimalen Planung und Vorbereitung eines Upgrades.
- **Betriebs- und Entwicklungsteams**—Erfahren Sie mehr über die technischen Schritte, die für die Aktualisierung auf die neueste Version von Adobe Commerce erforderlich sind, sowie über die verfügbaren Tools, die den Prozess einfacher, schneller und erschwinglicher machen.

## Aktualisierungsprozess erläutert

Einer der Gründe, aus denen Sie Adobe Commerce auswählen, ist wahrscheinlich:

- Umfassender vordefinierter Funktionssatz
- SaaS-Funktionen, die getrennt vom Kerncode angeboten werden
- Robustes Angebot von Marketplace-Erweiterungen
- Eindeutige Möglichkeit, unendliche Flexibilität zu ermöglichen, sodass Sie Ihre Site so anpassen können, dass sie den Anforderungen Ihres Unternehmens und Ihrer Kunden am besten entspricht

Der Vorteil eines hochgradig erweiterbaren und anpassbaren Produkts kann jedoch potenzielle Aktualisierungsprobleme hervorrufen, wenn Anpassungen nicht nach Best Practices codiert werden, was zu unerwartet hohen Upgrade-Kosten führt.

_Also... warum überhaupt ein Upgrade?_

Durch die Aktualisierung kann Ihr Unternehmen in der schnelllebigen und sich ständig ändernden E-Commerce-Branche unnachgiebig bleiben und Ihre Plattform kann mit den neuesten Adobe Commerce-Funktionen kompatibel sein, mit denen Sie Umsätze und Konversionen maximieren können. Die Einbindung von Upgrades in Ihre regulären Wartungspläne ist von entscheidender Bedeutung, um sicherzustellen, dass Ihr Speicher sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird.

### Sicherheit

Sicherheit ist einer der Hauptgründe für die Aktualisierung, da 83 % der Sicherheitsvorfälle auf veralteter Software auftreten. Gemäß [IBM](https://www.ibm.com/reports/data-breach)die durchschnittlichen Kosten einer Datenverletzung betragen 3,86 Millionen Dollar - viel höher als die Kosten, die durch eine Aktualisierung entstehen. Adobe bietet zwei Möglichkeiten, Ihren Speicher ganzjährig sicher zu halten:

- **Patch-Versionen**- Beinhaltet Fehlerbehebungen für Sicherheit, Leistung, Qualität und hohe Priorität.
- **Sicherheits-Patch-Versionen**- Binden Sie Fehlerbehebungen und Verbesserungen ein, um Ihre Site sicher zu halten und die Implementierung zu erleichtern.

### Leistung

Die Leistung ist ein weiterer Hauptgrund für die Aktualisierung. Gemäß [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), wirken sich die ersten fünf Sekunden der Ladezeit signifikant auf die Konversionsraten aus und jede Sekunde Latenz wirkt sich anschließend auf -4,4 % aus. Dies in Verbindung mit der Tatsache, dass die Seitengeschwindigkeit ein führender SEO-Ranking-Faktor ist, zeigt, warum die Site-Performance ein wichtiges Element Ihrer Website ist, um sie zu pflegen und regelmäßig zu verbessern. Jede Patch-Version enthält Leistungsverbesserungen, sodass die Nutzung neuer Releases Ihre Wachstumspläne unterstützt und Ihr Unternehmen wettbewerbsfähig macht.

### Kosten der Verzögerung

Die Gründe für Verzögerungen oder Verzögerungen bei der Aktualisierung der Plattform liegen oft in den unmittelbaren Kosten. Die tatsächlichen Kosten für die Ausführung einer veralteten Version einer Software sind jedoch viel größer und können sich dauerhaft auf ein Unternehmen auswirken.

Es mag intuitiv erscheinen, aber die Durchführung regelmäßiger Plattformaktualisierungen erfordert insgesamt weniger Aufwand als die Durchführung seltener Aktualisierungen aufgrund der Höhe der angesammelten technischen Schulden, die sich aus einer Verzögerung ergeben. Adobe hat kürzlich mit einem Partner zusammengearbeitet, der über einen Einzelhandelsverkäufer verfügt, der früher selten und inkonsistent (jährlich oder länger) Upgrades durchgeführt hat. Durch die Umgestaltung der Herangehensweise an Upgrades und die Befolgung eines von der Adobe empfohlenen regelmäßigen Aktualisierungspfads im Laufe von 12 Monaten konnte der Partner dem Kunden eine kumulative Entwicklungszeit, Mühe und damit verbundene Kosten von vier Wochen sparen. Diese Kosten könnten dann in Initiativen zur Förderung des Unternehmenswachstums umgeleitet werden.

Wenn regelmäßig Aktualisierungen vorgenommen werden, sind die Änderungen inkrementell und der entsprechende Aktualisierungsaufwand spiegelt dies wider. Wenn Plattformaktualisierungen für einen längeren Zeitraum verzögert werden, können sie zu einem viel stärker involvierten Prozess werden. Darüber hinaus werden die Erweiterungen verwendet, die Sie aus dem [Adobe Commerce Marketplace](https://marketplace.magento.com/) und anderen Drittanbieterintegrationen ebenfalls betroffen sein. Schließlich wird die Zeit für die Untersuchung, Planung und Durchführung einer verzögerten Aktualisierung verlängert, was zu vermeidbaren Aufwand und Kosten führt.

Zu den allgemeinen Faktoren, die sich auf den Aufwand für die Aktualisierung Ihres Projekts auswirken, gehören unter anderem:

| Technische Komplexität | Planung und Strategie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Umfang der Anpassungen | Klarheit der Anforderungen, schwindende Entscheidungen und Schlupflöcher |
| Anzahl der Erweiterungen | Aktualisierungshäufigkeit |
| Anzahl der Integrationen mit Drittanbietern (OMS, ERP) | Ihre Teststrategie |
| Kodierung mit Best Practices |                                                              |

Das anhaltende Wachstum des digitalen Handels hat den Druck auf die Unternehmen verstärkt, sich schneller, häufiger und unvorhersehbarer zu entwickeln. Wenn wir das Kaufverhalten der Kunden nicht einhalten und vorwegnehmen, haben wir die Voraussetzungen für selbst die größten, am weitesten etablierten Marken geschaffen. Sie müssen über alle Touchpoints hinweg in der Lage sein, robuste, personalisierte Erlebnisse ohne Leistungseinbußen und Produktionsausfälle bereitzustellen. Sie müssen in der Lage sein, schneller und unbegrenzt zu innovieren, um den globalen Konkurrenten voraus zu sein. Durch ein Upgrade testen Sie Ihr Unternehmen zukünftig und richten sich selbst auf bessere Service-dynamische Kundenanforderungen ein.
