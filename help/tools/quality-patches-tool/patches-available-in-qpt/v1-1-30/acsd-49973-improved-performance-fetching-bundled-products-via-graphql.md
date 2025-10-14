---
title: 'ACSD-49973: Verbesserte Leistung beim Abrufen gebündelter Produkte über [!DNL GraphQL]'
description: Wenden Sie den ACSD-49973 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem beim Abrufen gebündelter Produkte über eine Leistungsbeeinträchtigung auftritt [!DNL GraphQL].
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-49973: Verbesserte Leistung beim Abrufen von gebündelten Produkten über [!DNL GraphQL]

Der Patch ACSD-49973 verbessert die Leistung beim Abrufen von gebündelten Produkten über [!DNL GraphQL]. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-49973. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Abrufen gebündelter Produkte über [!DNL GraphQL] tritt eine Leistungsbeeinträchtigung auf.

<u>Voraussetzungen</u>:

Erstellen Sie 2000 Bundle-Produkte mit dem [Leistungs-Toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html?lang=de).

<u>Schritte zur Reproduktion</u>:

1. [!DNL DB] Query Logger aktivieren:

   ```
   bin/magento dev:query-log:enable
   ```

1. Führen Sie die folgende [!DNL GraphQL] aus:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. `var/log/db.log` auf Anfragen an die `catalog_product_bundle_selection`-Tabelle überprüfen.

<u>Erwartete Ergebnisse</u>:

Anfragen an die `catalog_product_bundle_selection`-Tabelle sollten in der `var/log/db.log` nicht vorhanden sein.

<u>Tatsächliche Ergebnisse</u>:

Es gibt 2.000 Anfragen an `catalog_product_bundle_selection` Tabelle, die gleichzeitig ausgelöst werden und zu Leistungseinbußen führen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
