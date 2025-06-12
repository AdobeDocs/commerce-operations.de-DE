---
title: 'MDVA-41229: Im Backend verfügbare Bilder werden nach dem Import konfigurierbarer Produkte nicht im Frontend angezeigt'
description: Der Patch MDVA-41229 löst das Problem, dass im Backend verfügbare Bilder nach dem Import konfigurierbarer Produkte nicht im Frontend angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41229. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Data Import/Export, Configuration, Products
role: Admin
exl-id: 894fdc5b-545c-4ed8-ae1b-573d1d8d3cd6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# MDVA-41229: Im Backend verfügbare Bilder werden nach dem Import konfigurierbarer Produkte nicht im Frontend angezeigt

Der Patch MDVA-41229 löst das Problem, dass im Backend verfügbare Bilder nach dem Import konfigurierbarer Produkte nicht im Frontend angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41229. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2-p2 und 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Im Backend verfügbare Bilder werden nach dem konfigurierbaren Produktimport nicht im Frontend angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine saubere Adobe Commerce.
1. Fügen Sie ein benutzerdefiniertes Attribut hinzu, indem Sie zu **Stores** > **Attribute** > **Produkt** > **Neues Attribut hinzufügen** mit den folgenden Einstellungen wechseln:

   * Eigenschaften:
      * Attributeigenschaften:

         * Standardbezeichnung: Größe festlegen
         * Katalogeingabetyp für Store-Inhaber: Textmuster
         * Erforderliche Werte: Nein
         * Produktvorschau-Bild aktualisieren: Ja

      * Farbfeld verwalten (Werte Ihres Attributs):

        | Ist Standard | Admin-Farbfeld | Administratorbeschreibung | Standard-Farbfeld für Store-Ansicht | Beschreibung der Standardspeicheransicht |
        |---|---|---|---|---|
        | Nein | 4 | 4 | 4 | 4 |
        | Nein | 24 | 24 | 24 | 24 |
        | Nein | 30 | 30 | 30 | 30 |
        | Nein | 60 | 60 | 60 | 60 |
        | Nein | 68 | 68 | 68 | 68 |

      * Erweiterte Attributeigenschaften:

         * Attributcode: set_size
         * Bereich: Global
         * Eindeutiger Wert: Nein
         * Eingabevalidierung für Store-Inhaber: Keine
         * Zu Spaltenoptionen hinzufügen: Nein
         * Verwendung in Filteroptionen: Nein

   * Verwalten von Kennzeichnungen:

      * Titel verwalten (Größe, Farbe usw.)

         * Standardmäßige Store-Ansicht: Größe festlegen

   * Storefront-Eigenschaften:

      * In Suche verwenden: Ja
      * Suchgewichtung: 1
      * In der erweiterten Suche sichtbar: Nein
      * Vergleichbar auf Storefront: Ja
      * Verwendung in der mehrschichtigen Navigation: Filterbar (mit Ergebnissen)
      * Verwendung in Suchergebnissen - mehrschichtige Navigation: Ja
      * Verwendung für Bedingungen der Promo-Regel: Nein
      * Auf Katalogseiten in der Storefront sichtbar: Ja
      * In der Produktliste verwendet: Ja
      * Wird für die Sortierung in der Produktliste verwendet: Nein

1. Fügen Sie dieses Attribut zum Standardattribut hinzu, das in der Gruppe „Produktdetails“ festgelegt ist (**Stores** > **Attribute** > **Attributsatz**).
1. Laden Sie Bilder herunter, die in den Var-Ordner im Stammverzeichnis von Adobe Commerce festgelegt wurden.
1. Wechseln Sie zu **System** > **Datenübertragung** und importieren Sie die Datei mit den folgenden Optionen:

   * Importeinstellungen:

      * Entitätstyp: Produkte

   * Importverhalten:

      * Importverhalten: Hinzufügen/Aktualisieren
      * Validierungsstrategie: Bei Fehler anhalten
      * Anzahl der zulässigen Fehler: 1
      * Feldtrennzeichen: `;`
      * Trennzeichen für mehrere Werte: `,`
      * Konstanter Attributwert: EMPTYVALUE
      * Felder in der Einschließung: deaktiviert

   * Zu importierende Datei:

      * Zu importierende Datei auswählen
      * Dateiordner für Bilder: Leer lassen

1. Wechseln Sie zur Storefront, um `/product-set.html` Seite zu öffnen und zwischen verschiedenen Set-Größen zu wechseln. Für die Größe 24 festlegen wird es keine Galerie geben.

<u>Erwartete Ergebnisse</u>:

Die Galerie für alle einfachen Produkte innerhalb eines konfigurierbaren Produkts ist mit allen zugehörigen Bildern sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Es gibt keine Galerie für die Produkte.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
