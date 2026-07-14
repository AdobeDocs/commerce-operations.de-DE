---
title: '[!DNL Commerce Version Tool] Versionshinweise'
description: Erfahren Sie mehr  [!DNL Commerce Version Tool]  Versionen, einschließlich neuer Patch-Statusberichte, des CVE-Schutzstatus, der CSV-Ausgabe und des Cache-Verhaltens.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# [!DNL Commerce Version Tool] Versionshinweise

In diesen Versionshinweisen werden Aktualisierungen für [!DNL Commerce Version Tool] ([!DNL CVT]) beschrieben.

## Version 1.0.0 — Juni 2026 {#version-1-0-0}

### Neue Funktionen

- **Patch-Statusberichte** - Gibt an, welche monatlichen Adobe Commerce-Sicherheits-Patches angewendet werden, fehlen oder für eine Adobe Commerce-Installation nicht klassifiziert werden konnten.
- **CVE-Schutzstatus** - Ordnet Patch-Ergebnisse den Werten für den jeweiligen CVE-Schutzstatus zu: `PROTECTED`, `VULNERABLE`, `UNKNOWN` und `NOT_APPLICABLE`.
- **Unterstützung mehrerer Komponenten** - Erkennt installierte Adobe Commerce-Komponenten aus `composer.lock`, einschließlich Adobe Commerce Business-to-Business (B2B), Adobe Commerce Page Builder, Adobe Commerce Inventory und anderen Komponenten, die in der Patch-Registrierungsdatei dargestellt werden.
- **JSON- und CSV-**: Bietet standardmäßig JSON-Ausgaben für die programmgesteuerte Nutzung und CSV-Ausgaben für Tabellen, Scanner, Dashboards und Kompatibilitäts-Tools.
- **Offline-freundliches Cacheverhalten** - Zwischenspeichert die Patch-Registrierungsdatei nach jedem erfolgreichen Abrufen lokal. Wenn die Remote-Registrierung nicht verfügbar ist, kann das [!DNL CVT]-Tool die zwischengespeicherte Registrierung mit einer Warnung verwenden.
- **Paketversand** - wird in monatlichen Adobe Commerce-Sicherheits-Patch-Dateien ausgeliefert. Durch Anwenden des Patches wird [!DNL CVT] unter `vendor/bin/patch-status` installiert, ohne dass ein separater Installationsschritt erforderlich ist.

## Verwandte Themen

- [Einführung](intro.md)
- [Erstellen eines Patch-Statusberichts](generate-report.md)
- [Fehlerbehebung](troubleshooting.md)
