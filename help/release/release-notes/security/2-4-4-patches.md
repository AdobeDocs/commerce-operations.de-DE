---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.4
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.4-Sicherheits-Patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-P13

Die Adobe Commerce-Sicherheitsversion 2.4.4-p13 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

## 2.4.4-P12

Die Adobe Commerce-Sicherheitsversion 2.4.4-p12 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-P11

Die Adobe Commerce-Sicherheitsversion 2.4.4-p11 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-P10

Die Adobe Commerce-Sicherheitsversion 2.4.4-p10 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.4 identifiziert wurden.

Aktuelle Informationen zu den behobenen Sicherheitsfehlern finden Sie im [Adobe Systems Security Bulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Höhepunkte

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

Die Adobe Commerce-Sicherheitsversion 2.4.4-p9 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.4 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Platform Upgrades

* **MariaDB 10.5-Unterstützung**. Diese Patch-Version führt die Kompatibilität mit MariaDB Version 10.5 ein. Adobe Commerce ist weiterhin mit MariaDB Version 10.4 kompatibel. Adobe empfiehlt jedoch die Verwendung von Adobe Commerce 2.4.4-p9 und allen kommenden Nur-Sicherheits-Patch-Versionen 2.4.4 nur mit MariaDB Version 10.5, da MariaDB 10.4-Wartungsarbeiten am 18. Juni 2024 beendet werden. <!--AC-11530-->

### Highlights

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

Die Adobe Commerce-Sicherheitsversion 2.4.4-p8 bietet Fehlerbehebungen für die Sicherheit Ihrer Adobe Commerce-Bereitstellung 2.4.4. Diese Updates beheben Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Die Adobe Commerce-Version 2.4.4-p7 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Highlights

Diese Version führt zwei wichtige Sicherheitsverbesserungen ein:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für -Blöcke enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Vorlagenanweisungssyntax oder die `setCacheKey`- oder `setData` festgelegt werden.)
   * Nicht generierte Cache-Schlüssel für -Blöcke dürfen jetzt nur noch Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Beschränkungen für die Anzahl der automatisch generierten Couponcodes**. Commerce begrenzt jetzt die Anzahl der Coupon Codes, die automatisch generiert werden. Der standardmäßige Maximalwert ist 250.000. Händler können die neue **[!UICONTROL Code Quantity Limit]** Konfigurationsoption (**[!UICONTROL Stores]** > > **[!UICONTROL Settings:Configuration]** **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) verwenden, um dieses neue Limit zu steuern. <!-- AC-8753 -->

## 2.4.4-p6

Die Sicherheitsversion Adobe Systems Commerce 2.4.4-p6 enthält Sicherheitsfehlerkorrekturen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version umfasst außerdem Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Diese Version umfasst außerdem Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

### Höhepunkte

Mit dieser Version wird eine neue Konfigurationseinstellung für den vollständigen Seite-Cache eingeführt, mit der die mit dem `{BASE-URL}/page_cache/block/esi HTTP` Endpunkt verbundenen Risiken verringert werden können. Dieser Endpunkt unterstützt uneingeschränkte, dynamisch geladene Inhalte-Fragmente aus Commerce-Layout-Handles und Blockstrukturen. Die neue **[!UICONTROL Handles Param]** Konfigurationseinstellung legt den Wert des Parameters dieses Endpunkts `handles` fest, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert im Admin-Bereich ändern (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Bekannte Probleme

**Problem**: Adobe Commerce zeigt beim Herunterladen durch Composer aus `repo.magento.com` den Fehler **falsche**) an und der Paket-Download wird unterbrochen. Dieses Problem kann beim Herunterladen von Veröffentlichungspaketen auftreten, die während der Vorabversion verfügbar gemacht wurden, und wird durch eine Neuverpackung des `magento/module-page-cache`-Pakets verursacht.

**Problemumgehung**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie das `/vendor` Verzeichnis innerhalb des Projekts, falls vorhanden.
2) Führen Sie den `bin/magento composer update magento/module-page-cache` Befehl aus. Dieser Befehl aktualisiert nur das `page cache`.

Wenn das Prüfsummenproblem weiterhin besteht, entfernen Sie die `composer.lock`-Datei, bevor Sie den `bin/magento composer update`-Befehl erneut ausführen, um jedes Paket zu aktualisieren.

## 2.4.4-p5

Die Adobe Commerce-Sicherheitsversion 2.4.4-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Händler, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Artikel [jQuery UI Security Vulnerability CVE-2022-31160 Fix for 2.4.4, 2.4.5 und 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html).

## 2.4.4-p4

Die Adobe Commerce-Version 2.4.4-p4 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version umfasst auch Sicherheitsverbesserungen und Plattform-Upgrades, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Händler, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Artikel [jQuery UI Security Vulnerability CVE-2022-31160 Fix for 2.4.4, 2.4.5 und 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html).

### Highlights

Das Standardverhalten der [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-Abfrage und des ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-Endpunkts hat sich geändert. Standardmäßig gibt die API jetzt immer `true` zurück. Händler können das ursprüngliche Verhalten aktivieren, d. h. `true` zurückgeben, wenn die E-Mail nicht in der Datenbank vorhanden ist, und `false`, ob sie vorhanden ist. <!-- AC-6695 -->

### Plattform-Upgrades

Plattform-Upgrades für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung des Lackcache 7.3**. Diese Version ist kompatibel mit der neuesten Version von Varnish Cache 7.3. Die Kompatibilität mit den Versionen 6.0.x und 7u.2.x bleibt bestehen, aber Adobe empfiehlt, Adobe Commerce 2.4.4-p4 nur mit Varnish Cache Version 7.3 oder Version 6.0 LTS zu verwenden.

* **Unterstützung für** RabbitMQ 3.11. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt bestehen, was bis August 2023 unterstützt wird, aber Adobe empfiehlt die Verwendung von Adobe Commerce 2.4.4-p4 nur mit RabbitMQ 3.11.

* **JavaScript Bibliotheken**. Veraltete JavaScript Bibliotheken wurden auf die neuesten Neben- oder Patch Versionen aktualisiert, einschließlich `moment.js` Bibliothek (v2.29.4), `jQuery UI` Bibliothek (v1.13.2) und `jQuery` Tauglichkeitsprüfung Plug-in Bibliothek (v1.19.5).

## 2.4.4-p3

Die Adobe Commerce-Version 2.4.4-p3 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

Die Adobe Commerce-Sicherheitsversion 2.4.4-p2 bietet Fehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Eine Korrektur beinhaltet die Erstellung einer neuen Konfigurationseinstellung. Mit der **E-Mail-Bestätigung verlangen, wenn die E-Mail geändert wurde** können Administratoren eine E-Mail-Bestätigung verlangen, wenn ein Administrator bzw. eine Administratorin ihre E-Mail-Adresse ändert. <!-- AC-6292-->

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Wenden Sie AC-3022.patch an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird die Schemaversion 6.0 in naher Zukunft einstellen. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten `AC-3022.patch` so bald wie möglich beantragen, DHL weiterhin als Reederei anzubieten. Informationen [ Herunterladen und Installieren des Patches finden Sie im Knowledgebase-Artikel ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481)Apply a patch to continue offer DHL as a shipping carrier) .

## 2.4.4-p1

Die Adobe Commerce-Sicherheitsversion 2.4.4-p1 bietet Fehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Wenden Sie `AC-3022.patch` an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird die Schemaversion 6.0 in naher Zukunft einstellen. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten `AC-3022.patch` so bald wie möglich beantragen, DHL weiterhin als Reederei anzubieten. Informationen [ Herunterladen und Installieren des Patches finden Sie im Knowledgebase-Artikel ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)Apply a patch to continue offer DHL as a shipping carrier) .

### Highlights

Die Sicherheitsverbesserungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit, einschließlich:

* ACL-Ressourcen wurden dem Inventar hinzugefügt.
* Die Sicherheit der Inventarvorlage wurde verbessert.

### Bekannte Probleme

**Problem**: Web-API- und Integrationstests zeigen diesen Fehler an, wenn sie mit dem 2.4.4-p1-Paket ausgeführt werden: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Problemumgehung**: Installieren die vorherige Version von Monolog, indem Sie den `require monolog/monolog:2.6.0` Befehl ausführen. <!-- AC-3651-->

**Problem**: Händler können während eines Upgrades von Adobe Systems Commerce 2.4.4 auf Adobe Systems Commerce 2.4.4-p1 Hinweise zur Herabstufung der Paketversion bemerken. Diese Meldungen können ignoriert werden. Die Diskrepanz zwischen den Paketversionen ist auf Anomalien bei der Paketerstellung zurückzuführen. Es ist kein Produkt Funktionen betroffen ist. Im Knowledgebase-Artikel [Pakete, die nach dem Upgrade von 2.4.4 auf 2.4.4-p1 ](https://support.magento.com/hc/en-us/articles/8214752983949) wurden) finden Sie eine Erläuterung der betroffenen Szenarien und Problemumgehungen.
