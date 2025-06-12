---
title: 'ACSD-53176: Produktregel mit der Bedingung „ist eine von“ stimmt nicht überein'
description: Wenden Sie den Patch ACSD-53176 an, um das Adobe Commerce-Problem zu beheben, bei dem die zugehörige Produktregel „is one of“-Bedingung für „Übereinstimmende Produkte“ nicht korrekt funktioniert.
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176: Produktregel mit `is one of` Bedingung stimmt nicht überein

Mit dem Patch ACSD-53176 wird das Problem behoben, dass die zugehörige Produktregel-`is one of`-Bedingung für nicht korrekt funktioniert **Übereinstimmende Produkte**. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-53176. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `is one of` für die zugehörige Produktregel funktioniert für nicht ordnungsgemäß **Übereinstimmende Produkte**.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie 3-4 Produkte.
1. Erstellen Sie eine neue zugehörige Produktregel.

   Legen Sie die Regel so fest, dass sie zwei oder mehr Produkten entspricht:
   * `SKU is one of "S1,S2".`

   Legen Sie die Regel so fest, dass zwei oder mehr Elemente angezeigt werden:
   * `Product SKU is one of constant value "S2,S3".`

1. Öffnen Sie das S1-Produkt in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die zugehörigen Produkte „S2“ und „S3“ werden auf den Produktseiten „S1“ und „S2“ angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Verwandte Produkte werden nicht auf den Produktseiten angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
