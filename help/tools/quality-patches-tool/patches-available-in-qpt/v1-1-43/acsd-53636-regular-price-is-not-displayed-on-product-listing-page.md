---
title: "ACSD-53636: Der reguläre Preis wird nicht auf der Seite [!UICONTROL Product Listing] angezeigt."
description: Wenden Sie den Patch ACSD-53636 an, um das Adobe Commerce-Problem zu beheben, bei dem der reguläre Preis auf *[!UICONTROL Product Listing]*-Seiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen nicht angezeigt wird.
feature: Catalog Management, Products
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: Der reguläre Preis wird nicht auf der Seite *[!UICONTROL Product Listing]* angezeigt

Der Patch ACSD-53636 behebt das Problem, dass der reguläre Preis nicht auf *[!UICONTROL Product Listing]* Seiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-53636. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der reguläre Preis wird nicht auf *[!UICONTROL Product Listing]* -Seiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an, navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** und erstellen oder öffnen Sie ein konfigurierbares Produkt.
2. Öffnen Sie das untergeordnete Produkt, fügen Sie allen oder einem der untergeordneten Produkte einen Sonderpreis hinzu und speichern Sie das Produkt.
3. Gehen Sie zur Frontend-Seite und öffnen Sie die Seite &quot;**[!UICONTROL Product Detail]**&quot; des konfigurierbaren Produkts. Auf den Farbfeldern des untergeordneten Produkts mit Sonderpreis sehen Sie, dass der *[!UICONTROL Regular price]* ausgestoßen ist (erwartet).
4. Gehen Sie zum Frontend und öffnen Sie die Seite &quot;**[!UICONTROL Product Listing]**&quot; für das konfigurierbare Produkt mit einem Sonderpreis. Beachten Sie, dass die konfigurierbaren Änderungen am Produktmuster im Gegensatz zu *[!UICONTROL Product Detail Page]* und anderen einfachen Produkten nicht den regulären Preis anzeigen.

<u>Erwartete Ergebnisse</u>:

Auf der Seite *[!UICONTROL Product Listing]* zeigt das konfigurierbare Produkt den regulären Preis für das untergeordnete Produkt an.

<u>Tatsächliche Ergebnisse</u>:

Auf der Seite *[!UICONTROL Product Listing]* zeigt das konfigurierbare Produkt nicht den regulären Preis für das untergeordnete Produkt an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
