---
title: Verwalten von Modulen und Erweiterungen (Entwickler)
description: Verwalten Sie Adobe Commerce-Module und -Erweiterungen mithilfe der Befehlszeilenschnittstelle und des Package Managers „Composer“.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%

---

# Module und Erweiterungen verwalten

Mitwirkende Entwickelnde aktualisieren Module und Erweiterungen, indem sie ihre Versionen in der Adobe Commerce-`composer.json` angeben. Wenn Sie kein beitragender Entwickler sind, lesen Sie [Durchführen eines Upgrades](../implementation/perform-upgrade.md).

Sie können der `composer.json`-Datei entweder einen `require` Abschnitt hinzufügen oder den `composer require` Befehl wie folgt verwenden:

{{$include /help/_includes/server-login.md}}

Sie haben die folgenden Optionen:

## Verfügbare Modulversionen abrufen

Befehlsverwendung:

```shell
composer show --all <vendor>/<name>
```

Beispiel:

```shell
composer show --all example/module
```

## Verwenden des Befehls `composer require`

Befehlsverwendung:

```shell
composer require <vendor>/<name>:<version>
```

Beispiel:

```shell
composer require example/module:1.0.0
```

Warten Sie, während Composer die Abhängigkeiten aktualisiert und das Modul installiert.

## Fügen Sie der Datei „composer.json“ einen `require` Abschnitt hinzu

1. Öffnen Sie die `composer.json` in einem Texteditor.

1. Fügen Sie einen `require` Abschnitt hinzu.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Speichern Sie Ihre Änderungen in der `composer.json` und beenden Sie den Texteditor.

1. Auflösen von Abhängigkeiten und Schreiben exakter Versionen in die `composer.lock`.

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
