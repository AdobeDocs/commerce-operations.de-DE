---
title: 'ACSD-54040: Das Feld [!UICONTROL Created] ist in den Bestelldetails leer, wenn B2B-Module aktiviert sind'
description: Wenden Sie den Patch ACSD-54040 an, um das Adobe Commerce-Problem zu beheben, bei dem das Feld [!UICONTROL Created] auf der Bestelldetailseite leer ist, wenn B2B-Module aktiviert sind.
feature: B2B
role: Admin, Developer
exl-id: 09fc1e0f-2e02-4cfc-9a7a-7c6aacd9fee0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040: Das Feld *[!UICONTROL Created]* ist in den Bestelldetails leer, wenn B2B-Module aktiviert sind.

Der Patch ACSD-54040 behebt das Problem, dass das Feld *[!UICONTROL Created]* auf der Seite mit Bestelldetails leer bleibt, wenn B2B-Module aktiviert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54040. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn B2B-Module aktiviert sind, bleibt das Feld *[!UICONTROL Created]* auf der Bestelldetailseite leer.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit dem B2B-Modul.
1. Erstellen Sie einen neuen Kunden und geben Sie eine Bestellung auf.
1. Markieren Sie im Frontend die Bestelldetails und aktivieren Sie das Feld *[!UICONTROL Created]* .

<u>Erwartete Ergebnisse</u>:

Das Feld *[!UICONTROL Created]* zeigt das Datum an, an dem die Bestellung erstellt wurde.

<u>Tatsächliche Ergebnisse</u>:

Das Feld *[!UICONTROL Created]* ist leer

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
