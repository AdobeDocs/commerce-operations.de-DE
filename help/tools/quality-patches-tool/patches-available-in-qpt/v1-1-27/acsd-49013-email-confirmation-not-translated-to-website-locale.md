---
title: "ACSD-49013: E-Mail-Bestätigung nicht in Website-Gebietsschema übersetzt"
description: Wenden Sie den Patch ACSD-49013 an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail-Bestätigung beim Erstellen von Kunden mit Bulk API nicht in das Gebietsschema der Website übersetzt wird.
feature: Admin Workspace, Communications
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013: E-Mail-Bestätigung nicht in das Gebietsschema der Website übersetzt

Der Patch ACSD-49013 behebt das Problem, dass die E-Mail-Bestätigung beim Erstellen von Kunden mit Bulk API nicht in das Gebietsschema der Website übersetzt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-49013. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die E-Mail-Bestätigung wird beim Erstellen von Kunden mithilfe der Bulk API nicht in das Gebietsschema der Website übersetzt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie ein anderes Gebietsschema wie `de_DE`.
1. Konfigurieren Sie *RabbitMQ*.
1. Führen Sie `bin/magento setup:upgrade` aus, um die Warteschlangen in RabbitMQ zu installieren und das Sprachpaket einzurichten.
1. Erstellen Sie eine zusätzliche Website unter [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Setzen Sie das Gebietsschema dieser neuen Website auf `de_DE` in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Führen Sie einen API-Aufruf aus, um ein Kundenkonto mit der Bulk API zu erstellen. Verwenden Sie den entsprechenden `website_id`.

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

1. Führen Sie `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10` aus.
1. Sie können sehen, dass das Kundenkonto auf der angegebenen Website korrekt erstellt wurde.
1. Überprüfen Sie die E-Mail, die zur Kundenregistrierung empfangen wurde.

<u>Erwartete Ergebnisse</u>:

Da der Kunde auf einer bestimmten Website erstellt wird, wird die Registrierungs-E-Mail mit dem Gebietsschema dieser Website gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde wird ordnungsgemäß auf der angegebenen Website erstellt, die Registrierungs-E-Mail wird jedoch mit dem Standardgebietsschema gesendet, wenn die Bulk-API verwendet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
