---
title: Konfigurationsdateien für die Bereitstellung
description: Erfahren Sie, wie die Konfigurationsdateien für die Installation der Commerce-Anwendung funktionieren.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Konfigurationsdateien für die Bereitstellung

Adobe Commerce bietet Konfigurationsdateien, mit denen Sie eine Komponente einfach anpassen und Konfigurationstypen erstellen können, um die Standardfunktion zu erweitern. Der Bereitstellungsprozess besteht aus der freigegebenen und systemspezifischen Konfiguration für Ihre Installation. Die Implementierungskonfiguration von Commerce ist unterteilt in [`app/etc/config.php`](../reference/config-reference-configphp.md) und [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` ist die _shared_ Konfigurationsdatei.
Diese Datei enthält die Liste der installierten Module, Designs und Sprachpakete. und freigegebenen Konfigurationseinstellungen.

   Checken Sie diese Datei in die Quell-Code-Verwaltung ein und verwenden Sie sie in Ihren Entwicklungs-, Staging- und Produktionssystemen.

   Ab Version 2.2 `app/etc/config.php` -Datei ist kein Eintrag mehr in der `.gitignore` -Datei.
Dies wurde erleichtert [Pipeline-Bereitstellung](../deployment/technical-details.md).

- `app/etc/env.php` enthält Einstellungen, die für die Installationsumgebung spezifisch sind.

Gemeinsam `config.php` und `env.php` als &quot;Handel&quot;bezeichnet werden _Bereitstellungskonfiguration_ weil die Dateien während der Installation erstellt werden und zum Starten der Commerce-Anwendung erforderlich sind.

>[!INFO]
>
>Die [!DNL Commerce 2] Die Bereitstellungskonfiguration ersetzt `local.xml` in [!DNL Magento 1.x].

Im Gegensatz zu anderen [Modulkonfigurationsdateien](../reference/module-files.md), wird die Konfiguration der Commerce-Bereitstellung während der Initialisierung in den Speicher geladen, wird nicht mit anderen Dateien zusammengeführt und kann nicht erweitert werden. (`config.php` und `env.php` zusammengeführt werden.)

## Details zur Bereitstellungskonfiguration

`config.php` und `env.php` sind PHP-Dateien, die eine [Mehrdimensionales assoziatives Array](https://www.w3schools.com:443/php/php_arrays.asp), was im Wesentlichen eine hierarchische Anordnung von Konfigurationsparametern und -werten ist.

Auf der obersten Ebene dieses Arrays finden Sie _Konfigurationssegmente_. Ein Segment weist beliebigen Inhalt (einen skalaren Wert oder ein verschachteltes Array) auf, der sich durch einen beliebigen Schlüssel unterscheidet, wobei sowohl das Schlüssel-Wert-Paar durch das Commerce-Framework definiert wird.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) bietet lediglich Zugriff auf diese Abschnitte, lässt jedoch keine Erweiterung zu.

Auf der nächsten Hierarchieebene werden Elemente in jedem Segment gemäß der Modulsequenzdefinition geordnet, die durch Zusammenführen der Konfigurationsdateien aller Module mit Ausnahme deaktivierter Module abgerufen wird.

In den folgenden Abschnitten werden Struktur und Inhalt der Bereitstellungskonfiguration beschrieben:

- Verwalten installierter Module
- Systemspezifische Konfiguration

## Verwalten installierter Module

Die `config.php` enthält eine Liste der installierten Module. Adobe Commerce bietet sowohl Befehlszeilen- als auch webbasierte Dienstprogramme zum Verwalten von Modulen (Installieren, Deinstallieren, Aktivieren, Deaktivieren oder Aktualisieren).

Beispiele:

- Deinstallieren von Komponenten: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Status von Komponenten überprüfen: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Komponenten aktivieren oder deaktivieren: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

Der Wert `1` oder `0` gibt an, ob ein Modul aktiviert oder deaktiviert ist.

Deaktivierte Module werden von der Commerce-Anwendung nicht erkannt. Mit anderen Worten, sie nehmen nicht an der Zusammenführung von Konfiguration, Abhängigkeitsinjektion, Ereignissen, Plug-ins usw. teil. Deaktivierte Module ändern weder die Storefront noch den Administrator und beeinflussen das Routing nicht.

Der einzige praktische Unterschied zwischen einem deaktivierten Modul und einem fehlenden Modul in der Codebasis besteht darin, dass ein deaktiviertes Modul vom Autoloader gefunden wird und seine Klassen und Konstanten für die Wiederverwendung in anderem Code verfügbar sind.
