---
title: Referenzarchitektur für Unternehmen
description: Erfahren Sie, wie Sie Adobe Commerce mithilfe der neuesten, zusammenstellbaren Commerce-Technologie von Adobe implementieren.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
source-git-commit: 96afb0ccf5ea872cb42320babfd04ba51fa7dbf6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---


# Adobe Commerce-Referenzarchitektur für Unternehmen

Adobe Commerce ist die erfahrungsgesteuerte Plattform, die technische Flexibilität und Benutzerfreundlichkeit auf einzigartige Weise verbindet und damit außergewöhnliche Erlebnisse schafft, die Geschäftsergebnisse vorantreiben.

Der Handel hat sich entwickelt, um die Anforderungen des Unternehmens an Leistung, Größe und Sicherheit zu erfüllen. Die Einführung eines modernen Implementierungsansatzes, der die neueste, zusammenstellbare Commerce-Lösung verwendet, ist von entscheidender Bedeutung für den Erfolg von Unternehmen. Auf dieser Seite wird der moderne Commerce-Implementierungsansatz im technischen Detail beschrieben.

Das folgende Architekturdiagramm veranschaulicht den Datenfluss zwischen Adobe Commerce und allen Adobe Experience Cloud-Lösungen.

![Architektonisches Diagramm, das zeigt, wie Adobe Commerce eine Verbindung zu Experience Cloud-Lösungen herstellt](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>Die im Diagramm dargestellten Datenflüsse auf hoher Ebene sind bei den meisten Unternehmensimplementierungen konsistent. Die Schlüsselkomponente, die Implementierungen eindeutig machen kann, ist die Art und Weise, wie Sie Ihren Katalog erstellen (insbesondere für B2B). Sie sollten Ihre Katalogarchitektur sorgfältig der [Commerce-Web-APIs](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud-Stiftung

[Adobe Commerce auf Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) ist die Grundlage Ihrer Commerce-Implementierung. Sie bietet eine [secure](../../security-and-compliance/shared-responsibility.md) automatisierte Hosting-Plattform mit Self-Service-Ansatz für die Erstellung, Bereitstellung, Überwachung und Verwaltung Ihrer Commerce-Anwendung in einer Cloud-nativen Umgebung.

Weitere Informationen finden Sie unter den folgenden technischen Details zur Cloud Foundation:

- [**Skalierte Architektur**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—Automatische Anpassung der Kapazität, um eine stabile, vorhersehbare Leistung zu gewährleisten
- [**Mehrere Umgebungen**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—Vorab mit PHP, MySQL (MariaDB), Redis, RabbitMQ bereitgestellt und unterstützte Suchmaschinentechnologien zum Entwickeln, Testen und Bereitstellen Ihrer Site
- [**Konfigurationsverwaltung**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)—Konfigurationsdateien für die anpassbare Umgebung und Befehlszeilenschnittstelle (CLI) zum Verwalten von Anwendungseinstellungen, Routen, Erstellen und Bereitstellen von Aktionen und Benachrichtigungen.
- [**Git-basierter Workflow**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow)—Automatisches Erstellen und Bereitstellen nach dem Pushen von Code-Änderungen für eine schnelle Entwicklung und kontinuierliche Bereitstellung
- [**Integrierte Beobachtbarkeit**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)—Tools, die Protokolldaten aus mehreren Quellen kombinieren, um Sie bei der Verwaltung der Leistung Ihrer Site und der Diagnose von Problemen zu unterstützen
- [**Umfassende API-Abdeckung**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) und [REST](https://developer.adobe.com/commerce/webapi/rest) APIs zur Integration der Commerce-Hauptanwendung in Drittanbietersysteme und Erweiterung der Commerce-Funktionen

## Integration mit Experience Cloud

Adobe Commerce ist mit allen Experience Cloud-Lösungen integriert, um [personalisierte Commerce-Erlebnisse in großem Maßstab](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Datenverbindung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) bietet Einblicke in das Kaufverhalten Ihrer Kunden, sodass Sie mit anderen Adobe Digital Experience-Produkten kanalübergreifend personalisierte Einkaufserlebnisse erstellen können.

>[!NOTE]
>
>Siehe [Entwürfe für digitale Erlebnisse](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) für weitere technische Details.


## Integration mit Drittanbietersystemen

Adobe bietet Entwicklern umfassende Erweiterungspunkte und Tools zum Erstellen von Anwendungen, die die Commerce-Kernfunktionen erweitern und Commerce mit Drittanbietersystemen (z. B. CRMs, ERPS und PIMS) integrieren. Diese Tools reduzieren Ihre Gesamtbetriebskosten für die Plattform wie folgt:

- **Skalierbarkeit**—Anwendungen können getrennt von der Kernsoftware skaliert werden, was eine höhere Effizienz und vereinfachte Upgrades ermöglicht.
- **Isolierung**-Eine isolierte Umgebung bedeutet, dass Entwickler ihre Erweiterungen nach eigenem Ermessen aktualisieren oder ändern können, ohne auf eine Kernversion angewiesen zu sein.
- **Technologische Unabhängigkeit**-Entwickler können wählen, welche Technologie-Stacks und Programmiersprachen ihren Bedürfnissen entsprechen.

Adobe bietet die folgenden Entwicklertools zum Erstellen von Integrationen und Anpassungen:

- [**API-Mesh für Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/)—Koordinieren und Kombinieren mehrerer API-, GraphQL-, REST- und anderer Quellen zu einem einzigen, abfraglichen GraphQL-Endpunkt.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/)—Erstellen und implementieren Sie sichere und skalierbare Webanwendungen, die die Commerce-Funktionalität erweitern und in Lösungen von Drittanbietern integrieren.
- [**Veranstaltungen**](https://developer.adobe.com/commerce/extensibility/events/)—Verwenden Sie benutzerdefinierte Ereignis-Trigger, um mit anderen erweiterbaren Entwicklungstools zu interagieren.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/)—Verwenden Sie Webhooks, um die Interaktionen zwischen Commerce- und Drittanbietersystemen automatisch Trigger.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)- Passen Sie den Commerce Admin an und erweitern Sie ihn mit neuen Seiten und Funktionen für Ihre Händler.

## Storefront-Dienste

Adobe bietet ein umfangreiches Sortiment an intelligenten, zusammenstellbaren Merchandising-Dienstleistungen, die Ihnen helfen, Ihre wichtigsten Geschäftsziele zu erreichen. Diese Dienste bieten auch APIs, die für die Optimierung der Leistung im großen Maßstab entscheidend sind.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)—Mit diesem KI-gestützten Suchwerkzeug können Sie intelligentere, schnellere und relevante Ergebnisse für Käufer erzielen.
- [Produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)- Fügen Sie KI-gestützte Empfehlungen hinzu, die auf dem Verhalten von Käufern, beliebten Trends, der Produktähnlichkeit und mehr basieren.
- [Catalog Service](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview)- Bieten Sie Ihren Kunden ein optimiertes Produkterlebnis, verbessern Sie gleichzeitig die Leistung, verbessern Sie die Skalierbarkeit und steigern Sie die Konversionsrate.
- [Zahlungsdienste](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)—Steigerung der Kundenzufriedenheit durch das Angebot verschiedener Zahlungsmethoden, einschließlich zinsfreier Zahlungseinsätze, und einen einheitlichen Einblick in die Zahlungsverarbeitung, Bestellungen und Rechnungen.

## Headless-Storefront

Headless Commerce ist API-First Commerce. Adobe Commerce ist vollständig Headless mit einer entkoppelten Architektur, die alle Commerce-Services und Daten über eine GraphQL-API-Ebene bereitstellt. Diese Architektur ermöglicht es Teams, ihre Frontends unabhängig von der Kernanwendung zu entwickeln, wodurch neue Touchpoints mit neuen Technologien schnell erstellt und getestet werden können.

Adobe bietet eine moderne, Headless-Storefront-Technologie, die die gleichen Vorteile und Funktionen aufweist, die von [Edge Delivery Services](https://www.aem.live/home) mit dokumentbasiertem Authoring, einer leistungsstarken Architektur und nativen Experimenten. Sie nutzt den Umfang und die Leistung von Adobe Commerce [Storefront-Dienste](#storefront-services) und die Flexibilität und Bequemlichkeit [Dropdown-Komponenten](https://experienceleague.adobe.com/developer/commerce/storefront/) um Commerce-Funktionen bereitzustellen.
