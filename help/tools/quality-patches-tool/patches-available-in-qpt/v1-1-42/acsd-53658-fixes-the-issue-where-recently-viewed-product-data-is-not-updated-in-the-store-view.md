---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** Daten in der Store-Ansicht nicht ordnungsgemäß aktualisiert'
description: Wenden Sie den Patch ACSD-53658 an, um das Adobe Commerce-Problem zu beheben, bei dem **[!UICONTROL Recently Viewed Product]**-Daten in der Store-Ansicht nicht ordnungsgemäß aktualisiert werden.
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** Daten in der Store-Ansicht nicht ordnungsgemäß aktualisiert

Der Patch ACSD-53658 behebt das Problem, dass **[!UICONTROL Recently Viewed Product]** Daten in der Store-Ansicht nicht ordnungsgemäß aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-53658. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die **[!UICONTROL Recently Viewed Product]** werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie eine zweite Shop-Ansicht für die Standard-Website.
1. Erstellen Sie ein einfaches Produkt.
1. Einen anderen Produktnamen für die neue Store-Ansicht festlegen.
1. Erstellen Sie ein **[!UICONTROL Recently Viewed Product]** Widget.
1. Dieses Widget so konfigurieren, dass es auf der Startseite angezeigt wird.
1. Öffnen Sie die Produktseite in der Storefront in der standardmäßigen Store-Ansicht.
1. Öffnen Sie die Startseite.
1. Wechseln Sie mithilfe des Store-Umschalters zur zweiten Store-Ansicht.

<u>Erwartete Ergebnisse</u>:

Der Produktname wird im Widget aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Der Produktname wird im Widget nicht aktualisiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
