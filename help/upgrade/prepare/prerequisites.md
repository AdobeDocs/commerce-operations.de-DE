---
title: Vollständige Voraussetzungen
description: Bereiten Sie Ihr Adobe Commerce-Projekt auf ein Upgrade vor, indem Sie diese erforderlichen Schritte ausführen.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 4c84710da62fbb31214a0de2adc8adbd68880a76
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 0%

---

# Vollständige Upgrade-Voraussetzungen

Es ist wichtig zu verstehen, was zum Ausführen von Adobe Commerce erforderlich ist. Sie müssen zunächst die [Systemanforderungen](../../installation/system-requirements.md) für die Version überprüfen, auf die Sie die Aktualisierung planen.

Nachdem Sie die Systemanforderungen überprüft haben, müssen Sie die folgenden Voraussetzungen erfüllen, bevor Sie das System aktualisieren:

* Alle Software aktualisieren
* Überprüfen, ob eine unterstützte Suchmaschine installiert ist
* Tabellenformat der Datenbank konvertieren
* Legen Sie die Grenze für geöffnete Dateien fest
* Überprüfen, ob Cron-Aufträge ausgeführt werden
* `DATA_CONVERTER_BATCH_SIZE` festlegen
* Überprüfen der Dateisystemberechtigungen
* Legen Sie den Stammordner des Ordners &quot;`pub/`&quot;fest.
* Installieren des Composer-Aktualisierungs-Plug-ins

## Alle Software aktualisieren

Die [Systemanforderungen](../../installation/system-requirements.md) beschreiben genau, welche Versionen von Software von Drittanbietern mit Adobe Commerce-Versionen getestet wurden.

Stellen Sie sicher, dass Sie alle Systemanforderungen und Abhängigkeiten in Ihrer Umgebung aktualisiert haben. Siehe PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php) und [erforderliche PHP-Einstellungen](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Für Adobe Commerce on Cloud Infrastructure Pro-Projekte müssen Sie ein [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)-Ticket erstellen, um Dienste in Staging- und Produktionsumgebungen zu installieren oder zu aktualisieren. Geben Sie die erforderlichen Dienständerungen an und nehmen Sie Ihre aktualisierten `.magento.app.yaml` - und `services.yaml` -Dateien sowie die PHP-Version in das Ticket auf. Es kann bis zu 48 Stunden dauern, bis das Cloud-Infrastruktur-Team Ihr Projekt aktualisiert. Siehe [Unterstützte Software und Dienste](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Überprüfen, ob eine unterstützte Suchmaschine installiert ist

Adobe Commerce erfordert die Installation von Elasticsearch oder OpenSearch, um die Software verwenden zu können.

**Wenn Sie von 2.3.x auf 2.4** aktualisieren, müssen Sie überprüfen, ob Sie MySQL, Elasticsearch oder eine Drittanbietererweiterung als Ihre Katalogsuchmaschine in Ihrer 2.3.x-Instanz verwenden. Das Ergebnis bestimmt, was Sie _vor_ einer Aktualisierung auf 2.4 tun müssen.

**Wenn Sie Patch-Versionen innerhalb der Release-Zeilen 2.3.x oder 2.4.x aktualisieren**, können Sie optional [zu OpenSearch](opensearch-migration.md) migrieren, wenn Elasticsearch 7.x bereits installiert ist.

Sie können die Befehlszeile oder den Admin verwenden, um Ihre Katalogsuchmaschine zu bestimmen:

* Geben Sie den Befehl `bin/magento config:show catalog/search/engine` ein. Der Befehl gibt den Wert `mysql`, `elasticsearch` (was bedeutet, dass Elasticsearch 2 konfiguriert ist), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` oder einen benutzerdefinierten Wert zurück, der angibt, dass Sie eine Suchmaschine eines Drittanbieters installiert haben. Verwenden Sie für Versionen vor 2.4.6 den Wert `elasticsearch7` für die Elasticsearch 7- oder OpenSearch-Engine. Verwenden Sie für Version 2.4.6 und höher den Wert `opensearch` für die OpenSearch-Engine.

* Überprüfen Sie vom Administrator den Wert des Felds **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** .

In den folgenden Abschnitten werden die Aktionen beschrieben, die Sie vor der Aktualisierung auf Version 2.4.0 ausführen müssen.

### MySQL

Ab Version 2.4 wird MySQL nicht mehr als Katalogsuchmaschine unterstützt. Vor der Aktualisierung müssen Sie Elasticsearch oder OpenSearch installieren und konfigurieren. Verwenden Sie die folgenden Ressourcen, um Sie durch diesen Prozess zu führen:

* [Installieren und Konfigurieren von Elasticsearch](../../configuration/search/overview-search.md)
* [Installieren von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Konfigurieren von [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) oder [Apache](../../installation/prerequisites/search-engine/configure-apache.md) für die Verwendung mit Ihrer Suchmaschine
* [Konfigurieren von Commerce für die Verwendung von Elasticsearch](../../configuration/search/configure-search-engine.md) und reindex

Einige Katalogsuchmaschinen von Drittanbietern werden über der Adobe Commerce-Suchmaschine ausgeführt. Wenden Sie sich an Ihren Anbieter, um festzustellen, ob Sie Ihre Erweiterung aktualisieren müssen.

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Suchmaschine

Sie müssen Elasticsearch 7.6 oder höher oder OpenSearch 1.2 installieren und konfigurieren, bevor Sie auf 2.4.0 aktualisieren. Adobe unterstützt Elasticsearch 2.x, 5.x und 6.x nicht mehr. [Suchmaschinenkonfiguration](../../configuration/search/configure-search-engine.md) im _Konfigurationshandbuch_ beschreibt die Aufgaben, die Sie nach dem Upgrade von Elasticsearch auf eine unterstützte Version ausführen müssen.

Eine vollständige Anleitung zum Sichern Ihrer Daten, zum Erkennen potenzieller Migrationsprobleme und zum Testen von Upgrades vor der Bereitstellung in der Produktionsumgebung finden Sie unter [Elasticsearch aktualisieren](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) . Abhängig von Ihrer aktuellen Version von Elasticsearch ist möglicherweise ein vollständiger Neustart des Clusters erforderlich.

Elasticsearch erfordert Java Development Kit (JDK) 1.8 oder höher. Siehe [Installieren des Java Software Development Kits (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) , um zu überprüfen, welche Version von JDK installiert ist.

#### OpenSearch

OpenSearch ist eine Open-Source-Abspaltung von Elasticsearch 7.10.2 nach der Lizenzänderung von Elasticsearch. In den folgenden Versionen von Adobe Commerce wird OpenSearch unterstützt:

* 2.4.6 (OpenSearch verfügt über ein eigenes Modul und separate Einstellungen)
* 2,4,5
* 2,4,4
* 2.4.3-p2
* 2.3.7-p3

Sie können [nur dann von Elasticsearch zu OpenSearch migrieren](opensearch-migration.md), wenn Sie ein Upgrade auf eine oben aufgeführte Adobe Commerce-Version (oder höher) durchführen.

OpenSearch erfordert JDK 1.8 oder höher. Siehe [Installieren des Java Software Development Kits (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) , um zu überprüfen, welche Version von JDK installiert ist.

[Suchmaschinenkonfiguration](../../configuration/search/configure-search-engine.md) beschreibt die Aufgaben, die Sie nach dem Ändern von Suchmaschinen ausführen müssen.

#### Upgrade-Elasticsearch

Die Unterstützung für Elasticsearch 8.x wurde in Adobe Commerce 2.4.6 eingeführt. Die folgenden Anweisungen zeigen ein Beispiel für die Aktualisierung von Elasticsearch von 7.x auf 8.x:

1. Aktualisieren Sie den Elasticsearch 7.x-Server auf 8.x und stellen Sie sicher, dass ausgeführt wird. Weitere Informationen finden Sie in der Dokumentation zum Elasticsearch [ .](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)

1. Aktivieren Sie das Feld &quot;`id_field_data`&quot;, indem Sie Ihrer `elasticsearch.yml` -Datei die folgende Konfiguration hinzufügen und den Elasticsearch 8.x-Dienst neu starten.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Zur Unterstützung von Elasticsearch 8.x deaktiviert Adobe Commerce 2.4.6 standardmäßig die Eigenschaft `indices.id_field_data` und verwendet das Feld `_id` in der Eigenschaft `docvalue_fields` .

1. Aktualisieren Sie im Stammverzeichnis Ihres Adobe Commerce-Projekts Ihre Composer-Abhängigkeiten, um das `Magento_Elasticsearch7` -Modul zu entfernen und das `Magento_Elasticsearch8` -Modul zu installieren.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. Aktualisieren Sie Ihre Projektkomponenten.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Konfigurieren Sie Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) im [!DNL Admin].

1. Neuindizieren des Katalogindex.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Löschen Sie alle Elemente aus den aktivierten Cache-Typen.

   ```bash
   bin/magento cache:clean
   ```

#### Elasticsearch herunterladen

Wenn Sie versehentlich die Elasticsearch-Version auf Ihrem Server aktualisieren oder feststellen, dass Sie aus anderen Gründen ein Upgrade durchführen müssen, müssen Sie auch Ihre Adobe Commerce-Projektabhängigkeiten aktualisieren. So aktualisieren Sie beispielsweise von Elasticsearch 8.x auf 7.x

1. Aktualisieren Sie den Server von Elasticsearch 8.x auf 7.x und stellen Sie sicher, dass ausgeführt wird. Weitere Informationen finden Sie in der Dokumentation zum Elasticsearch [ .](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)

1. Aktualisieren Sie im Stammverzeichnis Ihres Adobe Commerce-Projekts Ihre Composer-Abhängigkeiten, um das `Magento_Elasticsearch8`-Modul und seine Composer-Abhängigkeiten zu entfernen und das `Magento_Elasticsearch7`-Modul zu installieren.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Aktualisieren Sie Ihre Projektkomponenten.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Konfigurieren Sie Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) im [!DNL Admin].

1. Neuindizieren des Katalogindex.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Löschen Sie alle Elemente aus den aktivierten Cache-Typen.

   ```bash
   bin/magento cache:clean
   ```

### Drittanbietererweiterungen

Wir empfehlen Ihnen, sich an Ihren Suchmaschinenanbieter zu wenden, um zu ermitteln, ob Ihre Erweiterung vollständig mit einer Adobe Commerce-Version kompatibel ist.

## Tabellenformat der Datenbank konvertieren

Sie müssen das Format aller Datenbanktabellen von `COMPACT` in `DYNAMIC` konvertieren. Sie müssen auch den Speicher-Engine-Typ von `MyISAM` in `InnoDB` konvertieren. Siehe [Best Practices](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Legen Sie die Grenze für geöffnete Dateien fest

Das Festlegen der Grenze für offene Dateien (ulimit) kann dabei helfen, Fehler durch mehrere rekursive Aufrufe langer Abfragezeichenfolgen oder Probleme bei der Verwendung des Befehls `bin/magento setup:rollback` zu vermeiden. Dieser Befehl unterscheidet sich für verschiedene UNIX-Shells. Weitere Informationen zum Befehl `ulimit` finden Sie in Ihrem individuellen Geschmack.

Adobe empfiehlt, die geöffneten Dateien [ulimit](https://ss64.com/bash/ulimit.html) auf den Wert `65536` oder höher festzulegen. Sie können jedoch bei Bedarf einen größeren Wert verwenden. Sie können die ulimit in der Befehlszeile festlegen oder sie zu einer permanenten Einstellung für die Shell des Benutzers machen.

So legen Sie die ulimit über die Befehlszeile fest:

1. Wechseln Sie zum Besitzer des [Dateisystems](../../installation/prerequisites/file-system/overview.md).
1. Setzen Sie die Obergrenze auf `65536`.

   ```bash
   ulimit -n 65536
   ```

So legen Sie den Wert in Ihrer Bash-Shell fest:

1. Wechseln Sie zum Besitzer des [Dateisystems](../../installation/prerequisites/file-system/overview.md).
1. Öffnen Sie `/home/<username>/.bashrc` in einem Texteditor.
1. Fügen Sie die folgende Zeile hinzu:

   ```bash
   ulimit -n 65536
   ```

1. Speichern Sie Ihre Änderungen in der Datei `.bashrc` und beenden Sie den Texteditor.

>[!IMPORTANT]
>
>Es wird empfohlen, keinen Wert für die Eigenschaft `pcre.recursion_limit` in der Datei `php.ini` festzulegen, da dies zu unvollständigen Rollbacks ohne Fehlermeldung führen kann.

## Überprüfen, ob Cron-Aufträge ausgeführt werden

Der UNIX-Aufgabenplaner `cron` ist für laufende Adobe Commerce-Vorgänge von entscheidender Bedeutung. Er plant Dinge wie Neuindizierung, Newsletter, E-Mails und Sitemaps. Mehrere Funktionen erfordern mindestens einen Cron-Auftrag, der als Dateisysteminhaber ausgeführt wird.

Um sicherzustellen, dass Ihr Cron-Auftrag ordnungsgemäß eingerichtet ist, überprüfen Sie die Registerkarte &quot;crontab&quot;, indem Sie den folgenden Befehl als Dateisysteminhaber eingeben:

>[!NOTE]
>
>Die Crontab ist die Konfigurationsdatei, die für die Ausführung von Cron-Aufträgen verantwortlich ist.

```bash
crontab -l
```

Ergebnisse, die dem Folgenden ähneln, sollten angezeigt werden:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Ein weiteres Symptom dafür, dass Cron nicht ausgeführt wird, ist der folgende Fehler im Admin:

![Systemmeldungen - Cron wird nicht ausgeführt](../../assets/upgrade-guide/cron-not-running.png)

Um den Fehler anzuzeigen, klicken Sie oben im Fenster auf **Systemmeldungen** :

![Benachrichtigung bezüglich Systemmeldungen](../../assets/upgrade-guide/system-messages.png)

Weitere Informationen finden Sie unter [cron konfigurieren und ausführen](../../configuration/cli/configure-cron-jobs.md) .

## DATA_CONVERTER_BATCH_SIZE festlegen

Adobe Commerce 2.4 umfasst Sicherheitsverbesserungen, bei denen einige Daten von serialisierten Daten in JSON konvertiert werden müssen. Diese Konvertierung erfolgt während des Upgrades und kann abhängig von der Datenmenge in Ihrer Datenbank lange dauern.

Die folgenden Tabellen sind am stärksten betroffen:

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Wenn Sie über eine große Datenmenge verfügen, können Sie die Leistung verbessern, indem Sie den Wert einer Umgebungsvariablen `DATA_CONVERTER_BATCH_SIZE` festlegen. Standardmäßig ist der Wert auf `50,000` gesetzt.

So legen Sie die Umgebungsvariable fest:

1. Wechseln Sie zum Besitzer des [Dateisystems](../../installation/prerequisites/file-system/overview.md).
1. Legen Sie die Variable fest:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` erfordert Speicher. Vermeiden Sie es, ihn auf einen großen Wert (ca. 1 GB) festzulegen, ohne ihn zuerst zu testen.

1. Nach Abschluss des Upgrades können Sie die -Variable deaktivieren:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Überprüfen der Dateisystemberechtigungen

Aus Sicherheitsgründen erfordert Adobe Commerce bestimmte Berechtigungen für das Dateisystem. Berechtigungen unterscheiden sich von _[Eigentum](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. Die Eigentümerschaft bestimmt, wer Aktionen im Dateisystem durchführen kann. Durch Berechtigungen wird festgelegt, was der Benutzer tun kann.

Verzeichnisse im Dateisystem müssen von der Gruppe ](../../installation/prerequisites/file-system/overview.md) des Dateisysteminhabers schreibbar sein.[

Um zu überprüfen, ob Ihre Dateisystemberechtigungen richtig eingerichtet sind, melden Sie sich entweder beim Anwendungsserver an oder verwenden Sie die Dateiverwaltungsanwendung Ihres Hosting-Providers.

Geben Sie beispielsweise den folgenden Befehl ein, wenn die Anwendung in `/var/www/html/magento2` installiert ist:

```bash
ls -l /var/www/html/magento2
```

Beispielausgabe:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Eine Erläuterung der Beispielausgabe finden Sie im Folgenden:

* Die meisten Dateien sind `-rw-rw----`, was `660` ist
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* Der Dateisysteminhaber ist `magento_user`

Um genauere Informationen zu erhalten, können Sie den folgenden Befehl eingeben:

```bash
ls -la /var/www/html/magento2/pub
```

Da Adobe Commerce statische Datei-Assets in Unterverzeichnissen von `pub` bereitstellt, empfiehlt es sich, auch dort die Berechtigungen und das Eigentum zu überprüfen.

Weitere Informationen finden Sie unter [Dateisystemberechtigungen und Eigentümer](../../installation/prerequisites/file-system/overview.md).

## Legen Sie den Stammordner des Ordners &quot;`pub/`&quot;fest.

Weitere Informationen finden Sie unter [Basisverzeichnis ändern, um die Sicherheit zu verbessern](../../installation/tutorials/docroot.md) .

## Installieren des Composer-Aktualisierungs-Plug-ins

Das Plug-in [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer löst Änderungen auf, die an der Stammprojektdatei `composer.json` vorgenommen werden müssen, bevor auf eine neue Produktanforderung aktualisiert wird.

Das Plug-in automatisiert die manuelle Aktualisierung teilweise, indem es Abhängigkeitskonflikte identifiziert und unterstützt, anstatt sie manuell zu identifizieren und zu beheben.

Installieren des Plug-ins:

1. Fügen Sie das Paket zu Ihrer `composer.json` -Datei hinzu.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten:

   ```bash
   composer update
   ```
