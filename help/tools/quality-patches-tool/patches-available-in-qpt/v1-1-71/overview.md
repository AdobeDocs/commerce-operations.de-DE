---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.71 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '185'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.71

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.71 verfügbaren Patches behoben wurden.

QPT v1.1.71 enthält die folgenden Patches:


* **ACSD-60624**: Das Hochladen eines Bildes schlägt aufgrund leerer Inhalte in den Abschnitten „Bild“, „Banner“ und „Schieberegler“ in [!DNL Page Builder] fehl
* **ACSD-67089**: Paginierungsproblem in der `inventory/export-stock-salable-qty`-API, das `total_count` fälschlicherweise auf die Seitengröße beschränkt.
* **ACSD-67093**: Beim Abrufen von Bestellungen über [!DNL GraphQL] mithilfe des Datumsbereichsfilters werden falsche Ergebnisse zurückgegeben.
* **ACSD-67459**: Produkte mit Beschreibungen, die länger als 65.536 Zeichen sind, können nicht importiert werden.
* **ACSD-67603**: Sitemap-Generierung lange Verarbeitungszeiten für Produkte mit aktivierter Bildeinbindung
* **ACSD-67643**: Doppelte Einträge werden bei geplanten Aktualisierungen in Umgebungen mit einer hohen Anzahl verschachtelter Kategorien erstellt.
* **ACSD-67652**: Der Status des Bundle-Produkts wird in [!DNL GraphQL]-Aufrufen als nicht vorrätig zurückgegeben, auch wenn untergeordnete und übergeordnete Produkte auf Lager sind.
* **ACSD-67904**: Bestellungen können nicht aufgegeben werden, wenn der Stadtname Ziffern (0-9), kaufmännisches Und-Zeichen (&amp;), Punkte (.) oder Klammern () enthält.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
