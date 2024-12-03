---
title: 'ACSD-61348: Wishlist-Elemente über GraphQL sichtbar, aber nicht auf Storefront'
description: Wenden Sie den Patch ACSD-61348 an, um das Adobe Commerce-Problem zu beheben, bei dem die Elemente der Wunschliste über GraphQL sichtbar sind, aber nicht in einer Umgebung mit mehreren Websites auf der Storefront.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
source-git-commit: c1d3d3056d1ee3c33db6c14ed10a1df08f962795
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: Wishlist-Elemente über GraphQL sichtbar, aber nicht auf Storefront

Der Patch ACSD-61348 behebt das Problem, dass die Wunschlisten-Elemente über GraphQL sichtbar sind, aber nicht auf der Storefront in einer Umgebung mit mehreren Websites. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-61348. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Elemente der Wunschliste sind über GraphQL sichtbar, jedoch nicht in einer Umgebung mit mehreren Websites auf der Storefront.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie zwei Websites.
1. Gehen Sie zu **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** und legen Sie **[!UICONTROL Share Customer Accounts]** auf *[!UICONTROL Global]* fest.
1. Gehen Sie zu **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** und legen Sie **[!UICONTROL Enable Multiple Wish Lists]** auf *Ja* fest.
1. Gehen Sie zu **[!UICONTROL Config General]** > **[!UICONTROL Web]** und legen Sie **[!UICONTROL Add Store Code to URLs]** auf *Ja* fest.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es der zweiten Website zu.
1. Erstellen Sie einen Kunden und melden Sie sich an.
1. Fügen Sie der Wunschliste ein Produkt hinzu.
1. Weisen Sie das Produkt der Standardwebsite zu.
1. Gehen Sie auf der Standardwebsite zur Seite &quot;*[!UICONTROL Wishlist]*&quot;.

<u>Erwartete Ergebnisse</u>:

Das Produkt steht auf der Wunschliste.

<u>Tatsächliche Ergebnisse</u>:

Auf der Wunschliste stehen keine Produkte.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
