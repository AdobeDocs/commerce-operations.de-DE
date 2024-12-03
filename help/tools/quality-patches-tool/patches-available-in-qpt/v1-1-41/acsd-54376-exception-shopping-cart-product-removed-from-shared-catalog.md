---
title: 'ACSD-54376: Ausnahme im Warenkorb, wenn das Produkt aus [!UICONTROL shared catalog] entfernt wurde'
description: Wenden Sie den Patch ACSD-54376 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Ausnahme im Warenkorb auftritt, wenn ein Produkt aus dem [!UICONTROL shared catalog] entfernt wird, nachdem es zum Warenkorb hinzugefügt wurde.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: 59047ccb-d434-46cd-8d2f-ceb0c85a785a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-54376: Ausnahme im Warenkorb, wenn das Produkt aus [!UICONTROL shared catalog] entfernt wurde

Der Patch ACSD-54376 behebt das Problem, dass im Warenkorb eine Ausnahme auftritt, wenn ein Produkt aus dem [!UICONTROL shared catalog] entfernt wird, nachdem es zum Warenkorb hinzugefügt wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-54376. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Im Warenkorb tritt eine Ausnahme auf, wenn ein Produkt aus dem [!UICONTROL shared catalog] entfernt wird, nachdem es zum Warenkorb hinzugefügt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit B2B.
1. Aktivieren Sie [!UICONTROL shared catalog].
1. Erstellen Sie ein Produkt und weisen Sie es dem standardmäßigen [!UICONTROL shared catalog] zu.
1. Fügen Sie dem Warenkorb ein Produkt aus der Storefront hinzu.
1. Entfernen Sie das Produkt aus dem [!UICONTROL shared catalog].
1. Navigieren Sie über das Dropdown-Menü &quot;Mini-Warenkorb&quot;zur Checkout-Seite.

<u>Erwartete Ergebnisse</u>:

Ausnahmen werden bearbeitet und Ihnen nicht angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Eine nicht verarbeitete Ausnahme wird auf der Checkout-Seite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
