---
title: 'ACSD-49748: E-Mail-Einladungen können nicht gesendet werden'
description: Wenden Sie den Patch ACSD-49748 an, um das Adobe Commerce-Problem zu beheben, bei dem Benutzende keine E-Mail-Einladungen senden können.
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
exl-id: 03dad66c-4691-421e-8c80-eca12c60175c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# ACSD-49748: E-Mail-Einladungen können nicht gesendet werden

Mit dem Patch ACSD-49748 wird das Problem behoben, dass Benutzende keine E-Mail-Einladungen senden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49748. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Senden *Einladungen wird der Fehler „Beim Senden* Einladungen ist ein Fehler aufgetreten“ angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]**.
1. Erstellen Sie eine Einladung und speichern Sie sie.
1. Gehen Sie zu **[!UICONTROL Invitation Grid]** und wählen Sie eine Einladung aus.
1. Senden Sie die Einladung.

<u>Erwartete Ergebnisse</u>:

Beim Klicken auf &quot;*[!UICONTROL Send Invitation]*&quot; wird eine Einladung gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler *Beim Senden von Einladungen ist ein Fehler aufgetreten* wird angezeigt, und die Einladung wird nicht gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].
