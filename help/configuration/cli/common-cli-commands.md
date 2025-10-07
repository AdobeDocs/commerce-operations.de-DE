---
title: Allgemeine Befehle
description: Erfahren Sie mehr über gängige Adobe Commerce-CLI-Befehle und deren Anwendungsbeispiele. Entdecken Sie wichtige Befehlszeilen-Tools für Entwicklung und Administration.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Allgemeine Befehle

Im Folgenden werden einige der verfügbaren Befehle zusammengefasst.

**So zeigen Sie eine vollständige Liste der Befehle an**:

```bash
bin/magento list
```

Beispiel für einen Hilfe-Befehl:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Befehle werden nur im Zusammenfassungsformular angezeigt. Klicken Sie auf den Link in der Spalte Befehl, um weitere Informationen zu einem Befehl zu erhalten.

| Befehl | Beschreibung |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Verwaltet den Cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Verwaltet die Indexer |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Führt Commerce-Cron-Aufträge aus |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Kompiliert alle nicht vorhandenen Proxys und Factories und kompiliert Klassendefinitionen, Vererbungsinformationen und Plug-in-Definitionen vorab für einen Store und eine Website. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Modulabhängigkeiten, zirkuläre Abhängigkeiten und Commerce-Framework-Abhängigkeiten. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Erstellt ein Übersetzungs-Wörterbuch oder ein Übersetzungspaket |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Stellt statische Ansichtsdateien bereit |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Erstellt CSS aus LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Führt automatisierte Tests durch |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Aktualisieren Sie Ihre XML-Layoutdateien, um sie an die neue XSLT-Formatvorlage (Extensible Stylesheet Language Transformations) anzupassen |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Generieren von Daten für Leistungstests. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installiert optionale Beispieldaten, nachdem Sie die Commerce-Anwendung installiert haben.<br><br>Weitere Informationen zu Beispieldaten finden Sie unter [Optionale Beispieldaten](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Verwaltet Backend-Konfigurationen |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Erstellt/bearbeitet/entsperrt Admin-Benutzer. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Aktiviert/deaktiviert Hinweise auf Entwicklervorlagen. |

## Häufige Argumente

Die folgenden Argumente gelten für [alle Befehle](/help/tools/reference/commerce-on-premises.md). Diese Befehle können entweder vor oder nach der Installation der Commerce-Software ausgeführt werden:

| Lange Version | Kurzversion | Bedeutung |
|--- |--- |--- |
| `--help` | `-h` | Hilfe zu jedem Befehl. Beispiel: `./magento help setup:install` oder `./magento help setup:config:set`. |
| `--quiet` | `-q` | Ruhiger Modus; keine Ausgabe. |
| `--no-interaction` | `-n` | Keine interaktiven Fragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Ausführlichkeitsstufe. Beispielsweise zeigt `--verbose=3` oder `-vvv` die ausführlichste Ausgabe als Debugging-Ausführlichkeit an. Der Standardwert ist `--verbose=1` oder `-v`. |
| `--version` | `-V` | Diese Anwendungsversion anzeigen |
| `--ansi` | Nicht zutreffend | ANSI-Ausgabe erzwingen |
| `--no-ansi` | Nicht zutreffend | ANSI-Ausgabe deaktivieren |
