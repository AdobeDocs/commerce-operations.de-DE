---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] mit Fehlerbedingung für Coupons und Versandmethoden in der Admin-Benutzeroberfläche'
description: Wenden Sie den Patch ACSD-63992 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!UICONTROL Cart Price Rule] mit einem Coupon und einer Bedingung, die auf einer Versandmethode basiert, nicht korrekt über die Admin-Benutzeroberfläche angewendet werden kann.
feature: Price Rules, Admin Workspace
role: Admin, Developer
source-git-commit: ef17f2f75eae16e3efada4ea08ee0f068fd60702
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-63992: [!UICONTROL Cart Price Rule] mit Fehlerbedingung für Coupons und Versandmethoden in der Admin-Benutzeroberfläche

Mit dem Patch ACSD-63992 wird das Problem behoben, dass die [!UICONTROL Cart Price Rule] mit einem Coupon und einer auf einer Versandmethode basierenden Bedingung nicht korrekt über die Admin-Benutzeroberfläche angewendet werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 installiert ist. Die Patch-ID ist ACSD-63992. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn eine Warenkorbregel im Abschnitt **[!UICONTROL Conditions]** eine Bedingung für die Versandmethode enthält, gilt der zugehörige Couponcode nicht bei der Erstellung einer Bestellung über das Admin Panel. Stattdessen zeigt das System den folgenden Fehler an:

_Der Gutscheincode &lt;> ist ungültig. Überprüfen Sie den Code und versuchen Sie es erneut._

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Warenkorb-Preisregel und beschreiben Sie deren Bedingungen:
   * Unter *[!UICONTROL Conditions]*: Fügen Sie eine Bedingung hinzu, um die Versandmethode einzuschließen (z. B. *[!UICONTROL Flat Rate]*).
   * Unter *[!UICONTROL Rule Information]*: Setzen Sie **[!UICONTROL Coupon]** auf *[!UICONTROL Specific Coupon]* und geben Sie dann **[!UICONTROL Coupon Code]** als *TEST* ein.
1. Erstellen Sie eine neue Bestellung im Admin-Bedienfeld und geben Sie den Couponcode *TEST* in das Feld **[!UICONTROL Apply Coupon]** ein.

<u>Erwartete Ergebnisse</u>:

Der Coupon wird erfolgreich angewendet.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird angezeigt:

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
