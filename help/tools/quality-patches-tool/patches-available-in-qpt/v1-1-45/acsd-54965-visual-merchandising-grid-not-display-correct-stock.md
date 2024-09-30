---
title: "ACSD-54965: [!UICONTROL Visual Merchandising] grid does not display the richtige stock"
description: Wenden Sie den Patch ACSD-54965 an, um das Adobe Commerce-Problem zu beheben, bei dem das Raster "[!UICONTROL Visual Merchandising]"nicht das richtige Lager anzeigt, wenn ein Produkt einem benutzerdefinierten Lager zugewiesen ist.
feature: Merchandising, Categories
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht das richtige Lager an

Der Patch ACSD-54965 behebt das Problem, dass das Raster [!UICONTROL Visual Merchandising] nicht das richtige Lager anzeigt, wenn ein Produkt einem benutzerdefinierten Lager zugewiesen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-54965. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Raster [!UICONTROL Visual Merchandising] zeigt nicht das richtige Lager an, wenn ein Produkt einem benutzerdefinierten Lager zugewiesen wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager.
1. Erstellen Sie zwei Produkte:
   * Ein Produkt mit benutzerdefiniertem Lager.
   * Ein Produkt, das nur den Standardbestand aufweist.
1. Fügen Sie diese Produkte einer Kategorie hinzu.
1. Wechseln Sie zum Raster [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Tatsächliche Ergebnisse</u>:

In den *[!UICONTROL All Store Views]* -Bereichen zeigt das Produkt mit benutzerdefiniertem Lager keine Menge an. Erst wenn der Bereich *[!UICONTROL Default Store View]* ausgewählt ist, zeigt das benutzerdefinierte Lager die Menge des Produkts an.

<u>Erwartete Ergebnisse</u>:

Das Raster zeigt alle Lagerinformationen an, wenn der Umfang *[!UICONTROL All Store Views]* beträgt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
