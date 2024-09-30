---
title: '"ACSD-53176: Produktregel mit der Bedingung "ist eins von" stimmt nicht überein."'
description: Wenden Sie den Patch ACSD-53176 an, um das Adobe Commerce-Problem zu beheben, bei dem die zugehörige Produktregel "ist eine von"-Bedingung für "Produkte, die übereinstimmen"nicht richtig funktioniert.
feature: Marketing Tools
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176: Produktregel mit `is one of` -Bedingung stimmt nicht überein

Der Patch ACSD-53176 behebt das Problem, dass die zugehörige Bedingung der Produktregel `is one of` für **Produkte, die mit** übereinstimmen, nicht richtig funktioniert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-53176. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bedingung der zugehörigen Produktregel `is one of` funktioniert für **Produkte, die übereinstimmen**, nicht ordnungsgemäß.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie 3 bis 4 Produkte.
1. Erstellen Sie eine neue verwandte Produktregel.

   Legen Sie die Regel so fest, dass sie mit zwei oder mehr Produkten übereinstimmt:
   * `SKU is one of "S1,S2".`

   Legen Sie die Regel fest, um zwei oder mehr Elemente anzuzeigen:
   * `Product SKU is one of constant value "S2,S3".`

1. Öffnen Sie das S1-Produkt in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die verwandten Produkte &quot;S2&quot;und &quot;S3&quot;werden auf beiden Produktseiten &quot;S1&quot;und &quot;S2&quot;angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Zugehörige Produkte werden nicht auf den Produktseiten angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
