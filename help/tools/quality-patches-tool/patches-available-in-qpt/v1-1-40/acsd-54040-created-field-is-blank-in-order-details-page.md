---
title: 'ACSD-54040: Das Feld [!UICONTROL Created] ist leer, wenn B2B-Module aktiviert sind, in der Reihenfolge der Details'
description: Wenden Sie den ACSD-54040-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Feld [!UICONTROL Created] auf der Seite mit den Bestelldetails leer ist, wenn B2B-Module aktiviert sind.
feature: B2B
role: Admin, Developer
exl-id: 09fc1e0f-2e02-4cfc-9a7a-7c6aacd9fee0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040: *[!UICONTROL Created]* Feld ist leer, wenn B2B-Module aktiviert sind.

Mit dem Patch ACSD-54040 wird das Problem behoben, dass das Feld *[!UICONTROL Created]* auf der Seite mit den Bestelldetails leer bleibt, wenn B2B-Module aktiviert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54040. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn B2B-Module aktiviert sind, bleibt das Feld *[!UICONTROL Created]* auf der Seite mit den Bestelldetails leer.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce mit dem B2B-Modul.
1. Erstellen Sie einen neuen Kunden und geben Sie eine Bestellung auf.
1. Gehen Sie zu den Bestelldetails im Frontend und überprüfen Sie das Feld *[!UICONTROL Created]* .

<u>Erwartete Ergebnisse</u>:

Das Feld *[!UICONTROL Created]* zeigt das Datum an, an dem die Bestellung erstellt wurde.

<u>Tatsächliche Ergebnisse</u>:

Das Feld *[!UICONTROL Created]* ist leer

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
