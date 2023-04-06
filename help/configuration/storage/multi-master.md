---
title: Aufspaltung der Datenbankleistung
description: Erfahren Sie mehr über die geteilte Datenbanklösung für Adobe Commerce und Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---


# Übersicht über die geteilte Datenbanklösung

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce bietet verschiedene Skalierbarkeitsvorteile, darunter die Möglichkeit, drei separate Übergeordnete Datenbanken für verschiedene Funktionsbereiche der Commerce-Anwendung zu verwenden.

Checkout-, Bestellungen- und Produktdaten können jeweils eine separate Übergeordnete Datenbank verwenden, die Sie optional replizieren können. Diese Trennung skaliert die Auslastung unabhängig von Website-Kassengänge, Bestellverwaltungsaktivitäten, Website-Browsing und Merchandising-Aktivitäten, je nach Ihren Anforderungen. Diese Änderungen bieten eine erhebliche Flexibilität bei der Skalierung der Datenbankschicht.

>[!INFO]
>
>Adobe Commerce auf Cloud-Infrastruktur: _not_ unterstützt diese Funktion.

Die `ResourceConnections` -Klasse stellt die einheitliche MySQL-Datenbankverbindung zur Commerce-Anwendung bereit. Für Abfragen an die Übergeordneten Datenbanken implementieren wir das Datenbankmuster Command Query Responsibility Segregation (CQRS) . Dieses Muster verarbeitet die Logik zum Routing der Lese- und Schreibabfragen in die entsprechenden Datenbanken. Entwickler müssen nicht wissen, welche Konfiguration verwendet wird und es gibt keine separaten Lese- und Schreibdatenbankverbindungen.

Wenn Sie eine optionale Datenbankreplikation einrichten, haben Sie die folgenden Vorteile:

- Datensicherung
- Datenanalyse ohne Beeinträchtigung der Übergeordneten Datenbank
- Skalierbarkeit

MySQL-Datenbanken replizieren asynchron, was bedeutet, dass Slaves nicht dauerhaft verbunden werden müssen, um Updates von der Übergeordneten zu erhalten.

Die folgende Abbildung zeigt, wie diese Funktion funktioniert.

![Adobe Commerce verwendet verschiedene Datenbanken zum Speichern von Tabellen](../../assets/configuration/split-db-diagram-ee.png)

In Magento Open Source wird nur eine Übergeordnete Datenbank verwendet.

Adobe Commerce verwendet drei Übergeordnete Datenbanken und eine konfigurierbare Anzahl von Slave-Datenbanken zur Replikation. Adobe Commerce verfügt über eine einzige Schnittstelle für Datenbankverbindungen, was zu einer schnelleren Leistung und besseren Skalierbarkeit führt.

## Konfigurationsoptionen

Aufgrund der Art und Weise, wie die aufgespaltete Datenbank-Performance-Lösung entworfen wird, Ihr benutzerdefinierter Code und die installierten Komponenten _cannot_ Führen Sie einen der folgenden Schritte aus:

- Direktes Schreiben in die Datenbank (stattdessen müssen Sie die Adobe Commerce-Datenbankschnittstelle verwenden)
- Verwenden von JOINs, die sich auf die Verkaufs- oder Kursdatenbanken auswirken
- Fremdschlüssel für Tabellen in den Kasse-, Verkaufs- oder Hauptdatenbanken verwenden

>[!WARNING]
>
>Wenden Sie sich an Entwickler von Komponenten, um zu überprüfen, ob ihre Komponenten einen der oben genannten Schritte ausführen. In diesem Fall dürfen Sie nur eine der folgenden Optionen auswählen:
>
>- Bitten Sie die Komponentenentwickler, ihre Komponenten zu aktualisieren.
>- Die Komponenten unverändert verwenden _without_ die geteilte Datenbanklösung.
>- Entfernen Sie die Komponenten, damit Sie die geteilte Datenbanklösung verwenden können.


Dies bedeutet auch, dass Sie Folgendes tun können:

- Konfiguration der geteilten Datenbanklösung _before_ Handel in Produktion bringen.

   Adobe empfiehlt die Konfiguration von geteilten Datenbanken so bald wie möglich nach der Installation der Commerce-Software.

- [Manuelle Konfiguration](multi-master-manual.md) die geteilte Datenbanklösung.

   Sie müssen diese Aufgabe ausführen, wenn Sie bereits Komponenten installiert haben oder wenn Commerce bereits in Produktion ist. (_Nicht_ ein Produktionssystem zu aktualisieren; nehmen Sie die Aktualisierungen in einem Entwicklungssystem vor und synchronisieren Sie die Änderungen, nachdem Sie sie getestet haben.)

   >[!WARNING]
   >
   >Sie müssen die beiden zusätzlichen Datenbankinstanzen manuell sichern. Commerce sichert nur die Hauptdatenbankinstanz. Die [`magento setup:backup --db`](../../installation/tutorials/backup.md) -Befehl und Admin-Optionen sichern die zusätzlichen Tabellen nicht.

## Voraussetzungen

Für die geteilte Datenbank müssen Sie drei Übergeordnete MySQL-Datenbanken auf einem beliebigen Host einrichten (alle drei auf dem Commerce-Server, jede Datenbank auf einem separaten Server usw.). Dies sind die _Übergeordnet_ Datenbanken und werden wie folgt verwendet:

- Eine Übergeordnete Datenbank für Checkout-Tabellen
- Eine Übergeordnete Datenbank für Verkaufstabellen (auch als _Order Management System_ oder _OMS_, Tabellen)
- Eine Übergeordnete Datenbank für die restlichen Commerce 2-Anwendungstabellen

Darüber hinaus können Sie optional eine beliebige Anzahl von _Slave_ Datenbanken, die als Lastenausgleich und Backups dienen.

In diesem Handbuch wird beschrieben, wie Sie nur die Übergeordneten Datenbanken einrichten. Wir stellen Ihnen Beispielkonfigurationen und -referenzen zur Verfügung, um Slave-Datenbanken bei Bedarf einzurichten.

In diesem Handbuch werden die drei Übergeordneten Datenbanken benannt:

- `magento_quote`
- `magento_sales`
- `magento`

(Sie können Ihre Datenbanken beliebig benennen.)
