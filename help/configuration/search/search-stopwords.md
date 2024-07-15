---
title: Konfigurieren von Suchbegriffen
description: Erfahren Sie, wie Sie mithilfe von CSV-Dateien Stoppwörter für Adobe Commerce verwalten.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Konfigurieren von Suchbegriffen

Im Allgemeinen sind _Stoppwörter_ gängige Wörter, die von Suchmaschinen nach der Textverarbeitung herausgefiltert werden. Ursprünglich, als Festplattenspeicher und Speicher extrem begrenzt waren, bedeutete jeder eingesparte Kilobyte eine deutliche Leistungsverbesserung. Daher erzielten Suchmaschinen Leistungssteigerungen, indem sie bestimmte Wörter ignorieren und den Index klein halten.

Obwohl wir heute über mehr Speicher verfügen, ist die Leistung weiterhin wichtig. Elasticsearch und OpenSearch verwenden wie andere Suchmaschinen weiterhin Stoppwörter, um die Leistung zu verbessern.

Abhängig davon, wie Sie die Commerce-Software installiert haben, müssen Sie die Stoppwörter mithilfe von CSV-Dateien im Ordner &quot;`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`&quot;oder &quot;`<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`&quot;verwalten.

Weitere Informationen dazu, wie Elasticsearch und OpenSearch Stoppwörter verwenden, finden Sie in den folgenden Ressourcen:

- [Stoppwörter: Leistung im Vergleich zur Genauigkeit](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Vorteile und Nachteile von Stoppwörtern](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Verwenden von Stoppwörtern](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stoppwörter und Leistung](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Stoppwörter konfigurieren

Stoppwörter befinden sich im Verzeichnis `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` . Im Lieferumfang von Adobe Commerce ist eine CSV-Datei mit Stoppwörtern für die Standard-Gebietsschemas und eine zusätzliche Datei, `stopwords.csv`, enthalten, die Stoppwörter für alle Gebietsschemas enthält, die nicht durch eine andere CSV-Datei dargestellt werden.

Die standardmäßige Lebensdauer für den Cache mit Stoppwörter-Dateien beträgt 15 Minuten.

### Stoppwörter für ein vorhandenes Gebietsschema bearbeiten

**So bearbeiten Sie Stoppwörter**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zum [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Verwenden Sie einen Texteditor, um eine Stoppwortdatei im Verzeichnis `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` zu öffnen.

   CSV-Dateien verwenden die Namenskonvention `stopwords_<locale_code>.csv`. Beispielsweise trägt die deutsche Stoppwortdatei den Namen `stopwords_de_DE.csv`.

1. Fügen Sie Wörter hinzu, entfernen Sie Wörter oder ändern Sie Wörter in der Datei.

   (Jedes Stoppwort in einer Datei beginnt in einer neuen Zeile.)

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Bereinigen Sie den Konfigurations-Cache.

   - Admin: **System** > Werkzeuge > **Cache-Verwaltung**. Aktivieren Sie das Kontrollkästchen **Konfiguration** und klicken Sie in der Liste darüber auf **Aktualisieren**. Klicken Sie auf **Senden** , um die Aktion abzuschließen.

   - Befehlszeile: Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Überprüfen Sie die Ergebnisse, indem Sie nach Begriffen in Ihrer Storefront suchen.

### Erstellen von Stoppwörtern für ein neues Gebietsschema

**Hinzufügen von Stoppwörtern für ein Gebietsschema**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zum [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).

1. Verwenden Sie einen Texteditor, um eine Stoppwortdatei mit dem Namen `stopwords_<locale_code>.csv` im Verzeichnis `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` zu erstellen.

   Um beispielsweise Stoppwörter für das italienische Gebietsschema zu erstellen, benennen Sie die Datei &quot;`stopwords_it_IT.csv`&quot;.

1. Stellen Sie in Ihrer Stoppwortdatei sicher, dass sich jedes Stoppwort in einer separaten Zeile befindet.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Öffnen Sie im selben Ordner `esconfig.xml` in einem Texteditor.
1. Fügen Sie `esconfig.xml` eine Zeile wie folgt hinzu:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Um beispielsweise eine italienische Stoppwortdatei hinzuzufügen, fügen Sie die folgende Zeile hinzu:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Speichern Sie die Änderungen in `esconfig.xml` und beenden Sie den Texteditor.
1. Bereinigen Sie den Konfigurations-Cache.

   - Admin: **System** > Werkzeuge > **Cache-Verwaltung**. Aktivieren Sie das Kontrollkästchen **Konfiguration** und klicken Sie in der Liste darüber auf **Aktualisieren**. Klicken Sie auf **Senden** , um die Aktion abzuschließen.

   - Befehlszeile: Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Überprüfen Sie die Ergebnisse, indem Sie nach Begriffen in Ihrer Storefront suchen.

## Stoppwortverzeichnis ändern

In diesem Abschnitt wird beschrieben, wie Sie optional das standardmäßige stopword-Verzeichnis von einem der folgenden Ordner ändern:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

Der Speicherort hängt von der Installation der Commerce-Software ab. Wenn Sie das Magento 2-GitHub-Repository geklont haben, befindet sich der Pfad unter `app/code`. Wenn Sie ein komprimiertes Archiv oder ein Metapaket installiert haben, befindet sich der Pfad unter &quot;`vendor`&quot;.

**So ändern Sie den Ordner**:

1. Als Dateisysteminhaber öffnen Sie das Elasticsearch &quot;`di.xml`&quot; in einem Texteditor.

   Wenn Sie das Repository geklont haben, befindet es sich unter `app/code/Magento/Elasticsearch/etc/di.xml`

   Wenn Sie ein Archiv oder das Metapaket erhalten haben, befindet es sich unter `vendor/magento/module-elasticsearch/etc/di.xml`

1. Ändern Sie den Wert von `stopwordsDirectory` in den gewünschten Ordner:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Speichern Sie Ihre Änderungen in `di.xml` und beenden Sie den Texteditor.

## So ändern Sie den Ordner von Ihrem Modul aus

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

1. Erstellen Sie in Ihrem -Modul das Verzeichnis `etc/stopwords` mit der entsprechenden CSV-Datei.

1. Speichern Sie Ihre Änderungen in `di.xml` und beenden Sie den Texteditor.
