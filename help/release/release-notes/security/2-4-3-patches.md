---
title: Versionshinweise für Adobe Commerce 2.4.3 Sicherheits-Patches
description: Erfahren Sie mehr über Fehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsbezogene Updates in den Sicherheits-Patch-Versionen für Adobe Commerce 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.3-Sicherheits-Patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Die Adobe Commerce-Version 2.4.3-p3 bietet Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen von 2.4.3 identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).

### Wenden Sie AC-3022.patch an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird die Schemaversion 6.0 in naher Zukunft einstellen. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten `AC-3022.patch` so bald wie möglich beantragen, DHL weiterhin als Reederei anzubieten. Informationen [ Herunterladen und Installieren des Patches finden Sie im Knowledgebase-Artikel ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)Apply a patch to continue offer DHL as a shipping carrier) .

### Sicherheits-Highlights

* ACL-Ressourcen wurden dem Inventar hinzugefügt.
* Die Sicherheit der Inventarvorlage wurde verbessert.



## Adobe Commerce 2.4.3-p2

Die Adobe Commerce-Version 2.4.3-p2 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  Die Patch-Version behebt auch die Sicherheitsanfälligkeit, die von `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` und `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch` behoben wurde.


### Wenden Sie AC-3022.patch an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird die Schemaversion 6.0 in naher Zukunft einstellen. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten `AC-3022.patch` so bald wie möglich beantragen, DHL weiterhin als Reederei anzubieten. Informationen [ Herunterladen und Installieren des Patches finden Sie im Knowledgebase-Artikel ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)Apply a patch to continue offer DHL as a shipping carrier) .

### Sicherheits-Highlights

* Die Verwendung von E-Mail-Variablen wurde in Version 2.3.4 als Teil einer Sicherheitsrisikominderung zugunsten einer strengeren Variablensyntax eingestellt. Dieses veraltete Verhalten wurde in dieser Version als Fortsetzung dieser Sicherheitsrisikominderung vollständig entfernt.

  E-Mail- oder Newsletter-Vorlagen, die in früheren Versionen verwendet wurden, funktionieren daher nach dem Upgrade auf Adobe Commerce 2.4.3-p2 möglicherweise nicht mehr ordnungsgemäß. Betroffene Vorlagen umfassen Admin-Überschreibungen, Designs, untergeordnete Designs und Vorlagen aus benutzerdefinierten Modulen oder Erweiterungen von Drittanbietern. Ihre -Bereitstellung ist möglicherweise auch nach Verwendung des [Upgrade-Kompatibilitätstools) weiterhin betroffen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) um veraltete Anwendungen zu beheben. Informationen [ möglichen Auswirkungen und Richtlinien für die Migration betroffener ](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) finden Sie unter „Migrieren benutzerdefinierter E-Mail-Vorlagen“.

* OAuth-Zugriffs-Token und Kennwortzurücksetzungs-Token werden jetzt bei der Speicherung in der Datenbank verschlüsselt. <!-- AC-520 1323-->

* Die Validierung wurde verbessert, um das Hochladen nicht alphanumerischer Dateierweiterungen zu verhindern. <!-- AC-479-->

* Swagger ist jetzt standardmäßig deaktiviert, wenn sich Adobe Commerce im Produktionsmodus befindet. <!-- AC-1450-->

* Entwickler können jetzt die Größenbeschränkung für Arrays konfigurieren, die von Adobe Commerce RESTful-Endpunkten akzeptiert werden, und zwar pro Endpunkt. Siehe [API-](https://developer.adobe.com/commerce/webapi/get-started/api-security/)<!-- AC-465-->

* Es wurden Mechanismen hinzugefügt, um die Größe und Anzahl der Ressourcen zu begrenzen, die ein Benutzer über eine Web-API systemweit anfordern kann, und um die Standardwerte für einzelne Module zu überschreiben. Diese Verbesserung behebt das von `MC-43048__set_rate_limits__2.4.3.patch` behandelte Problem. Siehe [API-](https://developer.adobe.com/commerce/webapi/get-started/api-security/)<!-- AC-1120-->


## 2.4.3-p1

Die Adobe Commerce-Sicherheitsversion 2.4.3-p1 bietet Sicherheitsfehlerbehebungen für Sicherheitslücken, die in der vorherigen Version (Adobe Commerce 2.4.3 und Magento Open Source 2.4.3) identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.


Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). Die Patch-Version enthält auch Fehlerbehebungen für die vom Hersteller [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html) und [Vertex](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html) entwickelten Erweiterungen.

### Wenden Sie AC-3022.patch an, um DHL weiterhin als Versandunternehmen anzubieten

DHL hat die Schemaversion 6.2 eingeführt und wird die Schemaversion 6.0 in naher Zukunft einstellen. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten `AC-3022.patch` so bald wie möglich beantragen, DHL weiterhin als Reederei anzubieten. Informationen [ Herunterladen und Installieren des Patches finden Sie im Knowledgebase-Artikel ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)Apply a patch to continue offer DHL as a shipping carrier) .

### Hotfixes

Diese Version enthält den folgenden Hotfix und alle Hotfixes, die für die vorherige Patch-Version veröffentlicht wurden.

* Patch-`AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Informationen zu Patch und Problem finden Sie im Knowledgebase-Artikel [Adobe Commerce-Upgrade 2.4.3, 2.3.7-p1 PHP Fatal Error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) .

### Sicherheits-Highlights

**Sitzungs-IDs wurden aus der Datenbank**. Diese Code-Änderung kann zu grundlegenden Änderungen führen, wenn Händler Anpassungen oder installierte Erweiterungen haben, die die in der Datenbank gespeicherten rohen Sitzungs-IDs verwenden. <!-- MC-40976-->

**Eingeschränkter Administratorzugriff auf Mediensammlungs-Ordner**. Die standardmäßigen Mediensammlungs-Berechtigungen erlauben jetzt nur noch Verzeichnisvorgänge (Anzeigen, Hochladen, Löschen und Erstellen), die von der Konfiguration explizit zugelassen sind. Admin-Benutzer können nicht mehr über die Mediensammlung auf Medien-Assets zugreifen, die außerhalb der `catalog/category`- oder `wysiwyg` hochgeladen wurden. Administratoren, die auf Medien-Assets zugreifen möchten, müssen sie in einen explizit zulässigen Ordner verschieben oder ihre Konfigurationseinstellungen anpassen. Siehe [Ändern von Medienbibliotheks-](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/)<!-- B2B-1897-->

**Geringere Beschränkungen für die Komplexität von GraphQL-Abfragen**. Die maximal zulässige Komplexität von Abfragen in GraphQL wurde verringert, um DoS-Angriffe (Denial-of-Service) zu verhindern. Siehe [GraphQL-Sicherheitskonfiguration](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**Aktuelle Schwachstellen beim Penetrationstest** wurden in dieser Version behoben. <!-- MC-42431-->

Die nicht unterstützte `unsafe-inline` für Quellausdrücke wurde aus der Inhaltssicherheitsrichtliniensatz-`frame-ancestors` entfernt. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
