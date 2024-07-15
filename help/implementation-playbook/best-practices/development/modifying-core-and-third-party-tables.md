---
title: Best Practices für die Änderung von Datenbanktabellen
description: Erfahren Sie, wie und wann Adobe Commerce- und Drittanbieter-Datenbanktabellen geändert werden.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# Best Practices für die Änderung von Datenbanktabellen

Dieser Artikel enthält Best Practices zum Ändern von Datenbanktabellen, die von [!DNL Adobe Commerce]- oder Drittanbietermodulen erstellt werden. Wenn Sie wissen, wann und wie Sie Tabellen effektiv ändern, können Sie die langfristige Rentabilität und Stabilität Ihrer Commerce-Plattform sicherstellen.

Für die Migration von [!DNL Magento 1] und anderen E-Commerce-Plattformen oder die Arbeit mit Modulen vom [!DNL Adobe Commerce] Marketplace müssen möglicherweise zusätzliche Daten hinzugefügt und gespeichert werden. Als Erstes können Sie einer Datenbanktabelle eine Spalte hinzufügen oder eine vorhandene anpassen. Sie sollten jedoch nur in eingeschränkten Situationen eine Kern-Tabelle mit [!DNL Adobe Commerce] (oder Tabelle eines Drittanbieters) ändern.

## Warum Adobe empfiehlt, Änderungen zu vermeiden

Der Hauptgrund für die Vermeidung von Änderungen an Kerntabellen besteht darin, dass Adobe Commerce die zugrunde liegende Logik mit SQL-Rohabfragen enthält. Änderungen an der Tabellenstruktur können zu unerwarteten Nebenwirkungen führen, die schwer zu beheben sind. Die Änderung kann sich auch auf DDL-Vorgänge (Data Definition Language) auswirken und unvorhersehbare Auswirkungen auf die Leistung haben.

Ein weiterer Grund, die Änderung der Datenbanktabellenstruktur zu vermeiden, besteht darin, dass Ihre Änderungen Probleme verursachen können, wenn das Kernentwicklungsteam oder Entwickler von Drittanbietern die Struktur ihrer Datenbanktabellen ändern. Es gibt beispielsweise einige zentrale Datenbanktabellen mit der Spalte `additional_data`. Dies war immer ein Spaltentyp `text` . Aus Leistungsgründen kann das Kernteam die Spalte jedoch in `longtext` ändern. Dieser Spaltentyp ist ein Alias für JSON. Durch die Konvertierung in diesen Spaltentyp werden dieser Spalte Leistungsverbesserungen und Suchmöglichkeiten hinzugefügt, die nicht als `text` -Typ vorhanden sind. Weitere Informationen zu diesem Thema finden Sie unter [JSON-Datentyp](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Datum zum Speichern oder Entfernen von Daten

Adobe empfiehlt, dass Sie zuerst bestimmen, ob Sie diese Daten speichern müssen. Wenn Sie Daten aus einem Legacy-System verschieben, sparen Ihnen alle Daten, die Sie entfernen können, Zeit und Mühe während der Migration. (Es gibt Möglichkeiten, Daten zu archivieren, wenn sie später aufgerufen werden müssen.) Damit Sie die Anwendung und Leistung gut steuern können, können Sie eine Anforderung zum Speichern zusätzlicher Daten anfechten. Ihr Ziel besteht darin sicherzustellen, dass das Speichern der Daten eine Voraussetzung ist, um eine geschäftliche Anforderung zu erfüllen, die nicht auf andere Weise ausgefüllt werden kann.

### Alte Daten

Wenn Ihr Projekt veraltete Daten wie alte Bestellungen oder Kundendatensätze enthält, sollten Sie eine alternative Suchmethode in Erwägung ziehen. Wenn das Unternehmen beispielsweise nur gelegentlich Zugriff auf die Daten benötigt, sollten Sie eine externe Suche der alten Datenbank implementieren, die außerhalb der Commerce-Plattform gehostet wird, anstatt alte Daten in [!DNL Adobe Commerce] zu migrieren.

In diesem Fall muss die Datenbank auf einen Server migriert werden, der entweder eine Webschnittstelle zum Lesen der Daten anbietet oder vielleicht eine Schulung in der Verwendung von MySQL Workbench oder ähnlichen Tools. Das Ausschließen dieser Daten aus der neuen Datenbank beschleunigt die Migration, da das Entwicklungsteam sich auf die neue Site konzentrieren kann, anstatt Probleme mit der Datenmigration zu beheben.

Eine andere Möglichkeit, die Daten außerhalb des Handels zu halten, sie jedoch in Echtzeit zu verwenden, wäre die Nutzung anderer Tools wie GraphQL-Gitter. Diese Option kombiniert verschiedene Datenquellen und gibt sie als einzelne Antwort zurück.

Sie können beispielsweise &quot;`stitch`&quot; alte Bestellungen aus einer externen Datenbank zusammenführen, vielleicht die alte Magento 1-Site, die stillgelegt wurde. Zeigen Sie sie dann mithilfe des GraphQL-Gitters als Teil des Bestellverlaufs der Kunden an. Diese alten Bestellungen können mit den Bestellungen aus Ihrer aktuellen [!DNL Adobe Commerce] -Umgebung kombiniert werden.

Weitere Informationen zur Verwendung von API-Gitter mit GraphQL finden Sie unter [Was ist API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) und [GraphQL-Mesh-Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrieren älterer Daten mit Erweiterungsattributen

Wenn Sie feststellen, dass ältere Daten migriert werden müssen oder dass neue Daten in [!DNL Adobe Commerce] gespeichert werden müssen, empfiehlt Adobe die Verwendung von [Erweiterungsattributen](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. Die Verwendung von Erweiterungsattributen zum Speichern zusätzlicher Daten bietet die folgenden Vorteile:

- Sie können die beizubehaltenden Daten und die Datenbankstruktur steuern, um sicherzustellen, dass die Daten mit dem richtigen Spaltentyp und den richtigen Indizes gespeichert werden.
- Die meisten Entitäten in [!DNL Adobe Commerce] unterstützen die Verwendung von Erweiterungsattributen.
- Erweiterungsattribute sind ein speicherunabhängiger Mechanismus, der die Flexibilität bietet, die Daten an einem optimalen Speicherort für Ihr Projekt zu speichern.

Zwei Beispiele für Speicherorte sind Datenbanktabellen und [!DNL Redis]. Entscheidend bei der Auswahl eines Standorts ist, ob der Standort eine zusätzliche Komplexität einbringt oder sich auf die Leistung auswirkt.

### Andere Alternativen in Betracht ziehen

Als Entwickler ist es wichtig, immer Tools außerhalb Ihrer [!DNL Adobe Commerce]-Umgebung zu verwenden, z. B. GraphQL-Gitter und Adobe App Builder. Diese Tools können Ihnen dabei helfen, den Zugriff auf die Daten beizubehalten, wirken sich jedoch nicht auf die Commerce-Hauptanwendung oder die zugrunde liegenden Datenbanktabellen aus. Bei diesem Ansatz stellen Sie Ihre Daten über eine API bereit. Fügen Sie dann Ihrer App Builder-Konfiguration eine Datenquelle hinzu. Mit GraphQL Mesh können Sie diese Datenquellen kombinieren und eine einzige Antwort erstellen, wie in [alten Daten](#legacy-data) beschrieben.

Weitere Informationen zum GraphQL-Gitter finden Sie unter [GraphQL-Mesh-Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. Weitere Informationen zum Adobe App Builder finden Sie unter [Einführung in App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Ändern einer Kerntabelle oder Drittanbietertabelle

Wenn Sie sich dafür entscheiden, Daten durch Änderung einer Core- [!DNL Adobe Commerce] - oder Drittanbieter-Modul-Datenbanktabelle zu speichern, sollten Sie die folgenden Richtlinien verwenden, um die Auswirkungen auf Stabilität und Leistung zu minimieren.

- Nur neue Spalten hinzufügen.
- Ändern Sie nie den Wert _type_ einer vorhandenen Spalte. Ändern Sie beispielsweise nicht &quot;`integer`&quot;in &quot;`varchar`&quot;, um Ihren individuellen Anwendungsfall zu erfüllen.
- Vermeiden Sie das Hinzufügen von Spalten zu EAV-Attributtabellen. Diese Tabellen sind bereits mit Logik und Verantwortung überlastet.
- Bestimmen Sie vor dem Anpassen einer Tabelle deren Größe. Das Ändern großer Tabellen wirkt sich auf die Bereitstellung aus, was zu Minuten oder Stunden Verzögerung bei der Anwendung von Änderungen führen kann.

## Best Practices zum Ändern einer externen Datenbanktabelle

Adobe empfiehlt die folgenden Schritte, wenn Sie eine Spalte zu einer Kerndatenbanktabelle oder einer Drittanbieter-Tabelle hinzufügen:

1. Erstellen Sie ein Modul mit einem Namen in Ihrem Namespace, der das darstellt, was Sie aktualisieren.

   Beispiel: `app/code/YourCompany/Customer`

1. Erstellen Sie die entsprechenden Dateien, um das Modul zu aktivieren (siehe [Erstellen eines Moduls](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Erstellen Sie eine Datei mit dem Namen `db_schema.xml` im Ordner `etc` und nehmen Sie die entsprechenden Änderungen vor.

   Falls zutreffend, generieren Sie eine `db_schema_whitelist.json` -Datei. Weitere Informationen finden Sie unter [Deklaratives Schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} .

### Potenzielle Auswirkungen

Das Hinzufügen einer Spalte zu einer externen Datenbank kann sich auf folgende Weise auf Ihr Adobe Commerce-Projekt auswirken:

- Upgrades könnten komplizierter sein.
- Bereitstellungen sind betroffen, wenn die zu ändernde Tabelle groß ist.
- Die Migration zu einer neuen Plattform könnte komplizierter sein.

## Methoden zum Vermeiden von Änderungen an Kerntabellen

Sie können eine Änderung von Adobe Commerce-Datenbanktabellen durch Verwendung von [Erweiterungsattributen](#migrate-legacy-data-with-extension-attributes) vermeiden. Eine weitere Alternative besteht darin, eine spezielle Spalte (`additional_data`) zu verwenden, die in einigen Kerntabellen gefunden wird, um Daten zu speichern und sie im JSON-kodierten Format zu speichern.

### Daten in einer JSON-kodierten Datenspalte speichern

Einige Kerntabellen verfügen über eine Spalte &quot;`additional_data`&quot;, die JSON-kodierte Daten enthält. Diese Spalte bietet eine native Möglichkeit, zusätzliche Daten in einem Feld zuzuordnen. Mit dieser Methode wird verhindert, dass eine Tabelle für kleine, einfache Datenelemente hinzugefügt wird, die Informationen zum Datenabruf ohne Suchanforderung speichern. Die Spalte `additional_data` ist in der Regel nur auf Elementebene verfügbar, nicht für das gesamte Anführungszeichen oder die gesamte Bestellung.

- Vorteile der Verwendung des Felds `additional_data`

   - Es sind keine zusätzlichen Felder erforderlich, sodass die Anzahl der Spalten minimal bleibt. Dies ist im Verkaufsfluss hilfreich, wo bereits viele Tabellen enthalten sind. Es ist am besten, diesen bereits komplizierten Prozess nicht noch komplexer zu gestalten. Diese Methode erfüllt viele Anwendungsfälle, aber nicht alle.

- Nachteile

   - Diese Methode eignet sich nur zum Speichern schreibgeschützter Daten. Dieses Problem tritt auf, weil unser Code nicht serialisiert werden muss, um das Objekt zu ändern und zu erstellen, um Abhängigkeiten oder Datenbankbeziehungen hinzuzufügen.

   - Es ist schwierig, Datenbankvorgänge zu verwenden, um nach diesen Feldern zu suchen. Mit dieser Methode zu suchen ist langsam.

   - Beim Speichern von Daten in der Spalte `additional_data` ist besondere Vorsicht geboten, um zu verhindern, dass Serialisierungs- oder Unserialisierungsvorgänge ausgelöst werden, die den Code beschädigen könnten, indem ungültige JSON erstellt oder während der Laufzeit Lesefehler verursacht werden.

   - Diese Felder müssen im Code klar deklariert sein, damit sie ein Entwickler leicht finden kann.

   - Andere Probleme, die auftreten können, können sehr schwer zu diagnostizieren sein. Bei einigen nativen PHP-Funktionen, wenn Sie nicht die von der Kernanwendung bereitgestellten [!DNL Adobe Commerce] -Wrapper-Methoden verwenden, kann sich das Endergebnis der umgewandelten Daten vom erwarteten Format unterscheiden. Verwenden Sie immer die Wrapper-Funktionen, um die Konsistenz und Vorhersagbarkeit der zu speichernden oder abgerufenen Daten sicherzustellen.

Im Folgenden finden Sie Beispiele für Tabellen mit der Spalte und der Struktur für die Spalte `additional_data` .

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

In den Versionen 2.4.3, 2.4.4 und 2.4.5 gibt es zehn Tabellen mit der Spalte `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
