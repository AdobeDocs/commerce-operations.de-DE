---
title: 'ACSD-51204: Das Produkt wird nach der Erstellung der Gutschrift nicht wieder auf Lager zurückgegeben'
description: Wenden Sie den ACSD-51204 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Produkt nach der Erstellung der Gutschrift nicht wieder auf Lager ist.
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51204: Das Produkt wird nach der Erstellung der Gutschrift nicht wieder auf Lager zurückgegeben

Mit dem Patch des ACSD-51204 wird das Problem behoben, dass das Produkt nach der Erstellung der Gutschrift nicht wieder auf Lager ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51204. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das ausverkaufte Produkt wird nach der Erstellung der Gutschrift nicht wieder auf Lager zurückgegeben.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie **[!UICONTROL Adobe Commerce]** und aktivieren Sie die **[!UICONTROL Inventory Management Module]** nur mit *(Quelle* und *Lager*.
1. Fügen Sie eine **[!UICONTROL new product]** mit einer Menge von *10“*.
1. Weisen Sie das Produkt dem **[!UICONTROL default stock]** zu.
1. Fügen Sie das Produkt in der Storefront zum Warenkorb hinzu und bestellen Sie eine ganze verfügbare Menge von 10 Stück.
1. Generieren Sie im Admin-Panel eine *Rechnung* und *Lieferung* für die Bestellung.
1. Erstellen Sie eine **[!UICONTROL Credit Memo]**, bei *das Kontrollkästchen „Auf Lager*&quot; für alle Elemente aktiviert ist.
1. Überprüfen Sie die **[!UICONTROL Salable Quantity]** des Produkts im Admin-Bereich.

<u>Erwartete Ergebnisse</u>:

Die verkaufsfähige Menge des Erzeugnisses muss wieder auf *10*.

<u>Tatsächliche Ergebnisse</u>:

Die verkaufsfähige Menge des Erzeugnisses bleibt bei *0*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool].
