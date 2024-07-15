---
title: Technische Details
description: Erfahren Sie mehr über die technischen Details der Pipeline-Bereitstellung, die Arten von Konfigurationen und die empfohlenen Workflows.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Technische Details

In diesem Thema werden technische Implementierungsdetails zur Pipeline-Bereitstellung in Commerce 2.2 und höher erläutert. Die Verbesserungen lassen sich in folgende Bereiche unterteilen:

- [Konfigurationsverwaltung](#configuration-management)
- [Änderungen im Admin](#changes-in-the-admin)
- [Installieren und Entfernen von Cron](#install-and-remove-cron)

In diesem Thema wird auch der [empfohlene Workflow](#recommended-workflow) für die Pipeline-Bereitstellung erläutert und einige Beispiele bereitgestellt, anhand derer Sie verstehen können, wie er funktioniert.

Bevor Sie beginnen, überprüfen Sie die [Voraussetzungen für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md).

## Konfigurationsverwaltung

Verwenden Sie das folgende Überschreibungsschema, um die Konfiguration Ihrer Entwicklungs- und Produktionssysteme zu synchronisieren und zu verwalten.

![Wie die Werte der Konfigurationsvariablen bestimmt werden](../../assets/configuration/override-flow-diagram.png)

Wie das Diagramm zeigt, werden die Konfigurationswerte in der folgenden Reihenfolge verwendet:

1. Umgebungsvariablen überschreiben alle anderen Werte, sofern vorhanden.
1. Aus den freigegebenen Konfigurationsdateien `env.php` und `config.php`. Werte in `env.php` überschreiben Werte in `config.php`.
1. Aus in der Datenbank gespeicherten Werten.
1. Wenn in keiner dieser Quellen ein Wert vorhanden ist, wird der Standardwert oder NULL verwendet.

### Verwalten der freigegebenen Konfiguration

Die freigegebene Konfiguration wird in `app/etc/config.php` gespeichert, das sich in der Quell-Code-Verwaltung befinden sollte.

Legen Sie die freigegebene Konfiguration im Admin-System in Ihrer Entwicklungsumgebung (oder Adobe Commerce in der Cloud-Infrastruktur _integration_) fest und schreiben Sie die Konfiguration mit dem Befehl [`magento app:config:dump`](../cli/export-configuration.md) in `config.php`.

### Systemspezifische Konfiguration verwalten

Die systemspezifische Konfiguration wird in `app/etc/env.php` gespeichert, wobei _nicht_ im Quell-Code sein sollte.

Legen Sie die systemspezifische Konfiguration im Admin-System Ihres Entwicklungs- (oder Adobe Commerce-Integrationssystems der Cloud-Infrastruktur) fest und schreiben Sie die Konfiguration mit dem Befehl [`magento app:config:dump`](../cli/export-configuration.md) auf `env.php`.

Dieser Befehl schreibt auch vertrauliche Einstellungen in `env.php`.

### Vertrauliche Konfiguration verwalten

Die vertrauliche Konfiguration wird auch in `app/etc/env.php` gespeichert.

Sie können die vertrauliche Konfiguration auf eine der folgenden Arten verwalten:

- Umgebungsvariablen
- Speichern Sie die vertrauliche Konfiguration in `env.php` auf Ihrem Produktionssystem mit dem Befehl [`magento config:set:sensitive` ](../cli/set-configuration-values.md)

### In Admin gesperrte Konfigurationseinstellungen

Alle Konfigurationseinstellungen in `config.php` oder `env.php` sind im Admin gesperrt, d. h., diese Einstellungen können nicht im Admin geändert werden.
Verwenden Sie den Befehl [`magento config:set` oder `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set), um die Einstellungen in den Dateien `config.php` oder `env.php` zu ändern.

## Der Commerce-Administrator

Der Administrator weist im Produktionsmodus folgendes Verhalten auf:

- Sie können Cache-Typen in Admin nicht aktivieren oder deaktivieren
- Entwicklereinstellungen sind nicht verfügbar (**Speicher** > Einstellungen > **Konfiguration** > Erweitert > **Entwickler**), einschließlich:

   - Minimieren von CSS, JavaScript und HTML
   - Zusammenführen von CSS und JavaScript
   - Serverseitige oder clientseitige LESS-Kompilierung
   - Inline-Übersetzungen
   - Wie bereits erläutert, sind alle Konfigurationseinstellungen in `config.php` oder `env.php` gesperrt und können nicht im Admin bearbeitet werden.
   - Sie können das Gebietsschema &quot;Admin&quot;nur in Sprachen ändern, die von bereitgestellten Designs verwendet werden

     Die folgende Abbildung zeigt ein Beispiel der Liste **Kontoeinstellung** > **Gebietsschema der Schnittstelle** im Admin, in der nur zwei bereitgestellte Gebietsschemata angezeigt werden:

     ![Sie können das Admin-Gebietsschema nur in bereitgestellte Gebietsschemata ändern](../../assets/configuration/split-deploy-admin-locale.png)

- Mit dem Admin können Sie die Gebietsschemakonfigurationen für keinen Bereich ändern.

  Es wird empfohlen, diese Änderungen vorzunehmen, bevor Sie in den Produktionsmodus wechseln.

  Sie können das Gebietsschema weiterhin mit Umgebungsvariablen oder dem Befehl `config:set` CLI mit dem Pfad `general/locale/code` konfigurieren.

## Installieren und Entfernen von Cron

In Version 2.2 helfen wir Ihnen beim erstmaligen Einrichten Ihres Cron-Auftrags durch Bereitstellung des Befehls [`magento cron:install`](../cli/configure-cron-jobs.md). Mit diesem Befehl wird eine Crontab als der Benutzer eingerichtet, der den Befehl ausführt.

Sie können die Registerkarte auch mit dem Befehl `magento cron:remove` entfernen.

## Empfohlener Pipeline-Bereitstellungs-Workflow

Das folgende Diagramm zeigt, wie wir empfehlen, die Pipeline-Implementierung zur Verwaltung der Konfiguration zu verwenden.

![Empfohlener Pipeline-Bereitstellungs-Workflow](../../assets/configuration/split-deploy-workflow.png)

### Entwicklungssystem

Auf Ihrem Entwicklungssystem nehmen Sie Konfigurationsänderungen im Admin vor und generieren die freigegebene Konfiguration `app/etc/config.php` und die systemspezifische Konfiguration `app/etc/env.php`. Überprüfen Sie den Commerce-Code und die freigegebene Konfiguration in die Quell-Code-Verwaltung und pushen Sie ihn an den Build-Server.

Sie sollten auch Erweiterungen installieren und den Commerce-Code im Entwicklungssystem anpassen.

Auf Ihrem Entwicklungssystem:

1. Legen Sie die Konfiguration in Admin fest.

1. Verwenden Sie den Befehl `magento app:config:dump` , um die Konfiguration in das Dateisystem zu schreiben.

   - `app/etc/config.php` ist die freigegebene Konfiguration, die alle Einstellungen _außer_ enthält, die vertrauliche und systemspezifische Einstellungen enthalten. Diese Datei sollte sich in der Quell-Code-Verwaltung befinden.
   - `app/etc/env.php` ist die systemspezifische Konfiguration, die Einstellungen enthält, die für ein bestimmtes System eindeutig sind (z. B. Hostnamen und Portnummern). Diese Datei sollte sich _nicht_ im Quell-Code befinden.

1. Fügen Sie den modifizierten Code und die freigegebene Konfiguration zur Quell-Code-Verwaltung hinzu.

1. Führen Sie die folgenden Befehle aus, um während der Entwicklung generierten PHP-Code und statische Asset-Dateien zu entfernen:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Nachdem Sie die Befehle zum Löschen der Assets ausgeführt haben, generiert Commerce Arbeitsdateien.

>[!WARNING]
>
>Seien Sie vorsichtig mit dem oben genannten Ansatz. Das Löschen der Datei `.htacces` im Ordner `generated` oder `pub` kann Probleme verursachen.

### Build-System

Das Build-System kompiliert Code und generiert statische Ansichtsdateien für Designs, die in Commerce registriert sind. Es ist keine Verbindung zur Commerce-Datenbank erforderlich, sondern nur die Commerce-Codebasis.

Auf Ihrem Build-System:

1. Rufen Sie die freigegebene Konfigurationsdatei aus der Quell-Code-Verwaltung ab.
1. Verwenden Sie den Befehl `magento setup:di:compile` , um den Code zu kompilieren.
1. Verwenden Sie den Befehl `magento setup:static-content:deploy -f` , um statische Dateiansichtsdateien zu aktualisieren.
1. Überprüfen Sie die Aktualisierungen in der Quell-Code-Verwaltung.

>[!INFO]
>
>Siehe [Bereitstellungsstrategien für statische Ansichtsdateien](../cli/static-view-file-strategy.md).

### Produktionssystem

Auf Ihrem Produktionssystem (d. h. Ihrem Live Store) rufen Sie generierte Assets und Codeaktualisierungen aus der Quellcodeverwaltung ab und legen systemspezifische und vertrauliche Konfigurationseinstellungen mithilfe der Befehlszeile oder Umgebungsvariablen fest.

In Ihrem Produktionssystem:

1. Wartungsmodus starten
1. Rufen Sie Code- und Konfigurationsaktualisierungen aus der Quell-Code-Verwaltung ab.
1. Wenn Sie Adobe Commerce verwenden, beenden Sie die Warteschlangenarbeiter.
1. Verwenden Sie den Befehl `magento app:config:import` , um Konfigurationsänderungen in das Produktionssystem zu importieren.
1. Wenn Sie Komponenten installiert haben, die das Datenbankschema geändert haben, führen Sie `magento setup:upgrade --keep-generated` aus, um das Datenbankschema und die Daten zu aktualisieren, wobei die generierten statischen Dateien beibehalten werden.
1. Um systemspezifische Einstellungen festzulegen, verwenden Sie entweder den Befehl `magento config:set` oder Umgebungsvariablen.
1. Verwenden Sie zum Festlegen sensibler Einstellungen entweder den Befehl `magento config:sensitive:set` oder Umgebungsvariablen.
1. Löschen Sie den Cache (auch als _leeren_ bezeichnet).
1. Wartungsmodus beenden.

## Konfigurationsverwaltungsbefehle

Wir stellen die folgenden Befehle bereit, um Sie bei der Verwaltung der Konfiguration zu unterstützen:

- [`magento app:config:dump`](../cli/export-configuration.md) zum Schreiben der Admin-Konfigurationseinstellungen in `config.php` und `env.php` (außer bei sensiblen Einstellungen)
- [`magento config:set`](../cli/set-configuration-values.md) , um die Werte der systemspezifischen Einstellungen im Produktionssystem festzulegen.

  Verwenden Sie die optionale Option &quot;`--lock`&quot;, um die Option im Admin zu sperren (d. h., um die Einstellung unbearbeitbar zu machen). Wenn eine Einstellung bereits gesperrt ist, verwenden Sie die Option `--lock` , um die Einstellung zu ändern.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) , um die Werte der sensiblen Einstellungen im Produktionssystem festzulegen.
- [`magento app:config:import`](../cli/import-configuration.md) , um Konfigurationsänderungen von `config.php` und `env.php` in das Produktionssystem zu importieren.

## Beispiele für die Konfigurationsverwaltung

In diesem Abschnitt finden Sie Beispiele für die Verwaltung der Konfiguration, sodass Sie sehen können, wie Änderungen an `config.php` und `env.php` vorgenommen werden.

### Standardgebietsschema ändern

In diesem Abschnitt wird die Änderung an `config.php` angezeigt, wenn Sie die Standardgewichtseinheit mithilfe des Administrators ändern (**Geschäfte** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein** > **Gebietsschemaoptionen**).

Nachdem Sie die Änderung im Admin vorgenommen haben, führen Sie `bin/magento app:config:dump` aus, um den Wert in `config.php` zu schreiben. Der Wert wird in das Array `general` unter `locale` geschrieben, wie das folgende Codefragment aus `config.php` zeigt:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Mehrere Konfigurationseinstellungen ändern

In diesem Abschnitt werden die folgenden Konfigurationsänderungen besprochen:

- Hinzufügen einer Website-, Store- und Store-Ansicht (**Stores** > Einstellungen > **Alle Stores**)
- Ändern der Standard-E-Mail-Domäne (**Stores** > Einstellungen > **Konfiguration** > Kunden > **Kundenkonfiguration**)
- Festlegen des PayPal-API-Benutzernamen und -API-Kennworts (**Stores** > Einstellungen > **Konfiguration** > Vertrieb > **Zahlungsmethoden** > **PayPal** > **Erforderliche PayPal-Einstellungen**)

Nachdem Sie die Änderung im Admin vorgenommen haben, führen Sie `bin/magento app:config:dump` auf Ihrem Entwicklungssystem aus. Diesmal werden nicht alle Ihre Änderungen in `config.php` geschrieben. Tatsächlich werden nur die Website-, Store- und Store-Ansicht in diese Datei geschrieben, wie die folgenden Snippets zeigen.

### config.php

`config.php` enthält:

- Änderungen an der Website-, Store- und Store-Ansicht.
- Nicht systemspezifische Suchmaschineneinstellungen
- Nicht vertrauliche PayPal-Einstellungen
- Kommentare, die Sie über sensible Einstellungen informieren, die in &quot;`config.php`&quot;weggelassen wurden

`websites` array:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` array:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` array:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` array:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

Die standardmäßige systemspezifische Konfigurationseinstellung der E-Mail-Domain wird in `app/etc/env.php` geschrieben.

Die PayPal-Einstellungen werden in keine der beiden Dateien geschrieben, da der Befehl `bin/magento app:config:dump` keine vertraulichen Einstellungen schreibt. Sie müssen die PayPal-Einstellungen im Produktionssystem mit den folgenden Befehlen festlegen:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
