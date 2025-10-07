---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.71  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4660942d90435eaeb6960206c29733bed6453b6a
workflow-type: tm+mt
source-wordcount: '181'
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
