---
title: 'ACSD-54890: `aggregate_sales_report_bestsellers_data` verursacht [!DNL MySQL] Fehler'
description: Wenden Sie den Patch ACSD-54890 an, um das Adobe Commerce-Problem zu beheben, bei dem „aggregate_sales_report_bestsellers_data“ [!DNL MySQL] verursacht, weil "/tmpdisk“ nicht genügend Speicherplatz zur Verfügung steht.
feature: Attributes
role: Admin, Developer
exl-id: 21f926e0-a4f4-45ae-9397-4885a85db947
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
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
source-wordcount: '335'
ht-degree: 0%
---
# ACSD-54890: `aggregate_sales_report_bestsellers_data` verursacht MySQL-Fehler

Mit dem Patch ACSD-54890 wird das Problem behoben, dass der `aggregate_sales_report_bestsellers_data` [!DNL MySQL] verursacht, da `/tmpdisk` nicht genügend Speicherplatz vorhanden ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54890. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `aggregate_sales_report_bestsellers_data` verursacht **[!DNL MySQL]** Fehler, da `/tmpdisk` nicht genügend Speicherplatz vorhanden ist.

<u>Schritte zur Reproduktion</u>:

Führen Sie den `aggregate_sales_report_bestsellers_data` Cron-Auftrag aus, wenn die `sales_bestsellers_aggregated_daily` eine enorme Anzahl von Datensätzen enthält, z. B. mehrere zehn Millionen Datensätze.

<u>Erwartete Ergebnisse</u>:

Keine Fehler auftreten.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
