---
title: Optimieren der Backend-Leistung
description: Erfahren Sie mehr über die Optimierung der Backend-Leistung von Adobe Commerce-Sites.
badge: label="Von objectsource unterstützt" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
source-git-commit: 2416357d8cacb5627fd24f92b16c2d9839f91082
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Best Practices zur Optimierung der Backend-Leistung

In diesem Thema werden Best Practices für die Untersuchung und Optimierung der Backend-Leistung von Adobe Commerce-Sites mit Schwerpunkt auf Datenbankoptimierung und -tests vorgestellt. Entwickler können diese Informationen verwenden, um den eindeutigen Kontext jedes Commerce-Projekts zu untersuchen und Möglichkeiten zur Optimierung der Backend-Konfiguration und -Vorgänge zu identifizieren, um die Site-Leistung zu verbessern.

>[!NOTE]
>
>Recommendations und Beispiele werden von Prozessen inspiriert, die objektsource in Echtzeit-Kundeninteraktionen nutzt, um leistungsstarke Adobe Commerce-Sites in großem Maßstab bereitzustellen.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Datenbank für verbesserte Leistung optimieren

Die Datenbankoptimierung ist eine sichere Methode, um das Benutzererlebnis zu verbessern und den Umsatz zu steigern. Wenn Sie die Datenbank optimieren, das Rückgrat einer Commerce-Site, können Sie eine langsame Website-Performance verhindern und längere Ladezeiten vermeiden, die für Kunden Reibungsverluste verursachen.

### Belastungstests

In Zeiträumen mit hohem Traffic wie Black Friday wird gefordert, dass Commerce-Sites massive Traffic-Volumen verarbeiten. Zur Vorbereitung auf solche Ereignisse ist Stresstests unerlässlich, um zu verstehen, wie eine Site unter exponentieller Belastung arbeitet.

Ein Werkzeug, das Sie für Stresstests verwenden können, ist GTmetrix. Messen Sie die Site-Bereitschaft für mehr Ladevorgänge, indem Sie GTmetrix so konfigurieren, dass normales Besucherverhalten und -aktionen repliziert und multipliziert werden. Führen Sie anschließend Tests durch, um Probleme zu identifizieren und zu beheben, die sich auf die Leistung und Verfügbarkeit der Website bei wichtigen Einkaufsereignissen auswirken können.

Erfahren Sie mehr über die Vorbereitung von Commerce-Projekten für Zeiträume mit hohem Traffic-Aufkommen:

- [Urlaubsbereitschaft](https://experienceleague.adobe.com/docs/events/mbi-webinars-recordings/2021/holiday-readiness.html)
- [Holiday Shopping Analysis](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Erhöhung der Überlagerungskapazität](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Belastungstests

Sie können auch GTmetrix oder ein ähnliches Tool verwenden, um Commerce-Projekte zu testen. Als Vorstufe zu Stresstests ist Lasttests eine wesentliche Praxis für große, verkehrsreiche Standorte. Verhindern Sie unerwartete Site-Ausfälle, frustrierte Kunden und finanzielle Verluste, indem Sie Probleme vorhersehen und mildern, die sich auf die Site-Leistung bei Spitzenlasten auswirken.

Verwenden Sie GTmetrix, um starken Traffic zu simulieren und die Site-Leistung zu analysieren, um klare Informationen über die Site-Kapazität zu erhalten. Diese Analyse hilft dabei, Engpässe zu identifizieren und zu beheben sowie Optimierungsmöglichkeiten zu identifizieren und sicherzustellen, dass Commerce-Sites bei erhöhter Auslastung effektiv funktionieren können.

Weitere Informationen zum Testen von Adobe Commerce-Projekten:

- [Testleitfaden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  (Cloud-Infrastruktur)
- [Anwendungstests](https://developer.adobe.com/commerce/testing/guide/)

### Ermitteln und Beheben von Leistungsproblemen

Beheben Sie Leistungsprobleme, indem Sie verschiedene Tools wie New Relic und Observation for Adobe Commerce verwenden, um Engpässe zu erkennen und Commerce-Sites effektiv zu optimieren. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) ist in Adobe Commerce in der Cloud-Infrastruktur enthalten und [Beobachtung für Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) ist sowohl für Cloud- als auch für On-Premise-Bereitstellungen enthalten.

Verwenden Sie diese Tools, um die Site-Leistung zu analysieren und Leistungsprobleme im Zusammenhang mit Folgendem zu identifizieren:

- CPU-intensive Funktionen
- Cache-Verwaltungskonfiguration für Abfragen und Backend-Vorgänge
- API-Aufrufe von Drittanbietern
- Cron-Planung

Sie können beispielsweise Transaktionen mit einem Schwerpunkt auf Produktdetails- und Kategorieseiten genau untersuchen. Ermitteln Sie zeitaufwendige Prozesse, die zur Leistungsverbesserung optimiert werden können. Bei einer Kundeninteraktion bemerkte objectsource ein Leistungsproblem auf einer Produktdetailseite und fand einen API-Aufruf, der 3,5 % der Leistungszeit beanspruchte. Auf der Grundlage dieses Ergebnisses untersuchten sie die Hierarchie der Codeausführung, um das Problem zu identifizieren und zu beheben, das den Engpass verursachte.

Erfahren Sie mehr über die Verwaltung der Site-Leistung:

- [Leistungsüberwachung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (Cloud-Infrastruktur)
- [Leistungsoptimierungsprüfung](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [Best Practices bei der Konfiguration](/help/performance/configuration.md)
- [Beobachtung für Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Optimieren der MySQL-Leistung

Die Behebung von Leistungsproblemen bei MySQL durch die Implementierung von Datenbank-Clustering und Abfrageoptimierung ist ein effektiver Ansatz, um die Leistung vor und während Hochdatenverkehrszeiten wie Black Friday zu verbessern.

#### Implementieren von Datenbank-Clustering

Bei Websites mit hohem Traffic-Aufkommen gibt es häufig Datenbankengpässe, die in erster Linie auf die Abhängigkeit von einem einzelnen MySQL-Server zurückzuführen sind. Sie können diese Engpässe beheben, indem Sie Datenbankclustering implementieren, eine verteilte Architektur, die die Leistung verbessert und eine hohe Verfügbarkeit gewährleistet.

Durch das Datenbank-Clustering werden die Auswirkungen datenbankbezogener Probleme während der Traffic-Spitzenzeiten minimiert, da mehrere Webknoten eine Verbindung zu mehreren MySQL-Servern herstellen können. Verwenden Sie Tools wie den Galera-Cluster zum Einrichten von Datenbank-Clustern für Commerce-Sites. Galera Cluster ist enthalten in [Adobe Commerce-Projekte, die in der Cloud-Infrastruktur bereitgestellt werden](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### Optimierung von MySQL-Abfragen

In der Regel besteht die Infrastruktur für die meisten Adobe Commerce-Sites aus mehreren Webknoten, die mit einem einzelnen MySQL-Server verbunden sind.

Bei diesem Setup stellt jeder Frontend-Webknoten eine Verbindung zum Galera-Cluster her, der mehrere MySQL-Server ermöglicht. Eine Erhöhung der Anzahl der Frontend-Webknoten kann die Anwendungsleistung verbessern, doch der einzelne MySQL-Server bleibt ein Engpass.

Um die Leistung des MySQL-Servers zu optimieren und Engpässe zu minimieren, müssen unnötige Abfragen identifiziert und reduziert werden. Wenn Sie beispielsweise 1.000 Abfragen pro Sekunde senden, aber nur 200 erforderlich sind, kann die Leistung durch Optimierung und Verringerung der Abfrageanzahl erheblich verbessert werden.

Erfahren Sie mehr über die Konfiguration und Optimierung von MySQL:

- [Best Practices für die Datenbankkonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Langsame Replikation für die Galera DB-Replikation](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Allgemeine MySQL-Richtlinien](/help/installation/prerequisites/database/mysql.md)
- [Zwischenspeicherung von MySQL-Abfragen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Effektives Verwalten von Cron-Aufträgen: Leistung und Timing

Cron-Aufträge spielen eine entscheidende Rolle bei der Verarbeitung von Site-Hintergrundaufgaben wie der Berichterstellung und der Produktindizierung. Die Optimierung von Cron-Aufträgen erfordert jedoch eine sorgfältige Prüfung ihrer Auswirkungen auf die Gesamtleistung. Entwickler müssen die Planungsfrequenz bewerten und die optimale Zeitplanung anhand bestimmter Anforderungen bestimmen.

Um Leistung und Komfort auszugleichen, ist es oft ratsam, Cron-Aufträge in Zeiten niedrigen Traffics zu planen. Der Umgang mit Kunden in verschiedenen Zeitzonen kann jedoch Herausforderungen mit sich bringen und einen umsichtigen Ansatz verlangen, um ein harmonisches Erlebnis über mehrere Länder hinweg zu gewährleisten.

Wenn Sie für die Optimierung der Cron-Leistung und des Timings verantwortlich sind, überprüfen Sie die aktuelle Cron-Konfiguration vom Commerce Admin und erfahren Sie mehr über das Einrichten und Konfigurieren von Cron-Aufträgen für Commerce-Projekte.

Außerdem können Sie mithilfe der Beobachtung für Adobe Commerce cron-bezogene Leistungsindikatoren anzeigen. Dieses Tool kombiniert Protokolldaten aus verschiedenen Quellen, um Sie bei der besseren Verwaltung der Adobe Commerce-Site-Leistung und der Diagnose von Problemen zu unterstützen.

Weitere Informationen zur Adobe Commerce-Cron-Implementierung:

- [Cron (geplante Aufgaben)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) im _Benutzerhandbuch für Commerce Admin Systems_
- [Anwendungskonfiguration - Eigenschaft &quot;crons&quot;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (Cloud-Infrastruktur)
- [Konfigurieren und Ausführen von Crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (vor Ort)
- [Beobachtung für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (Siehe [!UICONTROL Cron] und [!UICONTROL MySQL] Registerkarten.)
