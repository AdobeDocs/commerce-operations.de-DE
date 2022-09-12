---
title: Suchmaschinenübersicht
description: Überblick über Suchmaschinenoptionen für Adobe Commerce und Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Suchmaschinenübersicht

Ab Version 2.4.4 erfordert Adobe Commerce und Magento Open Source entweder [Elasticsearch] oder [OpenSearch] zur Katalogsuchmaschine. Frühere Versionen von 2.4.x benötigten Elasticsearch. Weitere Informationen zum Installieren einer Suchmaschine und zur Erstkonfiguration finden Sie in den folgenden Themen:

- [Voraussetzungen für Suchmaschinen]
- [Konfigurieren von nginx für Ihre Suchmaschine]
- [Konfigurieren von Apache für Ihre Suchmaschine]
- [Commerce-Software installieren] (Befehlszeilenschnittstelle)

Nach der Installation und Integration Ihrer Suchmaschine in Adobe Commerce müssen Sie zusätzliche Wartungsarbeiten durchführen:

- [Konfigurieren von Suchbegriffen](search-stopwords.md)
- [Suchmaschinenkonfiguration](configure-search-engine.md)

<!-- Link Definitions -->

[Voraussetzungen für Suchmaschinen]: ../../installation/prerequisites/search-engine/overview.md
[Konfigurieren von nginx für Ihre Suchmaschine]: ../../installation/prerequisites/search-engine/configure-nginx.md
[Konfigurieren von Apache für Ihre Suchmaschine]: ../../installation/prerequisites/search-engine/configure-apache.md
[Elasticsearch]: https://www.elastic.co
[Commerce-Software installieren]: ../../installation/composer.md
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
