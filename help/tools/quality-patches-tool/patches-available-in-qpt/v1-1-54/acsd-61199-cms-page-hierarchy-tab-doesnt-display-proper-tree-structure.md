---
title: 'ACSD-61199: Registerkarte "CMS-Seite [!UICONTROL Hierarchy]"zeigt keine ordnungsgemäße Baumstruktur an'
description: Wenden Sie den Patch ACSD-61199 an, um das Adobe Commerce-Problem zu beheben, bei dem die Registerkarte *[!UICONTROL Hierarchy]* der CMS-Seite beim Bearbeiten einer CMS-Seite mit vorhandenem *[!UICONTROL Hierarchy]* keine ordnungsgemäße Baumstruktur anzeigt.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
source-git-commit: 5568b2f574c7e90e641513c3c0ea4574648770ac
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: Die Registerkarte &quot;[!UICONTROL Hierarchy]&quot;der CMS-Seite zeigt keine ordnungsgemäße Baumstruktur an

Der Patch ACSD-61199 behebt das Problem, dass die Registerkarte &quot;*[!UICONTROL Hierarchy]*&quot;der CMS-Seite beim Bearbeiten einer CMS-Seite mit einer vorhandenen &quot;*[!UICONTROL Hierarchy]*&quot;keine ordnungsgemäße Baumstruktur anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61199. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Registerkarte &quot;*[!UICONTROL Hierarchy]*&quot;der CMS-Seite zeigt beim Bearbeiten einer CMS-Seite mit vorhandenem &quot;*[!UICONTROL Hierarchy]*&quot;keine ordnungsgemäße Baumstruktur an.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Erstellen Sie eine neue **[!UICONTROL CMS page]**. Sie wird dem Website-Stamm am *[!UICONTROL Hierarchy]* hinzugefügt.
1. Speichern Sie die Seite.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Fügen Sie alle anderen vorhandenen Seiten zum *[!UICONTROL Hierarchy]* hinzu.
1. Speichern Sie die *[!UICONTROL Hierarchy]*.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Bearbeiten Sie eine der vorhandenen Seiten und öffnen Sie den *[!UICONTROL Hierarchy]*.

<u>Erwartete Ergebnisse</u>:

Der *[!UICONTROL Hierarchy]* wird erwartungsgemäß geladen.

<u>Tatsächliche Ergebnisse</u>:

Die *[!UICONTROL Hierarchy]* wird nicht auf der Registerkarte geladen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
