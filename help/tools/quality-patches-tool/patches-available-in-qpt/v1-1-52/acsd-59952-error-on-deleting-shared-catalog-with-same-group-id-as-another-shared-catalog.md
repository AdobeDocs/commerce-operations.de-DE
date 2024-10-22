---
title: "ACSD-59952: Fehler beim Löschen des freigegebenen Katalogs mit derselben Gruppen-ID wie einem anderen freigegebenen Katalog"
description: Wenden Sie den Patch ACSD-59952 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Löschen eines freigegebenen Katalogs mit derselben "customer_group_id"als einem anderen freigegebenen Katalog ein Fehler ausgegeben wird.
feature: B2B, REST
role: Admin, Developer
source-git-commit: a67f31aa905b420dcd2a17645734632d3f94520c
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACSD-59952: Fehler beim Löschen des freigegebenen Katalogs mit derselben Gruppen-ID wie einem anderen freigegebenen Katalog

Der Patch ACSD-59952 behebt den Fehler, der beim Löschen freigegebener Kataloge mit demselben `customer_group_id` -Wert wie ein anderer freigegebener Katalog ausgegeben wurde. Außerdem werden Benutzer daran gehindert, solche freigegebenen Kataloge zu erstellen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59952. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein neuer freigegebener Katalog mit dem gleichen &quot;`customer_group_id`&quot; wie ein anderer freigegebener Katalog kann nicht erstellt werden. Beim Versuch, den freigegebenen Katalog mit demselben `customer_group_id` zu löschen, wird jedoch ein Fehler ausgegeben.

<u>Voraussetzungen</u>:

Installieren Sie die B2B-Module von Adobe Commerce.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie mehrere freigegebene Kataloge, die demselben `customer_group_id` zugewiesen sind, mithilfe des folgenden REST-API-Aufrufs:

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
* Der folgende Fehler wird zurückgegeben, wenn versucht wird, den freigegebenen Katalog mit demselben `customer_group_id` zu löschen: *Freigegebener Katalog kann nicht gelöscht werden*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
