---
title: Erweiterte Einrichtung
description: Lesen Sie Best Practices und Empfehlungen für große Unternehmenssysteme, die für die Verarbeitung großer Datenmengen entwickelt wurden.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# Erweiterte Einrichtung

[!DNL Commerce] ist ein hochflexibles und skalierbares Produkt, das Lösungen für Händler aller Größen enthält. In diesem Abschnitt werden Best Practices und Empfehlungen zur Konfiguration von [!DNL Commerce] für die Verwendung mit großen Datenmengen, extremer Auslastung und anderen Fällen für Unternehmen beschrieben.

## Indexleistung kalibrieren

Bei großen Datenmengen kann die Neuindizierung zu einem Problem werden. Das [!DNL Commerce]-Team wählte die am meisten geladenen Indizes aus und aktivierte die Batch-Indizierung, mit der Sie einen Teil der Daten festlegen können, der bei jeder Iteration verarbeitet werden soll. Auf diese Weise kann der Benutzer die Batch-Größen basierend auf dem Typ und der Größe der Daten in der Datenbank anpassen.

Um diese Einstellung zu verwalten, bearbeiten Sie den Parameter `batchRowsCount` in der Datei `di.xml` des entsprechenden Moduls. Die folgenden Indizes unterstützen diese Funktion:

* Kategorieproduktindex (Katalogmodul)
* Preisindex (Katalogmodul)
* EAV-Index (Katalogmodul)
* Aktienindex (CatalogInventory-Modul)

Sie können die Indexleistung anpassen, indem Sie die Variablen für die Indexstapelgröße anpassen. Dadurch wird gesteuert, wie viele Entitäten gleichzeitig vom Indexer verarbeitet werden. In einigen Fällen ist die Indizierungszeit erheblich zurückgegangen.

Wenn Sie beispielsweise ein Profil ausführen, das B2B Medium ähnelt, können Sie den Konfigurationswert `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` überschreiben und den Standardwert `5000` in `1000` überschreiben. Dadurch wird die vollständige Indizierungszeit von 4 Stunden auf 2 Stunden mit einer standardmäßigen [!DNL MySQL] -Konfiguration reduziert.

>[!NOTE]
>
>Die Stapelverarbeitung für den Indexer für Katalogregeln wurde nicht aktiviert. Händler mit einer großen Anzahl von Katalogregeln müssen ihre [!DNL MySQL] -Konfiguration anpassen, um die Indizierungszeit zu optimieren. In diesem Fall wird durch die Bearbeitung Ihrer [!DNL MySQL] -Konfigurationsdatei und die Zuweisung von mehr Speicher zu den Konfigurationswerten TMP_TABLE_SIZE und MAX_HEAP_TABLE_SIZE (die Standardeinstellung ist 16M für beide) die Leistung für diesen Indexer verbessert, aber [!DNL MySQL] verbraucht mehr RAM.

### Beschränken von Kundengruppen und freigegebenen Katalogen nach Websites

Eine große Anzahl von Produkt-SKUs, Websites, Kundengruppen oder freigegebenen Katalogen wirkt sich auf die Laufzeit der Indexer für Produktpreise und Katalogregeln aus. Dies liegt daran, dass alle Websites standardmäßig allen Kundengruppen (freigegebenen Katalogen) zugewiesen sind.

Um die Indexierungszeit zu verkürzen, können Sie [bestimmte Websites aus Kundengruppen ausschließen (freigegebene Kataloge)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Einrichten von Redis

Manchmal reicht eine Redis-Instanz nicht aus, um eingehende Anfragen zu verarbeiten. Es gibt mehrere Lösungen, die wir empfehlen können, um diese Situation zu beheben.

Mit [!DNL Commerce] können Sie zunächst für jeden Cache-Typ einen separaten Cache-Speicher konfigurieren. Dadurch können Sie so viele separate Redis-Instanzen installieren wie die Anzahl der im Magento registrierten Cache-Typen. In der Praxis sollten Sie Redis-Instanzen für die am meisten verwendeten Caches wie Konfiguration, Layout und Blöcke verwenden.

Eine andere Lösung kann sein, den Konfigurations-Cache im Dateisystem zu platzieren und die anderen Caches auf den Redis-Server zu verschieben. Mit dieser Lösung benötigen Sie ein separates Tool für die zentralisierte Invalidierung des Konfigurations-Caches auf allen Ihren Web-Knoten.

Sie können auch einen Redis-Cluster verwenden, der parallele Lese-/Schreibvorgänge mit einer automatisch steigenden Anzahl von Knoten durchführt. [!DNL Commerce] stellt keine Konfiguration für diesen Fall bereit, kann jedoch mit geringfügigen Anpassungen gestartet werden.

## Einrichten von [!DNL RabbitMQ]

Adobe Commerce unterstützt Nachrichtenwarteschlangen, die über [!DNL RabbitMQ] implementiert wurden. [!DNL Commerce] verwendet diesen Dienst für die Ausführung zahlreicher asynchroner Vorgänge, einschließlich B2B-Katalogoperationen und asynchroner Lageraktualisierungen. Alle Schnittstellen zum Hinzufügen von mehr Aufträgen zum Auftrags-Server werden mit dem Produkt verteilt und sind für die benutzerdefinierte asynchrone Logikimplementierung im Rahmen von Drittanbieter-Erweiterungen verfügbar. Wie bei jeder anderen Integration stellt [!DNL Commerce] eine Beispielkonfigurationsdatei für [!DNL RabbitMQ] bereit, die alle empfohlenen Einstellungen enthält und vollständig für die Produktionsverwendung bereit ist.

## Datenbank aufteilen

>[!WARNING]
>
>Die Funktion der geteilten Datenbank war in Version 2.4.2 von Adobe Commerce [veraltet](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187). Siehe [Von einer geteilten Datenbank auf eine einzelne Datenbank zurücksetzen](../configuration/storage/revert-split-database.md).

Mit Adobe Commerce können Sie skalierbaren Datenbankspeicher konfigurieren, um den Anforderungen eines wachsenden Unternehmens gerecht zu werden. Sie können drei separate Master-Datenbanken einrichten, die bestimmte Domänen bedienen:

* Hauptdatenbank (Katalog)
* Checkout-Datenbank
* Datenbank für Order Management-Systeme (OMS)

Um zusätzliche Datenbanken zu konfigurieren, müssen Sie eine leere Datenbank erstellen und einen der folgenden Befehle ausführen:

Für Checkout Master DB

```bash
bin/magento setup:db-schema:split-quote
```

Für OMS Master DB

```bash
bin/magento setup:db-schema:split-sales
```

Mit diesen Befehlen werden bestimmte Domänentabellen aus der Hauptdatenbank in eine Domänendatenbank migriert. Außerdem wird die [!DNL Commerce] -Konfiguration geändert, um eine entsprechende Konnektivität und Begrenzungsverarbeitung zu ermöglichen.

Durch separate Datenbanken für den Checkout und Order Management können Sie die Auslastung zwischen Ihren Datenbankservern verteilen. Sie können mehr Kassengänge bedienen und mehr Bestellungen pro Sekunde verarbeiten, ohne die Verfügbarkeit Ihres Katalogs und anderer Vorgänge zu beeinträchtigen. Es wird empfohlen, Datenbanken für Zeiträume von Flash- oder aktiven Verkäufen zu teilen oder sie dauerhaft für natürlich hochbelastete Projekte zu verwenden. Die Migration vorhandener Daten zwischen Datenbanken sollte unter der Aufsicht Ihres Systemadministrators erfolgen.  Teilen Sie die Datenbanken nicht auf, während Sie sich im Produktionsmodus befinden.

Zusätzlich zu den Master-Datenbanken können Sie mit [!DNL Commerce] eine Reihe von Slave-Datenbanken konfigurieren (eine für jede im System deklarierte Datenressource). Eine Slave-Datenbank dient als vollständige Replikation Ihrer Hauptdatenbank oder einer Ihrer Domain-Master-Datenbanken. Sie wird für Lesevorgänge für eine bestimmte Ressource ausgegeben.

Sie können eine Slave-Datenbank hinzufügen, indem Sie den folgenden Befehl ausführen:

```bash
bin/magento setup:db-schema:add-slave
```

Dieser Befehl führt Konfigurationsänderungen durch, konfiguriert jedoch nicht die Replikation selbst. Dies sollte manuell erfolgen.

Nach dem Teilen Ihrer Master-Datenbank und dem Einrichten von Slave-Datenbanken reguliert [!DNL Commerce] automatisch Verbindungen zu einer bestimmten Datenbank, trifft Entscheidungen basierend auf dem Anforderungstyp (POST, PUT, GET usw.) und der Datenressource. Wenn [!DNL Commerce] oder seine Erweiterungen Schreibvorgänge für eine GET-Anfrage ausführen, wechselt das System automatisch die Verbindung von Slave zu Master-Datenbank. Dies funktioniert genauso mit Master-Datenbanken: Sobald Sie mit einer Checkout-Tabelle arbeiten, leitet das System alle Abfragen an eine bestimmte Datenbank weiter. In der Zwischenzeit werden alle katalogbezogenen Abfragen an die Hauptdatenbank gesendet.

Weitere Informationen zur Konfiguration und zu den Vorteilen der Master-/Slave-Konfiguration finden Sie unter
[Lösung zur Aufspaltung der Datenbankleistung](../configuration/storage/multi-master.md).

## Bereitstellen von Medieninhalten

Magento bietet keine spezielle Integration für die Bereitstellung und Bereitstellung von Medieninhalten. Alle gängigen Ansätze können gemeinsam im Magento verwendet werden.

Die einfachste Methode zur Bereitstellung von Medieninhalten besteht darin, diese auf einem [!DNL Varnish] -Server bereitzustellen und zu zwischenspeichern. Bei diesem Ansatz wird davon ausgegangen, dass entweder ein freigegebenes Dateisystem zum Speichern von Medieninhalten oder ein dedizierter Server mit Verweis auf [!DNL Varnish] vorhanden ist.

Für Umgebungen mit mittlerer und hoher Auslastung empfehlen wir die Verwendung von CDN-Diensten (Content Delivery Network) wie Fastly, Akamai und anderen. Beim Arbeiten mit diesen Diensten verwendet [!DNL Commerce] den klassischen Pull-Ansatz für Inhaltsaktualisierungen. Sie müssen [!DNL Commerce]-URLs für die Verwendung mit dem entsprechenden CDN-Dienst konfigurieren. Durch das Verschieben von Medieninhalten in ein CDN wird die Belastung Ihrer Instanzen erheblich verringert.

## Konfigurieren des Protokollspeichers

Die Speicherung von Protokollen und ihr Einfluss auf andere Festplattenvorgänge wirken sich auf die Verfügbarkeit Ihrer Webknoten aus, insbesondere in Situationen mit hoher Auslastung. Es wird empfohlen, die Protokollierung zu minimieren, wenn Sie sie nicht benötigen. Sie können die Protokollierung auch so konfigurieren, dass sie in ein separates Speichersystem mit hoher Zugriffsgeschwindigkeit geschrieben wird. Beachten Sie, dass sich Engpässe beim Zugriff auf die Protokollspeicherung direkt auf die Verarbeitung eingehender Anfragen auswirken können, die Schreibvorgänge oder Lesevorgänge protokollieren, die Teil ihres Datenflusses sind.
