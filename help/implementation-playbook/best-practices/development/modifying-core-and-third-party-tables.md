---
title: Best Practices für das Ändern von Datenbanktabellen
description: Erfahren Sie, wie und wann Adobe Commerce- und Datenbanktabellen von Drittanbietern geändert werden.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# Best Practices für das Ändern von Datenbanktabellen

Dieser Artikel enthält Best Practices zum Ändern von Datenbanktabellen, die von [!DNL Adobe Commerce] oder Drittanbietermodulen erstellt werden. Wenn Sie verstehen, wann und wie Sie Tabellen effektiv ändern können, können Sie die langfristige Lebensfähigkeit und Stabilität Ihrer Commerce-Plattform sicherstellen.

Für die Migration von [!DNL Magento 1] und anderen E-Commerce-Plattformen oder für die Arbeit mit Modulen aus dem [!DNL Adobe Commerce] Marketplace müssen möglicherweise zusätzliche Daten hinzugefügt und gespeichert werden. Der erste Instinkt kann darin bestehen, einer Datenbanktabelle eine Spalte hinzuzufügen oder eine vorhandene Tabelle anzupassen. Sie sollten eine [!DNL Adobe Commerce]-Kerntabelle (oder Drittanbietertabelle) jedoch nur in bestimmten Situationen ändern.

## Warum Adobe empfiehlt, Änderungen zu vermeiden

Der Hauptgrund dafür, dass Sie keine Kerntabellen ändern müssen, besteht darin, dass Adobe Commerce eine zugrunde liegende Logik enthält, die SQL-Rohabfragen enthält. Änderungen an der Struktur der Tabelle können zu unerwarteten Nebenwirkungen führen, die schwer zu beheben sind. Die Änderung kann sich auch auf DDL-Vorgänge (Data Definition Language) auswirken und unerwartete und unvorhersehbare Auswirkungen auf die Leistung haben.

Ein weiterer Grund, weshalb Sie eine Änderung der Datenbanktabellenstruktur vermeiden sollten, besteht darin, dass Ihre Änderungen zu Problemen führen können, wenn das zentrale Entwicklungsteam oder Drittanbieter-Entwickler die Struktur ihrer Datenbanktabellen ändern. Es gibt beispielsweise einige zentrale Datenbanktabellen mit einer Spalte namens `additional_data`. Dies war immer ein `text` Spaltentyp. Aus Leistungsgründen kann das Core-Team die Spalte jedoch in `longtext` ändern. Dieser Spaltentyp ist ein Alias für JSON. Durch die Konvertierung in diesen Spaltentyp werden Leistungsgewinne und Suchmöglichkeiten zu dieser Spalte hinzugefügt, die nicht als `text` existiert. Weitere Informationen zu diesem Thema finden Sie unter [JSON-Datentyp](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Ermitteln, wann Daten gespeichert oder entfernt werden

Adobe empfiehlt, zunächst zu ermitteln, ob diese Daten gespeichert werden müssen. Wenn Sie Daten aus einem Altsystem verschieben, sparen Sie sich durch alle Daten, die Sie entfernen können, Zeit und Mühe bei der Migration. (Es gibt Möglichkeiten, Daten zu archivieren, wenn auf sie später zugegriffen werden muss.) Um ein guter Verwalter der Anwendung und Leistung zu sein, ist es in Ordnung, eine Anfrage zum Speichern zusätzlicher Daten anzufechten. Ihr Ziel besteht darin, sicherzustellen, dass die Speicherung der Daten eine Voraussetzung für die Erfüllung einer Geschäftsanforderung ist, die nicht auf andere Weise erfüllt werden kann.

### Alte Daten

Wenn Ihr Projekt ältere Daten enthält, wie z. B. alte Bestellungen oder Kundendatensätze, sollten Sie eine alternative Suchmethode in Betracht ziehen. Wenn das Unternehmen beispielsweise den Zugriff auf die Daten nur gelegentlich als Referenz benötigt, sollten Sie eine externe Suche der alten Datenbank implementieren, die außerhalb der Commerce-Plattform gehostet wird, anstatt alte Daten nach [!DNL Adobe Commerce] zu migrieren.

In diesem Fall müsste die Datenbank auf einen Server migriert werden, der entweder eine Web-Schnittstelle zum Lesen der Daten oder möglicherweise eine Schulung im Umgang mit MySQL Workbench oder ähnlichen Tools bietet. Der Ausschluss dieser Daten aus der neuen Datenbank beschleunigt die Migration, da sich das Entwicklungs-Team auf die neue Site konzentrieren kann, anstatt Probleme mit der Datenmigration zu beheben.

Eine weitere damit zusammenhängende Option, um die Daten außerhalb von Commerce zu halten, sie jedoch in Echtzeit zu verwenden, besteht darin, andere Tools wie GraphQL Mesh zu nutzen. Diese Option kombiniert verschiedene Datenquellen und gibt sie als eine einzige Antwort zurück.

Sie können beispielsweise alte Bestellungen aus einer externen Datenbank `stitch`, z. B. aus der alten Magento 1-Site, die eingestellt wurde. Zeigen Sie sie dann mithilfe von GraphQL Mesh als Teil des Auftragsverlaufs des Kunden an. Diese alten Bestellungen können mit den Bestellungen aus Ihrer aktuellen [!DNL Adobe Commerce] kombiniert werden.

Weitere Informationen zur Verwendung von API Mesh mit GraphQL finden Sie unter [Was ist API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) und [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrieren von alten Daten mit Erweiterungsattributen

Wenn Sie feststellen, dass ältere Daten migriert werden müssen oder dass neue Daten in [!DNL Adobe Commerce] gespeichert werden müssen, empfiehlt Adobe die Verwendung von [Erweiterungsattributen](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. Die Verwendung von Erweiterungsattributen zum Speichern zusätzlicher Daten bietet die folgenden Vorteile:

- Sie können die beizubehaltenden Daten und die Datenbankstruktur steuern, um sicherzustellen, dass die Daten mit dem richtigen Spaltentyp und den richtigen Indizes gespeichert werden.
- Die meisten Entitäten in [!DNL Adobe Commerce] unterstützen die Verwendung von Erweiterungsattributen.
- Erweiterungsattribute sind ein speicherunabhängiger Mechanismus, der die Flexibilität bietet, die Daten am optimalen Speicherort für Ihr Projekt zu speichern.

Zwei Beispiele für Speicherorte sind Datenbanktabellen und [!DNL Redis]. Bei der Auswahl eines Standorts ist vor allem zu berücksichtigen, ob ein Standort zusätzliche Komplexität mit sich bringt oder die Leistung beeinträchtigt.

### Erwägen anderer Alternativen

Als Entwickler ist es wichtig, immer die Verwendung von Tools außerhalb Ihrer [!DNL Adobe Commerce]-Umgebung in Betracht zu ziehen, z. B. GraphQL Mesh und Adobe App Builder. Diese Tools können Ihnen dabei helfen, den Zugriff auf die Daten zu bewahren, haben jedoch keine Auswirkungen auf die Commerce-Kernanwendung oder die zugrunde liegenden Datenbanktabellen. Mit diesem Ansatz stellen Sie Ihre Daten über eine API zur Verfügung. Anschließend fügen Sie Ihrer App Builder-Konfiguration eine Datenquelle hinzu. Mithilfe von GraphQL Mesh können Sie diese Datenquellen kombinieren und eine einzige Antwort erzeugen, wie in [Legacy-Daten](#legacy-data) beschrieben.

Weitere Informationen zu GraphQL Mesh finden Sie unter [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. Weitere Informationen zum Adobe-App Builder finden Sie unter [Einführung in App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=de){target="_blank"}.

## Ändern einer Kerntabelle oder Drittanbietertabelle

Wenn Sie sich entscheiden, Daten durch Ändern einer [!DNL Adobe Commerce] oder einer Datenbanktabelle von Drittanbietermodulen zu speichern, befolgen Sie die folgenden Richtlinien, um die Auswirkungen auf Stabilität und Leistung zu minimieren.

- Nur neue Spalten hinzufügen.
- Ändern Sie nie den _Typ_-Wert einer vorhandenen Spalte. Ändern Sie beispielsweise keine `integer` in eine `varchar`, um Ihren speziellen Anwendungsfall zu erfüllen.
- Vermeiden Sie das Hinzufügen von Spalten zu EAV-Attributtabellen. Diese Tabellen sind bereits mit Logik und Verantwortung überlastet.
- Bestimmen Sie vor dem Anpassen einer Tabelle deren Größe. Das Ändern großer Tabellen wirkt sich auf die Bereitstellung aus, was beim Anwenden von Änderungen zu Verzögerungen von Minuten oder Stunden führen kann.

## Best Practices für das Ändern einer externen Datenbanktabelle

Adobe empfiehlt, diese Schritte auszuführen, wenn Sie eine Spalte zu einer Core-Datenbanktabelle oder einer Drittanbietertabelle hinzufügen:

1. Erstellen Sie ein Modul mit einem Namen in Ihrem Namespace, der darstellt, was Sie aktualisieren.

   Beispiel: `app/code/YourCompany/Customer`

1. Erstellen Sie die entsprechenden Dateien, um das Modul zu aktivieren (siehe [Erstellen eines Moduls](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=de){target="_blank"}.

1. Erstellen Sie eine Datei mit dem Namen `db_schema.xml` im Ordner `etc` und nehmen Sie die entsprechenden Änderungen vor.

   Generieren Sie ggf. eine `db_schema_whitelist.json`. Weitere Informationen finden [ unter ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"}Deklaratives Schema“.

### Potenzielle Auswirkungen

Das Hinzufügen einer Spalte zu einer externen Datenbank kann sich wie folgt auf Ihr Adobe Commerce-Projekt auswirken:

- Upgrades könnten komplizierter sein.
- Bereitstellungen sind betroffen, wenn die zu ändernde Tabelle groß ist.
- Migrationen auf eine neue Plattform könnten komplizierter sein.

## Vermeiden der Änderung von Kerntabellen

Sie können die Änderung von Adobe Commerce-Datenbanktabellen durch Verwendung von [Erweiterungsattributen](#migrate-legacy-data-with-extension-attributes) vermeiden. Eine weitere Alternative besteht darin, eine spezielle Spalte (`additional_data`) in einigen Kerntabellen zu verwenden, um Daten zu speichern und im JSON-kodierten Format zu speichern.

### Speichern von Daten in einer JSON-kodierten Datenspalte

Einige Kerntabellen verfügen über eine `additional_data`, die JSON-kodierte Daten enthält. Diese Spalte bietet eine native Möglichkeit, zusätzliche Daten in einem Feld zuzuordnen. Durch die Verwendung dieser Methode wird vermieden, dass eine Tabelle für kleine, einfache Datenelemente hinzugefügt wird, die Informationen für den Datenabruf ohne Suchanforderung speichern. Die `additional_data` Spalte ist in der Regel nur auf Artikelebene verfügbar, nicht für das gesamte Angebot oder die gesamte Bestellung.

- Vorteile der Verwendung des `additional_data` Felds

   - Es sind keine zusätzlichen Felder erforderlich, wodurch die Anzahl der Spalten minimal bleibt. Dies ist im Verkaufsablauf hilfreich, bei dem bereits viele Tabellen beteiligt sind. Es ist am besten, diesem ohnehin komplizierten Prozess keine zusätzliche Komplexität zu verleihen. Diese Methode eignet sich für viele Anwendungsfälle, aber nicht für alle.

- Nachteile

   - Diese Methode eignet sich nur zum Speichern schreibgeschützter Daten. Dieses Problem tritt auf, weil der Code nicht serialisiert werden muss, um das -Objekt zu ändern und zu erstellen und Abhängigkeiten oder Datenbankbeziehungen hinzuzufügen.

   - Es ist schwierig, Datenbankoperationen zu verwenden, um nach diesen Feldern zu suchen. Die Suche mit dieser Methode ist langsam.

   - Beim Speichern von Daten in der Spalte `additional_data` müssen Sie besonders vorsichtig sein, um zu vermeiden, dass Serialisierungs- oder Rückserialisierungsvorgänge ausgelöst werden, die den Code beschädigen könnten, indem sie ungültige JSON-Dateien erstellen oder während der Laufzeit Lesefehler verursachen.

   - Diese Felder müssen im Code klar deklariert sein, damit Entwickler sie leicht finden können.

   - Andere Probleme, die auftreten können und sehr schwer zu diagnostizieren sind. Wenn Sie beispielsweise bei einigen nativen PHP-Funktionen keine [!DNL Adobe Commerce] Wrapper-Methoden verwenden, die von der Kernanwendung bereitgestellt werden, kann das Endergebnis der umgewandelten Daten vom erwarteten Format abweichen. Verwenden Sie immer die Wrapper-Funktionen, um Konsistenz und Vorhersehbarkeit der zu speichernden oder abgerufenen Daten sicherzustellen.

Im Folgenden finden Sie Beispiele für Tabellen mit der Spalte und der Struktur für die `additional_data` Spalte.

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

In den Versionen 2.4.3, 2.4.4 und 2.4.5 gibt es zehn Tabellen mit den Spalten `additional_data`.

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
