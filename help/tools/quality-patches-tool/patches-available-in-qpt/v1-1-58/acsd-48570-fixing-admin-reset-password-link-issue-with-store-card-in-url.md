---
title: 'ACSD-48570: Problem mit dem Link zum Zurücksetzen des Admin-Kennworts beim Speichern des Codes in der URL wird behoben'
description: Wenden Sie den Patch ACSD-48570 an, um das Adobe Commerce-Problem zu beheben, bei dem die Seite „Kennwort zurücksetzen“ nicht über den Link „Admin-Kennwort zurücksetzen“ aufgerufen werden konnte, wenn die [!UICONTROL Add Store Code to URLs] aktiviert war.
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: Problem mit dem Link zum Zurücksetzen des Admin-Kennworts beim Speichern des Codes in der URL wird behoben

Der Patch von ACSD-48570 zur Behebung des Adobe Commerce-Problems, dass die Seite zum Zurücksetzen des Kennworts nicht über den Link zum Zurücksetzen des Admin-Kennworts aufgerufen werden konnte, wenn die *[!UICONTROL Add Store Code to URLs]* aktiviert war. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-48570. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die **[!UICONTROL Add Store Code to URLs]** aktiviert ist, funktioniert die Funktion zum Zurücksetzen des Administratorkennworts nicht ordnungsgemäß.
Nachdem ein Administrator bzw. eine Administratorin das Zurücksetzen des Kennworts angefordert und in der E-Mail auf den Wiederherstellungs-Link geklickt hat, wird er/sie zur Anmeldeseite weitergeleitet oder erhält einen 404-Fehler, anstatt zum Formular zum Zurücksetzen des Kennworts weitergeleitet zu werden. Dadurch wird verhindert, dass Administratoren ihre Konten ohne manuelles Eingreifen wiederherstellen können.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die **[!UICONTROL Add Store Code to URLs]** unter **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**.
1. Melden Sie sich über das Admin-Bedienfeld ab und klicken Sie auf der Admin-Anmeldeseite auf den Link **[!UICONTROL Forgot your password?]** .
1. Geben Sie die E-Mail-Adresse des Admin-Benutzers ein, übergeben Sie das Captcha und klicken Sie auf **[!UICONTROL Retrieve Password]**.
1. Öffnen Sie die E-Mail zum Zurücksetzen des Kennworts und klicken Sie auf den Link zur Kennwortwiederherstellung .

<u>Erwartete Ergebnisse</u>:

Das Formular zum Zurücksetzen des Kennworts sollte angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Anmeldeseite oder eine 404-Fehlerseite wird anstelle des Formulars zum Zurücksetzen des Passworts angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
