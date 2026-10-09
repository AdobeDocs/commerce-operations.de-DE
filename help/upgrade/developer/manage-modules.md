---
title: Verwalten von Modulen und Erweiterungen (Entwickler)
description: Verwalten Sie Adobe Commerce-Module und -Erweiterungen mithilfe der Befehlszeilenschnittstelle und des Package Managers „Composer“.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
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

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
