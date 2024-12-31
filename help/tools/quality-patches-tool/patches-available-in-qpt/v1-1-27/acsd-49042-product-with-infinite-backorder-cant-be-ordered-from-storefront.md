---
title: 'ACSD-49042: Produkt mit unendlicher Rückbestellung kann nicht über die Storefront bestellt werden'
description: Wenden Sie den Patch ACSD-49042 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produkt mit unendlicher Rückreihenfolge nicht über die Storefront bestellt werden kann.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49042: Produkt mit unendlicher Rückbestellung kann nicht über die Storefront bestellt werden

Mit dem Patch ACSD-49042 wird das Problem behoben, dass ein Produkt mit unendlicher Rückreihenfolge nicht über die Storefront bestellt werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-49042. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Fehler tritt auf, wenn ein Produkt mit unendlicher Rückreihenfolge nicht über die Storefront bestellt werden kann.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie die folgenden Konfigurationseinstellungen fest:
   * **[!UICONTROL Display Out of Stock Products]** auf *[!UICONTROL Yes]* gesetzt.
   * **[!UICONTROL Backorders]** auf *[!UICONTROL Allow Qty Below 0]* gesetzt.
1. Fügen Sie eine neue **[!DNL custom stock]** und **[!DNL custom source]** hinzu.
1. Weisen Sie dem **[!DNL custom source]** ein Produkt zu und stellen Sie sicher, dass eine Inventarnummer dafür festgelegt ist (z. B.: *10*).
1. Öffnen Sie auf der Seite „Produktbearbeitung“ **[!UICONTROL Advanced Inventory]**. Legen Sie die **[!UICONTROL minimum quantity]** im Warenkorb fest (z. B.: *160*). Die Menge muss über dem Lagerbestand liegen.
1. Gehen Sie in die Storefront und kaufen Sie ein Produkt, um eine Reservierung zu erstellen.
1. Ändern Sie die **[!UICONTROL product quantity]** in *0*. Der kritische Punkt ist, das Produkt aus dem **[!DNL Admin panel]** zu speichern, wenn es eine Reservierung gibt.
1. Öffnen Sie die **[!UICONTROL product page]** in der Storefront und versuchen Sie, das Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, das Produkt zum Warenkorb hinzuzufügen, da Nachbestellungen für eine Menge unter *0* zulässig sind.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird als nicht vorrätig angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
