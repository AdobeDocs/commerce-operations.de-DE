---
title: Adobe Commerce-Erweiterungsstrategie
description: Erfahren Sie, wie Sie mit dem Adobe Commerce-Erweiterungsmodell Ihre Implementierung anpassen können.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Erweiterungsstrategie

Die Erweiterbarkeitsplattform von Adobe Commerce ermöglicht es Marken, Prozesse effizient anzupassen, Systeme zu integrieren und neue Funktionen bereitzustellen, während die Upgradefähigkeit erhalten bleibt.

## Überblick über Commerce-Erweiterungsstrategien

Die Erweiterung der Funktionen der Commerce-Plattform umfasst die folgenden allgemeinen Ansätze:

* Erweiterung der nativen Funktionen der Commerce-Plattform. Händler können beispielsweise Marketplace-Anwendungen (häufig von Drittanbietern erstellt) installieren, die die nativen Funktionen der Plattform erweitern und verfeinern - z. B. eine Erweiterung, die Versandadressen beim Checkout validieren und die schnelle Integration mit UPS-Anbieteradressen-APIs erleichtern kann.

* Integration von Drittanbieteranwendungen/Erweiterungen in die Commerce-Plattform. Entwickler können die vorhandenen, umfassenden REST- und GraphQL-APIs von Commerce verwenden, um Commerce direkt in Drittanbieterlösungen zu integrieren.

Die Plattformarchitektur legt jedoch die besten Strategien für die Erweiterung einer Plattform fest. Commerce bietet umfassende GQL- und REST-API-Abdeckung für Headless-Implementierung. Die zentrale Commerce-Codebasis entwickelt sich weiter zu einer modulareren Architektur und einer einzelnen Integrationsschicht, die neue, verbesserte Anpassungs-Tools bietet:

* [App Builder für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) ist ein Entwicklungs-Framework und -Toolset, das auf der Adobe-Infrastruktur aufbaut. Entwickler können damit Commerce-Erweiterungen erstellen, die von Benutzererlebnis-/Storefront-Anpassungen bis hin zu Middleware- und Business-Logikerweiterungen reichen.

* [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) ermöglicht es Entwicklern, mehrere Datenquellen zu einem einzigen API-Endpunkt zu kombinieren. Dies unterstützt die API-Orchestrierung oder -Integration von privaten und Drittanbieter-APIs und anderen Softwareschnittstellen mit Adobe Commerce-APIs und anderen Adobe-Produkten, die Adobe I/O verwenden.

* [Adobe I/O von Ereignissen für Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) stellt Transaktionsdaten für Anwendungen bereit, die mit App Builder und Webhooks von Drittanbietern entwickelt wurden, und unterstützt so die Erstellung ereignisgesteuerter Anwendungen.

Diese Tools bieten Zugriff auf die Adobe Developer-Konsole und Adobe-Entwicklertools, mit denen APIs erstellt und benutzerdefinierte Plug-ins und Integrationen integriert werden können.

Im folgenden Diagramm werden die wichtigsten Komponenten der Commerce-Erlebnisstrategie dargestellt.

![Strategiediagramm zur Adobe Commerce-Erweiterung](../../assets/playbooks/extensibility-strategy-overview.png)
