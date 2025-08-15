---
title: 'ACSD-56193: [!DNL Fastly] Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht'
description: Wenden Sie den ACSD-56193-Patch an, um das Adobe Commerce-Problem zu beheben,  [!DNL Fastly]  der -Cache nicht für die Aktualisierung des Inhalts-Staging gelöscht wird.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht

Mit dem Patch ACSD-56193 wird das Problem behoben, dass der [!DNL Fastly]-Cache für die Aktualisierung des Inhalts-Staging nicht gelöscht wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56193. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der [!DNL Fastly/Varnish]-Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht

<u>Schritte zur Reproduktion</u>:

1. Installieren und Konfigurieren [!DNL Varnish] Cache.
1. Erstellen Sie einen statischen Block mit einer geplanten Aktualisierung.
1. Erstellen Sie eine den statischen Block einbettende Kategorie.
1. Rufen Sie den Inhalt der Kategorie mithilfe der folgenden GraphQL-Abfrage ab:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Führen Sie diese Abfrage mehrmals aus und stellen Sie sicher, dass die Antwort im [!DNL Varnish] zwischengespeichert ist.
1. Führen Sie cron aus, um die geplante Änderung anzuwenden.
1. Führen Sie die obige GraphQL-Abfrage erneut aus.
1. Erstellen Sie einen neuen Zeitplan für denselben statischen Block.
1. Wiederholen Sie die Schritte 5-9.

<u>Erwartete Ergebnisse</u>:

Der aktualisierte Inhalt wird nach Ausführung der geplanten Aktualisierungen zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Der veraltete Inhalt wird nach Ausführung der geplanten Aktualisierungen zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
