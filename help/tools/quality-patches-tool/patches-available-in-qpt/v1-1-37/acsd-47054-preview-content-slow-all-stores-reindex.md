---
title: 'ACSD-47054: Vorschau des Inhalts langsam, wenn alle Speicher neu indiziert werden'
description: Wenden Sie den Patch ACSD-47054 an, um das Adobe Commerce-Problem zu beheben, bei dem die Vorschauseite aufgrund der Neuindizierung aller Stores langsam geladen wird.
feature: Page Content
role: Admin, Developer
exl-id: bfbda95a-354b-4b67-8081-84aefbbd7cb4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47054: Vorschau des Inhalts langsam, wenn alle Speicher neu indiziert werden

Mit dem Patch ACSD-47054 wird das Problem behoben, dass das Laden einer Vorschau des Staging-Inhalts länger dauert, wenn viele Stores vorhanden sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.37 installiert ist. Die Patch-ID ist ACSD-47054. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.2-p2, 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Laden der Vorschauseite dauert aufgrund einer Neuindizierung aller Stores sehr lange.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zum Commerce-Administrator.
1. Erstellen Sie eine beliebige geplante Aktualisierung.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Vorschau der geplanten Aktualisierung anzeigen.
1. Beliebige Kategorie öffnen.

<u>Erwartete Ergebnisse</u>:

Die Vorschauseite wird innerhalb einer akzeptablen Zeit geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Vorschau des Inhalts-Staging dauert lange.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
