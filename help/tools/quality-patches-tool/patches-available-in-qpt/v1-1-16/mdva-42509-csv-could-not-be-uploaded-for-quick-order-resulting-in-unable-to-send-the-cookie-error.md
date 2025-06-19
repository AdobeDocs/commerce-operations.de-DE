---
title: 'MDVA-42509: CSV konnte für die Schnellreihenfolge nicht hochgeladen werden, was zu der Fehlermeldung „Cookie kann nicht gesendet werden“ führte'
description: Der Patch MDVA-42509 löst das Problem, dass eine CSV-Datei nicht hochgeladen werden konnte, um eine schnelle Reihenfolge zu erhalten, was zu der Fehlermeldung führte, dass das Cookie nicht gesendet werden konnte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-42509. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: B2B, Orders
role: Admin
exl-id: 6319931b-9cf1-4004-b302-737863c53ff8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: CSV konnte für die Schnellreihenfolge nicht hochgeladen werden, was zu der Fehlermeldung „Cookie kann nicht gesendet werden“ führte

Der Patch MDVA-42509 löst das Problem, dass eine CSV-Datei nicht hochgeladen werden konnte, um eine schnelle Reihenfolge zu erhalten, was zu dem Fehler *Das Cookie kann nicht gesendet werden* führte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-42509. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Erstellung einer Schnellbestellung mit einer großen Anzahl von Produkten über eine CSV-Datei wird ein Cookie-Fehler angezeigt: *Cookie kann nicht gesendet werden*

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Schnellbestellung, indem Sie zu **Stores** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **B2B-Funktionen** navigieren.
1. Erstellen Sie ein Kundenkonto und navigieren Sie **Schnellbestellung** über den oberen Link.
1. Versuchen Sie, eine Schnellbestellung mit einer CSV-Datei zu erstellen, die über 100 SKUs enthält.

<u>Erwartete Ergebnisse</u>:

Sie können eine Schnellbestellung mit einer großen Anzahl von SKUs erstellen.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine Fehlermeldung bezüglich der Cookie-Größe angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
