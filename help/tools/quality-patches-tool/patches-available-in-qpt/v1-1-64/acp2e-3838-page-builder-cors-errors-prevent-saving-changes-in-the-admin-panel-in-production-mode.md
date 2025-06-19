---
title: 'ACP2E-3838: [!DNL Page Builder] CORS-Fehler verhindern das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus'
description: Wenden Sie den Patch ACP2E-3838 an, um das Adobe Commerce-Problem zu beheben, bei dem  [!DNL Page Builder] -CORS-Fehler das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus verhindern.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838: [!DNL Page Builder] CORS-Fehler verhindern das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus

Mit dem Patch ACP2E-3838 wird das Problem behoben, dass [!DNL Page Builder] CORS-Fehler das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus verhindern. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID lautet ACP2E-3838. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL Page Builder] CORS-Fehler verhindern das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Admin Panel an.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Klicken Sie auf **[!UICONTROL Add New Page]** oder wählen Sie eine bestehende CMS-Seite aus und klicken Sie auf **[!UICONTROL Edit]**.
1. Klicken Sie auf **[!UICONTROL Edit with Page Builder]** , um einen neuen Inhaltsbaustein hinzuzufügen oder einen vorhandenen Baustein zu bearbeiten.
1. Nehmen Sie beliebige Änderungen am Inhalt vor, z. B. das Hinzufügen von Text, Bildern oder anderen Elementen.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** .

<u>Erwartete Ergebnisse</u>:

Der Seiteninhalt sollte erfolgreich und fehlerfrei gespeichert werden.

<u>Tatsächliche Ergebnisse</u>:

1. Die [!DNL Page Builder] Änderungen werden nicht gespeichert.
1. Die Browser-Konsole protokolliert CORS-bezogene Fehler.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
