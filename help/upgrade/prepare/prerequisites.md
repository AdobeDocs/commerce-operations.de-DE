---
title: Voraussetzungen abschließen
description: Bereiten Sie Ihr Adobe Commerce-Projekt auf ein Upgrade vor, indem Sie die folgenden erforderlichen Schritte ausführen.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 2d17da1f8cbda1462839ad2fa3ea569833443827
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Voraussetzungen für ein vollständiges Upgrade

Es ist wichtig zu verstehen, was zum Ausführen von Adobe Commerce erforderlich ist. Sie müssen zunächst die [Systemanforderungen](../../installation/system-requirements.md) für die Version überprüfen, auf die Sie ein Upgrade durchführen möchten.

Nachdem Sie die Systemanforderungen überprüft haben, müssen Sie die folgenden Voraussetzungen erfüllen, bevor Sie Ihr System aktualisieren:

* Gesamte Software aktualisieren
* Überprüfen, ob eine unterstützte Suchmaschine installiert ist
* Datenbanktabellenformat konvertieren
* Festlegen des Limits für geöffnete Dateien
* Überprüfen, ob Cron-Aufträge ausgeführt werden
* `DATA_CONVERTER_BATCH_SIZE` festlegen
* Überprüfen von Dateisystemberechtigungen
* Festlegen des `pub/` Ordnerstamms
* Installieren des Composer-Aktualisierungs-Plug-ins

## Gesamte Software aktualisieren

Die [Systemanforderungen](../../installation/system-requirements.md) beschreiben genau, welche Versionen von Software von Drittanbietern mit Adobe Commerce-Versionen getestet wurden.

Stellen Sie sicher, dass Sie alle Systemanforderungen und Abhängigkeiten in Ihrer Umgebung aktualisiert haben. Siehe PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php) und [erforderlichen PHP-Einstellungen](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Für Adobe Commerce in Cloud Infrastructure Pro-Projekten müssen Sie ein [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)-Ticket erstellen, um Services in Staging- und Produktionsumgebungen zu installieren oder zu aktualisieren. Geben Sie die erforderlichen Service-Änderungen an und fügen Sie Ihre aktualisierten `.magento.app.yaml`- und `services.yaml`-Dateien sowie die PHP-Version in das Ticket ein. Es kann bis zu 48 Stunden dauern, bis das Cloud-Infrastruktur-Team Ihr Projekt aktualisiert. Siehe [Unterstützte Software und Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Überprüfen, ob eine unterstützte Suchmaschine installiert ist

Adobe Commerce erfordert die Installation von Elasticsearch oder OpenSearch, damit die Software verwendet werden kann.

**Wenn Sie ein Upgrade von 2.3.x auf 2.4** durchführen, müssen Sie überprüfen, ob Sie MySQL, Elasticsearch oder eine Drittanbietererweiterung als Katalogsuchmaschine in Ihrer 2.3.x-Instanz verwenden. Das Ergebnis bestimmt, was Sie tun müssen _bevor Sie_ 2.4 aktualisieren.

**Wenn Sie Patch-Versionen innerhalb der Versionen 2.3.x oder 2.4.x aktualisieren** und Elasticsearch 7.x bereits installiert ist, können Sie optional [zu OpenSearch migrieren](opensearch-migration.md).

Sie können die Befehlszeile oder den Administrator verwenden, um Ihre Katalogsuchmaschine zu bestimmen:

* Geben Sie den `bin/magento config:show catalog/search/engine` Befehl ein. Der Befehl gibt den Wert `mysql`, `elasticsearch` (was anzeigt, dass Elasticsearch 2 konfiguriert ist), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` oder einen benutzerdefinierten Wert zurück, was anzeigt, dass Sie eine Suchmaschine eines Drittanbieters installiert haben. Verwenden Sie für Versionen vor 2.4.6 den `elasticsearch7` für die Elasticsearch 7- oder OpenSearch-Engine. Verwenden Sie für Version 2.4.6 und höher den `opensearch` für die OpenSearch-Engine.

* Überprüfen Sie in der Admin den Wert des Felds **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** .

In den folgenden Abschnitten wird beschrieben, welche Aktionen Sie durchführen müssen, bevor Sie ein Upgrade auf 2.4.0 durchführen.

### MySQL

Ab Version 2.4 ist MySQL keine unterstützte Katalogsuchmaschine mehr. Sie müssen Elasticsearch oder OpenSearch vor dem Upgrade installieren und konfigurieren. Verwenden Sie die folgenden Ressourcen, um Sie durch diesen Prozess zu führen:

* [Installieren und Konfigurieren von Elasticsearch](../../configuration/search/overview-search.md)
* [Installieren von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Konfigurieren Sie [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) oder [Apache](../../installation/prerequisites/search-engine/configure-apache.md) für Ihre Suchmaschine.
* [Konfigurieren von Commerce für die Verwendung von Elasticsearch](../../configuration/search/configure-search-engine.md) und Neuindizierung

Einige Katalogsuchmaschinen von Drittanbietern werden zusätzlich zur Adobe Commerce-Suchmaschine ausgeführt. Wenden Sie sich an Ihren Anbieter, um zu entscheiden, ob Sie Ihre Erweiterung aktualisieren müssen.

### MySQL 8.4-Änderungen

Adobe unterstützt MySQL 8.4 nun auch in Version 2.4.8.
In diesem Abschnitt werden wichtige Änderungen an MySQL 8.4 beschrieben, die Entwickler beachten sollten.

#### Veralteter nicht standardmäßiger Schlüssel

Die Verwendung von nicht eindeutigen oder partiellen Schlüsseln als Fremdschlüssel ist nicht standardmäßig und wird in MySQL 8.4 nicht mehr unterstützt. Ab MySQL 8.4.0 müssen Sie diese Schlüssel explizit aktivieren, indem Sie [`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) auf `OFF` setzen oder den Server mit der Option `--skip-restrict-fk-on-non-standard-key` starten.

#### Aktualisieren von MySQL 8.0 ( oder älteren Versionen ) auf MySQL 8.4

Um MySQL von Version 8.0 ordnungsgemäß auf Version 8.4 zu aktualisieren, müssen Sie die folgenden Schritte ausführen, um Folgendes zu tun:

1. Wartungsmodus aktivieren:

   ```bash
   bin/magento maintenance:enable
   ```

1. Erstellen Sie eine Datenbanksicherung:

   ```bash
   bin/magento setup:backup --db
   ```

1. Aktualisieren Sie MySQL auf Version 8.4.
1. Legen Sie `restrict_fk_on_non_standard_key` in `OFF` in der `[mysqld]` auf `my.cnf` fest.

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >Wenn Sie den Wert von `restrict_fk_on_non_standard_key` nicht in `OFF` ändern, erhalten Sie beim Import den folgenden Fehler:
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. Starten Sie den MySQL-Server neu.
1. Importieren Sie die gesicherten Daten in MySQL.
1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```

1. Wartungsmodus deaktivieren:

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Suchmaschine

Sie müssen entweder Elasticsearch 7.6 oder höher oder OpenSearch 1.2 installieren und konfigurieren, bevor Sie ein Upgrade auf 2.4.0 durchführen. Adobe unterstützt nicht mehr Elasticsearch 2.x, 5.x und 6.x. [Suchmaschinenkonfiguration](../../configuration/search/configure-search-engine.md) im _Konfigurationshandbuch_ beschreibt die Aufgaben, die Sie nach dem Upgrade von Elasticsearch auf eine unterstützte Version ausführen müssen.

Unter [Upgrade von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) finden Sie vollständige Anweisungen zum Sichern Ihrer Daten, Erkennen potenzieller Migrationsprobleme und Testen von Upgrades vor der Bereitstellung in der Produktion. Abhängig von Ihrer aktuellen Version von Elasticsearch kann ein vollständiger Cluster-Neustart erforderlich sein oder nicht.

Elasticsearch erfordert Java Development Kit (JDK) 1.8 oder höher. Siehe [Installieren des Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk), um zu überprüfen, welche Version von JDK installiert ist.

#### OpenSearch

OpenSearch ist eine Open-Source-Version von Elasticsearch 7.10.2, die auf die Lizenzänderung von Elasticsearch folgt. Mit den folgenden Versionen von Adobe Commerce wird Unterstützung für OpenSearch eingeführt:

* 2.4.6 (OpenSearch verfügt über ein separates Modul und Einstellungen)
* 2,4,5
* 2,4,4
* 2.4.3-p2
* 2.3.7-p3

Sie können [von Elasticsearch zu OpenSearch migrieren](opensearch-migration.md) nur, wenn Sie ein Upgrade auf eine der oben aufgeführten Adobe Commerce-Versionen (oder höher) durchführen.

OpenSearch erfordert JDK 1.8 oder höher. Siehe [Installieren des Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk), um zu überprüfen, welche Version von JDK installiert ist.

[Suchmaschinenkonfiguration](../../configuration/search/configure-search-engine.md) beschreibt die Aufgaben, die nach einem Wechsel der Suchmaschine ausgeführt werden müssen.

#### Elasticsearch aktualisieren

Die Unterstützung für Elasticsearch 8.x wurde mit Adobe Commerce 2.4.6 eingeführt. Die folgenden Anweisungen zeigen ein Beispiel für ein Upgrade von Elasticsearch von 7.x auf 8.x:

>[!NOTE]
>
>In der kommenden Version 2.4.8 sind diese Schritte nicht erforderlich, da das Elasticsearch 8-Modul standardmäßig enthalten ist und Sie es nicht separat installieren müssen.

1. Aktualisieren Sie den Elasticsearch 7.x-Server auf 8.x, und stellen Sie sicher, dass ausgeführt wird. Siehe die [Elasticsearch-Dokumentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Aktivieren Sie das Feld `id_field_data` , indem Sie die folgende Konfiguration zu Ihrer `elasticsearch.yml` hinzufügen und den Elasticsearch 8.x-Service neu starten.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Um Elasticsearch 8.x zu unterstützen, deaktiviert Adobe Commerce 2.4.6 standardmäßig die `indices.id_field_data`-Eigenschaft und verwendet das `_id` in der `docvalue_fields`.

1. Aktualisieren Sie im Stammverzeichnis Ihres Adobe Commerce-Projekts Ihre Composer-Abhängigkeiten, um das `Magento_Elasticsearch7` zu entfernen und das `Magento_Elasticsearch8` zu installieren.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   Wenn ein Abhängigkeitsfehler für `psr/http-message` auftritt, klicken Sie darauf, um den folgenden Abschnitt zur Fehlerbehebung zu erweitern:

   +++Fehlerbehebung

   Wenn bei der Installation von Elasticsearch 8 Abhängigkeitskonflikte auftreten, insbesondere bei `psr/http-message`, können Sie diese durch folgende Schritte beheben:

   1. Zunächst benötigen Sie das Elasticsearch 8-Modul, ohne andere Abhängigkeiten zu aktualisieren:

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. Aktualisieren Sie dann das Elasticsearch 8-Modul und die `aws/aws-sdk-php`:

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   Dieser Ansatz funktioniert für 2.4.7-p4 mit PHP 8.3. Das Problem tritt auf, weil `aws/aws-sdk-php` `psr/http-message >= 2.0` erfordert, was zu Konflikten führen kann. Die oben genannten Schritte helfen beim Beheben dieser Abhängigkeitsprobleme.

   +++

1. Aktualisieren Sie Ihre Projektkomponenten.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Konfigurieren von Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in der [!DNL Admin].

1. Indizieren Sie den Katalogindex neu.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Löschen Sie alle Elemente aus den aktivierten Cache-Typen.

   ```bash
   bin/magento cache:clean
   ```

#### Elasticsearch herunterstufen

Wenn Sie versehentlich die Version von Elasticsearch auf Ihrem Server aktualisieren oder feststellen, dass Sie aus einem anderen Grund ein Downgrade durchführen müssen, müssen Sie auch Ihre Adobe Commerce-Projektabhängigkeiten aktualisieren. Zum Beispiel für ein Downgrade von Elasticsearch 8.x auf 7.x

1. Führen Sie ein Downgrade des Elasticsearch 8.x-Servers auf 7.x durch und stellen Sie sicher, dass dieser ausgeführt wird. Siehe die [Elasticsearch-Dokumentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Aktualisieren Sie im Stammverzeichnis Ihres Adobe Commerce-Projekts Ihre Composer-Abhängigkeiten, um das `Magento_Elasticsearch8` und seine Composer-Abhängigkeiten zu entfernen und das `Magento_Elasticsearch7` zu installieren.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Aktualisieren Sie Ihre Projektkomponenten.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Konfigurieren von Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in der [!DNL Admin].

1. Indizieren Sie den Katalogindex neu.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Löschen Sie alle Elemente aus den aktivierten Cache-Typen.

   ```bash
   bin/magento cache:clean
   ```

### Erweiterungen von Drittanbietern

Es wird empfohlen, sich an den Suchmaschinenanbieter zu wenden, um festzustellen, ob Ihre Erweiterung vollständig mit einer Adobe Commerce-Version kompatibel ist.

## Datenbanktabellenformat konvertieren

Sie müssen das Format aller Datenbanktabellen von `COMPACT` in `DYNAMIC` konvertieren. Außerdem müssen Sie den Speichermodultyp von `MyISAM` in `InnoDB` konvertieren. Siehe [Best Practices](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Festlegen des Limits für geöffnete Dateien

Das Festlegen des Grenzwerts für offene Dateien (ulimit) kann dazu beitragen, Fehler durch mehrere rekursive Aufrufe langer Abfragezeichenfolgen oder Probleme mit der Verwendung des `bin/magento setup:rollback`-Befehls zu vermeiden. Dieser Befehl unterscheidet sich für verschiedene UNIX-Shells. Einzelheiten zum Befehl `ulimit` sind in der jeweiligen Variante zu finden.

Adobe empfiehlt, die geöffneten Dateien [ulimit](https://ss64.com/bash/ulimit.html) auf einen Wert von `65536` oder mehr festzulegen, Sie können jedoch bei Bedarf einen größeren Wert verwenden. Sie können ulimit auf der Befehlszeile festlegen oder es zu einer dauerhaften Einstellung für die Shell des Benutzers machen.

So legen Sie ulimit über die Befehlszeile fest:

1. Wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Setzen Sie ulimit auf `65536`.

   ```bash
   ulimit -n 65536
   ```

So legen Sie den Wert in Ihrer Bash-Shell fest:

1. Wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Öffnen Sie `/home/<username>/.bashrc` in einem Texteditor.
1. Fügen Sie die folgende Zeile hinzu:

   ```bash
   ulimit -n 65536
   ```

1. Speichern Sie Ihre Änderungen in der `.bashrc` und beenden Sie den Texteditor.

>[!IMPORTANT]
>
>Es wird empfohlen, in der `pcre.recursion_limit`-Datei keinen Wert für die `php.ini`-Eigenschaft festzulegen, da dies zu unvollständigen Rollbacks ohne Fehlermeldung führen kann.

## Überprüfen, ob Cron-Aufträge ausgeführt werden

Der UNIX-Aufgabenplaner `cron` ist für den täglichen Adobe Commerce-Betrieb von entscheidender Bedeutung. Es werden Dinge wie Neuindizierung, Newsletter, E-Mails und Sitemaps geplant. Einige Funktionen erfordern mindestens einen Cron-Auftrag, der als Dateisysteminhaber ausgeführt wird.

Um sicherzustellen, dass Ihr Cron-Auftrag ordnungsgemäß eingerichtet ist, überprüfen Sie die Registerkarte crontab , indem Sie den folgenden Befehl als Dateisystembesitzer eingeben:

>[!NOTE]
>
>Die crontab ist die Konfigurationsdatei, die für die Ausführung von Cron-Aufträgen zuständig ist.

```bash
crontab -l
```

Es sollten Ergebnisse ähnlich den folgenden angezeigt werden:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Ein weiteres Symptom dafür, dass cron nicht ausgeführt wird, ist der folgende Fehler in der Admin-Datei:

![Systemmeldungen - Cron läuft nicht](../../assets/upgrade-guide/cron-not-running.png)

Um den Fehler anzuzeigen, klicken Sie **Systemmeldungen** oben im Fenster wie folgt:

![Systemnachrichten-Benachrichtigung](../../assets/upgrade-guide/system-messages.png)

Weitere Informationen finden [&#x200B; unter „Konfigurieren &#x200B;](../../configuration/cli/configure-cron-jobs.md) Ausführen von cron“.

## SET DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 enthält Sicherheitsverbesserungen, die erfordern, dass einige Daten von serialisierten in JSON-Dateien konvertiert werden. Diese Konvertierung findet während des Upgrades statt und kann lange dauern, je nachdem, wie viele Daten sich in Ihrer Datenbank befinden.

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

Wenn Sie über eine große Datenmenge verfügen, können Sie die Leistung verbessern, indem Sie `DATA_CONVERTER_BATCH_SIZE` den Wert einer Umgebungsvariablen festlegen. Standardmäßig ist der Wert auf `50,000` festgelegt.

So legen Sie die Umgebungsvariable fest:

1. Wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Legen Sie die Variable fest:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` erfordert Arbeitsspeicher. Stellen Sie ihn nicht auf einen großen Wert (ca. 1 GB) ein, ohne ihn zuerst zu testen.

1. Nach Abschluss des Upgrades können Sie die Variable deaktivieren:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Überprüfen von Dateisystemberechtigungen

Aus Sicherheitsgründen erfordert Adobe Commerce bestimmte Berechtigungen für das Dateisystem. Berechtigungen unterscheiden sich von _[Inhaberschaft](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. Die Eigentümerschaft bestimmt, wer Aktionen im Dateisystem durchführen kann. Berechtigungen bestimmen, was der Benutzer tun kann.

Verzeichnisse im Dateisystem müssen von der Gruppe [Dateisystemeigentümer“ beschreibbar &#x200B;](../../installation/prerequisites/file-system/overview.md).

Um sicherzustellen, dass Ihre Dateisystemberechtigungen ordnungsgemäß festgelegt sind, melden Sie sich entweder beim Anwendungsserver an oder verwenden Sie die Dateimanager-Anwendung Ihres Hosting-Anbieters.

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
* Der Dateisystembesitzer ist `magento_user`

Um genauere Informationen zu erhalten, können Sie den folgenden Befehl eingeben:

```bash
ls -la /var/www/html/magento2/pub
```

Da Adobe Commerce statische Datei-Assets in Unterverzeichnissen von `pub` bereitstellt, empfiehlt es sich, auch dort die Berechtigungen und die Eigentümerschaft zu überprüfen.

Weitere Informationen finden Sie unter [Dateisystemberechtigungen und -eigentümerschaft](../../installation/prerequisites/file-system/overview.md).

## Festlegen des `pub/` Ordnerstamms

Weitere [&#x200B; finden Sie unter „Ändern des &#x200B;](../../installation/tutorials/docroot.md) zur Verbesserung der Sicherheit“.

## Installieren des Composer-Aktualisierungs-Plug-ins

Das Plug-in [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer löst Änderungen auf, die an der `composer.json`-Datei des Stammprojekts vorgenommen werden müssen, bevor sie auf eine neue Produktanforderung aktualisiert werden.

Das Plug-in automatisiert die manuelle Aktualisierung teilweise, indem es Abhängigkeitskonflikte identifiziert und behebt, anstatt sie manuell identifizieren und beheben zu müssen.

So installieren Sie das Plug-in:

1. Fügen Sie das Paket zu Ihrer `composer.json` hinzu.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten:

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2025-11-25 11:39:51 -->
