---
title: "ACSD-53998: Dynamischer Block, der auf dem Kundensegment basiert, funktioniert nach dem Abmelden nicht richtig."
description: Wenden Sie den Patch ACSD-53998 an, um das Adobe Commerce-Problem zu beheben, bei dem ein dynamischer Block, der auf einem Kundensegment basiert, nach dem Abmelden von einem Kundenkonto nicht ordnungsgemäß funktioniert.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53998: Dynamischer Block, der auf dem Kundensegment basiert, funktioniert nach dem Abmelden falsch

Der Patch ACSD-53998 behebt das Problem, dass ein dynamischer Block, der auf einem Kundensegment basiert, nach dem Abmelden von einem Kundenkonto nicht ordnungsgemäß funktioniert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-53998. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein dynamischer Block, der auf einem Kundensegment basiert, funktioniert nach dem Abmelden von einem Kundenkonto nicht ordnungsgemäß.

<u>Voraussetzungen</u>:

Installieren und aktivieren Sie die [!DNL Page Builder] -Module.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Kundensegmente ohne Bedingungen.
1. Erstellen Sie zwei dynamische Blöcke für jedes Segment.
1. Erstellen Sie einen Baustein mit den beiden dynamischen Bausteinen [!DNL Page Builder] als dynamische Bausteine.
1. Erstellen Sie ein Widget einschließlich des obigen Blocks und machen Sie den Block unter dem Fußzeilenabschnitt aller Seiten sichtbar.
1. Löschen Sie die Caches.
1. Öffnen Sie die Startseite.
1. Melden Sie sich als Kunde an.
1. Melden Sie sich ab.

<u>Erwartete Ergebnisse</u>:

Das für angemeldete Kunden erstellte Banner wird nicht für Gastbenutzer angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das für das angemeldete Kundensegment erstellte Banner wird auch nach dem Abmelden vom Kundenkonto angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
