---
title: Wartungsphase der Implementierung
description: Erfahren Sie mehr über die Best Practices für die Implementierung in der Wartungsphase von Adobe Commerce-Projekten.
exl-id: bd052412-a41c-4dbd-9aba-ba2fcac31f2d
feature: Best Practices
source-git-commit: aad06c1c2def87a319426860b47b8e5ff5e96780
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 1%

---

# Erhaltungsphase

Die Wartungsphase umfasst die folgenden Aktivitäten:

- Fehlerbehebung
- Katalogverwaltung
- Konfiguration
- Funktionsverbesserungen
- Indizierung
- Managed Services
- Site-Überwachung
- Upgrades

Die folgenden Abschnitte enthalten Informationen zu Best Practices für die Wartungsphase.

## Fehlerbehebungen

| Best Practice | Beschreibung |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [[!DNL Quality Patches Tool] usage](../../../tools/quality-patches-tool/usage.md) | Anwenden, Zurücksetzen und Anzeigen allgemeiner Informationen zu allen Adobe Commerce-Patches |

## Katalogverwaltung

| Best Practice | Beschreibung |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [Produktkatalog-Management](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/2eea2782fc874047a020391000519f8b/watch?source=CHANNEL) | Commerce &amp; Coffee Recording beschreibt Strategien zur Verwaltung von Produktkatalogen. |

## Konfiguration

| Best Practice | Beschreibung |
|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| [Planen von Admin-Aktualisierungen auf Produktions-Sites](scheduling-admin-updates-in-production.md) | Verwalten Sie wichtige Adobe Commerce-Aktualisierungen, um zu verhindern, dass die Leistung zu langsam und zu Ausfällen führt. |

## Datenbankverwaltung

| Best Practice | Beschreibung |
|----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [Beheben von Problemen mit der Datenbankleistung &#x200B;](resolve-database-performance-issues.md) | Behebung von Datenbankproblemen, die die Leistung auf Adobe Commerce-Sites verlangsamen, die in der Cloud-Infrastruktur bereitgestellt werden. |
| [Voraussetzungen für das Adobe Commerce 2.3.5-Upgrade für MariaDB-&#x200B;](commerce-235-upgrade-prerequisites-mariadb.md) | Bereiten Sie Ihre MariaDB-Datenbank auf ein Upgrade vor. |

## Funktionsverbesserungen

| Best Practice | Beschreibung |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| [Personalisierung](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/e218545a77de490fb5102eca07d0580a/watch?source=CHANNEL) | Commerce- und Kaffeeaufzeichnung, die Personalisierungsstrategien beschreibt. |
| [E-Commerce-Trends](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/9a772468d7b64409a3d5dff4d67e656d/watch?source=CHANNEL) | Commerce- und Kaffeeaufzeichnung, die E-Commerce-Trends beschreibt. |
| [KI-Automatisierung](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/27ae23699c2847be981a23ca098e548f/watch?source=CHANNEL) | Commerce &amp; Coffee-Recording, das Personalisierungsmöglichkeiten mit künstlicher Intelligenz und Automatisierung beschreibt. |

## Indizierung

| Best Practice | Beschreibung |
|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| [Neuindizierung](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) | Verwenden Sie Cron-Aufträge oder das CLI-Tool, um die Neuindizierung auszuführen. |
| [Konfigurieren von Indexern &#x200B;](indexer-configuration.md) | Optimieren Sie die Site-Leistung durch Befolgen der Best Practices für die Indexkonfiguration. |
| [Bestellverarbeitung](order-processing-configuration.md) | Verbessern Sie die Leistung bei der Kasse- und Auftragsverarbeitung. |

## Site-Überwachung

| Best Practice | Beschreibung |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Leistung des Frontend überprüfen](frontend-performance.md) | Mithilfe von Webleistungswerkzeugen können Sie Probleme identifizieren und beheben, die die Leistung der Website beeinträchtigen. |
| [Bereit, Festlegen, Verwalten](https://business.adobe.com/blog/basics/ready-set-maintain) | Tipps zur Verwaltung Ihrer Adobe Commerce-Sites, um den Geschäftswert und die Betriebszeit zu maximieren. |
| [Verwenden Sie die [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Zeigen Sie wichtige Einblicke über Ihre Adobe Commerce-Site an einem Ort an. |
| [Überwachen der Leistung, des Festplattenspeichers und der Protokolle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) | Verwenden Sie New Relic, um wichtige Leistungseinblicke zu Ihrer Adobe Commerce auf der Cloud-Infrastruktur-Site zu überwachen. |

### Upgrades

| Best Practice | Beschreibung |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| [Patchen im Maßstab](patching-at-scale.md) | Erfahren Sie, wie Sie durch zentrales Patchen für Adobe Commerce Unternehmensprojekte verwalten können. |
| [Aktualisierung von Diensten und Komponenten auf die neueste Version &#x200B;](update-services.md) | halten Sie Ihre Adobe Commerce auf dem neuesten Stand der Cloud-Infrastruktur-Technologie. |
| [Checkliste für die Aktualisierung von Adobe Commerce &#x200B;](upgrade-checklist.md) | Erstellen Sie eine Checkliste für das Upgrade und planen Sie Ihre Adobe Commerce-Upgrade-Strategie. |
