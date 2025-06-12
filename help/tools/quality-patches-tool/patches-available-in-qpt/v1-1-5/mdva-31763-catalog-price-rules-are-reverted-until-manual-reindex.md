---
title: 'MDVA-31763: Katalogpreisregeln werden zurückgesetzt, bis eine manuelle Neuindizierung erfolgt'
description: Der Patch MDVA-31763 löst das Problem, dass Katalogpreisregeln bis zur manuellen Neuindizierung zurückgesetzt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-31763. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763: Katalogpreisregeln werden zurückgesetzt, bis eine manuelle Neuindizierung erfolgt

Der Patch MDVA-31763 löst das Problem, dass Katalogpreisregeln bis zur manuellen Neuindizierung zurückgesetzt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-31763. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn `catalogrule_product` partielle Indexer für konfigurierbare Produkte ausgeführt wird, verschwinden Katalogregeln.

<u>Schritte zur Reproduktion</u>:

1. Beim Admin-Backend anmelden.
1. Navigieren Sie **Stores** > **Attribute** > **Produkt** und suchen Sie nach dem Attribut „hersteller“.
   * Fügen Sie einige Optionen hinzu und setzen Sie „Für Promo-Regelbedingungen verwenden“ auf *Ja*.
1. Navigieren Sie **Stores** > **Attribute** > **Attributsätze**.
   * Wählen Sie das Standardattribut aus und fügen Sie ihm das Attribut „produzent“ hinzu.
1. Erstellen Sie ein konfigurierbares Produkt mit einigen Varianten.
1. Legen Sie den Attributwert „Hersteller“ für das zuvor erstellte konfigurierbare Produkt fest.
1. Erstellen von Katalogregeln:
   * Aktiv = Ja
   * Websites = Haupt-Website
   * Kundengruppen = NICHT ANGEMELDET
   * Bedingungen: Hersteller = \&lt;ausgewählter Wert für konfigurierbares Produkt>
   * Aktionen: Beliebiger Rabatt
1. Führen Sie einen vollständigen Index durch.
1. Überprüfen Sie den Produktpreis auf PDP und stellen Sie sicher, dass der Preis korrekt ist.
1. Aktualisieren Sie das Attribut „weight“ des erstellten konfigurierbaren Produkts.
1. Überprüfen Sie den Produktpreis auf PDP.

<u>Erwartete Ergebnisse</u>:

Die Katalogpreisregeln für konfigurierbare Produkte werden während der partiellen Neuindizierung nicht entfernt.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogpreisregeln für konfigurierbare Produkte werden während der partiellen Neuindizierung nicht mehr angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
