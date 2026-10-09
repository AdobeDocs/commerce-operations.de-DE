---
title: AWS OpenSearch
description: Führen Sie diese Schritte aus, um den AWS OpenSearch-Webservice für lokale Installationen von Adobe Commerce zu konfigurieren.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%
---
# AWS OpenSearch

Adobe Commerce 2.4.5 unterstützt die Verwendung von Amazon OpenSearch-Service-Clustern. Dieser Service ist der Nachfolger von Amazon Elasticsearch Service. In diesem Abschnitt wird beschrieben, wie Sie Commerce für die Verwendung von AWS OpenSearch konfigurieren und Daten von einer lokalen Elasticsearch- oder OpenSearch-Instanz zu einem AWS OpenSearch-Cluster migrieren.

## Erstellen einer AWS OpenSearch-Service-Domain

Zunächst müssen Sie eine OpenSearch-Instanz in AWS einrichten.
Detaillierte [ finden Sie unter „Erstellen und Verwalten ](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) Amazon OpenSearch-Service-Domains“.

## Abrufen von Daten zu AWS OpenSearch

Sobald alles in AWS vorbereitet ist, ist es an der Zeit, es mit Daten zu füllen.

Für kleinere Installationen empfehlen wir aus den folgenden Gründen, Indizes direkt auf der AWS-Instanz zu erstellen:

* Das Neuerstellen der Indizes ist ein schneller Vorgang.
* Es kann zu Versionsinkompatibilitäten zwischen der alten Instanz und der AWS-Instanz kommen. Diese können vermieden werden, indem direkt auf der AWS-Instanz erstellt wird.

Bei größeren Installationen empfiehlt es sich möglicherweise, die Datenindizes von der bestehenden Instanz zu AWS zu migrieren. Dadurch können Ausfallzeiten verringert werden. Es besteht jedoch ein geringes Risiko von Inkompatibilitätsproblemen aufgrund unterschiedlicher Versionen zwischen dem alten Elasticsearch-Server und AWS.

Sie müssen keine Indizes migrieren, da diese einfach auf der AWS-Instanz neu erstellt werden können.
Stellen Sie jedoch beim Migrieren von Datenindizes sicher, dass die Versionen von Elasticsearch/OpenSearch kompatibel sind.

Weitere Informationen finden Sie in [ Anleitung zur Migration zum Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html)Service von Amazon.

### Konfigurieren von Commerce für OpenSearch

Die Schritte zum Konfigurieren von OpenSearch werden im Abschnitt [Erweiterte Installation](../../advanced.md) beschrieben.

Um zu testen, ob die neue Konfiguration funktioniert, testen Sie den OpenSearch-Endpunkt direkt:

1. Erstellen Sie ein Produkt in der Admin Console (zum Beispiel: sku=„testproduct1„).
1. Neuindizierung über den Administrator.
1. Fragen Sie den OpenSearch-Endpunkt (in der AWS-Benutzeroberfläche) ab:

   Um Indizes abzurufen, hängen Sie `/_cat/indices/*?v=true` an die URL an:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Um Produkte aus dem Index abzurufen, hängen Sie `/magento2docker_product_1/_search?q=*` an die URL an:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Zusätzliche Ressourcen

Weitere Informationen finden Sie in der [OpenSearch AWS-Dokumentation](https://docs.aws.amazon.com/opensearch-service/index.html).
