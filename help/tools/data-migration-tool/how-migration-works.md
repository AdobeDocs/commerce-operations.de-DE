---
title: Funktionsweise der Datenmigration
description: Erfahren Sie mehr über den Datenmigrationsprozess zwischen Magento 1 und Magento 2, einschließlich Terminologie, Workflow-Diagrammen und Schritten.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Funktionsweise der Datenmigration

Dieses Thema bietet einen allgemeinen Überblick darüber, wie Daten mithilfe der [!DNL Data Migration Tool] von Magento 1 zu Magento 2 migriert werden.

Der [!DNL Data Migration Tool] ist ein Befehlszeilen-Tool (Command Line Interface, CLI) zum Übertragen von Daten von Magento 1 zu Magento 2. Das Tool überprüft die Konsistenz zwischen Magento 1- und 2-Datenbankstrukturen (Tabellen und Felder), verfolgt den Fortschritt der Datenübertragung, erstellt Protokolle und führt Datenüberprüfungstests durch.

## Terminologie

* **Modi** - eine geordnete Reihe von Vorgängen zum Migrieren von Daten von Magento 1.x zu Magento 2.x.
* **Schritte** - die Aufgaben in einem Modus, der die zu migrierenden Datentypen definiert.
* **Phasen** - die Aufgaben im Schritt, die die Daten validieren, übertragen und überprüfen.
* **Zuordnungsdateien** - XML-Dateien, die die Regeln und Verbindungen zwischen den Datenstrukturen von Magento 1.x und Magento 2.x definieren, um diese Schritte abzuschließen.

## Modi

Der [!DNL Data Migration Tool] unterteilt den Migrationsprozess in drei Phasen oder *Modi* um Daten von Magento 1.x auf Magento 2.x zu übertragen und anzupassen. Die drei Modi sind hier aufgeführt und müssen in der folgenden Reihenfolge ausgeführt werden:

1. **Einstellungsmodus**: Migriert die Systemkonfiguration und die Website-bezogenen Einstellungen.
1. **Datenmodus**: Migriert Datenbank-Assets zusammen.
1. **Delta-Modus**: Migriert inkrementelle Änderungen (Änderungen seit der letzten Ausführung), z. B. neue Kunden und Bestellungen.

![Migrationsmodi](../../assets/data-migration/MigrationModes2.png)

## Schritte

Der [!DNL Data Migration Tool] verwendet eine Liste von *Schritten* innerhalb jedes Modus, um einen bestimmten Datentyp zu migrieren. Beispielsweise gibt es im Einstellungsmodus zwei Schritte zum Migrieren aller Einstellungsdaten: den Schritt Stores und den Schritt Einstellungen . Einzelheiten zu den spezifischen Daten, die in jedem dieser Schritte (und für die Schritte in den anderen Modi) migriert werden, finden Sie in der [[!DNL Data Migration Tool] Technischen Spezifikation](technical-specification.md).

![Migrationsübersicht](../../assets/data-migration/MigrationOverview2.png)

## Stadien

In jedem Schritt sind drei *Phasen* die immer ausgeführt werden, um sicherzustellen, dass die Daten ordnungsgemäß migriert werden:

1. **Integritätsprüfung**: Vergleicht die Namen, Typen und anderen Informationen der Tabellenfelder, um die Kompatibilität zwischen den Datenstrukturen von Magento 1 und 2 zu überprüfen.
1. **Datenübertragung**: Überträgt die Datentabelle nach Tabelle aus Magento 1 und 2.
1. **Volumeprüfung**: Vergleicht die Anzahl der Datensätze zwischen Tabellen, um zu überprüfen, ob die Übertragung erfolgreich war.

![Migrationsphasen](../../assets/data-migration/MigrationSteps2.png)

## Zuordnen von Dateien

Auf der untersten Ebene der Migrationsprozesse befinden sich die XML-*Zuordnungsdateien*. Der [!DNL Data Migration Tool] verwendet Zuordnungsdateien innerhalb der Schritte, um verschiedene Datenstrukturen zwischen den Tabellen Magento 1.x und 2.x umzuwandeln.

Wenn Sie beispielsweise Daten aus einer Magento Open Source 1.8.0.0-Datenbank in Magento Open Source 2.x.x umwandeln, berücksichtigt die Zuordnungsdatei die Tatsache, dass eine Tabelle umbenannt wurde, und benennt sie in der Zieldatenbank entsprechend um. Wenn es keine Unterschiede in der Datenstruktur oder dem Datenformat gibt, überträgt die [!DNL Data Migration Tool] sie unverändert, einschließlich der Daten aus durch Erweiterungen erstellten Tabellen, in die Magento 2-Datenbank.

Wenn Unterschiede nicht in Zuordnungsdateien deklariert werden, zeigt die [!DNL Data Migration Tool] einen Fehler an und startet nicht.

Zuordnungsdateien werden in der [[!DNL Data Migration Tool] Technische Spezifikation] ausführlicher erläutert.

## Diagramm zum Migrationsfluss

![Migrationsfluss](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Technische Spezifikation](technical-specification.md)

Wir freuen uns, dass Sie den Umstieg von der weltweit #1 Commerce-Plattform - Magento 1.x - auf Magento 2, die Plattform der Zukunft, in Erwägung ziehen. Wir freuen uns, die Details zu diesem Prozess, den wir als Migration bezeichnen, zu teilen.

## Migrationskomponenten

Die Magento 2-Migration umfasst vier Komponenten: Daten, Erweiterungen und benutzerspezifischen Code, Designs und Anpassungen.

### Daten

Wir haben die **Magento 2-[!DNL Data Migration Tool]** entwickelt, damit Sie all Ihre Produkte, Kunden, Bestelldaten, Store-Konfigurationen, Werbeaktionen und mehr effizient nach Magento 2 verschieben können. Dieses Handbuch enthält Informationen zum -Tool und Best Practices für dessen Verwendung zur Migration Ihrer Daten.

### Erweiterungen und benutzerdefinierter Code

Wir haben hart mit der Entwicklungs-Community zusammengearbeitet, um Sie bei der Verwendung Ihrer Magento 1-Erweiterungen in Magento 2 zu unterstützen. Jetzt sind wir stolz darauf, Ihnen die [Commerce Marketplace](https://marketplace.magento.com/) vorzustellen, wo Sie die neuesten Versionen Ihrer Lieblingserweiterungen herunterladen oder kaufen können.

Weitere Informationen zur Entwicklung von Erweiterungen für Magento 2 finden Sie im [PHP Developer Guide](https://developer.adobe.com/commerce/php/development/).

### Designs und Anpassungen

Magento 2 nutzt neue Ansätze und Technologien, die Händlern die unübertroffene Möglichkeit bieten, innovative Einkaufserlebnisse zu schaffen und auf neue Ebenen zu skalieren. Um diese Fortschritte nutzen zu können, müssen Entwickler Änderungen an ihren Designs und Anpassungen vornehmen. Die Dokumentation ist online für die Erstellung von Magento 2 [Designs](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [Layouts](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) und [Anpassungen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Migrationsbemühungen

Genau wie bei einem Upgrade zwischen 1.x-Versionen (z. B. von v1.12 auf v1.14) hängt der Aufwand für die Migration von Magento 1 zu Magento 2 davon ab, wie Sie Ihre Site erstellt haben, und wie stark sie angepasst wird.
Allerdings verbessern wir die [!DNL Data Migration Tool] ständig (weitere Einzelheiten finden Sie [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md)), sodass die Migrationsbemühungen kontinuierlich zurückgehen.
