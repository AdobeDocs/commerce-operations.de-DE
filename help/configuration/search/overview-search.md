---
title: Suchmaschinenübersicht
description: Überblick über Suchmaschinenoptionen für Adobe Commerce und Magento Open Source.
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
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

[Voraussetzungen für Suchmaschinen]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[Konfigurieren von nginx für Ihre Suchmaschine]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[Konfigurieren von Apache für Ihre Suchmaschine]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Commerce-Software installieren]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
