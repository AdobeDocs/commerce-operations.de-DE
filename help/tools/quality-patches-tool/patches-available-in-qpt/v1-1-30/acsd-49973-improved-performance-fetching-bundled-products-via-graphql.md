---
title: 'ACSD-49973: Verbesserte Leistung beim Abrufen gebündelter Produkte über [!DNL GraphQL]'
description: Wenden Sie den Patch ACSD-49973 an, um das Adobe Commerce-Problem zu beheben, bei dem die Leistung beim Abrufen gebündelter Produkte über  [!DNL GraphQL] beeinträchtigt wird.
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-49973: Verbesserte Leistung beim Abrufen gebündelter Produkte über [!DNL GraphQL]

Der Patch ACSD-49973 verbessert die Leistung beim Abrufen gebündelter Produkte über [!DNL GraphQL]. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID lautet ACSD-49973. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Leistung verschlechtert sich beim Abrufen gebündelter Produkte über [!DNL GraphQL].

<u>Voraussetzungen</u>:

Erstellen Sie 2000 Bundle-Produkte mit dem [Leistungs-Toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html).

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die [!DNL DB]-Abfragelogger:

   ```
   bin/magento dev:query-log:enable
   ```

1. Führen Sie die folgende [!DNL GraphQL] -Abfrage aus:

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

1. Überprüfen Sie `var/log/db.log` auf Anforderungen an die Tabelle `catalog_product_bundle_selection`.

<u>Erwartete Ergebnisse</u>:

Anforderungen an die Tabelle `catalog_product_bundle_selection` sollten nicht in der Tabelle `var/log/db.log` vorhanden sein.

<u>Tatsächliche Ergebnisse</u>:

Es gibt 2000 Anfragen an die Tabelle `catalog_product_bundle_selection` , die gleichzeitig ausgelöst werden und die die Leistung beeinträchtigen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
