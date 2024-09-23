---
title: "ACSD-49392: Auftragsstatus ändert sich nach teilweiser Rückerstattung zu schließen"
description: Wenden Sie den Patch ACSD-49392 an, um das Adobe Commerce-Problem zu beheben, bei dem der Auftragsstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt zu "geschlossen"geändert wird.
feature: Orders
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49392: Auftragsstatus wird nach teilweiser Rückerstattung geschlossen

Der Patch ACSD-49392 behebt das Problem, dass sich der Bestellstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in &quot;geschlossen&quot;ändert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID lautet ACSD-49392. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4 und 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Änderung des Bestellstatus nach teilweiser Rückerstattung für ein gebündeltes Produkt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Adobe Commerce an und erstellen Sie ein beliebiges gebündeltes Produkt oder verwenden Sie das vorhandene gebündelte Produkt.
1. Bestellen Sie mit diesem gebündelten Produkt eine Menge größer als 1.
1. Wechseln Sie zu &quot;admin&quot;, öffnen Sie die in Schritt 2 erstellte Bestellung über **[!UICONTROL Sales]** > **[!UICONTROL Order]** und erstellen Sie eine Rechnung. Beobachten Sie den Bestellstatus. Es wird verarbeitet.
1. Erstellen Sie ein Teil-Credit Memo (keine Rückerstattung für alle Produkte im Bundle).
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>

Nachdem Sie ein Teil-Kreditmemo für das gebündelte Produkt erstellt haben, wird der Auftragsstatus verarbeitet.

<u>Tatsächliche Ergebnisse</u>

Nach der Erstellung eines Teilgutschrift-Memos für das gebündelte Produkt ist der Auftragsstatus abgeschlossen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
