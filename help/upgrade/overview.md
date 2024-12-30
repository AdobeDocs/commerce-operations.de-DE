---
title: Überblick über den Upgrade-Prozess
description: Erfahren Sie, wie ein Upgrade Ihres Adobe Commerce-Projekts dazu beiträgt, dass Ihre Storefront sicher und effizient arbeitet.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 1%

---

# Überblick über den Upgrade-Prozess

Die Aktualisierung Ihres Adobe Commerce-Projekts ist von entscheidender Bedeutung, um sicherzustellen, dass Ihr Geschäft sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird. Dieses Handbuch führt Sie durch die wichtigsten Aspekte bei der Vorbereitung auf ein Upgrade.

Das Handbuch bietet einen Überblick über die typische Adobe Commerce-Upgrade-Journey und Best Practices, die auf dieser Journey befolgt werden sollten. Außerdem werden technische Details des Upgrade-Prozesses mit einem zeitnahen Beispiel und einer schrittweisen Anleitung für die Aktualisierung auf die neueste Version von Adobe Commerce beschrieben. Es ist wichtig, den Adobe Commerce-[ (Veröffentlichungszeitplan) zu überprüfen ](../release/schedule.md) frühzeitig mit der Vorbereitung auf Upgrades zu beginnen. Adobe veröffentlicht jährlich den Veröffentlichungszeitplan, um den Planungsprozess der Händler zu erleichtern, und empfiehlt, jeden Patch-Veröffentlichungszyklus zu aktualisieren. Um PCI-kompatibel zu bleiben, müssen Händler den neuesten Patch oder Sicherheits-Patch verwenden.

## Für wen ist dieser Leitfaden geeignet?

Die Zielgruppe für dieses Handbuch umfasst:

- **E-Commerce-Manager und technische**: Machen Sie sich mit der Upgrade-Journey, der Wichtigkeit regelmäßiger Upgrades und der optimalen Planung und Vorbereitung für ein Upgrade vertraut.
- **Betriebs- und Entwicklungsteams** - Lernen Sie die technischen Schritte kennen, die für ein Upgrade auf die neueste Version von Adobe Commerce erforderlich sind, und lernen Sie die verfügbaren Tools kennen, die den Prozess einfacher, schneller und erschwinglicher machen.

## Aktualisierungsprozess erklärt

Einer der Gründe, warum Sie sich für Adobe Commerce entschieden haben, ist wahrscheinlich:

- Umfassende vorkonfigurierte Funktionen
- SaaS-Funktionen werden getrennt vom Kern-Code angeboten
- Robustes Angebot von Marketplace-Erweiterungen
- Einzigartige Möglichkeit, unendliche Flexibilität zu ermöglichen, sodass Sie Ihre Website so anpassen können, dass sie den Anforderungen Ihres Unternehmens und Ihrer Kunden am besten entspricht

Der Vorteil eines hochgradig erweiterbaren und anpassbaren Produkts kann jedoch zu potenziellen Upgrade-Problemen führen, wenn Anpassungen nicht gemäß Best Practices codiert werden, was zu höheren Upgrade-Kosten als erwartet führt.

_Also… warum überhaupt upgraden?_

Ein Upgrade ermöglicht es Ihrem Unternehmen, in der schnelllebigen und sich ständig verändernden E-Commerce-Branche flexibel zu bleiben, und ermöglicht es Ihnen, Ihre Plattform mit den neuesten Adobe Commerce-Funktionen zu kompatibel zu machen, die Ihnen helfen, den Umsatz und die Konversionen zu maximieren. Die Aufnahme von Upgrades in Ihre regelmäßigen Wartungspläne ist von entscheidender Bedeutung, um sicherzustellen, dass Ihr Geschäft sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird.

### Sicherheit

Sicherheit ist einer der Hauptgründe für Upgrades, da 83 % der Sicherheitsvorfälle auf veralteter Software auftreten. Laut [IBM](https://www.ibm.com/reports/data-breach) betragen die durchschnittlichen Kosten für einen Datenverstoß 3,86 Millionen US-Dollar. Dies ist weit höher als die Kosten für die Minderung dieses Risikos durch Upgrades. Adobe bietet zwei Möglichkeiten, Ihren Store das ganze Jahr über sicher zu halten:

- **Patch-Versionen** - Umfasst Fehlerbehebungen für Sicherheit, Leistung, Qualität und hohe Priorität.
- **Sicherheits-Patch**-Versionen: Umfassen Sie Fehlerbehebungen und Verbesserungen, um Ihre Site sicher und einfacher zu implementieren.

### Leistung

Leistung ist ein weiterer Hauptgrund für Upgrades. Laut [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates) haben die ersten fünf Sekunden der Ladezeit einen signifikanten Einfluss auf die Konversionsraten und jede Sekunde der Latenz hat danach eine Auswirkung von -4,4 %. Dies, zusammen mit der Tatsache, dass die Seitengeschwindigkeit ein führender SEO-Ranking-Faktor ist, zeigt, warum die Site-Leistung ein wichtiges Element Ihrer Site ist, um sie zu pflegen und regelmäßig zu verbessern. Jede Patch-Version enthält Leistungsverbesserungen, sodass die Nutzung neuer Versionen Ihre Wachstumspläne unterstützt und Ihr Unternehmen wettbewerbsfähig bleibt.

### Verspätungskosten

Die Gründe für das Verzögern oder Aufschieben von Plattformaktualisierungen liegen häufig in den unmittelbaren Kosten. Die tatsächlichen Kosten für die Ausführung einer veralteten Version einer Software sind jedoch viel höher und können dauerhafte Auswirkungen auf ein Unternehmen haben.

Es mag der Intuition widersprechen, aber die Durchführung regelmäßiger Plattformaktualisierungen erfordert weniger Gesamtaufwand als die Durchführung unregelmäßiger Aktualisierungen, da sich technische Schulden aus der Verzögerung angehäuft haben. Adobe hat kürzlich mit einem Partner zusammengearbeitet, der über einen Einzelhändler verfügt, der Upgrades selten und inkonsistent (jährlich oder länger) durchgeführt hat. Durch die Umstellung der Vorgehensweise bei Upgrades und die Befolgung eines von Adobe empfohlenen regulären Upgrade-Pfads über einen Zeitraum von 12 Monaten konnte der Partner dem Kunden vier Wochen an kumulierter Entwicklungszeit, Aufwand und damit verbundenen Kosten ersparen. Diese Kosten könnten dann in Initiativen umgelenkt werden, die das Unternehmenswachstum fördern.

Wenn Aktualisierungen regelmäßig durchgeführt werden, erfolgt eine inkrementelle Aktualisierung, und der entsprechende Aktualisierungsaufwand spiegelt dies wider. Wenn Plattformaktualisierungen über einen längeren Zeitraum verschoben werden, können sie zu einem viel aufwändigeren Prozess werden. Außerdem können die Erweiterungen, die Sie vom [Adobe Commerce Marketplace](https://marketplace.magento.com/) und anderen Drittanbieterintegrationen verwenden, ebenfalls betroffen sein. Schließlich wird die Zeit für die Untersuchung, Planung und Durchführung eines verzögerten Upgrades verlängert, was zu vermeidbarem Aufwand und zusätzlichen Kosten führt.

Zu den allgemeinen Faktoren, die sich auf den Aufwand für die Aktualisierung Ihres Projekts auswirken, gehören unter anderem:

| Technische Komplexität | Planung und Strategie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Umfang der Anpassungen | Klarheit der Anforderungen, schwankende Entscheidungen und schleichender Anwendungsbereich |
| Anzahl der Erweiterungen | Ihre Aktualisierungshäufigkeit |
| Anzahl der Integrationen mit Drittanbietern (OMS, ERP) | Ihre Teststrategie |
| Codierung nach Best Practices |                                                              |

Durch das kontinuierliche Wachstum im Bereich des digitalen Handels ist der Druck auf Unternehmen gestiegen, sich schneller, häufiger und auf unvorhersehbare Weise zu entwickeln. Das Versäumnis, Schritt zu halten und das Kaufverhalten der Kunden vorwegzunehmen, hat sogar den größten und etabliertesten Marken gleiche Ausgangsbedingungen geboten. Sie müssen in der Lage sein, robuste, personalisierte Erlebnisse über alle Touchpoints hinweg bereitzustellen, ohne dass es zu Leistungs- und Betriebsunterbrechungen kommt. Sie müssen in der Lage sein, schneller und unbegrenzt Innovationen zu entwickeln, um der globalen Konkurrenz einen Schritt voraus zu sein. Mit einem Upgrade sind Sie in der Lage, Ihr Unternehmen zukunftssicher zu machen und sich für einen besseren Service und dynamische Kundenanforderungen zu rüsten.
