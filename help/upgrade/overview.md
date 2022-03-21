---
title: Überblick über den Aktualisierungsprozess
description: Erfahren Sie, wie Sie durch die Aktualisierung Ihres Adobe Commerce- und Magento Open Source-Projekts die Sicherheit und Effizienz Ihrer Storefront gewährleisten können.
source-git-commit: 517e38aa5b0f413503fdb7ba00be8c605cceb570
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---


# Übersicht über den Aktualisierungsprozess

Die Aktualisierung Ihres Adobe Commerce- oder Magento Open Source-Projekts ist entscheidend, um sicherzustellen, dass Ihr Store sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird. Wir haben diesen Leitfaden entwickelt, um Sie durch die wichtigsten Aspekte bei der Vorbereitung auf ein Upgrade zu führen.

Das Handbuch bietet einen Überblick über die typischen Journey und Best Practices für die Aktualisierung von Adobe Commerce/Magento Open Source, die auf dieser Journey folgen. Außerdem werden technische Details des Aktualisierungsprozesses mit einem zeitnahen Beispiel und schrittweisen Anleitungen für die Aktualisierung auf Adobe Commerce/Magento Open Source-Version 2.4.4 beschrieben. Die Patch-Version 2.4.4 wird am 8. März 2022 allgemein verfügbar sein. Daher ist es wichtig, frühzeitig mit der Vorbereitung auf dieses Upgrade zu beginnen, da die [Ende der Lebensdauer (EOL)](https://devdocs.magento.com/release/lifecycle-policy.html) 2022 nähern sich die Daten sowohl für die Zeile 2.3 als auch für die Versionen 2.4.0 bis 2.4.3. Schließlich stellen wir Planungsressourcen und Upgrade-Tools bereit, die Ihren Upgrade-Prozess effizienter machen.

## Für wen ist dieser Leitfaden?

Die Zielgruppe für dieses Handbuch umfasst:

### E-Commerce-Manager und technische Direktoren

Diese Anleitung hilft Kunden in diesen Rollen dabei, die Upgrade-Journey, die Wichtigkeit einer regelmäßigen Aktualisierung und die bestmögliche Planung und Vorbereitung einer Aktualisierung zu verstehen.

### Betriebs- und Entwicklungsteams

Diese Anleitung hilft diesen Teams dabei, die technischen Schritte für die Aktualisierung auf Version 2.4.4 (oder eine beliebige Version von Adobe Commerce/Magento Open Source) und die Tools zu lernen, die sie verwenden können, um den Prozess zu vereinfachen, schneller und erschwinglicher zu machen.

## Aktualisierungsprozess erläutert

Einer der Gründe, aus denen Sie Adobe Commerce/Magento Open Source auswählen, ist wahrscheinlich:

- Umfassender vordefinierter Funktionssatz
- SaaS-Funktionen, die getrennt vom Kerncode angeboten werden
- Robustes Angebot von Marketplace-Erweiterungen
- Einzigartige Möglichkeit, unendliche Flexibilität zu ermöglichen, sodass Sie Ihre Site so anpassen können, dass sie den Anforderungen Ihres Unternehmens und Ihrer Kunden am besten entspricht.

Der Vorteil eines hochgradig erweiterbaren und anpassbaren Produkts kann jedoch potenzielle Aktualisierungsprobleme hervorrufen, wenn Anpassungen nicht nach Best Practices codiert werden, was zu unerwartet hohen Upgrade-Kosten führt.

_Also... warum überhaupt ein Upgrade?_

Durch die Aktualisierung kann Ihr Unternehmen in der schnelllebigen und sich ständig ändernden E-Commerce-Branche ungehindert bleiben und Ihre Plattform ist stets mit den neuesten Funktionen kompatibel, die zur Maximierung von Umsatz und Konversionen beitragen. Die Einbindung von Upgrades in Ihre regulären Wartungspläne ist ebenfalls von entscheidender Bedeutung, um sicherzustellen, dass Ihr Speicher sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird.

### Sicherheit

Sicherheit ist einer der Hauptgründe für die Aktualisierung, da 83 % der Sicherheitsvorfälle auf veralteter Software auftreten. Gemäß [IBM](https://www.ibm.com/security/data-breach)die durchschnittlichen Kosten einer Datenverletzung betragen 3,86 Millionen Dollar - viel höher als die Kosten, die durch eine Aktualisierung entstehen. Adobe bietet zwei Möglichkeiten, Ihren Store ganzjährig sicher zu halten:

- **Patch-Versionen**- Beinhaltet Fehlerbehebungen für Sicherheit, Leistung, Qualität und hohe Priorität.
- **Sicherheits-Patch-Versionen**- Binden Sie Fehlerbehebungen und Verbesserungen ein, um Ihre Site sicher zu halten und die Implementierung zu erleichtern.

### Leistung

Die Leistung ist ein weiterer Hauptgrund für die Aktualisierung. Gemäß [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), wirken sich die ersten fünf Sekunden der Ladezeit signifikant auf die Konversionsraten aus und jede Sekunde Latenz wirkt sich anschließend auf -4,4 % aus. Dies in Verbindung mit der Tatsache, dass die Seitengeschwindigkeit ein führender SEO-Ranking-Faktor ist, zeigt, warum die Site-Performance ein wichtiges Element Ihrer Website ist, um sie zu pflegen und regelmäßig zu verbessern. Jede Patch-Version enthält Leistungsverbesserungen, sodass die Nutzung neuer Releases Ihre Wachstumspläne unterstützt und Ihr Unternehmen wettbewerbsfähig macht.

### Kosten der Verzögerung

Die Gründe für Verzögerungen oder Verzögerungen bei der Aktualisierung der Plattform liegen oft in den unmittelbaren Kosten. Die tatsächlichen Kosten für die Ausführung einer veralteten Version einer Software sind jedoch viel größer und können sich dauerhaft auf ein Unternehmen auswirken.

Es mag intuitiv erscheinen, aber die Durchführung regelmäßiger Plattformaktualisierungen erfordert insgesamt weniger Aufwand als die Durchführung seltener Aktualisierungen aufgrund der Höhe der angesammelten technischen Schulden, die sich aus einer Verzögerung ergeben. Kürzlich haben wir mit einem Partner zusammengearbeitet, der über einen Einzelhandelshändler verfügt, der früher selten und inkonsistent (jährlich oder länger) Upgrades durchgeführt hat. Durch die Umgestaltung der Herangehensweise an Upgrades und die Umsetzung eines von der Adobe empfohlenen regelmäßigen Aktualisierungspfads im Laufe von 12 Monaten konnte der Partner dem Kunden eine kumulative Entwicklungszeit, Mühe und damit verbundene Kosten einsparen, die allesamt auf Initiativen umgeleitet wurden, die das Geschäftswachstum vorantreiben.

Wenn regelmäßig Aktualisierungen vorgenommen werden, sind die Änderungen inkrementell und der entsprechende Aktualisierungsaufwand spiegelt dies wider. Wenn Plattformaktualisierungen für einen längeren Zeitraum verzögert werden, können sie zu einem viel stärker involvierten Prozess werden. Darüber hinaus werden die Erweiterungen verwendet, die Sie aus dem [Marketplace](https://marketplace.magento.com/) und andere Drittanbieterintegrationen ebenfalls betroffen sein können. Schließlich wird die Zeit für die Untersuchung, Planung und Durchführung einer verzögerten Aktualisierung verlängert, was zu vermeidbaren Aufwand und Kosten führt.

Zu den allgemeinen Faktoren, die sich auf den Aufwand für die Aktualisierung Ihres Projekts auswirken, gehören unter anderem:

| Technische Komplexität | Planung und Strategie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Umfang der Anpassungen | Klarheit der Anforderungen, schwindende Entscheidungen und Schlupflöcher |
| Anzahl der Erweiterungen | Aktualisierungshäufigkeit |
| Anzahl der Integrationen mit Drittanbietern (OMS, ERP) | Ihre Teststrategie |
| Kodierung mit Best Practices |  |

Das anhaltende Wachstum des digitalen Handels hat den Druck auf die Unternehmen verstärkt, sich schneller, häufiger und unvorhersehbarer zu entwickeln. Wenn wir das Kaufverhalten der Kunden nicht einhalten und vorwegnehmen, haben wir die Voraussetzungen für selbst die größten, etablierten Marken geschaffen. Sie müssen über alle Touchpoints hinweg in der Lage sein, robuste, personalisierte Erlebnisse ohne Leistungseinbußen und Produktionsausfälle bereitzustellen. Sie müssen in der Lage sein, schneller und unbegrenzt zu innovieren, um den globalen Konkurrenten voraus zu sein. Durch ein Upgrade testen Sie Ihr Unternehmen zukünftig und richten sich selbst auf bessere Service-dynamische Kundenanforderungen ein.

## Versionsplanung 2022

Adobe veröffentlicht eine [Release-Zeitplan](https://devdocs.magento.com/release/) jährlich, um die Planung der Händler zu erleichtern, und empfiehlt, jeden Patch-Release-Zyklus zu aktualisieren. Um PCI-konform zu bleiben, müssen Händler auf dem neuesten Patch oder Sicherheits-Patch installiert sein. Die folgende Zeitleiste zeigt die wichtigsten Release- und EOL-Ereignisse im Jahr 2022.

![](../assets/upgrade-guide/2022-release-timeline.png)

Zu den wichtigen Ereignissen gehören:

- 2.3.x erreicht Ende der Unterstützung (EOS) im September 2022
- 2.4.0 bis 2.4.3 (basierend auf PHP 7.4) erreicht EOS im November 2022, wenn PHP 7.4 das Ende der Lebensdauer (End of Life, EOL) erreicht
- Basierend auf diesen beiden EOS-Ereignissen **Es ist wichtig, bis November 2022 auf Version 2.4.4 oder höher zu aktualisieren.**
- Im Einklang mit der Adobe Commerce [Lebenszyklusrichtlinie](https://devdocs.magento.com/release/lifecycle-policy.html), werden die Versionen 2.4.4 und 2.4.5 bis November 2024 Qualitätsunterstützung und Sicherheits-Patches erhalten

