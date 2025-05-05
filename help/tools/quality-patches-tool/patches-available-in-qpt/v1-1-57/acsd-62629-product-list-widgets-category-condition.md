---
title: 'ACSD-62629: Die Produktliste in Widgets zeigt falsche Kategorien an'
description: Wenden Sie den Patch ACSD-62629 an, um das Adobe Commerce-Problem zu beheben, bei dem eine in Widgets verwendete Produktliste die Kategoriebedingung nicht erfüllt.
feature: Page Content
role: Admin, Developer
source-git-commit: 6440738bf01a95a2f1e666826685d325bf393249
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-62629: Die Produktliste in Widgets zeigt falsche Kategorien an

Der Patch ACSD-62629 behebt das Problem, dass die in Widgets verwendete Produktliste die Kategoriebedingung nicht respektiert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62629. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die in Widgets verwendete Produktliste berücksichtigt die Kategoriebedingung nicht.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine [!UICONTROL simple product] mit dem Namen TEST und fügen Sie sie der Kategorie 1 hinzu.
1. Erstellen Sie eine Staging-Aktualisierung ohne Enddatum für das Testprodukt. Warten Sie, bis die Aktualisierung aktiv wird.
1. Erstellen Sie eine [!UICONTROL configurable product] mit dem Namen TEST 2 mit zwei untergeordneten Produkten und fügen Sie sie der Kategorie 2 hinzu.
1. Erstellen Sie eine weitere [!UICONTROL simple product] mit dem Namen TEST 5 und fügen Sie sie der Kategorie 1 hinzu.
1. Führen Sie eine vollständige Neuindizierung aus.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** und bearbeiten Sie die Startseite.
1. Fügen Sie ein [!UICONTROL Products]-Widget hinzu, dessen *[!UICONTROL Appearance]* auf *[!UICONTROL Product Carousel]* und dessen Kategorie 2 eingestellt *[!UICONTROL Category]*. Speichern Sie die Seite.
1. Wechseln Sie zum Frontend und öffnen Sie die Startseite.

<u>Erwartete Ergebnisse</u>:

Nur das (konfigurierbare) Produkt „TEST 2“ sollte auf der Seite vorhanden sein.

<u>Tatsächliche Ergebnisse</u>:

Auf der Seite sind sowohl das Produkt TEST 5 (einfach) als auch das Produkt TEST 2 (konfigurierbar) vorhanden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
