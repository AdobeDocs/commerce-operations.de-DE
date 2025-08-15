---
title: Ausführen des  [!DNL Upgrade Compatibility Tool]
description: Führen Sie diese Schritte aus, um  [!DNL Upgrade Compatibility Tool]  in einer Befehlszeilenschnittstelle für Ihr Adobe Commerce-Projekt auszuführen.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: bfb952d29bd3d7fc7147107216981e05202e44aa
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# [!DNL Upgrade Compatibility Tool] herunterladen

{{commerce-only}}

Um mit der [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle zu beginnen, laden Sie sie herunter, indem Sie den folgenden Befehl ausführen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Möglicherweise müssen Sie dem Tool über den `chmod` Befehl ausführbare Berechtigungen erteilen:

```bash
chmod +x ./uct/bin/uct
```

## Die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle

Der [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz mit einer bestimmten Version vergleicht, indem alle darin installierten Module analysiert werden. Sie gibt eine Liste mit kritischen Problemen, Fehlern und Warnungen zurück, die vor dem Upgrade auf die neueste Version von Adobe Commerce behoben werden müssen.

In diesem [Video-Tutorial](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=de) (06:02) erfahren Sie mehr über die [!DNL Upgrade Compatibility Tool].

Verfügbare Befehle für die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle:

| **Befehl** | **Beschreibung** |
|----------------|-----------------|
| `upgrade:check` | Dieser Befehl führt den [!DNL Upgrade Compatibility Tool] aus, indem alle darin installierten Module analysiert werden. |
| `dbschema:diff` | Dieser Befehl zeigt alle Unterschiede des Datenbankschemas zwischen zwei angegebenen Adobe Commerce-Versionen an. |
| `core:code:changes` | Dieser Befehl vergleicht Ihre aktuelle Adobe Commerce-Installation mit einer reinen Vanilla-Installation. |
| `refactor` | Dieser Befehl behebt automatisch eine reduzierte Anzahl von Problemen. |
| `graphql:compare` | Dieser Befehl bietet die Möglichkeit, zwei GraphQL-Endpunkte zu untersuchen und ihre Schemata zu vergleichen. |
| `list` | Dieser Befehl gibt eine Liste aller [!DNL Upgrade Compatibility Tool] verfügbaren Befehle zurück. |
| `help` | Dieser Befehl gibt alle verfügbaren `help`Optionen für die [!DNL Upgrade Compatibility Tool] zurück. Dieser Befehl kann zusammen mit den vorherigen Befehlen ausgeführt werden. |

## Verwenden des Befehls `upgrade:check`

Der Befehl `upgrade:check` prüft, ob Änderungen am Kern-Code für diese spezifische Adobe Commerce-Instanz und alle darin installierten Änderungen am benutzerdefinierten Code vorhanden sind.

Der `upgrade:check` ist der Hauptbefehl zum Ausführen des Tools:

```bash
bin/uct upgrade:check <dir>
```

Dabei ist `<dir>` Wert der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Verfügbare Optionen für den `upgrade:check`:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Gibt alle verfügbaren Optionen zurück.</li><li>—current-version: Aktuelle Adobe Commerce-Version. Die Version der Adobe Commerce-Installation wird verwendet, wenn sie weggelassen wird.</li><li>—min-issue-level: Sie können Probleme nach der minimalen Anfrageebene filtern (der Standardwert ist „WARNUNG„).</li><li>—ignore-current-version-compatibility-issues (oder -i): Wenn Sie keine kritischen Probleme, Fehler und Warnungen aus der aktuellen Version in Ihren Bericht aufnehmen möchten.</li><li>—coming-version (oder -c): Wählen Sie eine bestimmte Adobe Commerce-Version aus. Die neueste verfügbare Version wird verwendet, wenn sie weggelassen wird.</li></ul> |

Mit der [!DNL Upgrade Compatibility Tool] können Sie den `upgrade:check`-Befehl mit einer `--ignore-current-version-compatibility-issues` Option ausführen. Verwenden Sie diese Option, wenn Sie nur neue Probleme erhalten möchten, die mit dem Update von Ihrer aktuellen Version auf die Zielversion in Ihrem [!DNL Upgrade Compatibility Tool] Bericht eingeführt werden:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Dies gilt nur für PHP-API-Validierungen.

### Hinzufügen der `--coming-version`

Sie können Ihre aktuelle Adobe Commerce-Installation mit einer beliebigen Adobe Commerce-Version `>=2.3` vergleichen, indem Sie die Option `--coming-version` verwenden.

Sie müssen die Version als Parameter angeben, wenn Sie den `upgrade:check` Befehl ausführen:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Hier verweist `-c, --coming-version[=COMING-VERSION]` auf die Zielversion von Adobe Commerce.

Beim Ausführen der `--coming-version` gibt es einige Einschränkungen:

- Dieser Parameter bezieht sich auf jedes Tag, das eine bestimmte Version von Adobe Commerce identifiziert.
- Es ist erforderlich, dies explizit bereitzustellen. Nur den Wert bereitzustellen, funktioniert nicht.
- Stellen Sie die Tag-Version ohne Anführungszeichen bereit (weder einzeln noch doppelt): ~~&#39;2.4.1-develop&#39;~~.
- Sie sollten KEINE älteren Versionen als die derzeit installierte oder ältere Version als 2.3 bereitstellen, die die älteste derzeit unterstützte Version ist.

## Verwenden des Befehls `dbschema:diff`

Sie können die Differenz zwischen dem Datenbankschema zweier Adobe Commerce-Versionen abrufen.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Dabei gelten folgende Argumente:

- `<current-version>`: Beliebige Adobe Commerce-Version zum Vergleich.
- `<target-version>`: Auch alle Adobe Commerce-Versionen zum Vergleich.

Anwendungsbeispiel:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## Verwenden des Befehls `core:code:changes`

Sie können Ihre aktuelle Adobe Commerce-Installation vergleichen, um zu überprüfen, ob der Kern-Code von Adobe Commerce geändert wurde, um eine Anpassung zu implementieren. Dieser Befehl zeigt nur eine Liste der grundlegenden Änderungen an:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Dabei gelten folgende Argumente:

- `<dir>`: Adobe Commerce-Installationsverzeichnis.
- `<vanilla dir>`: Adobe Commerce Vanilla-Installationsverzeichnis.

Verfügbare Optionen für den `core:code:changes`:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Gibt alle verfügbaren `--help` zurück. |

>[!NOTE]
>
> Es empfiehlt sich, benutzerdefinierten Code nicht in den Kern-Code aufzunehmen. Weitere Best Practices für Upgrades finden Sie [ Adobe Commerce 2.4 ](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=de) Upgrade-Handbuch .

### Vanilla-Installation

Eine _Vanilla_-Installation ist eine saubere Installation eines angegebenen Versions-Tags oder -Zweigs für eine bestimmte Release-Version.

Der Befehl `bin/uct core:code:changes` prüft, ob in Ihrem System eine Vanilla-Instanz vorhanden ist. Wenn Sie zum ersten Mal eine Vanilla-Installation verwenden, werden Sie durch eine interaktive Befehlszeilenfrage aufgefordert, das Vanilla-Projekt aus dem Adobe Commerce-Repository (`https://repo.magento.com/`) herunterzuladen.

Sie können einen [!DNL Upgrade Compatibility Tool]-Befehl mit der Option `--vanilla-dir` ausführen, um das Adobe Commerce Vanilla-Installationsverzeichnis anzugeben.

Weitere Informationen finden Sie [ Thema „Bereitstellen ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) Vanilla-Instanz“ .

## Verwenden des Befehls `refactor`

Der [!DNL Upgrade Compatibility Tool] hat die Möglichkeit, eine reduzierte Anzahl von Problemen automatisch zu beheben:

- Funktionen, die ohne Übergabe eines -Arguments verwendet werden durften, aber mit einer solchen Verwendung jetzt nicht mehr unterstützt werden.
- Verwendung von `$this` in Magento-Vorlagen.
- Verwendung von PHP-`final` in privaten Methoden.

Führen Sie dazu den `refactor` Befehl aus:

```bash
bin/uct refactor <dir>
```

Dabei ist `<dir>` Wert der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Verfügbare Optionen für den `refactor`:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `refactor` | `--help`: Gibt alle verfügbaren `--help` zurück. |

## Verwenden des Befehls `graphql:compare`

Dieser Befehl bietet dem [!DNL Upgrade Compatibility Tool] die Möglichkeit, zwei GraphQL-Endpunkte zu prüfen und ihre Schemas zu vergleichen, um nach laufenden und gefährlichen Änderungen zwischen ihnen zu suchen:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Dabei gelten folgende Argumente:

- `<schema1>`: Endpunkt-URL für die bestehende Installation.
- `<schema2>`: Endpunkt-URL für die Vanilla-Installation.

Verfügbare Optionen für den `graphql:compare`:

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Gibt alle verfügbaren `--help` zurück. |

## Verwenden des Befehls `list`

Um eine Liste der [!DNL Upgrade Compatibility Tool] verfügbaren Befehle zurückzugeben, führen Sie Folgendes aus:

```bash
bin/uct list
```

## Verwenden des Befehls `help`

Um die allgemeinen Optionen und die Hilfe des [!DNL Upgrade Compatibility Tool]-Befehls anzuzeigen, führen Sie Folgendes aus:

```bash
bin/uct --help
```

Dadurch wird eine Liste mit allen verfügbaren `help` für die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle zurückgegeben:

```
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

Es ist möglich, `--help` als Option auszuführen, wenn ein bestimmter Befehl ausgeführt wird. Gibt `--help` Optionen für den angegebenen Befehl zurück.

Beispiel für den `upgrade:check`-Befehl mit `--help` Option:

```bash
bin/uct upgrade:check --help
```

Dadurch werden spezifische Optionen zurückgegeben, die für den `upgrade:check`-Befehl ausgeführt werden können:

```
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Befolgen der Best Practices für Adobe Commerce

- Vermeiden Sie zwei Module mit demselben Namen.
- Befolgen Sie die [-](https://developer.adobe.com/commerce/php/coding-standards/) von Adobe Commerce.
- Adobe Commerce 2.4 [Upgrade-Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=de) Best Practices.
- Führen Sie die [!DNL Upgrade Compatibility Tool] über die [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=de) für [Adobe Commerce in Cloud-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=de){target=_blank} aus.

## Optimieren der Ergebnisse

Der [!DNL Upgrade Compatibility Tool] bietet einen Bericht mit Ergebnissen zu allen Problemen, die standardmäßig in Ihrem Projekt identifiziert wurden. Sie können die Ergebnisse optimieren, um sich auf die Probleme zu konzentrieren, die Sie beheben müssen, um das Upgrade abzuschließen:

- Verwenden Sie die Option `--ignore-current-version-compatibility-issues`, wenn Sie in Ihrem [!DNL Upgrade Compatibility Tool] Bericht nur neue Probleme erhalten möchten, die mit dem Update von Ihrer aktuellen Version auf die Zielversion eingeführt werden.
- Durch Hinzufügen der Option &quot;`--min-issue-level`&quot; können Sie mit dieser Einstellung die minimale Problemstufe festlegen, damit nur die wichtigsten Probleme bei Ihrem Upgrade priorisiert werden.
- Die [!DNL Upgrade Compatibility Tool] benötigt mindestens 2 GB RAM. Diese Einstellung wird empfohlen, um Probleme aufgrund einer niedrigen Speicherbegrenzung zu vermeiden. Der [!DNL Upgrade Compatibility Tool] zeigt eine Frage an, wenn Sie den `upgrade:check` Befehl mit einer Einstellung für niedrige `memory_limit` ausführen.
