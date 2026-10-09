---
title: Konfigurationseinstellungen exportieren
description: Erfahren Sie, wie Sie Adobe Commerce-Konfigurationseinstellungen mithilfe des Konfigurations-Dump in Dateien exportieren. Entdecken Sie Pipeline-Bereitstellung und Konfigurationsverwaltung.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%
---
# Konfigurationseinstellungen exportieren

In Commerce 2.2 und höher [Pipeline-Bereitstellungsmodell](../deployment/technical-details.md) können Sie systemübergreifend eine konsistente Konfiguration beibehalten. Nachdem Sie die Einstellungen in der Admin auf Ihrem Entwicklungssystem konfiguriert haben, exportieren Sie diese Einstellungen mit dem folgenden Befehl in Konfigurationsdateien:

```shell
bin/magento app:config:dump {config-types}
```

_config_ types_ ist eine durch Leerzeichen getrennte Liste der Konfigurationstypen, die ausgegeben werden sollen. Zu den verfügbaren Typen gehören `scopes`, `system`, `themes` und `i18n`. Wenn keine Konfigurationstypen angegeben sind, gibt der Befehl alle Systemkonfigurationsinformationen aus.

Im folgenden Beispiel werden nur Bereiche und Designs ausgegeben:

```shell
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

Konfigurationswerte werden entweder als sensibel oder systemspezifisch angegeben, indem in der [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings#how-to-specify-values-as-sensitive-or-system-specific) des Moduls auf [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) verwiesen wird.

Wenn Sie bei Verwendung von `config_types` zusätzliche Systemeinstellungen exportieren möchten, sollten Sie den Befehl [`bin/magento config:set`](set-configuration-values.md#set-values) verwenden.
