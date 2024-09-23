---
title: 'ACSD-56193: [!DNL Fastly] Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht'
description: Wenden Sie den Patch ACSD-56193 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!DNL Fastly] Cache für die Aktualisierung des Inhalts-Staging nicht gelöscht wird.
feature: Cache, GraphQL, Staging
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht

Der Patch ACSD-56193 behebt das Problem, dass der Cache [!DNL Fastly] nicht für die Aktualisierung des Inhalts-Staging gelöscht wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56193. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der [!DNL Fastly/Varnish]-Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht

<u>Zu reproduzierende Schritte</u>:

1. Installieren und konfigurieren Sie den [!DNL Varnish]-Cache.
1. Erstellen Sie einen statischen Block mit einer geplanten Aktualisierung.
1. Erstellen Sie eine Kategorie, die den statischen Block einbettet.
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
1. Führen Sie den Cron aus, um die geplante Änderung anzuwenden.
1. Führen Sie die oben genannte GraphQL-Abfrage erneut aus.
1. Erstellen Sie einen neuen Zeitplan für denselben statischen Baustein.
1. Wiederholen Sie die Schritte 5 bis 9.

<u>Erwartete Ergebnisse</u>:

Der aktualisierte Inhalt wird nach Ausführung der geplanten Aktualisierungen zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Der veraltete Inhalt wird nach Ausführung der geplanten Aktualisierungen zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
