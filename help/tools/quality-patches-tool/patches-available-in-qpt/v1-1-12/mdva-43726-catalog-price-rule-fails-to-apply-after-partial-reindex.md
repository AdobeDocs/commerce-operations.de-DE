---
title: 'MDVA-43726: Katalogpreisregel wird nach teilweiser Neuindizierung nicht angewendet'
description: Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer teilweisen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726: Katalogpreisregel wird nach teilweiser Neuindizierung nicht angewendet

Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer teilweisen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die auf der Attributübereinstimmung auf Speicherebene basiert, kann nach einer teilweisen Neuindizierung nicht angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie den Indexermodus auf „Planmäßig ausgeführt“.
1. Erstellen Sie zwei konfigurierbare Produktattribute. Beispiel: Farbe (visuelles Farbfeld) und Größe (Textfeld).
1. Erstellen Sie ein konfigurierbares Produkt mit beiden in Schritt 2 erstellten Attributen.
1. Erstellen Sie nach dem Erstellen der Produkte **Attribut** Ja/Nein“ und machen Sie es in den Regelbedingungen sichtbar.
1. Fügen Sie dieses Attribut zum Standardattributsatz hinzu.
1. Erstellen Sie eine Katalogpreisregel, die angewendet werden soll, wenn dieses Attribut auf &quot;**&quot;** ist.
1. Öffnen Sie eines der einfachen Produkte im Zusammenhang mit dem konfigurierbaren Produkt.
1. Ändern Sie den Bereich für die Speicheransicht und aktualisieren Sie den Attributwert auf **Ja**.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis am Frontend.
1. Führen Sie eine vollständige Neuindizierung aus. Überprüfen Sie erneut den Preis am Frontend.
1. Aktualisieren Sie die konfigurierbare Produktkategorie.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis erneut am Frontend.

<u>Erwartete Ergebnisse</u>:

Die Katalogregel gilt korrekt ohne vollständige Neuindizierung mithilfe von inkrementellen Indexern.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogregel gilt nicht, ohne eine vollständige Neuindizierung auszuführen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
