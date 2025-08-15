---
title: 'MDVA-38799: Herunterladbare Produkte werden nach dem Erstellen eines Staging-Updates nicht gespeichert'
description: Der Patch MDVA-38799 löst das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38799. Beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: Herunterladbare Produkte werden nach dem Erstellen eines Staging-Updates nicht gespeichert

Der Patch MDVA-38799 löst das Problem, dass herunterladbare Produkte nach der Erstellung eines Staging-Updates nicht gespeichert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38799. Beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Herunterladbare Produkte werden nach der Erstellung eines Staging-Updates nicht gespeichert. Benutzende erhalten die folgende Fehlermeldung: *Das herunterladbare Beispiel bezieht sich nicht auf das Produkt. Überprüfen Sie den Link und versuchen Sie es erneut*.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie **Katalog** > **Produkte**.
1. Klicken Sie auf das Dropdown-Menü neben Produkt hinzufügen und wählen Sie Herunterladbares Produkt aus.
   * Geben Sie den Namen, die SKU, den Preis und die Menge des Produkts ein.
1. Scrollen Sie nach unten zur Seite Herunterladbare Informationen .
1. Klicken Sie unter „Samples **auf „Link hinzufügen**.
   * Füllen Sie den Titel aus und laden Sie die Datei hoch (der Dateityp spielt keine Rolle).
1. Klicken Sie **Speichern**. Sie erhalten die folgende Meldung: *Sie haben das Produkt gespeichert*.
1. Klicken Sie **oben auf** Seite auf „Neues Update planen“.
   * Geben Sie den Aktualisierungsnamen sowie das legale Start- und Enddatum ein.
1. Klicken Sie **Staging** Update auf „Speichern“.
1. Klicken Sie **Produkt** Speichern“.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die Fehlermeldung: *Das herunterladbare Beispiel bezieht sich nicht auf das Produkt. Überprüfen Sie den Link und versuchen Sie es erneut*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
