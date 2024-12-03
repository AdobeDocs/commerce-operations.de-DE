---
title: 'ACSD-46404: Admin-Benutzer können sich nach einem Upgrade auf 2.4.4 nicht mehr anmelden'
description: Der Patch ACSD-46404 behebt das Problem, dass sich ein Admin-Benutzer nach einem Upgrade auf 2.4.4 nicht anmelden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.19 installiert ist. Die Patch-ID ist ACSD-46404. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.
feature: Admin Workspace
role: Admin
exl-id: f475ca56-5e06-4d4d-be42-f760c95968cf
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-46404: Admin-Benutzer können sich nach einem Upgrade auf 2.4.4 nicht mehr anmelden

Der Patch ACSD-46404 behebt das Problem, dass sich ein Admin-Benutzer nach einem Upgrade auf 2.4.4 nicht anmelden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.19 installiert ist. Die Patch-ID ist ACSD-46404. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator kann sich nach einem Upgrade auf 2.4.4 nicht mehr anmelden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin Panel an
1. Navigieren Sie zu Store > **Einstellungen** > **Konfiguration** > **Erweitert** > **System** > **Sicherheit**.
1. Setzen Sie die maximale Sitzungsgröße im Admin auf **0** und speichern Sie sie.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer kann sich erfolgreich anmelden.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator wird abgemeldet und kann sich nicht anmelden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
