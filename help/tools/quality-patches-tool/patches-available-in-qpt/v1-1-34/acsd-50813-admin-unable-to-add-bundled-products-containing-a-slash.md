---
title: 'ACSD-50813: Administrator kann gebündelte Produkte, die einen Schrägstrich enthalten, nicht hinzufügen'
description: Wenden Sie den Patch ACSD-50813 an, um das Adobe Commerce-Leistungsproblem zu beheben, bei dem der Administrator keine gebündelten Produkte mit einem Schrägstrich ("/") in der SKU hinzufügen kann, wobei die Funktion *Produkte nach SKU hinzufügen* der Administratorreihenfolge hinzugefügt wird.
exl-id: ff6fa673-bac1-4ef8-a427-60c2f56068f3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-50813: Administrator kann gebündelte Produkte, die einen Schrägstrich enthalten, nicht hinzufügen

Der Patch ACSD-50813 behebt das Problem, dass der Administrator keine gebündelten Produkte mit einem Schrägstrich (`/`) in der SKU mit der Funktion *[!UICONTROL Add Products by SKU]* zur Administratorreihenfolge hinzufügen kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID lautet ACSD-50813. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator kann der SKU keine gebündelten Produkte hinzufügen, die ein Schrägstrich (`/`) mit der Funktion *[!UICONTROL Add Products by SKU]* enthalten, und die Administratorreihenfolge kann nicht mit der Funktion versehen werden.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein neues gebündeltes Produkt.
1. Fügen Sie ein Schrägstrich (`/`) in der Mitte der SKU hinzu (Beispiel: *Bu/ndle*).
1. Fügen Sie eine gebündelte Option mit **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]* hinzu.
1. Weisen Sie der Option mindestens ein einfaches Produkt zu.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und erstellen Sie eine neue Bestellung.
1. Klicken Sie auf **[!UICONTROL Add Products by SKU]**.
1. Geben Sie Ihre SKU ein und klicken Sie auf **[!UICONTROL Add to Order]**.
1. Öffnen Sie die Browser-Konsole.
1. Klicken Sie auf **[!UICONTROL Configure]**.

<u>Erwartete Ergebnisse</u>:

Es gibt keinen Fehler.

<u>Tatsächliche Ergebnisse</u>:

JS-Fehler in der Konsole:

*Uncaught Error: Syntaxfehler, nicht erkannter Ausdruck: div[id=sku_bu/ndle]*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
