---
title: 'ACP2E-4050: [!UICONTROL Free Shipping] beim Multi-Shipping-Checkout nicht angewendet'
description: Wenden Sie den ACP2E-4050-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem [!UICONTROL Free Shipping] beim Checkout mit mehreren Adressen nicht angewendet wird, wenn [!UICONTROL Cart Price Rules] Unterauswahlbedingungen und Produkte mit bestimmten Preisen einschließen.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050: **[!UICONTROL Free Shipping]** beim Multi-Shipping-Checkout nicht angewendet

Der Patch ACP2E-4050 behebt das Problem, dass **[!UICONTROL Free Shipping]** beim Multi-Shipping-Checkout nicht angewendet wird, wenn **[!UICONTROL Cart Price Rules]** Unterauswahlbedingungen und Produkte mit bestimmten Preisen enthalten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID lautet ACP2E-4050. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p10

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

**[!UICONTROL Free Shipping]** wird beim Multi-Shipping-Checkout nicht angewendet, wenn **[!UICONTROL Cart Price Rules]** Unterauswahlbedingungen und Produkte mit spezifischen Preisen enthalten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Kundenkonto mit zwei Adressen.
1. Aktivieren Sie **[!UICONTROL Free Shipping]** und setzen Sie **[!UICONTROL Minimum Order Amount]** auf *999999*.
1. Navigieren Sie zu [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules] und erstellen Sie eine Warenkorb-Preisregel mit den folgenden Bedingungen:

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Installieren von Beispieldaten.
1. Fügen Sie die folgenden Produkte in der angegebenen Reihenfolge zum Warenkorb hinzu:
   * Kuriertasche
   * Olivia 1/4 Reißverschluss leichte Jacke
   * In: Sprite Yoga Companion Kit.
1. Öffnen Sie den Warenkorb und überprüfen Sie, ob die **[!UICONTROL Free Shipping]** verfügbar ist.
1. Klicken Sie auf **[!UICONTROL Check Out with Multiple Addresses]**.
1. Wählen Sie eine andere Lieferadresse für das einfache Produkt aus.
1. Klicken Sie auf **[!UICONTROL Go to Shipping Information]**.

<u>Erwartete Ergebnisse</u>:

**[!UICONTROL Free Shipping]** gilt für konfigurierbare und gebündelte Produktlieferungen.

<u>Tatsächliche Ergebnisse</u>:

**[!UICONTROL Free Shipping]** ist nicht verfügbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
