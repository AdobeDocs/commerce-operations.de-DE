---
title: Überblick über den Upgrade-Prozess
description: Erfahren Sie, wie Sie durch Upgrades Ihres Adobe Commerce-Projekts die Sicherheit und Effizienz von Storefronts gewährleisten. Erfahren Sie mehr über Best Practices für die Planung und Durchführung erfolgreicher Upgrades.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 16e16980e1b3b021aaaa8c3f1265162f87d5c951
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 2%
---
# Überblick über den Upgrade-Prozess

Die Aktualisierung Ihres Adobe Commerce-Projekts ist von entscheidender Bedeutung, um sicherzustellen, dass Ihr Geschäft sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird. Dieses Handbuch führt Sie durch die wichtigsten Aspekte bei der Vorbereitung auf ein Upgrade.

Das Handbuch bietet einen Überblick über die typische Adobe Commerce-Upgrade-Journey und Best Practices, die auf dieser Journey befolgt werden sollten. Außerdem werden technische Details des Upgrade-Prozesses mit einem zeitnahen Beispiel und einer schrittweisen Anleitung für die Aktualisierung auf die neueste Version von Adobe Commerce beschrieben. Es ist wichtig, den Adobe Commerce-[&#x200B; (Veröffentlichungszeitplan) zu überprüfen &#x200B;](../release/schedule.md) frühzeitig mit der Vorbereitung auf Upgrades zu beginnen. Adobe veröffentlicht jährlich den Versionsplan, um den Planungsprozess für Händler zu erleichtern, und empfiehlt, jeden Patch-Versionszyklus zu aktualisieren. Um PCI-kompatibel zu bleiben, müssen Händler den neuesten Patch oder Sicherheits-Patch verwenden.

## Für wen ist dieser Leitfaden geeignet?

Die Zielgruppe für dieses Handbuch umfasst:

- **E-Commerce-Manager und technische**: Machen Sie sich mit der Upgrade-Journey, der Wichtigkeit regelmäßiger Upgrades und der optimalen Planung und Vorbereitung für ein Upgrade vertraut.
- **Betriebs- und Entwicklungsteams** - Erfahren Sie mehr über die technischen Schritte, die für das Upgrade auf die neueste Version von Adobe Commerce erforderlich sind, und über die verfügbaren Tools, die den Prozess einfacher, schneller und erschwinglicher machen.

## Aktualisierungsprozess erklärt

Einer der Gründe, warum Sie sich für Adobe Commerce entschieden haben, ist wahrscheinlich:

- Umfassende standardmäßige Funktionen
- SaaS-Funktionen werden getrennt vom Kern-Code angeboten
- Robustes Angebot von Marketplace-Erweiterungen
- Einzigartige Möglichkeit, unendliche Flexibilität zu ermöglichen, sodass Sie Ihre Website so anpassen können, dass sie den Anforderungen Ihres Unternehmens und Ihrer Kunden am besten entspricht

Der Vorteil eines hochgradig erweiterbaren und anpassbaren Produkts kann jedoch zu potenziellen Upgrade-Problemen führen, wenn Anpassungen nicht gemäß Best Practices codiert werden, was zu höheren Upgrade-Kosten als erwartet führt.

_Also… warum überhaupt upgraden?_

Ein Upgrade ermöglicht es Ihrem Unternehmen, in der schnelllebigen und sich ständig verändernden E-Commerce-Branche flexibel zu bleiben, und ermöglicht es Ihnen, Ihre Plattform mit den neuesten Adobe Commerce-Funktionen zu kompatibel zu machen, die Ihnen helfen, den Umsatz und die Konversionen zu maximieren. Die Aufnahme von Upgrades in Ihre regelmäßigen Wartungspläne ist von entscheidender Bedeutung, um sicherzustellen, dass Ihr Geschäft sicher, PCI-kompatibel und mit maximaler Effizienz betrieben wird.

### Sicherheit

Sicherheit ist einer der Hauptgründe für Upgrades, da 83 % der Sicherheitsvorfälle auf veralteter Software auftreten. Laut [IBM](https://www.ibm.com/reports/data-breach) betragen die durchschnittlichen Kosten für einen Datenverstoß 3,86 Millionen US-Dollar. Dies ist weit höher als die Kosten für die Minderung dieses Risikos durch Upgrades. Adobe bietet zwei Möglichkeiten, Ihren Store das ganze Jahr über sicher zu halten:

- **Patch-Versionen** - Umfasst Fehlerbehebungen für Sicherheit, Leistung, Qualität und hohe Priorität.
- **[Sicherheits-Patch-Versionen](implementation/perform-upgrade.md#example---security-patch)** - Umfasst Fehlerbehebungen und Verbesserungen, die die Sicherheit Ihrer Site verbessern.

Wenn Sie Adobe Commerce in der Cloud-Version 2.4.4 bis 2.4.9 verwenden, finden Sie im [Hinweis zu Sicherheit und Compliance](../release/security-enforcement-policy.md) die erforderlichen Maßnahmen und Fristen, um Ihre Umgebung sicher und konform zu halten.

### Leistung

Leistung ist ein weiterer Hauptgrund für Upgrades. Laut [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates) haben die ersten fünf Sekunden der Ladezeit einen signifikanten Einfluss auf die Konversionsraten und jede Sekunde der Latenz hat danach eine Auswirkung von -4,4 %. Dies, zusammen mit der Tatsache, dass die Seitengeschwindigkeit ein führender SEO-Ranking-Faktor ist, zeigt, warum die Site-Leistung ein wichtiges Element Ihrer Site ist, um sie zu pflegen und regelmäßig zu verbessern. Jede Patch-Version enthält Leistungsverbesserungen, sodass die Nutzung neuer Versionen Ihre Wachstumspläne unterstützt und Ihr Unternehmen wettbewerbsfähig bleibt.

### Verspätungskosten

Die Gründe für das Verzögern oder Aufschieben von Plattformaktualisierungen liegen häufig in den unmittelbaren Kosten. Die tatsächlichen Kosten für die Ausführung einer veralteten Version einer Software sind jedoch viel höher und können dauerhafte Auswirkungen auf ein Unternehmen haben.

Es mag der Intuition widersprechen, aber die Durchführung regelmäßiger Plattformaktualisierungen erfordert weniger Gesamtaufwand als die Durchführung unregelmäßiger Aktualisierungen, da sich technische Schulden aus der Verzögerung angehäuft haben. Adobe hat kürzlich mit einem Partner zusammengearbeitet, der über einen Einzelhändler verfügt, der Upgrades früher selten und inkonsistent (jährlich oder länger) durchführte. Durch die Umgestaltung des Upgrade-Ansatzes und die Befolgung eines von Adobe empfohlenen regulären Upgrade-Pfads für 12 Monate sparte der Partner dem Kunden vier Wochen Entwicklungszeit, Aufwand und Kosten ein, sodass er diese Kosten auf andere strategische Initiativen umleiten konnte.

Wenn Aktualisierungen regelmäßig durchgeführt werden, erfolgt eine inkrementelle Aktualisierung, und der entsprechende Aktualisierungsaufwand spiegelt dies wider. Wenn Plattformaktualisierungen über einen längeren Zeitraum verschoben werden, können sie zu einem viel aufwändigeren Prozess werden. Außerdem können die Erweiterungen, die Sie vom [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com//) und anderen Drittanbieterintegrationen verwenden, ebenfalls betroffen sein. Schließlich wird die Zeit für die Untersuchung, Planung und Durchführung eines verzögerten Upgrades verlängert, was zu vermeidbarem Aufwand und zusätzlichen Kosten führt.

Zu den allgemeinen Faktoren, die sich auf den Aufwand für die Aktualisierung Ihres Projekts auswirken, gehören unter anderem:

| Technische Komplexität | Planung und Strategie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Umfang der Anpassungen | Klarheit der Anforderungen, schwankende Entscheidungen und schleichender Anwendungsbereich |
| Anzahl der Erweiterungen | Ihre Aktualisierungshäufigkeit |
| Anzahl der Integrationen mit Drittanbietern (OMS, ERP) | Ihre Teststrategie |
| Codierung nach Best Practices |                                                              |

Durch das kontinuierliche Wachstum im Bereich des digitalen Handels ist der Druck auf Unternehmen gestiegen, sich schneller, häufiger und auf unvorhersehbare Weise zu entwickeln. Das Versäumnis, Schritt zu halten und das Kaufverhalten der Kunden vorwegzunehmen, hat sogar den größten und etabliertesten Marken gleiche Ausgangsbedingungen geboten. Sie müssen in der Lage sein, robuste, personalisierte Erlebnisse über alle Touchpoints hinweg bereitzustellen, ohne dass es zu Leistungs- und Betriebsunterbrechungen kommt. Sie müssen in der Lage sein, schneller und unbegrenzt Innovationen zu entwickeln, um der globalen Konkurrenz einen Schritt voraus zu sein. Mit einem Upgrade bereiten Sie Ihr Unternehmen auf zukünftige Anforderungen vor und richten sich auf einen besseren Service für dynamische Kundenanforderungen ein.
