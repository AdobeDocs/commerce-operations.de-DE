---
title: Aktuelle Suchmaschine wird nicht unterstützt
description: Fehlerbehebung bei Ihrem Adobe Commerce-Upgrade, nachdem ein Fehler bezüglich einer nicht unterstützten Suchmaschine aufgetreten ist.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Aktuelle Suchmaschine wird nicht unterstützt

Die folgende Fehlermeldung weist darauf hin, dass die Adobe Commerce-Version, von der Sie ein Upgrade durchführen, für die Verwendung einer Katalogsuchmaschine konfiguriert ist, die in der Version, auf die Sie das Upgrade durchführen, nicht unterstützt wird:

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Dieser Fehler bedeutet, dass eine der folgenden Bedingungen auf der Abwärtsversion von Adobe Commerce zutrifft:

- Die Suchmaschine ist auf MySQL eingestellt.
- Die Suchmaschine ist auf eine Version des Elasticsearchs festgelegt, die nicht mehr unterstützt wird.

Verwenden Sie den folgenden Befehl, um die aktuelle Suchmaschine zu überprüfen:

```bash
bin/magento config:show catalog/search/engine
```

Der Fehler tritt auf, wenn der zurückgegebene Wert `mysql`, `elasticsearch` oder `elasticsearch6` ist.

>[!WARNING]
>
>Wenn Sie diesen Fehler erhalten haben, befindet sich Ihre Installation in einem inkonsistenten Zustand und Sie können nicht auf den Administrator zugreifen. Es wird empfohlen, zur vorherigen Version zurückzukehren, während Sie diesen Fehler beheben. Führen Sie dazu einen der folgenden Befehle aus:
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Wobei `<version>` die Version des Magento ist, die Sie **vor** der Aktualisierung ausgeführt haben. Beispiel: `2.3.5`.

Befolgen Sie die in den folgenden Abschnitten beschriebenen Richtlinien, um sich von einem inkonsistenten Zustand zu erholen.

## Wenn Ihre Suchmaschine `mysql` ist

Vor 2.4 war MySQL die Standard-Katalogsuchmaschine, aber MySQL wird in dieser Eigenschaft nicht mehr unterstützt. Jetzt müssen Sie Elasticsearch oder OpenSearch als Suchmaschine installieren und konfigurieren, bevor Sie auf 2.4 aktualisieren.

Verwenden Sie die folgenden Ressourcen, um Sie durch diesen Prozess zu führen:

- [Installieren und Konfigurieren des Suchsystems](../../configuration/search/overview-search.md)
- [Suchmaschinenkonfiguration](../../configuration/search/configure-search-engine.md)

Nachdem Sie die Suchmaschine und die Neuindizierung konfiguriert haben, können Sie auf Version 2.4 aktualisieren.

## Wenn Ihre Suchmaschine `elasticsearch` ist

Elasticsearch 6 und frühere Versionen werden nicht mehr unterstützt.

Der Wert &quot;`elasticsearch`&quot;zeigt an, dass Ihre Abwärtsversion von Adobe Commerce für die Verwendung von Elasticsearch 2.x konfiguriert ist. Diese Version von Elasticsearch wird nicht mehr unterstützt.

Sie müssen die folgenden Aufgaben ausführen, bevor Sie auf 2.4 aktualisieren:

1. Aktualisierung auf eine von Commerce unterstützte Elasticsearch-Version. Eine vollständige Anleitung zum Sichern Ihrer Daten, zum Erkennen potenzieller Migrationsprobleme und zum Testen von Upgrades vor der Bereitstellung in der Produktionsumgebung finden Sie unter [Elasticsearch aktualisieren](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) . Abhängig von Ihrer aktuellen Version von Elasticsearch ist möglicherweise ein vollständiger Neustart des Clusters erforderlich.

   >[!NOTE]
   >
   >Elasticsearch erfordert JDK 1.8 oder höher. Siehe [Installieren des Java Software Development Kits (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) , um zu überprüfen, welche Version von JDK installiert ist.

1. [Konfigurieren Sie Elasticsearch](../../configuration/search/configure-search-engine.md) und die Neuindizierung.

Nachdem Sie die Suchmaschine und die Neuindizierung konfiguriert haben, können Sie auf Version 2.4 aktualisieren.
