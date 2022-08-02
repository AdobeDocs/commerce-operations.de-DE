---
title: Allgemeine Befehle
description: Sehen Sie sich ein Beispiel für gängige Commerce-CLI-Befehle und -Verwendung an.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# Allgemeine Befehle

Im Folgenden werden einige der verfügbaren Befehle zusammengefasst.

**So zeigen Sie eine vollständige Liste der Befehle an**:

```bash
bin/magento list
```

Beispiel-Hilfebefehl:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Befehle werden nur in Form einer Zusammenfassung angezeigt. Klicken Sie für weitere Informationen zu einem Befehl auf den Link in der Spalte &quot;Befehl&quot;.

| Befehl | Beschreibung |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Verwalten des Cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Verwalten der Indexer |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Führt Commerce-Cron-Aufträge aus |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Kompiliert alle nicht vorhandenen Proxys und Fabriken; und kompiliert Klassendefinitionen, Vererbungsinformationen und Plug-in-Definitionen für einen Store und eine Website vorab. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Modulabhängigkeiten, zirkuläre Abhängigkeiten und Commerce-Framework-Abhängigkeiten. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Erstellt ein Übersetzungswörterbuch oder ein Übersetzungspaket |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Stellt statische Ansichtsdateien bereit |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Erstellt CSS aus LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Führt automatisierte Tests aus |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Aktualisieren Sie Ihre Layout-XML-Dateien entsprechend dem neuen XSLT-Stylesheet (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Generieren Sie Daten zur Verwendung für Leistungstests. |
| [`magento sampledata:install`](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html) | Installiert optionale Beispieldaten nach der Installation der Commerce-Anwendung.<br><br>Weitere Informationen zu Musterdaten finden Sie unter [Optionale Musterdaten](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Verwalten von Backend-Konfigurationen |
| [`magento admin:user:{create/unlock}`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-admin.html) | Erstellt/bearbeitet/entsperrt Administratorbenutzer. |
| [`magento dev:template-hints:{enable/disable}`](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/debug-theme.html) | Aktiviert/deaktiviert Hinweise zu Entwicklervorlagen. |

## Allgemeine Argumente

Die folgenden Argumente gelten für alle Befehle. Diese Befehle können vor oder nach der Installation der Commerce-Software ausgeführt werden:

| Lange Version | Kurzversion | Bedeutung |
|--- |--- |--- |
| `--help` | `-h` | Erhalten Sie Hilfe für jeden Befehl. Beispiel: `./magento help setup:install` oder `./magento help setup:config:set`. |
| `--quiet` | `-q` | Ruhezustand; keine Ausgabe. |
| `--no-interaction` | `-n` | Keine interaktiven Fragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbosity level. Beispiel: `--verbose=3` oder `-vvv` zeigt Debug-Ausführlichkeit an, die die ausführlichste Ausgabe ist. Der Standardwert ist `--verbose=1` oder `-v`. |
| `--version` | `-V` | Diese Anwendungsversion anzeigen |
| `--ansi` | Nicht zutreffend | ANSI-Ausgabe erzwingen |
| `--no-ansi` | Nicht zutreffend | ANSI-Ausgabe deaktivieren |
