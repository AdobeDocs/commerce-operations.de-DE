---
title: 'ACSD-50949: Der Preisfilter in der erweiterten Suche gibt keine ordnungsgemäßen Ergebnisse zurück, wenn er zusammen mit dem SKU-Filter verwendet wird'
description: Wenden Sie den Patch ACSD-50949 an, um das Adobe Commerce-Problem zu beheben, bei dem der Preisfilter in der erweiterten Suche keine ordnungsgemäßen Ergebnisse zurückgibt, wenn er zusammen mit dem SKU-Filter verwendet wird.
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949: Der Preisfilter in der erweiterten Suche gibt nicht die richtigen Ergebnisse zurück, wenn er mit dem SKU-Filter verwendet wird

Der Patch ACSD-50949 behebt das Problem, dass der Preisfilter in der erweiterten Suche keine ordnungsgemäßen Ergebnisse zurückgibt, wenn er zusammen mit dem SKU-Filter verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50949. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>). Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Problem

Der Preisfilter in der erweiterten Suche gibt keine ordnungsgemäßen Ergebnisse zurück, wenn er zusammen mit dem SKU-Filter verwendet wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie mehrere Produkte, z. B.:

   | SKU | -Name | Preis | Menge |
   |-----|-----------|-------|----------|
   | MJ1 | Produkt 1 | 10 $ | 10 |
   | MJ2 | Produkt 2 | 15 $ | 10 |
   | MJ3 | Produkt 3 | 21 $ | 10 |
   | MJ4 | Produkt 4 | 32 $ | 10 |
   | MJ5 | Produkt 5 | 33 $ | 10 |
   | MJ6 | Produkt 6 | 34 $ | 10 |
   | MJ7 | Produkt 7 | 44 $ | 10 |

1. Öffnen Sie die **[!UICONTROL Advanced Search]** in der Storefront und suchen Sie nach SKU: „MJ“.
1. Klicken Sie auf den Link **[!UICONTROL Modify your search]** .
1. Fügen Sie den Kriterien eine Preisspanne von *1* bis *21* hinzu und klicken Sie auf die Schaltfläche **[!UICONTROL Search]** .

<u>Erwartete Ergebnisse</u>:

Es werden nur Produkte mit Preisen im definierten Bereich zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Produkte mit Preisen über *$ 21* werden zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
