---
title: 'ACP2E-3918: Checkout-Fehler für Firmenkunden, die die Abholung im Geschäft verwenden'
description: Wenden Sie den ACP2E-3918-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der Checkout für angemeldete Firmenkunden, die eine Abholung im Geschäft ohne standardmäßige Rechnungsadresse verwenden, fehlschlägt.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACP2E-3918: Checkout-Fehler für Firmenkunden, die die Abholung im Geschäft verwenden

Mit dem Patch ACP2E-3918 wird das Problem behoben, dass der Checkout für angemeldete Firmenkunden, die eine Abholung im Geschäft ohne standardmäßige Rechnungsadresse verwenden, fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID lautet ACP2E-3918. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Checkout schlägt fehl, wenn ein angemeldeter Firmenkunde ohne Standardadresse versucht, mit der Abholung im Geschäft eine Bestellung aufzugeben.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL Purchase Orders]** aktivieren.
1. Erstellen Sie eine **[!UICONTROL Company]** und aktivieren Sie **[!UICONTROL Purchase Orders]** dafür.
1. Erstellen Sie eine **[!UICONTROL Company User]** ohne gespeicherte Adressen.
1. Aktivieren Sie die **[!UICONTROL In-Store Delivery]** Versandmethode.
1. Fügen Sie eine Inventarquelle hinzu.
1. Hinzufügen eines Lagerbestands.
1. Weisen Sie einem Produkt Inventar zu.
1. Melden Sie sich am Frontend als Unternehmensbenutzer an.
1. Hinzufügen von Produkten zu **[!UICONTROL Cart]**.
1. Zur Kasse gehen.
1. Wählen Sie beim Versandschritt **[!UICONTROL In-Store Pick Up]** aus.
1. Zahlung ausführen.

<u>Erwartete Ergebnisse</u>:

Der Zahlungsschritt sollte beim Checkout erfolgreich geladen werden und in der Browser-Konsole sollten keine Fehler angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Der Zahlungsschritt wird nicht geladen und die Browser-Konsole zeigt den folgenden JavaScript-Fehler an:

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
