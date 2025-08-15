---
title: 'ACSD-57003: Der Bestellstatus ändert sich in „Abgeschlossen“, anstatt in „Verarbeitung läuft“ zu wechseln'
description: Wenden Sie den Patch ACSD-57003 an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Bestellstatus in „Abgeschlossen“ ändert, anstatt in „Verarbeitung läuft“ zu wechseln.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-57003: Der Bestellstatus ändert sich in *Abgeschlossen* anstatt in *Verarbeitung* zu wechseln

Mit dem Patch „ACSD-57003“ wird das Problem behoben, dass der Bestellstatus in &quot;*&quot;*, anstatt in &quot;*&quot;*. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.46 installiert ist. Die Patch-ID ist ACSD-57003. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3, 2.4.6-p8, 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p9, 2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Bestellstatus ändert sich in *Abgeschlossen* anstatt in *Verarbeitung* zu wechseln, wenn eine Bestellung teilweise zurückerstattet und teilweise versendet wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit zwei konfigurierbaren Produkten.
1. Alle Positionen fakturieren.
1. Versand nur den ersten Artikel.
1. Gutschrift nur für den versendeten Artikel zurückerstatten/erstellen (*erster Artikel*).
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Bestellstatus muss den Status _Verarbeitung_ aufweisen.

<u>Tatsächliche Ergebnisse</u>:

Der Auftragsstatus ändert sich *Abgeschlossen* nachdem eine Gutschrift für den teilweise gelieferten Artikel erstellt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
