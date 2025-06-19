---
title: 'ACSD-51819: Mehrere Bestellungen mit einer einzigen Anführungszeichen-ID aufgeben'
description: Wenden Sie den ACSD-51819 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem mehrere Bestellungen über dieselbe Angebots-ID aufgegeben werden können.
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-51819: Mehrere Bestellungen mit einer einzigen Anführungszeichen-ID aufgeben

Der Patch ACSD-51819 behebt das Problem, dass mehrere Bestellungen über dieselbe Angebots-ID aufgegeben werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-51819. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2, 2.4.5-p5, 2.4.6, 2.4.6-p4, 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p11, 2.4.5-p3 - 2.4.5-p10, 2.4.6 - 2.4.6-p8, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es können mehrere Bestellungen mit derselben Angebotskennung aufgegeben werden.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Benutzer an.
1. Fügen Sie Artikel zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Wählen Sie eine Zahlungsmethode aus, klicken Sie jedoch nicht auf die Schaltfläche **[!UICONTROL Place Order]**.
1. Melden Sie sich bei demselben Konto in einem anderen Browser an.
1. Zur Kasse gehen Sie mit den gleichen Artikeln, ohne auf den **[!UICONTROL Place Order]** zu klicken.
1. Klicken Sie in beiden Systemen gleichzeitig auf die Schaltfläche **[!UICONTROL Place Order]** .
1. Validieren Sie die in beiden Browsern aufgegebenen Bestellungen.

<u>Erwartete Ergebnisse</u>:

Nur die erste Bestellung aus einem Browser wird erfolgreich verarbeitet.

<u>Tatsächliche Ergebnisse</u>:

In beiden Browsern wurden Bestellungen aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
