---
title: Einrichten des Entwicklungssystems
description: Erfahren Sie, wie Sie ein Entwicklungssystem für die Commerce-Anwendung einrichten.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Einrichten des Entwicklungssystems

Sie können über eine beliebige Anzahl von Entwicklungssystemen verfügen, sofern Folgendes für alle gilt:

- Sie führen alle Commerce 2.2 oder höher aus.
- Der gesamte Commerce-Code wird im selben Repository wie die Build- und Produktionssysteme unter Quellcode gesteuert
- Jedes Entwicklungssystem sollte entweder den [Standardmodus](../bootstrap/application-modes.md#default-mode) oder den [Entwicklermodus](../bootstrap/application-modes.md#developer-mode) verwenden
- Sie verfügt über Dateisystemeigentum und -berechtigungen, wie in [Voraussetzung für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/technical-details.md) beschrieben.
- Stellen Sie sicher, dass alle folgenden Elemente _ausgeschlossen_ aus der Quell-Code-Verwaltung sind:

   - Ordner `vendor` (und Unterverzeichnisse)
   - Ordner `generated` (und Unterverzeichnisse)
   - Ordner `pub/static` (und Unterverzeichnisse)
   - Datei `app/etc/env.php`

- Stellen Sie sicher, dass `app/etc/config.php` _included_ in der Quell-Code-Verwaltung ist.

Wenn Sie Git verwenden, stellt die Datei `.gitignore` die meisten der vorherigen bereit. Siehe [`.gitignore` reference](../reference/config-reference-gitignore.md).
