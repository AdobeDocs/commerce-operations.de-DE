---
title: 'ACSD-51497: Katalogseite kann nicht nach benutzerdefiniertem Attribut des Typs Dropdown sortiert werden'
description: Wenden Sie den Patch ACSD-51497 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kunde eine Katalogseite nicht nach benutzerdefinierten Attributen des Typs Dropdown sortieren kann.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497: Katalogseite kann nicht nach benutzerdefiniertem Attribut vom Typ (*) sortiert*

Mit dem Patch ACSD-51497 wird das Problem behoben, dass ein Kunde eine Katalogseite nicht nach einem benutzerdefinierten Attribut des Typs *Dropdown“* kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51497. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Kundin oder ein Kunde kann eine Katalogseite nicht nach einem benutzerdefinierten Attribut des Typs *Dropdown“*.

<u>Schritte zur Reproduktion</u>

1. Erstellen Sie etwa sechs einfache Produkte und weisen Sie sie einer einzelnen Kategorie zu.
1. Erstellen Sie ein Produktattribut, um es als Sortieroption zu den Auflistungsseiten hinzuzufügen.

   * Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Legen Sie auf der Registerkarte **[!UICONTROL Properties]** Folgendes fest:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* für Store-Inhaber = *Dropdown*
      * *[!UICONTROL Options]*:

         * *first*
         * *Sekunde*
         * *3*
         * *4*

   * Legen Sie auf der Registerkarte **[!UICONTROL Storefront Properties]** Folgendes fest:

      * *[!UICONTROL Used for sorting in product listing]* = *Ja*
      * Belassen Sie alle anderen Optionen auf *Standard*.

1. Weisen Sie das *test*-Attribut dem *Standard*-Attribut zu, das in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** festgelegt ist.
1. Konfigurieren Sie die Produkte so, *sie (Test*-Attributwerte aufweisen.

   * SKU: s00001, Test: 4.
   * SKU: s00002, Test: dritter
   * SKU: s00003, Test: Sekunde
   * SKU: s00004, Test: zuerst
   * SKU: s00005, Test: 4.
   * SKU: s00006, Test: dritter

1. Neuindizieren und Cache löschen.
1. Zur Kategorie in der Storefront gehen.
1. Sortieren Sie nach dem *test*-Attribut.

<u>Erwartete Ergebnisse</u>:

Die Produkte werden nach dem Attribut *test* sortiert.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht nach dem Attribut *test* sortiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
