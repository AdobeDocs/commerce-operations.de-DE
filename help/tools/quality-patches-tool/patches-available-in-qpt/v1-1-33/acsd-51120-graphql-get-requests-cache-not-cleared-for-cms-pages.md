---
title: "ACSD-51120: GraphQL GET-Anforderungscache für CMS-Seiten mit CMS-Bausteinen nicht gelöscht"
description: Wenden Sie den Patch ACSD-51120 an, um das Adobe Commerce-Problem zu beheben, bei dem der GraphQL-Anforderungscache für CMS-Seiten mit CMS-Bausteinen nicht gelöscht wird.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120: GraphQL GET-Anforderungscache für CMS-Seiten mit CMS-Bausteinen nicht gelöscht

Der Patch ACSD-51120 behebt das Problem, dass der GraphQL-Anforderungscache für CMS-Seiten, die CMS-Bausteine enthalten, die über ein Staging-Update aktualisiert werden, nicht gelöscht wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51120. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der GraphQL GET-Anforderungscache wird für CMS-Seiten mit CMS-Bausteinen, die über eine Staging-Aktualisierung aktualisiert werden, nicht gelöscht.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen CMS-Block.
1. Schließen Sie den CMS-Block mithilfe von [!DNL Page Builder] in eine CMS-Seite ein.
1. Rufen Sie die CMS-Seite mithilfe der angegebenen GraphQL-Abfrage mithilfe einer GET-Anfrage ab:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Stellen Sie sicher, dass die GraphQL-Antwort in [!DNL Varnish] zwischengespeichert ist.
1. Erstellen Sie eine geplante Aktualisierung für den Baustein.
1. Warten Sie, bis die geplante Aktualisierung angewendet wird, und führen Sie den Cron-Auftrag aus, um die geplante Aktualisierung anzuwenden.
1. Rufen Sie die CMS-Seite mithilfe der angegebenen GraphQL-Abfrage mithilfe einer GET-Anfrage erneut ab.

<u>Erwartete Ergebnisse</u>:

Die Antwort zeigt den aktualisierten Inhalt an.

<u>Tatsächliche Ergebnisse</u>:

Die Antwort zeigt weiterhin den alten Inhalt an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
