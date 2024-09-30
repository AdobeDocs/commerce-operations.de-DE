---
title: 'ACSD-48234: Katalogsuchergebnis: falsche Kategorieelementanzahl, wenn [!UICONTROL Display Out of Stock Products] aktiviert ist'
description: Wenden Sie den Patch ACSD-48234 an, um das Adobe Commerce-Problem zu beheben, bei dem das Katalogsuchergebnis eine falsche Kategorieelementanzahl anzeigt, wenn die Option [!UICONTROL Display Out of Stock Products] aktiviert ist.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234: Katalogsuchergebnis zeigt falsche Kategorieelementanzahl **[!UICONTROL Display Out of Stock Products]** aktiviert

Der Patch ACSD-48234 behebt das Problem, dass das Katalogsuchergebnis eine falsche Kategorieelementanzahl anzeigt, wenn die Option **[!UICONTROL Display Out of Stock Products]** aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID lautet ACSD-48234. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Suchergebnis im Katalog zeigt eine falsche Anzahl von Kategorieelementen an, wenn die Option **[!UICONTROL Display Out of Stock Products]** aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und öffnen Sie das Attribut **[!UICONTROL color]** .
1. Fügen Sie zwei Optionen hinzu, z. B. orange und grün. Speichern Sie das Attribut.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** und fügen Sie das Attribut **[!UICONTROL color]** zum Attributsatz **[!UICONTROL Default]** hinzu.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** und legen Sie **[!UICONTROL Display Out of Stock Products]** auf _Ja_ fest.
1. Kategorie &quot;cat1&quot;erstellen.
1. Erstellen Sie zwei Produkte:
   1. Name: prod1, Farbe: orange, Kategorien: cat1.
   1. Name: prod2, Farbe: grün, Kategorien: cat1.
1. Öffnen Sie die Kategorie &quot;cat1&quot;auf der Storefront.
1. Wählen Sie die orangefarbene Farbe in der Navigationsschicht aus.

<u>Erwartete Ergebnisse</u>:

Es wird nur das Produkt prod1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es werden sowohl die Produkte prod1 als auch prod2 angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
