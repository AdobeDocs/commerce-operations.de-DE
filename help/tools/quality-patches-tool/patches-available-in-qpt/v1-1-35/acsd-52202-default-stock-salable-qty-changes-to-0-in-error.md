---
title: '"ACSD-52202: Die standardmäßige Lagerverkaufsmenge ändert sich zu "0"mit Fehler, wenn der nicht standardmäßige Lagerbestand auf 0 qty in der Reihenfolge festgelegt ist."'
description: Wenden Sie den Patch ACSD-52202 an, um das Adobe Commerce-Problem zu beheben, bei dem eine standardmäßige Lagerverkaufsmenge fehlerhaft auf 0 geändert wird, wenn der nicht standardmäßige Lagerbestand in einer Bestellung auf 0 Menge eingestellt ist.
feature: Inventory, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52202: Die standardmäßige Lagerverkaufsmenge ändert sich zu 0, wenn der nicht standardmäßige Lagerbestand in einer Bestellung auf 0 Menge eingestellt ist.

Der Patch ACSD-52202 behebt das Problem, dass eine standardmäßige Lagerverkaufsmenge (qty) zu 0 fehlerhaft wird, wenn ein nicht standardmäßiges Lager in einer Bestellung auf 0 Menge eingestellt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52202. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die standardmäßige Lagerverkaufsmenge ändert sich zu 0, wenn der nicht standardmäßige Bestand in einer Bestellung auf 0 Menge eingestellt ist.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei [!DNL Admin] an.
1. Erstellen Sie **website2**.
1. Erstellen Sie eine benutzerdefinierte **Quelle2**.
1. Erstellen Sie benutzerdefiniertes **stock2**.
1. Weisen Sie **source2** und **stock2** **website1** sowie die Standardquelle und den Standardbestand der Standardwebsite zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie **qty** = *10* für die Standardquelle und **qty** = *1* für die Quelle **source2** zu.
1. Legen Sie eine Bestellung mit **qty** = *1* für **website2** auf.
1. Erstellen Sie eine Rechnung und eine Sendung.
1. Überprüfen Sie die einfache Produktmenge **Verkaufsmenge**.

<u>Erwartete Ergebnisse</u>:

Die **verkaufbare Menge** = *10* für **source2**.

<u>Tatsächliche Ergebnisse</u>:

Die **verkaufbare Menge** = *0* für beide Quellen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
