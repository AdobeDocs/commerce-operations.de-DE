---
title: Referenzarchitektur für Unternehmen
description: Erfahren Sie, wie Sie Adobe Commerce mithilfe der neuesten, zusammenstellbaren Commerce-Technologie von Adobe implementieren.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 581a7dbcc19c31df80e03cb9f321a6adb5fa1a73
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce-Referenzarchitektur für Unternehmen

Adobe Commerce ist die erfahrungsgesteuerte Plattform, die technische Flexibilität und Benutzerfreundlichkeit auf einzigartige Weise verbindet und damit außergewöhnliche Erlebnisse schafft, die Geschäftsergebnisse vorantreiben.

Commerce hat sich weiterentwickelt, um die Anforderungen des Unternehmens an Leistung, Skalierung und Sicherheit zu erfüllen. Die Einführung eines modernen Implementierungsansatzes, der die neueste, zusammenstellbare Commerce-Lösung verwendet, ist von entscheidender Bedeutung für den Erfolg von Unternehmen. Auf dieser Seite wird der moderne Commerce-Implementierungsansatz im Detail beschrieben.

Das folgende Architekturdiagramm veranschaulicht den Datenfluss zwischen Adobe Commerce und allen Adobe Experience Cloud-Lösungen.

![Architekturdiagramm, das zeigt, wie Adobe Commerce eine Verbindung zu Experience Cloud-Lösungen herstellt](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>Die im Diagramm dargestellten Datenflüsse auf hoher Ebene sind bei den meisten Unternehmensimplementierungen konsistent. Die Schlüsselkomponente, die Implementierungen eindeutig machen kann, ist die Art und Weise, wie Sie Ihren Katalog erstellen (insbesondere für B2B). Sie sollten Ihre Katalogarchitektur sorgfältig den [Commerce-Web-APIs](https://developer.adobe.com/commerce/webapi/get-started/) zuordnen.

## Cloud-Stiftung

[Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) ist die Grundlage Ihrer Commerce-Implementierung. Es bietet eine [sichere](../../security-and-compliance/shared-responsibility.md) automatisierte Hosting-Plattform mit einem Self-Service-Ansatz zum Erstellen, Bereitstellen, Überwachen und Verwalten Ihrer Commerce-Anwendung in einer Cloud-nativen Umgebung.

Weitere Informationen finden Sie unter den folgenden technischen Details zur Cloud Foundation:

- [**Skalierte Architektur**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—Automatisch angepasste Kapazität, um eine stabile, berechenbare Leistung zu gewährleisten
- [**Mehrere Umgebungen**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - Vorkonfiguriert mit PHP, MySQL (MariaDB), Redis, RabbitMQ und unterstützten Suchmaschinentechnologien zum Entwickeln, Testen und Bereitstellen Ihrer Site
- [**Konfigurationsverwaltung**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)—Anpassbare Umgebungskonfigurationsdateien und Befehlszeilenschnittstelle (CLI) zum Verwalten von Anwendungseinstellungen, Routen, Build- und Bereitstellungsaktionen und Benachrichtigungen.
- [**Git-basierter Workflow**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): Erstellen und bereitstellen Sie ihn nach dem Pushen von Code-Änderungen automatisch für eine schnelle Entwicklung und kontinuierliche Bereitstellung
- [**Integrierte Beobachtbarkeit**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) - Tools, die Protokolldaten aus mehreren Quellen kombinieren, um Sie bei der Verwaltung der Leistung und Diagnose Ihrer Site zu unterstützen
- [**Umfassende API-Abdeckung**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) und [REST](https://developer.adobe.com/commerce/webapi/rest) APIs zur Integration der Commerce-Hauptanwendung in Drittanbietersysteme und zur Erweiterung der Commerce-Funktionen

## Integration mit Experience Cloud

Adobe Commerce ist mit allen Experience Cloud-Lösungen integriert, um [personalisierte Commerce-Erlebnisse im Maßstab](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu) bereitzustellen.

[Datenverbindung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) bietet Einblicke in das Kaufverhalten Ihrer Kunden, sodass Sie über alle Kanäle hinweg personalisierte Einkaufserlebnisse mit anderen Adobe Digital Experience-Produkten erstellen können.

>[!NOTE]
>
>Weitere Informationen finden Sie in den folgenden Ressourcen:
>
>- [Entwürfe für digitale Erlebnisse](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) für weitere technische Details.
>- Siehe [Personalisieren des Kundenerlebnisses](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integration mit Drittanbietersystemen

Adobe bietet Entwicklern umfassende Erweiterungspunkte und Tools zum Erstellen von Anwendungen, die die Commerce-Kernfunktionen erweitern und Commerce mit Drittanbietersystemen (z. B. CRMs, ERPS und PIMS) integrieren. Diese Tools reduzieren Ihre Gesamtbetriebskosten für die Plattform wie folgt:

- **Skalierbarkeit**: Anwendungen können getrennt von der Kernsoftware skaliert werden, was eine höhere Effizienz und vereinfachte Aktualisierungen ermöglicht.
- **Isolierung** - Eine isolierte Umgebung bedeutet, dass Entwickler ihre Erweiterungen nach eigenem Ermessen aktualisieren oder ändern können, ohne auf eine Kernversion angewiesen zu sein.
- **Technologische Unabhängigkeit** - Entwickler können wählen, welche Technologie-Stacks und Programmiersprachen ihren Anforderungen entsprechen.

Adobe bietet die folgenden Entwicklertools zum Erstellen von Integrationen und Anpassungen:

- [**API-Mesh für Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/): Koordinieren und kombinieren Sie mehrere API-, GraphQL-, REST- und andere Quellen zu einem einzigen, abfraglichen GraphQL-Endpunkt.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): Erstellen und stellen Sie sichere und skalierbare Webanwendungen bereit, die die Commerce-Funktionalität erweitern und in Lösungen von Drittanbietern integrieren.
- [**Ereignisse**](https://developer.adobe.com/commerce/extensibility/events/): Verwenden Sie benutzerspezifische Ereignis-Trigger, um mit anderen erweiterbaren Entwicklungstools zu interagieren.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) - Verwenden Sie Webhooks, um die Interaktionen zwischen Commerce und Drittanbietersystemen automatisch Trigger.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/): Passen Sie den Commerce-Administrator an und erweitern Sie ihn mit neuen Seiten und Funktionen für Ihre Händler.
- [**Integrationsstarter-Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/): Beschleunigen Sie Ihre Backoffice-Integrationen mit Referenzintegrationen, Onboarding-Skripten und einer standardisierten Architektur.

>[!NOTE]
>
>Siehe [Der moderne Ansatz: Effektive Erweiterbarkeit in Adobe Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Storefront-Dienste

Adobe bietet ein umfangreiches Sortiment an intelligenten, zusammenstellbaren Merchandising-Dienstleistungen, die Ihnen helfen, Ihre wichtigsten Geschäftsziele zu erreichen. Diese Dienste bieten auch APIs, die für die Optimierung der Leistung im großen Maßstab entscheidend sind.

- [Live-Suche](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview): Mit diesem KI-gestützten Suchwerkzeug können Sie intelligentere, schnellere und relevante Ergebnisse für Käufer erzielen.
- [Produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview): Fügen Sie KI-gestützte Empfehlungen hinzu, die auf dem Kundenverhalten, beliebten Trends, der Produktähnlichkeit und mehr basieren.
- [Katalogdienst](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview): Bieten Sie Ihren Kunden ein optimiertes Produkterlebnis, während Sie gleichzeitig die Leistung steigern, die Skalierbarkeit verbessern und Konversionen steigern.
- [Zahlungsdienste](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview): Steigern Sie die Kundenzufriedenheit, indem Sie verschiedene Zahlungsmethoden anbieten, einschließlich zinsfreier Zahlungseinsätze und einer einzigen Ansicht in die Zahlungsverarbeitung, Bestellungen und Rechnungen.

## Headless-Storefront

Headless Commerce ist API-First Commerce. Adobe Commerce ist vollständig Headless mit einer entkoppelten Architektur, die alle Commerce-Services und Daten über eine GraphQL-API-Ebene bereitstellt. Diese Architektur ermöglicht es Teams, ihre Frontends unabhängig von der Kernanwendung zu entwickeln, wodurch neue Touchpoints mit neuen Technologien schnell erstellt und getestet werden können.

Adobe bietet eine moderne, Headless-Storefront-Technologie, die die gleichen Vorteile und Funktionen bietet, die von [Edge Delivery Services](https://www.aem.live/home) mit dokumentbasiertem Authoring, einer leistungsstarken Architektur und nativen Experimenten bereitgestellt werden. Sie nutzt die Skalierung und Leistung von Adobe Commerce [Storefront-Services](#storefront-services) sowie die Flexibilität und den Komfort von [Drop-in-Komponenten](https://experienceleague.adobe.com/developer/commerce/storefront/), um Commerce-Funktionen bereitzustellen.

