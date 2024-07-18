---
title: Führen Sie den  [!DNL Upgrade Compatibility Tool] aus.
description: Führen Sie diese Schritte aus, um den  [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle für Ihr Adobe Commerce-Projekt auszuführen.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# Laden Sie die [!DNL Upgrade Compatibility Tool] herunter.

{{commerce-only}}

Um mit dem [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle zu beginnen, laden Sie es herunter, indem Sie den folgenden Befehl ausführen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Möglicherweise müssen Sie dem ausführbaren Tool Berechtigungen mit dem Befehl `chmod` erteilen:

```bash
chmod +x ./uct/bin/uct
```

## Die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle

Der [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

Weitere Informationen zum [!DNL Upgrade Compatibility Tool] finden Sie in diesem [Video-Tutorial](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) .

Verfügbare Befehle für die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle:

| **Befehl** | **Beschreibung** |
|----------------|-----------------|
| `upgrade:check` | Dieser Befehl führt den [!DNL Upgrade Compatibility Tool] aus, indem alle darin installierten Module analysiert werden. |
| `dbschema:diff` | Dieser Befehl zeigt alle Unterschiede zwischen zwei angegebenen Adobe Commerce-Versionen des Datenbankschemas an. |
| `core:code:changes` | Dieser Befehl vergleicht Ihre aktuelle Adobe Commerce-Installation mit einer sauberen Vanilla-Installation. |
| `refactor` | Dieser Befehl behebt automatisch eine reduzierte Anzahl von Problemen. |
| `graphql:compare` | Dieser Befehl bietet die Möglichkeit, zwei GraphQL-Endpunkte zu untersuchen und ihre Schemas zu vergleichen. |
| `list` | Dieser Befehl gibt eine Liste aller verfügbaren [!DNL Upgrade Compatibility Tool] Befehle zurück. |
| `help` | Dieser Befehl gibt alle verfügbaren `help`Optionen für den [!DNL Upgrade Compatibility Tool] zurück. Dieser Befehl kann ebenso ausgeführt werden wie eine Option mit den vorherigen Befehlen. |

## Verwenden Sie den Befehl `upgrade:check` .

Der Befehl `upgrade:check` prüft, ob Kerncodeänderungen für diese bestimmte Adobe Commerce-Instanz und alle darin installierten Änderungen an benutzerdefiniertem Code vorgenommen wurden.

Der Befehl `upgrade:check` ist der Hauptbefehl zum Ausführen des Tools:

```bash
bin/uct upgrade:check <dir>
```

Dabei ist der Wert `<dir>` der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Verfügbare Optionen für den Befehl `upgrade:check` :

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Gibt alle verfügbaren Optionen zurück.</li><li>—current-version: Aktuelle Adobe Commerce-Version. Dieser Parameter ist erforderlich und muss immer verwendet werden.</li><li>—min-issue-level: Sie können Probleme nach der minimalen Problemstufe filtern (Standardwert ist WARNING).</li><li>—ignore-current-version-compatibility-issues (oder -i): Wenn Sie keine kritischen Probleme, Fehler und Warnungen aus der aktuellen Version in Ihren Bericht aufnehmen möchten.</li><li>—Bevorstehende Version (oder -c): Targeting einer bestimmten Adobe Commerce-Version. Die jeweils aktuellste Version wird verwendet, wenn sie weggelassen wird.</li></ul> |

Mit dem [!DNL Upgrade Compatibility Tool] können Sie den Befehl `upgrade:check` mit der Option `--ignore-current-version-compatibility-issues` ausführen. Verwenden Sie diese Option, wenn Sie nur neue Probleme erhalten möchten, die mit der Aktualisierung von Ihrer aktuellen Version auf die gewünschte Version in Ihrem [!DNL Upgrade Compatibility Tool] -Bericht eingeführt werden:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Dies gilt nur für PHP-API-Überprüfungen.

### Hinzufügen der `--coming-version`-Option

Sie können Ihre aktuelle Adobe Commerce-Installation mit einer beliebigen Adobe Commerce-Version `>=2.3` vergleichen, indem Sie die Option `--coming-version` verwenden.

Sie müssen die Version als Parameter angeben, wenn Sie den Befehl `upgrade:check` ausführen:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Dabei bezieht sich `-c, --coming-version[=COMING-VERSION]` auf die Targeting-Version von Adobe Commerce.

Beim Ausführen von `--coming-version` gibt es einige Einschränkungen:

- Dieser Parameter bezieht sich auf alle Tags, die eine bestimmte Version von Adobe Commerce identifizieren.
- Es ist eine Anforderung, diese explizit anzugeben; nur der Wert davon funktioniert nicht.
- Stellen Sie die Tag-Version ohne Anführungszeichen bereit (weder Einzel- noch Doppelpunkt): ~~&#39;2.4.1-develop&#39;~~.
- Sie sollten KEINE älteren Versionen als die derzeit installierten bereitstellen und auch nicht ältere als 2.3, die derzeit die älteste Version ist, die unterstützt wird.

## Verwenden Sie den Befehl `dbschema:diff` .

Sie können den Unterschied zwischen dem Datenbankschema von zwei Adobe Commerce-Versionen abrufen.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Wenn die Argumente wie folgt lauten:

- `<current-version>`: eine beliebige Adobe Commerce-Version zum Vergleich.
- `<target-version>`: auch eine beliebige Adobe Commerce-Version zum Vergleich.

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

## Verwenden Sie den Befehl `core:code:changes` .

Sie können Ihre aktuelle Adobe Commerce-Installation mit der Überprüfung vergleichen, ob der Kerncode von Adobe Commerce zur Implementierung einer Anpassung geändert wurde. Dieser Befehl zeigt nur eine Liste der wichtigsten Änderungen:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Wenn die Argumente wie folgt lauten:

- `<dir>`: Installationsordner von Adobe Commerce.
- `<vanilla dir>`: Adobe Commerce-Vanilla-Installationsordner.

Verfügbare Optionen für den Befehl `core:code:changes` :

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Gibt alle verfügbaren `--help` -Optionen zurück. |

>[!NOTE]
>
> Es empfiehlt sich, benutzerdefinierten Code aus dem Kerncode herauszuhalten. Weitere Best Practices für die Aktualisierung finden Sie im Adobe Commerce 2.4 [Upgrade-Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) .

### Vanilla-Installation

Bei einer Installation von _Vanilla_ handelt es sich um eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

Der Befehl `bin/uct core:code:changes` prüft, ob sich in Ihrem System eine Vanilla-Instanz befindet. Wenn Sie zum ersten Mal eine Vanilla-Installation verwenden, werden Sie bei einer interaktiven Befehlszeilenfrage aufgefordert, das Vanilla-Projekt aus dem Adobe Commerce-Repository (`https://repo.magento.com/`) herunterzuladen.

Sie können den Befehl [!DNL Upgrade Compatibility Tool] mit der Option `--vanilla-dir` ausführen, um den Installationsordner für Adobe Commerce Vanilla anzugeben.

Weitere Informationen finden Sie im Thema [Vanilla-Instanz bereitstellen](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) .

## Verwenden Sie den Befehl `refactor` .

Der [!DNL Upgrade Compatibility Tool] kann eine reduzierte Anzahl von Problemen automatisch beheben:

- Funktionen, die verwendet werden dürfen, ohne ein -Argument zu übergeben, aber mit einer solchen Verwendung sind jetzt veraltet.
- Verwendung von `$this` in Magento-Vorlagen.
- Verwendung des PHP-Suchbegriffs `final` in privaten Methoden.

Führen Sie dazu den Befehl `refactor` aus:

```bash
bin/uct refactor <dir>
```

Dabei ist der Wert `<dir>` der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Verfügbare Optionen für den Befehl `refactor` :

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `refactor` | `--help`: Gibt alle verfügbaren `--help` -Optionen zurück. |

## Verwenden Sie den Befehl `graphql:compare` .

Dieser Befehl bietet die Möglichkeit für die [!DNL Upgrade Compatibility Tool], zwei GraphQL-Endpunkte zu überprüfen und ihre Schemas zu vergleichen, um nach riskanten und gefährlichen Änderungen zwischen ihnen zu suchen:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Wenn die Argumente wie folgt lauten:

- `<schema1>`: Endpunkt-URL für die vorhandene Installation.
- `<schema2>`: Endpunkt-URL für die Vanilla-Installation.

Verfügbare Optionen für den Befehl `graphql:compare` :

| **Befehl** | **Verfügbare Optionen** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Gibt alle verfügbaren `--help` -Optionen zurück. |

## Verwenden Sie den Befehl `list` .

Um eine Liste der verfügbaren [!DNL Upgrade Compatibility Tool] -Befehle zurückzugeben, führen Sie Folgendes aus:

```bash
bin/uct list
```

## Verwenden Sie den Befehl `help` .

Um den Befehl [!DNL Upgrade Compatibility Tool] mit allgemeinen Optionen und Hilfe anzuzeigen, führen Sie Folgendes aus:

```bash
bin/uct --help
```

Dadurch wird eine Liste mit allen verfügbaren `help` -Optionen für die [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle zurückgegeben:

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

Es ist möglich, `--help` als Option auszuführen, wenn ein bestimmter Befehl ausgeführt wird. Es werden `--help` -Optionen für den angegebenen Befehl zurückgegeben.

Beispiel des Befehls `upgrade:check` mit der Option `--help`:

```bash
bin/uct upgrade:check --help
```

Dadurch werden bestimmte Optionen zurückgegeben, die für den Befehl `upgrade:check` ausgeführt werden können:

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

## Befolgen Sie die Best Practices für Adobe Commerce

- Vermeiden Sie es, zwei Module mit demselben Namen zu haben.
- Befolgen Sie die Adobe Commerce [Kodierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/).
- Best Practices für Adobe Commerce 2.4 [Aktualisierungshandbuch](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf).
- Führen Sie die [!DNL Upgrade Compatibility Tool] aus dem [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) für [Adobe Commerce in Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} -Projekte aus.

## Ergebnisse optimieren

Der [!DNL Upgrade Compatibility Tool] stellt einen Bericht mit Ergebnissen bereit, in dem alle in Ihrem Projekt standardmäßig identifizierten Probleme aufgeführt sind. Sie können die Ergebnisse optimieren, um sich auf die Probleme zu konzentrieren, die Sie beheben müssen, um das Upgrade abzuschließen:

- Verwenden Sie die Option `--ignore-current-version-compatibility-issues` , wenn Sie nur neue Probleme erhalten möchten, die mit der Aktualisierung von Ihrer aktuellen Version auf die gewünschte Version in Ihrem [!DNL Upgrade Compatibility Tool] -Bericht eingeführt werden.
- Wenn Sie die Option `--min-issue-level` hinzufügen, können Sie mit dieser Einstellung das minimale Problemniveau festlegen, damit nur die wichtigsten Probleme bei Ihrem Upgrade priorisiert werden.
- Die [!DNL Upgrade Compatibility Tool] benötigt mindestens 2 GB RAM, um ausgeführt zu werden. Diese Einstellung wird empfohlen, um Probleme aufgrund einer geringen Speicherbegrenzung zu vermeiden. Der [!DNL Upgrade Compatibility Tool] zeigt eine Frage an, wenn Sie den `upgrade:check` -Befehl mit einer niedrigen `memory_limit` -Einstellung ausführen.
