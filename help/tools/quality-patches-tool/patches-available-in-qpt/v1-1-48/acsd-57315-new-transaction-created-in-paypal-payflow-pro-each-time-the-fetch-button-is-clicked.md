---
title: 'ACSD-57315: Bei  [!DNL PayPal Payflow Pro]  Klicken auf die Schaltfläche „Abrufen“ wird in eine neue Transaktion erstellt'
description: Wenden Sie den ACSD-57315 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem in eine neue  [!DNL PayPal Payflow Pro]  erstellt wird, jedes Mal, wenn auf die Schaltfläche Abrufen im Bildschirm Transaktion anzeigen im [!UICONTROL Admin] geklickt wird.
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315: Jedes Mal, wenn auf die Schaltfläche „Abrufen“ geklickt wird, wird in [!DNL PayPal Payflow Pro] eine neue Transaktion erstellt

Mit dem Patch ACSD-57315 wird das Problem behoben, dass in [!DNL PayPal Payflow Pro] jedes Mal, wenn auf dem Bildschirm Transaktion anzeigen im [!UICONTROL Admin] auf die Schaltfläche Abrufen geklickt wird, eine neue Transaktion erstellt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57315. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

In [!DNL PayPal Payflow Pro] wird jedes Mal eine neue Transaktion erstellt, wenn auf dem Bildschirm Transaktion anzeigen im [!UICONTROL Admin] auf die Schaltfläche Abrufen geklickt wird.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie [!DNL PayPal Payflow Pro].
1. Legen Sie die Transaktionsmethode auf *[!UICONTROL Sale]* fest.
1. Bestellen Sie mit *Kreditkarte*.
1. Öffnen Sie die Transaktion über [!UICONTROL Admin].
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Fetch]** .
1. Prüfen Sie [!DNL PayPal] Konto auf Transaktionen im Zusammenhang mit der aufgegebenen Bestellung.

<u>Erwartete Ergebnisse</u>:

Es wird keine neue Zahlungsbuchung erstellt.

<u>Tatsächliche Ergebnisse</u>:

Für eine bereits bezahlte Bestellung wird eine neue Zahlungsbuchung erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
