---
title: Aktuelle Suchmaschine wird nicht unterstützt
description: Führen Sie eine Fehlerbehebung bei Ihrem Adobe Commerce- oder Magento Open Source-Upgrade durch, nachdem ein Fehler bezüglich einer nicht unterstützten Suchmaschine aufgetreten ist.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# Aktuelle Suchmaschine wird nicht unterstützt

Die folgende Fehlermeldung weist darauf hin, dass die Magento-Version, von der Sie ein Upgrade durchführen, für die Verwendung einer Katalogsuchmaschine konfiguriert ist, die in der Magento-Version, auf die Sie ein Upgrade durchführen, nicht unterstützt wird:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Dieser Fehler bedeutet, dass eine der folgenden Bedingungen auf der Abwärtsversion von Adobe Commerce oder Magento Open Source zutrifft:

- Die Suchmaschine ist auf MySQL eingestellt.
- Die Suchmaschine ist auf eine Version des Elasticsearchs festgelegt, die nicht mehr unterstützt wird.

Verwenden Sie den folgenden Befehl, um die aktuelle Suchmaschine zu überprüfen:

```bash
bin/magento config:show catalog/search/engine
```

Der Fehler tritt auf, wenn der zurückgegebene Wert `mysql` oder `elasticsearch`.

>[!WARNING]
>
>Wenn Sie diesen Fehler erhalten haben, befindet sich das Magento in einem inkonsistenten Zustand und Sie können nicht auf den Administrator zugreifen. Es wird empfohlen, zur vorherigen Version zurückzukehren, während Sie diesen Fehler beheben. Führen Sie dazu einen der folgenden Befehle aus:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Wo `<version>` ist die Version des Magentos, das Sie ausgeführt haben **before** das Upgrade. Beispiel: `2.3.5`.

Befolgen Sie die in den folgenden Abschnitten beschriebenen Richtlinien, um sich von einem inkonsistenten Zustand zu erholen.

## Wenn Ihre Suchmaschine `mysql`

Vor 2.4 war MySQL die Standard-Katalogsuchmaschine, aber MySQL wird in dieser Eigenschaft nicht mehr unterstützt. Jetzt müssen Sie Elasticsearch als Suchmaschine installieren und konfigurieren, bevor Sie auf 2.4 aktualisieren.

Verwenden Sie die folgenden Ressourcen, um Sie durch diesen Prozess zu führen:

- [Installieren und Konfigurieren von Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [Installieren von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Konfigurieren von Elasticsearch für die Verwendung mit [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) oder [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [Magento für die Verwendung von Elasticsearch konfigurieren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

Nachdem Sie Elasticsearch und Neuindizierung konfiguriert haben, können Sie auf Version 2.4 aktualisieren.

## Wenn Ihre Suchmaschine `elasticsearch`

Ein Wert von `elasticsearch` zeigt an, dass Ihre heruntergestufte Version von Adobe Commerce oder Magento Open Source für die Verwendung von Elasticsearch 2.x konfiguriert ist. Diese Version von Elasticsearch wird nicht mehr unterstützt.

Sie müssen die folgenden Aufgaben ausführen, bevor Sie auf 2.4 aktualisieren:

1. Elasticsearch aktualisieren. Es wird empfohlen, auf Elasticsearch 7.x zu aktualisieren. Siehe [Upgrade von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) umfassende Anweisungen zum Sichern Ihrer Daten, zur Erkennung potenzieller Migrationsprobleme und zum Testen von Upgrades vor der Bereitstellung in der Produktion. Abhängig von Ihrer aktuellen Version von Elasticsearch ist möglicherweise ein vollständiger Neustart des Clusters erforderlich.

   >[!NOTE]
   >
   >Elasticsearch erfordert JDK 1.8 oder höher. Siehe [Java Software Development Kit (JDK) installieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) um zu überprüfen, welche Version von JDK installiert ist.

1. [Magento für die Verwendung von Elasticsearch konfigurieren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) und reindex.

Nachdem Sie Elasticsearch und Neuindizierung konfiguriert haben, können Sie auf Version 2.4 aktualisieren.
