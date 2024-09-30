---
title: 'ACSD-52277: Admin-Benutzer hat beim Auswählen der Store-Ansicht beim Erstellen einer neuen Bestellung fälschlicherweise umgeleitet.'
description: Wenden Sie den Patch ACSD-52277 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer nach Auswahl der Store-Ansicht beim Erstellen einer neuen Bestellung in Admin nicht ordnungsgemäß umgeleitet wird.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277: Admin-Benutzer hat beim Erstellen einer neuen Bestellung fälschlicherweise die Auswahl der Store-Ansicht umgeleitet

Der Patch ACSD-52277 behebt das Problem, dass ein Admin-Benutzer nach Auswahl der Store-Ansicht beim Erstellen einer neuen Bestellung in Admin nicht ordnungsgemäß umgeleitet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-52277. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Admin-Benutzer wird nicht ordnungsgemäß umgeleitet, nachdem beim Erstellen einer neuen Bestellung die Store-Ansicht ausgewählt wurde.

<u>Zu reproduzierende Schritte</u>

1. Installieren Sie eine saubere Instanz.
1. Erstellen Sie ein Produkt.
1. Erstellen Sie eine zusätzliche Website, einen Store und zwei Store-Ansichten.
1. Erstellen Sie eine Bestellung vom Administrator, indem Sie *Store-Ansicht 1* auswählen.

<u>Erwartete Ergebnisse</u>:

Der Benutzer wird zur Bestellseite weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Der Benutzer wird nach Auswahl der Store-Ansicht nicht zur Bestellseite weitergeleitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
