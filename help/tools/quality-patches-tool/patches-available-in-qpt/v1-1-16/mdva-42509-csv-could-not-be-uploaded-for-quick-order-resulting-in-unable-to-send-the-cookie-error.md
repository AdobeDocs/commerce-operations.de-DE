---
title: '"MDVA-42509: CSV konnte nicht für schnelle Bestellung hochgeladen werden, was zu dem Fehler "Cookie kann nicht gesendet werden"führte.'
description: Der MDVA-42509-Patch behebt das Problem, dass eine CSV-Datei nicht für eine schnelle Bestellung hochgeladen werden konnte, was dazu führte, dass der Cookie-Fehler nicht gesendet werden konnte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-42509. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: B2B, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: CSV konnte nicht für schnelle Bestellung hochgeladen werden, was zu dem Fehler &quot;Cookie kann nicht gesendet werden&quot;führte

Der Patch MDVA-42509 behebt das Problem, dass eine CSV-Datei nicht für eine schnelle Bestellung hochgeladen werden konnte, was dazu führte, dass der Fehler *Cookie konnte nicht gesendet werden* angezeigt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-42509. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie mithilfe einer CSV-Datei eine schnelle Bestellung mit einer großen Anzahl von Produkten erstellen, wird ein Cookie-Fehler angezeigt: *Cookie kann nicht gesendet werden*

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Schnellreihenfolge, indem Sie zu **Stores** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **B2B-Funktionen** navigieren.
1. Erstellen Sie ein Kundenkonto und gehen Sie zu **Quick Order** am oberen Link.
1. Versuchen Sie, eine schnelle Bestellung mithilfe einer CSV-Datei mit mehr als 100 SKUs zu erstellen.

<u>Erwartete Ergebnisse</u>:

Sie können eine schnelle Bestellung mit einer großen Anzahl von SKUs erstellen.

<u>Tatsächliche Ergebnisse</u>:

Eine Fehlermeldung wird in Bezug auf die Cookie-Größe angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
