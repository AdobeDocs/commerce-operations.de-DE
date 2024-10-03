---
title: 'ACSD-51630: Zahlreiche Systemnachrichten verlangsamen den Download von Admin-Seiten.'
description: Wenden Sie den Patch ACSD-51630 an, um das Adobe Commerce-Leistungsproblem zu beheben, das das Herunterladen von Admin-Seiten durch eine große Anzahl von Systemnachrichten verlangsamt.
feature: Admin Workspace, System
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-51630: Zahlreiche Systemnachrichten verlangsamen den Download von Admin-Seiten

Der Patch ACSD-51630 behebt das Leistungsproblem, bei dem eine große Anzahl von Systemnachrichten das Herunterladen von Admin-Seiten verlangsamt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID ist ACSD-51630. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Zahlreiche Systemnachrichten verlangsamen den Download von Admin Pages

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie eine große Anzahl von Anfragen (~50k) an DELETE `/rest/async/v1/products/ {sku}`.
1. Greifen Sie auf eine beliebige **Admin-Seite** zu.

<u>Erwartete Ergebnisse</u>:

Die Seite wird in einer geeigneten Zeit geladen. Nur angezeigte Nachrichten sollten geladen werden.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert zu lange. Alle vorhandenen Nachrichten werden aus der Datenbank geladen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.