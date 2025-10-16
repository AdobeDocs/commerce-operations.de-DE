---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.72  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 89b78f72fce3f65b8f282038cc4e2ef0f190bda3
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.72

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.72 verfügbaren Patches behoben wurden.

QPT v1.1.72 enthält die folgenden Patches:
1. **ACSD-68040**: Die Frontend-Suchseite verschlechtert sich unter [!DNL MariaDB] 10.6 und 11.4 mit vielen historischen Suchanfragen.
1. **ACSD-67941**: GraphQL-Anfragen mit unbekannten Filternamen verursachen PHP-Ausnahmeprotokolle.
1. **ACSD-68064**: Das Erstellen geplanter Aktualisierungen führt zu doppelten Einträgen in Umgebungen mit einer hohen Anzahl verschachtelter Kategorien.
1. **ACSD-66807**: `report_viewed_product_index` Tabelle zeigt eine falsche Anzahl von Produktseitenansichten an.
1. **ACSD-67383**: Die Anmeldung als Kunde mit zwei Unternehmensadministratorkonten in derselben Sitzung verursacht den Fehler *Keine solche Entität mit cartId*.
1. **ACSD-67518**: Die erweiterte Berichterstellung generiert doppelte Kopfzeilen, wenn die Zeilenanzahl die Batch-Größe überschreitet.
1. **ACSD-67639**: Das Erstellen einer Gutschrift schlägt für Bundle-Produkte fehl, wobei **[!UICONTROL Dynamic Price]** auf &quot;*&quot;*.
1. **ACSD-67696**: `media_gallery` Einträge werden nach einer Cache-Leerung nicht im Warenkorb-GraphQL-Produktknoten zurückgegeben.
1. **ACSD-67946**: Bei Warenkorbaktualisierungen werden doppelte Fehlerbanner angezeigt.
1. **ACSD-68011**: Nicht vorhandene SKUs können über die `/V1/sharedCatalog/:id/assignProducts` [!DNL REST]-API einem freigegebenen Katalog zugewiesen werden.
1. **ACSD-68118**: `customerCart` GraphQL-Abfrage gibt Produktattributwerte zurück, die nicht die Store-Kopfzeile widerspiegeln, was zu einer inkonsistenten Lokalisierung führt.
1. **ACSD-68092**: Bundle-Produktoptionen gehen nach mehreren Speichervorgängen verloren, da zwischen geplanten Aktualisierungen und Basisproduktdaten nicht ordnungsgemäß synchronisiert wird.
1. **ACSD-67424**: `updated_at` Wert in der `GET /carts/search` [!DNL REST] API-Antwort stimmt nicht mit dem in der **[!UICONTROL Admin panel]** angezeigten Wert überein, wenn verhandelbare Anführungszeichen verwendet werden.
1. **ACSD-67187**: Admin-Benutzer, die auf nicht standardmäßige Websites beschränkt sind, sehen den Fehler *&quot;*Erstellen Sie mindestens einen öffentlichen freigegebenen Katalog, um fortzufahren* und können nicht auf die Schaltfläche &quot;**[!UICONTROL Add New Company]**&quot; im Firmenraster zugreifen.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
