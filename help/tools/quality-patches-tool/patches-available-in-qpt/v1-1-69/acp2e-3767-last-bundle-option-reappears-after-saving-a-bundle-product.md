---
title: 'ACP2E-3767: Option „Letztes Bundle“ wird nach dem Speichern eines Bundle-Produkts erneut angezeigt'
description: Wenden Sie den ACP2E-3767-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die letzte Bundle-Option in einem Bundle-Produkt nicht entfernt werden konnte.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767: Option „Letztes Bundle“ wird nach dem Speichern eines Bundle-Produkts erneut angezeigt

Mit dem Patch ACP2E-3767 wird das Problem behoben, dass die letzte Bundle-Option nach dem Speichern des Bundle-Produkts erneut angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID lautet ACP2E-3767. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die letzte Bundle-Option in einem Bundle-Produkt kann nicht entfernt werden.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Wählen Sie **[!UICONTROL Simple Product]** aus dem Dropdown-Menü aus.
1. Erforderliche Daten eingeben und speichern.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Wählen Sie **[!UICONTROL Bundle Product]** aus dem Dropdown-Menü aus.
1. Erforderliche Daten eingeben.
1. Klicken Sie unter „Bundle-Elemente“ auf **[!UICONTROL Add Option]**.
1. Fügen Sie der neuen Option einen Titel hinzu und klicken Sie dann auf **[!UICONTROL Add Products to Option]**.
1. Wählen Sie das zuvor erstellte einfache Produkt und dann **[!UICONTROL Add Selected Products]** aus.
1. Paket-Produkt speichern.
1. Entfernen Sie die Bundle-Option und speichern Sie sie.

<u>Erwartete Ergebnisse</u>:

1. Die Bundle-Option wurde erfolgreich entfernt.
1. Wenn das Entfernen nicht zulässig ist, wird eine Meldung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

1. Die Bundle-Option bleibt aktiv.
1. Es wird kein Fehler oder keine Benachrichtigung angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
