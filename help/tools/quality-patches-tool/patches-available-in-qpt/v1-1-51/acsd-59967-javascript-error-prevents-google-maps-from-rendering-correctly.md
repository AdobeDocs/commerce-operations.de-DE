---
title: 'ACSD-59967: JavaScript-Fehler verhindert [!DNL Google Maps]  dass korrekt gerendert wird'
description: Wenden Sie den ACSD-59967-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der JavaScript-Fehler verhindert [!DNL Google Maps]  dass korrekt gerendert wird.
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967: JavaScript-Fehler verhindert, dass [!DNL Google Maps] korrekt gerendert werden

Der Patch ACSD-59967 behebt das Problem, dass der JavaScript-Fehler verhindert, dass [!DNL Google Maps] korrekt gerendert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-59967. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

JavaScript-Fehler verhindert, dass [!DNL Google Maps] richtig gerendert werden.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie einen gültigen [!DNL Google Maps].
1. Konfigurieren Sie den [!DNL Google Maps] API-Schlüssel unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**.
1. Fügen Sie Ihre [!DNL Google API Key] zu **[!UICONTROL Google Maps API Key]** Feld hinzu und speichern Sie die Konfiguration.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**.
1. Fügen Sie ein **[!UICONTROL Row]** und ein **[!UICONTROL Maps]** Element hinzu.

<u>Erwartete Ergebnisse</u>:

In der Konsole sind keine JavaScript-Fehler vorhanden, und die Zuordnung wird auf der *Storefront* und *Admin* korrekt dargestellt.

<u>Tatsächliche Ergebnisse</u>:

JavaScript-Fehler werden in der Konsole angezeigt und die Zuordnung wird nicht ordnungsgemäß gerendert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
