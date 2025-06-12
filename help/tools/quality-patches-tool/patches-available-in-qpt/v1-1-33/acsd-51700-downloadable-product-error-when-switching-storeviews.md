---
title: 'ACSD-51700: Fehler beim Wechseln der Store-Ansichten auf der herunterladbaren Produktbearbeitungsseite'
description: Wenden Sie den Patch ACSD-51700 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Wechseln der Store-Ansichten auf einer herunterladbaren Produktbearbeitungsseite in der Admin Console ein Fehler auftritt.
feature: Products
role: Admin
exl-id: dd3da026-ac72-440c-8632-8a3ca27fc134
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51700: Fehler beim Wechseln der Store-Ansichten auf der herunterladbaren Produktbearbeitungsseite

Mit dem Patch ACSD-51700 wird das Problem behoben, dass beim Wechsel der Store-Ansichten auf einer herunterladbaren Produktbearbeitungsseite in der Admin Console ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51700. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

## Problem

Beim Wechseln der Store-Ansichten auf einer herunterladbaren Produktbearbeitungsseite in der Admin-Instanz tritt ein Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein herunterladbares Produkt mit Namen, [!DNL SKU] und Preis. Fügen Sie keine Links hinzu und speichern Sie das Produkt.
1. Von allen Store-Ansichten zur Standard-Store-Ansicht wechseln.
1. Erstellen Sie einen Link für das herunterladbare Produkt und speichern Sie es.
1. Wechseln Sie von der standardmäßigen Store-Ansicht zu allen Store-Ansichten.

<u>Erwartete Ergebnisse</u>:

Die verknüpften Produkte sind sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird angezeigt:

*Veraltete Funktionalität: number_format(): Die Übergabe von null an den Parameter #1 ($num) vom Typ „float“ ist in vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php in Zeile 228 veraltet*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
