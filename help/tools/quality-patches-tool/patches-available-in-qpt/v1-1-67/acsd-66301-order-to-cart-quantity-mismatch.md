---
title: 'ACSD-66301: Die Verschiebung von Produkten aus einer Bestellung in den Warenkorb in Commerce Admin führt zu einer Mengenabweichung'
description: Wenden Sie den Patch ACSD-66301 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Erstellen einer Bestellung über das Admin-Bedienfeld die Produkte im Warenkorb des Kunden nicht entfernt werden, nachdem sie zur Bestellung hinzugefügt wurden.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
source-git-commit: 1e56c38713344b117ca3882861ced35e602b3239
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-66301: Wenn Sie Produkte aus einer Bestellung zurück in den Warenkorb in der Commerce Admin verschieben, führt dies zu einer Mengenabweichung

Mit dem Patch ACSD-66301 wird das Problem behoben, dass die Verschiebung von Produkten von einer Bestellung zurück in den Warenkorb im Admin-Bereich zu einer Mengenabweichung führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66301. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p10, 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie Produkte aus einer Bestellung zurück in den Warenkorb in der Commerce Admin verschieben, führt dies zu einer Mengenabweichung.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Benutzer über die Storefront.
2. Fügen Sie dem Warenkorb ein Produkt mit der Menge = *5* hinzu.
3. Gehen Sie zum Admin-Bedienfeld und öffnen Sie das Benutzerkonto, dem das Produkt hinzugefügt wurde.
4. Klicken Sie auf **[!UICONTROL Create Order]**.
5. Im linken Bedienfeld können Sie die Aktivitäten des Kunden anzeigen, einschließlich des hinzugefügten Produkts und der hinzugefügten Menge.
6. Fügen Sie das Produkt zur Bestellung hinzu.
7. Aktualisieren Sie die Menge = *4* im Hauptauftragsabschnitt.
8. Klicken Sie auf **[!UICONTROL Update Items and Quantities]** Schaltfläche.
9. Übertragen Sie die ausgewählten Artikel aus der Bestellung zurück in den Warenkorb des Kunden.

<u>Erwartete Ergebnisse</u>:

Produkt zum Warenkorb hinzugefügt mit der neuen Menge = *4*.

<u>Tatsächliche Ergebnisse</u>:

Produkt zum Warenkorb hinzugefügt mit der alten Menge = *5*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
