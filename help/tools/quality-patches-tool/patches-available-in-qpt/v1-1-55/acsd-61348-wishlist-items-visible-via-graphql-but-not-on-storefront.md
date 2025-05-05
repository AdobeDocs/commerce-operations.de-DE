---
title: 'ACSD-61348: Artikel auf der Wunschliste, die über GraphQL, aber nicht auf der Storefront sichtbar sind'
description: Wenden Sie den ACSD-61348-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Elemente der Wunschliste über GraphQL sichtbar sind, jedoch nicht in der Storefront in einer Umgebung mit mehreren Websites.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
source-git-commit: c1d3d3056d1ee3c33db6c14ed10a1df08f962795
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: Artikel auf der Wunschliste, die über GraphQL, aber nicht auf der Storefront sichtbar sind

Mit dem Patch ACSD-61348 wird das Problem behoben, dass die Elemente der Wunschliste über GraphQL sichtbar sind, jedoch nicht in der Storefront in einer Umgebung mit mehreren Websites. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-61348. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wunschlistenelemente sind in einer Umgebung mit mehreren Websites über GraphQL sichtbar, jedoch nicht in der Storefront.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie zwei Websites.
1. Gehen Sie zu **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** und setzen Sie **[!UICONTROL Share Customer Accounts]** auf *[!UICONTROL Global]*.
1. Gehen Sie zu **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** und setzen Sie **[!UICONTROL Enable Multiple Wish Lists]** auf *Ja*.
1. Navigieren Sie zu **[!UICONTROL Config General]** > **[!UICONTROL Web]** und setzen Sie **[!UICONTROL Add Store Code to URLs]** auf *Ja*.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es der zweiten Website zu.
1. Erstellen Sie einen Kunden und melden Sie sich an.
1. Fügen Sie ein Produkt zur Wunschliste hinzu.
1. Weisen Sie das Produkt der Standard-Website zu.
1. Rufen Sie die Seite *[!UICONTROL Wishlist]* auf der Standard-Website auf.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist auf der Wunschliste.

<u>Tatsächliche Ergebnisse</u>:

Es befinden sich keine Produkte auf der Wunschliste.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
