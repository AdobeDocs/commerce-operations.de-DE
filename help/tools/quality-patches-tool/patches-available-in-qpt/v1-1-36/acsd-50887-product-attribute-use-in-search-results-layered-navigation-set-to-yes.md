---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* ohne *[!UICONTROL Use in Search]*-Option auf Ja gesetzt'
description: Wenden Sie den Patch ACSD-50887 an, um das Adobe Commerce-Problem zu beheben, bei dem die Produktattribut-Eigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* festgelegt werden kann, ohne dass die Option *[!UICONTROL Use in Search]* auch auf *Ja* festgelegt wird.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* ohne die Option *[!UICONTROL Use in Search]* festgelegt

Der Patch ACSD-50887 behebt das Problem, dass die Produktattribut-Eigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* auf *Ja* gesetzt werden kann, ohne dass die Option *[!UICONTROL Use in Search]* ebenfalls auf *Ja* gesetzt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-50887. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Produktattribut-Eigenschaft *[!UICONTROL Use in Search Results Layered Navigation]* kann auf &quot;*&quot;* werden, ohne dass die Option &quot;*[!UICONTROL Use in Search]*&quot; auch auf &quot;*&quot;*.

Diese Einstellungen wurden für die gemeinsame Verwendung entwickelt. Wenn bei angewendetem Patch die Option *[!UICONTROL Use in Search]* auf *Nein* festgelegt ist, wird die Option *[!UICONTROL Use in Search Results Layered Navigation]* ausgeblendet, sodass sie funktioniert, als ob sie auch auf *Nein* festgelegt wäre.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie in der Admin Console zu **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** und erstellen Sie ein Attribut mit dem Mehrfachauswahl-Typ. Legen Sie dann Folgendes fest:

   * *[!UICONTROL Use in Search]= Nein*
   * *[!UICONTROL Use in Layered Navigation]= (Beliebige Option)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Ja*
   * *Name = test_attribute*
   * *Optionen*:
      * *Aufkleber*
      * *Auswahl*

1. Fügen Sie das neue Attribut zum Standardattributsatz hinzu.
1. Erstellen Sie zwei Produkte:

   1. Erstes Produkt:
      * Name = Aufkleber
      * Preis, Menge, Gewicht auf 1 setzen
      * Test_attribute = Option auswählen *Aufkleber*

   1. Zweites Produkt:
      * Name = Auswahl
      * Preis, Menge, Gewicht auf 1 setzen
      * Test_Attribute = beide Optionen auswählen

1. Neuindizierung `catalogsearch_fulltext`:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Suche mit dem Wort *Aufkleber* in der Storefront.

<u>Erwartete Ergebnisse</u>:

Nur das Produkt *Aufkleber* wird zurückgegeben, da [!DNL Elasticsearch] Testattribut nicht indiziert, wenn *[!UICONTROL Use in Search]* auf &quot;*&quot;*.

<u>Tatsächliche Ergebnisse</u>:

Beide Produkte werden zurückgesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
