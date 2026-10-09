---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.72 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.72

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.72 verfügbaren Patches behoben wurden.

QPT v1.1.72 enthält die folgenden Patches:

1. **ACSD-66807**: `report_viewed_product_index` Tabelle zeigt eine falsche Anzahl von Produktseitenansichten an.
1. **ACSD-67187**: Admin-Benutzer, die auf nicht standardmäßige Websites beschränkt sind, sehen den Fehler *&quot;* Erstellen Sie mindestens einen öffentlichen freigegebenen Katalog, um fortzufahren* und können nicht auf die Schaltfläche &quot;**[!UICONTROL Add New Company]**&quot; im Firmenraster zugreifen.
1. **ACSD-67383**: Fehler bei der Anmeldung als Kunde mit zwei Unternehmensadministratorkonten in derselben Sitzung.
1. **ACSD-67424**: `updated_at` Wert in der `GET /carts/search` [!DNL REST] API-Antwort stimmt nicht mit dem in der **[!UICONTROL Admin panel]** angezeigten Wert überein, wenn verhandelbare Anführungszeichen verwendet werden.
1. **ACSD-67518**: Die erweiterte Berichterstellung generiert doppelte Kopfzeilen, wenn die Zeilenanzahl die Batch-Größe überschreitet.
1. **ACSD-67639**: Das Erstellen einer Gutschrift schlägt für Bundle-Produkte fehl, wobei **[!UICONTROL Dynamic Price]** auf &quot;*&quot;*.
1. **ACSD-67696**: `media_gallery` Einträge werden nach einer Cache-Leerung nicht im Warenkorb-GraphQL-Produktknoten zurückgegeben.
1. **ACSD-67941**: GraphQL-Anfragen mit unbekannten Filternamen verursachen PHP-Ausnahmeprotokolle.
1. **ACSD-67946**: Bei der Aktualisierung des Warenkorbs werden doppelte Fehlerbanner angezeigt.
1. **ACSD-68011**: Nicht vorhandene SKUs, die über die API /V1/sharedCatalog/:id/assignProducts dem freigegebenen Katalog zugewiesen sind.
1. **ACSD-68040**: Frontend-Suchseite verlangsamt sich auf [!DNL MariaDB] 10.6 mit großem Verlauf.
1. **ACSD-68064**: Doppelte Einträge, die bei geplanten Aktualisierungen in Umgebungen mit tief verschachtelten Kategorien erstellt werden.
1. **ACSD-68092**: Bundle-Produktoptionen gehen nach mehreren Speichervorgängen verloren, da zwischen geplanten Aktualisierungen und Basisproduktdaten nicht ordnungsgemäß synchronisiert wird.
1. **ACSD-68118**: `customerCart` [!DNL GraphQL] Abfrage gibt falsche Produktattributwerte für die Store-Ansicht zurück.


Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
