---
title: Funktionsweise der Datenmigration
description: Erfahren Sie mehr über den Datenmigrationsprozess zwischen Magento 1 und Magento 2, einschließlich Terminologie, Workflow-Diagrammen und -Schritten.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Funktionsweise der Datenmigration

Dieses Thema bietet einen allgemeinen Überblick darüber, wie Daten mithilfe von [!DNL Data Migration Tool] von Magento 1 auf Magento 2 migriert werden.

Der [!DNL Data Migration Tool] ist ein Befehlszeilenschnittstelle-Tool (CLI), mit dem Daten von Magento 1 auf Magento 2 übertragen werden können. Das Tool überprüft die Konsistenz zwischen Magento 1 und 2 Datenbankstrukturen (Tabellen und Felder), verfolgt den Fortschritt der Datenübertragung, erstellt Protokolle und führt Datenüberprüfungstests durch.

## Terminologie

* **Modi** - ein geordneter Satz von Vorgängen für die Migration von Daten von Magento 1.x auf Magento 2.x.
* **Schritte** - die Aufgaben in einem Modus, die die zu migrierenden Datentypen definieren.
* **Phasen** - die Aufgaben in Schritt, die die Daten validieren, übertragen und überprüfen.
* **Zuordnen von Dateien** - XML-Dateien, die die Regeln und Verbindungen zwischen Magento 1.x und Magento 2.x-Datenstrukturen zum Abschließen der Bühnen definieren.

## Modi

Der [!DNL Data Migration Tool] teilt den Migrationsprozess in drei Phasen oder *Modi* auf, um Daten von Magento 1.x an Magento 2.x zu übertragen und anzupassen. Die drei Modi sind hier aufgeführt und müssen in dieser Reihenfolge ausgeführt werden:

1. **Einstellungsmodus**: migriert die Systemkonfiguration und Website-bezogene Einstellungen.
1. **Datenmodus**: Migriert Datenbank-Assets stapelweise.
1. **Deltamodus**: migriert inkrementelle Änderungen (Änderungen seit der letzten Ausführung) wie neue Kunden und Bestellungen.

![Migrationsmodi](../../assets/data-migration/MigrationModes2.png)

## Schritte

Der [!DNL Data Migration Tool] verwendet eine Liste mit *Schritten* in jedem Modus, um einen bestimmten Datentyp zu migrieren. Im Modus Einstellungen werden beispielsweise zwei Schritte zum Migrieren aller Einstellungsdaten verwendet: der Schritt Stores und der Schritt Einstellungen . Details zu den spezifischen Daten, die in jedem dieser Schritte migriert werden (und zu den Schritten in den anderen Modi), finden Sie in der [[!DNL Data Migration Tool] technischen Spezifikation](technical-specification.md).

![Migrationsübersicht](../../assets/data-migration/MigrationOverview2.png)

## Phasen

Innerhalb jedes Schritts sind drei *Phasen*, die immer ausgeführt werden, um sicherzustellen, dass die Daten ordnungsgemäß migriert werden:

1. **Integritätsprüfung**: Vergleicht die Tabellenkalkulationsfeldnamen, -typen und andere Informationen, um die Kompatibilität zwischen Magento 1 und 2 Datenstrukturen zu überprüfen.
1. **Datenübertragung**: Überträgt die Datentabelle von Magento 1 und 2 nach Tabelle.
1. **Volumenüberprüfung**: Vergleicht die Anzahl der Datensätze zwischen Tabellen, um sicherzustellen, dass die Übertragung erfolgreich war.

![Migrationsphasen](../../assets/data-migration/MigrationSteps2.png)

## Zuordnen von Dateien

Auf der niedrigsten Ebene der Migrationsprozesse befinden sich die XML *map-Dateien*. Der [!DNL Data Migration Tool] verwendet Zuordnungsdateien in den Phasen eines Schritts, um verschiedene Datenstrukturen zwischen den Magento 1.x- und 2.x-Tabellen umzuwandeln.

Wenn Sie beispielsweise Daten aus einer Magento Open Source 1.8.0.0 in Magento Open Source 2.x.x umwandeln, berücksichtigt die Zuordnungsdatei, dass eine Tabelle umbenannt wurde, und benennt sie entsprechend in der Zieldatenbank um. Wenn es keine Unterschiede in der Datenstruktur oder im Datenformat gibt, überträgt der [!DNL Data Migration Tool] die Daten unverändert, einschließlich der Daten aus Tabellen, die von Erweiterungen erstellt wurden, in die Magento 2-Datenbank.

Wenn Unterschiede nicht in Zuordnungsdateien deklariert werden, zeigt der [!DNL Data Migration Tool] einen Fehler an und startet nicht.

Die Zuordnungsdateien werden ausführlicher unter [[!DNL Data Migration Tool] Technische Spezifikation] beschrieben.

## Migrationsflussdiagramm

![Migrationsfluss](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Technische Spezifikation](technical-specification.md)

Wir freuen uns, dass Sie erwägen, von der 1. Handelsplattform der Welt - Magento 1.x - zur Zukunftsplattform, Magento 2, zu wechseln. Wir freuen uns, die Details dieses Prozesses, den wir als Migration bezeichnen, zu teilen.

## Migrationskomponenten

Die Migration auf Magento 2 umfasst vier Komponenten: Daten, Erweiterungen und benutzerspezifischen Code, Designs und Anpassungen.

### Daten

Wir haben die **Magento 2[!DNL Data Migration Tool]** entwickelt, um Ihnen zu helfen, alle Ihre Produkte, Kunden und Bestelldaten, Speicherkonfigurationen, Promotions und mehr effizient auf Magento 2 zu verschieben. Dieses Handbuch enthält Informationen zum Tool und zu Best Practices für die Verwendung dieses Tools zur Migration Ihrer Daten.

### Erweiterungen und benutzerspezifischer Code

Wir haben hart mit der Entwickler-Community zusammengearbeitet, um Ihnen bei der Verwendung Ihrer Magento 1-Erweiterungen in Magento 2 zu helfen. Jetzt sind wir stolz, Ihnen die [Commerce Marketplace](https://marketplace.magento.com/) vorstellen zu können, wo Sie die neuesten Versionen Ihrer Lieblingserweiterungen herunterladen oder erwerben können.

Weitere Informationen zum Entwickeln von Erweiterungen für Magento 2 finden Sie im [PHP-Entwicklerhandbuch](https://developer.adobe.com/commerce/php/development/).

### Designs und Anpassungen

Magento 2 setzt neue Ansätze und Technologien ein, die Händlern eine unübertroffene Möglichkeit bieten, innovative Einkaufserlebnisse zu schaffen und neue Maßstäbe zu setzen. Um diese Fortschritte nutzen zu können, müssen Entwickler Änderungen an ihren Designs und Anpassungen vornehmen. Die Dokumentation ist online für die Erstellung von Magento 2 [Designs](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [Layouts](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) und [Anpassungen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) verfügbar.

## Migrationsbemühungen

Wie bei einem Upgrade zwischen 1.x-Versionen (z. B. von v1.12 auf v1.14) hängt der Aufwand für die Migration von Magento 1 auf Magento 2 davon ab, wie Sie Ihre Site erstellt haben und wie hoch der Grad der Anpassung ist.
Wir verbessern jedoch ständig den [!DNL Data Migration Tool] (weitere Informationen finden Sie im [Änderungsprotokoll](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) ), sodass die Migrationsbemühungen kontinuierlich zurückgehen.
