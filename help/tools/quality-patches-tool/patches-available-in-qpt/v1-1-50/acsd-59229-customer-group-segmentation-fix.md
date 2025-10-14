---
title: 'ACSD-59229: Fehlzuordnung von Kundengruppendaten aufgrund eines veralteten X-Magento-Vary-Werts'
description: Wenden Sie den ACSD-59229-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Informationen zu Kundengruppen aufgrund eines veralteten Wertes von X-Magento-Vary in der Anfrage im falschen Segment gespeichert werden.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-59229: Fehlzuordnung von Kundengruppendaten aufgrund eines veralteten X-Magento-Vary-Werts

Mit dem Patch „ACSD-59229“ wird das Problem behoben, dass aufgrund eines veralteten Werts für „X-Magento-Vary“ in der Anfrage Informationen zu Kundengruppen im falschen Segment gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59229. Beachten Sie, dass das Problem in 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kundengruppenbezogene Informationen werden aufgrund eines veralteten X-Magento-Vary-Werts in der Anfrage im falschen Segment gespeichert.

<u>Voraussetzungen</u>:

Stellen Sie sicher, dass Adobe Commerce B2B mit Beispieldaten installiert und [!DNL Varnish] konfiguriert ist.

<u>Schritte zur Reproduktion</u>:

1. Erweiterte Preise für die [!DNL SKU 24-MB01] einrichten:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Großhandel* = *$200*
      * *Retailer* = *$30*

1. Erstellen Sie zwei Kundenkonten.
1. Weisen Sie beide Kunden der Gruppe &quot;**&quot;**.
1. Öffnen Sie zwei verschiedene Browser-Sitzungen und melden Sie sich mit jedem Kunden an.
1. Navigieren Sie für jeden Kunden zur **[!UICONTROL 24-MB01]** Produktseite und vergewissern Sie sich, dass der angezeigte Preis *$ 200 %*.
1. Ändern Sie die Kundengruppe für einen der Kunden in **Einzelhandel**.
1. Löschen Sie den Cache mithilfe des Befehls `bin/magento cache:flush full_page`.
1. Aktualisieren Sie die Produktseite für jeden Kunden.

<u>Erwartete Ergebnisse</u>:

1. Der Einzelhandelskunde kann den korrekten Preis von *$ 30* für das Produkt sehen.
1. Der Großhandelskunde kann den korrekten Preis von *$ 200* für das Produkt sehen.

<u>Tatsächliche Ergebnisse</u>:

1. Der Einzelhandelskunde kann den korrekten Preis von *$ 30* für das Produkt sehen.
1. Der Großhandelskunde sieht einen falschen Preis von *$ 30* (Einzelhandelspreis) für das Produkt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
