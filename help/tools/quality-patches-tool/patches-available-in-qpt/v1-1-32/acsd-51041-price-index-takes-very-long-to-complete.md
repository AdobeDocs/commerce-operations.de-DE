---
title: 'ACSD-51041: Der Preisindex dauert sehr lange, bis er abgeschlossen ist'
description: Wenden Sie den Patch ACSD-51041 an, um das Adobe Commerce-Problem zu beheben, bei dem der Preisindex lange dauert, bis er mit einem sehr großen Produktset abgeschlossen ist.
feature: Configuration
role: Admin
exl-id: d45d4042-06a1-445d-bed3-803085626dd3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51041: Der Preisindex dauert sehr lange, bis er abgeschlossen ist

Der Patch ACSD-51041 behebt das Problem, bei dem der Preisindex lange dauert, bis er mit einem sehr großen Produktset fertig ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51041. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei einem sehr großen Produktsatz dauert es sehr lange, bis der Preisindex abgeschlossen ist.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie das Modul *[!UICONTROL Inventory]* .
1. Sie verfügen über mehrere Stammquellen (mit einer nicht standardmäßigen Quelle, die den Großteil des Bestands bereitstellt).
1. Generieren Sie ca. 200.000 Produkte.
1. Führen Sie einen Inventarindex aus.

<u>Erwartete Ergebnisse</u>:

`deleteIndexData` verarbeitet nur die eindeutigen IDs zur Leistungsoptimierung.

<u>Tatsächliche Ergebnisse</u>:

`deleteIndexData` verarbeitet alle IDs, was lange dauert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
