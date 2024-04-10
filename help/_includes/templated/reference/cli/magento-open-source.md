---
source-git-commit: 755ea50a75924cc16f690ff888367abd305565e9
workflow-type: tm+mt
source-wordcount: '18031'
ht-degree: 0%

---
# bin/magento (Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 2.4.7

Diese Referenz enthält 116 Befehle, die über die `bin/magento` Befehlszeilen-Tool.
Die anfängliche Liste wird automatisch mit dem `bin/magento list` Befehl bei Magento Open Source.
Verwenden des [„Hinzufügen von CLI-Befehlen“](https://developer.adobe.com/commerce/php/development/cli-commands/) Anleitung zum Hinzufügen eines benutzerdefinierten CLI-Befehls.

>[!NOTE]
>
>Sie können anrufen `bin/magento` CLI-Befehle mit Tastaturbefehlen anstelle des vollständigen Befehlsnamens. Sie können beispielsweise aufrufen. `bin/magento setup:upgrade` Verwenden von `bin/magento s:up`, `bin/magento s:upg`. Siehe [Shortcut-Syntax](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) , um zu verstehen, wie Tastaturbefehle mit beliebigen CLI-Befehlen verwendet werden.

>[!NOTE]
>
>Dieser Verweis wird aus der Anwendungs-Code-Basis generiert. Um den Inhalt zu ändern, können Sie den Quell-Code für die entsprechende Befehlsimplementierung in der [Codebase](https://github.com/magento) Repository speichern und Ihre Änderungen zur Überprüfung übermitteln. Eine andere Möglichkeit besteht darin, _Geben Sie uns Feedback_ (finden Sie den Link oben rechts). Richtlinien für Beiträge finden Sie unter [Code-Beiträge](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Interner Befehl zur Bereitstellung von Shell-Fertigstellungsvorschlägen

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

Der Schalentyp („bash„, „fish„, „zsh„)

- Erfordert einen Wert

### `--input`, `-i`

Ein Array von Eingabe-Token (z. B. COMP_WORDS oder argv)

- Standard: `[]`
- Erfordert einen Wert

### `--current`, `-c`

Der Index des „Eingabe„-Arrays, in dem sich der Cursor befindet (z. B. COMP_CWORD)

- Erfordert einen Wert

### `--api-version`, `-a`

Die API-Version des Abschlussskripts

- Erfordert einen Wert

### `--symfony`, `-S`

Veraltet

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `completion`

Dump des Shell-Fertigstellungsskripts

```bash
bin/magento completion [--debug] [--] [<shell>]
```


### `shell`

Der Shell-Typ (z. B. „bash„), der Wert der „$SHELL„-Env-Var wird verwendet, wenn dieser nicht angegeben wird


### `--debug`

Verfolgen Sie den Abschluss des Debug-Protokolls

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `help`

Anzeigen der Hilfe zu einem Befehl

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Der Befehlsname

- Standard: `help`


### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

### `--raw`

So geben Sie die Raw-Befehlshilfe aus

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `list`

Befehle auflisten

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

Der Namespace-Name


### `--raw`

So geben Sie die unbearbeitete Befehlsliste aus

- Standard: `false`
- Akzeptiert keinen Wert

### `--format`

Das Ausgabeformat (txt, xml, json oder md)

- Standard: `txt`
- Erfordert einen Wert

### `--short`

So überspringen Sie die Beschreibung der Argumente von Befehlen

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:adobe-ims:disable`

Adobe IMS-Modul deaktivieren

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:adobe-ims:enable`

Aktivieren Sie das Adobe IMS-Modul.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Festlegen der Organisations-ID für die Adobe IMS-Konfiguration. Erforderlich bei Aktivierung des Moduls

- Akzeptiert einen Wert

### `--client-id`, `-c`

Legen Sie die Client-ID für die Adobe IMS-Konfiguration fest. Erforderlich bei Aktivierung des Moduls

- Akzeptiert einen Wert

### `--client-secret`, `-s`

Legen Sie das Client-Geheimnis für die Adobe IMS-Konfiguration fest. Erforderlich bei Aktivierung des Moduls

- Akzeptiert einen Wert

### `--2fa`, `-t`

Überprüfen Sie, ob 2FA für die Organisation in Adobe Admin Console aktiviert ist. Erforderlich bei Aktivierung des Moduls

- Akzeptiert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:adobe-ims:info`

Informationen zur Adobe IMS-Modulkonfiguration

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:adobe-ims:status`

Status des Adobe IMS-Moduls

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:user:create`

Erstellt einen Administrator

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

(Erforderlich) Admin-Benutzer

- Erfordert einen Wert

### `--admin-password`

(Erforderlich) Administratorkennwort

- Erfordert einen Wert

### `--admin-email`

(Erforderlich) Admin-E-Mail

- Erfordert einen Wert

### `--admin-firstname`

(Erforderlich) Vorname des Administrators

- Erfordert einen Wert

### `--admin-lastname`

(Erforderlich) Nachname des Administrators

- Erfordert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `admin:user:unlock`

Admin-Konto entsperren

```bash
bin/magento admin:user:unlock <username>
```


### `username`

Der zu entsperrende Admin-Benutzername

- Erforderlich

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `app:config:dump`

Erstellen eines Dump der Anwendung

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Durch Leerzeichen getrennte Liste von Konfigurationstypen oder Weglassen, um alle zu sichern [Bereiche, System, Themen, i18n]

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `app:config:import`

Importieren von Daten aus freigegebenen Konfigurationsdateien in den entsprechenden Datenspeicher

```bash
bin/magento app:config:import
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `app:config:status`

Prüft, ob die Konfigurationsweitergabe eine Aktualisierung erfordert

```bash
bin/magento app:config:status
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `braintree:migrate`

Migrieren gespeicherter Karten aus einer Magento 1-Datenbank

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

Hostname/IP Port ist optional

- Erfordert einen Wert

### `--dbname`

Datenbankname

- Erfordert einen Wert

### `--username`

Benutzername der Datenbank. Muss Lesezugriff haben

- Erfordert einen Wert

### `--password`

Kennwort

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cache:clean`

Löscht den/die Cache-Typ(en)

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`

- Array

### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cache:disable`

Deaktiviert Cache-Typ(en)

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`

- Array

### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cache:enable`

Aktiviert Cache-Typ(en)

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`

- Array

### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cache:flush`

Leert den von Cache-Typen verwendeten Cache-Speicher

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder eine Auslassung, um sie auf alle Cache-Typen anzuwenden.

- Standard: `[]`

- Array

### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cache:status`

Überprüft den Cache-Status

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `catalog:images:resize`

Erstellt skalierte Produktbilder.

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Ändern der Bildgröße im asynchronen Modus

- Standard: `false`
- Akzeptiert keinen Wert

### `--skip_hidden_images`

Keine Bilder verarbeiten, die auf der Produktseite als ausgeblendet markiert sind

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `catalog:product:attributes:cleanup`

Entfernt nicht verwendete Produktattribute.

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cms:wysiwyg:restrict`

Festlegen, ob die Validierung des Benutzerinhalts durch HTML erzwungen oder stattdessen eine Warnung angezeigt werden soll

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

J\n

- Erforderlich

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `config:sensitive:set`

Festlegen sensibler Konfigurationswerte

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

Konfigurationspfad, z. B. group/section/field_name


### `value`

Konfigurationswert


### `--interactive`, `-i`

Interaktiven Modus aktivieren, um alle sensiblen Variablen festzulegen

- Standard: `false`
- Akzeptiert keinen Wert

### `--scope`

Konfigurationsbereich, falls nicht festgelegt, „Standard“ verwenden

- Standard: `default`
- Akzeptiert einen Wert

### `--scope-code`

Code-Bereich für Konfiguration, standardmäßig leere Zeichenfolge

- Standard: &quot;
- Akzeptiert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `config:set`

Systemkonfiguration ändern

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

Konfigurationspfad im Formatabschnitt/group/field_name

- Erforderlich

### `value`

Konfigurationswert

- Erforderlich

### `--scope`

Konfigurationsumfang (Standard, Website oder Store)

- Standard: `default`
- Erfordert einen Wert

### `--scope-code`

Bereichscode (nur erforderlich, wenn der Bereich nicht „Standard“ ist)

- Erfordert einen Wert

### `--lock-env`, `-e`

Sperrwert, der eine Änderung im Admin verhindert (wird in app/etc/env.php gespeichert)

- Standard: `false`
- Akzeptiert keinen Wert

### `--lock-config`, `-c`

Wert sperren und für andere Installationen freigeben, Änderungen im Admin verhindern (wird in app/etc/config.php gespeichert)

- Standard: `false`
- Akzeptiert keinen Wert

### `--lock`, `-l`

Veraltet, verwenden Sie stattdessen die Option —lock-env .

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `config:show`

Zeigt den Konfigurationswert für den angegebenen Pfad an. Wenn kein Pfad angegeben ist, werden alle gespeicherten Werte angezeigt

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Konfigurationspfad, z. B. section_id/group_id/field_id


### `--scope`

Konfigurationsbereich: Wenn kein Bereich angegeben ist, wird der Standardbereich verwendet.

- Standard: `default`
- Akzeptiert einen Wert

### `--scope-code`

Berechnung des Umfangs (nur erforderlich, wenn der Umfang nicht `default`)

- Standard: &quot;
- Akzeptiert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cron:install`

Erzeugt und installiert crontab für den aktuellen Benutzer

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Installationsaufgaben erzwingen

- Standard: `false`
- Akzeptiert keinen Wert

### `--non-optional`, `-d`

Nur die nicht optionalen (Standard-)Aufgaben installieren

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cron:remove`

Entfernt Aufgaben aus der crontab

```bash
bin/magento cron:remove
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `cron:run`

Führt Aufträge nach Zeitplan aus

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

### `--group`

Aufträge nur von der angegebenen Gruppe ausführen

- Erfordert einen Wert

### `--exclude-group`

Ausschließen von Aufträgen aus der angegebenen Gruppe

- Standard: `[]`
- Akzeptiert mehrere Werte

### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `customer:hash:upgrade`

Aktualisieren des Hash-Werts des Kunden gemäß dem neuesten Algorithmus

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `deploy:mode:set`

Festlegen des Anwendungsmodus

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

Der festzulegende Anwendungsmodus. Verfügbare Optionen sind „Entwickler“ oder „Produktion“

- Erforderlich

### `--skip-compilation`, `-s`

Überspringt das Löschen und die Neuerstellung von statischen Inhalten (generierter Code, vorverarbeitetes CSS und Assets in pub/static/)

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `deploy:mode:show`

Zeigt den aktuellen Anwendungsmodus an.

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:di:info`

Enthält Informationen zur Konfiguration der Injektion von Abhängigkeiten für den Befehl.

```bash
bin/magento dev:di:info <class>
```


### `class`

Klassenname

- Erforderlich

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:email:newsletter-compatibility-check`

Durchsucht Newsletter-Vorlagen nach potenziellen Problemen mit der Variablennutzungskompatibilität

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:email:override-compatibility-check`

Überschreibungen von E-Mail-Vorlagen auf mögliche Kompatibilitätsprobleme bei der Variablennutzung überprüfen

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:profiler:disable`

Deaktivieren Sie den Profiler.

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:profiler:enable`

Aktivieren Sie den Profiler.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Profiltyp


### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:query-log:disable`

DB-Abfrageprotokollierung deaktivieren

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:query-log:enable`

DB-Abfrageprotokollierung aktivieren

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

Alle Abfragen protokollieren. [true\|false]

- Standard: `true`
- Akzeptiert einen Wert

### `--query-time-threshold`

Schwellenwerte für Abfragezeiten.

- Standard: `0.001`
- Akzeptiert einen Wert

### `--include-call-stack`

Aufrufliste einschließen. [true\|false]

- Standard: `true`
- Akzeptiert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:source-theme:deploy`

Sammelt Quelldateien für Designs und veröffentlicht diese.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

Dateien zur Vorab-Bearbeitung (Datei sollte ohne Erweiterung angegeben werden)

- Standard: `css/styles-mcss/styles-l`

- Array

### `--type`

Typ der Quelldateien: [weniger]

- Standard: `less`
- Erfordert einen Wert

### `--locale`

Gebietsschema: [en_US]

- Standard: `en_US`
- Erfordert einen Wert

### `--area`

Bereich: [frontend\|adminHTML]

- Standard: `frontend`
- Erfordert einen Wert

### `--theme`

Design: [Anbieter/Design]

- Standard: `Magento/luma`
- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:template-hints:disable`

Deaktivieren Sie Hinweise zu Frontend-Vorlagen. Möglicherweise ist eine Cache-Leerung erforderlich.

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:template-hints:enable`

Aktivieren Sie Hinweise zu Frontend-Vorlagen. Möglicherweise ist eine Cache-Leerung erforderlich.

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:template-hints:status`

Status der Hinweise zu Frontend-Vorlagen anzeigen.

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:tests:run`

Führt Tests durch

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Typ des auszuführenden Tests. Verfügbare Typen: all, unit, integration, integration-all, static, static-all, integrity, legacy, default

- Standard: `default`


### `--arguments`, `-c`

Zusätzliche Argumente für PHPUnit. Beispiel: „-c&#39;—filter=MyTest&#39;“ (keine Leerzeichen)

- Standard: &quot;
- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:urn-catalog:generate`

Generiert den Katalog der URNs zu *.xsd-Zuordnungen für die IDE zum Hervorheben von XML.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Pfad zur auszugebenden Datei des Katalogs. Verwenden Sie für PhpStorm .idea/misc.xml

- Erforderlich

### `--ide`

Format, in dem der Katalog generiert wird. Unterstützt: [PhpStorm, VSCode]

- Standard: `phpstorm`
- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `dev:xml:convert`

Konvertiert eine XML-Datei mithilfe von XSL-Stylesheets

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

Pfad zur zu transformierenden XML-Datei

- Erforderlich

### `processor`

Pfad zum XSL-Stylesheet, das auf die XML-Datei angewendet werden soll

- Erforderlich

### `--overwrite`, `-o`

XML-Datei überschreiben

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `downloadable:domains:add`

Hinzufügen von Domains zur Whitelist für herunterladbare Domains

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Domain-Name

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `downloadable:domains:remove`

Entfernen von Domains aus der Whitelist für herunterladbare Domains

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Domain-Namen

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `downloadable:domains:show`

Whitelist herunterladbarer Domains anzeigen

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `encryption:payment-data:update`

Verschlüsselt verschlüsselte Kreditkartendaten erneut mit der neuesten Verschlüsselungschiffre.

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `i18n:collect-phrases`

Erkennt Sätze in der Codebasis

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

Zu analysierender Verzeichnispfad. Nicht erforderlich, wenn —magento Flag gesetzt ist


### `--output`, `-o`

Pfad (einschließlich Dateiname) zu einer Ausgabedatei. Wenn keine Datei angegeben ist, wird standardmäßig stdout verwendet.

- Erfordert einen Wert

### `--magento`, `-m`

Verwenden Sie den Parameter —magento, um die aktuelle Magento-Codebasis zu analysieren. Lassen Sie den Parameter weg, wenn ein Verzeichnis angegeben ist.

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `i18n:pack`

Speichert das Sprachpaket

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

Pfad zur Quellwörterbuchdatei mit Übersetzungen

- Erforderlich

### `locale`

Zielgebietsschema für das Wörterbuch, z. B. „de_DE“

- Erforderlich

### `--mode`, `-m`

Speichermodus für Wörterbuch - „replace“ - Sprachpaket durch neues ersetzen - „merge“ - Sprachpakete zusammenführen, standardmäßig „replace“

- Standard: `replace`
- Erfordert einen Wert

### `--allow-duplicates`, `-d`

Verwenden Sie den Parameter —allow-duplicates, um Dubletten der Übersetzung zu speichern. Lassen Sie andernfalls den Parameter weg.

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `i18n:uninstall`

Deinstalliert Sprachpakete

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

Name des Sprachpakets

- Standard: `[]`

- Erforderlich
- Array

### `--backup-code`, `-b`

Code- und Konfigurationsdateien sichern (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:info`

Zeigt zulässige Indexer an

```bash
bin/magento indexer:info
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:reindex`

Daten neu indizieren

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung gilt für alle Indizes.

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:reset`

Setzt den Indexerstatus auf ungültig zurück

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung gilt für alle Indizes.

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:set-dimensions-mode`

Festlegen des Indexermodus für Dimensionen

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Indexername [CATALOG_PRODUCT_PRICE]


### `mode`

Indexerdimensionsmodi catalog_product_price, none, website,customer_group,website_and_customer_group


### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:set-mode`

Legt den Indexmodus-Typ fest

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Indexermodus-Typ [Echtzeit|Zeitplan]


### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung gilt für alle Indizes.

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:set-status`

Legt den angegebenen Indexerstatus fest

```bash
bin/magento indexer:set-status <status> [<index>...]
```


### `status`

Indexerstatustyp [ungültig|ausgesetzt|gültig]

- Erforderlich

### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung gilt für alle Indizes.

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:show-dimensions-mode`

Zeigt den Indexermodus der Dimension an

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung, um sie auf alle Indizes anzuwenden (CATALOG_PRODUCT_PRICE)

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:show-mode`

Zeigt den Indexmodus an

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung gilt für alle Indizes.

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `indexer:status`

Zeigt den Status des Indexers an

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder eine Auslassung gilt für alle Indizes.

- Standard: `[]`

- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:adminuri`

Zeigt den Magento-Admin-URI an

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:backups:list`

Druckt die Liste der verfügbaren Sicherungsdateien

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:currency:list`

Zeigt die Liste der verfügbaren Währungen an

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:dependencies:show-framework`

Zeigt die Anzahl der Abhängigkeiten vom Magento-Framework an

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Berichtsdateiname

- Standard: `framework-dependencies.csv`
- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:dependencies:show-modules`

Anzahl der Abhängigkeiten zwischen Modulen anzeigen

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Berichtsdateiname

- Standard: `modules-dependencies.csv`
- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:dependencies:show-modules-circular`

Zeigt die Anzahl der zirkulären Abhängigkeiten zwischen Modulen an

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Berichtsdateiname

- Standard: `modules-circular-dependencies.csv`
- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:language:list`

Zeigt die Liste der verfügbaren Sprachen an

```bash
bin/magento info:language:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `info:timezone:list`

Zeigt die Liste der verfügbaren Zeitzonen an

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `inventory:reservation:create-compensations`

Erstellen von Reservierungen durch angegebene Vergütungsargumente

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Liste der Kompensationsargumente im Format „\&lt;order_increment_id>:\&lt;sku>:\&lt;quantity>:\&lt;stock-id>&quot;

- Standard: `[]`

- Array

### `--raw`, `-r`

Rohausgabe

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `inventory:reservation:list-inconsistencies`

Alle Bestellungen und Produkte mit Inkonsistenzen der verkäuflichen Menge anzeigen

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

Nur Inkonsistenzen bei vollständigen Bestellungen anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--incomplete-orders`, `-i`

Nur Inkonsistenzen bei unvollständigen Bestellungen anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--bunch-size`, `-b`

Definiert, wie viele Bestellungen gleichzeitig geladen werden

- Standard: `50`
- Akzeptiert einen Wert

### `--raw`, `-r`

Rohausgabe

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `inventory-geonames:import`

Herunterladen und Importieren von Geonamen für den Quellenauswahlalgorithmus

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Liste der zu importierenden Ländercodes

- Standard: `[]`

- Erforderlich
- Array

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `maintenance:allow-ips`

Legt IPs mit Ausnahme des Wartungsmodus fest

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

Zulässige IP-Adressen

- Standard: `[]`

- Array

### `--none`

Zulässige IP-Adressen löschen

- Standard: `false`
- Akzeptiert keinen Wert

### `--add`

Hinzufügen der IP-Adresse zur vorhandenen Liste

- Standard: `false`
- Akzeptiert keinen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `maintenance:disable`

Deaktiviert den Wartungsmodus

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Zulässige IP-Adressen (verwenden Sie „none„, um die Liste der zulässigen IP-Adressen zu löschen)

- Standard: `[]`
- Erfordert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `maintenance:enable`

Aktiviert den Wartungsmodus

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Zulässige IP-Adressen (verwenden Sie „none„, um die Liste der zulässigen IP-Adressen zu löschen)

- Standard: `[]`
- Erfordert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `maintenance:status`

Zeigt den Wartungsmodus-Status an

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `media-content:sync`

Synchronisieren von Inhalten mit Assets

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `media-gallery:sync`

Synchronisieren des Medienspeichers und der Medienelemente in der Datenbank

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `module:config:status`

Überprüft die Modulkonfiguration in der Datei &quot;app/etc/config.php&quot; und gibt Berichte aus, ob die Module aktuell sind oder nicht

```bash
bin/magento module:config:status
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `module:disable`

Deaktiviert die angegebenen Module

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Modulname

- Standard: `[]`

- Array

### `--force`, `-f`

Abhängigkeitsprüfung umgehen

- Standard: `false`
- Akzeptiert keinen Wert

### `--all`

Alle Module deaktivieren

- Standard: `false`
- Akzeptiert keinen Wert

### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `module:enable`

Aktiviert die angegebenen Module

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Modulname

- Standard: `[]`

- Array

### `--force`, `-f`

Abhängigkeitsprüfung umgehen

- Standard: `false`
- Akzeptiert keinen Wert

### `--all`

Alle Module aktivieren

- Standard: `false`
- Akzeptiert keinen Wert

### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `module:status`

Zeigt den Status der Module an

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

Optionaler Modulname

- Standard: `[]`

- Array

### `--enabled`

Nur aktivierte Module drucken

- Standard: `false`
- Akzeptiert keinen Wert

### `--disabled`

Nur deaktivierte Module drucken

- Standard: `false`
- Akzeptiert keinen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `module:uninstall`

Deinstalliert vom Composer installierte Module

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

Modulname

- Standard: `[]`

- Erforderlich
- Array

### `--remove-data`, `-r`

Von Modul(en) installierte Daten entfernen

- Standard: `false`
- Akzeptiert keinen Wert

### `--backup-code`

Code- und Konfigurationsdateien sichern (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

### `--backup-media`

Medien-Backup erstellen

- Standard: `false`
- Akzeptiert keinen Wert

### `--backup-db`

Erstellen einer vollständigen Datenbanksicherung

- Standard: `false`
- Akzeptiert keinen Wert

### `--non-composer`

Alle Module, die an dieser Stelle eingefügt werden, sind nicht komponentenbasiert

- Standard: `false`
- Akzeptiert keinen Wert

### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen. Erforderlich, wenn die Module statische Ansichtsdateien haben

- Standard: `false`
- Akzeptiert keinen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `newrelic:create:deploy-marker`

Überprüfen Sie die Bereitstellungswarteschlange auf Einträge und erstellen Sie eine geeignete Bereitstellungsmarkierung.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

Nachricht bereitstellen?

- Erforderlich

### `change_log`

Änderungsprotokoll?

- Erforderlich

### `user`

Bereitstellungsbenutzer


### `revision`

Revision


### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `queue:consumers:list`

Liste der MessageQueue-Verbraucher

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `queue:consumers:restart`

MessageQueue-Verbraucher neu starten

```bash
bin/magento queue:consumers:restart
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `queue:consumers:start`

MessageQueue-Verbraucher starten

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

Der Name des zu startenden Verbrauchers.

- Erforderlich

### `--max-messages`

Die Anzahl der Nachrichten, die vom Verbraucher vor Beendigung des Prozesses verarbeitet werden sollen. Wenn nicht anders angegeben, wird der Vorgang nach der Verarbeitung aller Nachrichten in der Warteschlange beendet.

- Erfordert einen Wert

### `--batch-size`

Die Anzahl der Nachrichten pro Batch. Gilt nur für den Batch-Verbraucher.

- Erfordert einen Wert

### `--area-code`

Der bevorzugte Bereich (global, adminHTML usw.) ist standardmäßig global.

- Erfordert einen Wert

### `--single-thread`

Diese Option verhindert, dass mehrere Kopien eines Verbrauchers gleichzeitig ausgeführt werden.

- Standard: `false`
- Akzeptiert keinen Wert

### `--multi-process`

Die Anzahl der Prozesse pro Verbraucher.

- Akzeptiert einen Wert

### `--pid-file-path`

Der Dateipfad zum Speichern der PID (diese Option ist veraltet, verwenden Sie stattdessen —single-thread)

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `remote-storage:sync`

Synchronisieren Sie Mediendateien mit dem Remote-Speicher.

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `saas:resync`

Synchronisiert Feed-Daten erneut mit dem SaaS-Service.

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

### `--feed`

Feed-Name zur vollständigen Neusynchronisierung mit dem SaaS-Service. Verfügbare Feeds: Zahlungsdienste-Auftragsproduktion, Zahlungsdienste-Auftrags-Sandbox, Zahlungsdienste-Auftragsstatus Produktion, Zahlungsdienste-Auftragsstatus Sandbox, Zahlungsdienste-Storeproduktion, Zahlungsdienste-Store-Sandbox

- Erfordert einen Wert

### `--no-reindex`

Führen Sie die erneute Übermittlung von Feed-Daten nur an den SaaS-Service aus. Indiziert nicht neu. (Diese Option gilt nicht für Produkte, Produktüberschreibungen, Preise und Feeds.)

- Standard: `false`
- Akzeptiert keinen Wert

### `--cleanup-feed`

Bereinigung der Feed-Indexertabelle vor der Synchronisierung erzwingen

- Standard: `false`
- Akzeptiert keinen Wert

### `--dry-run`

Probelauf. Daten werden nicht exportiert. Um die Payload in der Protokolldatei zu speichern, führen Sie var/log/saas-export.log mit der Umgebungsvariablen EXPORTER_EXTENDED_LOG=1 aus.

- Standard: `false`
- Akzeptiert keinen Wert

### `--thread-count`

Anzahl der Synchronisierungs-Threads festlegen.

- Erfordert einen Wert

### `--batch-size`

Festlegen der Größe eines Synchronisierungs-Batches

- Erfordert einen Wert

### `--continue-resync`

Neusynchronisierung von der letzten gespeicherten Position fortsetzen (Diese Option gilt für die Produkte, Produktüberschreibungen, Preise und Feeds)

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:deploy`

Bereitstellen von Beispieldatenmodulen für Composer-basierte Magento-Installationen

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Aktualisieren Sie composer.json, ohne das Composer-Update auszuführen

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:remove`

Entfernen Sie alle Beispieldatenpakete aus „composer.json“

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Aktualisieren Sie composer.json, ohne das Composer-Update auszuführen

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `sampledata:reset`

Alle Beispieldatenmodule zur Neuinstallation zurücksetzen

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `security:recaptcha:disable-for-user-forgot-password`

Deaktivieren von reCAPTCHA für Formular bei vergessenem Kennwort für Admin-Benutzer

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `security:recaptcha:disable-for-user-login`

Deaktivieren von reCAPTCHA für das Administrator-Benutzeranmeldeformular

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `security:tfa:google:set-secret`

Legen Sie die für die OTP-Generierung von Google verwendeten geheimen Daten fest.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

Benutzername

- Erforderlich

### `secret`

Geheim

- Erforderlich

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `security:tfa:providers`

Alle verfügbaren Anbieter auflisten

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `security:tfa:reset`

Konfiguration für einen Benutzer zurücksetzen

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

Benutzername

- Erforderlich

### `provider`

Anbietercode

- Erforderlich

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:backup`

Ermöglicht die Sicherung der Magento-Anwendungs-Code-Basis, des Mediums und der Datenbank

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

Code- und Konfigurationsdateien sichern (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

### `--media`

Medien-Backup erstellen

- Standard: `false`
- Akzeptiert keinen Wert

### `--db`

Erstellen einer vollständigen Datenbanksicherung

- Standard: `false`
- Akzeptiert keinen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:config:set`

Erstellt oder ändert die Bereitstellungskonfiguration

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)

- Erfordert einen Wert

### `--enable-debug-logging`

Debug-Protokollierung aktivieren

- Erfordert einen Wert

### `--enable-syslog-logging`

Syslog-Protokollierung aktivieren

- Erfordert einen Wert

### `--remote-storage-driver`

Remote-Speichertreiber

- Erfordert einen Wert

### `--remote-storage-prefix`

Remote-Speicherpräfix

- Standard: &quot;
- Erfordert einen Wert

### `--remote-storage-endpoint`

Remote-Speicher-Endpunkt

- Erfordert einen Wert

### `--remote-storage-bucket`

Remote-Speicher-Bucket

- Erfordert einen Wert

### `--remote-storage-region`

Remote-Speicherregion

- Erfordert einen Wert

### `--remote-storage-key`

Remote-Speicherzugriffsschlüssel

- Standard: &quot;
- Erfordert einen Wert

### `--remote-storage-secret`

Geheimschlüssel des Remotespeichers

- Standard: &quot;
- Erfordert einen Wert

### `--remote-storage-path-style`

Remote-Speicherpfadstil

- Standard: `0`
- Erfordert einen Wert

### `--id_salt`

GraphQL-Salz

- Erfordert einen Wert

### `--config-async`

Async Admin Config Speichern aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

### `--amqp-host`

AMQL-Server-Host

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-port`

AMQL-Server-Port

- Standard: `5672`
- Erfordert einen Wert

### `--amqp-user`

AMQL-Server-Benutzername

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-password`

AMQL-Serverkennwort

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-virtualhost`

AMQP VirtualHost

- Standard: `/`
- Erfordert einen Wert

### `--amqp-ssl`

AMQP-SSL

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-ssl-options`

AMQL-SSL-Optionen (JSON)

- Standard: &quot;
- Erfordert einen Wert

### `--consumers-wait-for-messages`

Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein

- Erfordert einen Wert

### `--queue-default-connection`

Standardverbindung für Nachrichtenwarteschlangen. Kann „db„, „amqp“ oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert werden, da andernfalls Nachrichten nicht korrekt verarbeitet werden.

- Erfordert einen Wert

### `--key`

Verschlüsselungsschlüssel

- Erfordert einen Wert

### `--db-host`

Datenbankserver-Host

- Erfordert einen Wert

### `--db-name`

Datenbankname

- Erfordert einen Wert

### `--db-user`

Benutzername des Datenbank-Servers

- Erfordert einen Wert

### `--db-engine`

Datenbank-Server-Engine

- Erfordert einen Wert

### `--db-password`

Datenbankserver-Kennwort

- Erfordert einen Wert

### `--db-prefix`

Datenbanktabellen-Präfix

- Erfordert einen Wert

### `--db-model`

Datenbanktyp

- Erfordert einen Wert

### `--db-init-statements`

Anfangssatz der Befehle in der Datenbank

- Erfordert einen Wert

### `--skip-db-validation`, `-s`

Wenn angegeben, wird die Überprüfung der DB-Verbindung übersprungen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--http-cache-hosts`

HTTP-Cache-Hosts

- Erfordert einen Wert

### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei zum Aufbau der DB-Verbindung über SSL

- Standard: &quot;
- Erfordert einen Wert

### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei zum Aufbau der DB-Verbindung über SSL

- Standard: &quot;
- Erfordert einen Wert

### `--db-ssl-ca`

Vollständiger Pfad der Serverzertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

### `--db-ssl-verify`

Serverzertifizierung überprüfen

- Standard: `false`
- Akzeptiert keinen Wert

### `--session-save`

Session Save Handler

- Erfordert einen Wert

### `--session-save-redis-host`

Vollqualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets

- Erfordert einen Wert

### `--session-save-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--session-save-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--session-save-redis-timeout`

Verbindungs-Timeout, in Sekunden

- Erfordert einen Wert

### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen

- Erfordert einen Wert

### `--session-save-redis-db`

Redis-Datenbanknummer

- Erfordert einen Wert

### `--session-save-redis-compression-threshold`

Redis-Komprimierungsschwellenwert

- Erfordert einen Wert

### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy

- Erfordert einen Wert

### `--session-save-redis-log-level`

Protokollebene neu angeben. Werte: 0 (am wenigsten ausführlich) bis 7 (am meisten ausführlich)

- Erfordert einen Wert

### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperre einer Sitzung warten können

- Erfordert einen Wert

### `--session-save-redis-break-after-frontend`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Frontend-Sitzung aufzuheben

- Erfordert einen Wert

### `--session-save-redis-break-after-adminhtml`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Admin-Sitzung aufzuheben

- Erfordert einen Wert

### `--session-save-redis-first-lifetime`

Lebensdauer der Sitzung für Nicht-Bots beim ersten Schreiben (0 zum Deaktivieren) in Sekunden

- Erfordert einen Wert

### `--session-save-redis-bot-first-lifetime`

Lebensdauer der Sitzung für Bots beim ersten Schreiben in Sekunden (zur Deaktivierung 0 verwenden)

- Erfordert einen Wert

### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (zur Deaktivierung mit 0)

- Erfordert einen Wert

### `--session-save-redis-disable-locking`

Redis-Sperre deaktivieren. Werte: false (Standard), true

- Erfordert einen Wert

### `--session-save-redis-min-lifetime`

Sitzungslebensdauer in Sekunden ändern

- Erfordert einen Wert

### `--session-save-redis-max-lifetime`

Maximale Sitzungslebensdauer in Sekunden anpassen

- Erfordert einen Wert

### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Erfordert einen Wert

### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommata getrennt

- Erfordert einen Wert

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifizieren Master. Werte: false (Standard), true

- Erfordert einen Wert

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-Verbindungsversuche.

- Erfordert einen Wert

### `--cache-backend`

Standard-Cache-Handler

- Erfordert einen Wert

### `--cache-backend-redis-server`

Redis-Server

- Erfordert einen Wert

### `--cache-backend-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

### `--cache-backend-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--cache-backend-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--cache-backend-redis-compress-data`

Auf 0 gesetzt, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

### `--cache-backend-redis-compression-lib`

Zu verwendende Komprimierungsbibliothek [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

### `--cache-backend-redis-use-lua`

Auf 1 gesetzt, um LUA zu aktivieren (Standard ist 0, deaktiviert)

- Erfordert einen Wert

### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

### `--allow-parallel-generation`

Generieren von Cache auf nicht blockierende Weise zulassen

- Standard: `false`
- Akzeptiert keinen Wert

### `--page-cache`

Standard-Cache-Handler

- Erfordert einen Wert

### `--page-cache-redis-server`

Redis-Server

- Erfordert einen Wert

### `--page-cache-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

### `--page-cache-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--page-cache-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--page-cache-redis-compress-data`

Legen Sie hierfür 1 fest, um den vollständigen Seiten-Cache zu komprimieren (verwenden Sie 0, um ihn zu deaktivieren).

- Erfordert einen Wert

### `--page-cache-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

### `--lock-provider`

Anbieternamen sperren

- Erfordert einen Wert

### `--lock-db-prefix`

Installationsspezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten

- Erfordert einen Wert

### `--lock-zookeeper-host`

Host und Port für die Verbindung mit dem ZooKeeper-Cluster. Beispiel: 127.0.0.1:2181

- Erfordert einen Wert

### `--lock-zookeeper-path`

Der Pfad, in dem ZooKeeper Sperren speichert. Der Standardpfad lautet: /magento/locks

- Erfordert einen Wert

### `--lock-file-path`

Der Pfad, unter dem Dateisperren gespeichert werden.

- Erfordert einen Wert

### `--document-root-is-pub`

Markierung, die anzeigt, ob Pub sich im Stammverzeichnis befindet, kann nur „true“ oder „false“ sein.

- Erfordert einen Wert

### `--backpressure-logger`

Handler für den Rückdrucklogger

- Erfordert einen Wert

### `--backpressure-logger-redis-server`

Redis-Server

- Erfordert einen Wert

### `--backpressure-logger-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--backpressure-logger-redis-timeout`

Redis-Server-Zeitüberschreitung

- Erfordert einen Wert

### `--backpressure-logger-redis-persistent`

Redis persistent

- Erfordert einen Wert

### `--backpressure-logger-redis-db`

Redis-DB-Nummer

- Erfordert einen Wert

### `--backpressure-logger-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--backpressure-logger-redis-user`

Redis-Server-Benutzer

- Erfordert einen Wert

### `--backpressure-logger-id-prefix`

ID-Präfix für Schlüssel

- Erfordert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:db-data:upgrade`

Installiert und aktualisiert Daten in der Datenbank

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:db-declaration:generate-patch`

Erzeugt den Patch und legt ihn in einem bestimmten Ordner ab.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

Modulname

- Erforderlich

### `patch`

Patch-Name

- Erforderlich

### `--revertable`

Überprüfen, ob das Patch rückgängig gemacht werden kann oder nicht.

- Standard: `false`
- Akzeptiert einen Wert

### `--type`

Finden Sie heraus, welcher Patch-Typ generiert werden soll. Verfügbare Werte: `data`, `schema`.

- Standard: `data`
- Akzeptiert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:db-declaration:generate-whitelist`

Generieren einer Whitelist von Tabellen und Spalten, die vom Deklarations-Installationsprogramm bearbeitet werden dürfen

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Name des Moduls, in dem die Whitelist generiert wird

- Standard: `all`
- Akzeptiert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:db-schema:upgrade`

Installiert und aktualisiert das DB-Schema

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Ermöglicht die Konvertierung alter Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:db:status`

Prüft, ob DB-Schema oder Daten aktualisiert werden müssen

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:di:compile`

Erzeugt die ID-Konfiguration und alle fehlenden Klassen, die automatisch generiert werden können

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:install`

Installiert die Magento-Anwendung

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)

- Erfordert einen Wert

### `--enable-debug-logging`

Debug-Protokollierung aktivieren

- Erfordert einen Wert

### `--enable-syslog-logging`

Syslog-Protokollierung aktivieren

- Erfordert einen Wert

### `--remote-storage-driver`

Remote-Speichertreiber

- Erfordert einen Wert

### `--remote-storage-prefix`

Remote-Speicherpräfix

- Standard: &quot;
- Erfordert einen Wert

### `--remote-storage-endpoint`

Remote-Speicher-Endpunkt

- Erfordert einen Wert

### `--remote-storage-bucket`

Remote-Speicher-Bucket

- Erfordert einen Wert

### `--remote-storage-region`

Remote-Speicherregion

- Erfordert einen Wert

### `--remote-storage-key`

Remote-Speicherzugriffsschlüssel

- Standard: &quot;
- Erfordert einen Wert

### `--remote-storage-secret`

Geheimschlüssel des Remotespeichers

- Standard: &quot;
- Erfordert einen Wert

### `--remote-storage-path-style`

Remote-Speicherpfadstil

- Standard: `0`
- Erfordert einen Wert

### `--id_salt`

GraphQL-Salz

- Erfordert einen Wert

### `--config-async`

Async Admin Config Speichern aktivieren? 1 - Ja, 0 - Nein

- Erfordert einen Wert

### `--amqp-host`

AMQL-Server-Host

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-port`

AMQL-Server-Port

- Standard: `5672`
- Erfordert einen Wert

### `--amqp-user`

AMQL-Server-Benutzername

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-password`

AMQL-Serverkennwort

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-virtualhost`

AMQP VirtualHost

- Standard: `/`
- Erfordert einen Wert

### `--amqp-ssl`

AMQP-SSL

- Standard: &quot;
- Erfordert einen Wert

### `--amqp-ssl-options`

AMQL-SSL-Optionen (JSON)

- Standard: &quot;
- Erfordert einen Wert

### `--consumers-wait-for-messages`

Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein

- Erfordert einen Wert

### `--queue-default-connection`

Standardverbindung für Nachrichtenwarteschlangen. Kann „db„, „amqp“ oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert werden, da andernfalls Nachrichten nicht korrekt verarbeitet werden.

- Erfordert einen Wert

### `--key`

Verschlüsselungsschlüssel

- Erfordert einen Wert

### `--db-host`

Datenbankserver-Host

- Erfordert einen Wert

### `--db-name`

Datenbankname

- Erfordert einen Wert

### `--db-user`

Benutzername des Datenbank-Servers

- Erfordert einen Wert

### `--db-engine`

Datenbank-Server-Engine

- Erfordert einen Wert

### `--db-password`

Datenbankserver-Kennwort

- Erfordert einen Wert

### `--db-prefix`

Datenbanktabellen-Präfix

- Erfordert einen Wert

### `--db-model`

Datenbanktyp

- Erfordert einen Wert

### `--db-init-statements`

Anfangssatz der Befehle in der Datenbank

- Erfordert einen Wert

### `--skip-db-validation`, `-s`

Wenn angegeben, wird die Überprüfung der DB-Verbindung übersprungen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--http-cache-hosts`

HTTP-Cache-Hosts

- Erfordert einen Wert

### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei zum Aufbau der DB-Verbindung über SSL

- Standard: &quot;
- Erfordert einen Wert

### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei zum Aufbau der DB-Verbindung über SSL

- Standard: &quot;
- Erfordert einen Wert

### `--db-ssl-ca`

Vollständiger Pfad der Serverzertifikatdatei, um die DB-Verbindung über SSL herzustellen

- Standard: &quot;
- Erfordert einen Wert

### `--db-ssl-verify`

Serverzertifizierung überprüfen

- Standard: `false`
- Akzeptiert keinen Wert

### `--session-save`

Session Save Handler

- Erfordert einen Wert

### `--session-save-redis-host`

Vollqualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets

- Erfordert einen Wert

### `--session-save-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--session-save-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--session-save-redis-timeout`

Verbindungs-Timeout, in Sekunden

- Erfordert einen Wert

### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen

- Erfordert einen Wert

### `--session-save-redis-db`

Redis-Datenbanknummer

- Erfordert einen Wert

### `--session-save-redis-compression-threshold`

Redis-Komprimierungsschwellenwert

- Erfordert einen Wert

### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy

- Erfordert einen Wert

### `--session-save-redis-log-level`

Protokollebene neu angeben. Werte: 0 (am wenigsten ausführlich) bis 7 (am meisten ausführlich)

- Erfordert einen Wert

### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperre einer Sitzung warten können

- Erfordert einen Wert

### `--session-save-redis-break-after-frontend`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Frontend-Sitzung aufzuheben

- Erfordert einen Wert

### `--session-save-redis-break-after-adminhtml`

Wartezeit in Sekunden, bevor versucht wird, eine Sperre für die Admin-Sitzung aufzuheben

- Erfordert einen Wert

### `--session-save-redis-first-lifetime`

Lebensdauer der Sitzung für Nicht-Bots beim ersten Schreiben (0 zum Deaktivieren) in Sekunden

- Erfordert einen Wert

### `--session-save-redis-bot-first-lifetime`

Lebensdauer der Sitzung für Bots beim ersten Schreiben in Sekunden (zur Deaktivierung 0 verwenden)

- Erfordert einen Wert

### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (zur Deaktivierung mit 0)

- Erfordert einen Wert

### `--session-save-redis-disable-locking`

Redis-Sperre deaktivieren. Werte: false (Standard), true

- Erfordert einen Wert

### `--session-save-redis-min-lifetime`

Sitzungslebensdauer in Sekunden ändern

- Erfordert einen Wert

### `--session-save-redis-max-lifetime`

Maximale Sitzungslebensdauer in Sekunden anpassen

- Erfordert einen Wert

### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Erfordert einen Wert

### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommata getrennt

- Erfordert einen Wert

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifizieren Master. Werte: false (Standard), true

- Erfordert einen Wert

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-Verbindungsversuche.

- Erfordert einen Wert

### `--cache-backend`

Standard-Cache-Handler

- Erfordert einen Wert

### `--cache-backend-redis-server`

Redis-Server

- Erfordert einen Wert

### `--cache-backend-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

### `--cache-backend-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--cache-backend-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--cache-backend-redis-compress-data`

Auf 0 gesetzt, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)

- Erfordert einen Wert

### `--cache-backend-redis-compression-lib`

Zu verwendende Komprimierungsbibliothek [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

### `--cache-backend-redis-use-lua`

Auf 1 gesetzt, um LUA zu aktivieren (Standard ist 0, deaktiviert)

- Erfordert einen Wert

### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

### `--allow-parallel-generation`

Generieren von Cache auf nicht blockierende Weise zulassen

- Standard: `false`
- Akzeptiert keinen Wert

### `--page-cache`

Standard-Cache-Handler

- Erfordert einen Wert

### `--page-cache-redis-server`

Redis-Server

- Erfordert einen Wert

### `--page-cache-redis-db`

Datenbanknummer für den Cache

- Erfordert einen Wert

### `--page-cache-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--page-cache-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--page-cache-redis-compress-data`

Legen Sie hierfür 1 fest, um den vollständigen Seiten-Cache zu komprimieren (verwenden Sie 0, um ihn zu deaktivieren).

- Erfordert einen Wert

### `--page-cache-redis-compression-lib`

Komprimierungsbibliothek zur Verwendung [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)

- Erfordert einen Wert

### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel

- Erfordert einen Wert

### `--lock-provider`

Anbieternamen sperren

- Erfordert einen Wert

### `--lock-db-prefix`

Installationsspezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten

- Erfordert einen Wert

### `--lock-zookeeper-host`

Host und Port für die Verbindung mit dem ZooKeeper-Cluster. Beispiel: 127.0.0.1:2181

- Erfordert einen Wert

### `--lock-zookeeper-path`

Der Pfad, in dem ZooKeeper Sperren speichert. Der Standardpfad lautet: /magento/locks

- Erfordert einen Wert

### `--lock-file-path`

Der Pfad, unter dem Dateisperren gespeichert werden.

- Erfordert einen Wert

### `--document-root-is-pub`

Markierung, die anzeigt, ob Pub sich im Stammverzeichnis befindet, kann nur „true“ oder „false“ sein.

- Erfordert einen Wert

### `--backpressure-logger`

Handler für den Rückdrucklogger

- Erfordert einen Wert

### `--backpressure-logger-redis-server`

Redis-Server

- Erfordert einen Wert

### `--backpressure-logger-redis-port`

Redis-Server-Listener-Port

- Erfordert einen Wert

### `--backpressure-logger-redis-timeout`

Redis-Server-Zeitüberschreitung

- Erfordert einen Wert

### `--backpressure-logger-redis-persistent`

Redis persistent

- Erfordert einen Wert

### `--backpressure-logger-redis-db`

Redis-DB-Nummer

- Erfordert einen Wert

### `--backpressure-logger-redis-password`

Redis-Serverkennwort

- Erfordert einen Wert

### `--backpressure-logger-redis-user`

Redis-Server-Benutzer

- Erfordert einen Wert

### `--backpressure-logger-id-prefix`

ID-Präfix für Schlüssel

- Erfordert einen Wert

### `--base-url`

URL, unter der der Speicher verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url

- Erfordert einen Wert

### `--language`

Standardsprachcode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code

- Erfordert einen Wert

### `--timezone`

Standard-Zeitzonencode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone

- Erfordert einen Wert

### `--currency`

Standard-Währungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow

- Erfordert einen Wert

### `--use-rewrites`

Verwenden Sie Umschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites

- Erfordert einen Wert

### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend

- Erfordert einen Wert

### `--base-url-secure`

Basis-URL für die SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url

- Erfordert einen Wert

### `--use-secure-admin`

Ausführen der Admin-Benutzeroberfläche mit SSL. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml

- Erfordert einen Wert

### `--admin-use-security-key`

Ob die Funktion „Sicherheitsschlüssel“ in Magento-Admin-URLs und -Formularen verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key

- Erfordert einen Wert

### `--admin-user`

Admin-Benutzer

- Akzeptiert einen Wert

### `--admin-password`

Administratorkennwort

- Akzeptiert einen Wert

### `--admin-email`

Admin Email

- Akzeptiert einen Wert

### `--admin-firstname`

Vorname des Administrators

- Akzeptiert einen Wert

### `--admin-lastname`

Admin-Nachname

- Akzeptiert einen Wert

### `--search-engine`

Suchmaschine. Werte: elasticsearch7, elasticsearch8, opensearch

- Erfordert einen Wert

### `--elasticsearch-host`

Elasticsearch-Server-Host.

- Erfordert einen Wert

### `--elasticsearch-port`

Elasticsearch-Server-Port.

- Erfordert einen Wert

### `--elasticsearch-enable-auth`

Auf 1 gesetzt, um die Authentifizierung zu aktivieren. (Standard ist 0, deaktiviert)

- Erfordert einen Wert

### `--elasticsearch-username`

Benutzername des Elasticsearchs. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

### `--elasticsearch-password`

Elasticsearch-Passwort. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

### `--elasticsearch-index-prefix`

Elasticsearch-Indexpräfix.

- Erfordert einen Wert

### `--elasticsearch-timeout`

Zeitüberschreitung des Elasticsearch-Servers.

- Erfordert einen Wert

### `--opensearch-host`

OpenSearch-Server-Host.

- Erfordert einen Wert

### `--opensearch-port`

OpenSearch-Server-Port.

- Erfordert einen Wert

### `--opensearch-enable-auth`

Auf 1 gesetzt, um die Authentifizierung zu aktivieren. (Standard ist 0, deaktiviert)

- Erfordert einen Wert

### `--opensearch-username`

OpenSearch-Benutzername. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

### `--opensearch-password`

Kennwort für OpenSearch. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist

- Erfordert einen Wert

### `--opensearch-index-prefix`

OpenSearch-Indexpräfix.

- Erfordert einen Wert

### `--opensearch-timeout`

OpenSearch-Server-Zeitüberschreitung.

- Erfordert einen Wert

### `--cleanup-database`

Bereinigen der Datenbank vor der Installation

- Standard: `false`
- Akzeptiert keinen Wert

### `--sales-order-increment-prefix`

Präfix der Kundenauftragsnummer

- Erfordert einen Wert

### `--use-sample-data`

Verwenden von Beispieldaten

- Standard: `false`
- Akzeptiert keinen Wert

### `--enable-modules`

Liste der kommagetrennten Modulnamen. Dieser muss bei der Installation miteinbezogen werden. Verfügbarer magischer Parameter „all„.

- Akzeptiert einen Wert

### `--disable-modules`

Liste der kommagetrennten Modulnamen. Dies muss bei der Installation vermieden werden. Verfügbarer magischer Parameter „all„.

- Akzeptiert einen Wert

### `--convert-old-scripts`

Ermöglicht die Konvertierung alter Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

### `--interactive`, `-i`

Interaktive Magento-Installation

- Standard: `false`
- Akzeptiert keinen Wert

### `--safe-mode`

Sichere Installation von Magento mit Dumps bei zerstörerischen Vorgängen, wie Säulenentfernung

- Akzeptiert einen Wert

### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps

- Akzeptiert einen Wert

### `--dry-run`

Die Magento-Installation wird im Trockenlauf-Modus ausgeführt

- Standard: `false`
- Akzeptiert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:performance:generate-fixtures`

Erzeugt Vorrichtungen

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

Pfad zur Profilkonfigurationsdatei

- Erforderlich

### `--skip-reindex`, `-s`

Neuindizierung überspringen

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:rollback`

Rollback von Magento-Anwendungs-Codebase, Medien und Datenbank

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

Basisname der Code-Sicherungsdatei in var/backups

- Erfordert einen Wert

### `--media-file`, `-m`

Basisname der Mediensicherungsdatei in var/backups

- Erfordert einen Wert

### `--db-file`, `-d`

Basisname der Datenbank-Backup-Datei in var/backups

- Erfordert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:static-content:deploy`

Stellt statische Ansichtsdateien bereit

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

Durch Leerzeichen getrennte Liste von ISO-639-Sprachcodes, für die statische Ansichtsdateien ausgegeben werden sollen.

- Standard: `[]`

- Array

### `--force`, `-f`

Dateien in jedem Modus bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--strategy`, `-s`

Stellen Sie Dateien mithilfe einer angegebenen Strategie bereit.

- Standard: `quick`
- Akzeptiert einen Wert

### `--area`, `-a`

Generieren Sie Dateien nur für die angegebenen Bereiche.

- Standard: `all`
- Akzeptiert mehrere Werte

### `--exclude-area`

Keine Dateien für die angegebenen Bereiche generieren.

- Standard: `none`
- Akzeptiert mehrere Werte

### `--theme`, `-t`

Generieren Sie statische Ansichtsdateien nur für die angegebenen Designs.

- Standard: `all`
- Akzeptiert mehrere Werte

### `--exclude-theme`

Keine Dateien für die angegebenen Designs generieren.

- Standard: `none`
- Akzeptiert mehrere Werte

### `--language`, `-l`

Generieren Sie Dateien nur für die angegebenen Sprachen.

- Standard: `all`
- Akzeptiert mehrere Werte

### `--exclude-language`

Keine Dateien für die angegebenen Sprachen erzeugen.

- Standard: `none`
- Akzeptiert mehrere Werte

### `--jobs`, `-j`

Aktivieren Sie die parallele Verarbeitung mit der angegebenen Anzahl von Aufträgen.

- Standard: `0`
- Akzeptiert einen Wert

### `--max-execution-time`

Die maximal erwartete Ausführungszeit des statischen Bereitstellungsprozesses (in Sekunden).

- Standard: `900`
- Akzeptiert einen Wert

### `--symlink-locale`

Erstellen Sie Symlinks für die Dateien dieser Gebietsschemata, die für die Bereitstellung übergeben werden, aber keine Anpassungen aufweisen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--content-version`

Benutzerdefinierte Versionen statischer Inhalte können verwendet werden, wenn die Bereitstellung auf mehreren Knoten ausgeführt wird, um sicherzustellen, dass die Version statischer Inhalte identisch ist und die Zwischenspeicherung ordnungsgemäß funktioniert.

- Erfordert einen Wert

### `--refresh-content-version-only`

Die Aktualisierung der Version statischer Inhalte kann nur verwendet werden, um statische Inhalte im Browser-Cache und CDN-Cache zu aktualisieren.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-javascript`

Stellen Sie keine JavaScript-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-js-bundle`

Stellen Sie keine JavaScript-Paketdateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-css`

Stellen Sie keine CSS-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-less`

Stellen Sie keine LESS-Dateien bereit.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-images`

Keine Bilder bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-fonts`

Schriftarten-Dateien nicht bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-html`

Keine HTML-Dateien bereitstellen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-misc`

Stellen Sie keine Dateien anderer Typen bereit (MD, JBF, CSV usw.).

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-html-minify`

Minimieren Sie keine HTML-Dateien.

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-parent`

Übergeordnete Designs nicht kompilieren. Wird nur in schnellen und standardmäßigen Strategien unterstützt.

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:store-config:set`

Installiert die Store-Konfiguration. Veraltet seit 2.2.0. Verwenden Sie stattdessen config:set .

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

URL, unter der der Speicher verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url

- Erfordert einen Wert

### `--language`

Standardsprachcode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code

- Erfordert einen Wert

### `--timezone`

Standard-Zeitzonencode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone

- Erfordert einen Wert

### `--currency`

Standard-Währungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow

- Erfordert einen Wert

### `--use-rewrites`

Verwenden Sie Umschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites

- Erfordert einen Wert

### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend

- Erfordert einen Wert

### `--base-url-secure`

Basis-URL für die SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url

- Erfordert einen Wert

### `--use-secure-admin`

Ausführen der Admin-Benutzeroberfläche mit SSL. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml

- Erfordert einen Wert

### `--admin-use-security-key`

Ob die Funktion „Sicherheitsschlüssel“ in Magento-Admin-URLs und -Formularen verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key

- Erfordert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:uninstall`

Deinstalliert die Magento-Anwendung

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `setup:upgrade`

Aktualisiert das Magento-Programm, die DB-Daten und das Schema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

Verhindert das Löschen der generierten Dateien. Wir raten von der Verwendung dieser Option ab, es sei denn, sie wird in der Produktion bereitgestellt. Wenden Sie sich an Ihren Systemintegrator oder Administrator, um weitere Informationen zu erhalten.

- Standard: `false`
- Akzeptiert keinen Wert

### `--convert-old-scripts`

Ermöglicht die Konvertierung alter Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml

- Standard: `false`
- Akzeptiert einen Wert

### `--safe-mode`

Sichere Installation von Magento mit Dumps bei zerstörerischen Vorgängen, wie Säulenentfernung

- Akzeptiert einen Wert

### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps

- Akzeptiert einen Wert

### `--dry-run`

Die Magento-Installation wird im Trockenlauf-Modus ausgeführt

- Standard: `false`
- Akzeptiert einen Wert

### `--magento-init-params`

Fügen Sie zu einem beliebigen Befehl hinzu, um Magento-Initialisierungsparameter anzupassen. Beispiel: „MAGE_MODE=developer&amp;MAGE_DIRS[Basis][path]=/var/www/example.com&amp;MAGE_DIRS[Cache][path]= /var/tmp/cache“

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `store:list`

Zeigt die Liste der Stores an

```bash
bin/magento store:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `store:website:list`

Zeigt die Liste der Websites an

```bash
bin/magento store:website:list
```

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `theme:uninstall`

Deinstalliert ein Design

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

Pfad des Designs. Der Designpfad sollte als vollständiger Pfad angegeben werden, der „area/provider/name“ lautet. Beispiel: frontend/Magento/blank

- Standard: `[]`

- Erforderlich
- Array

### `--backup-code`

Code-Backup erstellen (ohne temporäre Dateien)

- Standard: `false`
- Akzeptiert keinen Wert

### `--clear-static-content`, `-c`

Erzeugte statische Ansichtsdateien löschen.

- Standard: `false`
- Akzeptiert keinen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert


## `varnish:vcl:generate`

Erzeugt VCL-Lack und überträgt es in die Befehlszeile

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

### `--access-list`

IP-Zugriffsliste, die Varnish löschen kann

- Standard: `localhost`
- Erfordert einen Wert

### `--backend-host`

Host des Web-Backends

- Standard: `localhost`
- Erfordert einen Wert

### `--backend-port`

Port des Web-Backends

- Standard: `8080`
- Erfordert einen Wert

### `--export-version`

Die Version der Lackdatei

- Standard: `6`
- Erfordert einen Wert

### `--grace-period`

Übergangsphase in Sekunden

- Standard: `300`
- Erfordert einen Wert

### `--input-file`

Eingabedatei, aus der VCL generiert werden soll

- Erfordert einen Wert

### `--output-file`

Pfad zur VCL-Datei

- Erfordert einen Wert

### `--help`, `-h`

Zeigt die Hilfe für den angegebenen Befehl an. Wenn kein Befehl angegeben wird, wird die Hilfe für \ angezeigt.&lt;info>list\&lt;/info> Befehl

- Standard: `false`
- Akzeptiert keinen Wert

### `--quiet`, `-q`

Keine Nachricht ausgeben

- Standard: `false`
- Akzeptiert keinen Wert

### `--verbose`, `-v|-vv|-vvv`

Erhöhen Sie die Ausführlichkeit der Meldungen: 1 für die normale Ausgabe, 2 für die ausführlichere Ausgabe und 3 für die Fehlersuche.

- Standard: `false`
- Akzeptiert keinen Wert

### `--version`, `-V`

Diese Anwendungsversion anzeigen

- Standard: `false`
- Akzeptiert keinen Wert

### `--ansi`

ANSI-Ausgabe erzwingen (oder deaktivieren —no-ansi)

- Akzeptiert keinen Wert

### `--no-ansi`

Negieren Sie die Option „—ansi“

- Standard: `false`
- Akzeptiert keinen Wert

### `--no-interaction`, `-n`

Keine interaktiven Fragen stellen

- Standard: `false`
- Akzeptiert keinen Wert
