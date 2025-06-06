---
title: 'ACSD-65684: Das Upgrade von Magento_Company in B2B 1.5.2 ist mit über 100.000 Datensätzen in Company_Structure sehr langsam'
description: Wenden Sie den Patch ACSD-65684 an, um das Adobe Commerce-Problem zu beheben, bei dem das Upgrade des Magento_Company-Moduls in B2B 1.5.2 aufgrund der Verarbeitung einer großen Anzahl von Datensätzen (~100.000+) in der Tabelle company_structure zu lange dauert.
feature: B2B
role: Admin, Developer
source-git-commit: dbf1bf3483aa7e52f5d1c950ab82f504c44fc989
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACSD-65684: Die Aktualisierung von `Magento_Company` in [!DNL B2B] 1.5.2 ist mit über 100.000 Datensätzen in `company_structure` langsam

Mit dem Patch ACSD-65684 wird ein Leistungsproblem behoben, bei dem das Upgrade des `Magento_Company`-Moduls in [!DNL B2B] 1.5.2 zu lange dauert, wenn mehr als 100.000 Datensätze in der `company_structure` verarbeitet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-65684. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce B2B (alle Bereitstellungsmethoden) 1.5.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce B2B (alle Bereitstellungsmethoden) 1.5.2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Leistungsproblem, bei dem das Upgrade des `Magento_Company`-Moduls in [!DNL B2B] 1.5.2 zu lange dauert, wenn mehr als 100.000 Datensätze in der `company_structure` verarbeitet werden.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce 2.4.7-p4 mit [!DNL B2B].
1. Fügen Sie 100.000 Datensätze zu `company_structure` Tabelle hinzu.
1. Aktualisieren Sie auf Adobe Commerce 2.4.7-p5 und das neueste [!DNL B2B] (1.5.2).
1. Patch für ACSD-65540 anwenden.
1. Durchgang:

```
bin/magento setup:upgrade
```

<u>Erwartete Ergebnisse</u>:

`setup:upgrade` wird in angemessener Zeit abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

`setup:upgrade` dauert zu lange.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
