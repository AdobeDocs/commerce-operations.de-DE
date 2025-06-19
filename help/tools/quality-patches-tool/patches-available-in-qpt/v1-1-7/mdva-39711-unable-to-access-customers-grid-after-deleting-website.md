---
title: 'MDVA-39711: Nach dem Löschen der Website kann nicht auf das Kundenraster zugegriffen werden'
description: Der Patch MDVA-39711 behebt das Problem, dass der Admin-Benutzer nach dem Löschen der Website nicht auf das Raster der Kunden zugreifen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-39711. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Configuration
role: Admin
exl-id: 7ddca2e7-86f5-4ffd-9c00-ea4c511ab663
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39711: Nach dem Löschen der Website kann nicht auf das Kundenraster zugegriffen werden

Der Patch MDVA-39711 behebt das Problem, dass der Admin-Benutzer nach dem Löschen der Website nicht auf das Raster der Kunden zugreifen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-39711. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7-p2, 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Administrator bzw. eine Administratorin kann nach dem Löschen der Website nicht auf das Raster der Kundinnen und Kunden zugreifen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Erstellen Sie einen neuen Kunden in der Admin Console und verknüpfen Sie ihn mit der erstellten Website.
1. Gehen Sie zu **Stores** > **Alle Stores** und löschen Sie die erstellte Website.
1. Navigieren Sie **Kunden** > **Alle Kunden**.

<u>Erwartete Ergebnisse</u>:

* Es wird keine Fehlermeldung angezeigt.
* Alle Kunden sind im Raster sichtbar.

<u>Tatsächliche Ergebnisse</u>:

* Der/die Benutzende erhält eine Fehlermeldung: *Die angeforderte Website mit der ID 2 wurde nicht gefunden. Überprüfen Sie die Website und versuchen Sie es erneut*
* Es werden nicht alle Kunden angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
