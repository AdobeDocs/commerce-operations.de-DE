---
title: 'ACSD-51041: Der Preisindex dauert sehr lange'
description: Wenden Sie den Patch ACSD-51041 an, um das Adobe Commerce-Problem zu beheben, bei dem es lange dauert, bis der Preisindex mit einem sehr großen Produktsatz abgeschlossen ist.
feature: Configuration
role: Admin
exl-id: d45d4042-06a1-445d-bed3-803085626dd3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51041: Der Preisindex dauert sehr lange

Mit dem Patch ACSD-51041 wird das Problem behoben, dass es lange dauert, bis der Preisindex mit einer sehr großen Produktgruppe abgeschlossen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51041. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei einem sehr großen Produktsatz dauert die Fertigstellung des Preisindex sehr lange.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie das *[!UICONTROL Inventory]*.
1. Verfügen über mehrere Lagerquellen (mit einer nicht standardmäßigen Quelle, die den größten Teil des Lagerbestands bereitstellt).
1. Generieren Sie ~200.000 Produkte.
1. Führen Sie einen Inventarindex aus.

<u>Erwartete Ergebnisse</u>:

`deleteIndexData` verarbeitet nur die eindeutigen IDs, um die Leistung zu optimieren.

<u>Tatsächliche Ergebnisse</u>:

`deleteIndexData` verarbeitet alle IDs, was viel Zeit in Anspruch nimmt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
