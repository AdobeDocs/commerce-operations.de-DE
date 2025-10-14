---
title: 'ACSD-49960: Die Filterung nach Datum funktioniert nicht für das Kundenauftragsraster'
description: Wenden Sie den Patch ACSD-49960 an, um das Adobe Commerce-Problem zu beheben, bei dem das Filtern nach Datum für das Kundenauftragsraster nicht funktioniert.
feature: Admin Workspace, Orders
role: Admin
exl-id: 0ca607b4-5500-4d70-be5e-a3a2b62c6864
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-49960: Die Filterung nach Datum funktioniert nicht für das Kundenauftragsraster

Mit dem Patch ACSD-49960 wird das Problem behoben, dass das Filtern nach Datum für das Kundenauftragsraster nicht funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49960. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Filterung nach Datum funktioniert nicht für das Kundenauftragsraster.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Edit customer]** im Backend.
1. Öffnen Sie die Registerkarte **[!UICONTROL Orders]** .
1. Wenden Sie Datumsfilter in der *[!UICONTROL Purchased]* an.

<u>Erwartete Ergebnisse</u>:

Durch Anwendung des Filters werden Kundenaufträge nach ihrem Kaufdatum sortiert.

<u>Tatsächliche Ergebnisse</u>:

Beim Anwenden des Filters wird ein JS-Fehler in der Konsole ausgegeben und das Ladeprogramm wird weiter geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
