---
title: 'ACSD-65540: SQL-Fehler tritt aufgrund fehlender REGEXP_LIKE-Funktion in company_structure updates auf'
description: Wenden Sie den Patch ACSD-65540 an, um das Adobe Commerce-Problem zu beheben, bei dem SQL-Fehler aufgrund einer fehlenden REGEXP_LIKE-Funktion in Aktualisierungen der company_structure auftreten.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%
---
# ACSD-65540: SQL-Fehler tritt aufgrund fehlender `REGEXP_LIKE` in `company_structure` Updates auf

Der Patch ACSD-65540 behebt das Problem, dass SQL-Fehler aufgrund fehlender `REGEXP_LIKE` in `company_structure`-Updates auftreten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-65540.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce B2B (alle Bereitstellungsmethoden) 1.5.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce B2B (alle Bereitstellungsmethoden) 1.5.2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

SQL-Syntaxfehler tritt aufgrund fehlender `REGEXP_LIKE` in `company_structure` Aktualisierungen auf.

<u>Schritte zur Reproduktion</u>:

1. Aktualisieren Sie [!DNL B2B] auf Version 1.5.2.
1. Führen Sie den folgenden Befehl aus:

```shell
bin/magento setup:upgrade
```

<u>Erwartete Ergebnisse</u>:

Upgrade wurde erfolgreich abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

```text
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
