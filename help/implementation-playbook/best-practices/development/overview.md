---
title: Implementierungs-Entwicklungsphase
description: Erfahren Sie mehr über Best Practices für die Implementierung der Entwicklungsphase von Adobe Commerce-Projekten.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%
---

# Entwicklungsphase

Die Entwicklungsphase umfasst die folgenden Aktivitäten:

- Einrichtung der lokalen und Staging-Umgebung
- Sprint-Planung
- Ticketausführung
- Fehlerbehebung
- Überprüfung, Zusammenführen und Testen von Code
- Sprint review
- Kundenabnahme

>[!TIP]
>
>Allgemeine Best [&#x200B; finden Sie &#x200B;](general.md) allgemeinen Empfehlungen zur Gesamtverwaltung des Entwicklungsprozesses.

Die folgenden Abschnitte enthalten Informationen zu Best Practices für die Entwicklungsphase.

## Code-Management

| Best Practice | Beschreibung |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Code-Überprüfung](code-review.md) | Empfohlener Validierungsprozess, um sicherzustellen, dass die implementierte Funktionalität die Anforderungen erfüllt |
| [Composer vs. Git](code-management.md) | Ermitteln, wie benutzerdefinierter Code unter Berücksichtigung von Versionsverwaltung, Codekomplexität und Abhängigkeitsverwaltung verteilt werden kann |
| [Verzweigungsstrategie](git-branching.md) | Verwalten von Quellcode in Git-Repositorys |

## Plattform und Services

| Best Practice | Beschreibung |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Builds und Bereitstellung](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/best-practices){target="_blank"} | Beschreibt Best Practices für die Build- und Bereitstellungsphase von Adobe Commerce in Cloud-Infrastrukturprojekten |
| Debugging | Systematisches und effektives Debugging des Adobe Commerce-Frameworks |
| [Statische Inhaltsbereitstellung](static-content-deployment.md) | Vermeiden Sie Probleme mit statischen Inhalten, die nicht in Ihrer Storefront angezeigt werden |
| [Fehlerbehebung](troubleshooting.md) | Beheben häufiger Adobe Commerce-Implementierungsprobleme |

## Datenbank

| Best Practice | Beschreibung |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Tabellenänderung](modifying-core-and-third-party-tables.md) | Legen Sie fest, wie und wann Adobe Commerce- und Datenbanktabellen von Drittanbietern geändert werden sollen |

## Dateioptimierung

| Best Practice | Beschreibung |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Ändern der Größe von Katalogbildern](catalog-image-resizing.md) | Unterstützung bei der Größenanpassung von Bildern, bevor ein Store in die Produktion geht, um eine optimale Leistung zu gewährleisten |
| [CSS und JS](optimize-css-js-files.md) | Zusammenführen und Minimieren von CSS- (Cascading Style Sheet) und JS-Dateien (JavaScript) über die Admin- oder Befehlszeile |
| [Bilder](image-optimization.md) | Optimieren Sie Bilder und verwenden Sie Fastly, um die Reaktionszeit zu optimieren |

## Frontend-Entwicklung

| Best Practice | Beschreibung |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Design-Entwicklung](https://developer.adobe.com/commerce/frontend-core/guide/best-practices){target="_blank"} | Beschreibt Entwicklungsmuster, die dazu beitragen, die Kompatibilität zwischen Ihrem Design, zukünftigen Versionen von Adobe Commerce und benutzerdefinierten Erweiterungen sicherzustellen |

## PHP-Entwicklung

| Best Practice | Beschreibung |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Ausnahmebehandlung](exception-handling.md) | Beschreibt empfohlene Methoden zum Protokollieren von Ausnahmen |
| [Erweiterungen](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Beschreibt Entwicklungsmuster, die die Kompatibilität zwischen Ihrer Erweiterung, zukünftigen Versionen von Adobe Commerce und anderen benutzerdefinierten Erweiterungen sicherstellen |
| [Private Inhaltsblöcke](private-content-block-configuration.md) | Konfigurieren von privaten Inhaltsblöcken zur Optimierung der Leistung der Storefront |
| [Ändern des Kern- und Drittanbieter-PHP-Codes](modifying-core-and-third-party-code.md) | Ändern Sie die Funktionalität, das Ergebnis oder die Eingabe von Code, den Sie nicht selbst erstellt haben oder nicht direkt steuern |
