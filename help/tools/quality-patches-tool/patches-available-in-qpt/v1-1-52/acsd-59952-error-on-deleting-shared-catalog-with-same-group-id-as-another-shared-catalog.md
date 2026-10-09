---
title: 'ACSD-59952: Fehler beim Löschen eines freigegebenen Katalogs mit derselben Gruppen-ID wie ein anderer freigegebener Katalog'
description: Wenden Sie den Patch ACSD-59952 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Löschen eines freigegebenen Katalogs mit derselben „customer_group_id“ wie ein anderer freigegebener Katalog ein Fehler ausgelöst wird.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '451'
ht-degree: 0%
---
# ACSD-59952: Fehler beim Löschen eines freigegebenen Katalogs mit derselben Gruppen-ID wie ein anderer freigegebener Katalog

Der Patch ACSD-59952 behebt den Fehler, der beim Löschen freigegebener Kataloge mit demselben `customer_group_id` wie ein anderer freigegebener Katalog ausgelöst wird. Außerdem verhindert sie, dass Benutzer solche freigegebenen Kataloge erstellen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59952. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein neuer freigegebener Katalog mit demselben `customer_group_id` wie ein anderer freigegebener Katalog kann nicht erstellt werden. Wenn Sie jedoch versuchen, den freigegebenen Katalog mit demselben `customer_group_id` zu löschen, wird ein Fehler ausgelöst.

<u>Voraussetzungen</u>:

Installieren Sie die Adobe Commerce B2B-Module.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie mehrere freigegebene Kataloge, die demselben `customer_group_id` zugewiesen sind, indem Sie den folgenden REST-API-Aufruf verwenden:

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Versuchen Sie, einen der freigegebenen Kataloge mithilfe des folgenden REST-API-Aufrufs zu löschen:

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Erwartete Ergebnisse</u>:

* Das Erstellen mehrerer freigegebener Kataloge, die demselben `customer_group_id` zugewiesen sind, ist nicht möglich.
* Der freigegebene Katalog im obigen Fall wurde erfolgreich gelöscht.

<u>Tatsächliche Ergebnisse</u>:

* Es ist möglich, mehrere freigegebene Kataloge zu erstellen, die demselben `customer_group_id` zugewiesen sind.
* Beim Löschen des freigegebenen Katalogs mit demselben `customer_group_id` wird der folgende Fehler zurückgegeben: *Freigegebener Katalog kann nicht gelöscht werden*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
