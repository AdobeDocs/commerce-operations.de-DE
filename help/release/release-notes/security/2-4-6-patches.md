---
title: Versionshinweise zu Adobe Commerce 2.4.6 Security Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.6 enthalten sind.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.6-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.6-p8

Die Sicherheitsversion Adobe Commerce 2.4.6-p8 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.6 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.6-p7

Die Adobe Commerce-Sicherheitsversion 2.4.6-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.6 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/2024-08/security.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.6-p6

Die Adobe Commerce-Sicherheitsversion 2.4.6-p6 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.6 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

Zur Kompatibilität mit Commerce-Version 2.4.6-p6 müssen Händler mit der Adobe Commerce B2B-Erweiterung auf [B2B-Version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) aktualisieren.

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

Zur Kompatibilität mit Commerce-Version 2.4.6-p6 müssen Händler mit der Adobe Commerce B2B-Erweiterung auf [B2B-Version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) aktualisieren.

### Highlights

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.6-p5

Die Adobe Commerce-Sicherheitsversion 2.4.6-p5 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.6 identifiziert wurden.

Die neuesten Informationen zu diesen Fehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.6-p4

Die Sicherheitsversion Adobe Commerce 2.4.6-p4 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Highlights

Mit dieser Version werden zwei wesentliche Sicherheitsverbesserungen eingeführt:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für Bausteine enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Syntax der Vorlagenanweisung oder die Methoden `setCacheKey` oder `setData` festgelegt werden.)
   * Nicht generierte Cache-Schlüssel für Blöcke dürfen jetzt nur Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Beschränkungen der Anzahl der automatisch generierten Couponcodes**. Commerce beschränkt jetzt die Anzahl der automatisch generierten Couponcodes. Der Standardwert ist maximal 250.000. Händler können die neue Konfigurationsoption **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) verwenden, um diese neue Begrenzung zu steuern. <!-- AC-8753 -->

## 2.4.6-p3

Die Sicherheitsversion Adobe Commerce 2.4.6-p3 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitskorrekturen finden Sie im [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Highlights

Mit dieser Version wird eine neue Einstellung für die vollständige Seiten-Cache-Konfiguration eingeführt, die dazu beiträgt, die Risiken im Zusammenhang mit dem `{BASE-URL}/page_cache/block/esi HTTP` -Endpunkt zu verringern. Dieser Endpunkt unterstützt nicht eingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue Konfigurationseinstellung **[!UICONTROL Handles Param]** legt den Wert des Parameters `handles` dieses Endpunkts fest, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert über Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]** <!-- AC-9113 --> ändern.

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.6-p3 beinhaltet die Auflösung des durch Patch ACSD-51892 festgelegten Leistungsabfalls. Händler sind nicht von dem Problem betroffen, das durch diesen Patch behoben wird, der im Knowledge Base-Artikel [ACSD-51892: Leistungsproblem beschrieben wird, bei dem Konfigurationsdateien mehrmals geladen werden.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html)

### Bekannte Probleme

**Problem**: Adobe Commerce zeigt während des Herunterladens durch den Composer von `repo.magento.com` einen Fehler vom Typ `wrong checksum` an und der Paketdownload wird unterbrochen. Dieses Problem kann beim Herunterladen von Release-Paketen auftreten, die während der Vorabversion bereitgestellt werden, und wird durch eine Neuverpackung des `magento/module-page-cache` -Pakets verursacht.

**Problemumgehung**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie das Verzeichnis &quot;`/vendor`&quot; im Projekt, sofern vorhanden.
2) Führen Sie den Befehl `bin/magento composer update magento/module-page-cache` aus. Dieser Befehl aktualisiert nur das `page cache` -Paket.

Wenn das Prüfsummenproblem fortbesteht, entfernen Sie die Datei &quot;`composer.lock`&quot;, bevor Sie den Befehl &quot;`bin/magento composer update`&quot;erneut ausführen, um jedes Paket zu aktualisieren.

## 2.4.6-p2

Die Sicherheitsversion Adobe Commerce 2.4.6-p2 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version bietet außerdem Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Knowledge Base-Artikel 2.4.4, 2.4.5 und 2.4.6 zur Sicherheitslücke CVE-2022-31160 in der jQuery-Benutzeroberfläche angegeben ist.[](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)

### Highlights

Der Wert von `fastcgi_pass` in der Datei `nginx.sample` wurde zum vorherigen (vor 2.4.6-p1) Wert von `fastcgi_backend` zurückgegeben. Dieser Wert wurde in Adobe Commerce 2.4.6-p1 versehentlich in `php-fpm:9000` geändert.

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.6-p2 beinhaltet die Auflösung des Leistungsabfalls, der durch Patch ACSD-51892 behoben wurde. Händler sind nicht von dem Problem betroffen, das durch diesen Patch behoben wird, der im Knowledge Base-Artikel [ACSD-51892: Leistungsproblem beschrieben wird, bei dem Konfigurationsdateien mehrmals geladen werden.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html)

## 2.4.6-p1

Die Adobe Commerce-Sicherheitsversion 2.4.6-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version umfasst auch Sicherheitsverbesserungen und Plattformaktualisierungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` -Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und Magento Open Source 2.4.4, 2.4.5 und 2.4.6. Merchants, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Knowledge Base-Artikel 2.4.4, 2.4.5 und 2.4.6 der Sicherheitslücke CVE-2022-31160 im Abschnitt zur Fehlerbehebung der Query UI angegeben ist.[](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)

#### Hervorheben

Das Standardverhalten der GraphQL-Abfragen [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) und des REST-Endpunkts ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) wurde geändert. Standardmäßig gibt die API jetzt immer `true` zurück. Händler können das ursprüngliche Verhalten aktivieren, d. h. `true` zurückgeben, wenn die E-Mail nicht in der Datenbank vorhanden ist, und `false`, wenn sie existiert. <!-- AC-6695 -->

### Plattformaktualisierungen

Plattformaktualisierungen für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung des Unterschiedlichen Cache 7.3**. Diese Version ist mit der neuesten Version von Varnish Cache 7.3 kompatibel. Die Kompatibilität bleibt mit den Versionen 6.0.x und 7.2.x bestehen. Adobe wird jedoch empfohlen, Adobe Commerce 2.4.6-p1 nur mit Version 7.3 (Varnish Cache) oder Version 6.0 LTS zu verwenden.

* **RabbitMQ 3.11-Unterstützung**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt erhalten, was bis August 2023 unterstützt wird. Adobe wird jedoch empfohlen, Adobe Commerce 2.4.6-p1 nur mit RabbitMQ 3.11 zu verwenden.

* **JavaScript-Bibliotheken**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten kleineren oder Patch-Versionen aktualisiert, einschließlich der `moment.js` -Bibliothek (v2.29.4), der `jQuery UI` -Bibliothek (v1.13.2) und der `jQuery` -Validierungs-Plug-in-Bibliothek (v1.19.5).

### Bekannte Probleme

* Die Datei `nginx.sample` wurde versehentlich mit einer Änderung aktualisiert, die den Wert von `fastcgi_pass` von `fastcgi_backend` in `php-fpm:9000` ändert. Diese Änderung kann sicher rückgängig gemacht oder ignoriert werden. <!-- AC-8992 -->

* Fehlende Abhängigkeiten für das B2B-Sicherheitspaket verursachen den folgenden Installationsfehler bei der Installation oder Aktualisierung der B2B-Erweiterung auf 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Dieses Problem kann gelöst werden, indem manuelle Abhängigkeiten für das B2B-Sicherheitspaket mit dem [Stabilitäts-Tag](https://getcomposer.org/doc/04-schema.md#package-links) hinzugefügt werden. Weitere Informationen finden Sie in den [B2B-Versionshinweisen](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
