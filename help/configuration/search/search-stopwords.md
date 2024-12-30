---
title: Konfigurieren von Suchbegriffen
description: Erfahren Sie, wie Sie Stoppwörter für Adobe Commerce mithilfe von CSV-Dateien verwalten.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Konfigurieren von Suchbegriffen

Im Allgemeinen sind _Stoppwörter_ gebräuchliche Wörter, die Suchmaschinen nach der Verarbeitung von Text herausfiltern. Ursprünglich bedeutete jedes eingesparte Kilobyte, wenn Festplattenspeicher und Arbeitsspeicher extrem begrenzt waren, eine deutliche Leistungsverbesserung. Daher erzielten Suchmaschinen Leistungsgewinne, indem sie bestimmte Wörter ignorierten und den Index klein hielten.

Obwohl wir heute mehr Speicher haben, ist die Leistung immer noch wichtig. Elasticsearch und OpenSearch verwenden wie andere Suchmaschinen immer noch Stoppwörter, um die Leistung zu verbessern.

Sie müssen Ihre Stoppwörter mithilfe von CSV-Dateien verwalten, die sich im Verzeichnis `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` oder im Verzeichnis `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` befinden, je nachdem, wie Sie die Commerce-Software installiert haben.

Weitere Informationen dazu, wie Elasticsearch und OpenSearch Stoppwörter verwenden, finden Sie in den folgenden Ressourcen:

- [Stoppwörter: Leistung versus Präzision](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Vor- und Nachteile von Stoppwörtern](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Verwendung von Stoppwörtern](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stoppwörter und Leistung](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Stoppwörter konfigurieren

Stoppwörter befinden sich im `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`. Adobe Commerce wird mit einer CSV-Datei ausgeliefert, die Stoppwörter für die Standardgebietsschemata enthält, und einer zusätzlichen Datei, `stopwords.csv`, die Stoppwörter für alle Gebietsschemata enthält, die nicht durch eine andere CSV-Datei dargestellt werden.

Die Standardlebensdauer für den Stoppwörter-Datei-Cache beträgt 15 Minuten.

### Bearbeiten von Stoppwörtern für ein vorhandenes Gebietsschema

**Stoppwörter bearbeiten**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Verwenden Sie einen Texteditor, um eine Stoppwortdatei im `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` zu öffnen.

   CSV-Dateien verwenden die `stopwords_<locale_code>.csv` der Namenskonvention. Beispielsweise heißt die deutsche Stoppwortdatei `stopwords_de_DE.csv`.

1. Hinzufügen von Wörtern, Entfernen von Wörtern oder Ändern von Wörtern in der Datei

   (Jedes Stoppwort in einer Datei beginnt auf einer neuen Zeile.)

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Bereinigen Sie den Konfigurations-Cache.

   - Admin: **System** > Tools > **Cache-Verwaltung**. Aktivieren Sie **Kontrollkästchen** Konfiguration“ und klicken Sie in der Liste darüber auf **Aktualisieren**. Klicken Sie **Senden**, um die Aktion abzuschließen.

   - Befehlszeile: Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Überprüfen Sie die Ergebnisse, indem Sie in Ihrer Storefront nach Begriffen suchen.

### Erstellen von Stoppwörtern für ein neues Gebietsschema

**So fügen Sie Stoppwörter für ein Gebietsschema hinzu**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).

1. Verwenden Sie einen Texteditor, um eine Stoppwortdatei mit dem Namen `stopwords_<locale_code>.csv` im `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` zu erstellen.

   Um beispielsweise Stoppwörter für das italienische Gebietsschema zu erstellen, benennen Sie die Datei `stopwords_it_IT.csv`.

1. Achten Sie in Ihrer Stoppwortdatei darauf, dass jedes Stoppwort auf einer separaten Zeile steht.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Öffnen Sie `esconfig.xml` im selben Verzeichnis in einem Texteditor.
1. Fügen Sie `esconfig.xml` wie folgt eine Zeile hinzu:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Um beispielsweise eine italienische Stoppwortdatei hinzuzufügen, fügen Sie die folgende Zeile hinzu:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Speichern Sie die Änderungen in `esconfig.xml` und beenden Sie den Texteditor.
1. Bereinigen Sie den Konfigurations-Cache.

   - Admin: **System** > Tools > **Cache-Verwaltung**. Aktivieren Sie **Kontrollkästchen** Konfiguration“ und klicken Sie in der Liste darüber auf **Aktualisieren**. Klicken Sie **Senden**, um die Aktion abzuschließen.

   - Befehlszeile: Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Überprüfen Sie die Ergebnisse, indem Sie in Ihrer Storefront nach Begriffen suchen.

## Ändern des Stoppwortverzeichnisses

In diesem Abschnitt wird beschrieben, wie Sie optional das standardmäßige Stoppwortverzeichnis aus einem der folgenden Ordner ändern können:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

Der Speicherort hängt von der Installation der Commerce-Software ab. Wenn Sie das GitHub-Repository von Magento 2 geklont haben, befindet sich der Pfad unter `app/code`. Wenn Sie ein komprimiertes Archiv oder ein Metapaket installiert haben, befindet sich der Pfad unter `vendor`.

**So ändern Sie das Verzeichnis**:

1. Öffnen Sie als Verantwortlicher für das Dateisystem das Elasticsearch `di.xml` in einem Texteditor.

   Wenn Sie das Repository geklont haben, befindet es sich unter `app/code/Magento/Elasticsearch/etc/di.xml`

   Wenn Sie ein Archiv oder das Metapaket haben, befindet es sich unter `vendor/magento/module-elasticsearch/etc/di.xml`

1. Ändern Sie den Wert von `stopwordsDirectory` in das gewünschte Verzeichnis:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Speichern Sie Ihre Änderungen in `di.xml` und beenden Sie den Texteditor.

## So ändern Sie das Verzeichnis in Ihrem Modul

1. [Erstellen eines Moduls](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. Fügen Sie in Ihrem Modul `etc/di.xml` Anweisungen hinzu:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Erstellen Sie in Ihrem Modul das Verzeichnis `etc/stopwords` mit der entsprechenden CSV-Datei.

1. Speichern Sie Ihre Änderungen in `di.xml` und beenden Sie den Texteditor.
