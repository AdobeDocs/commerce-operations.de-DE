---
title: 'MDVA-40545: Nur der erste Knoten für eine Seite wird abgerufen'
description: Mit dem Patch MDVA-40545 wird das Problem behoben, dass nur der erste Knoten für eine Seite abgerufen wird, selbst wenn für dieselbe Seite mehr als ein Knoten vorhanden ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-40545. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: CMS, Cache
role: Admin
exl-id: f87344e9-5a63-4c38-af2b-1500ef053dec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-40545: Nur der erste Knoten für eine Seite wird abgerufen

Mit dem Patch MDVA-40545 wird das Problem behoben, dass nur der erste Knoten für eine Seite abgerufen wird, selbst wenn für dieselbe Seite mehr als ein Knoten vorhanden ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-40545. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es wird nur der erste Knoten für eine Seite abgerufen, selbst wenn für dieselbe Seite mehr als ein Knoten vorhanden ist.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie im Admin-Bedienfeld zu **Hierarchie** und fügen Sie zwei Menüelemente/Knoten hinzu.
1. Fügen Sie jedem Knoten dieselbe CMS-Seite hinzu.
1. Löschen Sie den Cache und überprüfen Sie das Frontend.
1. Überprüfen Sie den Link und die Breadcrumbs für das erste hinzugefügte Untermenü.
1. Überprüfen Sie den Link und die Breadcrumbs für das zweite hinzugefügte Untermenü.

<u>Erwartete Ergebnisse</u>:

Breadcrumbs und Links im zweiten Untermenü sind für den zweiten Knoten relevant.

<u>Tatsächliche Ergebnisse</u>:

Breadcrumbs und Links im zweiten Untermenü sind mit dem ersten Untermenü identisch.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
