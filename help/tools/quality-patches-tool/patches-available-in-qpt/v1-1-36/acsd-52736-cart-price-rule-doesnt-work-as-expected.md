---
title: 'ACSD-52736: [!UICONTROL Cart Price Rule] funktioniert nicht erwartungsgemäß'
description: Wenden Sie den Patch ACSD-52736 an, um das Adobe Commerce-Problem zu beheben, bei dem ein [!UICONTROL Cart Price Rule], das die Anforderungen für konfigurierbare Produktmengen enthält, nicht wie erwartet funktioniert.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 80c3b14e-62ce-4cfc-b1ff-968e70e3a6f8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-52736: [!UICONTROL Cart Price Rule] funktioniert nicht erwartungsgemäß

Mit dem Patch ACSD-52736 wird das Problem behoben, dass eine [!UICONTROL Cart Price Rule], die die Anforderungen für konfigurierbare Produktmengen enthält, nicht wie erwartet funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.36 installiert ist. Die Patch-ID ist ACSD-52736. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine [!UICONTROL Cart Price Rule], die die Anforderungen an eine konfigurierbare Produktmenge enthält, funktioniert nicht wie erwartet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Warenkorbregel:
   * [!UICONTROL Apply] = Prozentsatz des Produktpreisrabatts
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Wenden Sie die Regel nur auf die Artikel im Warenkorb an, die den folgenden Bedingungen entsprechen: Die Menge im Warenkorb ist 1
2. Fügen Sie ein Produkt mit [!UICONTROL Qty] = 2 in den Warenkorb.
3. Überprüfen Sie die Warenkorbpreise.

<u>Erwartete Ergebnisse</u>:

Die Regel wird nicht angewendet, da die Menge der Produkte im Warenkorb *2%*.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird angewendet.

<u> Weitere Schritte, die nach der Patch-Installation erforderlich sind</u>:

Nach dem Anwenden des Patches müssen die Warenkorbregelbedingungen mit dem *Quantity*-Attribut entfernt und erneut hinzugefügt werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
