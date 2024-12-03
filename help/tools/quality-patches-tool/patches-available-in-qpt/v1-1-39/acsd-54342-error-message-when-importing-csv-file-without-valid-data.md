---
title: 'ACSD-54342: Fehlermeldung beim Import einer CSV-Datei ohne gültige Daten'
description: Wenden Sie den Patch ACSD-54342 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Importieren einer CSV-Datei ohne gültige Daten eine falsche Fehlermeldung auftritt.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 34324a18-45af-462b-a6e6-6b6a02d4d331
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54342: Fehlermeldung beim Import einer CSV-Datei ohne gültige Daten

Der Patch ACSD-54342 behebt das Problem, dass beim Import einer CSV-Datei ohne gültige Daten eine falsche Fehlermeldung auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-54342. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Import einer CSV-Datei ohne gültige Daten wird eine falsche Fehlermeldung angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Importdatei mit nur ungültigen Daten (Beispiele: [!DNL SKUs] , die nicht vorhanden sind, ungültige Felder der Kundenadresse oder fehlerhafte E-Mail-Adressen von Kunden).
1. Importieren Sie die Datei und wählen Sie diese Option, um die Überprüfungsfehler zu überspringen.

<u>Erwartete Ergebnisse</u>:

Die Validierung schlägt mit der Meldung `There are no valid rows to import` fehl.

<u>Tatsächliche Ergebnisse</u>:

Die Validierung ist erfolgreich, der Import schlägt jedoch mit der Meldung `Error in data structure: values are mixed` fehl.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
