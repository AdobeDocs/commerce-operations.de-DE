---
title: "ACSD-47079: Bestandsstatus von zusammengesetzten Erzeugnissen nicht aktualisiert, wenn sich der Lagerstatus der Teilprodukte ändert"
description: Wenden Sie den Patch ACSD-47079 an, um das Adobe Commerce-Problem zu beheben, bei dem der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus von Unterprodukten über die REST-API-POST /rest/V1/inventory/source-items ändert.
feature: Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47079: Bestandsstatus von zusammengesetzten Produkten wird nicht aktualisiert, wenn sich der Lagerstatus von Unterprodukten ändert

Der Patch ACSD-47079 behebt das Problem, dass der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn der Lagerstatus des Unterprodukts über die REST API-POST `/rest/V1/inventory/source-items` geändert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47079. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) wird nicht aktualisiert, wenn der Lagerstatus des Unterprodukts über die REST-API-POST `/rest/V1/inventory/source-items` geändert wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares, gebündeltes und gruppiertes Produkt mit jeweils einem einfachen untergeordneten Produkt.
1. Setzen Sie jeden einfachen untergeordneten Produktstatus mithilfe des API-Aufrufs `source-items` auf **[!UICONTROL Out of Stock]**.
1. Überprüfen Sie nun den Lagerstatus des übergeordneten Produkts.

<u>Erwartete Ergebnisse</u>:

Der Status des übergeordneten Produkts lautet [!UICONTROL Out of Stock].

<u>Tatsächliche Ergebnisse</u>:

Der Status des übergeordneten Produkts lautet [!UICONTROL In Stock].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
