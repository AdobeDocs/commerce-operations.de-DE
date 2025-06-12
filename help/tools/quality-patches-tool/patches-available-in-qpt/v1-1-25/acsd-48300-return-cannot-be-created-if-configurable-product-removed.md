---
title: 'ACSD-48300: Rückgabe kann nicht erstellt werden, wenn konfigurierbares Produkt entfernt wird'
description: Wenden Sie den ACSD-48300-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem keine Rückgabe erstellt werden kann, wenn das konfigurierbare Produkt entfernt wird.
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
exl-id: 50139364-e2ea-47a8-9bca-09876dd0e70d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-48300: Rückgabe kann nicht erstellt werden, wenn konfigurierbares Produkt entfernt wird

Mit dem Patch ACSD-48300 wird das Problem behoben, dass keine Rückgabe erstellt werden kann, wenn das konfigurierbare Produkt entfernt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48300. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Rückgabe kann nicht erstellt werden, wenn das konfigurierbare Produkt entfernt wird.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie RMA in der Storefront unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**.
1. Erstellen Sie ein konfigurierbares Produkt.
1. Erstellen Sie in der Storefront ein Konto (und/oder melden Sie sich an).
1. Fügen Sie als ersten Artikel ein konfigurierbares Produkt zum Warenkorb hinzu.
1. Fügen Sie anschließend ein einfaches Produkt hinzu.
1. Bestellung aufgeben.
1. Versand der Bestellung.
1. Löschen Sie nun nur noch das konfigurierbare Produkt (nicht dessen untergeordnete Produkte).
1. Gehen Sie in der Storefront zu **[!UICONTROL My Orders]** und sehen Sie sich die Bestellung an.
1. Klicken Sie auf **[!UICONTROL Return]**.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann Elemente zurückgeben, obwohl das konfigurierbare Produkt gelöscht wurde.

<u>Tatsächliche Ergebnisse</u>:

Beim Zurückgeben von Elementen tritt ein Fehler auf.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
