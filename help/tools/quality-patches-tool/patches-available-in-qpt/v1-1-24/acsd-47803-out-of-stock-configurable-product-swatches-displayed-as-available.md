---
title: "ACSD-47803: konfigurierbare, nicht vorrätig konfigurierbare Produktmuster, die als verfügbar angezeigt werden"
description: Wenden Sie den Patch ACSD-47803 an, um das Adobe Commerce-Problem zu beheben, bei dem konfigurierbare nicht vorrätige Produktmuster als verfügbar angezeigt wurden.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803: konfigurierbare, nicht vorrätig verfügbare Produktmuster, die als verfügbar angezeigt werden

Der Patch ACSD-47803 behebt das Problem, dass konfigurierbare nicht vorrätige Produktmuster als verfügbar angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47803. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nicht vorrätig konfigurierbare Produktmuster werden als verfügbar angezeigt.

<u>Zu reproduzierende Schritte</u>:

>[!NOTE]
>
>Die folgenden Schritte beziehen sich als Beispiel auf Beispieldaten.

1. Navigieren Sie in [!UICONTROL Commerce] Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** und setzen Sie die **[!UICONTROL Display Out of Stock Products]** auf *Ja*.
1. Navigieren Sie vom Administrator erneut zu &quot;**[!UICONTROL Catalog]** > &quot;**[!UICONTROL Products]**&quot;und bearbeiten Sie ein konfigurierbares Produkt auf der Seite zur Produktbearbeitung (z. B. &quot;WB04&quot;-SKU, wenn Sie Beispieldaten verwenden):
   * Legen Sie für eine der Konfigurationsvarianten die Menge auf *0* fest (z. B. für &quot;WB04-M-Purple&quot;).
1. Öffnen Sie nun das konfigurierbare Produkt auf der Storefront.
1. Wählen Sie die Produktgröße für die konfigurierbare Variante mit Nullbestand (d. h. &quot;M&quot;) aus.

<u>Erwartete Ergebnisse</u>:

Die nicht vorrätigen Optionen sind deaktiviert und als [!UICONTROL Out of Stock] markiert.

<u>Tatsächliche Ergebnisse</u>:

Alle Farbmuster sind aktiviert, auch die Farbfelder [!UICONTROL Out of Stock].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
