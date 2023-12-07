---
title: Entwicklungsphase der Implementierung
description: Erfahren Sie mehr über die Best Practices für die Implementierung in der Entwicklungsphase von Adobe Commerce-Projekten.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: ce386611834c4199e34b5d95ce76254957821f46
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# Entwicklungsphase

Die Entwicklungsphase umfasst die folgenden Aktivitäten:

- Lokale Einrichtung der Staging-Umgebung
- Raumplanung
- Ticketausführung
- Fehlerbehebung
- Codeüberprüfung, -zusammenführung und -test
- Sprint-Überprüfung
- Kundenabmeldung

>[!TIP]
>
>Siehe [Allgemeine Best Practices](general.md) für Empfehlungen auf hoher Ebene zur Gesamtverwaltung des Entwicklungsprozesses.

Die folgenden Abschnitte enthalten Informationen zu Best Practices für die Entwicklungsphase.

## Code-Management

| Best Practice | Beschreibung |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Codeüberprüfung](code-review.md) | Empfohlener Validierungsprozess, um sicherzustellen, dass die implementierte Funktionalität die Anforderungen erfüllt |
| [Composer vs. Git](code-management.md) | Bestimmen Sie, wie Sie benutzerdefinierten Code unter Berücksichtigung der Versionsverwaltung, der Code-Komplexität und der Abhängigkeitsverwaltung verteilen. |
| [Verzweigungsstrategie](git-branching.md) | Quellcode in Git-Repositorys verwalten |
| [GRA-Beispiele](../../architecture/global-reference/examples.md) | Grundlegendes zu den gemeinsamen Methoden zur Organisation einer [globale Referenzarchitektur](../../architecture/global-reference/overview.md) Codebasis |

## Datenbank

| Best Practice | Beschreibung |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Tabellenänderung](modifying-core-and-third-party-tables.md) | Bestimmen, wie und wann Adobe Commerce- und Drittanbieter-Datenbanktabellen geändert werden |

## Dateioptimierung

| Best Practice | Beschreibung |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Größe des Katalogbilds ändern](catalog-image-resizing.md) | Bietet Anleitungen zur Größenanpassung von Bildern, bevor ein Store in die Produktion aufgenommen wird, um eine optimale Leistung zu gewährleisten |
| [CSS und JS](optimize-css-js-files.md) | Zusammenführen und Minimieren von Cascading Style Sheets (CSS)- und JavaScript (JS)-Dateien aus dem Admin oder der Befehlszeile |
| [Bilder](image-optimization.md) | Optimieren von Bildern und Verwenden Sie Fastly zur Optimierung der Reaktionszeit. |

## Frontend-Entwicklung

| Best Practice | Beschreibung |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Designentwicklung](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Beschreibt Entwicklungsmuster, um die Kompatibilität zwischen Ihrem Design, zukünftigen Versionen von Adobe Commerce und benutzerdefinierten Erweiterungen sicherzustellen |

## PHP-Entwicklung

| Best Practice | Beschreibung |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Ausnahmebehandlung](exception-handling.md) | Beschreibt empfohlene Methoden für die Protokollierung von Ausnahmen |
| [Erweiterungen](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Beschreibt Entwicklungsmuster, um die Kompatibilität zwischen Ihrer Erweiterung, zukünftigen Versionen von Adobe Commerce und anderen benutzerdefinierten Erweiterungen sicherzustellen |
| [Private Inhaltsbausteine](private-content-block-configuration.md) | Konfigurieren privater Inhaltsbausteine zur Optimierung der Storefront-Leistung |
| [Ändern des Kern- und Drittanbieter-PHP-Codes](modifying-core-and-third-party-code.md) | Ändern Sie die Funktionalität, das Ergebnis oder die Eingabe von Code, den Sie nicht erstellt haben oder den Sie nicht direkt steuern |

## Plattform und Dienste

| Best Practice | Beschreibung |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Builds und Bereitstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html){target="_blank"} | Beschreibt Best Practices für die Build- und Bereitstellungsschritte von Adobe Commerce in Cloud-Infrastrukturprojekten |
| Debugging | Systematisches und effektives Debugging des Adobe Commerce-Frameworks |
| [Statische Inhaltsbereitstellung](static-content-deployment.md) | Vermeiden Sie Probleme mit statischem Inhalt, der nicht auf Ihrer Storefront angezeigt wird. |
| [Fehlerbehebung](troubleshooting.md) | Beheben häufiger Probleme bei der Implementierung von Adobe Commerce |
