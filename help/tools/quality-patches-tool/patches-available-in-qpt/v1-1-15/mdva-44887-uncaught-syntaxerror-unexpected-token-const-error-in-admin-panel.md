---
title: 'MDVA-44887: Fehler "Uncaught SyntaxError: Unexpected Token const"im Admin Panel'
description: 'Der Patch MDVA-44887 behebt das Problem, dass der Admin-Benutzer nicht auf eine Menüoption klicken kann. Der Fehler *Uncaught SyntaxError: Unerwartete Token const* wird im Admin-Bedienfeld angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44887. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.'
feature: Admin Workspace, Orders
role: Admin
exl-id: d8cc03c3-35a0-4f00-8ec3-1ba3e100f7ca
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-44887: Fehler &quot;Uncaught SyntaxError: Unexpected Token const&quot;im Admin Panel

Der Patch MDVA-44887 behebt das Problem, dass der Admin-Benutzer nicht auf eine Menüoption klicken kann. Der Fehler *Uncaught SyntaxError: Unexpected Token const* wird im Admin-Bereich angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44887. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator kann auf keine Menüoption klicken. Der Fehler *Uncaught SyntaxError: Unexpected Token const* wird im Admin-Bereich angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie JS-Bundling.
1. Minimieren Sie die JS-Dateien.
1. Melden Sie sich beim Commerce Admin-Bedienfeld an.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann auf keine Menüoption klicken. In der Browser-Konsole tritt ein Fehler auf: *Uncaught SyntaxError: Unexpected token const*.

<u>Tatsächliche Ergebnisse</u>:

Auf das Admin-Bedienfeld kann ein Admin-Benutzer zugreifen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
