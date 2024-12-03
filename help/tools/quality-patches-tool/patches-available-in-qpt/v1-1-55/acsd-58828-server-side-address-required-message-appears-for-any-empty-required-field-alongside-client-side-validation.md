---
title: 'ACSD-58828: Die serverseitige *Adresse ist erforderlich*-Meldung wird für jedes leere erforderliche Feld neben der clientseitigen Validierung angezeigt.'
description: Wenden Sie den Patch ACSD-58828 an, um das Adobe Commerce-Problem zu beheben, bei dem neben der clientseitigen Validierungsmeldung die serverseitige Validierungsmeldung *Adresse erforderlich* angezeigt wird, wenn ein erforderliches Feld leer gelassen wird.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
source-git-commit: 3b47046d31a6f71f8c366fb468f435633832c039
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# ACSD-58828: Die serverseitige Meldung *Adresse ist erforderlich* wird für jedes leere erforderliche Feld neben der clientseitigen Validierung angezeigt.

Der Patch ACSD-58828 behebt das Problem, dass die serverseitige Validierungsmeldung *Adresse erforderlich* angezeigt wird, wenn ein erforderliches Feld leer gelassen wird, neben der clientseitigen Validierungsmeldung. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID lautet ACSD-58828. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die serverseitige Validierungsmeldung &quot;*Adresse ist erforderlich*&quot; wird angezeigt, wenn ein erforderliches Feld neben der clientseitigen Validierungsmeldung leer gelassen wird.

Zu reproduzierende Schritte:

1. Melden Sie sich als Kunde an.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Fahren Sie mit dem Checkout fort.
1. Lassen Sie die Lieferadresse unverändert.
1. Wählen Sie den Wert **[!UICONTROL Flat rate]** und danach **[!UICONTROL Next]** aus.
1. Deaktivieren Sie **[!UICONTROL My billing and shipping address are the same]**.
1. Fügen Sie eine neue Adresse aus dem Dropdown-Menü hinzu.
1. Lassen Sie jedes erforderliche Feld leer und wählen Sie **[!UICONTROL Update]** aus.

Erwartete Ergebnisse:

Die Fehlermeldung beschreibt fehlende oder falsche Informationen, die zum Auschecken erforderlich sind.

Ergebnisse:

Die Fehleradresse *ist erforderlich. Geben Sie ein und versuchen Sie es erneut.* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
