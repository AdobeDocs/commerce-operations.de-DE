---
title: 'ACSD-47106: Neues benutzerdefiniertes Attribut auf der Seite „Unternehmenserstellung“ nicht gespeichert'
description: Wenden Sie den Patch ACSD-47106 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Unternehmenserstellungsseite gespeichert werden kann.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 5835760d-fca1-44ba-aa5e-8797258c7c75
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47106: Neues benutzerdefiniertes Attribut auf der Seite „Unternehmenserstellung“ nicht gespeichert

Mit dem Patch ACSD-47106 wird das Problem behoben, dass ein Wert auf einer Unternehmenserstellungsseite nicht in einem neuen benutzerdefinierten Attribut gespeichert werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22 installiert ist. Die Patch-ID ist ACSD-47106. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Wert kann nicht in einem neuen benutzerdefinierten Attribut auf einer Unternehmenserstellungsseite gespeichert werden.

<u>Voraussetzungen</u>:

* B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Neues Attribut erstellen: _Test 01_.
1. Gehen Sie zu Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und erstellen Sie eine neue Firma mit allen erforderlichen Details.
1. Versuchen Sie, dem benutzerdefinierten Attribut einen Wert hinzuzufügen _Test 01_.
1. Versuchen Sie, den Wert des benutzerdefinierten Attributs zu aktualisieren _Test 01_.

<u>Erwartete Ergebnisse</u>:

Änderungen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Änderungen werden nicht gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
