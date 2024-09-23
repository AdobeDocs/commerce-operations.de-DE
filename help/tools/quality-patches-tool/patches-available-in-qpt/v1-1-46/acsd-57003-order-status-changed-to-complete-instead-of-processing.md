---
title: '"ACSD-57003: Der Bestellstatus ändert sich in *Complete*, anstatt zu *Processing* zu wechseln.'
description: Wenden Sie den Patch ACSD-57003 an, um das Adobe Commerce-Problem zu beheben, bei dem der Auftragsstatus zu *Complete* geändert wird, anstatt zu *Processing* zu wechseln.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-57003: Der Bestellstatus ändert sich in *Complete*, anstatt in *Processing* zu wechseln.

Der Patch ACSD-57003 behebt das Problem, bei dem der Auftragsstatus zu *Complete* geändert wird, anstatt zu *Processing* zu wechseln. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.46 installiert ist. Die Patch-ID ist ACSD-57003. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Bestellstatus ändert sich in *Complete*, anstatt in *Processing* zu wechseln, wenn eine Bestellung teilweise zurückerstattet und teilweise versendet wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit zwei konfigurierbaren Produkten.
1. Rechnungsstellung für alle Artikel.
1. Verschicken Sie nur den ersten Artikel.
1. Sie können nur für das ausgelieferte Element (*erster Eintrag*) ein Kreditmemo zurückerstatten/erstellen.
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Auftragsstatus sollte sich im Status _Verarbeitung_ befinden.

<u>Tatsächliche Ergebnisse</u>:

Der Auftragsstatus ändert sich in *Abgeschlossen* , nachdem ein Kreditmemo für das teilweise ausgelieferte Element erstellt wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
