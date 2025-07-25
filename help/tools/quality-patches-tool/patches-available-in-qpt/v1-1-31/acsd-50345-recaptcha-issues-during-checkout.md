---
title: 'ACSD-50345: reCAPTCHA-Probleme während des Checkouts'
description: Wenden Sie den ACSD-50345 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die reCAPTCHA-v2- und -v3-Validierungen beim Aufgeben von Bestellungen und während des Checkouts fehlschlagen.
feature: Checkout, Orders
role: Admin
exl-id: eae9a6ad-0999-4581-b3c0-7667ee7beb54
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-Probleme während des Checkouts

Mit dem Patch ACSD-50345 wird das Problem behoben, dass die Validierungen von reCAPTCHA v2 und v3 beim Aufgeben von Bestellungen und während des Checkouts fehlschlagen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31 installiert ist. Die Patch-ID ist ACSD-50345. Beachten Sie, dass das Problem teilweise in Adobe Commerce 2.4.6 behoben wurde und in Adobe Commerce 2.4.7 vollständig behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

**#1**

Google reCAPTCHA v2 wird nach dem Übermitteln einer fehlgeschlagenen Zahlung nicht neu geladen.

<u>Schritte zur Reproduktion</u>

1. Konfigurieren Sie **[!UICONTROL Google reCAPTCHA v2]** (*bin kein Roboter*).
1. Aktivieren Sie die **[!UICONTROL reCAPTCHA]** für den Checkout.
1. Versuchen Sie, eine Bestellung aufzugeben, ohne auf **[!UICONTROL reCAPTCHA]** zu klicken.
1. Sobald der/die Benutzende die Fehlermeldung für das fehlende reCAPTCHA erhalten hat (*reCAPTCHA-Validierung fehlgeschlagen, bitte erneut versuchen*), auf das **[!UICONTROL reCAPTCHA]** klicken und dann versuchen, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>

Die Bestellung wird nicht mit einem falschen reCAPTCHA aufgegeben.

<u>Tatsächliche Ergebnisse</u>

Es wird ein Fehler ausgelöst - *reCAPTCHA-Validierung fehlgeschlagen, erneut versuchen* und *Kein solcher Warenkorb mit ID = 4*

**#2**

Google reCAPTCHA v3 Invisible funktioniert nicht beim Checkout und die Bestellung kann nicht aufgegeben werden. `PlaceOrder` Ereignis wird nicht ausgelöst.

<u>Schritte zur Reproduktion</u>

1. Konfigurieren Sie die **[!UICONTROL reCAPTCHA v3 Invisible]** über die **[!UICONTROL Security]** **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > .
1. Aktivieren Sie **[!UICONTROL reCAPTCHA v3 Invisible]** für den Checkout/die Bestellung auf der Registerkarte **[!UICONTROL Storefront]** .
1. Versuchen Sie, eine Bestellung mit der [!UICONTROL Check/Money order] Zahlungsmethode aufzunehmen.

<u>Erwartete Ergebnisse</u>

Die Bestellung sollte bei eingeschaltetem **[!UICONTROL reCAPTCHA]** erfolgen.

<u>Tatsächliche Ergebnisse</u>

Nach dem Klicken auf die Schaltfläche &quot;**[!UICONTROL Place Order]**&quot; wird sie deaktiviert, und es passiert nichts weiter.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
