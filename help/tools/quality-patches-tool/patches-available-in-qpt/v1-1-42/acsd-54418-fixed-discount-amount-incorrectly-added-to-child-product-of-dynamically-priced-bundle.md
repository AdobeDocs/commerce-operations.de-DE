---
title: 'ACSD-54418: Fester Abzinsungsbetrag wurde fälschlicherweise zum untergeordneten Produkt eines dynamisch priorisierten Bundles hinzugefügt'
description: Wenden Sie den Patch ACSD-54418 an, um das Adobe Commerce-Problem zu beheben, bei dem der feste Abzinsungsbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch primitierten Bundles angewendet wird.
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54418: Fester Rabattbetrag wurde fälschlicherweise zum untergeordneten Produkt des dynamisch preisgekrönten Bundles hinzugefügt.

Der Patch ACSD-54418 behebt das Problem, bei dem der feste Rabattbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch preisgekrönten Bundles angewendet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.42 installiert ist. Die Patch-ID lautet ACSD-54418. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der feste Abzinsungsbetrag wird fälschlicherweise auf jedes untergeordnete Produkt des dynamisch preisgekrönten Bundles angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL bundle product]** mit dynamischen Preisen und Bundle-Optionen für *2* .
1. Erstellen Sie eine **[!UICONTROL cart price rule]** mit einem bestimmten Couponcode, der nur für das gebündelte Produkt **[!UICONTROL SKU]** gilt und einen festen Rabatt bietet.
1. Fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Wenden Sie die **[!UICONTROL coupon code]** an.
1. Überprüfen Sie den Rabatt, der auf den Warenkorb angewendet wird.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nur einmal auf das gesamte gebündelte Produkt angewendet.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird auf jedes untergeordnete Paket angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
