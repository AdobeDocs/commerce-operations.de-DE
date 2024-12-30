---
title: Split-Datenbankleistungslösung
description: Lesen Sie mehr über die Split-Datenbanklösung für Adobe Commerce.
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Überblick über die Lösung für die Aufspaltung der Datenbank

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce bietet mehrere Skalierbarkeitsvorteile, darunter die Möglichkeit, drei separate Master-Datenbanken für verschiedene Funktionsbereiche der Commerce-Anwendung zu verwenden.

Checkout, Bestellungen und Produktdaten können jeweils eine separate Master-Datenbank verwenden, die Sie optional replizieren können. Diese Trennung skaliert die Last unabhängig von Website-Checkouts, Bestellverwaltungsaktivitäten, Website-Browsing und Merchandising-Aktivitäten je nach Ihren Anforderungen. Diese Änderungen bieten beträchtliche Flexibilität bei der Skalierung der Datenbankebene.

>[!INFO]
>
>Adobe Commerce auf Cloud-Infrastruktur unterstützt _nicht_ diese Funktion.

Die `ResourceConnections`-Klasse stellt die einheitliche MySQL-Datenbankverbindung zum Commerce-Programm bereit. Für Abfragen an die primären Datenbanken implementieren wir das Datenbankmuster Command Query Responsibility Segregation (CQRS) . Dieses Muster behandelt die Logik zum Routing der Lese- und Schreibabfragen an die entsprechenden Datenbanken. Entwickler müssen nicht wissen, welche Konfiguration verwendet wird, und es gibt keine separaten Lese- und Schreibdatenbankverbindungen.

Wenn Sie eine optionale Datenbankreplikation einrichten, erhalten Sie die folgenden Vorteile:

- Datensicherung
- Datenanalyse ohne Beeinträchtigung der Master-Datenbank
- Skalierbarkeit

MySQL-Datenbanken werden asynchron repliziert, was bedeutet, dass Slaves nicht dauerhaft verbunden sein müssen, um Aktualisierungen vom Master zu erhalten.

Die folgende Abbildung zeigt, wie diese Funktion funktioniert.

![Adobe Commerce verwendet verschiedene Datenbanken zum Speichern von Tabellen](../../assets/configuration/split-db-diagram-ee.png)

In Magento Open Source wird nur eine Master-Datenbank verwendet.

Adobe Commerce verwendet drei Master-Datenbanken und eine konfigurierbare Anzahl von Slave-Datenbanken für die Replikation. Adobe Commerce verfügt über eine einzige Schnittstelle für Datenbankverbindungen, was zu einer schnelleren Leistung und besseren Skalierbarkeit führt.

## Konfigurationsoptionen

Aufgrund der Art und Weise, wie die Lösung zur Aufspaltung der Datenbankleistung konzipiert ist, können Ihr benutzerdefinierter Code und _installierten Komponenten_ der folgenden Aufgaben ausführen:

- Schreiben Sie direkt in die Datenbank (stattdessen müssen Sie die Adobe Commerce-Datenbankschnittstelle verwenden)
- JOINs verwenden, die sich auf die Verkaufs- oder Angebotsdatenbanken auswirken
- Verwenden von Fremdschlüsseln für Tabellen in der Checkout-, Verkaufs- oder Hauptdatenbank

>[!WARNING]
>
>Wenden Sie sich an Entwickler von Komponenten, um zu überprüfen, ob ihre Komponenten einen der oben genannten Punkte erfüllen. In diesem Fall müssen Sie nur eine der folgenden Optionen auswählen:
>
>- Bitten Sie die Komponentenentwickler, ihre Komponenten zu aktualisieren.
>- Verwenden Sie die Komponenten wie vorliegend _ohne_ die Lösung für die Aufspaltung der Datenbank.
>- Entfernen Sie die Komponenten, damit Sie die Lösung für die Aufspaltung der Datenbank verwenden können.

Dies bedeutet auch, dass Sie entweder:

- Konfigurieren Sie die Split-Datenbanklösung, _bevor_ Commerce in die Produktion überführt wird.

  Adobe empfiehlt, Split-Datenbanken so bald wie möglich nach der Installation der Commerce-Software zu konfigurieren.

- [Manuelles Konfigurieren](multi-master-manual.md) der Split-Datenbanklösung.

  Sie müssen diese Aufgabe ausführen, wenn Sie bereits Komponenten installiert haben oder wenn Commerce bereits in der Produktion ist. (_Aktualisieren Sie_ Produktionssystem. Nehmen Sie die Aktualisierungen in einem Entwicklungssystem vor und synchronisieren Sie die Änderungen, nachdem Sie sie getestet haben.)

  >[!WARNING]
  >
  >Sie müssen die beiden zusätzlichen Datenbankinstanzen manuell sichern. Commerce sichert nur die Hauptdatenbankinstanz. Mit den [`magento setup:backup --db`](../../installation/tutorials/backup.md) Befehls- und Admin-Optionen werden die zusätzlichen Tabellen nicht gesichert.

## Voraussetzungen

Für die Split-Datenbank müssen drei MySQL-Master-Datenbanken auf einem beliebigen Host eingerichtet werden (alle drei auf dem Commerce-Server, jede Datenbank auf einem separaten Server usw.). Dies sind _Master_-Datenbanken, die wie folgt verwendet werden:

- Eine Master-Datenbank für Checkout-Tabellen
- Eine Master-Datenbank für Verkaufstabellen (auch als _Order Management-System_ oder _OMS_-Tabellen bezeichnet)
- Eine Master-Datenbank für die übrigen Commerce 2-Anwendungstabellen

Darüber hinaus können Sie optional eine beliebige Anzahl von _Slave_-Datenbanken einrichten, die als Lastenausgleich und Backups dienen.

In diesem Handbuch wird beschrieben, wie Sie nur die primären Datenbanken einrichten. Wir stellen Ihnen Beispielkonfigurationen und Referenzen zur Verfügung, um bei Bedarf Slave-Datenbanken einzurichten.

In diesem Handbuch werden die drei Master-Datenbanken benannt:

- `magento_quote`
- `magento_sales`
- `magento`

(Sie können Ihre Datenbanken beliebig benennen.)
