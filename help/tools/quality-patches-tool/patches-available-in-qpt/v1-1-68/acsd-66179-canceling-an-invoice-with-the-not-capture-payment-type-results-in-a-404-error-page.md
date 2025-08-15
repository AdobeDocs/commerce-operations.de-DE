---
title: 'ACSD-66179: Eine Stornierung einer Rechnung mit dem [!UICONTROL Not Capture] Zahlungstyp führt zu einer 404-Fehlerseite'
description: Wenden Sie den Patch ACSD-66179 an, um das Adobe Commerce-Problem zu beheben, bei dem die Stornierung einer Rechnung mit dem [!UICONTROL Not Capture] Zahlungstyp zu einer 404-Fehlerseite führte.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179: Eine Stornierung einer Rechnung mit dem [!UICONTROL Not Capture] Zahlungstyp führt zu einer 404-Fehlerseite

Mit dem Patch ACSD-66179 wird das Problem behoben, dass die Stornierung einer Rechnung, die mit dem *[!UICONTROL Not Capture]* Zahlungstyp erstellt wurde, zu einer 404-Fehlerseite führte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66179. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Stornieren einer Rechnung, die mit dem *[!UICONTROL Not Capture]* Zahlungstyp erstellt wurde, führt zu einer 404-Fehlerseite.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit einer Zahlungsmethode wie PayPal Express Checkout.
1. Rechnung erstellen. Legen Sie **[!UICONTROL Amount]** auf *[!UICONTROL Not Capture]* fest und übermitteln Sie die Rechnung.
1. Öffnen Sie die erstellte Rechnung und wählen Sie **[!UICONTROL Cancel]** aus.

<u>Erwartete Ergebnisse</u>:

1. Die Rechnung wurde erfolgreich storniert.
1. Eine Erfolgsmeldung wird angezeigt: *Sie haben die Rechnung storniert.*

<u>Tatsächliche Ergebnisse</u>:

Eine 404-Fehlerseite wird angezeigt: *Seite nicht gefunden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
