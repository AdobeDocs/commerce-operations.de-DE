---
title: 'MDVA-44940: SQL-Fehler beim Speichern der Kategorie unter Admin'
description: Der Patch MDVA-44940 behebt das Problem, dass beim Speichern einer Kategorie vom Administrator ein SQL-Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44940. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Admin Workspace, Categories, Sales Channels
role: Admin
exl-id: de4384f1-a75d-4726-810f-6560a7c57b82
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-44940: SQL-Fehler beim Speichern der Kategorie unter Admin

Der Patch MDVA-44940 behebt das Problem, dass beim Speichern einer Kategorie vom Administrator ein SQL-Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44940. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Speichern einer Kategorie vom Administrator tritt ein SQL-Fehler auf.

<u>Zu reproduzierende Schritte</u>:

1. Beispieldaten installieren.
1. Erstellen Sie eine zweite Website mit einer Store-Gruppe, die der Standardkategorie zugeordnet ist.

   * Erstellen Sie eine Store-Ansicht, die der neuen Store-Gruppe zugewiesen ist.

1. Erstellen Sie ein Lager und eine zusätzliche Quelle, die diesem Lager zugewiesen ist, sowie einen Vertriebskanal, der der zweiten Website zugewiesen ist.
1. Erstellen Sie ein Testprodukt, das der zweiten Website zugewiesen ist.
1. Navigieren Sie zu **Admin** > **Katalog** > **Kategorien**, wählen Sie **Umfang** = **Zweite Website** aus und gehen Sie zu **Produkte in Kategorie** > **Automatische Sortierung** > Nach unten verschieben und klicken Sie auf **Speichern**}.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wird gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf: *Beim Speichern der Kategorie* ist etwas schief gelaufen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
