---
title: 'ACSD-49370: Das Produktattribut hat den Typ „FilterMatchTypeInput“ im GraphQL-Schema'
description: Wenden Sie den Patch ACSD-49370 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produktattribut im GraphQL-Schema den Typ „FilterMatchTypeInput“ aufweist.
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
exl-id: 05cc6db6-6ea6-4eb7-8dc0-fcb9f479fd89
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-49370: Das Produktattribut hat `FilterMatchTypeInput` Typ im GraphQL-Schema

Mit dem Patch ACSD-49370 wird das Problem behoben, dass das Produktattribut im GraphQL-Schema einen `FilterMatchTypeInput` aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49370. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Produktattribut hat im GraphQL-Schema einen `FilterMatchTypeInput`.

<u>Schritte zur Reproduktion</u>:

1. Erstellen *Produktattributs* Datum und Uhrzeit“.

   * [!UICONTROL Type]: [!UICONTROL DateTime]
   * [!UICONTROL Default Label]: [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]: [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]: [!UICONTROL Yes]

1. Fragen Sie in der *GQL API*-Dokumentation nach der `ProductAttributeFilterInput` ab.
1. Beobachten Sie den Eingabetyp für das erstellte Attribut.

<u>Erwartete Ergebnisse</u>:

Das *Datum/Uhrzeit*-Attribut zeigt den `FilterRangeTypeInput` des Filtereingabetyps an.

<u>Tatsächliche Ergebnisse</u>:

Das *Datum/Uhrzeit*-Attribut zeigt den `FilterMatchInputType` des Filtereingabetyps an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
