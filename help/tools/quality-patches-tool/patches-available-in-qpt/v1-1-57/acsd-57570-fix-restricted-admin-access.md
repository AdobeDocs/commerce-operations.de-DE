---
title: 'ACSD-57570: Fehlerbehebung für eingeschränkten Admin-Benutzerzugriff auf freigegebene Kataloge'
description: Wenden Sie den ACSD-57570 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer mit eingeschränktem Administratorzugriff auf einen bestimmten Store nicht alle freigegebenen Kataloge, die Produkten zugewiesen sind, konsistent anzeigen oder Kundeninformationen speichern kann, was zu Systeminkonsistenzen führt.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570: Fehlerbehebung für eingeschränkten Admin-Benutzerzugriff auf freigegebene Kataloge

Mit dem Patch ACSD-57570 wird das Problem behoben, dass ein Admin-Benutzer mit eingeschränktem Zugriff auf einen bestimmten Store nicht alle freigegebenen Kataloge, die Produkten zugewiesen sind, konsistent anzeigen oder Kundeninformationen speichern kann, was zu Systeminkonsistenzen führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-57570. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Admin-Benutzer mit eingeschränktem Zugriff auf einen bestimmten Store kann nicht immer alle freigegebenen Kataloge anzeigen oder Kunden speichern, was zu Inkonsistenzen führt. Bei mehreren Stores kann der Admin mit Zugriffsbeschränkung keine neuen Unternehmen oder benutzerdefinierten freigegebenen Kataloge sehen.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie Stores in der folgenden Reihenfolge ein:
   * Erstellen Sie eine neue Website mit dem Namen W2.
   * Erstellen Sie eine neue Store-Ansicht für die Standard-Website.
   * Erstellen Sie einen neuen Store mit dem Namen W2S2 für die Website W2.
   * Erstellen Sie eine neue Store-Ansicht mit dem Namen W2S2SV1 für den Store W2S2.
   * Erstellen Sie eine weitere neue Store-Ansicht mit dem Namen W2S2SV2 für den Store W2S2.
   * Erstellen Sie eine Firma für W2.
1. Produkte zuweisen:
   * Weisen Sie einige Produkte nur W1 zu.
   * Weisen Sie einige Produkte nur W2 zu.
   * Weisen Sie einige Produkte sowohl W1 als auch W2 zu.
1. Erstellen Sie einen benutzerdefinierten freigegebenen Katalog und weisen Sie ihm alle Produkte zu.
1. Erstellen Sie eine benutzerdefinierte Administratorrolle mit Zugriff nur auf **W2S2**, nicht auf **W2**.
1. Weisen Sie den eingeschränkten Admin-Benutzer der neuen benutzerdefinierten Admin-Rolle zu.
1. Melden Sie sich als eingeschränkter Admin-Benutzer an.
1. Überprüfen Sie den Zugriff:
   * Überprüfen Sie, welche Firmen Sie sehen können.
   * Überprüfen Sie, welche freigegebenen Kataloge Sie sehen können.
   * Öffnen Sie die Produktliste und überprüfen Sie, ob Sie alle freigegebenen Kataloge sehen können, denen die Produkte zugewiesen sind.

<u>Erwartete Ergebnisse</u>:

Das Verhalten sollte konsistent sein.

<u>Tatsächliche Ergebnisse</u>:

Wenn Sie nur eine zusätzliche Website-, Store- und Store-Ansicht erstellen, kann der Benutzer mit eingeschränkten Administratorrechten das Unternehmen, den freigegebenen Katalog und beide freigegebenen Kataloge in der Produktliste sehen. Mit der obigen Einrichtung kann der eingeschränkte Administrator das neue Unternehmen oder den benutzerdefinierten freigegebenen Katalog nicht sehen, und in der Produktliste wird nur der standardmäßige freigegebene Katalog angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
