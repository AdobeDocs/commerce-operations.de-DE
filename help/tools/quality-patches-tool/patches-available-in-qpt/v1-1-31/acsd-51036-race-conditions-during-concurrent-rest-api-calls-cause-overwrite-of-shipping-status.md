---
title: 'ACSD-51036: Wettbewerbsbedingungen während gleichzeitiger REST-API-Aufrufe führen zu einer Überschreibungen des Versandstatus'
description: Wenden Sie den Patch ACSD-51036 an, um das Adobe Commerce-Problem zu beheben, bei dem es während gleichzeitiger REST-API-Aufrufe zu Race-Bedingungen kommt, die zu einer Überschreibung des Versandstatus in der Tabelle mit den bestellten Artikeln führen.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036: Wettbewerbsbedingungen während gleichzeitiger REST-API-Aufrufe führen zu einer Überschreibungen des Versandstatus in der Tabelle mit den bestellten Artikeln

Der Patch ACSD-51036 behebt das Problem, dass die Race-Bedingungen während gleichzeitiger REST-API-Aufrufe zu einer Überschreibungen des Versandstatus in der Tabelle mit den bestellten Artikeln führen. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID ist ACSD-51036. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Race-Bedingungen während gleichzeitiger REST-API-Aufrufe führen zu einer Überschreibung des Versandstatus in der Tabelle „Artikel bestellt“.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit zwei Artikeln.
1. Rechnungsposition A.
1. Senden Sie gleichzeitig eine Erstattungsanfrage für den Artikel A über die REST-API, während Sie eine Versandanfrage für den Artikel B senden.
1. Gehen Sie zur Bestellung in **[!UICONTROL Admin Panel]**.

<u>Erwartete Ergebnisse</u>

*[!UICONTROL Shipped 1]* Status sollte für Element B in der Tabelle mit der *[!UICONTROL Items]* Reihenfolge vorhanden sein.

<u>Tatsächliche Ergebnisse</u>

*[!UICONTROL Shipped 1]* Status ist für Element B in der *[!UICONTROL Items]* Tabelle nicht vorhanden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
