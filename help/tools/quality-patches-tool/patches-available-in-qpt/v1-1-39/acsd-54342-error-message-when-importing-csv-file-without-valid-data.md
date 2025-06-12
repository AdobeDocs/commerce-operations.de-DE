---
title: 'ACSD-54342: Fehlermeldung beim Importieren einer CSV-Datei ohne gültige Daten'
description: Wenden Sie den Patch ACSD-54342 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Importieren einer CSV-Datei ohne gültige Daten eine falsche Fehlermeldung auftritt.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 34324a18-45af-462b-a6e6-6b6a02d4d331
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54342: Fehlermeldung beim Importieren einer CSV-Datei ohne gültige Daten

Der Patch ACSD-54342 behebt das Problem, dass beim Importieren einer CSV-Datei ohne gültige Daten eine falsche Fehlermeldung auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-54342. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Importieren einer CSV-Datei ohne gültige Daten tritt eine falsche Fehlermeldung auf.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Importdatei nur mit ungültigen Daten (Beispiele: [!DNL SKUs], die nicht vorhanden sind, ungültige Kundenadressfelder oder falsch formatierte Kunden-E-Mail-Adressen).
1. Importieren Sie die Datei und wählen Sie diese Option aus, um die Validierungsfehler zu überspringen.

<u>Erwartete Ergebnisse</u>:

Die Validierung schlägt mit `There are no valid rows to import` Meldung fehl.

<u>Tatsächliche Ergebnisse</u>:

Die Validierung verläuft erfolgreich, aber der Import schlägt mit `Error in data structure: values are mixed` Meldung fehl.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
