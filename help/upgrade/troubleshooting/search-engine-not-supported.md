---
title: Aktuelle Suchmaschine wird nicht unterstützt
description: Führen Sie eine Fehlerbehebung bei Ihrem Adobe Commerce- oder Magento Open Source-Upgrade durch, nachdem ein Fehler bezüglich einer nicht unterstützten Suchmaschine aufgetreten ist.
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Aktuelle Suchmaschine wird nicht unterstützt

Die folgende Fehlermeldung weist darauf hin, dass die Adobe Commerce- oder Magento Open Source-Version, von der Sie ein Upgrade durchführen, für die Verwendung einer Katalogsuchmaschine konfiguriert ist, die in der Version, auf die Sie das Upgrade durchführen, nicht unterstützt wird:

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

Der Fehler tritt auf, wenn der zurückgegebene Wert `mysql`, `elasticsearch`oder `elasticsearch6`.

>[!WARNING]
>
>Wenn Sie diesen Fehler erhalten haben, befindet sich Ihre Installation in einem inkonsistenten Zustand und Sie können nicht auf den Administrator zugreifen. Es wird empfohlen, zur vorherigen Version zurückzukehren, während Sie diesen Fehler beheben. Führen Sie dazu einen der folgenden Befehle aus:
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

Vor 2.4 war MySQL die Standard-Katalogsuchmaschine, aber MySQL wird in dieser Eigenschaft nicht mehr unterstützt. Jetzt müssen Sie Elasticsearch oder OpenSearch als Suchmaschine installieren und konfigurieren, bevor Sie auf 2.4 aktualisieren.

Verwenden Sie die folgenden Ressourcen, um Sie durch diesen Prozess zu führen:

- [Installieren und Konfigurieren des Suchsystems](../../configuration/search/overview-search.md)
- [Suchmaschinenkonfiguration](../../configuration/search/configure-search-engine.md)

Nachdem Sie die Suchmaschine und die Neuindizierung konfiguriert haben, können Sie auf Version 2.4 aktualisieren.

## Wenn Ihre Suchmaschine `elasticsearch`

Elasticsearch 6 und frühere Versionen werden nicht mehr unterstützt.

Ein Wert von `elasticsearch` zeigt an, dass Ihre heruntergestufte Version von Adobe Commerce oder Magento Open Source für die Verwendung von Elasticsearch 2.x konfiguriert ist. Diese Version von Elasticsearch wird nicht mehr unterstützt.

Sie müssen die folgenden Aufgaben ausführen, bevor Sie auf 2.4 aktualisieren:

1. Aktualisieren Sie auf eine Elasticsearch-Version, die von Commerce unterstützt wird. Siehe [Upgrade von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) umfassende Anweisungen zum Sichern Ihrer Daten, zur Erkennung potenzieller Migrationsprobleme und zum Testen von Upgrades vor der Bereitstellung in der Produktion. Abhängig von Ihrer aktuellen Version von Elasticsearch ist möglicherweise ein vollständiger Neustart des Clusters erforderlich.

   >[!NOTE]
   >
   >Elasticsearch erfordert JDK 1.8 oder höher. Siehe [Java Software Development Kit (JDK) installieren](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) um zu überprüfen, welche Version von JDK installiert ist.

1. [Elasticsearch konfigurieren](../../configuration/search/configure-search-engine.md) und reindex.

Nachdem Sie die Suchmaschine und die Neuindizierung konfiguriert haben, können Sie auf Version 2.4 aktualisieren.
