---
title: "ACSD-46581: Der geschätzte Steuergesamtbetrag wird nach Auswahl eines Landes im Warenkorb nicht aktualisiert."
description: Wenden Sie den Patch ACSD-46581 an, um das Adobe Commerce-Problem zu beheben, bei dem der Steuersatz nach dem Wechsel des Landes in den Warenkorb nicht aktualisiert wird.
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-46581: Der geschätzte Steuergesamtbetrag wird nach Auswahl eines Landes im Warenkorb nicht aktualisiert

Dieser Patch ACSD-46581 behebt das Problem, dass der Steuersatz nach dem Wechsel des Landes in den Warenkorb nicht aktualisiert wird. Es wird nur aktualisiert, nachdem die Versandmethode ausgewählt wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 installiert ist. Die Patch-ID lautet ACSD-46581. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Steuersatz wird nach dem Wechsel des Landes in den Warenkorb nicht aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie im Adobe Commerce-Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Erstellen Sie einen neuen Steuersatz für **[!UICONTROL Country]** = _Vereinigte Staaten_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Erstellen Sie einen neuen Steuersatz für **[!UICONTROL Country]** = _Indien_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Erstellen Sie eine Steuerregelung mit Steuersätzen für die USA und Indien.
1. Wechseln Sie zu **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** und aktivieren Sie mehr als eine Versandmethode (_Pauschalsatz_ und _Free Shipping_ zum Beispiel).
1. Erstellen Sie ein einfaches Produkt mit der Steuerklasse **[!UICONTROL Taxable Goods]** .
1. Fügen Sie dem Warenkorb auf der Vorderseite des Stores ein Produkt hinzu.
1. Öffnen Sie den Warenkorb und überprüfen Sie den Steuerbetrag.
1. Die Standardsteuereinstellungen für die USA werden angewendet und die Steuer wird auf der Grundlage eines Steuersatzes von 8,25 % berechnet.
1. Schaltet das Land nach Indien um.

<u>Erwartete Ergebnisse</u>:

Der Steuerbetrag änderte sich beim Umstieg des Landes auf Indien auf 10%.

<u>Tatsächliche Ergebnisse</u>:

Der Steuerbetrag bleibt im gesamten Abschnitt des Warenkorbs gleich.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
