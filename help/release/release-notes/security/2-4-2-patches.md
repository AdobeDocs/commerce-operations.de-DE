---
title: Versionshinweise zu Adobe Commerce 2.4.2 Security Patch
description: Erfahren Sie mehr über Sicherheitsfehlerbehebungen, Sicherheitsverbesserungen und andere sicherheitsrelevante Updates, die in den Sicherheits-Patch-Versionen für Adobe Commerce Version 2.4.2 enthalten sind.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: d532402e2d65a1f34558fc3c283d4291be5b006b
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Versionshinweise für Adobe Commerce 2.4.2-Sicherheits-Patches

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.2-p2

Die Sicherheitsversion Adobe Commerce 2.4.2-p2 enthält Sicherheitsfehlerbehebungen für Sicherheitslücken, die in früheren Versionen 2.4.2 identifiziert wurden.

Die neuesten Informationen zu den Sicherheitsfehlerbehebungen finden Sie im [Adobe-Sicherheitsbulletin APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Wenden Sie `AC-3022.patch` an, um DHL weiterhin als Versandunternehmen anzubieten.

DHL hat die Schemaversion 6.2 eingeführt und wird in naher Zukunft die Schemaversion 6.0 veraltet sein. Adobe Commerce 2.4.4 und frühere Versionen, die die DHL-Integration unterstützen, unterstützen nur Version 6.0. Händler, die diese Versionen bereitstellen, sollten so schnell wie möglich `AC-3022.patch` anwenden, um DHL weiterhin als Versandunternehmen anzubieten. Informationen zum Herunterladen und Installieren des Patches finden Sie im Artikel [Anwenden eines Patches, um DHL weiterhin als Versandunternehmen anzubieten](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Knowledge Base .
