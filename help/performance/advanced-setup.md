---
title: Erweitertes Setup
description: Erfahren Sie, wie Sie das erweiterte Setup für Adobe Commerce einrichten. Hier finden Sie Schritt-für-Schritt-Anweisungen und Konfigurationsanforderungen.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: da9ce645d4d32c1368da442d9bd260f5fb3cdb98
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# Erweitertes Setup

[!DNL Commerce] ist ein hochflexibles und skalierbares Produkt, das Lösungen für Händler jeder Größe enthält. Dieser Abschnitt enthält Best Practices und Empfehlungen zur Konfiguration von [!DNL Commerce] für die Arbeit mit großen Datenmengen, extremer Auslastung und anderen Unternehmensfällen.

## Indexleistung kalibrieren

Bei großen Datenmengen kann die Neuindizierung ein Problem darstellen. Das [!DNL Commerce]-Team hat die am häufigsten geladenen Indizes ausgewählt und die Batch-Indizierung aktiviert, mit der Sie einen Teil der Daten festlegen können, die bei jeder Iteration verarbeitet werden sollen. Auf diese Weise kann der Benutzer die Batch-Größen auf der Grundlage des Typs und der Größe der Daten in der Datenbank anpassen.

Um diese Einstellung zu verwalten, bearbeiten Sie den `batchRowsCount` in der `di.xml` des entsprechenden Moduls. Die folgenden Indizes unterstützen diese Funktion:

* Kategorie-Produktindex (Modul Katalog)
* Preisindex (Modul Katalog)
* EAV Index (Catalog Module)
* Aktienindex (CatalogInventory-Modul)

Sie können die Indexerleistung anpassen, indem Sie die Variablen für die Batch-Größe des Index anpassen. Dadurch wird gesteuert, wie viele Entitäten gleichzeitig vom Indexer verarbeitet werden. In einigen Situationen haben wir erhebliche Verringerungen bei der Indizierungszeit erlebt.

Wenn Sie beispielsweise ein Profil ausführen, das dem B2B-Medium ähnelt, können Sie den in `batchRowsCount` `app/code/Magento/catalog/etc/di.xml` Konfigurationswert überschreiben und den Standardwert von `5000` bis `1000` überschreiben. Dadurch wird die gesamte Indizierungszeit bei einer standardmäßigen [!DNL MySQL]-Konfiguration von 4 auf 2 Stunden reduziert.

>[!NOTE]
>
>Für den Katalogregeln-Indexer wurde kein Batch aktiviert. Händler mit einer großen Anzahl von Katalogregeln müssen ihre [!DNL MySQL] anpassen, um die Indizierungszeit zu optimieren. In diesem Fall verbessert das Bearbeiten Ihrer [!DNL MySQL]-Konfigurationsdatei und das Zuweisen von mehr Speicher zu den Konfigurationswerten „TMP_TABLE_SIZE“ und &quot;MAX_HEAP_TABLE_SIZE“ (der Standardwert ist 16M für beide) die Leistung dieses Indexers, führt jedoch zu [!DNL MySQL] höheren RAM-Verbrauch.

### Begrenzen von Kundengruppen und freigegebenen Katalogen nach Websites

Eine große Anzahl von Produkt-SKUs, Websites, Kundengruppen oder freigegebenen Katalogen wirkt sich auf die Laufzeit der Indizierungen für Produktpreise und Katalogregeln aus. Dies liegt daran, dass standardmäßig alle Websites allen Kundengruppen (freigegebenen Katalogen) zugewiesen sind.

Um die Indexierungszeit zu verkürzen, können Sie [bestimmte Websites aus Kundengruppen (freigegebene Kataloge) ausschließen](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Einrichten von Redis

Manchmal reicht eine Redis-Instanz nicht aus, um eingehende Anfragen zu bedienen. Es gibt mehrere Lösungen, die wir empfehlen können, um diese Situation zu beheben.

Zunächst können Sie mit [!DNL Commerce] für jeden Cache-Typ einen separaten Cache-Speicher konfigurieren. Auf diese Weise können Sie so viele separate Redis-Instanzen installieren wie Cache-Typen, die in Magento registriert sind. Realistisch betrachtet empfiehlt es sich, Redis-Instanzen für die am häufigsten verwendeten Caches zu verwenden, z. B. für Konfiguration, Layout und Blöcke.

Eine andere Lösung kann darin bestehen, den Konfigurations-Cache auf dem Dateisystem zu platzieren und die anderen Caches auf den Redis-Server zu verschieben. Mit dieser Lösung benötigen Sie ein separates Tool zur zentralisierten Invalidierung des Konfigurations-Caches auf allen Ihren Web-Knoten.

Sie können auch einen Redis-Cluster verwenden, der parallele Lese-/Schreibvorgänge mit einer automatisch wachsenden Anzahl von Knoten durchführt. [!DNL Commerce] stellt keine Konfiguration für diesen Fall bereit, kann jedoch mit geringfügigen Anpassungen gestartet werden.

## Einrichten von [!DNL RabbitMQ]

Adobe Commerce unterstützt Nachrichtenwarteschlangen, die über [!DNL RabbitMQ] implementiert werden. [!DNL Commerce] verwendet diesen Service zum Ausführen zahlreicher asynchroner Vorgänge, einschließlich B2B-Katalogvorgängen und asynchroner Stock-Aktualisierungen. Alle Schnittstellen zum Hinzufügen weiterer Aufträge zum Auftrags-Server sind mit dem Produkt verteilt und stehen für benutzerdefinierte asynchrone Logikimplementierungen im Umfang von Erweiterungen von Drittanbietern zur Verfügung. Wie bei jeder anderen Integration bietet [!DNL Commerce] eine Beispielkonfigurationsdatei für [!DNL RabbitMQ], die alle empfohlenen Einstellungen enthält und für die Verwendung in der Produktion vollständig bereit ist.

## Aufspalten der Datenbank

>[!WARNING]
>
>Die Funktion „Split Database[&#x200B; wurde in &#x200B;](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 2.4.2 von Adobe Commerce als veraltet gekennzeichnet. Siehe [Von einer geteilten Datenbank auf eine einzelne Datenbank zurücksetzen](../configuration/storage/revert-split-database.md).

Mit Adobe Commerce können Sie skalierbaren Datenbankspeicher konfigurieren, um den Anforderungen eines wachsenden Unternehmens gerecht zu werden. Sie können drei separate Master-Datenbanken für bestimmte Domains einrichten:

* Hauptdatenbank (Katalog)
* Checkout-Datenbank
* Order Management System (OMS)-Datenbank

Um zusätzliche Datenbanken zu konfigurieren, müssen Sie eine leere Datenbank erstellen und einen der folgenden Befehle ausführen:

Für Checkout-Master-DB

```bash
bin/magento setup:db-schema:split-quote
```

Für OMS-Master-DB

```bash
bin/magento setup:db-schema:split-sales
```

Diese Befehle migrieren bestimmte Domain-Tabellen von der Hauptdatenbank in eine Domain-Datenbank. Sie ändern auch die [!DNL Commerce], um die entsprechende Konnektivität und Verarbeitungseinschränkungen zu ermöglichen.

Durch separate Datenbanken für Checkout und Order Management können Sie die Last zwischen Ihren Datenbankservern verteilen. Sie können mehr Checkouts bereitstellen und mehr Bestellungen pro Sekunde verarbeiten, ohne die Verfügbarkeit Ihres Katalogs und anderer Vorgänge zu beeinträchtigen. Wir empfehlen, Datenbanken für Zeiträume des Flash- oder aktiven Verkaufs aufzuteilen oder dauerhaft für natürlich hochladende Projekte zu verwenden. Die Migration vorhandener Daten zwischen Datenbanken sollte unter der Aufsicht Ihres Systemadministrators erfolgen.  Trennen Sie Datenbanken nicht im Produktionsmodus.

Zusätzlich zu den Master-Datenbanken können Sie mit [!DNL Commerce] eine Reihe von Slave-Datenbanken konfigurieren (eine für jede im System deklarierte Datenressource). Eine Slave-Datenbank dient als vollständige Replikation Ihrer Hauptdatenbank oder einer Ihrer Domain-Master-Datenbanken. Sie wird für Lesevorgänge für eine bestimmte Ressource ausgegeben.

Sie können eine Slave-Datenbank hinzufügen, indem Sie den folgenden Befehl ausführen:

```bash
bin/magento setup:db-schema:add-slave
```

Mit diesem Befehl werden Konfigurationsänderungen durchgeführt, die Replikation wird jedoch nicht selbst konfiguriert. Dies sollte manuell geschehen.

Nach dem Aufteilen der Master-Datenbank und dem Einrichten der Slave-Datenbanken regelt [!DNL Commerce] automatisch die Verbindungen zu einer bestimmten Datenbank, wobei Entscheidungen auf der Grundlage der Art der Anfrage (POST, PUT, GET usw.) und der Datenressource getroffen werden. Wenn [!DNL Commerce] oder seine Erweiterungen Schreibvorgänge für eine GET-Anfrage durchführen, wechselt das System automatisch die Verbindung vom Slave zur Master-Datenbank. Dies funktioniert genauso wie bei Master-Datenbanken: Sobald Sie mit einer Checkout-bezogenen Tabelle arbeiten, leitet das System alle Abfragen an eine bestimmte Datenbank weiter. In der Zwischenzeit werden alle Katalogabfragen an die Hauptdatenbank gesendet.

Weitere Informationen zur Konfiguration und den Vorteilen mehrerer Master/Slave-Konfigurationen finden Sie unter
[Split-Datenbankleistungslösung](../configuration/storage/multi-master.md).

## Bereitstellen von Medieninhalten

Magento bietet keine spezielle Integration zur Bereitstellung und Bereitstellung von Medieninhalten. In Magento können alle gängigen Ansätze zusammen verwendet werden.

Die einfachste Möglichkeit, Medieninhalte bereitzustellen, besteht darin, sie auf einem [!DNL Varnish]-Server bereitzustellen und zwischenzuspeichern. Bei diesem Ansatz wird entweder von einem freigegebenen Dateisystem zum Speichern von Medieninhalten oder einem dedizierten Server ausgegangen, der auf [!DNL Varnish] verweist.

Für Umgebungen mit mittlerer und hoher Last empfehlen wir die Verwendung von CDN-Services (Content Delivery Network) wie Fastly, Akamai und anderen. Bei der Arbeit mit diesen Services verwendet [!DNL Commerce] den klassischen Pull-Ansatz für Inhaltsaktualisierungen. Sie müssen [!DNL Commerce] URLs konfigurieren, damit sie mit dem entsprechenden CDN-Service funktionieren. Indem Sie Medieninhalte in ein CDN verschieben, verringern Sie die Last für Ihre Instanzen erheblich.

## Konfigurieren des Protokollspeichers

Das Speichern von Protokollen und deren Einfluss auf andere Datenträgervorgänge wirkt sich auf die Verfügbarkeit Ihrer Web-Knoten aus, insbesondere in Situationen mit hoher Auslastung. Wir empfehlen, die Protokollierung zu minimieren, wenn Sie sie nicht benötigen. Sie können die Protokollierung auch so konfigurieren, dass sie auf ein separates Speichersystem mit hohen Zugriffsgeschwindigkeiten schreibt. Beachten Sie, dass Engpässe beim Zugriff auf die Protokollspeicherung sich direkt auf die Verarbeitung eingehender Anfragen auswirken können, die Schreib- oder Lesevorgänge als Teil ihres Flusses protokollieren.
