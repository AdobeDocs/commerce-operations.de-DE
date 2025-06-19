---
title: 'ACSD-51899: Standardmäßige Lieferadresse wurde falsch ausgefüllt'
description: Wenden Sie den Patch ACSD-51899 an, um das Problem in Adobe Commerce zu beheben, bei dem die standardmäßige Versandadresse automatisch mit einer falschen Adresse ausgefüllt wird.
feature: Checkout
role: Admin
exl-id: 14e48613-6af8-476c-978d-87c27a0b0d15
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-51899: Standardmäßige Lieferadresse wurde falsch ausgefüllt

Mit dem Patch ACSD-51899 wird das Problem behoben, dass die standardmäßige Versandadresse automatisch mit einer falschen Adresse ausgefüllt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51899. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die standardmäßige Lieferadresse wird automatisch mit einer falschen Adresse ausgefüllt

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **In-Store** Abholung unter Versandmethode.
1. Erstellen Sie *Lager* und *Quelle*.
1. Erstellen Sie ein Produkt und weisen Sie es der Quelle zu.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Klicken Sie **Mini-Warenkorb auf** Zur Kasse gehen“.
1. Geben Sie die Test-E-Mail-Adresse ein und wählen **Pick In Store**.
1. Klicken Sie auf **Store auswählen** und wählen Sie einen Store-Speicherort für die Auswahl aus.
1. Klicken Sie auf die **Weiter**-Schaltfläche.
1. Navigieren Sie zur **Startseite** indem Sie auf das Store-Logo klicken.
1. Öffnen Sie den **Mini-Warenkorb**.
1. Klicken Sie auf den unteren Hyperlink mit dem Namen **Warenkorb anzeigen und bearbeiten**.
1. Klicken Sie **Weiter zur Kasse**.
1. Klicken Sie auf der Versandseite auf die Schaltfläche Versand .

<u>Erwartete Ergebnisse</u>

Das Feld Lieferadresse bleibt leer, mit Ausnahme von *Land, Region und Postleitzahl*.

<u>Tatsächliche Ergebnisse</u>

Die standardmäßige Versandadresse wird nach dem Aktualisieren der Seite automatisch mit *Abholadresse* Ladengeschäft“ ausgefüllt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
