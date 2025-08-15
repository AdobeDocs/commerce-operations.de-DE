---
title: Aktuelle Suchmaschine wird nicht unterstützt
description: Fehlerbehebung beim Adobe Commerce-Upgrade nach einem Fehler über eine nicht unterstützte Suchmaschine.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Aktuelle Suchmaschine wird nicht unterstützt

Die folgende Fehlermeldung weist darauf hin, dass die Adobe Commerce-Version, von der Sie ein Upgrade durchführen, für die Verwendung einer Katalogsuchmaschine konfiguriert ist, die in der Version, auf die Sie ein Upgrade durchführen, nicht unterstützt wird:

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Dieser Fehler bedeutet, dass eine der folgenden Bedingungen für die reduzierte Version von Adobe Commerce zutrifft:

- Die Suchmaschine ist auf MySQL eingestellt.
- Die Suchmaschine ist auf eine Version von Elasticsearch eingestellt, die nicht mehr unterstützt wird.

Verwenden Sie den folgenden Befehl, um die aktuelle Suchmaschine zu überprüfen:

```bash
bin/magento config:show catalog/search/engine
```

Der Fehler tritt auf, wenn der zurückgegebene Wert `mysql`, `elasticsearch` oder `elasticsearch6` lautet.

>[!WARNING]
>
>Wenn Sie diesen Fehler erhalten haben, befindet sich Ihre Installation in einem inkonsistenten Zustand und Sie können nicht auf den Admin zugreifen. Es wird empfohlen, zur vorherigen Version zurückzukehren, während Sie diesen Fehler beheben. Führen Sie dazu einen der folgenden Befehle aus:
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>`<version>` ist die Version von Magento, die Sie vor **Upgrade** haben. Beispiel: `2.3.5`.

Befolgen Sie die in den folgenden Abschnitten beschriebenen Richtlinien, um einen inkonsistenten Zustand wiederherzustellen.

## Wenn Ihre Suchmaschine `mysql` ist

Vor 2.4 war MySQL die Standard-Katalogsuchmaschine, aber MySQL wird in dieser Funktion nicht mehr unterstützt. Jetzt müssen Sie Elasticsearch oder OpenSearch als Suchmaschine installieren und konfigurieren, bevor Sie ein Upgrade auf 2.4 durchführen.

Verwenden Sie die folgenden Ressourcen, um Sie durch diesen Prozess zu führen:

- [Installieren und Konfigurieren der Suchmaschine](../../configuration/search/overview-search.md)
- [Konfiguration von Suchmaschinen](../../configuration/search/configure-search-engine.md)

Nachdem Sie die Suchmaschine konfiguriert und neu indiziert haben, können Sie auf 2.4 aktualisieren.

## Wenn Ihre Suchmaschine `elasticsearch` ist

Elasticsearch 6 und früher werden nicht mehr unterstützt.

Der Wert `elasticsearch` gibt an, dass Ihre Adobe Commerce-Version auf untergeordneter Ebene für die Verwendung von Elasticsearch 2.x konfiguriert ist. Diese Version von Elasticsearch wird nicht mehr unterstützt.

Sie müssen die folgenden Aufgaben ausführen, bevor Sie ein Upgrade auf 2.4 durchführen:

1. Aktualisieren Sie auf eine Version von Elasticsearch, die von Commerce unterstützt wird. Unter [Upgrade von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) finden Sie vollständige Anweisungen zum Sichern Ihrer Daten, Erkennen potenzieller Migrationsprobleme und Testen von Upgrades vor der Bereitstellung in der Produktion. Abhängig von Ihrer aktuellen Version von Elasticsearch kann ein vollständiger Cluster-Neustart erforderlich sein oder nicht.

   >[!NOTE]
   >
   >Elasticsearch erfordert JDK 1.8 oder höher. Siehe [Installieren des Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk), um zu überprüfen, welche Version von JDK installiert ist.

1. [Elasticsearch konfigurieren](../../configuration/search/configure-search-engine.md) und neu indizieren.

Nachdem Sie die Suchmaschine konfiguriert und neu indiziert haben, können Sie auf 2.4 aktualisieren.
