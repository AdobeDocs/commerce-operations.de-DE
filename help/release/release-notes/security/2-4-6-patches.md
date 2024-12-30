---
title: Versionshinweise zum Sicherheits-Patch für Adobe Commerce 2.4.6
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.6-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.6-p8

Die Adobe Commerce-Sicherheitsversion 2.4.6-p8 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.6 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.6-p7

Die Adobe Commerce-Sicherheitsversion 2.4.6-p7 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.6 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Highlights

{{$include /help/_includes/release-notes/2024-08/security.md}}

### In dieser Version enthaltene Hotfixes

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.6-p6

Die Adobe Commerce-Sicherheitsversion 2.4.6-p6 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.6 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

Um die Kompatibilität mit Commerce Version 2.4.6-p6 zu gewährleisten, müssen Händler, die die Adobe Commerce B2B-Erweiterung besitzen, ein Upgrade auf [B2B Version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) durchführen.

### Hotfix für CVE-2024-34102 anwenden

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

Um die Kompatibilität mit Commerce Version 2.4.6-p6 zu gewährleisten, müssen Händler, die die Adobe Commerce B2B-Erweiterung besitzen, ein Upgrade auf [B2B Version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) durchführen.

### Highlights

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.6-p5

Die Adobe Commerce-Sicherheitsversion 2.4.6-p5 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen von 2.4.6 identifiziert wurden.

Die neuesten Informationen zu diesen Fehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.6-p4

Die Adobe Commerce-Version 2.4.6-p4 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Highlights

Diese Version führt zwei wichtige Sicherheitsverbesserungen ein:

* **Änderungen am Verhalten nicht generierter Cache-Schlüssel**:

   * Nicht generierte Cache-Schlüssel für -Blöcke enthalten jetzt Präfixe, die sich von Präfixen für automatisch generierte Schlüssel unterscheiden. (Nicht generierte Cache-Schlüssel sind Schlüssel, die über die Vorlagenanweisungssyntax oder die `setCacheKey`- oder `setData` festgelegt werden.)
   * Nicht generierte Cache-Schlüssel für -Blöcke dürfen jetzt nur noch Buchstaben, Ziffern, Bindestriche (-) und Unterstriche (_) enthalten. <!-- AC-9831 -->

* **Beschränkungen für die Anzahl der automatisch generierten Couponcodes**. Commerce begrenzt jetzt die Anzahl der Gutscheincodes, die automatisch generiert werden. Der standardmäßige Maximalwert ist 250.000. Händler können die neue **[!UICONTROL Code Quantity Limit]**-Konfigurationsoption (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) verwenden, um dieses neue Limit zu steuern. <!-- AC-8753 -->

## 2.4.6-p3

Die Adobe Commerce-Sicherheitsversion 2.4.6-p3 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitskorrekturen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Highlights

Diese Version führt eine neue Konfigurationseinstellung für den vollständigen Seiten-Cache ein, die dazu beiträgt, die mit dem `{BASE-URL}/page_cache/block/esi HTTP`-Endpunkt verbundenen Risiken zu minimieren. Dieser Endpunkt unterstützt uneingeschränkte, dynamisch geladene Inhaltsfragmente aus Commerce-Layout-Handles und -Blockstrukturen. Die neue **[!UICONTROL Handles Param]**-Konfigurationseinstellung legt den Wert des `handles`-Parameters dieses Endpunkts fest, der die maximal zulässige Anzahl von Handles pro API bestimmt. Der Standardwert dieser Eigenschaft ist 100. Händler können diesen Wert unter Admin ändern (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.6-p3 beinhaltet die Auflösung der Leistungsbeeinträchtigung, die durch den Patch ACSD-51892 behoben wurde. Händler sind von dem Problem, das durch diesen Patch behoben wird, nicht betroffen. Dies wird im Artikel [ACSD-51892: Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) in der Wissensdatenbank beschrieben.

### Bekannte Probleme

**Problem**: Adobe Commerce zeigt beim Herunterladen durch Composer von `repo.magento.com` einen `wrong checksum` an, und der Paket-Download wird unterbrochen. Dieses Problem kann beim Herunterladen von Veröffentlichungspaketen auftreten, die während der Vorabversion verfügbar gemacht werden, und wird durch eine Neuverpackung des `magento/module-page-cache`-Pakets verursacht.

**Problemumgehung**: Händler, die diesen Fehler beim Herunterladen sehen, können die folgenden Schritte ausführen:

1) Löschen Sie das `/vendor` Verzeichnis innerhalb des Projekts, falls vorhanden.
2) Führen Sie den `bin/magento composer update magento/module-page-cache` Befehl aus. Dieser Befehl aktualisiert nur das `page cache`.

Wenn das Prüfsummenproblem weiterhin besteht, entfernen Sie die `composer.lock`-Datei, bevor Sie den `bin/magento composer update`-Befehl erneut ausführen, um jedes Paket zu aktualisieren.

## 2.4.6-p2

Die Adobe Commerce-Version 2.4.6-p2 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version bietet außerdem Sicherheitsverbesserungen, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und den Magento Open Sourcen 2.4.4, 2.4.5 und 2.4.6. Händler, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Artikel [jQuery UI Security Vulnerability CVE-2022-31160 Fix for 2.4.4, 2.4.5 und 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html).

### Highlights

Der Wert von `fastcgi_pass` in der `nginx.sample`-Datei wurde auf den vorherigen Wert (vor 2.4.6-p1) von `fastcgi_backend` zurückgesetzt. Dieser Wert wurde in Adobe Commerce 2.4.6-p1 versehentlich in `php-fpm:9000` geändert.

### In dieser Version enthaltene Hotfixes

Adobe Commerce 2.4.6-p2 schließt die Auflösung der Leistungsbeeinträchtigung ein, die durch den Patch ACSD-51892 behoben wurde. Händler sind von dem Problem, das durch diesen Patch behoben wird, nicht betroffen. Dies wird im Artikel [ACSD-51892: Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) in der Wissensdatenbank beschrieben.

## 2.4.6-p1

Die Adobe Commerce-Version 2.4.6-p1 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version umfasst auch Sicherheitsverbesserungen und Plattform-Upgrades, um die Einhaltung der neuesten Best Practices für die Sicherheit zu verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie unter [Adobe-Sicherheitsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Hotfix für CVE-2022-31160 anwenden

`jQuery-UI` Bibliotheksversion 1.13.1 weist eine bekannte Sicherheitslücke (CVE-2022-31160) auf, die mehrere Versionen von Adobe Commerce und Magento Open Source betrifft. Diese Bibliothek ist eine Abhängigkeit von Adobe Commerce und den Magento Open Sourcen 2.4.4, 2.4.5 und 2.4.6. Händler, die betroffene Bereitstellungen ausführen, sollten den Patch anwenden, der im Artikel [Sicherheitslücke der Abfrage-Benutzeroberfläche CVE-2022-31160 Fehlerbehebung für die Versionen 2.4.4, 2.4.5 und 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) der Wissensdatenbank angegeben ist.

#### hervorheben

Das Standardverhalten der [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL-Abfrage und des ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-Endpunkts hat sich geändert. Standardmäßig gibt die API jetzt immer `true` zurück. Händler können das ursprüngliche Verhalten aktivieren, d. h. `true` zurückgeben, wenn die E-Mail nicht in der Datenbank vorhanden ist, und `false`, ob sie vorhanden ist. <!-- AC-6695 -->

### Plattform-Upgrades

Plattform-Upgrades für diese Version verbessern die Einhaltung der neuesten Best Practices für die Sicherheit.

* **Unterstützung des Lackcache 7.3**. Diese Version ist kompatibel mit der neuesten Version von Varnish Cache 7.3. Die Kompatibilität mit den Versionen 6.0.x und 7.2.x bleibt bestehen, aber Adobe wird empfohlen, Adobe Commerce 2.4.6-p1 nur mit Varnish Cache Version 7.3 oder Version 6.0 LTS zu verwenden.

* Unterstützung für **RabbitMQ 3.11**. Diese Version ist mit der neuesten Version von RabbitMQ 3.11 kompatibel. Die Kompatibilität mit RabbitMQ 3.9 bleibt bestehen, die bis August 2023 unterstützt wird, aber Adobe empfiehlt die Verwendung von Adobe Commerce 2.4.6-p1 nur mit RabbitMQ 3.11.

* **JavaScript-**. Veraltete JavaScript-Bibliotheken wurden auf die neuesten Neben- oder Patch-Versionen aktualisiert, einschließlich `moment.js`-Bibliothek (v2.29.4), `jQuery UI`-Bibliothek (v1.13.2) und `jQuery` Validierungs-Plug-in-Bibliothek (v1.19.5).

### Bekannte Probleme

* Die `nginx.sample`-Datei wurde versehentlich mit einer Änderung aktualisiert, die den Wert von `fastcgi_pass` von `fastcgi_backend` in `php-fpm:9000` ändert. Diese Änderung kann sicher rückgängig gemacht oder ignoriert werden. <!-- AC-8992 -->

* Fehlende Abhängigkeiten für das B2B-Sicherheitspaket führen beim Installieren oder Aktualisieren der B2B-Erweiterung auf 1.4.0 zum folgenden Installationsfehler.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Dieses Problem kann behoben werden, indem manuelle Abhängigkeiten für das B2B-Sicherheitspaket mit einem &quot;[&quot;-Tag ](https://getcomposer.org/doc/04-schema.md#package-links) werden. Weitere Informationen finden Sie in den [B2B-Versionshinweisen](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
