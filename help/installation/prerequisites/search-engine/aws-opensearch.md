---
title: AWS OpenSearch
description: Führen Sie diese Schritte aus, um den AWS OpenSearch-Webdienst für lokale Installationen von Adobe Commerce zu konfigurieren.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 unterstützt die Verwendung von Amazon OpenSearch Service-Clustern. Dieser Dienst ist der Nachfolger von Amazon Elasticsearch Service. Hier wird beschrieben, wie Sie Commerce für die Verwendung von AWS OpenSearch konfigurieren und Daten von einem lokalen Elasticsearch oder einer OpenSearch-Instanz in einen AWS OpenSearch-Cluster migrieren.

## Erstellen einer AWS OpenSearch-Dienstdomäne

Sie müssen zunächst eine OpenSearch-Instanz in AWS einrichten.
Detaillierte Anweisungen finden Sie unter [Erstellen und Verwalten von Amazon OpenSearch Service-Domänen](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) .

## Abrufen von Daten zu AWS OpenSearch

Sobald alles auf AWS vorbereitet ist, ist es an der Zeit, es mit Daten zu füllen.

Für kleinere Installationen wird empfohlen, Indizes aus folgenden Gründen direkt in der AWS-Instanz zu erstellen:

* Die Neuerstellung der Indizes ist ein schneller Vorgang.
* Es kann zu Versionsinkompatibilitäten zwischen der alten Instanz und der AWS-Instanz kommen. Diese können vermieden werden, indem Sie direkt auf der AWS-Instanz aufbauen.

Bei größeren Installationen ist es empfehlenswert, ihre Datenindizes von der vorhandenen Instanz nach AWS zu migrieren. Dies kann zwar zu Ausfallzeiten führen, es besteht aber dennoch ein geringes Risiko von Inkompatibilitätsproblemen aufgrund unterschiedlicher Versionen zwischen dem alten Elasticsearch-Server und AWS.

Sie müssen keine Indizes migrieren, da diese einfach in der AWS-Instanz neu erstellt werden können.
Stellen Sie jedoch bei der Migration von Datenindizes sicher, dass die Versionen von Elasticsearch/OpenSearch kompatibel sind.

Weitere Informationen finden Sie in den Anweisungen von Amazon für die [Migration zu Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) .

### Konfigurieren von Commerce für OpenSearch

Die Schritte zum Konfigurieren von OpenSearch werden im Thema [Erweiterte Installation](../../advanced.md) beschrieben.

Um zu testen, ob die neue Konfiguration funktioniert, testen Sie den OpenSearch-Endpunkt direkt:

1. Erstellen Sie ein Produkt in der Admin-Konsole (z. B. sku=&quot;testproduct1&quot;).
1. Neuindizieren über den Administrator.
1. Abfragen des OpenSearch-Endpunkts (in der AWS-Benutzeroberfläche):

   Um Indizes zu erhalten, hängen Sie Folgendes an die URL an: `/_cat/indices/*?v=true`:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Um Produkte aus dem Index zu erhalten, hängen Sie Folgendes an: `/magento2docker_product_1/_search?q=*` an die URL an:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Zusätzliche Ressourcen

Weitere Informationen finden Sie in der Dokumentation zu [OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html) .
