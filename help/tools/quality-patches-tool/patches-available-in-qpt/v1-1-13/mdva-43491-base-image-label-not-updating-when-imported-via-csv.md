---
title: 'MDVA-43491: Basisbildbeschriftung wird beim Import über CSV nicht aktualisiert'
description: Der Patch MDVA-43491 behebt das Problem, dass „base_image_label“ beim Import über eine CSV-Datei für eine Multi-Store-Website nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43491. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491: Basisbildbeschriftung wird beim Import über CSV nicht aktualisiert

Der Patch MDVA-43491 behebt das Problem, dass der `base_image_label` beim Import über eine CSV-Datei für eine Multi-Store-Website nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43491. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der `base_image_label` wird beim Import mit einer CSV-Datei für eine Website mit mehreren Stores nicht aktualisiert.

<u>Voraussetzungen</u>:

Eine oder mehrere vorhandene, nicht standardmäßige Websites, Stores und Store-Ansichten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues Produkt.

   * Laden Sie ein Bild hoch.
   * Weisen Sie das Produkt den neu erstellten Websites zu.

1. Exportieren Sie das Produkt als CSV.
1. Aktualisieren Sie die `base_image_label` für jede Store-Ansicht, indem Sie die Standardzeile der CSV-Datei duplizieren.
1. Importieren Sie die CSV-Datei. Dadurch werden die Beschriftungen für jeden Shop korrekt aktualisiert, was auf der Seite zur Produktbearbeitung auf der Registerkarte **Bilder und Videos** überprüft werden kann.
1. Exportieren Sie die CSV-Datei erneut und aktualisieren Sie die `base_image_label` Spalte mit anderen Werten.
1. Importieren Sie die CSV-Datei erneut.
1. Öffnen Sie das Produkt in der Admin Console und überprüfen Sie, ob die Bezeichnung für jede Shop-Ansicht aktualisiert wurde.

<u>Erwartete Ergebnisse</u>:

Alt-Text (Bildbeschriftung) wird mit dem speicherspezifischen Wert gemäß CSV-Datei aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Alt-Text (Bildbeschriftung) wird in der CSV-Datei nicht mit dem `base_image_label` Wert aktualisiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
