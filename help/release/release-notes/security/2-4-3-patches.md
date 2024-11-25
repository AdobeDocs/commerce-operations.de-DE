---
title: Versionshinweise für Adobe Commerce 2.4.3-Sicherheitspatches
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.3 enthalten sind.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.3-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.3-p3

Die Sicherheitsversion Adobe Commerce 2.4.3-p3 enthält Sicherheitskorrekturen für Sicherheitslücken, die in früheren Versionen 2.4.3 identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).

### Wenden Sie `AC-3022.patch` an, um DHL weiterhin als Versandunternehmen anzubieten.

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten so schnell wie möglich `AC-3022.patch` anwenden, um DHL weiterhin als Versandunternehmen anzubieten. Informationen zum Herunterladen und Installieren des Patches finden Sie im Artikel [Anwenden eines Patches, um DHL weiterhin als Versandunternehmen anzubieten](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Knowledge Base .

### Sicherheitshinweise

* ACL-Ressourcen wurden zum Inventar hinzugefügt.
* Die Sicherheit der Lagerbestandsvorlage wurde verbessert.

## Adobe Commerce 2.4.3-p2

Die Sicherheitsversion Adobe Commerce 2.4.3-p2 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  Die Patch-Version behebt auch die Sicherheitslücke, die von `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` und `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch` behoben wurde.


### Wenden Sie `AC-3022.patch` an, um DHL weiterhin als Versandunternehmen anzubieten.

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten so schnell wie möglich `AC-3022.patch` anwenden, um DHL weiterhin als Versandunternehmen anzubieten. Informationen zum Herunterladen und Installieren des Patches finden Sie im Artikel [Anwenden eines Patches, um DHL weiterhin als Versandunternehmen anzubieten](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Knowledge Base .

### Sicherheitshinweise

* Die Verwendung von E-Mail-Variablen wurde bereits in Version 2.3.4 als Teil einer Sicherheitsrisikobegrenzung zugunsten einer strikteren Variablensyntax eingestellt. Dieses veraltete Verhalten wurde in dieser Version als Fortsetzung dieser Sicherheitsrisikobegrenzung vollständig entfernt.

  Daher funktionieren E-Mail- oder Newsletter-Vorlagen, die in früheren Versionen funktioniert haben, möglicherweise nicht ordnungsgemäß, nachdem sie auf Adobe Commerce 2.4.3-p2 aktualisiert wurden. Betroffene Vorlagen sind Admin-Überschreibungen, Designs, untergeordnete Designs und Vorlagen aus benutzerdefinierten Modulen oder Erweiterungen von Drittanbietern. Ihre Bereitstellung kann auch nach Verwendung des [Kompatibilitätstools für Aktualisierungen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) zur Behebung veralteter Verwendungszwecke weiter beeinträchtigt sein. Informationen zu möglichen Auswirkungen und Richtlinien für die Migration der betroffenen Vorlagen finden Sie unter [Migrieren benutzerdefinierter E-Mail-Vorlagen](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) .

* OAuth-Zugriffstoken und Token zum Zurücksetzen des Kennworts werden jetzt verschlüsselt, wenn sie in der Datenbank gespeichert werden. <!-- AC-520 1323-->

* Die Validierung wurde verbessert, um das Hochladen von nicht alphanumerischen Dateierweiterungen zu verhindern. <!-- AC-479-->

* Swagger ist jetzt standardmäßig deaktiviert, wenn sich Adobe Commerce im Produktionsmodus befindet. <!-- AC-1450-->

* Entwickler können jetzt die Größenbeschränkung für Arrays konfigurieren, die von Adobe Commerce RESTful-Endpunkten pro Endpunkt akzeptiert werden. Siehe [API-Sicherheit](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Es wurden Mechanismen hinzugefügt, mit denen die Größe und Anzahl der Ressourcen, die ein Benutzer über eine Web-API systemweit anfordern kann, begrenzt und die Standardwerte für einzelne Module überschrieben werden können. Durch diese Verbesserung wird das Problem behoben, das durch `MC-43048__set_rate_limits__2.4.3.patch` behoben wurde. Siehe [API-Sicherheit](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

Die Adobe Commerce-Sicherheitsversion 2.4.3-p1 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in der vorherigen Version (Adobe Commerce 2.4.3 und Magento Open Source 2.4.3) identifiziert wurden. Diese Version enthält auch Sicherheitsverbesserungen, die die Einhaltung der neuesten Best Practices für die Sicherheit verbessern.


Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). Die Patch-Version enthält außerdem Fehlerbehebungen für die vom Hersteller entwickelten Erweiterungen [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html) und [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html).

### Wenden Sie `AC-3022.patch` an, um DHL weiterhin als Versandunternehmen anzubieten.

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten so schnell wie möglich `AC-3022.patch` anwenden, um DHL weiterhin als Versandunternehmen anzubieten. Informationen zum Herunterladen und Installieren des Patches finden Sie im Artikel [Anwenden eines Patches, um DHL weiterhin als Versandunternehmen anzubieten](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Knowledge Base .

### Hotfixes

Diese Version enthält den folgenden Hotfix und alle Hotfixes, die für die vorherige Patch-Version freigegeben wurden.

* Patch `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Informationen zu Patch und Problem finden Sie im Artikel [Adobe Commerce-Upgrade 2.4.3, 2.3.7-p1 PHP-Fatal error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) Knowledge Base .

### Sicherheitshinweise

**Sitzungs-IDs wurden aus der Datenbank entfernt**. Diese Codeänderung kann zu Änderungen führen, wenn Händler Anpassungen vornehmen oder Erweiterungen installiert haben, die die in der Datenbank gespeicherten Sitzungs-IDs verwenden. <!-- MC-40976-->

**Eingeschränkter Administratorzugriff auf Ordner der Media Gallery**. Standardberechtigungen für Media Gallery erlauben jetzt nur Ordneroperationen (Anzeigen, Hochladen, Löschen und Erstellen), die explizit von der Konfiguration erlaubt sind. Admin-Benutzer können nicht mehr über die Media Gallery auf Medien-Assets zugreifen, die außerhalb der Verzeichnisse `catalog/category` oder `wysiwyg` hochgeladen wurden. Administratoren, die auf Medien-Assets zugreifen möchten, müssen sie in einen explizit zulässigen Ordner verschieben oder ihre Konfigurationseinstellungen anpassen. Siehe [Ändern der Media Library-Ordnerberechtigungen](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Verringerte Beschränkungen der GraphQL-Abfragekomplexität**. Die maximal zulässige GraphQL-Abfragekomplexität wurde verringert, um Denial-of-Service-Angriffe (DOS) zu verhindern. Siehe [GraphQL-Sicherheitskonfiguration](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**Schwachstellen beim aktuellen Penetrationstest** wurden in dieser Version behoben. <!-- MC-42431-->

Der nicht unterstützte Quellausdruck `unsafe-inline` wurde aus der Richtlinie &quot;Content Security Policy `frame-ancestors`&quot;entfernt. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->
