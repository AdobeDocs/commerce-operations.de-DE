---
title: Allgemeine Befehle
description: Sehen Sie sich ein Beispiel für gängige Commerce-CLI-Befehle und -Verwendung an.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Allgemeine Befehle

Im Folgenden werden einige der verfügbaren Befehle zusammengefasst.

**So zeigen Sie eine vollständige Liste der Befehle an**:

```bash
bin/magento list
```

Beispiel für einen Hilfebefehl:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Befehle werden nur in der Zusammenfassung angezeigt. Klicken Sie für weitere Informationen zu einem Befehl auf den Link in der Spalte &quot;Befehl&quot;.

| Befehl | Beschreibung |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Verwalten des Cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Verwaltet die Indexer |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Führt Commerce-Cron-Aufträge aus |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Kompiliert alle nicht vorhandenen Proxys und Fabriken und erstellt eine Vorkompilierung von Klassendefinitionen, Vererbungsinformationen und Plug-in-Definitionen für einen Store und eine Website. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Modulabhängigkeiten, zirkuläre Abhängigkeiten und Commerce-Framework-Abhängigkeiten. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Erstellt ein Übersetzungswörterbuch oder ein Übersetzungspaket |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Stellt statische Ansichtsdateien bereit |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Erstellt CSS aus LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Führt automatisierte Tests aus |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Aktualisieren Sie Ihre Layout-XML-Dateien entsprechend dem neuen XSLT-Stylesheet (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Generieren Sie Daten zur Verwendung für Leistungstests. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installiert optionale Beispieldaten nach der Installation der Commerce-Anwendung.<br><br>Weitere Informationen zu Musterdaten finden Sie unter [Optionale Musterdaten](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Verwalten von Backend-Konfigurationen |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Erstellt/bearbeitet/entsperrt Administratorbenutzer. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Aktiviert/deaktiviert Hinweise zu Entwicklervorlagen. |

## Allgemeine Argumente

Die folgenden Argumente gelten für alle Befehle. Diese Befehle können vor oder nach der Installation der Commerce-Software ausgeführt werden:

| Lange Version | Kurzversion | Bedeutung |
|--- |--- |--- |
| `--help` | `-h` | Erhalten Sie Hilfe für jeden Befehl. Beispiel: `./magento help setup:install` oder `./magento help setup:config:set`. |
| `--quiet` | `-q` | Ruhig, keine Ausgabe. |
| `--no-interaction` | `-n` | Keine interaktiven Fragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbosity level. Beispiel: `--verbose=3` oder `-vvv` zeigt Debug-Ausführlichkeit an, die die ausführlichste Ausgabe ist. Der Standardwert ist `--verbose=1` oder `-v`. |
| `--version` | `-V` | Diese Anwendungsversion anzeigen |
| `--ansi` | Nicht zutreffend | ANSI-Ausgabe erzwingen |
| `--no-ansi` | Nicht zutreffend | ANSI-Ausgabe deaktivieren |
