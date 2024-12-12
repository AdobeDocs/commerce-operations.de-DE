---
title: 'ACSD-50949: Der Preisfilter in der erweiterten Suche liefert keine korrekten Ergebnisse, wenn er zusammen mit dem SKU-Filter verwendet wird.'
description: Wenden Sie den Patch ACSD-50949 an, um das Adobe Commerce-Problem zu beheben, bei dem der Preisfilter bei der erweiterten Suche keine richtigen Ergebnisse liefert, wenn er zusammen mit dem SKU-Filter verwendet wird.
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949: Der Preisfilter in der erweiterten Suche gibt bei Verwendung mit dem SKU-Filter keine korrekten Ergebnisse zurück

Der Patch ACSD-50949 behebt das Problem, dass der Preisfilter in der erweiterten Suche keine richtigen Ergebnisse zurückgibt, wenn er zusammen mit dem SKU-Filter verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50949. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Problem

Der Preisfilter in der erweiterten Suche gibt keine korrekten Ergebnisse zurück, wenn er zusammen mit dem SKU-Filter verwendet wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie mehrere Produkte, beispielsweise:

   | SKU | Name | Preis | Menge |
   |-----|-----------|-------|----------|
   | MJ1 | Produkt 1 | 10$ | 10 |
   | MJ2 | Produkt 2 | 15$ | 10 |
   | MJ3 | Produkt 3 | 21 $ | 10 |
   | MJ4 | Produkt 4 | 32 $ | 10 |
   | MJ5 | Produkt 5 | 33$ | 10 |
   | MJ6 | Produkt 6 | 34 $ | 10 |
   | MJ7 | Produkt 7 | 44$ | 10 |

1. Öffnen Sie die **[!UICONTROL Advanced Search]** in der Storefront und suchen Sie nach SKU: &quot;MJ&quot;.
1. Klicken Sie auf den Link **[!UICONTROL Modify your search]** .
1. Fügen Sie den Kriterien einen Preisbereich von *1* bis *21* hinzu und klicken Sie auf die Schaltfläche **[!UICONTROL Search]** .

<u>Erwartete Ergebnisse</u>:

Nur Produkte mit Preisen im definierten Bereich werden zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Produkte mit höheren Preisen als *$21* werden zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
