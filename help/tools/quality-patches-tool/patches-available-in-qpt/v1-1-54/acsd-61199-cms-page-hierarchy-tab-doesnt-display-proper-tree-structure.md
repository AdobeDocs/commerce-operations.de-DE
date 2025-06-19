---
title: 'ACSD-61199: Die Registerkarte "[!UICONTROL Hierarchy]" der CMS-Seite zeigt keine ordnungsgemäße Baumstruktur an'
description: Wenden Sie den Patch ACSD-61199 an, um das Adobe Commerce-Problem zu beheben, bei dem auf der Registerkarte *[!UICONTROL Hierarchy]* der CMS-Seite beim Bearbeiten einer CMS-Seite mit einer vorhandenen *[!UICONTROL Hierarchy]* keine richtige Baumstruktur angezeigt wird.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: Auf der Registerkarte &quot;[!UICONTROL Hierarchy]&quot; der CMS-Seite wird keine ordnungsgemäße Baumstruktur angezeigt

Mit dem Patch ACSD-61199 wird das Problem behoben, dass auf der Registerkarte *[!UICONTROL Hierarchy]* der CMS-Seite beim Bearbeiten einer CMS-Seite mit einer vorhandenen *[!UICONTROL Hierarchy]* keine richtige Baumstruktur angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61199. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Auf der Registerkarte &quot;*[!UICONTROL Hierarchy]*&quot; der CMS-Seite wird beim Bearbeiten einer CMS-Seite mit einer vorhandenen *[!UICONTROL Hierarchy]* keine richtige Baumstruktur angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Erstellen Sie eine neue **[!UICONTROL CMS page]**. Er wird dem Website-Stammverzeichnis unter *[!UICONTROL Hierarchy]* hinzugefügt.
1. Speichern Sie die Seite.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Fügen Sie dem *[!UICONTROL Hierarchy]* alle anderen vorhandenen Seiten hinzu.
1. Speichern Sie die *[!UICONTROL Hierarchy]*.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Bearbeiten Sie eine der vorhandenen Seiten und öffnen Sie die *[!UICONTROL Hierarchy]*.

<u>Erwartete Ergebnisse</u>:

Der *[!UICONTROL Hierarchy]* wird erwartungsgemäß geladen.

<u>Tatsächliche Ergebnisse</u>:

Die *[!UICONTROL Hierarchy]* wird nicht in die Registerkarte geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
