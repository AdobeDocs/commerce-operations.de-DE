---
title: 'MDVA-41229: Im Backend verfügbare Bilder werden nach dem Import konfigurierbarer Produkte nicht an der Frontend angezeigt'
description: Der Patch MDVA-41229 behebt das Problem, dass im Backend verfügbare Bilder nach dem Import konfigurierbarer Produkte nicht auf dem Frontend angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41229. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Data Import/Export, Configuration, Products
role: Admin
exl-id: 894fdc5b-545c-4ed8-ae1b-573d1d8d3cd6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# MDVA-41229: Im Backend verfügbare Bilder werden nach dem Import konfigurierbarer Produkte nicht an der Frontend angezeigt

Der Patch MDVA-41229 behebt das Problem, dass im Backend verfügbare Bilder nach dem Import konfigurierbarer Produkte nicht auf dem Frontend angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41229. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2-p2 und 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Im Backend verfügbare Bilder werden nach konfigurierbarem Produktimport nicht auf dem Frontend angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie einen sauberen Adobe Commerce.
1. Fügen Sie ein benutzerdefiniertes Attribut hinzu, indem Sie zu **Stores** > **Attribute** > **Produkt** > **Neues Attribut hinzufügen** mit den unten stehenden Einstellungen navigieren:

   * Eigenschaften:
      * Attributeigenschaften:

         * Standardbezeichnung: Größe festlegen
         * Katalogeingabetyp für Store Owner: Textmuster
         * Erforderliche Werte: nein
         * Update Product Preview Image: Ja

      * Muster verwalten (Werte Ihres Attributs):

        | Ist Standard | Admin Swatch | Administratorbeschreibung | Standardmuster für Store-Ansicht | Standardmäßige Store-Ansichtsbeschreibung |
        |---|---|---|---|---|
        | no | 4 | 4 | 4 | 4 |
        | no | 24 | 24 | 24 | 24 |
        | no | 30 | 30 | 30 | 30 |
        | no | 60 | 60 | 60 | 60 |
        | no | 68 | 68 | 68 | 68 |

      * Erweiterte Attributeigenschaften:

         * Attributcode: set_size
         * Umfang: Global
         * Einzelwert: nein
         * Eingabevalidierung für Store Owner: Keine
         * Zu Spaltenoptionen hinzufügen: Nein
         * Verwendung in Filteroptionen: nein

   * Verwalten von Bezeichnungen:

      * Titel verwalten (Größe, Farbe usw.)

         * Standardspeicheransicht: Größe festlegen

   * Storefront-Eigenschaften:

      * In der Suche verwenden: Ja
      * Suchgewichtung: 1
      * In der erweiterten Suche sichtbar: nein
      * Vergleich auf Storefront: ja
      * Verwendung in der Ebenennavigation: Gefilterbar (mit Ergebnissen)
      * Verwendung in mehrstufiger Navigation mit Suchergebnissen: Ja
      * Verwendung für Bedingungen für Angebotsregeln: nein
      * Auf Katalogseiten in der Storefront sichtbar: ja
      * Wird in der Produktliste verwendet: ja
      * Wird für die Sortierung in der Produktliste verwendet: nein

1. Fügen Sie dieses Attribut zum standardmäßigen Attributsatz in der Produktdetailgruppe hinzu (**Stores** > **Attribute** > **Attributsatz**).
1. Laden Sie Bilder herunter, die in den Ordner var im Stammverzeichnis von Adobe Commerce eingestellt sind.
1. Wechseln Sie zu **System** > **Datenübertragung** > und importieren Sie die Datei mit den folgenden Optionen:

   * Importeinstellungen:

      * Entitätstyp: Produkte

   * Importverhalten:

      * Importverhalten: Hinzufügen/Aktualisieren
      * Validierungsstrategie: Bei Fehler stoppen
      * Anzahl zulässiger Fehler: 1
      * Feldtrennzeichen: `;`
      * Trennzeichen für mehrere Werte: `,`
      * Attributwertkonstante: EMPTYVALUE
      * Feldeinteilung: deaktiviert

   * Zu importierende Datei:

      * Datei zum Importieren auswählen
      * Verzeichnis der Bilddateien: leer lassen

1. Gehen Sie zur Storefront zur Seite `/product-set.html` und wechseln Sie zwischen verschiedenen Set-Größen. Für Set Size 24 gibt es keine Galerie.

<u>Erwartete Ergebnisse</u>:

Die Galerie für alle einfachen Produkte innerhalb eines konfigurierbaren Produkts ist mit allen zugehörigen Bildern sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Es gibt keine Galerie für die Produkte.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
