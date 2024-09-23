---
title: 'ACSD-51497: Katalogseite kann nicht nach benutzerdefiniertem Attribut des Typs Dropdown sortiert werden.'
description: Wenden Sie den Patch ACSD-51497 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kunde eine Katalogseite nicht nach einem benutzerdefinierten Attribut des Typs Dropdown sortieren kann.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: Katalogseite kann nicht nach benutzerdefiniertem Attribut des Typs *Dropdown* sortiert werden

Der Patch ACSD-51497 behebt das Problem, dass ein Kunde eine Katalogseite nicht mit einem benutzerdefinierten Attribut vom Typ *Dropdown* sortieren kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51497. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Kunde kann eine Katalogseite nicht nach einem benutzerdefinierten Attribut vom Typ *Dropdown* sortieren.

<u>Zu reproduzierende Schritte</u>

1. Erstellen Sie etwa sechs einfache Produkte und weisen Sie sie einer Kategorie zu.
1. Erstellen Sie ein Produktattribut, um es als Sortieroption auf den Listenseiten hinzuzufügen.

   * Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Legen Sie auf der Registerkarte **[!UICONTROL Properties]** Folgendes fest:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* für Store Owner = *Dropdown*
      * *[!UICONTROL Options]*:

         * *first*
         * *second*
         * *third*
         * *vierte*

   * Legen Sie auf der Registerkarte **[!UICONTROL Storefront Properties]** Folgendes fest:

      * *[!UICONTROL Used for sorting in product listing]* = *Ja*
      * Belassen Sie alle anderen Optionen als *Standard*.

1. Weisen Sie das Attribut *test* dem Attribut *Default* zu, das in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** festgelegt ist.
1. Konfigurieren Sie die Produkte so, dass sie *test* -Attributwerte aufweisen.

   * SKU: s00001, Test: vierte
   * SKU: s00002, Test: dritte
   * SKU: s00003, Test: Sekunde
   * SKU: s00004, test: first
   * SKU: s00005, Test: vierte
   * SKU: s00006, Test: dritte

1. Neuindizieren und leeren Sie den Cache.
1. Gehen Sie zur Kategorie in der Storefront.
1. Sortieren Sie nach dem Attribut *test* .

<u>Erwartete Ergebnisse</u>:

Die Produkte werden nach dem Attribut *test* sortiert.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht nach dem Attribut *test* sortiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
