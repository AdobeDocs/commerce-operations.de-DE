---
title: Einrichten des Entwicklungssystems
description: Erfahren Sie, wie Sie ein Entwicklungssystem für die Commerce-Anwendung einrichten.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Einrichten des Entwicklungssystems

Sie können über eine beliebige Anzahl von Entwicklungssystemen verfügen, sofern Folgendes für alle gilt:

- Sie alle führen Commerce 2.2 oder höher aus.
- Der gesamte Commerce-Code unterliegt der Quell-Code-Kontrolle im selben Repository wie die Build- und Produktionssysteme
- Jedes Entwicklungssystem sollte entweder [Standardmodus](../bootstrap/application-modes.md#default-mode) oder [Entwicklermodus](../bootstrap/application-modes.md#developer-mode)
- Sie verfügt über Dateisystemeigentümer und -berechtigungen, wie hier beschrieben: [Voraussetzungen für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/technical-details.md).
- Stellen Sie sicher, dass alle folgenden Elemente _ausgeschlossen_ von der Quell-Code-Verwaltung:

   - `vendor` Verzeichnis (und Unterverzeichnisse)
   - `generated` Verzeichnis (und Unterverzeichnisse)
   - `pub/static` Verzeichnis (und Unterverzeichnisse)
   - `app/etc/env.php` file

- Stellen Sie sicher `app/etc/config.php` is _enthalten_ in der Quellcodeverwaltung

Wenn Sie Git verwenden, wird die `.gitignore` -Datei stellt die meisten der vorangehenden bereit. Siehe [`.gitignore` reference](../reference/config-reference-gitignore.md).
