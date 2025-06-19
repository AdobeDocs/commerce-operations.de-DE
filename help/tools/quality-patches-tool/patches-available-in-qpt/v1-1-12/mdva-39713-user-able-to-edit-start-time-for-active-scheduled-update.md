---
title: 'MDVA-39713: Der Benutzer kann die Startzeit der aktiven geplanten Aktualisierung bearbeiten'
description: Der Patch MDVA-39713 behebt das Problem, dass ein Benutzer die Startzeit eines aktiven geplanten Updates bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39713. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713: Der Benutzer kann die Startzeit der aktiven geplanten Aktualisierung bearbeiten

Der Patch MDVA-39713 behebt das Problem, dass ein Benutzer die Startzeit eines aktiven geplanten Updates bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39713. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.6

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Benutzer kann die Startzeit für eine aktive geplante Aktualisierung bearbeiten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie neue CMS-Seiten.
1. Wählen Sie **Neues Update planen** und legen Sie das **Startdatum** auf aktuelle +1 Minute fest.
1. Aktivieren Sie das geplante Update, indem Sie den Befehl `bin/magento cron:run --group=staging` in der lokalen Umgebung ausführen. Warten Sie einige Minuten und überprüfen Sie, ob der Zeitplan aktiv ist.
1. Sobald der Zeitplan aktiv ist, aktualisieren Sie die Seite.
1. Klicken **im Abschnitt Geplante** auf „Anzeigen/Bearbeiten“.
1. Bearbeiten Sie die Zeit durch Hinzufügen von +2 Minuten und speichern Sie die Änderung.
1. Speichern Sie die CMS-Seite.
1. Führen Sie erneut den folgenden Befehl aus: `bin/magento cron:run --group=staging`.
1. Klicken Sie **Anzeigen/Bearbeiten** der geplanten Aktualisierung.

<u>Erwartete Ergebnisse</u>:

Der/die Benutzende kann die Startzeit für eine aktive geplante Aktualisierung nicht bearbeiten.

<u>Tatsächliche Ergebnisse</u>:

Der Benutzer erhält einen Fehler wie *Element (Magento\Cms\Model\Page) mit der gleichen ID „11“ bereits vorhanden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
