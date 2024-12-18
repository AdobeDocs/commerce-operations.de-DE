---
title: Konfigurationseinstellungen exportieren
description: Exportieren Sie Adobe Commerce-Konfigurationseinstellungen in Konfigurationsdateien, die auch als Konfigurations-Dump bezeichnet werden.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Konfigurationseinstellungen exportieren

In Commerce 2.2 und höher [Pipeline-Bereitstellungsmodell](../deployment/technical-details.md) können Sie systemübergreifend eine konsistente Konfiguration beibehalten. Nachdem Sie die Einstellungen in der Admin auf Ihrem Entwicklungssystem konfiguriert haben, exportieren Sie diese Einstellungen mit dem folgenden Befehl in Konfigurationsdateien:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ ist eine durch Leerzeichen getrennte Liste der Konfigurationstypen, die ausgegeben werden sollen. Zu den verfügbaren Typen gehören `scopes`, `system`, `themes` und `i18n`. Wenn keine Konfigurationstypen angegeben sind, gibt der Befehl alle Systemkonfigurationsinformationen aus.

Im folgenden Beispiel werden nur Bereiche und Designs ausgegeben:

```bash
bin/magento app:config:dump scopes themes
```

Infolge der Ausführung des Befehls werden die folgenden Konfigurationsdateien aktualisiert:

- `app/etc/config.php`

  Dies ist die freigegebene Konfigurationsdatei für alle Commerce-Instanzen.
Fügen Sie dies in Ihre Quellcodeverwaltung ein, damit es von den Entwicklungs-, Build- und Produktionssystemen gemeinsam verwendet werden kann.

  Siehe [config.php-Referenz](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Dies ist die umgebungsspezifische Konfigurationsdatei.
Es enthält sensible und systemspezifische Einstellungen für einzelne Umgebungen.

  Fügen _diese_ nicht in die Quell-Code-Verwaltung ein

  Siehe [env.php-Referenz](../reference/config-reference-envphp.md).

## Sensible oder systemspezifische Einstellungen

Verwenden Sie den Befehl [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values), um die sensiblen Einstellungen festzulegen, die in `env.php` geschrieben werden.

Konfigurationswerte werden entweder als sensibel oder systemspezifisch angegeben, indem in der [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) des Moduls auf [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) verwiesen wird.

Wenn Sie bei Verwendung von `config_types` zusätzliche Systemeinstellungen exportieren möchten, sollten Sie den Befehl [`bin/magento config:set`](set-configuration-values.md#set-values) verwenden.
