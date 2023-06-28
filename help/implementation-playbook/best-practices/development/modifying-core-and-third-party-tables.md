---
title: Best Practices für die Änderung von Datenbanktabellen
description: Erfahren Sie, wie und wann Adobe Commerce- und Drittanbieter-Datenbanktabellen geändert werden.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Best Practices für die Änderung von Datenbanktabellen

Dieser Artikel enthält Best Practices zum Ändern von Datenbanktabellen, die von [!DNL Adobe Commerce] oder Drittanbietermodulen. Wenn Sie wissen, wann und wie Sie Tabellen effektiv ändern, können Sie die langfristige Rentabilität und Stabilität Ihrer Commerce-Plattform sicherstellen.

Migration von [!DNL Magento 1] und anderen E-Commerce-Plattformen oder mit Modulen aus der [!DNL Adobe Commerce] Marketplace kann das Hinzufügen und Speichern zusätzlicher Daten erfordern. Als Erstes können Sie einer Datenbanktabelle eine Spalte hinzufügen oder eine vorhandene anpassen. Sie sollten jedoch nur einen Kern ändern [!DNL Adobe Commerce] -Tabelle (oder Tabelle eines Drittanbieters) in eingeschränkten Situationen.

## Warum Adobe empfiehlt, Änderungen zu vermeiden

Der Hauptgrund für die Vermeidung von Änderungen an Kerntabellen besteht darin, dass Adobe Commerce die zugrunde liegende Logik mit SQL-Rohabfragen enthält. Änderungen an der Tabellenstruktur können zu unerwarteten Nebenwirkungen führen, die schwer zu beheben sind. Die Änderung kann sich auch auf DDL-Vorgänge (Data Definition Language) auswirken und unvorhersehbare Auswirkungen auf die Leistung haben.

Ein weiterer Grund, die Änderung der Datenbanktabellenstruktur zu vermeiden, besteht darin, dass Ihre Änderungen Probleme verursachen können, wenn das Kernentwicklungsteam oder Entwickler von Drittanbietern die Struktur ihrer Datenbanktabellen ändern. Beispielsweise gibt es einige Kerndatenbanktabellen mit einer Spalte namens `additional_data`. Dies war immer eine `text` Spaltentyp. Aus Leistungsgründen kann das Kernteam die Spalte jedoch in `longtext`. Dieser Spaltentyp ist ein Alias für JSON. Durch die Konvertierung in diesen Spaltentyp werden dieser Spalte Leistungsverbesserungen und Suchmöglichkeiten hinzugefügt, die nicht als `text` Typ. Weitere Informationen zu diesem Thema finden Sie unter [JSON-Datentyp](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Ermitteln, wann Daten gespeichert oder entfernt werden

Adobe empfiehlt, zunächst zu ermitteln, ob diese Daten gespeichert werden müssen. Wenn Sie Daten aus einem Legacy-System verschieben, sparen Ihnen alle Daten, die Sie entfernen können, Zeit und Mühe während der Migration. (Es gibt Möglichkeiten, Daten zu archivieren, wenn sie später aufgerufen werden müssen.) Damit Sie die Anwendung und Leistung gut steuern können, können Sie eine Anforderung zum Speichern zusätzlicher Daten anfechten. Ihr Ziel besteht darin sicherzustellen, dass das Speichern der Daten eine Voraussetzung ist, um eine geschäftliche Anforderung zu erfüllen, die nicht auf andere Weise ausgefüllt werden kann.

### Alte Daten

Wenn Ihr Projekt veraltete Daten wie alte Bestellungen oder Kundendatensätze enthält, sollten Sie eine alternative Suchmethode in Erwägung ziehen. Wenn das Unternehmen beispielsweise nur gelegentlich Zugriff auf die Daten benötigt, sollten Sie eine externe Suche der alten Datenbank implementieren, die außerhalb der Commerce-Plattform gehostet wird, anstatt alte Daten zu migrieren. [!DNL Adobe Commerce].

In diesem Fall muss die Datenbank auf einen Server migriert werden, der entweder eine Webschnittstelle zum Lesen der Daten anbietet oder vielleicht eine Schulung in der Verwendung von MySQL Workbench oder ähnlichen Tools. Das Ausschließen dieser Daten aus der neuen Datenbank beschleunigt die Migration, da das Entwicklungsteam sich auf die neue Site konzentrieren kann, anstatt Probleme mit der Datenmigration zu beheben.

Eine andere Möglichkeit, die Daten außerhalb des Handels zu halten, sie jedoch in Echtzeit zu verwenden, wäre die Nutzung anderer Tools wie GraphQL-Gitter. Diese Option kombiniert verschiedene Datenquellen und gibt sie als einzelne Antwort zurück.

Sie können beispielsweise `stitch` zusammen alte Bestellungen aus einer externen Datenbank, vielleicht die alte Magento 1-Site, die eingestellt wird. Zeigen Sie sie dann mithilfe des GraphQL-Gitters als Teil des Bestellverlaufs der Kunden an. Diese alten Bestellungen können mit den Bestellungen Ihrer aktuellen [!DNL Adobe Commerce] Umgebung.

Weitere Informationen zur Verwendung von API-Gittern mit GraphQL finden Sie unter [Was ist API-Mesh?](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrieren von Legacy-Daten mit Erweiterungsattributen

Wenn Sie feststellen, dass ältere Daten migriert werden müssen oder dass neue Daten in gespeichert werden müssen [!DNL Adobe Commerce]empfiehlt Adobe die Verwendung von [Erweiterungsattribute](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. Die Verwendung von Erweiterungsattributen zum Speichern zusätzlicher Daten bietet die folgenden Vorteile:

- Sie können die beizubehaltenden Daten und die Datenbankstruktur steuern, um sicherzustellen, dass die Daten mit dem richtigen Spaltentyp und den richtigen Indizes gespeichert werden.
- Die meisten Entitäten in [!DNL Adobe Commerce] und [!DNL Magento Open Source] unterstützt die Verwendung von Erweiterungsattributen.
- Erweiterungsattribute sind ein speicherunabhängiger Mechanismus, der die Flexibilität bietet, die Daten an einem optimalen Speicherort für Ihr Projekt zu speichern.

Zwei Beispiele für Speicherorte sind Datenbanktabellen und [!DNL Redis]. Entscheidend bei der Auswahl eines Standorts ist, ob der Standort eine zusätzliche Komplexität bringt oder sich auf die Leistung auswirkt.

### Andere Alternativen in Betracht ziehen

Als Entwickler ist es wichtig, immer die Verwendung von Tools außerhalb Ihrer [!DNL Adobe Commerce] -Umgebung, z. B. GraphQL-Gitter und Adobe App Builder. Diese Tools können Ihnen dabei helfen, den Zugriff auf die Daten beizubehalten, wirken sich jedoch nicht auf die Commerce-Hauptanwendung oder die zugrunde liegenden Datenbanktabellen aus. Bei diesem Ansatz stellen Sie Ihre Daten über eine API bereit. Fügen Sie dann Ihrer App Builder-Konfiguration eine Datenquelle hinzu. Mit GraphQL Mesh können Sie diese Datenquellen kombinieren und eine einzige Antwort erstellen, wie in [Legacy-Daten](#legacy-data).

Weitere Informationen zum GraphQL-Gitter finden Sie unter [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Ändern von Kerntabellen oder Drittanbietertabellen

Wenn Sie Daten speichern möchten, indem Sie einen Kern ändern [!DNL Adobe Commerce] Verwenden Sie die folgenden Richtlinien, um die Auswirkungen auf Stabilität und Leistung zu minimieren.

- Fügen Sie nur neue Spalten hinzu.
- Ändern Sie nie die _type_ Wert einer vorhandenen Spalte. Ändern Sie beispielsweise nicht die `integer` zu `varchar` um Ihren individuellen Anwendungsfall zu erfüllen.
- Vermeiden Sie das Hinzufügen von Spalten zu EAV-Attributtabellen. Diese Tabellen sind bereits mit Logik und Verantwortung überlastet.
- Bestimmen Sie vor dem Anpassen einer Tabelle deren Größe. Das Ändern großer Tabellen wirkt sich auf die Bereitstellung aus, was zu Minuten oder Stunden Verzögerung bei der Anwendung von Änderungen führen kann.

## Best Practices zum Ändern einer externen Datenbanktabelle

Adobe empfiehlt, die folgenden Schritte auszuführen, wenn Sie eine Spalte zu einer Kerndatenbanktabelle oder einer Drittanbietertabelle hinzufügen:

1. Erstellen Sie ein Modul mit einem Namen in Ihrem Namespace, der das darstellt, was Sie aktualisieren.

   Beispiel: `app/code/YourCompany/Customer`

1. Erstellen Sie die entsprechenden Dateien, um das Modul zu aktivieren (siehe [Modul erstellen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Erstellen Sie eine Datei mit dem Namen `db_schema.xml` im `etc` und nehmen Sie die entsprechenden Änderungen vor.

   Falls zutreffend, generieren Sie eine `db_schema_whitelist.json` -Datei. Siehe [Deklaratives Schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} für weitere Informationen.

### Potenzielle Auswirkungen

Das Hinzufügen einer Spalte zu einer externen Datenbank kann sich auf folgende Weise auf Ihr Adobe Commerce-Projekt auswirken:

- Upgrades könnten komplizierter sein.
- Bereitstellungen sind betroffen, wenn die zu ändernde Tabelle groß ist.
- Die Migration zu einer neuen Plattform könnte komplizierter sein.

## Methoden zum Vermeiden von Änderungen an Kerntabellen

Sie können eine Änderung der Adobe Commerce-Datenbanktabellen vermeiden, indem Sie [Erweiterungsattribute](#migrate-legacy-data-with-extension-attributes). Eine weitere Alternative ist die Verwendung einer speziellen Spalte (`additional_data`) in einigen Kerntabellen gefunden werden, um Daten zu speichern und sie im JSON-kodierten Format zu speichern.

### Daten in einer JSON-kodierten Datenspalte speichern

Einige Kerntabellen verfügen über eine `additional_data` -Spalte, die JSON-kodierte Daten enthält. Diese Spalte bietet eine native Möglichkeit, zusätzliche Daten in einem Feld zuzuordnen. Mit dieser Methode wird verhindert, dass eine Tabelle für kleine, einfache Datenelemente hinzugefügt wird, die Informationen zum Datenabruf ohne Suchanforderung speichern. Die `additional_data` -Spalte ist normalerweise nur auf Artikelebene verfügbar, nicht aber für das gesamte Anführungszeichen oder die gesamte Bestellung.

- Vorteile der Verwendung der `additional_data` field

   - Es sind keine zusätzlichen Felder erforderlich, sodass die Anzahl der Spalten minimal bleibt. Dies ist im Verkaufsfluss hilfreich, wo bereits viele Tabellen enthalten sind. Es ist am besten, diesen bereits komplizierten Prozess nicht noch komplexer zu gestalten. Diese Methode erfüllt viele Anwendungsfälle, aber nicht alle.

- Nachteile

   - Diese Methode eignet sich nur zum Speichern schreibgeschützter Daten. Dieses Problem tritt auf, weil unser Code nicht serialisiert werden muss, um das Objekt zu ändern und zu erstellen, um Abhängigkeiten oder Datenbankbeziehungen hinzuzufügen.

   - Es ist schwierig, Datenbankvorgänge zu verwenden, um nach diesen Feldern zu suchen. Mit dieser Methode zu suchen ist langsam.

   - Bei der Speicherung von Daten im `additional_data` -Spalte, um zu vermeiden, dass Serialisierungs- oder Unserialisierungsvorgänge ausgelöst werden, die den Code beschädigen könnten, indem ungültige JSON erstellt wird oder während der Laufzeit Lesefehler auftreten.

   - Diese Felder müssen im Code klar deklariert sein, damit sie ein Entwickler leicht finden kann.

   - Andere Probleme, die auftreten können, können sehr schwer zu diagnostizieren sein. Zum Beispiel mit einigen nativen PHP-Funktionen, wenn Sie nicht verwenden [!DNL Adobe Commerce] Wrapper-Methoden, die von der Kernanwendung bereitgestellt werden, kann das Endergebnis der umgewandelten Daten vom erwarteten Format abweichen. Verwenden Sie immer die Wrapper-Funktionen, um die Konsistenz und Vorhersagbarkeit der zu speichernden oder abgerufenen Daten sicherzustellen.

Im Folgenden finden Sie Beispiele für Tabellen mit Spalten und Struktur für die Variablen `additional_data` Spalte.

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
