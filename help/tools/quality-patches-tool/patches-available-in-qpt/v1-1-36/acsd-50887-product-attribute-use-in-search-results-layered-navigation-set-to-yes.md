---
title: '"ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* ohne die *[!UICONTROL Use in Search]*-Option auf "Ja" gesetzt'
description: Wenden Sie den Patch ACSD-50887 an, um das Adobe Commerce-Problem zu beheben, bei dem die Produktattributeigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* gesetzt werden kann, ohne dass die *[!UICONTROL Use in Search]*-Option ebenfalls auf *Ja* gesetzt wird.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* ohne die Option *[!UICONTROL Use in Search]* auf *Ja* gesetzt

Der Patch ACSD-50887 behebt das Problem, dass die Produktattributeigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* gesetzt werden kann, ohne dass die Option *[!UICONTROL Use in Search]* ebenfalls auf *Ja* gesetzt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-50887. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Produktattributeigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* kann auf *Ja* gesetzt werden, ohne dass die Option *[!UICONTROL Use in Search]* ebenfalls auf *Ja* gesetzt ist.

Diese Einstellungen wurden für die gemeinsame Verwendung entwickelt. Wenn der Patch angewendet wird und die Option *[!UICONTROL Use in Search]* auf *Nein* gesetzt ist, wird die Option *[!UICONTROL Use in Search Results Layered Navigation]* ausgeblendet, um so zu funktionieren, als wäre sie auch auf *Nein* gesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie im Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]**, erstellen Sie ein Attribut mit dem Mehrfachauswahltyp und legen Sie Folgendes fest:

   * *[!UICONTROL Use in Search]= Nein*
   * *[!UICONTROL Use in Layered Navigation]= (Beliebige Option)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Ja*
   * *Name = Test_attribute*
   * *Options*:
      * *Aufkleber*
      * *Picker*

1. Fügen Sie dem standardmäßigen Attributsatz das neue Attribut hinzu.
1. Erstellen Sie zwei Produkte:

   1. Erstes Produkt:
      * Name = Aufkleber
      * Legen Sie Preis, QTY, Gewichtung auf 1 fest.
      * Test_attribute = Auswahloption *Aufkleber*

   1. Zweites Produkt:
      * Name = Picker
      * Legen Sie Preis, QTY, Gewichtung auf 1 fest.
      * Test_attribute = beide Optionen auswählen

1. Führen Sie `catalogsearch_fulltext` reindex aus:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Suchen Sie nach dem Wort *Aufkleber* auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Nur das Produkt *Sticker* wird zurückgegeben, da [!DNL Elasticsearch] das Attribut &quot;Test_attribute&quot;nicht indiziert, wenn *[!UICONTROL Use in Search]* auf *Nein* gesetzt wurde.

<u>Tatsächliche Ergebnisse</u>:

Beide Produkte werden zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
