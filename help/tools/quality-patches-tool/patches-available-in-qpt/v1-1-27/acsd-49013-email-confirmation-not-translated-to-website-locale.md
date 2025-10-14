---
title: 'ACSD-49013: E-Mail-Bestätigung nicht ins Website-Gebietsschema übersetzt'
description: Wenden Sie den ACSD-49013-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail-Bestätigung beim Erstellen von Kunden, die die Massen-API verwenden, nicht in das Website-Gebietsschema übersetzt wird.
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013: E-Mail-Bestätigung nicht ins Website-Gebietsschema übersetzt

Mit dem Patch ACSD-49013 wird das Problem behoben, dass E-Mail-Bestätigungen beim Erstellen von Kunden, die die Massen-API verwenden, nicht in das Website-Gebietsschema übersetzt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-49013. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die E-Mail-Bestätigung wird beim Erstellen von Kunden mit der Bulk-API nicht in das Website-Gebietsschema übersetzt.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie ein anderes Gebietsschema wie `de_DE`.
1. Konfigurieren Sie *RabbitMQ*.
1. Führen Sie `bin/magento setup:upgrade` aus, um die Warteschlangen in RabbitMQ zu installieren und das Sprachpaket einzurichten.
1. Erstellen Sie eine zusätzliche Website unter [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Legen Sie unter `de_DE` > [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** das Gebietsschema dieser neuen Website auf **[!UICONTROL Locale Options]** fest.
1. Führen Sie einen API-Aufruf aus, um mithilfe der Bulk-API ein Kundenkonto zu erstellen. Verwenden Sie die entsprechende `website_id`.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10` ausführen.
1. Sie können sehen, dass das Kundenkonto auf der angegebenen Website korrekt erstellt wurde.
1. Überprüfen Sie die für die Kundenregistrierung erhaltene E-Mail.

<u>Erwartete Ergebnisse</u>:

Da der Kunde auf einer bestimmten Website erstellt wird, wird die Registrierungs-E-Mail über das Gebietsschema dieser Website gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde wird auf der angegebenen Website korrekt erstellt, die Registrierungs-E-Mail wird jedoch unter Verwendung des Standardgebietsschemas gesendet, wenn die Massen-API verwendet wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
