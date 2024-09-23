---
title: "ACSD-52219: Beheben des Problems mit dem Administrator-Raster-Filter beim Wechseln der Lesezeichenansicht"
description: Wenden Sie den Patch ACSD-52219 an, um das Adobe Commerce-Problem zu beheben, bei dem die gespeicherten Filter der Admin-Raster nicht wie erwartet funktionieren, wenn häufig zwischen Lesezeichenansichten gewechselt wird.
feature: Admin Workspace
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: Problem mit Admin-Raster-Filtern beim Wechseln der Lesezeichenansicht behoben

Der Patch ACSD-52219 behebt das Problem, dass die gespeicherten Filter der Admin-Raster beim häufigen Wechseln zwischen Lesezeichenansichten nicht wie erwartet funktionieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-52219. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn häufig zwischen Lesezeichenansichten gewechselt wird, funktionieren die gespeicherten Filter in den Admin Rastern nicht wie gewünscht.

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie das Raster [!DNL Sales Order] im Admin auf.
1. Erstellen Sie zwei bis drei Filter.
1. Überprüfen Sie die Filtereinstellungen, indem Sie die Ansichten wechseln, um sicherzustellen, dass sie korrekt gespeichert werden.
1. Navigieren Sie zu Filter1 oder Filter2.
1. Aktualisieren Sie die Seite, um die angezeigten Daten zu aktualisieren.
1. Wechseln Sie zu einer anderen Ansicht und beachten Sie, dass die Filter unverändert bleiben.
1. Beachten Sie, dass in der Standardansicht jetzt gefilterte Ergebnisse angezeigt werden, auch wenn kein spezifischer Filter dafür festgelegt wurde.

<u>Erwartete Ergebnisse</u>:

Die Filter werden nicht verändert und behalten ihren ursprünglichen Status bei.

<u>Tatsächliche Ergebnisse</u>:

Beim Ändern einer Ansicht werden die Filter vermischt und die richtige Ansicht wird nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
