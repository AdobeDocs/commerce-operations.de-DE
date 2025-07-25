---
title: 'ACSD-65822: Die Anzahl der im Paket enthaltenen und konfigurierbaren Produkte wird nicht korrekt im Warenkorb angezeigt.'
description: Wenden Sie den Patch ACSD-65822 an, um das Adobe Commerce-Problem zu beheben, bei dem die Menge beim Hinzufügen von Bundle-Produkten im Abschnitt Warenkorb des Kunden im Admin-Bedienfeld als 0 angezeigt wurde.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
source-git-commit: d8421ba07a5d2fa3a3174541ed8cd6a2bc76f157
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# ACSD-65822: Bundle- und konfigurierbare Produktmengen werden in der [!UICONTROL Shopping Cart] nicht korrekt angezeigt

Der Patch ACSD-65822 behebt das Problem, dass Paket- und konfigurierbare Produktmengen im Abschnitt **[!UICONTROL Shopping Cart]** unter *[!UICONTROL Customer's Activities]* nicht korrekt angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-65822. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bundle- und konfigurierbaren Produktmengen werden im **[!UICONTROL Shopping Cart]** unter *[!UICONTROL Customer's Activities]* nicht korrekt angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Benutzer in der Storefront.
2. Erstellen Sie eine **[!UICONTROL Bundle product]** im Admin-Bedienfeld.
3. Fügen Sie in der Storefront als angemeldeter Benutzer das Bundle-Produkt mit einer bestimmten Menge zum Warenkorb hinzu.
4. Wechseln Sie im *Admin*-Bedienfeld zu **[!UICONTROL Customers]** und klicken Sie auf **[!UICONTROL Edit]** für den in Schritt 1 erstellten Kunden.
5. Klicken Sie auf **[!UICONTROL Create Order]**.
6. Überprüfen Sie auf der linken Seite unter *[!UICONTROL Customer's Activities]* den Abschnitt **[!UICONTROL Shopping Cart]** . Das Produktpaket sollte zusammen mit der ausgewählten Menge angezeigt werden.

<u>Erwartete Ergebnisse</u>:

Die Menge des Bundle-Artikels muss mit der in der Storefront angezeigten Menge übereinstimmen.

<u>Tatsächliche Ergebnisse</u>:

Die Menge des Bundle-Artikels wird als 0 angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
