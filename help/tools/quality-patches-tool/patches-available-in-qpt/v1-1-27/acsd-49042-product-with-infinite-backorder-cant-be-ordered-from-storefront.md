---
title: "ACSD-49042: Produkt mit unendlichem Backorder kann nicht von der Storefront bestellt werden"
description: Wenden Sie den Patch ACSD-49042 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: Produkt mit unendlichem Backorder kann nicht von der Storefront bestellt werden

Der Patch ACSD-49042 behebt das Problem, dass ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-49042. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Fehler tritt auf, wenn ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie die folgenden Konfigurationseinstellungen fest:
   * **[!UICONTROL Display Out of Stock Products]** auf *[!UICONTROL Yes]* gesetzt.
   * **[!UICONTROL Backorders]** auf *[!UICONTROL Allow Qty Below 0]* gesetzt.
1. Fügen Sie neue **[!DNL custom stock]** und **[!DNL custom source]** hinzu.
1. Weisen Sie ein Produkt dem Wert &quot;**[!DNL custom source]**&quot;zu und stellen Sie sicher, dass dafür eine Inventarnummer festgelegt ist (z. B. *10*).
1. Öffnen Sie auf der Produktebearbeitungsseite **[!UICONTROL Advanced Inventory]**. Legen Sie den Wert **[!UICONTROL minimum quantity]** im Warenkorb fest (z. B. *160*). Die Menge muss über dem Bestand liegen.
1. Gehen Sie zur Storefront und kaufen Sie ein Produkt, um eine Reservierung zu erstellen.
1. Ändern Sie die **[!UICONTROL product quantity]** in *0*. Der entscheidende Punkt ist, das Produkt aus dem **[!DNL Admin panel]** zu speichern, wenn eine Reservierung vorliegt.
1. Öffnen Sie die **[!UICONTROL product page]** in der Storefront und versuchen Sie, das Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, das Produkt zum Warenkorb hinzuzufügen, da Backorder für eine Menge unter *0* zulässig sind.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird als nicht vorrätig angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
