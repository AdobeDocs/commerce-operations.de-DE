---
source-git-commit: e50883135e13621f9668914a260bd5a2bf48641d
workflow-type: tm+mt
source-wordcount: '8232'
ht-degree: 1%

---
# bin/Magento (Adobe Commerce On-Premise)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Version**: 2.4.8

Diese Referenz enthält 145 Befehle, die über das `bin/magento` Befehlszeilen-Tool verfügbar sind.
Die anfängliche Liste wird automatisch mit dem `bin/magento list`-Befehl in Adobe Commerce generiert.

## Allgemein

Verwenden Sie das [&#x200B; „CLI-Befehle hinzufügen](https://developer.adobe.com/commerce/php/development/cli-commands/) um einen benutzerdefinierten CLI-Befehl hinzuzufügen.

Sie können `bin/magento` CLI-Befehle über Tastaturbefehle anstelle des vollständigen Befehlsnamens aufrufen. Beispielsweise können Sie `bin/magento setup:upgrade` mithilfe von `bin/magento s:up` aufrufen, `bin/magento s:upg`. Unter [Verknüpfungssyntax](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) erfahren Sie, wie Sie Verknüpfungen mit beliebigen CLI-Befehlen verwenden.

Diese Referenzdokumentation wird aus dem Programm-Quell-Code generiert. Um die Dokumentation zu ändern, sollten Sie Folgendes öffnen
eine Pull-Anfrage für den entsprechenden Befehl im entsprechenden [Codebase](https://github.com/magento)-Repository. Siehe
[Code-Beiträge](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) für weitere Informationen.

### Globale Optionen

#### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für den Listenbefehl angezeigt

- Standard: `false`
- Akzeptiert keinen Wert

#### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

#### `--no-ansi`

Negieren Sie die Option &quot;—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Interner Befehl zur Bereitstellung von Shell-Fertigstellungsvorschlägen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--shell`, `-s`

Der Schalentyp („bash“, „fish“, „zsh„)

- Erfordert einen Wert

#### `--input`, `-i`

Ein Array von Eingabe-Token (z. B. COMP_WORDS oder argv)

- Standard: `[]`
- Erfordert einen Wert

#### `--current`, `-c`

Der Index des „Eingabe“-Arrays, in dem sich der Cursor befindet (z. B. COMP_CWORD)

- Erfordert einen Wert

#### `--api-version`, `-a`

Die API-Version des Abschlussskripts

- Erfordert einen Wert

#### `--symfony`, `-S`

Veraltet

- Erfordert einen Wert


## `completion`

```bash
bin/magento completion [--debug] [--] [<shell>]
```

Dump des Shell-Fertigstellungsskripts

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
```

### Argumente

#### `shell`

Der Shell-Typ (z. B. „bash„), der Wert der &quot;$SHELL“-Env-Var wird verwendet, wenn diese nicht angegeben wird

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--debug`

Verfolgen Sie den Abschluss des Debug-Protokolls

- Standard: `false`
- Akzeptiert keinen Wert


## `help`

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Anzeigen der Hilfe für einen Befehl

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumente

#### `command_name`

Der Befehlsname

- Standard: `help`

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

#### `--raw`

So geben Sie die Raw-Befehlshilfe aus

- Standard: `false`
- Akzeptiert keinen Wert


## `list`

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Befehle auflisten

```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
```

### Argumente

#### `namespace`

Der Namespace-Name

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--raw`

Ausgabe der unbearbeiteten Befehlsliste

- Standard: `false`
- Akzeptiert keinen Wert

#### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

#### `--short`

So überspringen Sie die Beschreibung der Befehlsargumente

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Adobe IMS-Modul deaktivieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Aktivieren des Adobe IMS-Moduls.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--organization-id`, `-o`

Festlegen der Organisations-ID für die Adobe IMS-Konfiguration. Erforderlich, wenn das Modul aktiviert wird

- Akzeptiert einen Wert

#### `--client-id`, `-c`

Legen Sie die Client-ID für die Adobe IMS-Konfiguration fest. Erforderlich, wenn das Modul aktiviert wird

- Akzeptiert einen Wert

#### `--client-secret`, `-s`

Legen Sie das Client-Geheimnis für die Adobe IMS-Konfiguration fest. Erforderlich, wenn das Modul aktiviert wird

- Akzeptiert einen Wert

#### `--2fa`, `-t`

Überprüfen Sie, ob 2FA für die Organisation in Adobe Admin Console aktiviert ist. Erforderlich, wenn das Modul aktiviert wird

- Akzeptiert einen Wert


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Informationen zur Adobe IMS-Modulkonfiguration

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Status des Adobe IMS-Moduls

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Erstellt einen Administrator

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--admin-user`

(Erforderlich) Admin-Benutzer

- Erfordert einen Wert

#### `--admin-password`

(Erforderlich) Administratorkennwort

- Erfordert einen Wert

#### `--admin-email`

(Erforderlich) Admin-E-Mail

- Erfordert einen Wert

#### `--admin-firstname`

(Erforderlich) Vorname des Administrators

- Erfordert einen Wert

#### `--admin-lastname`

(Erforderlich) Nachname des Administrators

- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Admin-Konto entsperren

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### Argumente

#### `username`

Der zu entsperrende Admin-Benutzername

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Erstellen eines Dump der Anwendung

### Argumente

#### `config-types`

Durch Leerzeichen getrennte Liste von Konfigurationstypen oder Weglassen, um alle Bereiche ([, Themen, System, i18n) ]

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Daten aus freigegebenen Konfigurationsdateien in den entsprechenden Datenspeicher importieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `app:config:status`

```bash
bin/magento app:config:status
```

Prüft, ob die Konfigurationsweitergabe eine Aktualisierung erfordert

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migrieren von gespeicherten Karten aus einer Magento 1-Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

Hostname/IP Port ist optional

- Erfordert einen Wert

#### `--dbname`

Datenbankname

- Erfordert einen Wert

#### `--username`

Benutzername der Datenbank. Muss Lesezugriff haben

- Erfordert einen Wert

#### `--password`

Kennwort

- Erfordert einen Wert


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Löscht den/die Cache-Typ(en)

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap

- Erfordert einen Wert


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Cache für Merchant Scopes in Payment Services bereinigen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Deaktiviert Cache-Typ(en)

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap

- Erfordert einen Wert


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Aktiviert Cache-Typ(en)

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap

- Erfordert einen Wert


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Leert den von Cache-Typ(en) verwendeten Cache-Speicher

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap

- Erfordert einen Wert


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Überprüft den Cache-Status

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap

- Erfordert einen Wert


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Erstellt skalierte Produktbilder.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--async`, `-a`

Ändern der Bildgröße im asynchronen Modus

- Standard: `false`
- Akzeptiert keinen Wert

#### `--skip_hidden_images`

Keine Bilder verarbeiten, die auf der Produktseite als ausgeblendet markiert sind

- Standard: `false`
- Akzeptiert keinen Wert


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Entfernt nicht verwendete Produktattribute.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Festlegen, ob die Inhaltsvalidierung von HTML erzwungen oder stattdessen eine Warnung angezeigt werden soll

### Argumente

#### `restrict`

J\n

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Festlegen sensibler Konfigurationswerte

### Argumente

#### `path`

Konfigurationspfad, z. B. group/section/field_name


#### `value`

Konfigurationswert

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--interactive`, `-i`

Aktivieren des interaktiven Modus zum Festlegen aller sensiblen Variablen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--scope`

Konfigurationsbereich, falls nicht festgelegt, „Standard“ verwenden

- Standard: `default`
- Akzeptiert einen Wert

#### `--scope-code`

Code-Bereich für Konfiguration, Leer-String standardmäßig

- Standard: &quot;
- Akzeptiert einen Wert


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Systemkonfiguration ändern

### Argumente

#### `path`

Konfigurationspfad im Formatabschnitt/group/field_name

- Erforderlich


#### `value`

Konfigurationswert

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--scope`

Konfigurationsumfang (Standard, Website oder Store)

- Standard: `default`
- Erfordert einen Wert

#### `--scope-code`

Umfangscode (nur erforderlich, wenn der Umfang nicht „Standard“ ist)

- Erfordert einen Wert

#### `--lock-env`, `-e`

Sperrwert, der Änderungen in der Admin verhindert (wird in app/etc/env.php gespeichert)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--lock-config`, `-c`

Wert sperren und für andere Installationen freigeben, Änderungen in der Admin verhindern (wird in app/etc/config.php gespeichert)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--lock`, `-l`

Veraltet, verwenden Sie stattdessen die Option —lock-env .

- Standard: `false`
- Akzeptiert keinen Wert


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Zeigt den Konfigurationswert für den angegebenen Pfad an. Wenn kein Pfad angegeben ist, werden alle gespeicherten Werte angezeigt

### Argumente

#### `path`

Konfigurationspfad, z. B. section_id/group_id/field_id

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--scope`

Konfigurationsbereich: Wenn kein Bereich angegeben ist, wird der Standardbereich verwendet.

- Standard: `default`
- Akzeptiert einen Wert

#### `--scope-code`

Umfangscode (nur erforderlich, wenn der Umfang nicht `default` ist)

- Standard: &quot;
- Akzeptiert einen Wert


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Erzeugt und installiert crontab für den aktuellen Benutzer

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Installationsaufgaben erzwingen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--non-optional`, `-d`

Nur die nicht optionalen (Standard-)Aufgaben installieren

- Standard: `false`
- Akzeptiert keinen Wert


## `cron:remove`

```bash
bin/magento cron:remove
```

Entfernt Aufgaben aus der crontab

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Führt Aufträge nach Zeitplan aus

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--group`

Nur Aufträge aus einer angegebenen Gruppe ausführen

- Erfordert einen Wert

#### `--exclude-group`

Ausschließen von Aufträgen aus der angegebenen Gruppe

- Standard: `[]`
- Akzeptiert mehrere Werte

#### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Aktualisieren des Hash-Werts des Kunden gemäß dem neuesten Algorithmus

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Festlegen des Anwendungsmodus.

### Argumente

#### `mode`

Der einzustellende Anwendungsmodus. Verfügbare Optionen sind „Entwickler“ oder „Produktion“

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--skip-compilation`, `-s`

Überspringt das Löschen und erneute Generieren von statischem Inhalt (generierter Code, vorverarbeitetes CSS und Assets in pub/static/)

- Standard: `false`
- Akzeptiert keinen Wert


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Zeigt den aktuellen Anwendungsmodus an.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

Enthält Informationen zur Konfiguration der Injektion von Abhängigkeiten für den Befehl .

### Argumente

#### `class`

Klassenname

- Erforderlich


#### `area`

Ortsvorwahl

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Durchsucht Newsletter-Vorlagen nach potenziellen Problemen mit der Variablennutzungskompatibilität

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Überschreibungen von E-Mail-Vorlagen auf mögliche Kompatibilitätsprobleme bei der Variablennutzung überprüfen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Deaktivieren Sie den Profiler.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Aktivieren Sie den Profiler.

### Argumente

#### `type`

Profiltyp

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

DB-Abfrageprotokollierung deaktivieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

DB-Abfrageprotokollierung aktivieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--include-all-queries`

Alle Abfragen protokollieren. [true\|false]

- Standard: `true`
- Akzeptiert einen Wert

#### `--query-time-threshold`

Schwellenwerte für die Abfragezeit.

- Standard: `0.001`
- Akzeptiert einen Wert

#### `--include-call-stack`

Aufrufliste einschließen. [true\|false]

- Standard: `true`
- Akzeptiert einen Wert


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Sammelt Quelldateien für Designs und veröffentlicht diese.

### Argumente

#### `file`

Dateien zur Vorab-Bearbeitung (Datei sollte ohne Erweiterung angegeben werden)

- Standard: `css/styles-mcss/styles-l`

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--type`

Typ der Quelldateien: [less]

- Standard: `less`
- Erfordert einen Wert

#### `--locale`

Gebietsschema: [en_US]

- Standard: `en_US`
- Erfordert einen Wert

#### `--area`

Bereich: [frontend\|adminhtml]

- Standard: `frontend`
- Erfordert einen Wert

#### `--theme`

Design: [Anbieter/Design]

- Standard: `Magento/luma`
- Erfordert einen Wert


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Deaktiviert Hinweise zu Frontend-Vorlagen. Möglicherweise ist eine Cache-Leerung erforderlich.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Aktivieren Sie Hinweise zu Frontend-Vorlagen. Möglicherweise ist eine Cache-Leerung erforderlich.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Status der Hinweise zu Frontend-Vorlagen anzeigen.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Führt Tests durch

### Argumente

#### `type`

Typ des auszuführenden Tests. Verfügbare Typen: all, unit, integration, integration-all, static, static-all, integrity, legacy, default

- Standard: `default`

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--arguments`, `-c`

Zusätzliche Argumente für PHPUnit. Beispiel: &quot;-c&#39;—filter=MyTest&#39;&quot; (keine Leerzeichen)

- Standard: &quot;
- Erfordert einen Wert


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Generiert den Katalog der URNs zu *.xsd-Zuordnungen für die IDE zum Hervorheben von XML.

### Argumente

#### `path`

Pfad zur auszugebenden Datei des Katalogs Verwenden Sie für PhpStorm .idea/misc.xml

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--ide`

Format, in dem der Katalog generiert wird. Unterstützt: [phpstorm, vscode]

- Standard: `phpstorm`
- Erfordert einen Wert


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Konvertiert eine XML-Datei mithilfe von XSL-Stylesheets

### Argumente

#### `xml-file`

Pfad zur zu transformierenden XML-Datei

- Erforderlich


#### `processor`

Pfad zum XSL-Stylesheet, das auf die XML-Datei angewendet werden soll

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--overwrite`, `-o`

XML-Datei überschreiben

- Standard: `false`
- Akzeptiert keinen Wert


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Hinzufügen von Domains zur Whitelist für herunterladbare Domains

### Argumente

#### `domains`

Domain-Name

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Entfernen von Domains aus der Whitelist für herunterladbare Domains

### Argumente

#### `domains`

Domain-Namen

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Whitelist für herunterladbare Domains anzeigen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

Zeigt eine Liste der verfügbaren Datenwiederverschlüsseler an.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

Verschlüsselt verschlüsselte Daten mit dem aktuellen Verschlüsselungsschlüssel erneut.

### Argumente

#### `encryptors`

Durch Leerzeichen getrennte Liste der zu verwendenden Verschlüsselungsmethoden.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

Ändern Sie den Verschlüsselungsschlüssel in der Datei env.php.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--key`, `-k`

Der Schlüssel muss eine 32 Zeichen lange Zeichenfolge sein. Wenn kein zufälliger Schlüssel angegeben wird, wird er generiert.

- Akzeptiert einen Wert


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Verschlüsselt verschlüsselte Kreditkartendaten erneut mit der neuesten Verschlüsselungschiffre.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Erstellen Sie für diese Instanz einen benutzerdefinierten Ereignisanbieter in Adobe I/O Events. Wenn Sie die Beschriftungs- und Beschreibungsoptionen nicht angeben, müssen diese in der Datei &quot;app/etc/event-types.json&quot; des Systems definiert werden.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--label`

Eine Bezeichnung zum Definieren des benutzerdefinierten Anbieters.

- Akzeptiert einen Wert

#### `--description`

Eine Beschreibung Ihres Anbieters.

- Akzeptiert einen Wert


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Modul basierend auf der Plug-in-Liste erzeugen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Gibt die Payload des angegebenen Ereignisses zurück.

### Argumente

#### `event-code`

Ereigniscode

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--depth`

Die Anzahl der Ebenen in der Ereignis-Payload, die zurückgegeben werden sollen

- Standard: `2`
- Akzeptiert einen Wert


## `events:list`

```bash
bin/magento events:list
```

Zeigt die Liste der abonnierten Ereignisse an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Gibt eine Liste der abonnierten Ereignisse zurück, die im angegebenen Modul definiert sind

### Argumente

#### `module_name`

Modulname

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Erstellt Metadaten in Adobe I/O aus der Konfigurationsliste (XML- und Anwendungskonfigurationen)

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Gibt Details zum konfigurierten Ereignisanbieter zurück.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Listet Ereignisregistrierungen in Ihrem App Builder-Projekt auf

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

Abonniert das Ereignis

### Argumente

#### `event-code`

Ereigniscode

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Erzwingt das Abonnieren des angegebenen Ereignisses, auch wenn es nicht lokal definiert wurde.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--fields`

Die Liste der Felder in der Payload der Ereignisdaten.

- Standard: `[]`
- Erfordert einen Wert

#### `--parent`

Der übergeordnete Ereigniscode für ein Ereignisabonnement mit Regeln oder als Alias.

- Erfordert einen Wert

#### `--rules`

Die Liste der Regeln für das Ereignisabonnement, wobei jede Regel als „Feld\|Benutzer\|Wert“ formatiert ist. Um diese Option zu verwenden, müssen Sie auch die Option „Übergeordnet“ angeben.

- Standard: `[]`
- Erfordert einen Wert

#### `--priority`, `-p`

Beschleunigt die Übertragung dieses Ereignisses. Legen Sie diese Option für Ereignisse fest, die sofort gesendet werden müssen. Standardmäßig werden Ereignisse von Cron einmal pro Minute gesendet.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--destination`, `-d`

Das Ziel dieses Ereignisses. Geben Sie diese Option für die Ereignisse an, die an das benutzerdefinierte Ziel gesendet werden sollen.

- Standard: `default`
- Erfordert einen Wert

#### `--hipaaAuditRequired`

Gibt an, dass das Ereignis Daten enthält, die HIPAA-Prüfungen unterliegen.

- Standard: `false`
- Akzeptiert keinen Wert


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Ereignismetadaten für diese Instanz synchronisieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--delete`, `-d`

Ereignismetadaten sind nicht mehr erforderlich.

- Standard: `false`
- Akzeptiert keinen Wert


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Entfernt das Abonnement des angegebenen Ereignisses

### Argumente

#### `event-code`

Ereigniscode, von dem das Abonnement zu kündigen ist

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Erkennt Sätze in der Codebasis

### Argumente

#### `directory`

Zu analysierender Verzeichnispfad Nicht erforderlich, wenn —magento Flag gesetzt ist

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Pfad (einschließlich Dateiname) zu einer Ausgabedatei. Wenn keine Datei angegeben ist, wird standardmäßig stdout verwendet.

- Erfordert einen Wert

#### `--magento`, `-m`

Verwenden Sie den Parameter —magento, um die aktuelle Magento Codebasis zu analysieren. Lassen Sie den Parameter weg, wenn ein Verzeichnis angegeben ist.

- Standard: `false`
- Akzeptiert keinen Wert


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Speichert das Sprachpaket

### Argumente

#### `source`

Pfad zur Wörterbuchdatei mit Übersetzungen

- Erforderlich


#### `locale`

Zielgebietsschema für das Wörterbuch, z. B. „de_DE“

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--mode`, `-m`

Speichermodus für Wörterbuch - „replace“ - Sprachpaket durch neues ersetzen - „merge“ - Sprachpakete zusammenführen, standardmäßig „replace“

- Standard: `replace`
- Erfordert einen Wert

#### `--allow-duplicates`, `-d`

Verwenden Sie den Parameter —allow-duplicates, um Dubletten der Übersetzung zu speichern. Lassen Sie andernfalls den Parameter weg.

- Standard: `false`
- Akzeptiert keinen Wert


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Deinstalliert Sprachpakete

### Argumente

#### `package`

Name des Sprachpakets

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--backup-code`, `-b`

Code- und Konfigurationsdateien sichern (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:info`

```bash
bin/magento indexer:info
```

Zeigt zulässige Indexer an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

indiziert Daten neu

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, die auf alle Indizes angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Setzt den Indexerstatus auf ungültig zurück

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, die auf alle Indizes angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Festlegen des Indexerdimensionsmodus

### Argumente

#### `indexer`

Indexername [CATALOG_PRODUCT_PRICE|CATALOGPERMISSIONS_CATEGORY]


#### `mode`

Indexerdimensionsmodi catalog_product_price          none,website,customer_group,website_and_customer_group_catalogPermissions_category    none,customer_group

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Legt den Indexmodus-Typ fest

### Argumente

#### `mode`

Indexermodus-Typ [realtime|schedule]


#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, die auf alle Indizes angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Legt den angegebenen Indexerstatus fest

### Argumente

#### `status`

Indexerstatustyp [ungültig|ausgesetzt|gültig]

- Erforderlich


#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, die auf alle Indizes angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Zeigt den Indexer-Dimension-Modus an

### Argumente

#### `indexer`

Durch Leerzeichen getrennte Liste von Indextypen oder Weglassen der Anwendung auf alle Indizes (CATALOG_PRODUCT_PRICE, CATALOGPERMISSIONS_CATEGORY)

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Zeigt den Indexmodus an

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, die auf alle Indizes angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Zeigt den Status des Indexers an

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, die auf alle Indizes angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Zeigt den Magento Admin-URI an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Druckt die Liste der verfügbaren Backup-Dateien

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Zeigt die Liste der verfügbaren Währungen an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Zeigt die Anzahl der Abhängigkeiten vom Magento-Framework an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Berichtsdateiname

- Standard: `framework-dependencies.csv`
- Erfordert einen Wert


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Zeigt die Anzahl der Abhängigkeiten zwischen Modulen an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Berichtsdateiname

- Standard: `modules-dependencies.csv`
- Erfordert einen Wert


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Zeigt die Anzahl der zirkulären Abhängigkeiten zwischen Modulen an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Berichtsdateiname

- Standard: `modules-circular-dependencies.csv`
- Erfordert einen Wert


## `info:language:list`

```bash
bin/magento info:language:list
```

Zeigt die Liste der verfügbaren Sprachgebietsschemata an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Zeigt die Liste der verfügbaren Zeitzonen an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Erstellen von Reservierungen durch angegebene Vergütungsargumente

### Argumente

#### `compensations`

Liste der Vergütungsargumente im Format &quot;::“

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--raw`, `-r`

Rohausgabe

- Standard: `false`
- Akzeptiert keinen Wert


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Alle Bestellungen und Produkte mit Inkonsistenzen der verkäuflichen Menge anzeigen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--complete-orders`, `-c`

Nur Inkonsistenzen für abgeschlossene Bestellungen anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--incomplete-orders`, `-i`

Nur Inkonsistenzen bei unvollständigen Bestellungen anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--bunch-size`, `-b`

Definiert, wie viele Bestellungen gleichzeitig geladen werden

- Standard: `50`
- Akzeptiert einen Wert

#### `--raw`, `-r`

Rohausgabe

- Standard: `false`
- Akzeptiert keinen Wert


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Herunterladen und Importieren von Geonamen für den Quellenauswahlalgorithmus

### Argumente

#### `countries`

Liste der zu importierenden Länder-Codes

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Legt IPs mit Ausnahme des Wartungsmodus fest

### Argumente

#### `ip`

Zulässige IP-Adressen

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--none`

Zulässige IP-Adressen löschen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--add`

Hinzufügen der IP-Adresse zur vorhandenen Liste

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Deaktiviert den Wartungsmodus

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--ip`

Zulässige IP-Adressen (verwenden Sie „none“, um die Liste der zulässigen IP-Adressen zu löschen)

- Standard: `[]`
- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Aktiviert den Wartungsmodus

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--ip`

Zulässige IP-Adressen (verwenden Sie „none“, um die Liste der zulässigen IP-Adressen zu löschen)

- Standard: `[]`
- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Zeigt den Wartungsmodus-Status an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Synchronisieren von Inhalten mit Assets

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Synchronisieren von Medienspeicher und Medienelementen in der Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `module:config:status`

```bash
bin/magento module:config:status
```

Überprüft die Konfiguration der Module in der Datei &quot;app/etc/config.php&quot; und meldet, ob sie aktuell sind oder nicht

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Deaktiviert die angegebenen Module

### Argumente

#### `module`

Modulname

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Abhängigkeitsprüfung umgehen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--all`

Alle Module deaktivieren

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Aktiviert die angegebenen Module

### Argumente

#### `module`

Modulname

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Abhängigkeitsprüfung umgehen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--all`

Alle Module aktivieren

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Zeigt den Status der Module an

### Argumente

#### `module-names`

Optionaler Modulname

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--enabled`

Nur aktivierte Module drucken

- Standard: `false`
- Akzeptiert keinen Wert

#### `--disabled`

Nur deaktivierte Module drucken

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Deinstalliert vom Composer installierte Module

### Argumente

#### `module`

Modulname

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--remove-data`, `-r`

Von Modul(en) installierte Daten entfernen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--backup-code`

Code- und Konfigurationsdateien sichern (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--backup-media`

Mediensicherung erstellen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--backup-db`

Vollständige Datenbanksicherung durchführen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--non-composer`

Alle Module, die hier überschrieben werden, sind nicht komponentenbasiert

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Überprüfen Sie die Bereitstellungswarteschlange auf Einträge und erstellen Sie eine geeignete Bereitstellungsmarkierung.

### Argumente

#### `message`

Nachricht bereitstellen?

- Erforderlich


#### `change_log`

Änderungsprotokoll?

- Erforderlich


#### `user`

Bereitstellungsbenutzer


#### `revision`

Revision

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Liste der MessageQueue-Verbraucher

```
This command shows list of MessageQueue consumers.
```

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

MessageQueue-Verbraucher neu starten

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

MessageQueue-Verbraucher starten

```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```

### Argumente

#### `consumer`

Der Name des zu startenden Verbrauchers.

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--max-messages`

Die Anzahl der Nachrichten, die von der Verbraucherin bzw. dem Verbraucher vor Beendigung des Prozesses verarbeitet werden sollen. Wenn nicht anders angegeben: Beendet nach der Verarbeitung aller Nachrichten in der Warteschlange.

- Erfordert einen Wert

#### `--batch-size`

Die Anzahl der Nachrichten pro Batch. Gilt nur für den Chargenverbraucher.

- Erfordert einen Wert

#### `--area-code`

Der bevorzugte Bereich (global, adminhtml usw.) ist standardmäßig global.

- Erfordert einen Wert

#### `--single-thread`

Diese Option verhindert, dass mehrere Kopien eines Verbrauchers gleichzeitig ausgeführt werden.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--multi-process`

Die Anzahl der Prozesse pro Verbraucher.

- Akzeptiert einen Wert

#### `--pid-file-path`

Der Dateipfad zum Speichern der PID (diese Option ist veraltet, verwenden Sie stattdessen —single-thread)

- Erfordert einen Wert


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Synchronisieren von Mediendateien mit dem Remote-Speicher.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

Re-Synchronisiert Feed-Daten mit dem SaaS-Service.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--feed`

Feed-Name zur vollständigen Neusynchronisierung mit dem SaaS-Service. Verfügbare Feeds: Zahlungsdienste-Auftragsproduktion, Zahlungsdienste-Auftrags-Sandbox, Zahlungsdienste-Auftragsstatus Produktion, Zahlungsdienste-Auftragsstatus Sandbox, Zahlungsdienste-Storeproduktion, Zahlungsdienste-Store-Sandbox

- Erfordert einen Wert

#### `--no-reindex`

Führen Sie die erneute Übermittlung von Feed-Daten nur an den SaaS-Service aus. Indiziert nicht neu. (Diese Option gilt nicht für Produkte, Produktüberschreibungen, Preise und Feeds.)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--cleanup-feed`

Bereinigung der Feed-Indexertabelle vor der Synchronisierung erzwingen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--dry-run`

Probelauf. Daten werden nicht exportiert. Um die Payload in der Protokolldatei zu speichern, führen Sie var/log/saas-export.log mit der Umgebungsvariablen EXPORTER_EXTENDED_LOG=1 aus.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--thread-count`

Anzahl der Synchronisierungs-Threads festlegen.

- Erfordert einen Wert

#### `--batch-size`

Festlegen der Größe eines Synchronisierungs-Batches

- Erfordert einen Wert

#### `--continue-resync`

Fortsetzen der Resynchronisation von der letzten gespeicherten Position (diese Option gilt für die Produkte, Produktüberschreibungen, Preise und Feeds)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--by-ids`

Teilweise nach Liste der angegebenen Kennungen neu synchronisieren. (Diese Option gilt für die Produkte, Produktüberschreibungen und Preise für Feeds.)

- Erfordert einen Wert

#### `--id-type`

Typ der Kennungen für die teilweise Resynchronisation (z. B.: SKU, productId, usw.)

- Erfordert einen Wert


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Bereitstellen von Beispieldatenmodulen für Composer-basierte Magento-Installationen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--no-update`

Aktualisieren von composer.json ohne Ausführen eines Composer-Updates

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Entfernen Sie alle Beispieldatenpakete aus „composer.json“

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--no-update`

Aktualisieren von composer.json ohne Ausführen eines Composer-Updates

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Alle Beispieldatenmodule zur Neuinstallation zurücksetzen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Deaktivieren von reCAPTCHA für Formular bei vergessenem Kennwort für Admin-Benutzer

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Deaktivieren von reCAPTCHA für das Administratorbenutzer-Anmeldeformular

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Legen Sie die für die OTP-Generierung von Google verwendeten geheimen Daten fest.

### Argumente

#### `user`

Benutzername

- Erforderlich


#### `secret`

Geheim

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Alle verfügbaren Anbieter auflisten

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Konfiguration für einen Benutzer zurücksetzen

### Argumente

#### `user`

Benutzername

- Erforderlich


#### `provider`

Anbietercode

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Ausführen des Anwendungsservers

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--port`, `-p`

Zu bedienender Port

- Standard: `9501`
- Akzeptiert einen Wert

#### `--background`, `-b`

Hintergrundmodus-Markierung

- Standard: `0`
- Akzeptiert einen Wert

#### `--workerNum`, `-wn`

Anzahl der zu startenden Worker-Prozesse

- Standard: `4`
- Akzeptiert einen Wert

#### `--dispatchMode`, `-dm`

Methode der Bereitstellung von Verbindungen zu den Arbeitsabläufen

- Standard: `3`
- Akzeptiert einen Wert

#### `--maxRequests`, `-mr`

Max. Anfragen vor Neustart des Arbeitsprozesses

- Standard: `10000`
- Akzeptiert einen Wert

#### `--area`, `-a`

Anwendungsserverbereich

- Standard: `graphql`
- Akzeptiert einen Wert

#### `--magento-init-params`, `-mip`

Magento-Bootstrap-Init-Parameter

- Standard: &quot;
- Akzeptiert einen Wert

#### `--maxWaitTime`, `-mwt`

Wie lange nach dem Neuladen auf die Arbeiter gewartet wird (z. B. Konfigurationsänderung), bevor sie beendet werden

- Standard: `3600`
- Akzeptiert einen Wert

#### `--state-monitor`

Zustandsüberwachung aktivieren. Verwenden Sie dies nur zum Debuggen von Statusproblemen!

- Standard: `false`
- Akzeptiert keinen Wert


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Aggregatausgabe des Statusmonitors von ApplicationServer

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Ermöglicht die Sicherung der Code-Basis, der Medien und der Datenbank der Magento-Anwendung

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--code`

Code- und Konfigurationsdateien sichern (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--media`

Mediensicherung erstellen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--db`

Vollständige Datenbanksicherung durchführen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Erstellt oder ändert die Bereitstellungskonfiguration

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--remote-storage-driver`

Remote-Speichertreiber

- Erfordert einen Wert

#### `--remote-storage-prefix`

Remote-Speicherpräfix

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-endpoint`

Remote-Speicherendpunkt

- Erfordert einen Wert

#### `--remote-storage-bucket`

Remote-Speicher-Bucket

- Erfordert einen Wert

#### `--remote-storage-region`

Remote-Speicherregion

- Erfordert einen Wert

#### `--remote-storage-key`

Remote-Speicherzugriffsschlüssel

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-secret`

Geheimschlüssel des Remotespeichers

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-path-style`

Remote-Speicherpfadstil

- Standard: `0`
- Erfordert einen Wert

#### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)

- Erfordert einen Wert

#### `--enable-debug-logging`

Debug-Protokollierung aktivieren

- Erfordert einen Wert

#### `--enable-syslog-logging`

Syslog-Protokollierung aktivieren

- Erfordert einen Wert

#### `--id_salt`

GraphQL-Salz

- Erfordert einen Wert

#### `--checkout-async`

Asynchrone Bestellverarbeitung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--config-async`

Async Admin Config Speichern aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--amqp-host`

AMQP-Server-Host

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-port`

AMQP-Server-Port

- Standard: `5672`
- Erfordert einen Wert

#### `--amqp-user`

AMQP-Server-Benutzername

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-password`

AMQP-Server-Kennwort

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-virtualhost`

AMQP VirtualHost

- Standard: `/`
- Erfordert einen Wert

#### `--amqp-ssl`

AMQP-SSL

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-ssl-options`

AMQL-SSL-Optionen (JSON)

- Standard: &quot;
- Erfordert einen Wert

#### `--consumers-wait-for-messages`

Sollen Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--queue-default-connection`

Standardverbindung für Nachrichtenwarteschlangen. Kann „db“, „amqp“ oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert sein, da andernfalls Nachrichten nicht korrekt verarbeitet werden.

- Erfordert einen Wert

#### `--deferred-total-calculating`

Verzögerte Gesamtberechnung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--key`

Verschlüsselungsschlüssel

- Erfordert einen Wert

#### `--db-host`

Datenbankserver-Host

- Erfordert einen Wert

#### `--db-name`

Datenbankname

- Erfordert einen Wert

#### `--db-user`

Benutzername des Datenbank-Servers

- Erfordert einen Wert

#### `--db-engine`

Datenbank-Server-Engine

- Erfordert einen Wert

#### `--db-password`

Datenbankserver-Kennwort

- Erfordert einen Wert

#### `--db-prefix`

Datenbanktabellen-Präfix

- Erfordert einen Wert

#### `--db-model`

Datenbanktyp

- Erfordert einen Wert

#### `--db-init-statements`

Anfangssatz der Befehle in der Datenbank

- Erfordert einen Wert

#### `--skip-db-validation`, `-s`

Wenn angegeben, wird die Überprüfung der DB-Verbindung übersprungen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--http-cache-hosts`

HTTP-Cache-Hosts

- Erfordert einen Wert

#### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei zum Aufbau der DB-Verbindung über SSL

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-ca`

Vollständiger Pfad der Serverzertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-verify`

Serverzertifizierung überprüfen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--session-save`

Session Save Handler

- Erfordert einen Wert

#### `--session-save-redis-host`

Vollqualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets

- Erfordert einen Wert

#### `--session-save-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--session-save-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--session-save-redis-timeout`

Verbindungs-Timeout, in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-retries`

Wiederholte Verbindungsversuche anpassen.

- Erfordert einen Wert

#### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen

- Erfordert einen Wert

#### `--session-save-redis-db`

Redis-Datenbanknummer

- Erfordert einen Wert

#### `--session-save-redis-compression-threshold`

Redis-Komprimierungsschwellenwert

- Erfordert einen Wert

#### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy

- Erfordert einen Wert

#### `--session-save-redis-log-level`

Protokollebene neu angeben. Werte: 0 (am wenigsten ausführlich) bis 7 (am meisten ausführlich)

- Erfordert einen Wert

#### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperre einer Sitzung warten können

- Erfordert einen Wert

#### `--session-save-redis-break-after-frontend`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Frontend-Sitzung aufzuheben

- Erfordert einen Wert

#### `--session-save-redis-break-after-adminhtml`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Admin-Sitzung aufzuheben

- Erfordert einen Wert

#### `--session-save-redis-first-lifetime`

Lebensdauer der Sitzung für Nicht-Bots beim ersten Schreiben in Sekunden (zur Deaktivierung 0 verwenden)

- Erfordert einen Wert

#### `--session-save-redis-bot-first-lifetime`

Lebensdauer der Sitzung für Bots beim ersten Schreiben (0 zum Deaktivieren) in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (0 zur Deaktivierung)

- Erfordert einen Wert

#### `--session-save-redis-disable-locking`

Redis-Sperre deaktivieren. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-min-lifetime`

Sitzungslebensdauer in Sekunden ändern

- Erfordert einen Wert

#### `--session-save-redis-max-lifetime`

Maximale Redis-Sitzungslebensdauer in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Erfordert einen Wert

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommata getrennt

- Erfordert einen Wert

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifizieren den Master. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-Verbindungsversuche.

- Erfordert einen Wert

#### `--cache-backend`

Standard-Cache-Handler

- Erfordert einen Wert

#### `--cache-backend-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--cache-backend-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

#### `--cache-backend-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--cache-backend-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--cache-backend-redis-compress-data`

Auf 0 gesetzt, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

#### `--cache-backend-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--cache-backend-redis-use-lua`

Auf 1 gesetzt, um lua zu aktivieren (Standard ist 0, deaktiviert)

- Erfordert einen Wert

#### `--cache-backend-redis-use-lua-on-gc`

Auf 0 gesetzt, um LUA bei der automatischen Bereinigung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

#### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--allow-parallel-generation`

Cache-Generierung nicht blockierend zulassen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--page-cache`

Standard-Cache-Handler

- Erfordert einen Wert

#### `--page-cache-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--page-cache-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

#### `--page-cache-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--page-cache-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--page-cache-redis-compress-data`

Auf 1 gesetzt, um den vollständigen Seiten-Cache zu komprimieren (zur Deaktivierung 0 verwenden)

- Erfordert einen Wert

#### `--page-cache-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--lock-provider`

Anbieternamen sperren

- Erfordert einen Wert

#### `--lock-db-prefix`

Installationsspezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten

- Erfordert einen Wert

#### `--lock-zookeeper-host`

Host und Port für die Verbindung mit dem ZooKeeper-Cluster. Beispiel: 127.0.0.1:2181

- Erfordert einen Wert

#### `--lock-zookeeper-path`

Der Pfad, in dem ZooKeeper Sperren speichert. Der Standardpfad lautet: /magento/locks

- Erfordert einen Wert

#### `--lock-file-path`

Der Pfad, in dem Dateisperren gespeichert werden.

- Erfordert einen Wert

#### `--document-root-is-pub`

Markierung, die anzeigt, ob Pub sich im Stammverzeichnis befindet, nur „true“ oder „false“ sein kann.

- Erfordert einen Wert

#### `--backpressure-logger`

Handler für den Rückdrucklogger

- Erfordert einen Wert

#### `--backpressure-logger-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--backpressure-logger-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--backpressure-logger-redis-timeout`

Redis-Server-Zeitüberschreitung

- Erfordert einen Wert

#### `--backpressure-logger-redis-persistent`

Redis persistent

- Erfordert einen Wert

#### `--backpressure-logger-redis-db`

Redis-DB-Nummer

- Erfordert einen Wert

#### `--backpressure-logger-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--backpressure-logger-redis-user`

Redis-Server-Benutzer

- Erfordert einen Wert

#### `--backpressure-logger-id-prefix`

ID-Präfix für Schlüssel

- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installiert und aktualisiert Daten in der Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Erzeugt den Patch und legt ihn in einem bestimmten Ordner ab.

### Argumente

#### `module`

Modulname

- Erforderlich


#### `patch`

Patch-Name

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--revertable`

Überprüfen Sie, ob das Patch rückgängig gemacht werden kann oder nicht.

- Standard: `false`
- Akzeptiert einen Wert

#### `--type`

Finden Sie heraus, welcher Patch-Typ generiert werden soll. Verfügbare Werte: `data`, `schema`.

- Standard: `data`
- Akzeptiert einen Wert


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Erstellen einer Whitelist von Tabellen und Spalten, die vom Deklarationsinstallationsprogramm bearbeitet werden dürfen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--module-name`

Name des Moduls, in dem die Whitelist generiert wird

- Standard: `all`
- Akzeptiert einen Wert


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verschieben von Tabellen mit Auscheckzitaten auf einen separaten DB-Server

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

Slave-DB-Server-Host

- Standard: `localhost`
- Erfordert einen Wert

#### `--dbname`

Slave-Datenbankname

- Erfordert einen Wert

#### `--username`

Slave-DB-Benutzername

- Standard: `root`
- Erfordert einen Wert

#### `--password`

Slave DB-Benutzerkennwort

- Akzeptiert einen Wert

#### `--connection`

Slave-Verbindungsname

- Standard: `default`
- Akzeptiert einen Wert

#### `--resource`

Slave-Ressourcenname

- Standard: `default`
- Akzeptiert einen Wert

#### `--maxAllowedLag`

Max. zulässige Zeitverzögerungsunterdrückung (in Sekunden)

- Standard: &quot;
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verschieben von Tabellen mit Auscheckzitaten auf einen separaten DB-Server. Veraltet seit 2.4.2 und wird entfernt

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

DB-Server-Host auschecken

- Erfordert einen Wert

#### `--dbname`

Checkout-Datenbankname

- Erfordert einen Wert

#### `--username`

Checkout-DB-Benutzername

- Erfordert einen Wert

#### `--password`

Checkout-DB-Benutzerkennwort

- Akzeptiert einen Wert

#### `--connection`

Checkout-Verbindungsname

- Standard: `checkout`
- Akzeptiert einen Wert

#### `--resource`

Checkout-Ressourcenname

- Standard: `checkout`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verschieben von verkaufsbezogenen Tabellen auf einen separaten DB-Server. Veraltet seit 2.4.2 und wird entfernt

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

Vertriebs-DB-Server-Host

- Erfordert einen Wert

#### `--dbname`

Name der Verkaufsdatenbank

- Erfordert einen Wert

#### `--username`

Benutzername der Verkaufsdatenbank

- Erfordert einen Wert

#### `--password`

Sales DB-Benutzerkennwort

- Akzeptiert einen Wert

#### `--connection`

Name der Verkaufsverbindung

- Standard: `sales`
- Akzeptiert einen Wert

#### `--resource`

Name der Vertriebsressource

- Standard: `sales`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installiert und aktualisiert das DB-Schema

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--convert-old-scripts`

Ermöglicht die Konvertierung alter Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Prüft, ob DB-Schema oder Daten aktualisiert werden müssen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Erzeugt die ID-Konfiguration und alle fehlenden Klassen, die automatisch generiert werden können

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installiert das Magento-Programm

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--remote-storage-driver`

Remote-Speichertreiber

- Erfordert einen Wert

#### `--remote-storage-prefix`

Remote-Speicherpräfix

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-endpoint`

Remote-Speicherendpunkt

- Erfordert einen Wert

#### `--remote-storage-bucket`

Remote-Speicher-Bucket

- Erfordert einen Wert

#### `--remote-storage-region`

Remote-Speicherregion

- Erfordert einen Wert

#### `--remote-storage-key`

Remote-Speicherzugriffsschlüssel

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-secret`

Geheimschlüssel des Remotespeichers

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-path-style`

Remote-Speicherpfadstil

- Standard: `0`
- Erfordert einen Wert

#### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)

- Erfordert einen Wert

#### `--enable-debug-logging`

Debug-Protokollierung aktivieren

- Erfordert einen Wert

#### `--enable-syslog-logging`

Syslog-Protokollierung aktivieren

- Erfordert einen Wert

#### `--id_salt`

GraphQL-Salz

- Erfordert einen Wert

#### `--checkout-async`

Asynchrone Bestellverarbeitung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--config-async`

Async Admin Config Speichern aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--amqp-host`

AMQP-Server-Host

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-port`

AMQP-Server-Port

- Standard: `5672`
- Erfordert einen Wert

#### `--amqp-user`

AMQP-Server-Benutzername

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-password`

AMQP-Server-Kennwort

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-virtualhost`

AMQP VirtualHost

- Standard: `/`
- Erfordert einen Wert

#### `--amqp-ssl`

AMQP-SSL

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-ssl-options`

AMQL-SSL-Optionen (JSON)

- Standard: &quot;
- Erfordert einen Wert

#### `--consumers-wait-for-messages`

Sollen Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--queue-default-connection`

Standardverbindung für Nachrichtenwarteschlangen. Kann „db“, „amqp“ oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert sein, da andernfalls Nachrichten nicht korrekt verarbeitet werden.

- Erfordert einen Wert

#### `--deferred-total-calculating`

Verzögerte Gesamtberechnung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--key`

Verschlüsselungsschlüssel

- Erfordert einen Wert

#### `--db-host`

Datenbankserver-Host

- Erfordert einen Wert

#### `--db-name`

Datenbankname

- Erfordert einen Wert

#### `--db-user`

Benutzername des Datenbank-Servers

- Erfordert einen Wert

#### `--db-engine`

Datenbank-Server-Engine

- Erfordert einen Wert

#### `--db-password`

Datenbankserver-Kennwort

- Erfordert einen Wert

#### `--db-prefix`

Datenbanktabellen-Präfix

- Erfordert einen Wert

#### `--db-model`

Datenbanktyp

- Erfordert einen Wert

#### `--db-init-statements`

Anfangssatz der Befehle in der Datenbank

- Erfordert einen Wert

#### `--skip-db-validation`, `-s`

Wenn angegeben, wird die Überprüfung der DB-Verbindung übersprungen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--http-cache-hosts`

HTTP-Cache-Hosts

- Erfordert einen Wert

#### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei zum Aufbau der DB-Verbindung über SSL

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-ca`

Vollständiger Pfad der Serverzertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-verify`

Serverzertifizierung überprüfen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--session-save`

Session Save Handler

- Erfordert einen Wert

#### `--session-save-redis-host`

Vollqualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets

- Erfordert einen Wert

#### `--session-save-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--session-save-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--session-save-redis-timeout`

Verbindungs-Timeout, in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-retries`

Wiederholte Verbindungsversuche anpassen.

- Erfordert einen Wert

#### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen

- Erfordert einen Wert

#### `--session-save-redis-db`

Redis-Datenbanknummer

- Erfordert einen Wert

#### `--session-save-redis-compression-threshold`

Redis-Komprimierungsschwellenwert

- Erfordert einen Wert

#### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy

- Erfordert einen Wert

#### `--session-save-redis-log-level`

Protokollebene neu angeben. Werte: 0 (am wenigsten ausführlich) bis 7 (am meisten ausführlich)

- Erfordert einen Wert

#### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperre einer Sitzung warten können

- Erfordert einen Wert

#### `--session-save-redis-break-after-frontend`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Frontend-Sitzung aufzuheben

- Erfordert einen Wert

#### `--session-save-redis-break-after-adminhtml`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Admin-Sitzung aufzuheben

- Erfordert einen Wert

#### `--session-save-redis-first-lifetime`

Lebensdauer der Sitzung für Nicht-Bots beim ersten Schreiben in Sekunden (zur Deaktivierung 0 verwenden)

- Erfordert einen Wert

#### `--session-save-redis-bot-first-lifetime`

Lebensdauer der Sitzung für Bots beim ersten Schreiben (0 zum Deaktivieren) in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (0 zur Deaktivierung)

- Erfordert einen Wert

#### `--session-save-redis-disable-locking`

Redis-Sperre deaktivieren. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-min-lifetime`

Sitzungslebensdauer in Sekunden ändern

- Erfordert einen Wert

#### `--session-save-redis-max-lifetime`

Maximale Redis-Sitzungslebensdauer in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Erfordert einen Wert

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommata getrennt

- Erfordert einen Wert

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifizieren den Master. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-Verbindungsversuche.

- Erfordert einen Wert

#### `--cache-backend`

Standard-Cache-Handler

- Erfordert einen Wert

#### `--cache-backend-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--cache-backend-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

#### `--cache-backend-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--cache-backend-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--cache-backend-redis-compress-data`

Auf 0 gesetzt, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

#### `--cache-backend-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--cache-backend-redis-use-lua`

Auf 1 gesetzt, um lua zu aktivieren (Standard ist 0, deaktiviert)

- Erfordert einen Wert

#### `--cache-backend-redis-use-lua-on-gc`

Auf 0 gesetzt, um LUA bei der automatischen Bereinigung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

#### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--allow-parallel-generation`

Cache-Generierung nicht blockierend zulassen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--page-cache`

Standard-Cache-Handler

- Erfordert einen Wert

#### `--page-cache-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--page-cache-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

#### `--page-cache-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--page-cache-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--page-cache-redis-compress-data`

Auf 1 gesetzt, um den vollständigen Seiten-Cache zu komprimieren (zur Deaktivierung 0 verwenden)

- Erfordert einen Wert

#### `--page-cache-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--lock-provider`

Anbieternamen sperren

- Erfordert einen Wert

#### `--lock-db-prefix`

Installationsspezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten

- Erfordert einen Wert

#### `--lock-zookeeper-host`

Host und Port für die Verbindung mit dem ZooKeeper-Cluster. Beispiel: 127.0.0.1:2181

- Erfordert einen Wert

#### `--lock-zookeeper-path`

Der Pfad, in dem ZooKeeper Sperren speichert. Der Standardpfad lautet: /magento/locks

- Erfordert einen Wert

#### `--lock-file-path`

Der Pfad, in dem Dateisperren gespeichert werden.

- Erfordert einen Wert

#### `--document-root-is-pub`

Markierung, die anzeigt, ob Pub sich im Stammverzeichnis befindet, nur „true“ oder „false“ sein kann.

- Erfordert einen Wert

#### `--backpressure-logger`

Handler für den Rückdrucklogger

- Erfordert einen Wert

#### `--backpressure-logger-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--backpressure-logger-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

#### `--backpressure-logger-redis-timeout`

Redis-Server-Zeitüberschreitung

- Erfordert einen Wert

#### `--backpressure-logger-redis-persistent`

Redis persistent

- Erfordert einen Wert

#### `--backpressure-logger-redis-db`

Redis-DB-Nummer

- Erfordert einen Wert

#### `--backpressure-logger-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--backpressure-logger-redis-user`

Redis-Server-Benutzer

- Erfordert einen Wert

#### `--backpressure-logger-id-prefix`

ID-Präfix für Schlüssel

- Erfordert einen Wert

#### `--base-url`

URL, unter der der Store verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url

- Erfordert einen Wert

#### `--language`

Standardsprachcode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code

- Erfordert einen Wert

#### `--timezone`

Standard-Zeitzonen-Code. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone

- Erfordert einen Wert

#### `--currency`

Standard-Währungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow

- Erfordert einen Wert

#### `--use-rewrites`

Verwenden Sie Neuschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites

- Erfordert einen Wert

#### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend

- Erfordert einen Wert

#### `--base-url-secure`

Basis-URL für die SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url

- Erfordert einen Wert

#### `--use-secure-admin`

Ausführen der Admin-Oberfläche mit SSL. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml

- Erfordert einen Wert

#### `--admin-use-security-key`

Ob die Funktion „Sicherheitsschlüssel“ in den Admin-URLs und Formularen von Magento verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key

- Erfordert einen Wert

#### `--admin-user`

Admin-Benutzer

- Akzeptiert einen Wert

#### `--admin-password`

Administratorkennwort

- Akzeptiert einen Wert

#### `--admin-email`

Admin Email

- Akzeptiert einen Wert

#### `--admin-firstname`

Vorname des Administrators

- Akzeptiert einen Wert

#### `--admin-lastname`

Nachname des Administrators

- Akzeptiert einen Wert

#### `--search-engine`

Suchmaschine. Werte: elasticsearch8, opensearch

- Erfordert einen Wert

#### `--elasticsearch-host`

Elasticsearch-Server-Host.

- Erfordert einen Wert

#### `--elasticsearch-port`

Elasticsearch-Server-Port.

- Erfordert einen Wert

#### `--elasticsearch-enable-auth`

Auf 1 gesetzt, um die Authentifizierung zu aktivieren. (Standard ist 0, deaktiviert)

- Erfordert einen Wert

#### `--elasticsearch-username`

Elasticsearch-Benutzername. Nur anwendbar, wenn die HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--elasticsearch-password`

Elasticsearch-Kennwort. Nur anwendbar, wenn die HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--elasticsearch-index-prefix`

Elasticsearch-Indexpräfix.

- Erfordert einen Wert

#### `--elasticsearch-timeout`

Elasticsearch-Server-Zeitüberschreitung.

- Erfordert einen Wert

#### `--opensearch-host`

OpenSearch-Server-Host.

- Erfordert einen Wert

#### `--opensearch-port`

OpenSearch-Server-Port.

- Erfordert einen Wert

#### `--opensearch-enable-auth`

Auf 1 gesetzt, um die Authentifizierung zu aktivieren. (Standard ist 0, deaktiviert)

- Erfordert einen Wert

#### `--opensearch-username`

OpenSearch-Benutzername. Nur anwendbar, wenn die HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--opensearch-password`

OpenSearch-Kennwort. Nur anwendbar, wenn die HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--opensearch-index-prefix`

OpenSearch-Indexpräfix.

- Erfordert einen Wert

#### `--opensearch-timeout`

OpenSearch-Server-Zeitüberschreitung.

- Erfordert einen Wert

#### `--cleanup-database`

Datenbank vor der Installation bereinigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--sales-order-increment-prefix`

Präfix für Kundenauftragsnummer

- Erfordert einen Wert

#### `--use-sample-data`

Beispieldaten verwenden

- Standard: `false`
- Akzeptiert keinen Wert

#### `--enable-modules`

Liste der durch Kommas getrennten Modulnamen. Dieser muss bei der Installation miteinbezogen werden. Verfügbarer Zauberparameter „all“.

- Akzeptiert einen Wert

#### `--disable-modules`

Liste der durch Kommas getrennten Modulnamen. Dies muss bei der Installation vermieden werden. Verfügbarer Zauberparameter „all“.

- Akzeptiert einen Wert

#### `--convert-old-scripts`

Ermöglicht die Konvertierung alter Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

#### `--interactive`, `-i`

Interaktive Magento-Installation

- Standard: `false`
- Akzeptiert keinen Wert

#### `--safe-mode`

Sichere Installation von Magento mit Dumps bei destruktiven Vorgängen, z. B. Entfernen von Spalten

- Akzeptiert einen Wert

#### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps

- Akzeptiert einen Wert

#### `--dry-run`

Die Magento-Installation wird im Trockenlaufmodus ausgeführt

- Standard: `false`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Erzeugt Vorrichtungen

### Argumente

#### `profile`

Pfad zur Profilkonfigurationsdatei

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--skip-reindex`, `-s`

Neuindex überspringen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Rollback der Magento-Anwendungs-Codebase, der Medien und der Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--code-file`, `-c`

Basisname der Code-Sicherungsdatei in var/backups

- Erfordert einen Wert

#### `--media-file`, `-m`

Basisname der Mediensicherungsdatei in var/backups

- Erfordert einen Wert

#### `--db-file`, `-d`

Basisname der Datenbank-Backup-Datei in var/backups

- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Stellt statische Ansichtsdateien bereit

### Argumente

#### `languages`

Durch Leerzeichen getrennte Liste von ISO-639-Sprachcodes, für die statische Ansichtsdateien ausgegeben werden sollen.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Dateien in jedem Modus bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--strategy`, `-s`

Dateien mithilfe einer angegebenen Strategie bereitstellen.

- Standard: `quick`
- Akzeptiert einen Wert

#### `--area`, `-a`

Generieren Sie Dateien nur für die angegebenen Bereiche.

- Standard: `all`
- Akzeptiert mehrere Werte

#### `--exclude-area`

Keine Dateien für die angegebenen Bereiche erzeugen

- Standard: `none`
- Akzeptiert mehrere Werte

#### `--theme`, `-t`

Generieren Sie statische Ansichtsdateien nur für die angegebenen Designs.

- Standard: `all`
- Akzeptiert mehrere Werte

#### `--exclude-theme`

Keine Dateien für die angegebenen Designs generieren.

- Standard: `none`
- Akzeptiert mehrere Werte

#### `--language`, `-l`

Generieren Sie Dateien nur für die angegebenen Sprachen.

- Standard: `all`
- Akzeptiert mehrere Werte

#### `--exclude-language`

Keine Dateien für die angegebenen Sprachen erzeugen.

- Standard: `none`
- Akzeptiert mehrere Werte

#### `--jobs`, `-j`

Aktivieren Sie die parallele Verarbeitung mit der angegebenen Anzahl von Aufträgen.

- Standard: `0`
- Akzeptiert einen Wert

#### `--max-execution-time`

Die maximale erwartete Ausführungszeit des statischen Bereitstellungsprozesses (in Sekunden).

- Standard: `900`
- Akzeptiert einen Wert

#### `--symlink-locale`

Erstellen Sie Symlinks für die Dateien dieser Gebietsschemata, die für die Bereitstellung übergeben werden, aber keine Anpassungen aufweisen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--content-version`

Benutzerdefinierte Versionen statischer Inhalte können verwendet werden, wenn die Bereitstellung auf mehreren Knoten ausgeführt wird, um sicherzustellen, dass die Version statischer Inhalte identisch ist und die Zwischenspeicherung ordnungsgemäß funktioniert.

- Erfordert einen Wert

#### `--refresh-content-version-only`

Die Aktualisierung der Version statischer Inhalte kann nur verwendet werden, um statische Inhalte im Browser-Cache und CDN-Cache zu aktualisieren.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-javascript`

JavaScript-Dateien nicht bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-js-bundle`

Stellen Sie keine JavaScript-Paketdateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-css`

Stellen Sie keine CSS-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-less`

Stellen Sie keine LESS-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-images`

Keine Bilder bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-fonts`

Stellen Sie keine Schriftarten bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-html`

HTML-Dateien nicht bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-misc`

Stellen Sie keine Dateien anderer Typen bereit (.md, .jbf, .csv usw.).

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-html-minify`

Minimieren Sie keine HTML-Dateien.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-parent`

Übergeordnete Designs nicht kompilieren. Wird nur in schnellen und standardmäßigen Strategien unterstützt.

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installiert die Store-Konfiguration. Veraltet seit 2.2.0. Verwenden Sie stattdessen :set config.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--base-url`

URL, unter der der Store verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url

- Erfordert einen Wert

#### `--language`

Standardsprachcode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code

- Erfordert einen Wert

#### `--timezone`

Standard-Zeitzonen-Code. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone

- Erfordert einen Wert

#### `--currency`

Standard-Währungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow

- Erfordert einen Wert

#### `--use-rewrites`

Verwenden Sie Neuschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites

- Erfordert einen Wert

#### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend

- Erfordert einen Wert

#### `--base-url-secure`

Basis-URL für die SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url

- Erfordert einen Wert

#### `--use-secure-admin`

Ausführen der Admin-Oberfläche mit SSL. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml

- Erfordert einen Wert

#### `--admin-use-security-key`

Ob die Funktion „Sicherheitsschlüssel“ in den Admin-URLs und Formularen von Magento verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key

- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Deinstalliert das Magento-Programm

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Führt Upgrades für die Magento-Anwendung, DB-Daten und das Schema durch

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--keep-generated`

Verhindert das Löschen der generierten Dateien. Wir raten von der Verwendung dieser Option ab, es sei denn, sie wird in der Produktion bereitgestellt. Weitere Informationen erhalten Sie von Ihrem Systemintegrator oder Administrator.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--convert-old-scripts`

Ermöglicht die Konvertierung alter Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

#### `--safe-mode`

Sichere Installation von Magento mit Dumps bei destruktiven Vorgängen, z. B. Entfernen von Spalten

- Akzeptiert einen Wert

#### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps

- Akzeptiert einen Wert

#### `--dry-run`

Die Magento-Installation wird im Trockenlaufmodus ausgeführt

- Standard: `false`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache“

- Erfordert einen Wert


## `store:list`

```bash
bin/magento store:list
```

Zeigt die Liste der Stores an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `store:website:list`

```bash
bin/magento store:website:list
```

Zeigt die Liste der Websites an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Code-Sicherung erstellen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--name`

Dump-Name

- Akzeptiert einen Wert

#### `--output`, `-o`

Ausgabepfad

- Akzeptiert einen Wert

#### `--logs`, `-l`

Protokolle einschließen

- Standard: `false`
- Akzeptiert keinen Wert


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

DB-Backup erstellen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--name`

Dump-Name

- Akzeptiert einen Wert

#### `--output`, `-o`

Ausgabepfad

- Akzeptiert einen Wert

#### `--logs`, `-l`

Protokolle einschließen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--ignore-sanitize`, `-i`

Bereinigen ignorieren

- Standard: `false`
- Akzeptiert keinen Wert


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Überprüfen der erforderlichen Backup-Dienstprogramme

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--hide-paths`

Nur erforderliche Konsolendienstprogramme überprüfen

- Standard: `false`
- Akzeptiert keinen Wert


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Erstellen der Liste der Dienstprogrammpfade

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

erzwingen

- Standard: `false`
- Akzeptiert keinen Wert


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Deinstalliert ein Design

### Argumente

#### `theme`

Pfad des Designs. Der Designpfad sollte als vollständiger Pfad angegeben werden, der „area/provider/name“ lautet. Beispiel: frontend/Magento/blank

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--backup-code`

Code-Backup erstellen (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen.

- Standard: `false`
- Akzeptiert keinen Wert


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Erzeugt VCL-Lackierung und überträgt sie an die Befehlszeile

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--access-list`

IP-Zugriffsliste, die Varnish löschen kann

- Standard: `localhost`
- Erfordert einen Wert

#### `--backend-host`

Host des Web-Backends

- Standard: `localhost`
- Erfordert einen Wert

#### `--backend-port`

Port des Web-Backends

- Standard: `8080`
- Erfordert einen Wert

#### `--export-version`

Die Version der Lackdatei

- Standard: `6`
- Erfordert einen Wert

#### `--grace-period`

Übergangsphase in Sekunden

- Standard: `300`
- Erfordert einen Wert

#### `--input-file`

Eingabedatei, aus der die VCL generiert werden soll

- Erfordert einen Wert

#### `--output-file`

Pfad zur VCL-Datei

- Erfordert einen Wert


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Führt einen registrierten Webhook zu Entwicklungszwecken aus.

### Argumente

#### `name`

Webhook-Name

- Erforderlich


#### `payload`

Die Webhook-Payload im JSON-Format

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Erstellen von Plug-ins basierend auf Webhook-Registrierungen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Gibt die Payload des angegebenen Webhooks zurück.

### Argumente

#### `webhook-name`

Webhook-Methodenname

- Erforderlich


#### `webhook-type`

Webhook-Typ (vor, nach)

- Standard: `before`

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--depth`

Die Anzahl der zurückzugebenden Ebenen in der Webhook-Payload

- Standard: `3`
- Akzeptiert einen Wert


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Zeigt die Liste der abonnierten Webhooks an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Gibt eine Liste unterstützter Webhook-Methodennamen für das angegebene Modul zurück

### Argumente

#### `module_name`

Modulname

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).
