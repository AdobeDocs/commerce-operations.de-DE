---
title: 'MDVA-43824: Fehler bei Aktion zum Stornieren der Bestellung: „Sie haben das Element nicht storniert“'
description: 'Der Patch MDVA-43824 löst das Problem, dass die Aktion zum Stornieren der Bestellung mit folgendem Fehler fehlgeschlagen ist: * Sie haben den Artikel nicht storniert*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43824. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.'
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824: Fehler bei Aktion zum Stornieren der Bestellung: „Sie haben das Element nicht storniert“

Der MDVA-43824 Patch löst das Problem, dass die Aktion zum Stornieren der Bestellung mit dem Fehler fehlgeschlagen ist: *Sie haben den Artikel nicht*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43824. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestellung eines angemeldeten Kunden kann nicht storniert werden. Die Aktion zum Stornieren der Bestellung schlug mit dem folgenden Fehler fehl:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Verkaufsregel (Coupontyp ist entweder „Spezifischer Coupon“ oder „Kein Coupon„).
1. Gehen Sie zur Storefront und melden Sie sich als Kunde an und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Wechseln Sie zum Warenkorb und wenden Sie die Warenkorb-Preisregel an, wenn die Warenkorb-Preisregel einen Coupon als „Bestimmter Coupon“ hat. Die Preisregel für den Warenkorb sollte erfolgreich angewendet werden.
1. Zur Kasse gehen und die Bestellung mit jeder Zahlungsmethode aufgeben.
1. Gehen Sie zu Commerce Admin > **Vertrieb** > **Bestellungen**.
1. Öffnen Sie die in Schritt 4 aufgegebene Bestellung.
1. Klicken Sie auf die Schaltfläche **Abbrechen**.

<u>Erwartete Ergebnisse</u>:

Die Bestellung wurde ohne Fehler erfolgreich storniert.

<u>Tatsächliche Ergebnisse</u>:

Die Aktion des Auftragsstornierens ist mit dem folgenden Fehler fehlgeschlagen: *Sie haben den Artikel nicht storniert.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
