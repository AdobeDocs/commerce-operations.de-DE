---
title: Konfigurieren von Suchbegriffen
description: Erfahren Sie, wie Sie mithilfe von CSV-Dateien Stoppwörter für Adobe Commerce verwalten.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# Konfigurieren von Suchbegriffen

Im Allgemeinen _Stoppwörter_ sind häufig verwendete Wörter, die von Suchmaschinen nach der Textverarbeitung herausgefiltert werden. Ursprünglich, als Festplattenspeicher und Speicher extrem begrenzt waren, bedeutete jeder gespeicherte Kilobyte eine deutliche Leistungsverbesserung. Daher erzielten Suchmaschinen Leistungssteigerungen, indem sie bestimmte Wörter ignorieren und den Index klein halten.

Obwohl wir heute über mehr Speicher verfügen, ist die Leistung weiterhin wichtig. Elasticsearch und OpenSearch verwenden wie andere Suchmaschinen weiterhin Stoppwörter, um die Leistung zu verbessern.

Sie müssen Ihre Stoppwörter mithilfe von CSV-Dateien verwalten, die sich im Abschnitt `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` oder `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` -Verzeichnis, abhängig davon, wie Sie die Commerce-Software installiert haben.

Weitere Informationen dazu, wie Elasticsearch und OpenSearch Stoppwörter verwenden, finden Sie in den folgenden Ressourcen:

- [Stoppwörter: Leistung im Vergleich zur Genauigkeit](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Vorteile und Nachteile von Stoppwörtern](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Verwenden von Stoppwörtern](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stoppwörter und Leistung](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Stoppwörter konfigurieren

Stoppwörter befinden sich im `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` Verzeichnis. Im Lieferumfang von Adobe Commerce und Magento Open Source ist eine CSV-Datei mit Stoppwörtern für Standard-Gebietsschemata und einer zusätzlichen Datei enthalten. `stopwords.csv`, das Stoppwörter für alle Gebietsschemas enthält, die nicht durch eine andere CSV-Datei dargestellt werden.

Standardlebensdauer für Stoppwörter-Dateien [cache](https://glossary.magento.com/cache) ist 15 Minuten.

### Stoppwörter für ein vorhandenes Gebietsschema bearbeiten

**So bearbeiten Sie Stoppwörter**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zu der [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Verwenden Sie einen Texteditor, um eine Stoppwortdatei im `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` Verzeichnis.

   CSV-Dateien verwenden die Namenskonvention `stopwords_<locale_code>.csv`. Die deutsche Stoppwortdatei heißt beispielsweise `stopwords_de_DE.csv`.

1. Fügen Sie Wörter hinzu, entfernen Sie Wörter oder ändern Sie Wörter in der Datei.

   (Jedes Stoppwort in einer Datei beginnt in einer neuen Zeile.)

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Bereinigen Sie den Konfigurations-Cache.

   - Admin: **System** > Tools > **Cacheverwaltung**. Wählen Sie die **Konfiguration** und klicken Sie in der Liste darüber auf **Aktualisieren**. Klicken **Einsenden** , um die Aktion abzuschließen.

   - Befehlszeile: Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein:

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. Überprüfen Sie die Ergebnisse, indem Sie nach Begriffen in Ihren [storefront](https://glossary.magento.com/storefront).

### Erstellen von Stoppwörtern für ein neues Gebietsschema

**So fügen Sie Stoppwörter für ein Gebietsschema hinzu**:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zu der [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Verwenden Sie einen Texteditor, um eine Stoppwortdatei mit dem Namen `stopwords_<locale_code>.csv` im `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` Verzeichnis.

   Um beispielsweise Stoppwörter für das italienische Gebietsschema zu erstellen, geben Sie der Datei einen Namen `stopwords_it_IT.csv`.

1. Stellen Sie in Ihrer Stoppwortdatei sicher, dass sich jedes Stoppwort in einer separaten Zeile befindet.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Öffnen Sie im selben Ordner `esconfig.xml` in einem Texteditor.
1. Zeile hinzufügen zu `esconfig.xml` wie folgt:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Um beispielsweise eine italienische Stoppwortdatei hinzuzufügen, fügen Sie die folgende Zeile hinzu:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Speichern Sie die Änderungen in `esconfig.xml` und beenden Sie den Texteditor.
1. Bereinigen Sie den Konfigurations-Cache.

   - Admin: **System** > Tools > **Cacheverwaltung**. Wählen Sie die **Konfiguration** und klicken Sie in der Liste darüber auf **Aktualisieren**. Klicken **Einsenden** , um die Aktion abzuschließen.

   - Befehlszeile: Geben Sie als Eigentümer des Dateisystems den folgenden Befehl ein:

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. Überprüfen Sie die Ergebnisse, indem Sie nach Begriffen in Ihrer Storefront suchen.

## Stoppwortverzeichnis ändern

In diesem Abschnitt wird beschrieben, wie Sie optional das standardmäßige stopword-Verzeichnis von einem der folgenden Ordner ändern:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

Der Speicherort hängt von der Installation der Commerce-Software ab. Wenn Sie das GitHub-Repository von Magento 2 geklont haben, befindet sich der Pfad unter `app/code`. Wenn Sie ein komprimiertes Archiv oder ein Metapaket installiert haben, befindet sich der Pfad unter `vendor`.

**So ändern Sie den Ordner**:

1. Als Eigentümer des Dateisystems öffnen Sie das Elasticsearch `di.xml` in einem Texteditor.

   Wenn Sie das Repository geklont haben, befindet es sich unter `app/code/Magento/Elasticsearch/etc/di.xml`

   Wenn Sie ein Archiv oder das Metapaket erhalten haben, finden Sie es unter `vendor/magento/module-elasticsearch/etc/di.xml`

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

1. [Modul erstellen](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/module-file-structure.html)
1. In Ihrem Modul `etc/di.xml` Anweisungen hinzufügen:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Erstellen Sie in Ihrem -Modul den Ordner . `etc/stopwords`, mit der entsprechenden CSV-Datei.

1. Speichern Sie Ihre Änderungen in `di.xml` und beenden Sie den Texteditor.
