---
title: 'ACSD-51120: GraphQL GET-Anforderungs-Cache wird für CMS-Seiten mit CMS-Blöcken nicht gelöscht'
description: Wenden Sie den Patch ACSD-51120 an, um das Adobe Commerce-Problem zu beheben, bei dem der GraphQL-GET-Anforderungs-Cache für CMS-Seiten, die CMS-Blöcke enthalten, nicht gelöscht wird.
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120: GraphQL GET-Anforderungs-Cache wird für CMS-Seiten mit CMS-Blöcken nicht gelöscht

Mit dem Patch „ACSD-51120“ wird das Problem behoben, dass der GraphQL GET-Anforderungscache für CMS-Seiten mit CMS-Blöcken, die über ein Staging-Update aktualisiert werden, nicht gelöscht wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51120. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der GraphQL GET-Anforderungs-Cache wird nicht für CMS-Seiten geleert, die CMS-Blöcke enthalten, die über eine Staging-Aktualisierung aktualisiert werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen CMS-Block.
1. Fügen Sie den CMS-Block mithilfe der -[!DNL Page Builder] in eine CMS-Seite ein.
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

1. Stellen Sie sicher, dass die GraphQL-Antwort in [!DNL Varnish] zwischengespeichert wird.
1. Erstellen Sie eine geplante Aktualisierung für den Block.
1. Warten Sie, bis das geplante Update angewendet wird, und führen Sie den Cron-Auftrag aus, um das geplante Update anzuwenden.
1. Rufen Sie die CMS-Seite mithilfe der angegebenen GraphQL-Abfrage mithilfe einer GET-Anfrage erneut ab.

<u>Erwartete Ergebnisse</u>:

Die Antwort zeigt den aktualisierten Inhalt an.

<u>Tatsächliche Ergebnisse</u>:

Die Antwort zeigt weiterhin den alten Inhalt an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
