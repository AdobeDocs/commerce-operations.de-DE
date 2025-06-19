---
title: 'ACSD-58828: Server-seitige *Adresse ist erforderlich* -Meldung wird für jedes leere erforderliche Feld neben der Client-seitigen Validierung angezeigt'
description: Wenden Sie den ACSD-58828-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Server-seitige Validierungsmeldung *address is required* angezeigt wird, wenn ein erforderliches Feld leer gelassen wird, zusammen mit der Client-seitigen Validierungsmeldung.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828: Server-seitige *Adresse ist erforderlich* Meldung wird für jedes leere erforderliche Feld neben der Client-seitigen Validierung angezeigt

Mit dem Patch ACSD-58828 wird das Problem behoben, dass die Server-seitige Validierungsmeldung *Adresse ist erforderlich* angezeigt wird, wenn ein erforderliches Feld leer bleibt, zusammen mit der Client-seitigen Validierungsmeldung. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58828. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Server-seitige Validierungsmeldung *Adresse ist erforderlich* wird angezeigt, wenn ein erforderliches Feld leer gelassen wird, zusammen mit der Client-seitigen Validierungsmeldung.

Schritte zur Reproduktion:

1. Melden Sie sich als Kunde an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Zur Kasse gehen.
1. Lassen Sie die Lieferadresse unverändert.
1. Wählen Sie die **[!UICONTROL Flat rate]** und dann **[!UICONTROL Next]** aus.
1. Deaktivieren Sie **[!UICONTROL My billing and shipping address are the same]**.
1. Fügen Sie eine neue Adresse aus dem Dropdown-Menü hinzu.
1. Lassen Sie ein erforderliches Feld leer und wählen Sie **[!UICONTROL Update]** aus.

Erwartete Ergebnisse:

Die Fehlermeldung beschreibt fehlende oder falsche Informationen, die zum Auschecken erforderlich sind.

Tatsächliche Ergebnisse:

Der Fehler *Adresse ist erforderlich. Geben Sie ein und versuchen Sie es erneut.*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
