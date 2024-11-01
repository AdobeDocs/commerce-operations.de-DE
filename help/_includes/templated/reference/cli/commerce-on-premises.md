---
source-git-commit: a8f4df78dfec2a1e94d650cac03c7fba21f398e8
workflow-type: tm+mt
source-wordcount: '8072'
ht-degree: 0%

---
# bin/magento (Adobe Commerce vor Ort)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Version**: 2.4.7-p1

Diese Referenz enthält 141 Befehle, die über das Befehlszeilen-Tool `bin/magento` verfügbar sind.
Die anfängliche Liste wird automatisch mit dem Befehl `bin/magento list` in Adobe Commerce generiert.

## Allgemein

Verwenden Sie die Anleitung &quot;[&quot;CLI-Befehle hinzufügen&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/)&quot;, um einen benutzerdefinierten CLI-Befehl hinzuzufügen.

Sie können `bin/magento` CLI-Befehle mit Shortcuts anstelle des vollständigen Befehlsnamens aufrufen. Sie können beispielsweise `bin/magento setup:upgrade` mit `bin/magento s:up` und `bin/magento s:upg` aufrufen. Informationen zur Verwendung von Tastaturbefehlen mit CLI-Befehlen finden Sie unter [Syntax der Kurzbefehle](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) .

Diese Referenzdokumentation wird aus dem Quellcode der Anwendung generiert. Um die Dokumentation zu ändern, sollten Sie eine Pull-Anfrage für den entsprechenden Befehl im relevanten [Codebase](https://github.com/magento)-Repository öffnen. Weitere Informationen finden Sie unter [Code-Beiträge](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) .

### Globale Optionen

#### `--help`, `-h`

Zeigen Sie Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe zum Listenbefehl angezeigt

- Standard: `false`
- Akzeptiert keinen Wert

#### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Nachrichten: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlerbehebung.

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

Die Option &quot;—ansi&quot;umkehren

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-interaction`, `-n`

Interaktive Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Interner Befehl zum Bereitstellen von Vorschlägen zur Shell-Fertigstellung

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--shell`, `-s`

Der Shell-Typ (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Erfordert einen Wert

#### `--input`, `-i`

Ein Array von Eingabe-Token (z. B. COMP_WORDS oder argv)

- Standard: `[]`
- Erfordert einen Wert

#### `--current`, `-c`

Der Index des &quot;input&quot;-Arrays, in dem sich der Cursor befindet (z. B. COMP_CWORD)

- Erfordert einen Wert

#### `--api-version`, `-a`

Die API-Version des Fertigstellungsskripts

- Erfordert einen Wert

#### `--symfony`, `-S`

veraltet

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

Der Shell-Typ (z. B. &quot;bash&quot;), der Wert der env var &quot;$SHELL&quot; wird verwendet, wenn dies nicht angegeben wird.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--debug`

Fertigstellungs-Debug-Protokoll verfolgen

- Standard: `false`
- Akzeptiert keinen Wert


## `help`

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Hilfe für einen Befehl anzeigen

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

Ausgabe der Rohbefehl-Hilfe

- Standard: `false`
- Akzeptiert keinen Wert


## `list`

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Listen-Befehle

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

So geben Sie die unformatierte Befehlsliste aus

- Standard: `false`
- Akzeptiert keinen Wert

#### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

#### `--short`

Überspringen der Beschreibung der Befehlsargumente

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Deaktivieren des Adobe IMS-Moduls

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Aktivieren Sie das Adobe IMS-Modul.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--organization-id`, `-o`

Legen Sie die Organisations-ID für die Adobe IMS-Konfiguration fest. Erforderlich beim Aktivieren des Moduls

- Akzeptiert einen Wert

#### `--client-id`, `-c`

Legen Sie die Client-ID für die Adobe IMS-Konfiguration fest. Erforderlich beim Aktivieren des Moduls

- Akzeptiert einen Wert

#### `--client-secret`, `-s`

Legen Sie den Client-Geheimnis für die Adobe IMS-Konfiguration fest. Erforderlich beim Aktivieren des Moduls

- Akzeptiert einen Wert

#### `--2fa`, `-t`

Überprüfen Sie, ob 2FA für die Organisation in Adobe Admin Console aktiviert ist. Erforderlich beim Aktivieren des Moduls

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

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Der Benutzername des Administrators zum Entsperren

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Erstellen einer Sicherungskopie der Anwendung

### Argumente

#### `config-types`

Durch Leerzeichen getrennte Liste von Konfigurationstypen oder Auslassungspunkten zum Ablegen aller [Bereiche, Systeme, Designs, i18n]

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Importieren von Daten aus freigegebenen Konfigurationsdateien in den entsprechenden Datenspeicher

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `app:config:status`

```bash
bin/magento app:config:status
```

Prüft, ob für die Konfigurationsübertragung eine Aktualisierung erforderlich ist

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migrieren gespeicherter Karten aus einer Magento 1-Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

Hostname/IP. Port ist optional

- Erfordert einen Wert

#### `--dbname`

Datenbankname

- Erfordert einen Wert

#### `--username`

Datenbank-Benutzername. Muss Lesezugriff haben

- Erfordert einen Wert

#### `--password`

Kennwort

- Erfordert einen Wert


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Bereinigt Cache-Typen

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Deaktiviert Cache-Typen

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Aktiviert Cache-Typen

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Leert Cache-Speicher, der von Cache-Typen verwendet wird

### Argumente

#### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Überprüft den Cache-Status

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Erstellt Größenangepasste Produktbilder

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--async`, `-a`

Bildgröße im asynchronen Modus ändern

- Standard: `false`
- Akzeptiert keinen Wert

#### `--skip_hidden_images`

Verarbeiten Sie keine Bilder, die auf der Produktseite als ausgeblendet markiert sind.

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

Festlegen, ob die Überprüfung von HTML-Inhalten durch den Benutzer erzwungen oder stattdessen eine Warnung angezeigt werden soll

### Argumente

#### `restrict`

y\n

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Vertrauliche Konfigurationswerte festlegen

### Argumente

#### `path`

Konfigurationspfad zum Beispiel für group/section/field_name


#### `value`

Konfigurationswert

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--interactive`, `-i`

Aktivieren Sie den interaktiven Modus zum Festlegen aller sensiblen Variablen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--scope`

Konfigurationsbereich, falls nicht festgelegt, &quot;Standard&quot;verwenden

- Standard: `default`
- Akzeptiert einen Wert

#### `--scope-code`

Code für die Konfiguration, standardmäßig leere Zeichenfolge

- Standard: &quot;
- Akzeptiert einen Wert


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Systemkonfiguration ändern

### Argumente

#### `path`

Konfigurationspfad im Format &quot;section/group/field_name&quot;

- Erforderlich


#### `value`

Konfigurationswert

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--scope`

Konfigurationsbereich (Standard, Website oder Store)

- Standard: `default`
- Erfordert einen Wert

#### `--scope-code`

Code des Umfangs (nur erforderlich, wenn der Umfang nicht &quot;Standard&quot;ist)

- Erfordert einen Wert

#### `--lock-env`, `-e`

Sperrwert, der Änderungen im Admin verhindert (wird unter app/etc/env.php gespeichert)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--lock-config`, `-c`

Sperren und Freigeben von Werten für andere Installationen verhindern Änderungen im Admin (wird unter app/etc/config.php gespeichert)

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

Konfigurationsbereich, falls nicht angegeben, wird der Standardbereich verwendet

- Standard: `default`
- Akzeptiert einen Wert

#### `--scope-code`

Code des Umfangs (nur erforderlich, wenn der Umfang nicht `default` ist)

- Standard: &quot;
- Akzeptiert einen Wert


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Generiert und installiert die Crontab für den aktuellen Benutzer

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Installationsaufgaben erzwingen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--non-optional`, `-d`

Installieren Sie nur die nicht optionalen (Standard-) Aufgaben

- Standard: `false`
- Akzeptiert keinen Wert


## `cron:remove`

```bash
bin/magento cron:remove
```

Entfernt Aufgaben aus der Registerkarte &quot;Crontab&quot;

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

Ausführen von Aufträgen nur aus der angegebenen Gruppe

- Erfordert einen Wert

#### `--exclude-group`

Aufträge aus der angegebenen Gruppe ausschließen

- Standard: `[]`
- Akzeptiert mehrere Werte

#### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap

- Erfordert einen Wert


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Hash des Kunden gemäß dem neuesten Algorithmus aktualisieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Anwendungsmodus festlegen.

### Argumente

#### `mode`

Der festzulegende Anwendungsmodus. Verfügbare Optionen sind &quot;Entwickler&quot;oder &quot;Produktion&quot;

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--skip-compilation`, `-s`

Überspringt das Löschen und Neugenerieren statischer Inhalte (generierter Code, vorverarbeitetes CSS und Assets in pub/static/)

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
bin/magento dev:di:info <class>
```

Enthält Informationen zur Konfiguration der Abhängigkeitsinjizierung für den Befehl.

### Argumente

#### `class`

Klassenname

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Überprüft Newsletter-Vorlagen auf potenzielle Kompatibilitätsprobleme bei der Variablennutzung

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Überschreibungen von E-Mail-Vorlagen auf potenzielle Kompatibilitätsprobleme bei der Variablennutzung scannen

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

Aktivieren der DB-Abfrageprotokollierung

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--include-all-queries`

Protokollieren Sie alle Abfragen. [true\|false]

- Standard: `true`
- Akzeptiert einen Wert

#### `--query-time-threshold`

Zeitschwellen der Abfrage.

- Standard: `0.001`
- Akzeptiert einen Wert

#### `--include-call-stack`

Include call stack. [true\|false]

- Standard: `true`
- Akzeptiert einen Wert


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Erfasst Quelldateien für das Design und veröffentlicht sie.

### Argumente

#### `file`

Vorab zu verarbeitende Dateien (Datei sollte ohne Erweiterung angegeben werden)

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

Deaktivierung von Frontend-Vorlagenhinweisen. Möglicherweise ist eine Cache-Leerung erforderlich.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Aktivieren Sie Frontend-Vorlagenhinweise. Möglicherweise ist eine Cache-Leerung erforderlich.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Status der Frontend-Vorlagenhinweise anzeigen.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Führt Tests aus

### Argumente

#### `type`

Typ des auszuführenden Tests. Verfügbare Typen: all, unit, integration, integration, static, static, static all, integrität, veraltet, Standard

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

Generiert den Katalog von URNs zu *.xsd-Zuordnungen, damit die IDE XML hervorhebt.

### Argumente

#### `path`

Pfad zur Datei, um den Katalog auszugeben. Verwenden Sie für PhpStorm .idea/misc.xml

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--ide`

Format, in dem der Katalog erstellt wird. Unterstützt: [phpstorm, vscode]

- Standard: `phpstorm`
- Erfordert einen Wert


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Konvertiert XML-Dateien mit XSL-Stylesheets

### Argumente

#### `xml-file`

Pfad zur XML-Datei, die umgewandelt werden soll

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

Domänen zur Whitelist für herunterladbare Domänen hinzufügen

### Argumente

#### `domains`

Domänenname

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Entfernen von Domänen aus der Whitelist der herunterladbaren Domänen

### Argumente

#### `domains`

Domänennamen

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Anzeigen einer Whitelist für herunterladbare Domänen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Verschlüsselt verschlüsselte Kreditkartendaten mit dem neuesten Verschlüsselungsschlüssel erneut.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Erstellen Sie einen benutzerdefinierten Ereignisanbieter unter Adobe I/O-Ereignisse für diese Instanz. Wenn Sie die Beschriftungs- und Beschreibungsoptionen nicht angeben, müssen diese in der Datei app/etc/event-types.json des Systems definiert werden.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--label`

Eine Bezeichnung zur Definition Ihres benutzerdefinierten Providers.

- Akzeptiert einen Wert

#### `--description`

Eine Beschreibung Ihres Providers.

- Akzeptiert einen Wert


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Modul basierend auf der Plugin-Liste generieren

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

Zeigt eine Liste der abonnierten Ereignisse an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Gibt eine Liste der abonnierbaren Ereignisse zurück, die im angegebenen Modul definiert sind

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

Gibt Details zum konfigurierten Ereignisanbieter zurück

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

Erzwingt das Abonnieren des angegebenen Ereignisses, selbst wenn es nicht lokal definiert wurde.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--fields`

Die Liste der Felder in der Payload der Ereignisdaten.

- Standard: `[]`
- Erfordert einen Wert

#### `--parent`

Der übergeordnete Ereigniscode für ein Ereignisabonnement mit Regeln.

- Erfordert einen Wert

#### `--rules`

Die Liste der Regeln für das Ereignisabonnement, wobei jede Regel als &quot;field\|operator\|value&quot;formatiert ist.

- Standard: `[]`
- Erfordert einen Wert

#### `--priority`, `-p`

Beschleunigt die Übertragung dieses Ereignisses. Geben Sie diese Option für Ereignisse an, die sofort bereitgestellt werden müssen. Standardmäßig werden Ereignisse einmal pro Minute per Cron gesendet.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--destination`, `-d`

Das Ziel dieses Ereignisses. Geben Sie diese Option für die Ereignisse an, die an das benutzerdefinierte Ziel gesendet werden sollen.

- Standard: `default`
- Erfordert einen Wert

#### `--hipaaAuditRequired`

Zeigt an, dass das Ereignis Daten enthält, die HIPAA-Prüfungen unterliegen.

- Standard: `false`
- Akzeptiert keinen Wert


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Synchronisieren von Ereignismetadaten für diese Instanz

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--delete`, `-d`

Löschen von Ereignismetadaten nicht mehr erforderlich

- Standard: `false`
- Akzeptiert keinen Wert


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Entfernt das Abonnement für das bereitgestellte Ereignis

### Argumente

#### `event-code`

Abmelde-Ereignis-Code

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Erkennt Ausdrücke in der Codebase

### Argumente

#### `directory`

Pfad zum Analysieren. Nicht erforderlich, wenn die Markierung —magento gesetzt ist

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--output`, `-o`

Pfad (einschließlich Dateiname) zu einer Ausgabedatei. Wenn keine Datei angegeben ist, wird standardmäßig stdout verwendet.

- Erfordert einen Wert

#### `--magento`, `-m`

Verwenden Sie den Parameter —magento , um die aktuelle Magento-Codebase zu analysieren. Lassen Sie den Parameter aus, wenn ein Verzeichnis angegeben ist.

- Standard: `false`
- Akzeptiert keinen Wert


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Speichert das Sprachpaket

### Argumente

#### `source`

Pfad zur Quellwörterbuchdatei mit Übersetzungen

- Erforderlich


#### `locale`

Zielgebietsschema für Wörterbücher, z. B. &quot;de_DE&quot;

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--mode`, `-m`

Speichermodus für Wörterbuch - &quot;Ersetzen&quot;- Sprachpaket durch neues ersetzen - &quot;Zusammenführen&quot;- Sprachpakete zusammenführen, standardmäßig &quot;Ersetzen&quot;

- Standard: `replace`
- Erfordert einen Wert

#### `--allow-duplicates`, `-d`

Verwenden Sie den Parameter —allow-duplicates , um das Speichern von Dubletten der Übersetzung zu ermöglichen. Lassen Sie andernfalls den Parameter weg.

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

Sichern von Code- und Konfigurationsdateien (ohne temporäre Dateien)

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

Neuindizierung von Daten

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Setzt den Indexstatus auf ungültig zurück

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Indexer-Dimensionen-Modus festlegen

### Argumente

#### `indexer`

Indexername [catalog_product_price|catalogpermissions_category]


#### `mode`

Indexer-Dimensionsmodi catalog_product_price          none,website,customer_group,website_and_customer_group catalogpermissions_category    none,customer_group

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Legt den Indexmodustyp fest

### Argumente

#### `mode`

Indexermodustyp [realtime|schedule]


#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Legt den angegebenen Indexstatus fest

### Argumente

#### `status`

Indexerstatustyp [invalid|suspen|valid]

- Erforderlich


#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

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

Durch Leerzeichen getrennte Liste von Indextypen oder Unterlassen der Anwendung auf alle Indizes (catalog_product_price,catalogpermissions_category)

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

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Zeigt den Status des Indexers

### Argumente

#### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

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

Zeigt die Liste der verfügbaren Zeitzonen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Erstellen von Vorbehalten aus den vorgelegten Ausgleichsargumenten

### Argumente

#### `compensations`

Liste der Ausgleichsargumente im Format &quot;:::&quot;

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

Alle Bestellungen und Produkte mit Inkonsistenzen bei der Verkaufsmenge anzeigen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--complete-orders`, `-c`

Nur Inkonsistenzen für vollständige Bestellungen anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--incomplete-orders`, `-i`

Nur Inkonsistenzen für unvollständige Bestellungen anzeigen

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

Herunterladen und Importieren von Geo-Namen für den Quellauswahlalgorithmus

### Argumente

#### `countries`

Liste der zu importierenden Ländercodes

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Legt IPs ohne Wartungsmodus fest

### Argumente

#### `ip`

Zulässige IP-Adressen

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--none`

Löschen zulässiger IP-Adressen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--add`

Hinzufügen der IP-Adresse zur vorhandenen Liste

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Deaktiviert den Wartungsmodus

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--ip`

Zulässige IP-Adressen (verwenden Sie &quot;Keine&quot;, um die zulässige IP-Liste zu löschen)

- Standard: `[]`
- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Aktiviert den Wartungsmodus

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--ip`

Zulässige IP-Adressen (verwenden Sie &quot;Keine&quot;, um die zulässige IP-Liste zu löschen)

- Standard: `[]`
- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Zeigt den Status des Wartungsmodus an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Inhalt mit Assets synchronisieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Synchronisieren von Medienspeichern und Medien-Assets in der Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `module:config:status`

```bash
bin/magento module:config:status
```

Prüft die Modulkonfiguration in der Datei &quot;app/etc/config.php&quot;und meldet, ob sie aktuell ist oder nicht

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Deaktiviert angegebene Module

### Argumente

#### `module`

Name des Moduls

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Prüfung von Abhängigkeiten umgehen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--all`

Alle Module deaktivieren

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Löschen Sie die generierten statischen Ansichtsdateien. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Aktiviert die angegebenen Module

### Argumente

#### `module`

Name des Moduls

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Prüfung von Abhängigkeiten umgehen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--all`

Alle Module aktivieren

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Löschen Sie die generierten statischen Ansichtsdateien. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Status der Module anzeigen

### Argumente

#### `module-names`

Optionaler Modulname

- Standard: `[]`
- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--enabled`

Schreibgeschützte Module

- Standard: `false`
- Akzeptiert keinen Wert

#### `--disabled`

Nur deaktivierte Module drucken

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Deinstalliert die vom Composer installierten Module

### Argumente

#### `module`

Name des Moduls

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--remove-data`, `-r`

Von Modulen installierte Daten entfernen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--backup-code`

Sichern von Code- und Konfigurationsdateien (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--backup-media`

Mediensicherung durchführen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--backup-db`

Führen Sie eine vollständige Datenbanksicherung durch

- Standard: `false`
- Akzeptiert keinen Wert

#### `--non-composer`

Alle Module, die hier vorbei sein werden, sind nicht auf Composer basiert

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Löschen Sie die generierten statischen Ansichtsdateien. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Überprüfen Sie die Bereitstellungswarteschlange auf Einträge und erstellen Sie eine entsprechende Bereitstellungsmarkierung.

### Argumente

#### `message`

Nachricht bereitstellen?

- Erforderlich


#### `change_log`

Änderungsprotokoll

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

MessageQueue Consumer starten

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

Die Anzahl der Nachrichten, die vom Verbraucher vor der Beendigung des Vorgangs verarbeitet werden. Wenn nicht angegeben - beenden Sie nach der Verarbeitung aller in die Warteschlange gestellten Nachrichten.

- Erfordert einen Wert

#### `--batch-size`

Die Anzahl der Nachrichten pro Batch. Gilt nur für den Batch-Verbraucher.

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

Mediendateien mit Remote-Speicher synchronisieren.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

Synchronisiert Feed-Daten erneut mit dem SaaS-Dienst.

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--feed`

Feed-Name zur vollständigen erneuten Synchronisierung mit dem SaaS-Dienst. Verfügbare Feeds: Payment Services Order Production, Payment Services Order Sandbox, Payment Services Order Status Production, Payment Services Order Status Sandbox, Payment Services Order Status Sandbox, Payment Services Store Production, Payment Services Store Sandbox

- Erfordert einen Wert

#### `--no-reindex`

Führen Sie die erneute Übermittlung von Feed-Daten nur an den SaaS-Dienst aus. Indexiert nicht neu. (Diese Option gilt nicht für die Produkte, Produktoverride und Preisfeeds.)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--cleanup-feed`

Feed-Indexertabelle vor der Synchronisierung bereinigen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--dry-run`

Probieren Sie aus. Daten werden nicht exportiert. Zum Speichern der Nutzlast in die Protokolldatei var/log/saas-export.log mit der env-Variablen EXPORTER_EXTENDED_LOG=1 ausführen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--thread-count`

Legen Sie die Anzahl der Synchronisierungs-Threads fest.

- Erfordert einen Wert

#### `--batch-size`

Stapelgröße für die Synchronisierung festlegen

- Erfordert einen Wert

#### `--continue-resync`

Fortsetzen der Synchronisierung von der letzten gespeicherten Position (diese Option gilt für die Produkte, Produktoverrides und Preise-Feeds)

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Bereitstellen von Beispieldatenmodulen für Composer-basierte Magento-Installationen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--no-update`

Aktualisieren von Composer.json ohne Ausführen der Komponentenaktualisierung

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Entfernen Sie alle Beispieldatenpakete aus Composer.json

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--no-update`

Aktualisieren von Composer.json ohne Ausführen der Komponentenaktualisierung

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

Deaktivieren Sie reCAPTCHA für das Formular für vergessene Administratorrechte

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Deaktivieren Sie reCAPTCHA für das Anmeldeformular für Administratoren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Legen Sie das für die OTP-Generierung von Google verwendete Geheimnis fest.

### Argumente

#### `user`

Benutzername

- Erforderlich


#### `secret`

Geheimnis

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

Provider-Code

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Anwendungsserver ausführen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--port`, `-p`

Anschluss an Server

- Standard: `9501`
- Akzeptiert einen Wert

#### `--background`, `-b`

Hintergrundmodus-Markierung

- Standard: `0`
- Akzeptiert einen Wert

#### `--workerNum`, `-wn`

Anzahl der zu startenden Arbeitsprozesse

- Standard: `4`
- Akzeptiert einen Wert

#### `--dispatchMode`, `-dm`

Modus zum Senden von Verbindungen zu den Worker-Prozessen

- Standard: `3`
- Akzeptiert einen Wert

#### `--maxRequests`, `-mr`

Maximale Anforderungen vor dem Neustart des Worker-Prozesses

- Standard: `10000`
- Akzeptiert einen Wert

#### `--area`, `-a`

Anwendungsserverbereich

- Standard: `graphql`
- Akzeptiert einen Wert

#### `--magento-init-params`, `-mip`

magento bootstrap init params

- Standard: &quot;
- Akzeptiert einen Wert

#### `--maxWaitTime`, `-mwt`

wie lange es nach dem Neuladen auf Arbeitnehmer warten kann (z. B. Konfigurationsänderung) vor dem Töten

- Standard: `3600`
- Akzeptiert einen Wert

#### `--state-monitor`

Aktivieren Sie die Statusüberwachung. Verwenden Sie dies nur zum Debuggen von Statusproblemen!

- Standard: `false`
- Akzeptiert keinen Wert


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Aggregierte Ausgabe aus der Statusüberwachung von ApplicationServer

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Backup von Magento Application Code-Basis, Medien und Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--code`

Sichern von Code- und Konfigurationsdateien (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--media`

Mediensicherung durchführen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--db`

Führen Sie eine vollständige Datenbanksicherung durch

- Standard: `false`
- Akzeptiert keinen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:config:set`

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Erstellt oder ändert die Bereitstellungskonfiguration

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--enable-debug-logging`

Debug-Protokollierung aktivieren

- Erfordert einen Wert

#### `--enable-syslog-logging`

Aktivieren der syslog-Protokollierung

- Erfordert einen Wert

#### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)

- Erfordert einen Wert

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

Remote-Speicherbehälter

- Erfordert einen Wert

#### `--remote-storage-region`

Remote-Speicherregion

- Erfordert einen Wert

#### `--remote-storage-key`

Zugriffsschlüssel für Remote-Speicher

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-secret`

geheimer Schlüssel für Remote-Speicher

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-path-style`

Pfad für Remote-Speicher - Stil

- Standard: `0`
- Erfordert einen Wert

#### `--id_salt`

GraphQl-Salz

- Erfordert einen Wert

#### `--config-async`

Asynchrone Admin Config-Speicherung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--checkout-async`

Asynchrone Auftragsverarbeitung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--amqp-host`

AMQP-Server-Host

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-port`

AMQP-Server-Anschluss

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

Amqp virtualhost

- Standard: `/`
- Erfordert einen Wert

#### `--amqp-ssl`

AMQP SSL

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-ssl-options`

AMQP-SSL-Optionen (JSON)

- Standard: &quot;
- Erfordert einen Wert

#### `--consumers-wait-for-messages`

Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--queue-default-connection`

Die Standardverbindung der Nachrichtenwarteschlangen wird festgelegt. Kann &#39;db&#39;, &#39;amqp&#39; oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert sein, andernfalls werden Nachrichten nicht korrekt verarbeitet.

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

Benutzername des Datenbankservers

- Erfordert einen Wert

#### `--db-engine`

Datenbank-Server-Engine

- Erfordert einen Wert

#### `--db-password`

Datenbankserver-Kennwort

- Erfordert einen Wert

#### `--db-prefix`

Datenbanktabellenpräfix

- Erfordert einen Wert

#### `--db-model`

Datenbanktyp

- Erfordert einen Wert

#### `--db-init-statements`

Grundmenge an Befehlen in der Datenbank

- Erfordert einen Wert

#### `--skip-db-validation`, `-s`

Wenn angegeben, wird die Überprüfung der db-Verbindung übersprungen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--http-cache-hosts`

HTTP-Cache-Hosts

- Erfordert einen Wert

#### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-ca`

Vollständiger Pfad der Datei mit dem Serverzertifikat, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-verify`

Serverzertifizierung überprüfen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--session-save`

Sitzungsspeicherhandler

- Erfordert einen Wert

#### `--session-save-redis-host`

Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets

- Erfordert einen Wert

#### `--session-save-redis-port`

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--session-save-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--session-save-redis-timeout`

Zeitüberschreitung bei Verbindung in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen

- Erfordert einen Wert

#### `--session-save-redis-db`

Rediv-Datenbanknummer

- Erfordert einen Wert

#### `--session-save-redis-compression-threshold`

Schwelle für Rediv-Komprimierung

- Erfordert einen Wert

#### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy

- Erfordert einen Wert

#### `--session-save-redis-log-level`

Redis log level. Werte: 0 (am wenigsten ausführlich) bis 7 (am ausführlichsten)

- Erfordert einen Wert

#### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperrung einer Sitzung warten können

- Erfordert einen Wert

#### `--session-save-redis-break-after-frontend`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, ein Schloss für die Frontend-Sitzung zu brechen

- Erfordert einen Wert

#### `--session-save-redis-break-after-adminhtml`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, eine Sperre für die Admin-Sitzung zu unterbrechen

- Erfordert einen Wert

#### `--session-save-redis-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Nicht-Bots beim ersten Schreiben (verwenden Sie 0, um zu deaktivieren)

- Erfordert einen Wert

#### `--session-save-redis-bot-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Bots beim ersten Schreiben (verwenden Sie 0 zur Deaktivierung)

- Erfordert einen Wert

#### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (verwenden Sie 0 zur Deaktivierung)

- Erfordert einen Wert

#### `--session-save-redis-disable-locking`

Redis deaktivieren die Sperrung. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-min-lifetime`

Redis min session lifetime in seconds

- Erfordert einen Wert

#### `--session-save-redis-max-lifetime`

Gibt die maximale Sitzungslebensdauer in Sekunden zurück.

- Erfordert einen Wert

#### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Erfordert einen Wert

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommas getrennt

- Erfordert einen Wert

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verify master. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel Connect-Neuversuche.

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

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--cache-backend-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--cache-backend-redis-compress-data`

Auf 0 setzen, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

#### `--cache-backend-redis-compression-lib`

Komprimierungs-Lib zur Verwendung von [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--cache-backend-redis-use-lua`

Auf 1 setzen, um lua zu aktivieren (Standard ist 0, deaktiviert)

- Erfordert einen Wert

#### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--allow-parallel-generation`

Cache nicht blockieren lassen

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

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--page-cache-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--page-cache-redis-compress-data`

Auf 1 setzen, um den gesamten Seiten-Cache zu komprimieren (verwenden Sie 0, um ihn zu deaktivieren)

- Erfordert einen Wert

#### `--page-cache-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung von [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--lock-provider`

Name des Anbieters sperren

- Erfordert einen Wert

#### `--lock-db-prefix`

Installation-spezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten

- Erfordert einen Wert

#### `--lock-zookeeper-host`

Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster. Beispiel: 127.0.0.1:2181

- Erfordert einen Wert

#### `--lock-zookeeper-path`

Der Pfad, in dem Zookeeper Sperren speichert. Der Standardpfad lautet: /magento/lock

- Erfordert einen Wert

#### `--lock-file-path`

Der Pfad, in dem Dateisperren gespeichert werden.

- Erfordert einen Wert

#### `--document-root-is-pub`

Flag zum Anzeigen, ob Pub sich auf dem Stamm befindet, kann nur &quot;true&quot;oder &quot;false&quot;sein

- Erfordert einen Wert

#### `--backpressure-logger`

Rückdruckprotokollierer

- Erfordert einen Wert

#### `--backpressure-logger-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--backpressure-logger-redis-port`

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--backpressure-logger-redis-timeout`

Redis server timeout

- Erfordert einen Wert

#### `--backpressure-logger-redis-persistent`

Rediv beständig

- Erfordert einen Wert

#### `--backpressure-logger-redis-db`

Redis db number

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

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installiert und aktualisiert Daten in der DB

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Erstellen Sie einen Patch und legen Sie ihn in einen bestimmten Ordner.

### Argumente

#### `module`

Modulname

- Erforderlich


#### `patch`

Patch name

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--revertable`

Überprüfen Sie, ob der Patch rückgängig gemacht werden kann oder nicht.

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

Generieren einer Whitelist von Tabellen und Spalten, die vom Deklarationinstallationsprogramm bearbeitet werden dürfen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--module-name`

Name des Moduls, für das eine Whitelist generiert wird

- Standard: `all`
- Akzeptiert einen Wert


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Checkout-zifferbezogene Tabellen in einen separaten DB-Server verschieben

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

DB-Server-Host auswählen

- Standard: `localhost`
- Erfordert einen Wert

#### `--dbname`

Slave-Datenbankname

- Erfordert einen Wert

#### `--username`

DB-Benutzername herunterladen

- Standard: `root`
- Erfordert einen Wert

#### `--password`

DB-Benutzerkennwort speichern

- Akzeptiert einen Wert

#### `--connection`

Slave-Verbindungsname

- Standard: `default`
- Akzeptiert einen Wert

#### `--resource`

Slave Resource name

- Standard: `default`
- Akzeptiert einen Wert

#### `--maxAllowedLag`

Max. zulässige Lag-Slave-Verbindung (in Sekunden)

- Standard: &quot;
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verschieben Sie die mit Checkout verbundenen Tabellen an einen separaten DB-Server. Veraltet seit 2.4.2 und wird entfernt

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

Checkout für DB Server-Host

- Erfordert einen Wert

#### `--dbname`

Checkout-Datenbankname

- Erfordert einen Wert

#### `--username`

Checkout DB-Benutzername

- Erfordert einen Wert

#### `--password`

DB-Benutzerkennwort auschecken

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

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verschieben Sie umsatzbezogene Tabellen auf einen separaten DB-Server. Veraltet seit 2.4.2 und wird entfernt

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--host`

Sales DB Server-Host

- Erfordert einen Wert

#### `--dbname`

Name der Verkaufsdatenbank

- Erfordert einen Wert

#### `--username`

Name des DB-Vertriebsbenutzers

- Erfordert einen Wert

#### `--password`

Benutzerpasswort von Sales DB

- Akzeptiert einen Wert

#### `--connection`

Name der Verkaufsverbindung

- Standard: `sales`
- Akzeptiert einen Wert

#### `--resource`

Name der Verkaufsressource

- Standard: `sales`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installation und Aktualisierung des DB-Schemas

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--convert-old-scripts`

Konvertiert alte Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Prüft, ob ein DB-Schema oder Daten aktualisiert werden muss

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Generiert ID-Konfiguration und alle fehlenden Klassen, die automatisch generiert werden können

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `setup:install`

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installation der Magento-Anwendung

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--enable-debug-logging`

Debug-Protokollierung aktivieren

- Erfordert einen Wert

#### `--enable-syslog-logging`

Aktivieren der syslog-Protokollierung

- Erfordert einen Wert

#### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)

- Erfordert einen Wert

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

Remote-Speicherbehälter

- Erfordert einen Wert

#### `--remote-storage-region`

Remote-Speicherregion

- Erfordert einen Wert

#### `--remote-storage-key`

Zugriffsschlüssel für Remote-Speicher

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-secret`

geheimer Schlüssel für Remote-Speicher

- Standard: &quot;
- Erfordert einen Wert

#### `--remote-storage-path-style`

Pfad für Remote-Speicher - Stil

- Standard: `0`
- Erfordert einen Wert

#### `--id_salt`

GraphQl-Salz

- Erfordert einen Wert

#### `--config-async`

Asynchrone Admin Config-Speicherung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--checkout-async`

Asynchrone Auftragsverarbeitung aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--amqp-host`

AMQP-Server-Host

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-port`

AMQP-Server-Anschluss

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

Amqp virtualhost

- Standard: `/`
- Erfordert einen Wert

#### `--amqp-ssl`

AMQP SSL

- Standard: &quot;
- Erfordert einen Wert

#### `--amqp-ssl-options`

AMQP-SSL-Optionen (JSON)

- Standard: &quot;
- Erfordert einen Wert

#### `--consumers-wait-for-messages`

Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein

- Erfordert einen Wert

#### `--queue-default-connection`

Die Standardverbindung der Nachrichtenwarteschlangen wird festgelegt. Kann &#39;db&#39;, &#39;amqp&#39; oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert sein, andernfalls werden Nachrichten nicht korrekt verarbeitet.

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

Benutzername des Datenbankservers

- Erfordert einen Wert

#### `--db-engine`

Datenbank-Server-Engine

- Erfordert einen Wert

#### `--db-password`

Datenbankserver-Kennwort

- Erfordert einen Wert

#### `--db-prefix`

Datenbanktabellenpräfix

- Erfordert einen Wert

#### `--db-model`

Datenbanktyp

- Erfordert einen Wert

#### `--db-init-statements`

Grundmenge an Befehlen in der Datenbank

- Erfordert einen Wert

#### `--skip-db-validation`, `-s`

Wenn angegeben, wird die Überprüfung der db-Verbindung übersprungen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--http-cache-hosts`

HTTP-Cache-Hosts

- Erfordert einen Wert

#### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-ca`

Vollständiger Pfad der Datei mit dem Serverzertifikat, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

#### `--db-ssl-verify`

Serverzertifizierung überprüfen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--session-save`

Sitzungsspeicherhandler

- Erfordert einen Wert

#### `--session-save-redis-host`

Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets

- Erfordert einen Wert

#### `--session-save-redis-port`

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--session-save-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--session-save-redis-timeout`

Zeitüberschreitung bei Verbindung in Sekunden

- Erfordert einen Wert

#### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen

- Erfordert einen Wert

#### `--session-save-redis-db`

Rediv-Datenbanknummer

- Erfordert einen Wert

#### `--session-save-redis-compression-threshold`

Schwelle für Rediv-Komprimierung

- Erfordert einen Wert

#### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy

- Erfordert einen Wert

#### `--session-save-redis-log-level`

Redis log level. Werte: 0 (am wenigsten ausführlich) bis 7 (am ausführlichsten)

- Erfordert einen Wert

#### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperrung einer Sitzung warten können

- Erfordert einen Wert

#### `--session-save-redis-break-after-frontend`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, ein Schloss für die Frontend-Sitzung zu brechen

- Erfordert einen Wert

#### `--session-save-redis-break-after-adminhtml`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, eine Sperre für die Admin-Sitzung zu unterbrechen

- Erfordert einen Wert

#### `--session-save-redis-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Nicht-Bots beim ersten Schreiben (verwenden Sie 0, um zu deaktivieren)

- Erfordert einen Wert

#### `--session-save-redis-bot-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Bots beim ersten Schreiben (verwenden Sie 0 zur Deaktivierung)

- Erfordert einen Wert

#### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (verwenden Sie 0 zur Deaktivierung)

- Erfordert einen Wert

#### `--session-save-redis-disable-locking`

Redis deaktivieren die Sperrung. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-min-lifetime`

Redis min session lifetime in seconds

- Erfordert einen Wert

#### `--session-save-redis-max-lifetime`

Gibt die maximale Sitzungslebensdauer in Sekunden zurück.

- Erfordert einen Wert

#### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Erfordert einen Wert

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommas getrennt

- Erfordert einen Wert

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verify master. Werte: false (Standard), true

- Erfordert einen Wert

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel Connect-Neuversuche.

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

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--cache-backend-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--cache-backend-redis-compress-data`

Auf 0 setzen, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

#### `--cache-backend-redis-compression-lib`

Komprimierungs-Lib zur Verwendung von [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--cache-backend-redis-use-lua`

Auf 1 setzen, um lua zu aktivieren (Standard ist 0, deaktiviert)

- Erfordert einen Wert

#### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--allow-parallel-generation`

Cache nicht blockieren lassen

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

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--page-cache-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

#### `--page-cache-redis-compress-data`

Auf 1 setzen, um den gesamten Seiten-Cache zu komprimieren (verwenden Sie 0, um ihn zu deaktivieren)

- Erfordert einen Wert

#### `--page-cache-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung von [snappy,lzf,l4z,zstd,gzip] (leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

#### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

#### `--lock-provider`

Name des Anbieters sperren

- Erfordert einen Wert

#### `--lock-db-prefix`

Installation-spezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten

- Erfordert einen Wert

#### `--lock-zookeeper-host`

Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster. Beispiel: 127.0.0.1:2181

- Erfordert einen Wert

#### `--lock-zookeeper-path`

Der Pfad, in dem Zookeeper Sperren speichert. Der Standardpfad lautet: /magento/lock

- Erfordert einen Wert

#### `--lock-file-path`

Der Pfad, in dem Dateisperren gespeichert werden.

- Erfordert einen Wert

#### `--document-root-is-pub`

Flag zum Anzeigen, ob Pub sich auf dem Stamm befindet, kann nur &quot;true&quot;oder &quot;false&quot;sein

- Erfordert einen Wert

#### `--backpressure-logger`

Rückdruckprotokollierer

- Erfordert einen Wert

#### `--backpressure-logger-redis-server`

Redis-Server

- Erfordert einen Wert

#### `--backpressure-logger-redis-port`

Überwachungsanschluss des Redis-Servers

- Erfordert einen Wert

#### `--backpressure-logger-redis-timeout`

Redis server timeout

- Erfordert einen Wert

#### `--backpressure-logger-redis-persistent`

Rediv beständig

- Erfordert einen Wert

#### `--backpressure-logger-redis-db`

Redis db number

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

Standardsprachencode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code

- Erfordert einen Wert

#### `--timezone`

Standardmäßiger Zeitzonen-Code. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone

- Erfordert einen Wert

#### `--currency`

Standardwährungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow

- Erfordert einen Wert

#### `--use-rewrites`

Verwenden Sie Neuschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites

- Erfordert einen Wert

#### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend

- Erfordert einen Wert

#### `--base-url-secure`

Basis-URL für SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url

- Erfordert einen Wert

#### `--use-secure-admin`

Führen Sie die Admin-Oberfläche mit SSL aus. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml

- Erfordert einen Wert

#### `--admin-use-security-key`

Gibt an, ob eine Funktion des Typs &quot;Sicherheitsschlüssel&quot;in Magento-Admin-URLs und -Formularen verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key .

- Erfordert einen Wert

#### `--admin-user`

Admin-Benutzer

- Akzeptiert einen Wert

#### `--admin-password`

Administratorkennwort

- Akzeptiert einen Wert

#### `--admin-email`

Admin-E-Mail

- Akzeptiert einen Wert

#### `--admin-firstname`

Vorname des Administrators

- Akzeptiert einen Wert

#### `--admin-lastname`

Nachname des Administrators

- Akzeptiert einen Wert

#### `--search-engine`

Suchmaschine. Werte: elasticsearch7, elasticsearch8, opensearch

- Erfordert einen Wert

#### `--elasticsearch-host`

Elasticsearch-Server-Host.

- Erfordert einen Wert

#### `--elasticsearch-port`

Elasticsearch-Server-Anschluss.

- Erfordert einen Wert

#### `--elasticsearch-enable-auth`

Auf 1 setzen, um die Authentifizierung zu aktivieren. (Standardwert ist 0, deaktiviert)

- Erfordert einen Wert

#### `--elasticsearch-username`

Benutzername des Elasticsearchs. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--elasticsearch-password`

Passwort des Elasticsearchs. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--elasticsearch-index-prefix`

Elasticsearch-Indexpräfix.

- Erfordert einen Wert

#### `--elasticsearch-timeout`

Zeitüberschreitung des Elasticsearch-Servers.

- Erfordert einen Wert

#### `--opensearch-host`

OpenSearch-Server-Host.

- Erfordert einen Wert

#### `--opensearch-port`

OpenSearch-Serveranschluss.

- Erfordert einen Wert

#### `--opensearch-enable-auth`

Auf 1 setzen, um die Authentifizierung zu aktivieren. (Standardwert ist 0, deaktiviert)

- Erfordert einen Wert

#### `--opensearch-username`

OpenSearch-Benutzername. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--opensearch-password`

OpenSearch-Kennwort. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

#### `--opensearch-index-prefix`

OpenSearch-Indexpräfix.

- Erfordert einen Wert

#### `--opensearch-timeout`

OpenSearch-Server-Timeout.

- Erfordert einen Wert

#### `--cleanup-database`

Bereinigen der Datenbank vor der Installation

- Standard: `false`
- Akzeptiert keinen Wert

#### `--sales-order-increment-prefix`

Präfix der Bestellnummer

- Erfordert einen Wert

#### `--use-sample-data`

Beispieldaten verwenden

- Standard: `false`
- Akzeptiert keinen Wert

#### `--enable-modules`

Liste mit kommagetrennten Modulnamen. Dies muss während der Installation enthalten sein. Verfügbarer Zauberparam &quot;all&quot;.

- Akzeptiert einen Wert

#### `--disable-modules`

Liste mit kommagetrennten Modulnamen. Dies muss während der Installation vermieden werden. Verfügbarer Zauberparam &quot;all&quot;.

- Akzeptiert einen Wert

#### `--convert-old-scripts`

Konvertiert alte Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

#### `--interactive`, `-i`

Interaktive Magento-Installation

- Standard: `false`
- Akzeptiert keinen Wert

#### `--safe-mode`

Sichere Installation von Magento mit Dumps auf destruktiven Vorgängen, z. B. Spaltenentfernung

- Akzeptiert einen Wert

#### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps

- Akzeptiert einen Wert

#### `--dry-run`

Magento-Installation wird im Trockenlaufmodus ausgeführt

- Standard: `false`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Generiert Fehlerbehebungen

### Argumente

#### `profile`

Pfad zur Profilkonfigurationsdatei

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--skip-reindex`, `-s`

Neuindizierung überspringen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Zurücksetzen der Magento Application Codebase, des Mediums und der Datenbank

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--code-file`, `-c`

Name der Code-Sicherungsdatei in var/backup

- Erfordert einen Wert

#### `--media-file`, `-m`

Name der Mediensicherungsdatei in var/backup

- Erfordert einen Wert

#### `--db-file`, `-d`

Name der Datenbanksicherungsdatei in var/backup

- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Bereitstellen von Dateien in einem beliebigen Modus.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--strategy`, `-s`

Stellen Sie Dateien mithilfe der angegebenen Strategie bereit.

- Standard: `quick`
- Akzeptiert einen Wert

#### `--area`, `-a`

Generieren Sie Dateien nur für die angegebenen Bereiche.

- Standard: `all`
- Akzeptiert mehrere Werte

#### `--exclude-area`

Generieren Sie keine Dateien für die angegebenen Bereiche.

- Standard: `none`
- Akzeptiert mehrere Werte

#### `--theme`, `-t`

Generieren Sie statische Ansichtsdateien nur für die angegebenen Designs.

- Standard: `all`
- Akzeptiert mehrere Werte

#### `--exclude-theme`

Generieren Sie keine Dateien für die angegebenen Designs.

- Standard: `none`
- Akzeptiert mehrere Werte

#### `--language`, `-l`

Generieren Sie Dateien nur für die angegebenen Sprachen.

- Standard: `all`
- Akzeptiert mehrere Werte

#### `--exclude-language`

Generieren Sie keine Dateien für die angegebenen Sprachen.

- Standard: `none`
- Akzeptiert mehrere Werte

#### `--jobs`, `-j`

Aktivieren Sie die parallele Verarbeitung mit der angegebenen Anzahl von Aufträgen.

- Standard: `0`
- Akzeptiert einen Wert

#### `--max-execution-time`

Die maximal erwartete Ausführungszeit des statischen Bereitstellungsprozesses (in Sekunden).

- Standard: `900`
- Akzeptiert einen Wert

#### `--symlink-locale`

Erstellen Sie Symlinks für die Dateien dieser Gebietsschemas, die zur Bereitstellung übergeben werden, aber keine Anpassungen aufweisen.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--content-version`

Benutzerdefinierte Version von statischem Inhalt kann verwendet werden, wenn die Bereitstellung auf mehreren Knoten ausgeführt wird, um sicherzustellen, dass die statische Inhaltsversion identisch ist und die Zwischenspeicherung ordnungsgemäß funktioniert.

- Erfordert einen Wert

#### `--refresh-content-version-only`

Das Aktualisieren der Version statischer Inhalte kann nur verwendet werden, um statische Inhalte im Browser-Cache und CDN-Cache zu aktualisieren.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-javascript`

Stellen Sie keine JavaScript-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-js-bundle`

Stellen Sie keine JavaScript-Bundle-Dateien bereit.

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

Stellen Sie keine Bilder bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-fonts`

Stellen Sie keine Schriftartdateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-html`

Stellen Sie keine HTML-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-misc`

Stellen Sie keine Dateien anderer Typen (.md, .jbf, .csv usw.) bereit.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-html-minify`

Minimieren Sie keine HTML-Dateien.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--no-parent`

Kompilieren Sie keine übergeordneten Designs. Wird nur in schnellen und standardmäßigen Strategien unterstützt.

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installiert die Store-Konfiguration. Seit 2.2.0 veraltet. Verwenden Sie stattdessen config:set

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--base-url`

URL, unter der der Store verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url

- Erfordert einen Wert

#### `--language`

Standardsprachencode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code

- Erfordert einen Wert

#### `--timezone`

Standardmäßiger Zeitzonen-Code. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone

- Erfordert einen Wert

#### `--currency`

Standardwährungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow

- Erfordert einen Wert

#### `--use-rewrites`

Verwenden Sie Neuschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites

- Erfordert einen Wert

#### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend

- Erfordert einen Wert

#### `--base-url-secure`

Basis-URL für SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url

- Erfordert einen Wert

#### `--use-secure-admin`

Führen Sie die Admin-Oberfläche mit SSL aus. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml

- Erfordert einen Wert

#### `--admin-use-security-key`

Gibt an, ob eine Funktion des Typs &quot;Sicherheitsschlüssel&quot;in Magento-Admin-URLs und -Formularen verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key .

- Erfordert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Deinstalliert die Magento-Anwendung

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Erfordert einen Wert


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Magento-Anwendung, DB-Daten und Schema aktualisieren

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--keep-generated`

Verhindert das Löschen generierter Dateien. Wir empfehlen, diese Option nur bei der Bereitstellung in der Produktion zu verwenden. Weitere Informationen erhalten Sie von Ihrem Systemintegrator oder -administrator.

- Standard: `false`
- Akzeptiert keinen Wert

#### `--convert-old-scripts`

Konvertiert alte Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

#### `--safe-mode`

Sichere Installation von Magento mit Dumps auf destruktiven Vorgängen, z. B. Spaltenentfernung

- Akzeptiert einen Wert

#### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps

- Akzeptiert einen Wert

#### `--dry-run`

Magento-Installation wird im Trockenlaufmodus ausgeführt

- Standard: `false`
- Akzeptiert einen Wert

#### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Codesicherung erstellen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--name`

Dump-Name

- Akzeptiert einen Wert

#### `--output`, `-o`

Ausgabepfad

- Akzeptiert einen Wert

#### `--logs`, `-l`

Logs einschließen

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

Logs einschließen

- Standard: `false`
- Akzeptiert keinen Wert

#### `--ignore-sanitize`, `-i`

Ignore sanitize

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

Nur erforderliche Konsolenprogramme überprüfen

- Standard: `false`
- Akzeptiert keinen Wert


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Liste mit Dienstprogrammpfaden erstellen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--force`, `-f`

Stärke

- Standard: `false`
- Akzeptiert keinen Wert


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Deinstalliert das Design

### Argumente

#### `theme`

Pfad des Designs. Der Designpfad sollte als vollständiger Pfad angegeben werden, der sich aus Bereich/Anbieter/Name zusammensetzt. Beispiel: frontend/Magento/blank

- Standard: `[]`
- Erforderlich

- Array

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--backup-code`

Codesicherung durchführen (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

#### `--clear-static-content`, `-c`

Löschen Sie die generierten statischen Ansichtsdateien.

- Standard: `false`
- Akzeptiert keinen Wert


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Generiert Varnish VCL und echnet es an die Befehlszeile

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--access-list`

IP-Zugriffsliste, die &quot;Varnish&quot;bereinigen kann

- Standard: `localhost`
- Erfordert einen Wert

#### `--backend-host`

Host des Web-Backend

- Standard: `localhost`
- Erfordert einen Wert

#### `--backend-port`

Anschluss des Web-Backend

- Standard: `8080`
- Erfordert einen Wert

#### `--export-version`

Die Version der Datei &quot;Varnish&quot;

- Standard: `6`
- Erfordert einen Wert

#### `--grace-period`

Übergangsphase in Sekunden

- Standard: `300`
- Erfordert einen Wert

#### `--input-file`

Eingabedatei, aus der vcl generiert werden soll

- Erfordert einen Wert

#### `--output-file`

Pfad zur Datei, die vcl schreiben soll

- Erfordert einen Wert


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Führt zu Entwicklungszwecken einen registrierten Webhook aus.

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

Generieren von Plug-ins basierend auf Webhook-Registrierungen

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Gibt die Payload des angegebenen Webhooks zurück.

### Argumente

#### `webhook-name`

Name der Webhook-Methode

- Erforderlich


#### `webhook-type`

Webhook-Typ (vor, nach)

- Standard: `before`

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).

#### `--depth`

Die Anzahl der Ebenen in der Webhook-Payload, die zurückgegeben werden sollen

- Standard: `3`
- Akzeptiert einen Wert


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Zeigt eine Liste der abonnierten Webhooks an

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Gibt eine Liste der unterstützten Webhook-Methodennamen für das angegebene Modul zurück

### Argumente

#### `module_name`

Modulname

- Erforderlich

### Optionen

Globale Optionen finden Sie unter [Globale Optionen](#global-options).
