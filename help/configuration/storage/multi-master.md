---
title: Aufspaltung der Datenbankleistung
description: Erfahren Sie mehr über die geteilte Datenbanklösung für Adobe Commerce.
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Übersicht über die geteilte Datenbanklösung

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce bietet verschiedene Skalierbarkeitsvorteile, darunter die Möglichkeit, drei separate Master-Datenbanken für verschiedene Funktionsbereiche der Commerce-Anwendung zu verwenden.

Checkout-, Bestellungen- und Produktdaten können jeweils eine separate Master-Datenbank verwenden, die Sie optional replizieren können. Diese Trennung skaliert die Auslastung unabhängig von Website-Kassengänge, Bestellverwaltungsaktivitäten, Website-Browsing und Merchandising-Aktivitäten, je nach Ihren Anforderungen. Diese Änderungen bieten eine erhebliche Flexibilität bei der Skalierung der Datenbankschicht.

>[!INFO]
>
>Adobe Commerce in der Cloud-Infrastruktur unterstützt diese Funktion nicht _._

Die Klasse `ResourceConnections` stellt die einheitliche MySQL-Datenbankverbindung zur Commerce-Anwendung bereit. Für Abfragen an die Master-Datenbanken implementieren wir das Datenbankmuster Command Query Responsibility Segregation (CQRS) . Dieses Muster verarbeitet die Logik zum Routing der Lese- und Schreibabfragen in die entsprechenden Datenbanken. Entwickler müssen nicht wissen, welche Konfiguration verwendet wird und es gibt keine separaten Lese- und Schreibdatenbankverbindungen.

Wenn Sie eine optionale Datenbankreplikation einrichten, haben Sie die folgenden Vorteile:

- Datensicherung
- Datenanalyse ohne Beeinträchtigung der Master-Datenbank
- Skalierbarkeit

MySQL-Datenbanken replizieren asynchron, was bedeutet, dass Slaves nicht dauerhaft verbunden werden müssen, um Updates vom Master zu erhalten.

Die folgende Abbildung zeigt, wie diese Funktion funktioniert.

![Adobe Commerce verwendet verschiedene Datenbanken zum Speichern von Tabellen](../../assets/configuration/split-db-diagram-ee.png)

In Magento Open Source wird nur eine Masterdatenbank verwendet.

Adobe Commerce verwendet drei Master-Datenbanken und eine konfigurierbare Anzahl von Slave-Datenbanken zur Replikation. Adobe Commerce verfügt über eine einzige Schnittstelle für Datenbankverbindungen, was zu einer schnelleren Leistung und besseren Skalierbarkeit führt.

## Konfigurationsoptionen

Aufgrund der Art und Weise, wie die Aufspaltungsdatenbankleistung entworfen wird, kann Ihr benutzerdefinierter Code und die installierten Komponenten _nicht_ einen der folgenden Schritte ausführen:

- Direktes Schreiben in die Datenbank (stattdessen müssen Sie die Adobe Commerce-Datenbankschnittstelle verwenden)
- Verwenden von JOINs, die sich auf die Verkaufs- oder Kursdatenbanken auswirken
- Fremdschlüssel für Tabellen in den Kasse-, Verkaufs- oder Hauptdatenbanken verwenden

>[!WARNING]
>
>Wenden Sie sich an Entwickler von Komponenten, um zu überprüfen, ob ihre Komponenten einen der oben genannten Schritte ausführen. In diesem Fall dürfen Sie nur eine der folgenden Optionen auswählen:
>
>- Bitten Sie die Komponentenentwickler, ihre Komponenten zu aktualisieren.
>- Verwenden Sie die Komponenten unverändert _ohne_ die aufgespaltete Datenbanklösung.
>- Entfernen Sie die Komponenten, damit Sie die geteilte Datenbanklösung verwenden können.

Dies bedeutet auch Folgendes:

- Konfigurieren Sie die geteilte Datenbanklösung _vor_, die Commerce in die Produktion einführt.

  Adobe empfiehlt die Konfiguration von geteilten Datenbanken so bald wie möglich nach der Installation der Commerce-Software.

- [Konfigurieren Sie die geteilte Datenbanklösung manuell ](multi-master-manual.md).

  Sie müssen diese Aufgabe ausführen, wenn Sie bereits Komponenten installiert haben oder Commerce bereits in Produktion ist. (_Aktualisieren Sie kein_ Produktionssystem. Nehmen Sie die Aktualisierungen in einem Entwicklungssystem vor und synchronisieren Sie die Änderungen, nachdem Sie sie getestet haben.)

  >[!WARNING]
  >
  >Sie müssen die beiden zusätzlichen Datenbankinstanzen manuell sichern. Commerce sichert nur die Hauptdatenbankinstanz. Die Optionen [`magento setup:backup --db`](../../installation/tutorials/backup.md) und &quot;Admin&quot;sichern die zusätzlichen Tabellen nicht.

## Voraussetzungen

Für die geteilte Datenbank müssen Sie drei MySQL-Master-Datenbanken auf einem beliebigen Host einrichten (alle drei auf dem Commerce-Server, jede Datenbank auf einem separaten Server usw.). Dies sind die _Master_ -Datenbanken und werden wie folgt verwendet:

- Eine Master-Datenbank für Checkout-Tabellen
- Eine Masterdatenbank für Verkaufstabellen (auch als _Order Management-System_ oder _OMS_, Tabellen bezeichnet)
- Eine Master-Datenbank für die übrigen Commerce 2-Anwendungstabellen

Darüber hinaus können Sie optional eine beliebige Anzahl von _Slave_-Datenbanken einrichten, die als Lastenausgleich und Sicherungen dienen.

In diesem Handbuch wird beschrieben, wie Sie die Master-Datenbanken einrichten. Wir stellen Ihnen Beispielkonfigurationen und -referenzen zur Verfügung, um Slave-Datenbanken bei Bedarf einzurichten.

In diesem Handbuch werden die drei Master-Datenbanken benannt:

- `magento_quote`
- `magento_sales`
- `magento`

(Sie können Ihre Datenbanken beliebig benennen.)
