---
title: Architektur von verbundenen Storefront
description: Erfahren Sie, was eine gekoppelte Storefront im Kontext von Headless-Adobe Commerce-Architekturen bedeutet.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Closed-Adobe Commerce-Storefront-Architektur (veraltet)

Die aktuelle standardmäßige Bereitstellungsoption für die meisten kommerziellen Kunden umfasst:

- 100 % Funktionsunterstützung für B2B und B2C
- Reife Referenzthemen (Luma), die schnell bereitgestellt/angepasst werden können
- Matutes SI-Partnerimplementierungs-Know-how
- Vollständig kompatibel mit Commerce-Funktionen wie Page Builder oder Staging und Vorschau
- Umfassende Kompatibilität mit Erweiterungen in Adobe Commerce Marketplace

![Abbildung einer gekoppelten Adobe Commerce-Storefront-Architektur](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Inhalt der veralteten Storefront

- **Nicht Headless**—Alle Teile der monolithischen Adobe Commerce-Anwendung. Keine Trennung von Geschäftslogik und Prozessen zwischen Frontend und Backend.

- **Nicht PWA**—Obwohl das Design responsiv ist, liegt die Site-Performance weit hinter dem erstklassigen PWA zurück.

- **Frontend-Architektur (Adobe Commerce-Benutzeroberflächen-Komponenten)**—Adobe Commerce-/PHP-Spezialisten, um auf der alten Storefront aufzubauen.

Bevor wir in Headless-Optionen einsteigen, fangen wir mit der vertrauteren Storefront-Architektur an. Wenn Headless entkoppelt wird, wäre dies die gekoppelte Storefront-Architektur, die am häufigsten mit unseren Luma-Demos zu sehen ist.

Hier sind die Storefront-Funktionen eng in die zentralen Commerce-Dienste integriert, nicht durch diese GraphQL-API-Ebene getrennt. Es gibt also eine Menge Geschäftslogik, die mit diesem Thema verknüpft ist. Dieser Ansatz ist nicht Headless, und er ist nicht PWA.

Dies ist derzeit die häufigste Option, die Händler verwenden, da sie 100 % Funktionsunterstützung mit B2B- und B2C-Commerce-Funktionen bietet. Die Community ist damit vertraut, es gibt ein ausgereiftes Know-how-System, das weit reichende Kompatibilität mit Adobe Commerce Marketplace-Erweiterungen aufweist.

Es fehlt jedoch an den Vorteilen, über die wir zuvor gesprochen haben. Ohne Trennung der Ebenen gibt es viele Abhängigkeiten und potenzielle Fehlerquellen, wenn Änderungen vorgenommen werden. Es ist nicht so leistungsfähig wie eine gut implementierte PWA und wenn ein Händler keine Erfahrung in der Entwicklung von Adobe Commerce oder PHP hat, muss er diese Ressourcen finden.
