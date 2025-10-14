---
title: 'ACSD-64813: Die Zuweisung von Kategorien im freigegebenen  [!DNL B2B]  über die REST-API ist langsam'
description: Wenden Sie den Patch ACSD-64813 an, um das Adobe Commerce-Problem zu beheben, bei dem das Aufheben der Zuweisung  [!DNL B2B]  Kategorien in einem freigegebenen Katalog über die REST-API langsam ist.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
source-git-commit: 239a9efcc2ae231b337f654e4e36e6119e6eff7e
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-64813: Das Aufheben der Zuweisung von Kategorien in [!DNL B2B] freigegebenen Katalog über die REST-API ist langsam

Mit dem Patch ACSD-64813 wird das Problem behoben, dass die Zuweisung von Kategorien in einem [!DNL B2B] freigegebenen Katalog über die REST-API langsam aufgehoben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-64813. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Zuweisung von Kategorien in einem [!DNL B2B] freigegebenen Katalog über die REST-API wird langsam aufgehoben.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL B2B]**, **[!UICONTROL Company]** und **[!UICONTROL Shared Catalog]**.
1. Generieren Sie 30.000 aktive, vorrätige Produkte.
1. Erstellen Sie [&#x200B; benutzerdefinierten freigegebenen &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) und weisen Sie ihm alle Produkte zu.
1. Erstellen Sie eine neue Kategorie unter der standardmäßigen Stammkategorie und weisen Sie ihr einige Produkte zu.
1. Verwenden Sie das Admin-Token, um den REST-API-Endpunkt `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` mit der neuen Kategorie-ID aufzurufen.

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. Bestätigen Sie, dass die Antwort *true“*.
1. Führen Sie `bin/magento cron:run` zweimal aus oder führen Sie eine Neuindizierung durch.
1. Verwenden Sie das Admin-Token, um den REST-API-Endpunkt `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` mit der neuen Kategorie-ID aufzurufen.

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>Erwartete Ergebnisse</u>:

Der Vorgang sollte in angemessener Zeit (unter einigen Minuten) abgeschlossen sein.

<u>Tatsächliche Ergebnisse</u>:

Die Ausführung dauert etwa 30 Minuten oder führt zu einem Zeitüberschreitungsfehler.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
