---
title: 'ACSD-45849: Videometadaten gehen nach der Staging-Aktualisierung verloren'
description: Mit dem Patch „ACSD-45849“ wird das Problem behoben, dass die Videometadaten nach einer Staging-Aktualisierung verloren gehen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
feature: Staging, Page Content
role: Admin
exl-id: cbab0120-585a-47ef-8ed9-abb2da1ec3d6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-45849: Videometadaten gehen nach der Staging-Aktualisierung verloren

Mit dem Patch „ACSD-45849“ wird das Problem behoben, dass die Videometadaten nach einer Staging-Aktualisierung verloren gehen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Videometadaten gehen nach einer Staging-Aktualisierung verloren.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie den YouTube-API-Schlüssel unter **Admin** > **Stores** > **Configuration** > **Catalog** > **Produktvideo** ein.
1. Erstellen Sie ein Produkt mit einem YouTube-Video. Beachten Sie, dass die URL, der Titel und die Beschreibung ausgefüllt sind.
1. Erstellen Sie ein neues geplantes Update für das Produkt mit beliebigen Parametern, ohne den Abschnitt *Bilder und Video* zu ändern.
1. Klicken Sie **geplanten Änderungen auf** Anzeigen/Bearbeiten“.
1. Gehen Sie zu **Bilder und Videos** und klicken Sie auf das Video.

<u>Erwartete Ergebnisse</u>:

Die URL, der Titel und die Beschreibung enthalten die entsprechenden Daten.

<u>Tatsächliche Ergebnisse</u>:

Die Felder URL, Titel und Beschreibung sind leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
