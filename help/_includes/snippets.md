---
source-git-commit: 20add0a748e8df38dff48a779c63e1177d2a022d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---
# Snippets

## Nur Commerce {#commerce-only}

>[!NOTE]
>
>Die [!DNL Upgrade Compatibility Tool] ist nur für Adobe Commerce-Instanzen verfügbar.

<!-- Configuration guide snippets -->

## Dateisysteminhaber {#file-system-owner}

>[!WARNING]
>
>Alle Magento-CLI-Befehle müssen von der [Dateisysteminhaber](/help/configuration/cli/config-cli.md#prerequisites).

## Sicherungsbefehle {#tip-backup-command}

>[!TIP]
>
>Die `support:backup` Befehl ist _not_ die gleiche Codesicherung durch die `setup:backup` Befehl. Die `support:backup` -Befehl dient dazu, den Code für die Prüfung durch den Adobe Commerce-Support zu sichern.

## Nur Adobe Commerce {#ee-only}

>[!NOTE]
>
>Diese Funktion ist nur für Adobe Commerce-Instanzen verfügbar.

## Geteilte DB nicht mehr unterstützt {#deprecate-split-db}

>[!IMPORTANT]
>
>Die Funktion für die geteilte Datenbank war [veraltet](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) in Version 2.4.2 von Adobe Commerce. Siehe [Aus einer geteilten Datenbank in eine einzige Datenbank zurücksetzen](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Abwärtskompatible Änderungen {#bics}

>[!NOTE]
>
>Adobe Commerce- und Magento Open Source-Versionen können abwärtsinkompatible Änderungen (BICs) enthalten. Informationen zum Überprüfen rückwärtsinkompatibler Änderungen finden Sie unter [BIC-Referenz](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Wichtige rückwärtskompatible Probleme werden unter [BIC-Highlights](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Nicht alle Versionen führen wichtige BICs ein.

## CVE-Hinweis {#cve-notice}

>[!NOTE]
>
>Ab Version 2.3.2 werden wir indizierte Common Vulnerabilities and Expositions (CVE)-Zahlen mit jedem Sicherheitsfehler zuweisen und veröffentlichen, der uns von externen Parteien gemeldet wird. Auf diese Weise können Benutzer nicht adressierte Schwachstellen in ihrer Implementierung leichter identifizieren. Weitere Informationen zu CVE-Kennungen finden Sie unter [CVE](https://cve.mitre.org/).

## Weitere Versionsinformationen {#other-release-info}

>[!NOTE]
>
>Obwohl der in diesen Versionshinweisen beschriebene Code für Verbesserungen und Fehlerbehebungen mit Adobe Commerce gebündelt ist, werden mehrere dieser Projekte (z. B. B2B, Page Builder und Progressive Web Application (PWA) Studio) ebenfalls unabhängig voneinander veröffentlicht. Fehlerbehebungen für diese Projekte werden in den separaten, projektspezifischen Versionsinformationen dokumentiert, die in der Dokumentation für jedes Projekt verfügbar sind. Siehe [Produktversion - Übersicht](/help/release/release-notes/overview.md).
