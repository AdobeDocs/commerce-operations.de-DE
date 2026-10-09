---
title: Einrichten des Entwicklungssystems
description: Erfahren Sie, wie Sie ein Entwicklungssystem für das Commerce-Programm einrichten.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '131'
ht-degree: 0%
---
# Einrichten des Entwicklungssystems

Sie können über eine beliebige Anzahl von Entwicklungssystemen verfügen, sofern Folgendes für alle gilt:

- Auf allen Modellen wird Commerce 2.2 oder höher ausgeführt
- Der gesamte Commerce-Code befindet sich unter der Versionskontrolle im selben Repository wie die Build- und Produktionssysteme
- Jedes Entwicklungssystem sollte entweder den [Standardmodus) ](../bootstrap/application-modes.md#default-mode) den [Entwicklermodus“ ](../bootstrap/application-modes.md#developer-mode)
- Für sie sind der Besitz und die Berechtigungen des Dateisystems festgelegt, wie unter [Voraussetzung für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/technical-details.md) erläutert.
- Stellen Sie sicher, dass Folgendes _der_ ausgeschlossen ist:

  - `vendor` (und Unterverzeichnisse)
  - `generated` (und Unterverzeichnisse)
  - `pub/static` (und Unterverzeichnisse)
  - `app/etc/env.php`

- Stellen Sie sicher, dass `app/etc/config.php` in _Quell_ Code-Verwaltung enthalten ist

Wenn Sie Git verwenden, bietet die `.gitignore`-Datei die meisten der zuvor genannten Funktionen. Siehe die [`.gitignore`-Referenz](../reference/config-reference-gitignore.md).
