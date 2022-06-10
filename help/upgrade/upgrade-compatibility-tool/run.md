---
title: '"Führen Sie die [!DNL Upgrade Compatibility Tool]"'
description: Führen Sie die folgenden Schritte aus, um [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle für Ihr Adobe Commerce-Projekt.
source-git-commit: 1dde98ab903f54aee0a094efd86dbf296065e92c
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 0%

---


# Laden Sie die [!DNL Upgrade Compatibility Tool]

{{commerce-only}

Erste Schritte mit dem [!DNL Upgrade Compatibility Tool] Laden Sie es in einer Befehlszeilenschnittstelle herunter, indem Sie den folgenden Befehl ausführen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle

Die [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

Siehe dies [Video-Tutorial](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) , um mehr über die [!DNL Upgrade Compatibility Tool].

Verfügbare Befehle für [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle:

| **Befehl** | **Beschreibung** |
|----------------|-----------------|
| `upgrade:check` | Mit diesem Befehl wird die [!DNL Upgrade Compatibility Tool] durch Analyse aller darin installierten Module. |
| `core:code:changes` | Dieser Befehl vergleicht Ihre aktuelle Adobe Commerce-Installation mit einer sauberen Vanilla-Installation. |
| `refactor` | Dieser Befehl behebt automatisch eine reduzierte Anzahl von Problemen. |
| `graphql:compare` | Dieser Befehl bietet die Möglichkeit, zwei GraphQL-Endpunkte zu überprüfen und ihre Schemas zu vergleichen. |
| `list` | Dieser Befehl gibt eine Liste aller [!DNL Upgrade Compatibility Tool] verfügbare Befehle. |
| `help` | Dieser Befehl gibt alle verfügbaren `help`Optionen für [!DNL Upgrade Compatibility Tool]. Dieser Befehl kann ebenso ausgeführt werden wie eine Option mit den vorherigen Befehlen. |

## Verwenden Sie die `upgrade:check` command

Die `upgrade:check` -Befehl sucht nach Änderungen am Kerncode für diese bestimmte Adobe Commerce-Instanz und alle darin installierten Änderungen an benutzerdefiniertem Code.

Die `upgrade:check` -Befehl ist der Hauptbefehl zum Ausführen des Tools:

```bash
bin/uct upgrade:check <dir>
```

Wo `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Verfügbare Optionen für `upgrade:check` command:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Gibt alle verfügbaren Optionen zurück.</li><li>—min-issue-level: Sie können Probleme nach der minimalen Problemstufe filtern (der Standardwert lautet WARNING).</li><li>—ignore-current-version-compatibility-issues (oder -i): Wenn Sie keine kritischen Probleme, Fehler und Warnungen aus der aktuellen Version in Ihren Bericht aufnehmen möchten.</li><li>—coming-version (oder -c): Targeting einer bestimmten Adobe Commerce-Version.</li></ul> |

Die [!DNL Upgrade Compatibility Tool] ermöglicht Ihnen, die `upgrade:check` -Befehl mit einer `--ignore-current-version-compatibility-issues` -Option. Verwenden Sie diese Option, wenn Sie nur neue Probleme erhalten möchten, die mit der Aktualisierung von Ihrer aktuellen Version auf die Zielversion in Ihrer [!DNL Upgrade Compatibility Tool] Bericht:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Dies gilt nur für PHP-API-Überprüfungen.

### Hinzufügen der `--coming-version` option

Sie können Ihre aktuelle Adobe Commerce-Installation mit einer beliebigen Adobe Commerce-Version vergleichen `>=2.3` durch Verwendung von `--coming-version` -Option.

Sie müssen die Version als Parameter angeben, wenn Sie die `upgrade:check` command:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Wo `-c, --coming-version[=COMING-VERSION]` bezieht sich auf die Zielversion von Adobe Commerce.

Es gibt einige Einschränkungen bei der Ausführung der `--coming-version`:

- Dieser Parameter bezieht sich auf alle Tags, die eine bestimmte Version von Adobe Commerce identifizieren.
- Es ist eine Pflicht, dies explizit anzugeben. Die Bereitstellung nur des Werts funktioniert nicht.
- Geben Sie die Tag-Version ohne Anführungszeichen an (weder Einzel- noch Doppelpunkt): ~~&quot;2.4.1-develop&quot;~~.
- Sie sollten KEINE älteren Versionen als die derzeit installierten bereitstellen und auch nicht ältere als 2.3, die derzeit die älteste Version ist, die unterstützt wird.

## Verwenden Sie die `core:code:changes` command

Sie können Ihre aktuelle Adobe Commerce-Installation mit der Überprüfung vergleichen, ob der Kerncode von Adobe Commerce zur Implementierung einer Anpassung geändert wurde. Dieser Befehl zeigt nur eine Liste der wichtigsten Änderungen:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `<vanilla dir>`: Adobe Commerce-Vanilla-Installationsordner.

Verfügbare Optionen für `core:code:changes` command:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Gibt alle verfügbaren zurück `--help` Optionen. |

>[!NOTE]
>
> Es empfiehlt sich, benutzerdefinierten Code aus dem Kerncode herauszuhalten. Siehe Adobe Commerce 2.4 [Upgrade-Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) für weitere Best Practices bei der Aktualisierung.

### Vanilla-Installation

A _Vanille_ Bei der Installation handelt es sich um eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

Die `bin/uct core:code:changes` -Befehl prüft, ob sich in Ihrem System eine Vanilla-Instanz befindet. Wenn Sie zum ersten Mal eine Vanilla-Installation verwenden, werden Sie durch eine interaktive Befehlszeilenfrage aufgefordert, das Vanilla-Projekt aus dem Adobe Commerce-Repository herunterzuladen (`https://repo.magento.com/`).

Sie können eine [!DNL Upgrade Compatibility Tool] mit dem Befehl `--vanilla-dir` -Option, um den Installationsordner für Adobe Commerce Vanilla anzugeben.

Siehe [Vanilla-Instanz bereitstellen](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) für weitere Informationen.

## Verwenden Sie die `refactor` command

Die [!DNL Upgrade Compatibility Tool] hat die Möglichkeit, einen reduzierten Satz von Problemen automatisch zu beheben:

- Funktionen, die verwendet werden dürfen, ohne ein -Argument zu übergeben, aber mit einer solchen Verwendung sind jetzt veraltet.
- Verwendung `$this` in Magento-Vorlagen.
- Verwendung des PHP-Suchbegriffs `final` in privaten Methoden.

Führen Sie dazu die `refactor` command:

```bash
bin/uct refactor <dir>
```

Wo `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Verfügbare Optionen für `refactor` command:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `refactor` | `--help`: Gibt alle verfügbaren zurück `--help` Optionen. |

## Verwenden Sie die `graphql:compare` command

Dieser Befehl bietet die Option zum [!DNL Upgrade Compatibility Tool] , um zwei GraphQL-Endpunkte einzuführen und ihre Schemas zu vergleichen, die nach brechenden und gefährlichen Änderungen zwischen ihnen suchen:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Wenn die Argumente wie folgt lauten:

- `<schema1>`: Endpunkt-URL für die vorhandene Installation.
- `<schema2>`: Endpunkt-URL für die Vanilla-Installation.

Verfügbare Optionen für `graphql:compare` command:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Gibt alle verfügbaren zurück `--help` Optionen. |

## Verwenden Sie die `list` command

So geben Sie eine Liste der [!DNL Upgrade Compatibility Tool] verfügbare Befehle, ausführen:

```bash
bin/uct list
```

## Verwenden Sie die `--help` command

So zeigen Sie die [!DNL Upgrade Compatibility Tool] allgemeine Optionen und Hilfe, ausführen:

```bash
bin/uct --help
```

Gibt eine Liste mit allen verfügbaren `help` Optionen für [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle:

```terminal
- -m, --module-path[=MODULE-PATH]: Path of the modules to be analysed
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

Es ist jedoch möglich, `--help` als Option beim Ausführen eines bestimmten Befehls. Dies gibt spezifische `--help` Optionen für diesen spezifischen Befehl.

Beispiel der `upgrade:check` Befehl mit `--help` Option:

```bash
bin/uct upgrade:check --help
```

Dadurch werden bestimmte Optionen zurückgegeben, die für die `upgrade:check` command:

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Befolgen Sie die Best Practices für Adobe Commerce

- Vermeiden Sie es, zwei Module mit demselben Namen zu haben.
- Folgen Sie Adobe Commerce [Codierungsstandards](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).
- Adobe Commerce 2.4 [Upgrade-Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) Best Practices.

## Ergebnisse optimieren

Die [!DNL Upgrade Compatibility Tool] liefert einen Bericht mit Ergebnissen, in dem alle in Ihrem Projekt identifizierten Probleme standardmäßig aufgeführt sind. Sie können die Ergebnisse optimieren, um sich auf die Probleme zu konzentrieren, die Sie beheben müssen, um das Upgrade abzuschließen:

- Option verwenden `--ignore-current-version-compatibility-issues` wenn Sie nur neue Probleme erhalten möchten, die mit der Aktualisierung von Ihrer aktuellen Version auf die Zielversion in Ihrer [!DNL Upgrade Compatibility Tool] Bericht.
- Hinzufügen der `--min-issue-level` festlegen, können Sie mit dieser Einstellung das minimale Problem-Level festlegen, damit nur die wichtigsten Probleme bei Ihrem Upgrade priorisiert werden.
- Die [!DNL Upgrade Compatibility Tool] erfordert mindestens 2 GB RAM für die Ausführung. Diese Einstellung wird empfohlen, um Probleme aufgrund einer geringen Speicherbegrenzung zu vermeiden. Die [!DNL Upgrade Compatibility Tool] zeigt eine Frage an, wenn Sie die `upgrade:check` -Befehl mit einer niedrigen `memory_limit` -Einstellung.
- Wenn Sie nur ein bestimmtes Anbieter, Modul oder Verzeichnis analysieren möchten, können Sie auch den Pfad als Option angeben. Führen Sie die `bin` -Befehl mit der hinzugefügten Option `-m`. Dies ermöglicht die [!DNL Upgrade Compatibility Tool] , um ein bestimmtes Modul unabhängig zu analysieren, und hilft bei Speicherproblemen, die auftreten können, wenn das [!DNL Upgrade Compatibility Tool]. Geben Sie die `-m` -Option, um das Tool für ein bestimmtes Modul auszuführen:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=MODULE-PATH]`: Spezifisches Modulpfadverzeichnis.
