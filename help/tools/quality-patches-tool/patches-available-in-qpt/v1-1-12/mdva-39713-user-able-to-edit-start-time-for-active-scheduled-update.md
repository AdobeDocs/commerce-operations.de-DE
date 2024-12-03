---
title: 'MDVA-39713: Benutzer kann die Startzeit einer geplanten aktiven Aktualisierung bearbeiten'
description: Der Patch MDVA-39713 behebt das Problem, dass ein Benutzer die Startzeit eines aktiven geplanten Updates bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39713. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713: Benutzer kann die Startzeit einer geplanten aktiven Aktualisierung bearbeiten

Der Patch MDVA-39713 behebt das Problem, dass ein Benutzer die Startzeit eines aktiven geplanten Updates bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39713. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer kann die Startzeit für eine aktive geplante Aktualisierung bearbeiten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie neue CMS-Seiten.
1. Wählen Sie **Neues Update planen** und setzen Sie das **Startdatum** auf die aktuelle +1-Minute-Zeit.
1. Aktivieren Sie das geplante Update, indem Sie den Befehl `bin/magento cron:run --group=staging` in der lokalen Umgebung ausführen. Warten Sie einige Minuten und überprüfen Sie, ob der Zeitplan aktiv ist.
1. Sobald der Zeitplan aktiv ist, aktualisieren Sie die Seite.
1. Klicken Sie im Abschnitt &quot;Geplante Änderungen&quot;auf **Anzeigen/Bearbeiten** .
1. Bearbeiten Sie die Zeit, indem Sie +2 Minuten hinzufügen und speichern Sie die Änderung.
1. Speichern Sie die CMS-Seite.
1. Führen Sie erneut den folgenden Befehl aus: `bin/magento cron:run --group=staging`.
1. Klicken Sie auf **Anzeigen/Bearbeiten** des geplanten Updates.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann die Startzeit für eine aktive geplante Aktualisierung nicht bearbeiten.

<u>Tatsächliche Ergebnisse</u>:

Der Benutzer erhält einen Fehler wie *Element (Magento\Cms\Model\Page) mit der gleichen ID &quot;11&quot;bereits vorhanden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
