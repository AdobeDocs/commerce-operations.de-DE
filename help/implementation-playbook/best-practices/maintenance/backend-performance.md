---
title: Optimieren der Backend-Leistung
description: Erfahren Sie mehr über die Optimierung der Backend-Leistung von Adobe Commerce Sites.
badge: label="Von Objektquelle beigetragen" type="Informative" url="https://objectsource.co.uk/" tooltip="Objektquelle"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: d884d434e696a911de626dc76983468556cf451f
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# Best Practices für die Optimierung der Backend-Leistung

In diesem Abschnitt werden Best Practices für die Untersuchung und Optimierung der Backend-Leistung von Adobe Commerce Sites mit Schwerpunkt auf Datenbankoptimierung und -tests beschrieben. Entwickler können diese Informationen verwenden, um den eindeutigen Kontext jedes Commerce-Projekts zu untersuchen und Möglichkeiten zur Optimierung der Backend-Konfiguration und -Vorgänge zur Verbesserung der Site-Leistung zu identifizieren.

>[!NOTE]
>
>Empfehlungen und Beispiele sind von Prozessen inspiriert, denen die Objektquelle bei realen Kundeninteraktionen folgt, um Adobe Commerce Sites im benötigten Umfang bereitzustellen.

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Datenbank optimieren, um die Leistung zu verbessern

Die Datenbankoptimierung ist eine sichere Möglichkeit, das Benutzererlebnis zu verbessern und den Umsatz zu steigern. Wenn Sie die Datenbank optimieren, das Rückgrat einer Commerce-Site, können Sie eine langsame Website-Performance verhindern und lange Ladezeiten vermeiden, die zu Reibung für Kunden führen.

### Belastungstest

In Zeiten hohen Traffics wie Black Friday müssen Commerce-Sites massives Traffic-Volumen verarbeiten. Zur Vorbereitung auf solche Ereignisse sind Stresstests unerlässlich, um zu verstehen, wie eine Site unter exponentiell steigender Last arbeitet.

Ein Tool, das Sie für Belastungstests verwenden können, ist GTmetrix. Die Belastungsbereitschaft der Messstelle nimmt zu, indem die GTmetrix so konfiguriert wird, dass das normale Verhalten und die normalen Aktionen der Besucher repliziert und multipliziert werden. Führen Sie dann Tests durch, um Probleme zu identifizieren und zu beheben, die sich bei wichtigen Einkaufsereignissen auf die Leistung und Site-Verfügbarkeit auswirken können.

Erfahren Sie mehr über die Vorbereitung von Commerce-Projekten für Zeiträume mit hohem Traffic:

- [Holiday Readiness](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html?lang=de)
- [Holiday Shopping Analysis](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html?lang=de)
- [Überspannungskapazität erhöht](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html?lang=de)

### Belastungstests

Sie können auch GTmetrix oder ein ähnliches Tool verwenden, um Commerce-Projekte zu laden und zu testen. Lasttests sind als Vorläufer von Belastungstests eine unverzichtbare Praxis für große Sites mit hohem Traffic-Aufkommen. Vermeiden Sie unerwartete Site-Ausfälle, frustrierte Kunden und finanzielle Verluste, indem Sie Probleme antizipieren und abmildern, die die Site-Leistung bei Spitzenlasten beeinträchtigen.

Verwenden Sie GTmetrix, um hohen Traffic zu simulieren und die Site-Performance zu analysieren, um klare Informationen über die Site-Kapazität zu erhalten. Diese Analyse hilft dabei, Engpässe zu identifizieren und zu beheben sowie Optimierungsmöglichkeiten zu identifizieren, um sicherzustellen, dass Commerce-Sites bei erhöhter Auslastung effektiv arbeiten können.

Weitere Informationen zum Testen von Adobe Commerce-Projekten:

- [Testanleitung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html?lang=de) (Cloud-Infrastruktur)
- [Anwendungstests](https://developer.adobe.com/commerce/testing/guide/)

### Identifizieren und Beheben von Leistungsproblemen

Beheben Sie Leistungsprobleme, indem Sie verschiedene Tools wie New Relic und Observation for Adobe Commerce verwenden, um Engpässe zu erkennen und Commerce-Sites effektiv zu optimieren. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=de) ist in Adobe Commerce in der Cloud-Infrastruktur enthalten und [Observation for Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) ist sowohl für Cloud- als auch für On-Premise-Bereitstellungen enthalten.

Verwenden Sie diese Tools, um die Leistung der Site zu analysieren und Leistungsprobleme im Zusammenhang mit folgenden Themen zu identifizieren:

- CPU-intensive Funktionen
- Konfiguration der Cache-Verwaltung für Abfragen und Backend-Vorgänge
- API-Aufrufe von Drittanbietern
- Cron-Planung

Beispielsweise können Sie Transaktionen mit Fokus auf Produktdetailseiten und Kategorieseiten genau untersuchen. Identifizieren Sie zeitaufwendige Prozesse, die optimiert werden können, um die Leistung zu verbessern. Bei einer Client-Interaktion stellte die Objektquelle auf einer Produktdetailseite ein Leistungsproblem fest und fand einen API-Aufruf, der 3,5 % der Leistungszeit in Anspruch nahm. Basierend auf diesem Ergebnis untersuchten sie die Hierarchie der Code-Ausführung, um das Problem, das den Engpass verursachte, zu identifizieren und zu beheben.

Weitere Informationen zum Verwalten der Site-Leistung:

- [Leistungsüberwachung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html?lang=de) (Cloud-Infrastruktur)
- [Best Practices für die Konfiguration](/help/performance/configuration.md)
- [Beobachtung für Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Optimieren der MySQL-Leistung

Die Behebung von MySQL-Leistungsproblemen durch die Implementierung von Datenbank-Clustering und Abfrageoptimierung ist ein effektiver Ansatz zur Verbesserung der Leistung vor und während Zeiten mit hohem Traffic wie dem Black Friday.

#### Implementieren von Datenbank-Clustering

Websites mit hohem Traffic sind häufig mit Datenbankengpässen konfrontiert, die in erster Linie durch die Abhängigkeit von einem einzelnen MySQL-Server verursacht werden. Sie können diese Engpässe beheben, indem Sie das Datenbank-Clustering implementieren, eine verteilte Architektur, die die Leistung verbessert und eine hohe Verfügbarkeit sicherstellt.

Datenbank-Clustering minimiert die Auswirkungen von datenbankbezogenen Problemen während Spitzenzeiten des Traffics, indem es mehreren Web-Knoten ermöglicht, eine Verbindung zu mehreren MySQL-Servern herzustellen. Verwenden Sie Tools wie Galera Cluster, um das Datenbank-Clustering für Commerce Sites einzurichten. Der Galera-Cluster ist in [Adobe Commerce-Projekten enthalten, die in der Cloud-Infrastruktur bereitgestellt &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/architecture/pro-architecture).

#### Optimieren von MySQL-Abfragen

In der Regel besteht die Infrastruktur für die meisten Adobe Commerce-Sites aus mehreren Web-Knoten, die mit einem einzigen MySQL-Server verbunden sind.

Bei diesem Setup stellt jeder Frontend-Web-Knoten eine Verbindung zum Galera-Cluster her, was mehrere MySQL-Server ermöglicht. Die Erhöhung der Anzahl der Frontend-Web-Knoten kann die Anwendungsleistung verbessern, aber der einzelne MySQL-Server bleibt ein Engpass.

Um die MySQL Server-Leistung zu optimieren und Engpässe zu minimieren, ist es wichtig, unnötige Abfragen zu identifizieren und zu reduzieren. Wenn Sie beispielsweise 1.000 Abfragen pro Sekunde senden, aber nur 200 erforderlich sind, kann die Optimierung und Verringerung der Abfrageanzahl die Leistung erheblich verbessern.

Weitere Informationen zum Konfigurieren und Optimieren von MySQL:

- [Best Practices für die Datenbankkonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=de)
- [Langsame Replikation für Galera DB-Replikation](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html?lang=de)
- [Allgemeine MySQL-Richtlinien](/help/installation/prerequisites/database/mysql.md)
- [Zwischenspeicherung von MySQL-Abfragen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html?lang=de)

## Cron-Aufträge effektiv verwalten: Leistung und Timing

Cron-Aufträge spielen eine wichtige Rolle bei der Verarbeitung von Site-Hintergrundaufgaben, wie der Berichterstellung und der Produktindizierung. Die Cron-Auftragsoptimierung erfordert jedoch eine sorgfältige Abwägung ihrer Auswirkungen auf die Gesamtleistung. Entwickler müssen die Zeitplanungshäufigkeit bewerten und den optimalen Zeitpunkt anhand spezifischer Anforderungen bestimmen.

Um ein ausgewogenes Verhältnis zwischen Leistung und Komfort zu erzielen, ist es oft ratsam, Cron-Aufträge in verkehrsarmen Zeiten zu planen. Der Umgang mit Kunden in verschiedenen Zeitzonen kann jedoch Herausforderungen mit sich bringen und erfordert einen durchdachten Ansatz, um ein harmonisches Erlebnis über mehrere Regionen hinweg sicherzustellen.

Wenn Sie für die Optimierung der Cron-Leistung und -Zeitplanung verantwortlich sind, überprüfen Sie die aktuelle Cron-Konfiguration vom Commerce-Administrator und erfahren Sie mehr über das Einrichten und Konfigurieren von Cron-Aufträgen für Commerce-Projekte.

Sie können auch Observation for Adobe Commerce verwenden, um cron-bezogene Leistungsindikatoren anzuzeigen. Dieses Tool kombiniert Protokolldaten aus verschiedenen Quellen, um die Leistung der Adobe Commerce-Site besser zu verwalten und Probleme zu diagnostizieren.

Weitere Informationen zur Implementierung von Adobe Commerce Cron:

- [Cron (geplante Aufgaben)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html?lang=de) im _Commerce Admin Systems-Benutzerhandbuch_
- [Anwendungskonfiguration - crons-Eigenschaft](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=de) (Cloud-Infrastruktur)
- [Konfigurieren und Ausführen von &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=de) (lokal)
- [Beobachtung für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=de) (Siehe die Registerkarten [!UICONTROL Cron] und [!UICONTROL MySQL] .)
