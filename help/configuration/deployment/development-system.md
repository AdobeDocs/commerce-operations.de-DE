---
title: Einrichten des Entwicklungssystems
description: Erfahren Sie, wie Sie ein Entwicklungssystem für die Commerce-Anwendung einrichten.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
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

- Stellen Sie sicher `app/etc/config.php` is _enthalten_ in der Quell-Code-Verwaltung

Wenn Sie Git verwenden, wird die `.gitignore` -Datei stellt die meisten der vorangehenden bereit. Siehe [`.gitignore` reference](../reference/config-reference-gitignore.md).
