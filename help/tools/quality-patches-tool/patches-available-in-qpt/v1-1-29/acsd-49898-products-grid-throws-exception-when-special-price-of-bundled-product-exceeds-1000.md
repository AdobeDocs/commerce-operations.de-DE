---
title: "ACSD-49898: Das Produktraster gibt eine Ausnahme aus."
description: Wenden Sie den Patch ACSD-49898 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produktnetz eine Ausnahme auslöst, wenn ein gebündeltes Produkt einen Sonderpreis von mehr als 1000 aufweist.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: Das Produkt-Raster gibt eine Ausnahme aus

Der Patch ACSD-49898 behebt das Problem, dass das Produktnetz eine Ausnahme auslöst, wenn ein gebündeltes Produkt einen Sonderpreis von über 1000 aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49898. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produktnetz gibt eine Ausnahme aus, wenn ein gebündeltes Produkt einen Sonderpreis von mehr als 1000 aufweist. Das Problem betrifft die Verwendung von Kommas anstelle von Punkten für Dezimalzahlen in bestimmten Gebietsschemata.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein gebündeltes Produkt.
1. Setzen Sie den Sonderpreis auf 9999; sparen und schließen Sie.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .

>[!NOTE]
>
>Suchen Sie nach gebündelter Produkt-SKU, wenn sie nicht sichtbar ist.

<u>Erwartete Ergebnisse</u>:

* Der Benutzer kann das gebündelte Produkt mit dem Sonderpreis filtern/anzeigen.
* Der Sonderpreis wird als Prozentsatz für gebündelte Produkte und als Preis für andere Produktarten angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird ausgegeben: *Nicht-numerischer Wert gefunden*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
