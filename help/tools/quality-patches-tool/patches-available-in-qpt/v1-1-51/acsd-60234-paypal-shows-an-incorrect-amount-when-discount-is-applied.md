---
title: 'ACSD-60234: [!DNL PayPal] zeigt einen falschen Betrag an, wenn ein Rabatt angewendet wird'
description: Wenden Sie den Patch ACSD-60234 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL PayPal] einen falschen Betrag anzeigt, wenn der Rabatt über die Zahlungsmethode angewendet wird.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234: [!DNL PayPal] zeigt einen falschen Betrag an, wenn der Rabatt angewendet wird

Der Patch ACSD-60234 behebt das Problem, dass [!DNL PayPal] einen falschen Betrag anzeigt, wenn der Rabatt über die Zahlungsmethode angewendet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist. Die Patch-ID ist ACSD-60234. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL PayPal] zeigt einen falschen Betrag an, wenn der Rabatt über die Zahlungsmethode angewendet wird.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie *[!DNL PayPal Express]* in **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] kann [!UICONTROL Yes] oder [!UICONTROL NO] sein, das Problem wird in beiden Szenarien reproduziert.
1. Erstellen Sie eine *[!UICONTROL Cart Rule]* in **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Bedingung: Wenn alle dieser Bedingungen wahr sind: *[!UICONTROL Payment Method]* ist *[!DNL PayPal Express Checkout]*.
   * Aktionen: Alle Aktionen.
1. Erstellen Sie ein Produkt.
1. Gehen Sie zur Storefront, fügen Sie das Produkt zum Warenkorb hinzu und gehen Sie dann zum Schritt **[!UICONTROL Payment Method]** im Checkout.
1. Stellen Sie sicher, dass Sie &quot;*[!DNL PayPal Express]*&quot;auswählen und überprüfen, ob der Rabatt korrekt angewendet wird.
1. Klicken Sie auf die Schaltfläche **[!DNL PayPal]** .
1. Melden Sie sich an und beobachten Sie den Inhalt des Popup-Fensters.

<u>Erwartete Ergebnisse</u>:

Der an [!DNL PayPal] übergebene Betrag enthält den Rabatt so, wie er sich im Warenkorb befindet.

<u>Tatsächliche Ergebnisse</u>:

Der zu zahlende Gesamtbetrag enthält den Rabatt nicht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
