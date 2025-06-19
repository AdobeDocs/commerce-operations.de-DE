---
title: 'ACSD-50813: Der Administrator kann keine gebündelten Produkte mit einem Schrägstrich hinzufügen'
description: Wenden Sie den Patch ACSD-50813 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem der Administrator bzw. die Administratorin nicht gebündelte Produkte mit einem Schrägstrich (“/„) in der SKU mit der Funktion „Produkte nach SKU hinzufügen“ zur Administratorbestellung hinzufügen kann.
exl-id: ff6fa673-bac1-4ef8-a427-60c2f56068f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-50813: Der Administrator kann keine gebündelten Produkte mit einem Schrägstrich hinzufügen

Der Patch ACSD-50813 behebt das Problem, dass der Administrator gebündelte Produkte mit einem Schrägstrich (`/`) in der SKU mit der *[!UICONTROL Add Products by SKU]* Funktion nicht zur Admin-Bestellung hinzufügen kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID ist ACSD-50813. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator kann keine gebündelten Produkte mit einem Schrägstrich (`/`) in der SKU mit der Funktion &quot;*[!UICONTROL Add Products by SKU]*&quot; zur Admin-Bestellung hinzufügen.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein neues gebündeltes Produkt.
1. Fügen Sie einen Schrägstrich (`/`) in der Mitte der SKU hinzu (Beispiel: *Bu/ndle*).
1. Fügen Sie eine gebündelte Option mit **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]* hinzu.
1. Weisen Sie der Option mindestens ein einfaches Produkt zu.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und erstellen Sie eine neue Bestellung.
1. Klicken Sie auf **[!UICONTROL Add Products by SKU]**.
1. Geben Sie Ihre SKU ein und klicken Sie auf **[!UICONTROL Add to Order]**.
1. Öffnen Sie die Browser-Konsole.
1. Klicken Sie auf **[!UICONTROL Configure]**.

<u>Erwartete Ergebnisse</u>:

Es liegt kein Fehler vor.

<u>Tatsächliche Ergebnisse</u>:

JS-Fehler in der Konsole:

*Nicht erfasster Fehler: Syntaxfehler, nicht erkannter Ausdruck: div[id=sku_bu/ndle]*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
