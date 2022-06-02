---
title: '"Führen Sie die [!DNL Upgrade Compatibility Tool]"'
description: Führen Sie die folgenden Schritte aus, um [!DNL Upgrade Compatibility Tool] in Ihrem Adobe Commerce-Projekt.
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---


# Laden Sie die [!DNL Upgrade Compatibility Tool]

{{commerce-only}

Erste Schritte mit dem [!DNL Upgrade Compatibility Tool] Laden Sie es in einer Befehlszeilenschnittstelle herunter, indem Sie den folgenden Befehl ausführen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

>[!NOTE]
>
> Siehe [Voraussetzungen](../upgrade-compatibility-tool/prerequisites.md) für weitere Informationen zu den Mindestanforderungen für die Verwendung des Tools.

## Führen Sie die [!DNL Upgrade Compatibility Tool]

Die [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

Die [!DNL Upgrade Compatibility Tool] identifiziert potenzielle Probleme, die in Ihrem Code behoben werden müssen, bevor versucht wird, ein Upgrade auf eine neuere Version von Adobe Commerce durchzuführen.

Siehe dies [Video-Tutorial](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) , um mehr über die [!DNL Upgrade Compatibility Tool].

## Empfohlene Aktionen

### Ergebnisse optimieren

Die [!DNL Upgrade Compatibility Tool] liefert einen Bericht mit Ergebnissen, in dem alle in Ihrem Projekt identifizierten Probleme standardmäßig aufgeführt sind. Sie können die Ergebnisse optimieren, um sich auf die Probleme zu konzentrieren, die Sie beheben müssen, um das Upgrade abzuschließen:

- Option verwenden `--ignore-current-version-compatibility-issues`, wodurch alle bekannten kritischen Probleme, Fehler und Warnungen gegenüber Ihrer aktuellen Adobe Commerce-Version unterdrückt werden. Es werden nur Fehler gegenüber der Version bereitgestellt, auf die Sie ein Upgrade durchführen möchten.
- Fügen Sie die `--min-issue-level` festlegen, können Sie mit dieser Einstellung das minimale Problem-Level festlegen, damit nur die wichtigsten Probleme bei Ihrem Upgrade priorisiert werden.
- Wenn Sie nur ein bestimmtes Anbieter, Modul oder Verzeichnis analysieren möchten, können Sie auch den Pfad als Option angeben. Führen Sie die `bin` -Befehl mit der hinzugefügten Option `-m`. Dies ermöglicht die [!DNL Upgrade Compatibility Tool] , um ein bestimmtes Modul unabhängig zu analysieren, und hilft bei Speicherproblemen, die auftreten können, wenn das [!DNL Upgrade Compatibility Tool].

### Befolgen Sie die Best Practices für Adobe Commerce

- Vermeiden Sie es, zwei Module mit demselben Namen zu haben.
- Folgen Sie Adobe Commerce [Codierungsstandards](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## Verwenden Sie die `upgrade:check` command

Die `upgrade:check` -Befehl ist der Hauptbefehl zum Ausführen des Tools:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>Die `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Die `upgrade:check` -Befehl führt die [!DNL Upgrade Compatibility Tool] und überprüft eine benutzerdefinierte Adobe Commerce-Instanz auf eine bestimmte Version, indem alle darin installierten Module analysiert werden. Es wird eine Liste mit kritischen Problemen, Fehlern und Warnungen zurückgegeben, die behoben werden müssen, bevor ein Upgrade auf die neueste Version Ihres Adobe Commerce durchgeführt werden kann.

>[!WARNING]
>
>Führen Sie die Ausführung nur aus, wenn der Ordner des Projektstamms (oder des Hauptordners) angegeben ist.

Mit diesem Befehl werden Änderungen am Kerncode für diese bestimmte Adobe Commerce-Instanz sowie alle darin installierten Änderungen an benutzerdefiniertem Code überprüft.

Sie können die `core:code:changes` -Befehl, um nur Änderungen am Kerncode für diese bestimmte Adobe Commerce-Instanz zu analysieren. Siehe [Core-Code-Änderungen](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) Abschnitt.

Sie können die `graphql:compare` verwenden, um zwei GraphQL-Schemas zu vergleichen, um nach etwaigen Änderungen zwischen ihnen zu suchen. Siehe [Überprüfung der Kompatibilität mit GraphQL-Schemas](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) Abschnitt.

### Recommendations zur Verwendung der `upgrade:check` command

- Die [!DNL Upgrade Compatibility Tool] erfordert mindestens 2 GB RAM für die Ausführung. Diese Einstellung wird empfohlen, um Probleme aufgrund einer geringen Speicherbegrenzung zu vermeiden. Die [!DNL Upgrade Compatibility Tool] zeigt eine Frage an, wenn Sie die `upgrade:check` -Befehl mit einer niedrigen `memory_limit` -Einstellung.
- Geben Sie die `-m` -Option, um das Tool für ein bestimmtes Modul auszuführen:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `[=MODULE-PATH]`: Spezifisches Modulpfadverzeichnis.

### Verwenden Sie die `--help` option

So zeigen Sie die [!DNL Upgrade Compatibility Tool] allgemeine Optionen und Hilfe, ausführen:

```bash
bin/uct --help
```

Es ist jedoch möglich, `--help` als Option beim Ausführen eines bestimmten Befehls, z. B. `bin/uct upgrade:check`. Gibt spezifische `--help` Optionen für diesen Befehl:

```bash
bin/uct upgrade:check --help
```

Verfügbar `--help` Optionen für `upgrade:check` command:

- `-m, --module-path[=MODULE-PATH]`: Pfad der zu analysierenden Module
- `-a, --current-version[=CURRENT-VERSION]`: Aktuelle Adobe Commerce-Version, Version der Adobe Commerce-Installation wird verwendet, wenn sie weggelassen wird.
- `-c, --coming-version[=COMING-VERSION]`: Target Adobe Commerce-Version, wird die neueste veröffentlichte Version von Adobe Commerce verwendet, wenn sie weggelassen wird. Bietet eine Liste aller verfügbaren Adobe Commerce-Versionen.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Pfad der Datei, in die die Ausgabe im JSON-Format exportiert wird.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Pfad der Datei, in die die Ausgabe im HTML-Format exportiert wird.
- `--min-issue-level`: Minimale Problemstufe, die im Bericht angezeigt wird. Die Standardebene ist [WARNUNG].
- `-i, --ignore-current-version-compatibility-issues`: Verwenden Sie diese Option, wenn Sie bekannte kritische Probleme, Fehler und Warnungen nicht in Ihre [!DNL Upgrade Compatibility Tool] Bericht.
- `--context=CONTEXT`: Ausführungskontext. Diese Option dient Integrationszwecken und hat keine Auswirkungen auf das Ausführungsergebnis.
- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: Anwendungsversion anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

### Verwenden Sie die `--ignore-current-version-compatibility-issues` option

Die [!DNL Upgrade Compatibility Tool] ermöglicht Ihnen, die `upgrade:check` -Befehl mit einer `--ignore-current-version-compatibility-issues` angezeigt, sodass nur neue oder unbekannte kritische Probleme, Fehler und Warnungen angezeigt werden. Verwenden Sie diese Option, wenn Sie bekannte kritische Probleme, Fehler und Warnungen nicht in Ihre [!DNL Upgrade Compatibility Tool] Bericht.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Dies gilt nur für PHP-API-Überprüfungen.

### Vanilla-Installation

A _Vanille_ Bei der Installation handelt es sich um eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

Die `bin/uct core:code:changes` -Befehl prüft, ob sich in Ihrem System eine Vanilla-Instanz befindet. Wenn Sie zum ersten Mal eine Vanilla-Installation verwenden, werden Sie durch eine interaktive Befehlszeilenfrage aufgefordert, das Vanilla-Projekt aus dem Adobe Commerce-Repository herunterzuladen (`https://repo.magento.com/`).

Sie können eine [!DNL Upgrade Compatibility Tool] mit dem Befehl `--vanilla-dir` -Option, um den Installationsordner für Adobe Commerce Vanilla anzugeben.

Siehe [Vanilla-Instanz bereitstellen](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) für weitere Informationen.

## Verwenden Sie die `list` command

So geben Sie eine Liste der [!DNL Upgrade Compatibility Tool] verfügbare Befehle, ausführen:

```bash
bin/uct list
```

Die `list` gibt Folgendes zurück:

- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: App-Version anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

## Verwenden Sie die `core:code:changes` command

Sie können Ihre aktuelle Adobe Commerce-Installation mit einer sauberen Vanilla-Installation vergleichen, um festzustellen, ob im Kerncode Änderungen zur Implementierung einer neuen Funktion oder Anpassung vorgenommen wurden. Diese Validierung hilft bei der Schätzung des Aufwands, den das Upgrade basierend auf diesen Änderungen erfordert.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `<vanilla dir>`: Adobe Commerce-Vanilla-Installationsordner.

Beim Ausführen dieses Befehls gibt es einige Einschränkungen:

- Führen Sie die Ausführung nur aus, wenn der Ordner des Projektstamms (oder des Hauptordners) angegeben ist.
- Zeigt nur eine Liste der wichtigsten Änderungen an.

### Verwenden Sie die `core:code:changes` mit dem Befehl `--help` option

Verfügbar `--help` Optionen für `core:code:changes` command:

- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: App-Version anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

## Version

Sie können Ihre aktuelle Adobe Commerce-Installation mit Adobe Commerce-Versionen vergleichen `>=2.3`.

Sie müssen die Version als Parameter angeben, wenn Sie den Befehl ausführen:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

>[!NOTE]
>
>Dieser Parameter enthält eine Liste aller verfügbaren Adobe Commerce-Versionen.

Dabei gilt:

- `-c, --coming-version[=COMING-VERSION]`: Die Adobe Commerce-Zielversion.

Beim Ausführen des vorherigen Befehls gibt es einige Einschränkungen:

- Dieser Parameter bezieht sich auf alle Tags, die eine bestimmte Version von Adobe Commerce identifizieren.
- Es ist eine Pflicht, dies explizit anzugeben. Die Bereitstellung nur des Werts funktioniert nicht.
- Geben Sie die Tag-Version ohne Anführungszeichen an (weder Einzel- noch Doppelpunkt): ~~&quot;2.4.1-develop&quot;~~.
- Sie sollten KEINE älteren Versionen als die derzeit installierten bereitstellen und auch nicht ältere als 2.3, die derzeit die älteste Version ist, die unterstützt wird.

### Verwenden Sie die `refactor` command

Die [!DNL Upgrade Compatibility Tool] hat die Möglichkeit, einen reduzierten Satz von Problemen automatisch zu beheben:

- Funktionen, die verwendet werden dürfen, ohne ein -Argument zu übergeben, aber mit einer solchen Verwendung sind jetzt veraltet.
- Verwendung `$this` in Magento-Vorlagen.
- Verwendung des PHP-Suchbegriffs `final` in privaten Methoden.

Ausführen:

```bash
bin/uct refactor <dir>
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.

## Überprüfung der Kompatibilität mit GraphQL-Schemas

Die [!DNL Upgrade Compatibility Tool] bietet außerdem die Möglichkeit, zwei GraphQL-Endpunkte zu überprüfen und ihre Schemas zu vergleichen, um nach riskanten und gefährlichen Änderungen zwischen ihnen zu suchen:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Wenn die Argumente wie folgt lauten:

- `<schema1>`: Endpunkt-URL für die vorhandene Installation.
- `<schema2>`: Endpunkt-URL für die Vanilla-Installation.

Sie müssen `instance before` und `instance after` das Upgrade.

### GraphQL-Vergleich, Befehl `--help` options

Verfügbar `--help` Optionen für `graphql:compare` command:

- `-h, --help`: Zeigen Sie Hilfe für diesen spezifischen Befehl an. Wenn kein Befehl bereitgestellt wird, `list` -Befehl ist das Standardergebnis.
- `-q, --quiet`: Geben Sie beim Ausführen des Befehls keine Nachrichten aus.
- `-v, --version`: App-Version anzeigen.
- `--ansi, --no-ansi`: Aktivieren Sie die ANSI-Ausgabe.
- `-n, --no-interaction`: Stellen Sie beim Ausführen des Befehls keine interaktiven Fragen.
- `-v, --vv, --vvv, --verbose`: Erhöhen Sie die Ausführlichkeit der Ausgabekommunikation. 1 für die normale Ausgabe, 2 für die ausführliche Ausgabe und 3 für die DEBUG-Ausgabe.

### Beispiel mit einer Liste kritischer Probleme, Fehler und Warnungen für GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

## Fehlerbehebung

### Fehler bei Segmentierung

Wenn zwei Module denselben Namen haben, wird [!DNL Upgrade Compatibility Tool] zeigt einen Segmentierungsfehler an.

Um diesen Fehler zu vermeiden, wird empfohlen, die `bin` -Befehl mit der hinzugefügten Option `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>Die `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Die `-m` -Option ermöglicht die [!DNL Upgrade Compatibility Tool] , um jedes spezifische Modul unabhängig zu analysieren, um zu vermeiden, dass in Ihrer Adobe Commerce-Instanz zwei Module mit demselben Namen auftreten.

Diese Befehlsoption ermöglicht auch die [!DNL Upgrade Compatibility Tool] um einen Ordner zu analysieren, der mehrere Module enthält:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Diese Empfehlung hilft auch bei Speicherproblemen, die beim Ausführen der [!DNL Upgrade Compatibility Tool].

### Leere Ausgabe

>[!NOTE]
>
>Die `M2_VERSION` ist die Adobe Commerce-Zielversion, die Sie mit Ihrer Adobe Commerce-Instanz vergleichen möchten.

Wenn dieser Befehl nach der Ausführung ausgeführt wurde:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

Die einzige Ausgabe ist `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

Die wahrscheinliche Ursache ist eine PHP-Speicherbegrenzung.
Überschreiben Sie die Speicherbegrenzung durch Festlegen von `memory_limit` nach `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
