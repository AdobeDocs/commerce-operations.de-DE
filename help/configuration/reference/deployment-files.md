---
title: Konfigurationsdateien für die Bereitstellung
description: Erfahren Sie, wie Konfigurationsdateien für die Bereitstellung von Adobe Commerce-Anwendungen funktionieren. Lernen Sie die Best Practices für die gemeinsame und systemspezifische Konfigurationsverwaltung kennen.
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Konfigurationsdateien für die Bereitstellung

Adobe Commerce stellt Konfigurationsdateien bereit, mit denen Sie eine Komponente einfach anpassen und Konfigurationstypen erstellen können, um die Standardfunktionalität zu erweitern. Der Prozess der Bereitstellungskonfiguration besteht aus der freigegebenen und systemspezifischen Konfiguration für Ihre Installation. Die Commerce-Bereitstellungskonfiguration ist auf [`app/etc/config.php`](../reference/config-reference-configphp.md) und [`app/etc/env.php`](../reference/config-reference-envphp.md) aufgeteilt.

- `app/etc/config.php` ist die Konfigurationsdatei _shared_.
Diese Datei enthält die Liste der installierten Module, Designs und Sprachpakete sowie freigegebene Konfigurationseinstellungen.

  Checken Sie diese Datei in die Versionskontrolle ein und verwenden Sie sie in Ihren Entwicklungs-, Staging- und Produktionssystemen.

- `app/etc/env.php` enthält für die Installationsumgebung spezifische Einstellungen.

`config.php` und `env.php` werden zusammen als Commerce-Bereitstellungskonfiguration bezeichnet _da_ Dateien während der Installation erstellt werden und zum Starten der Commerce-Anwendung erforderlich sind.

>[!INFO]
>
>Die [!DNL Commerce 2]-Bereitstellungskonfiguration ersetzt `local.xml` in [!DNL Magento 1.x].

Im Gegensatz zu anderen [Modulkonfigurationsdateien](../reference/module-files.md) wird die Commerce-Bereitstellungskonfiguration bei der Initialisierung in den Speicher geladen, wird nicht mit anderen Dateien zusammengeführt und kann nicht erweitert werden. (`config.php` und `env.php` werden jedoch miteinander verschmolzen.)

## Details zur Bereitstellungskonfiguration

`config.php` und `env.php` sind PHP-Dateien, die ein [multidimensionales assoziatives Array](https://www.w3schools.com:443/php/php_arrays.asp) zurückgeben, welches im Grunde eine hierarchische Anordnung von Konfigurationsparametern und -werten ist.

Auf der obersten Ebene dieses Arrays befinden sich _Konfigurationssegmente_. Ein Segment verfügt über willkürlichen Inhalt (einen Skalarwert oder ein verschachteltes Array), der durch einen willkürlichen Schlüssel unterschieden wird, wobei sowohl das Schlüssel- als auch das Wertpaar vom Commerce-Framework definiert werden.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) bietet lediglich Zugriff auf diese Abschnitte, erlaubt Ihnen jedoch nicht, sie zu erweitern.

Auf der nächsten Hierarchieebene werden die Elemente in jedem Segment gemäß der Modulsequenzdefinition sortiert, die durch Zusammenführen der Konfigurationsdateien aller Module - mit Ausnahme deaktivierter Module - erhalten wird.

In den folgenden Abschnitten werden die Struktur und der Inhalt der Bereitstellungskonfiguration erläutert:

- Installierte Module verwalten
- Systemspezifische Konfiguration

## Installierte Module verwalten

Die `config.php`-Datei enthält eine Liste der installierten Module. Adobe Commerce bietet sowohl Befehlszeilen- als auch Web-basierte Dienstprogramme zum Verwalten von Modulen (Installieren, Deinstallieren, Aktivieren, Deaktivieren oder Aktualisieren).

Beispiele:

- Komponenten deinstallieren: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Überprüfen des Status von Komponenten: [`bin/magento module:status`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
- Aktivieren oder Deaktivieren von Komponenten: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

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

Deaktivierte Module werden von der Commerce-Anwendung nicht erkannt, d. h. sie sind nicht an der Zusammenführungskonfiguration, der Injektion von Abhängigkeiten, Ereignissen, Plug-ins usw. beteiligt. Deaktivierte Module ändern weder die Storefront noch den Administrator und wirken sich nicht auf das Routing aus.

Der einzige praktische Unterschied zwischen einem deaktivierten Modul und einem fehlenden Modul in der Code-Basis besteht darin, dass ein deaktiviertes Modul vom Autoloader gefunden wird und seine Klassen und Konstanten zur Wiederverwendung in anderem Code verfügbar sind.
