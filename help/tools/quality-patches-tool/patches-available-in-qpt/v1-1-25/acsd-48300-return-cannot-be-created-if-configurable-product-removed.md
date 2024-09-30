---
title: "ACSD-48300: return cannot be created if configuring product is removed"
description: Wenden Sie den Patch ACSD-48300 an, um das Adobe Commerce-Problem zu beheben, bei dem die Rückgabe nicht erstellt werden kann, wenn das konfigurierbare Produkt entfernt wird.
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-48300: Rückgabe kann nicht erstellt werden, wenn ein konfigurierbares Produkt entfernt wird

Der Patch ACSD-48300 behebt das Problem, dass eine Rückgabe nicht erstellt werden kann, wenn das konfigurierbare Produkt entfernt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48300. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Rückgabe kann nicht erstellt werden, wenn das konfigurierbare Produkt entfernt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie RMA auf der Storefront unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**.
1. Erstellen Sie ein konfigurierbares Produkt.
1. Erstellen Sie im Storefront ein Konto (und/oder melden Sie sich an).
1. Fügen Sie als ersten Artikel ein konfigurierbares Produkt zum Warenkorb hinzu.
1. Fügen Sie danach jedes einfache Produkt hinzu.
1. Platzieren Sie die Bestellung.
1. Schicken Sie die Bestellung.
1. Löschen Sie jetzt nur das konfigurierbare Produkt (löschen Sie nicht die untergeordneten Produkte).
1. Wechseln Sie in der Storefront zu **[!UICONTROL My Orders]** und zeigen Sie die Bestellung an.
1. Klicken Sie auf **[!UICONTROL Return]**.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann Elemente zurückgeben, auch wenn das konfigurierbare Produkt gelöscht wurde.

<u>Tatsächliche Ergebnisse</u>:

Beim Zurückgeben von Elementen tritt ein Fehler auf.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
