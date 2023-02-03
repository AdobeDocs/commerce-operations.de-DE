---
title: Funktionsweise der Datenmigration
description: Erfahren Sie mehr über den Datenmigrationsprozess zwischen Magento 1 und Magento 2, einschließlich Terminologie, Workflow-Diagrammen und -Schritten.
source-git-commit: be2f924728853236bba786e7611b2a368c9f3054
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---


# Funktionsweise der Datenmigration

Dieses Thema bietet einen allgemeinen Überblick darüber, wie Daten mithilfe der Variablen [!DNL Data Migration Tool].

Die [!DNL Data Migration Tool] ist ein Befehlszeilenschnittstelle-Tool (CLI), mit dem Daten von Magento 1 nach Magento 2 übertragen werden können. Das Tool überprüft die Konsistenz zwischen Magento 1 und 2 Datenbankstrukturen (Tabellen und Felder), verfolgt den Fortschritt der Datenübertragung, erstellt Protokolle und führt Datenprüfungstests durch.

## Terminologie

* **Modi** - ein geordneter Satz von Vorgängen für die Migration von Daten von Magento 1.x zu Magento 2.x.
* **Schritte** - die Aufgaben in einem Modus, die die zu migrierenden Daten definieren.
* **Phasen** - die Schritte, die die Daten validieren, übertragen und überprüfen.
* **Zuordnungsdateien** - XML-Dateien, die die Regeln und Verbindungen zwischen den Datenstrukturen von Magento 1.x und Magento 2.x zum Abschluss der Phasen definieren.

## Modi

Die [!DNL Data Migration Tool] teilt den Migrationsprozess in drei Phasen auf oder *Modi* um Daten von Magento 1.x auf Magento 2.x zu übertragen und anzupassen. Die drei Modi sind hier aufgeführt und müssen in dieser Reihenfolge ausgeführt werden:

1. **Einstellungsmodus**: migriert die Systemkonfiguration und websitebezogene Einstellungen.
1. **Datenmodus**: migriert Datenbank-Assets stapelweise.
1. **Delta-Modus**: migriert inkrementelle Änderungen (Änderungen seit der letzten Ausführung) wie neue Kunden und Bestellungen.

![Migrationsmodi](../../assets/data-migration/MigrationModes2.png)

## Schritte

Die [!DNL Data Migration Tool] verwendet eine Liste von *Schritte* in jedem Modus, um einen bestimmten Datentyp zu migrieren. Im Modus Einstellungen werden beispielsweise zwei Schritte zum Migrieren aller Einstellungsdaten verwendet: den Schritt Stores und den Schritt Einstellungen . Details zu den spezifischen Daten, die in jedem dieser Schritte migriert werden (und zu den Schritten in den anderen Modi), finden Sie im Abschnitt [[!DNL Data Migration Tool] Technische Spezifikation](technical-specification.md).

![Migrationsübersicht](../../assets/data-migration/MigrationOverview2.png)

## Phasen

Innerhalb jedes Schritts sind drei *Phasen* die immer in dieser Reihenfolge ausgeführt werden, um sicherzustellen, dass die Daten ordnungsgemäß migriert werden:

1. **Integritätsprüfung**: Vergleicht die Tabellenfeldnamen, -typen und andere Informationen, um die Kompatibilität zwischen den Datenstrukturen von Magento 1 und 2 zu überprüfen.
1. **Datenübertragung**: Sendet die Datentabelle aus Magento 1 und 2 nach Tabelle.
1. **Lautstärkeprüfung**: Vergleicht die Anzahl der Datensätze zwischen Tabellen, um sicherzustellen, dass die Übertragung erfolgreich war.

![Migrationsschritte](../../assets/data-migration/MigrationSteps2.png)

## Zuordnungsdateien

Auf der niedrigsten Ebene der Migrationsprozesse befindet sich die XML *Zuordnungsdateien*. Die [!DNL Data Migration Tool] verwendet Zuordnungsdateien in den Phasen eines Schritts, um verschiedene Datenstrukturen zwischen den Magento 1.x- und 2.x-Tabellen umzuwandeln.

Wenn Sie beispielsweise Daten aus einer Datenbank der Magento Open Source 1.8.0.0 in Magento Open Source 2.x.x umwandeln, berücksichtigt die Zuordnungsdatei, dass eine Tabelle umbenannt wurde, und benennt sie entsprechend in der Zieldatenbank um. Wenn es keine Unterschiede in der Datenstruktur oder im Datenformat gibt, wird die [!DNL Data Migration Tool] überträgt sie unverändert, einschließlich Daten aus Tabellen, die von Erweiterungen erstellt wurden, in die Magento 2-Datenbank.

Wenn Unterschiede nicht in Zuordnungsdateien deklariert werden, wird die [!DNL Data Migration Tool] zeigt einen Fehler an und startet nicht.

Weitere Informationen zu Zuordnungsdateien finden Sie im Abschnitt [[!DNL Data Migration Tool] Technische Spezifikation].

## Migrationsflussdiagramm

![Migrationsfluss](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Technische Spezifikation](technical-specification.md)

Wir freuen uns, dass Sie erwägen, von der 1. Handelsplattform der Welt - Magento 1.x - zur Zukunftsplattform, Magento 2, überzugehen. Wir freuen uns, die Details dieses Prozesses, den wir als Migration bezeichnen, zu teilen.

## Migrationskomponenten

Die Migration nach Magento 2 umfasst vier Komponenten: Daten, Erweiterungen und benutzerdefinierter Code, Designs und Anpassungen.

### Daten

Wir haben die **Magento 2[!DNL Data Migration Tool]** um Ihnen dabei zu helfen, alle Ihre Produkte, Kunden und Bestelldaten, Speicherkonfigurationen, Promotions und mehr effizient in Magento 2 zu verschieben. Dieses Handbuch enthält Informationen zum Tool und zu Best Practices für die Verwendung dieses Tools zur Migration Ihrer Daten.

### Erweiterungen und benutzerspezifischer Code

Wir haben hart mit der Entwicklungsgemeinschaft zusammengearbeitet, um Ihnen bei der Verwendung Ihrer Magento 1-Erweiterungen in Magento 2 zu helfen. Jetzt sind wir stolz darauf, Ihnen die [Commerce Marketplace](https://marketplace.magento.com/), wo Sie die neuesten Versionen Ihrer bevorzugten Erweiterungen herunterladen oder erwerben können.

Weitere Informationen zur Entwicklung von Erweiterungen für Magento 2 finden Sie im [PHP-Entwicklerhandbuch](https://developer.adobe.com/commerce/php/development/).

### Designs und Anpassungen

Magento 2 setzt neue Ansätze und Technologien ein, die Händlern eine unübertroffene Möglichkeit bieten, innovative Einkaufserlebnisse zu schaffen und neue Maßstäbe zu setzen. Um diese Fortschritte nutzen zu können, müssen Entwickler Änderungen an ihren Designs und Anpassungen vornehmen. Die Dokumentation ist online für die Erstellung von Magento 2 verfügbar. [themes](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [Layouts](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)und [Anpassungen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Migrationsbemühungen

Wie bei einem Upgrade zwischen 1.x-Versionen (z. B. von v1.12 auf v1.14) hängt der Aufwand für die Migration von Magento 1 zu Magento 2 davon ab, wie Sie Ihre Site erstellt haben und wie hoch der Anpassungsgrad ist.
Wir verbessern jedoch ständig die [!DNL Data Migration Tool] (siehe [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) für weitere Einzelheiten); damit die Migrationsbemühungen kontinuierlich zurückgehen.
