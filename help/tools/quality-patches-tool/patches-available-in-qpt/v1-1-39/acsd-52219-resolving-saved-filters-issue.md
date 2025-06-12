---
title: 'ACSD-52219: Problem beim Filtern von Admin-Rastern beim Umschalten der Lesezeichenansicht beheben'
description: Wenden Sie den Patch ACSD-52219 an, um das Adobe Commerce-Problem zu beheben, bei dem die gespeicherten Filter der Admin-Raster beim häufigen Wechsel zwischen Lesezeichenansichten nicht wie erwartet funktionieren.
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219: Problem beim Filtern von Admin-Rastern beim Umschalten der Lesezeichenansicht beheben

Mit dem Patch ACSD-52219 wird das Problem behoben, dass die gespeicherten Filter der Admin-Raster beim häufigen Wechsel zwischen Lesezeichenansichten nicht wie erwartet funktionieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-52219. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn häufig zwischen Lesezeichenansichten gewechselt wird, funktionieren die gespeicherten Filter in Admin-Rastern nicht wie vorgesehen.

<u>Schritte zur Reproduktion</u>:

1. Rufen Sie das [!DNL Sales Order] im Admin-Bereich auf.
1. Erstellen Sie zwei bis drei Filter.
1. Überprüfen Sie die Filtereinstellungen, indem Sie die Ansichten wechseln, um sicherzustellen, dass sie korrekt gespeichert werden.
1. Navigieren Sie zu Filter1 oder Filter2.
1. Aktualisieren Sie die Seite, um die angezeigten Daten zu aktualisieren.
1. Wechseln Sie zu einer anderen Ansicht und beachten Sie, dass die Filter unverändert bleiben.
1. Beachten Sie, dass in der Standardansicht jetzt gefilterte Ergebnisse angezeigt werden, obwohl dafür kein spezifischer Filter festgelegt wurde.

<u>Erwartete Ergebnisse</u>:

Die Filter werden nicht ausgetauscht und behalten ihren ursprünglichen Zustand.

<u>Tatsächliche Ergebnisse</u>:

Beim Ändern einer Ansicht werden die Filter verwechselt und die korrekte Ansicht wird nicht gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
