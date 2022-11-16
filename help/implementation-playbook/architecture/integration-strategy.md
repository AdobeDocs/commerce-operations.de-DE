---
title: Adobe Commerce-Integrationsstrategie
description: Überprüfen Sie die Integrationsstrategien und -optionen für Ihre Adobe Commerce-Implementierung.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce-Integrationsstrategie

Die Integration Ihrer Plattform ist &quot;nicht verhandelbar&quot;. Die Unternehmen wollen, dass ihre E-Commerce-Plattformen von verschiedenen Touchpoints aus zugänglich sind und nahtlos in ihre Technologiesysteme integriert werden, insbesondere in ihr ERP. Anpassungsfähigkeit, globale Skalierbarkeit und Erschwinglichkeit spielen auch beim endgültigen Kauf der Plattform eine Rolle.

Ein ganzheitlicher Integrationsansatz für Storefront- und Backend-Systeme wird von leistungsstarken GraphQL-APIs, umfassenden REST-APIs und dem Batch-Dateiimport zwischen Adobe Commerce und anderen Systemen oder Diensten unterstützt.

Die Adobe Commerce GraphQL-API bietet eine umfassende Storefront-Abdeckung, die Sie zur Integration mit anderen Storefronts verwenden können, darunter:

- Digitale Erlebnisplattformen (DXPs) wie Adobe Experience Manager und Bloomreach
- Content Management Systeme (CMS) wie Drupal und WordPress
- Moderne benutzerdefinierte Storefront-Anwendung wie Adobe Commerce, PWA Studio und Vue Storefront

GraphQL bietet eine effiziente, kanalspezifische Antwort, kein übermäßiges Abrufen von Daten und eine agile Implementierung neuer Touchpoint-Funktionen. Es wird auch oft ausgewählt, um eine Integration mit Vertriebskanälen wie mobilen nativen Apps, POS, IoT, Social-Kanälen und livestream-Commerce-Kanälen wie Facebook, Google, Instagram, WeChat und TikTok zu ermöglichen.

Die Adobe Commerce REST API bietet umfassende Systemkonfigurationsfunktionen und Datenverwaltungsfunktionen, einschließlich Produkt- und Katalogfunktionen. Warenkorb, Anführungszeichen und Checkout; Kunden, Konten und Unternehmen; und bestellt und zurückgibt. REST-APIs unterstützen Massenvorgänge, mehrere Authentifizierungsmodi und die granulare Autorisierung, sodass REST-APIs häufig zur Integration in Unternehmenssysteme ausgewählt werden, darunter:

- Enterprise Resource Planning (ERP)-Systeme wie SAP
- PIM-Systeme (Product Information Management) wie Akeneo
- CRM-Systeme (Customer Relationship Management) wie Salesforce
- Order Management Systems (OMS) wie MOM, Manhattan und SAP
- Warehouse Management System (WMS) oder Drittanbieter-Logistik (3PL) wie Oracle, NetSuite und SAP WM
- Konfigurieren, Preis, Zitat (CPQ) wie SalesforceCPQ
- Digital Asset Management (DAM) wie Adobe DAM.

Batch-Dateiimporte werden auch als eine gute Option zur Integration von Unternehmenssystemen wie ERPs und PIMs betrachtet, da sich diese Daten nicht sehr häufig ändern und Sie häufig eine bessere Leistung bei geplanten Dateiimporten haben. Batch-Dateiimporte werden also normalerweise für die tägliche/wöchentliche Massendatensynchronisation und für die monatliche vollständige Datensynchronisation ausgewählt, während REST-APIs für die schrittweise Datensynchronisation zur Leistungsverbesserung ausgewählt werden. Dies gilt auch nur als geplanter Auftrag, kann aber je nach Geschäftsanforderungen häufig - potenziell alle 15 Minuten bis 1 Stunde - durchgeführt werden.

## Integrationsoptionen

Adobe Commerce bietet drei flexible Integrationsoptionen:

- Direkte Integration von System zu System mit vordefinierten Connectoren. Einige Systeme verfügen möglicherweise bereits über Adobe Commerce-Erweiterungen auf dem Adobe Commerce Marketplace oder ihrer eigenen Website.

- Integration von System zu System durch benutzerdefinierte Middleware. Die bereitgestellte benutzerdefinierte Middleware-Lösung wird für die Zuordnung, Übersetzung und Verwaltung von Prozessdaten verwendet.

- Integration von System zu System über iPaaS (Integration Platform-as-a-Service), auch als EAI (Enterprise Application Integration Platform) bezeichnet, z. B. Mulesoft, Boomi und Software AG.

![Adobe Commerce-Integrationsoptionen](../../assets/playbooks/integration-options.svg)

Auch wenn Echtzeit-Integrationen normalerweise gewünscht werden, ist dies für einige Szenarien nicht erforderlich. Adobe Commerce unterstützt nativ [!DNL RabbitMQ] als Message-Bus zum Aktivieren asynchroner Prozesse, was für einige Daten empfohlen wird, die nicht in Echtzeit ausgetauscht werden müssen, sondern mit der Batch-Dateiaustausch- oder REST-Batch-Datenverarbeitungs-API aktualisiert werden, um eine asynchrone Verarbeitung zu ermöglichen.
