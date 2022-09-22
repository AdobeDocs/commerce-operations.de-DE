---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '15643'
ht-degree: 0%

---
# bin/magento (Adobe Commerce vor Ort)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Version**: 2,4,5 <!-- app.version -->

Diese Referenz enthält 118 Befehle, die über das `bin/magento` Befehlszeilen-Tool.
Die anfängliche Liste wird automatisch mit der Variablen `bin/magento list` -Befehl an der Edition.
Verwenden Sie die [&quot;Hinzufügen von CLI-Befehlen&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) Anleitung zum Hinzufügen eines benutzerdefinierten CLI-Befehls.

>[!NOTE]
>
>Sie können `bin/magento` CLI-Befehle mit Shortcuts anstelle des vollständigen Befehlsnamens. Beispielsweise können Sie `bin/magento setup:upgrade` using `bin/magento s:up`, `bin/magento s:upg`. Siehe [Kurzsyntax](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) , um zu verstehen, wie Sie Tastaturbefehle mit jedem CLI-Befehl verwenden.

>[!NOTE]
>
>Diese Referenz wird aus der Anwendungs-Codebase generiert. Um den Inhalt zu ändern, können Sie den Quellcode für die entsprechende Befehlsimplementierung im [codebase](https://github.com/magento) Repository erstellen und Ihre Änderungen zur Überprüfung einreichen. Eine andere Möglichkeit besteht darin, _Feedback geben_ (finden Sie den Link oben rechts). Beitragsrichtlinien finden Sie unter [Codebeiträge](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

Hilfe für einen Befehl anzeigen

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

Der Befehlsname
- Standard: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

Das Ausgabeformat (txt, xml, json oder md)
- Standard: `txt`
- Erfordert einen Wert


### `--raw`

Ausgabe der Rohbefehl-Hilfe
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `list`

Auflisten von Befehlen

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

Der Namespace-Name
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

So geben Sie die unformatierte Befehlsliste aus
- Standard: `false`
- Akzeptiert keinen Wert


### `--format`

Das Ausgabeformat (txt, xml, json oder md)
- Standard: `txt`
- Erfordert einen Wert <!-- options --> <!-- options.size -->

## `admin:adobe-ims:disable`

Adobe IMS-Modul deaktivieren

```bash
bin/magento admin:adobe-ims:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `admin:adobe-ims:enable`

Aktivieren Sie das Adobe IMS-Modul.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--organization-id`, `-o`



Legen Sie die Organisations-ID für die Adobe IMS-Konfiguration fest. Erforderlich beim Aktivieren des Moduls
- Akzeptiert einen Wert



### `--client-id`, `-c`



Legen Sie die Client-ID für die Adobe IMS-Konfiguration fest. Erforderlich beim Aktivieren des Moduls
- Akzeptiert einen Wert



### `--client-secret`, `-s`



Legen Sie den Client-Geheimnis für die Adobe IMS-Konfiguration fest. Erforderlich beim Aktivieren des Moduls
- Akzeptiert einen Wert



### `--2fa`, `-t`



Überprüfen Sie, ob 2FA für die Organisation in Adobe Admin Console aktiviert ist. Erforderlich beim Aktivieren des Moduls
- Akzeptiert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `admin:adobe-ims:info`

Informationen zur Konfiguration des Adobe IMS-Moduls

```bash
bin/magento admin:adobe-ims:info
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `admin:adobe-ims:status`

Status des Adobe IMS-Moduls

```bash
bin/magento admin:adobe-ims:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `admin:user:create`

Erstellt einen Administrator

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `admin:user:unlock`

Admin-Konto entsperren

```bash
bin/magento admin:user:unlock <username>
```

<!-- app.name --> <!-- command.usage -->

### `username`

Der Benutzername des Administrators, der entsperrt werden soll
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `app:config:dump`

Erstellen einer Sicherungskopie der Anwendung

```bash
bin/magento app:config:dump [<config-types>...]
```

<!-- app.name --> <!-- command.usage -->

### `config-types`

Durch Leerzeichen getrennte Liste von Konfigurationstypen oder Auslassungen zum Ablegen aller [Bereiche, Designs, System, i18n]

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `app:config:import`

Importieren von Daten aus freigegebenen Konfigurationsdateien in den entsprechenden Datenspeicher

```bash
bin/magento app:config:import
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `app:config:status`

Prüft, ob für die Konfigurationsübertragung eine Aktualisierung erforderlich ist

```bash
bin/magento app:config:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `braintree:migrate`

Migrieren gespeicherter Karten aus einer Magento 1-Datenbank

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Hostname/IP. Port ist optional
- Erfordert einen Wert


### `--dbname`

Datenbankname
- Erfordert einen Wert


### `--username`

Datenbank-Benutzername. Muss Lesezugriff haben
- Erfordert einen Wert


### `--password`

Passwort
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cache:clean`

Bereinigt Cache-Typen

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cache:disable`

Deaktiviert Cache-Typen

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cache:enable`

Aktiviert Cache-Typen

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cache:flush`

Leert Cache-Speicher, der von Cache-Typen verwendet wird

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Eine durch Leerzeichen getrennte Liste von Cache-Typen oder das Auslassen, das auf alle Cache-Typen angewendet werden soll.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cache:status`

Überprüft den Cache-Status

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--bootstrap`

Parameter des Bootstrap hinzufügen oder überschreiben
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `catalog:images:resize`

Erstellt in der Größe angepasste Produktbilder

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--async`, `-a`



Bildgröße im asynchronen Modus ändern
- Standard: `false`
- Akzeptiert keinen Wert


### `--skip_hidden_images`

Verarbeiten Sie keine Bilder, die auf der Produktseite als ausgeblendet markiert sind.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `catalog:product:attributes:cleanup`

Entfernt nicht verwendete Produktattribute.

```bash
bin/magento catalog:product:attributes:cleanup
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cms:wysiwyg:restrict`

Festlegen, ob die Überprüfung von HTML-Inhalten durch den Benutzer erzwungen oder stattdessen eine Warnung angezeigt werden soll

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

<!-- app.name --> <!-- command.usage -->

### `restrict`

y\n
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `config:sensitive:set`

Vertrauliche Konfigurationswerte festlegen

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Konfigurationspfad zum Beispiel für group/section/field_name
<!-- argument -->

### `value`

Konfigurationswert
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--interactive`, `-i`



Aktivieren Sie den interaktiven Modus, um alle sensiblen Variablen festzulegen
- Standard: `false`
- Akzeptiert keinen Wert


### `--scope`

Konfigurationsbereich, falls nicht festgelegt, &quot;Standard&quot;verwenden
- Standard: `default`
- Akzeptiert einen Wert


### `--scope-code`

Code für die Konfiguration, standardmäßig leere Zeichenfolge
- Standard: &quot;
- Akzeptiert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `config:set`

Systemkonfiguration ändern

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Konfigurationspfad im Format &quot;section/group/field_name&quot;
- Erforderlich

   <!-- argument -->

### `value`

Konfigurationswert
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Konfigurationsbereich (Standard, Website oder Store)
- Standard: `default`
- Erfordert einen Wert


### `--scope-code`

Code des Umfangs (nur erforderlich, wenn der Umfang nicht &quot;Standard&quot;ist)
- Erfordert einen Wert



### `--lock-env`, `-e`



Sperrwert, der Änderungen im Admin verhindert (wird unter app/etc/env.php gespeichert)
- Standard: `false`
- Akzeptiert keinen Wert



### `--lock-config`, `-c`



Sperren und Freigeben von Werten für andere Installationen, Vermeidung von Änderungen im Admin (wird unter app/etc/config.php gespeichert)
- Standard: `false`
- Akzeptiert keinen Wert



### `--lock`, `-l`



Veraltet, verwenden Sie stattdessen die Option —lock-env .
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `config:show`

Zeigt den Konfigurationswert für den angegebenen Pfad an. Wenn kein Pfad angegeben ist, werden alle gespeicherten Werte angezeigt

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Konfigurationspfad, z. B. section_id/group_id/field_id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Konfigurationsbereich, falls nicht angegeben, wird der Standardbereich verwendet
- Standard: `default`
- Akzeptiert einen Wert


### `--scope-code`

Scope-Code (nur erforderlich, wenn der Bereich nicht `default`)
- Standard: &quot;
- Akzeptiert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cron:install`

Generiert und installiert die Crontab für den aktuellen Benutzer

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Installationsaufgaben erzwingen
- Standard: `false`
- Akzeptiert keinen Wert



### `--non-optional`, `-d`



Installieren Sie nur die nicht optionalen (Standard-) Aufgaben
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cron:remove`

Entfernt Aufgaben aus der Registerkarte &quot;Crontab&quot;

```bash
bin/magento cron:remove
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `cron:run`

Führt Aufträge nach Zeitplan aus

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--group`

Ausführen von Aufträgen nur aus der angegebenen Gruppe
- Erfordert einen Wert


### `--bootstrap`

Hinzufügen oder Überschreiben von Parametern des Bootstrap
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `customer:hash:upgrade`

Hash des Kunden gemäß dem neuesten Algorithmus aktualisieren

```bash
bin/magento customer:hash:upgrade
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `deploy:mode:set`

Anwendungsmodus festlegen.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Der festzulegende Anwendungsmodus. Verfügbare Optionen sind &quot;Entwickler&quot;oder &quot;Produktion&quot;
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-compilation`, `-s`



Überspringt das Löschen und Neugenerieren von statischem Inhalt (generierter Code, vorverarbeitetes CSS und Assets in pub/static/)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `deploy:mode:show`

Zeigt den aktuellen Anwendungsmodus an.

```bash
bin/magento deploy:mode:show
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:di:info`

Enthält Informationen zur Konfiguration der Abhängigkeitsinjizierung für den Befehl.

```bash
bin/magento dev:di:info <class>
```

<!-- app.name --> <!-- command.usage -->

### `class`

Klassenname
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:email:newsletter-compatibility-check`

Überprüft Newsletter-Vorlagen auf potenzielle Kompatibilitätsprobleme bei der Variablennutzung

```bash
bin/magento dev:email:newsletter-compatibility-check
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:email:override-compatibility-check`

Überschreibungen von E-Mail-Vorlagen auf potenzielle Kompatibilitätsprobleme bei der Variablennutzung scannen

```bash
bin/magento dev:email:override-compatibility-check
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:profiler:disable`

Deaktivieren Sie den Profiler.

```bash
bin/magento dev:profiler:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:profiler:enable`

Aktivieren Sie den Profiler.

```bash
bin/magento dev:profiler:enable [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Profiltyp
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:query-log:disable`

DB-Abfrageprotokollierung deaktivieren

```bash
bin/magento dev:query-log:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:query-log:enable`

Aktivieren der DB-Abfrageprotokollierung

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--include-all-queries`

Protokollieren Sie alle Abfragen. [true\|false]
- Standard: `true`
- Akzeptiert einen Wert


### `--query-time-threshold`

Zeitschwellen der Abfrage.
- Standard: `0.001`
- Akzeptiert einen Wert


### `--include-call-stack`

Aufrufstapel einschließen. [true\|false]
- Standard: `true`
- Akzeptiert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:source-theme:deploy`

Erfasst Quelldateien für das Design und veröffentlicht sie.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

<!-- app.name --> <!-- command.usage -->

### `file`

Vorab zu verarbeitende Dateien (Datei sollte ohne Erweiterung angegeben werden)
- Standard: `css/styles-mcss/styles-l`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Typ der Quelldateien: [less]
- Standard: `less`
- Erfordert einen Wert


### `--locale`

Gebietsschema: [en_US]
- Standard: `en_US`
- Erfordert einen Wert


### `--area`

Bereich: [frontend\|adminhtml]
- Standard: `frontend`
- Erfordert einen Wert


### `--theme`

Design: [Anbieter/Design]
- Standard: `Magento/luma`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:template-hints:disable`

Deaktivierung von Frontend-Vorlagenhinweisen. Möglicherweise ist eine Cache-Leerung erforderlich.

```bash
bin/magento dev:template-hints:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:template-hints:enable`

Aktivieren Sie Frontend-Vorlagenhinweise. Möglicherweise ist eine Cache-Leerung erforderlich.

```bash
bin/magento dev:template-hints:enable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:template-hints:status`

Status der Frontend-Vorlagenhinweise anzeigen.

```bash
bin/magento dev:template-hints:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:tests:run`

Führt Tests aus

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Typ des auszuführenden Tests. Verfügbare Typen: alles, Einheit, Integration, alle Integration, statisch, statisch, Integrität, veraltet, Standard
- Standard: `default`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--arguments`, `-c`



Zusätzliche Argumente für PHPUnit. Beispiel: &quot;-c&#39;—filter=MyTest&#39;&quot; (keine Leerzeichen)
- Standard: &quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:urn-catalog:generate`

Generiert den Katalog von URNs zu *.xsd-Zuordnungen, damit die IDE XML hervorhebt.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Pfad zur Datei, um den Katalog auszugeben. Verwenden Sie für PhpStorm .idea/misc.xml
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--ide`

Format, in dem der Katalog erstellt wird. Unterstützt: [phpstorm, vscode]
- Standard: `phpstorm`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `dev:xml:convert`

Konvertiert XML-Dateien mit XSL-Stylesheets

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

<!-- app.name --> <!-- command.usage -->

### `xml-file`

Pfad zur XML-Datei, die umgewandelt werden soll
- Erforderlich

   <!-- argument -->

### `processor`

Pfad zum XSL-Stylesheet, das auf die XML-Datei angewendet werden soll
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--overwrite`, `-o`



XML-Datei überschreiben
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `downloadable:domains:add`

Domänen zur Whitelist für herunterladbare Domänen hinzufügen

```bash
bin/magento downloadable:domains:add [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Domänenname

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `downloadable:domains:remove`

Entfernen von Domänen aus der Whitelist der herunterladbaren Domänen

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Domänennamen

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `downloadable:domains:show`

Anzeigen einer Whitelist für herunterladbare Domänen

```bash
bin/magento downloadable:domains:show
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `encryption:payment-data:update`

Verschlüsselt verschlüsselte Kreditkartendaten mit dem neuesten Verschlüsselungsschlüssel erneut.

```bash
bin/magento encryption:payment-data:update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `i18n:collect-phrases`

Erkennt Ausdrücke in der Codebase

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

<!-- app.name --> <!-- command.usage -->

### `directory`

Pfad zum Analysieren. Nicht erforderlich, wenn die Markierung —magento gesetzt ist
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--output`, `-o`



Pfad (einschließlich Dateiname) zu einer Ausgabedatei. Wenn keine Datei angegeben ist, wird standardmäßig stdout verwendet.
- Erfordert einen Wert



### `--magento`, `-m`



Verwenden Sie den Parameter —magento , um die aktuelle Magento-Codebase zu analysieren. Lassen Sie den Parameter aus, wenn ein Verzeichnis angegeben ist.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `i18n:pack`

Speichert das Sprachpaket

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

<!-- app.name --> <!-- command.usage -->

### `source`

Pfad zur Quellwörterbuchdatei mit Übersetzungen
- Erforderlich

   <!-- argument -->

### `locale`

Zielgebietsschema für Wörterbücher, z. B. &quot;de_DE&quot;
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--mode`, `-m`



Speichermodus für Wörterbuch - &quot;Ersetzen&quot;- Sprachpaket durch neues ersetzen - &quot;Zusammenführen&quot;- Sprachpakete zusammenführen, standardmäßig &quot;Ersetzen&quot;
- Standard: `replace`
- Erfordert einen Wert



### `--allow-duplicates`, `-d`



Verwenden Sie den Parameter —allow-duplicates , um das Speichern von Dubletten der Übersetzung zu ermöglichen. Lassen Sie andernfalls den Parameter weg.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `i18n:uninstall`

Deinstalliert Sprachpakete

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

<!-- app.name --> <!-- command.usage -->

### `package`

Name des Sprachpakets

- Standard: `[]`
- Erforderlich

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--backup-code`, `-b`



Sichern von Code- und Konfigurationsdateien (ohne temporäre Dateien)
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:info`

Zeigt zulässige Indexer an

```bash
bin/magento indexer:info
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:reindex`

Neuindizierung von Daten

```bash
bin/magento indexer:reindex [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:reset`

Setzt den Indexstatus auf ungültig zurück

```bash
bin/magento indexer:reset [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:set-dimensions-mode`

Indexer-Dimensionen-Modus festlegen

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Indexname [catalog_product_price|catalogpermissions_category]
<!-- argument -->

### `mode`

Indexdimensionsmodi catalog_product_price none,website,customer_group,website_and_customer_group catalogpermissions_category none,customer_group
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:set-mode`

Legt den Indexmodustyp fest

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Indexmodustyp [realtime|schedule]
<!-- argument -->

### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:show-dimensions-mode`

Zeigt den Indexer-Dimension-Modus an

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Durch Leerzeichen getrennte Liste von Indextypen oder Unterlassen der Anwendung auf alle Indizes (catalog_product_price,catalogpermissions_category)

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:show-mode`

Zeigt den Indexmodus an

```bash
bin/magento indexer:show-mode [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `indexer:status`

Zeigt den Status des Indexers an

```bash
bin/magento indexer:status [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Eine durch Leerzeichen getrennte Liste von Indextypen oder lassen Sie die Anwendung auf alle Indizes weg.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:adminuri`

Zeigt den Magento-Admin-URI an

```bash
bin/magento info:adminuri
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:backups:list`

Druckt die Liste der verfügbaren Backup-Dateien

```bash
bin/magento info:backups:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:currency:list`

Zeigt die Liste der verfügbaren Währungen an

```bash
bin/magento info:currency:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:dependencies:show-framework`

Zeigt die Anzahl der Abhängigkeiten vom Magento-Framework an

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Berichtsdateiname
- Standard: `framework-dependencies.csv`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules`

Zeigt die Anzahl der Abhängigkeiten zwischen Modulen an

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Berichtsdateiname
- Standard: `modules-dependencies.csv`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules-circular`

Zeigt die Anzahl der zirkulären Abhängigkeiten zwischen Modulen an

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Berichtsdateiname
- Standard: `modules-circular-dependencies.csv`
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:language:list`

Zeigt die Liste der verfügbaren Sprachgebietsschemata an

```bash
bin/magento info:language:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `info:timezone:list`

Zeigt die Liste der verfügbaren Zeitzonen an

```bash
bin/magento info:timezone:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `inventory:reservation:create-compensations`

Erstellen von Vorbehalten aus den vorgelegten Ausgleichsargumenten

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

<!-- app.name --> <!-- command.usage -->

### `compensations`

Liste der Ausgleichsargumente im Format &quot;&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--raw`, `-r`



Rohausgabe
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `inventory:reservation:list-inconsistencies`

Alle Bestellungen und Produkte mit Inkonsistenzen bei der Verkaufsmenge anzeigen

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--complete-orders`, `-c`



Nur Inkonsistenzen für vollständige Bestellungen anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--incomplete-orders`, `-i`



Nur Inkonsistenzen für unvollständige Bestellungen anzeigen
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



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `inventory-geonames:import`

Herunterladen und Importieren von Geo-Namen für den Quellauswahlalgorithmus

```bash
bin/magento inventory-geonames:import <countries>...
```

<!-- app.name --> <!-- command.usage -->

### `countries`

Liste der zu importierenden Ländercodes

- Standard: `[]`
- Erforderlich

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `maintenance:allow-ips`

Legt IPs ohne Wartungsmodus fest

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

<!-- app.name --> <!-- command.usage -->

### `ip`

Zulässige IP-Adressen

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--none`

Löschen zulässiger IP-Adressen
- Standard: `false`
- Akzeptiert keinen Wert


### `--add`

Hinzufügen der IP-Adresse zur vorhandenen Liste
- Standard: `false`
- Akzeptiert keinen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `maintenance:disable`

Deaktiviert den Wartungsmodus

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Zulässige IP-Adressen (verwenden Sie &quot;Keine&quot;, um die zulässige IP-Liste zu löschen)
- Standard: `[]`
- Erfordert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `maintenance:enable`

Aktiviert den Wartungsmodus

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Zulässige IP-Adressen (verwenden Sie &quot;Keine&quot;, um die zulässige IP-Liste zu löschen)
- Standard: `[]`
- Erfordert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `maintenance:status`

Zeigt den Status des Wartungsmodus an

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `media-content:sync`

Synchronisieren von Inhalten mit Assets

```bash
bin/magento media-content:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `media-gallery:sync`

Synchronisieren von Medienspeichern und Medien-Assets in der Datenbank

```bash
bin/magento media-gallery:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `module:config:status`

Prüft die Modulkonfiguration in der Datei &quot;app/etc/config.php&quot;und meldet, ob sie aktuell ist oder nicht

```bash
bin/magento module:config:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `module:disable`

Deaktiviert angegebene Module

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Name des Moduls

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Prüfung von Abhängigkeiten umgehen
- Standard: `false`
- Akzeptiert keinen Wert


### `--all`

Alle Module deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--clear-static-content`, `-c`



Löschen Sie die generierten statischen Ansichtsdateien. Erforderlich, wenn die Module statische Ansichtsdateien haben
- Standard: `false`
- Akzeptiert keinen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `module:enable`

Aktiviert die angegebenen Module

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Name des Moduls

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Prüfung von Abhängigkeiten umgehen
- Standard: `false`
- Akzeptiert keinen Wert


### `--all`

Alle Module aktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--clear-static-content`, `-c`



Löschen Sie die generierten statischen Ansichtsdateien. Erforderlich, wenn die Module statische Ansichtsdateien haben
- Standard: `false`
- Akzeptiert keinen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `module:status`

Status der Module anzeigen

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

<!-- app.name --> <!-- command.usage -->

### `module-names`

Optionaler Modulname

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--enabled`

Schreibgeschützte Module
- Standard: `false`
- Akzeptiert keinen Wert


### `--disabled`

Nur deaktivierte Module drucken
- Standard: `false`
- Akzeptiert keinen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `module:uninstall`

Deinstalliert vom Composer installierte Module

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

<!-- app.name --> <!-- command.usage -->

### `module`

Name des Moduls

- Standard: `[]`
- Erforderlich

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--remove-data`, `-r`



Von Modulen installierte Daten entfernen
- Standard: `false`
- Akzeptiert keinen Wert


### `--backup-code`

Sichern von Code- und Konfigurationsdateien (ohne temporäre Dateien)
- Standard: `false`
- Akzeptiert keinen Wert


### `--backup-media`

Mediensicherung durchführen
- Standard: `false`
- Akzeptiert keinen Wert


### `--backup-db`

Führen Sie eine vollständige Datenbanksicherung durch.
- Standard: `false`
- Akzeptiert keinen Wert


### `--non-composer`

Alle Module, die hier vorbei sein werden, sind nicht auf Composer basiert
- Standard: `false`
- Akzeptiert keinen Wert



### `--clear-static-content`, `-c`



Löschen Sie die generierten statischen Ansichtsdateien. Erforderlich, wenn die Module statische Ansichtsdateien haben
- Standard: `false`
- Akzeptiert keinen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `newrelic:create:deploy-marker`

Überprüfen Sie die Bereitstellungswarteschlange auf Einträge und erstellen Sie eine entsprechende Bereitstellungsmarkierung.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

<!-- app.name --> <!-- command.usage -->

### `message`

Nachricht bereitstellen?
- Erforderlich

   <!-- argument -->

### `change_log`

Änderungsprotokoll?
- Erforderlich

   <!-- argument -->

### `user`

Bereitstellungsbenutzer
<!-- argument -->

### `revision`

Revision
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `queue:consumers:list`

Liste der MessageQueue-Verbraucher

```bash
bin/magento queue:consumers:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `queue:consumers:start`

MessageQueue Consumer starten

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

<!-- app.name --> <!-- command.usage -->

### `consumer`

Der Name des zu startenden Verbrauchers.
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--max-messages`

Die Anzahl der Nachrichten, die vom Verbraucher vor der Beendigung des Vorgangs verarbeitet werden. Wenn nicht angegeben - beenden Sie nach der Verarbeitung aller in die Warteschlange gestellten Nachrichten.
- Erfordert einen Wert


### `--batch-size`

Die Anzahl der Nachrichten pro Batch. Gilt nur für den Batch-Verbraucher.
- Erfordert einen Wert


### `--area-code`

Der bevorzugte Bereich (global, adminhtml usw.) ist standardmäßig global.
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



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `remote-storage:sync`

Synchronisieren Sie Mediendateien mit Remote-Speicher.

```bash
bin/magento remote-storage:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `sampledata:deploy`

Bereitstellen von Beispieldatenmodulen für Composer-basierte Magento-Installationen

```bash
bin/magento sampledata:deploy [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Aktualisieren von Composer.json ohne Ausführen der Komponentenaktualisierung
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `sampledata:remove`

Entfernen Sie alle Beispieldatenpakete aus Composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Aktualisieren von Composer.json ohne Ausführen der Komponentenaktualisierung
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `sampledata:reset`

Alle Beispieldatenmodule zur Neuinstallation zurücksetzen

```bash
bin/magento sampledata:reset
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-forgot-password`

Deaktivieren Sie reCAPTCHA für das Kennwortformular für Administratoren, die das Kennwort vergessen haben

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-login`

Deaktivieren Sie reCAPTCHA für das Anmeldeformular für Administratoren

```bash
bin/magento security:recaptcha:disable-for-user-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `security:tfa:google:set-secret`

Legen Sie das für die OTP-Generierung von Google verwendete Geheimnis fest.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Benutzername
- Erforderlich

   <!-- argument -->

### `secret`

Geheimnis
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `security:tfa:providers`

Alle verfügbaren Anbieter auflisten

```bash
bin/magento security:tfa:providers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `security:tfa:reset`

Konfiguration für einen Benutzer zurücksetzen

```bash
bin/magento security:tfa:reset <user> <provider>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Benutzername
- Erforderlich

   <!-- argument -->

### `provider`

Provider-Code
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:backup`

Backup von Magento Application Code-Basis, Medien und Datenbank

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--code`

Sichern von Code- und Konfigurationsdateien (ohne temporäre Dateien)
- Standard: `false`
- Akzeptiert keinen Wert


### `--media`

Mediensicherung durchführen
- Standard: `false`
- Akzeptiert keinen Wert


### `--db`

Führen Sie eine vollständige Datenbanksicherung durch.
- Standard: `false`
- Akzeptiert keinen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:config:set`

Erstellt oder ändert die Bereitstellungskonfiguration

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)
- Erfordert einen Wert


### `--enable-debug-logging`

Debug-Protokollierung aktivieren
- Erfordert einen Wert


### `--enable-syslog-logging`

Aktivieren der syslog-Protokollierung
- Erfordert einen Wert


### `--remote-storage-driver`

Remote-Speichertreiber
- Erfordert einen Wert


### `--remote-storage-prefix`

Remote-Speicherpräfix
- Standard: &quot;
- Erfordert einen Wert


### `--remote-storage-endpoint`

Remote-Speicherendpunkt
- Erfordert einen Wert


### `--remote-storage-bucket`

Remote-Speicher-Bucket
- Erfordert einen Wert


### `--remote-storage-region`

Remote-Speicherregion
- Erfordert einen Wert


### `--remote-storage-key`

Zugriffsschlüssel für Remote-Speicher
- Standard: &quot;
- Erfordert einen Wert


### `--remote-storage-secret`

geheimer Schlüssel für Remote-Speicher
- Standard: &quot;
- Erfordert einen Wert


### `--remote-storage-path-style`

Pfad für Remote-Speicher - Stil
- Standard: `0`
- Erfordert einen Wert


### `--checkout-async`

Asynchrone Auftragsverarbeitung aktivieren? 1 - Ja, 0 - Nein
- Erfordert einen Wert


### `--amqp-host`

AMQP-Server-Host
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-port`

AMQP-Server-Anschluss
- Standard: `5672`
- Erfordert einen Wert


### `--amqp-user`

AMQP-Server-Benutzername
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-password`

AMQP-Server-Kennwort
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-virtualhost`

Amqp virtualhost
- Standard: `/`
- Erfordert einen Wert


### `--amqp-ssl`

AMQP SSL
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-ssl-options`

AMQP-SSL-Optionen (JSON)
- Standard: &quot;
- Erfordert einen Wert


### `--consumers-wait-for-messages`

Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein
- Erfordert einen Wert


### `--queue-default-connection`

Die Standardverbindung der Nachrichtenwarteschlangen wird festgelegt. Kann &#39;db&#39;, &#39;amqp&#39; oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert sein, andernfalls werden Nachrichten nicht korrekt verarbeitet.
- Erfordert einen Wert


### `--deferred-total-calculating`

Verzögerte Gesamtberechnung aktivieren? 1 - Ja, 0 - Nein
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

Benutzername des Datenbankservers
- Erfordert einen Wert


### `--db-engine`

Datenbank-Server-Engine
- Erfordert einen Wert


### `--db-password`

Datenbankserver-Kennwort
- Erfordert einen Wert


### `--db-prefix`

Datenbanktabellenpräfix
- Erfordert einen Wert


### `--db-model`

Datenbanktyp
- Erfordert einen Wert


### `--db-init-statements`

Grundmenge an Befehlen in der Datenbank
- Erfordert einen Wert



### `--skip-db-validation`, `-s`



Wenn angegeben, wird die Überprüfung der db-Verbindung übersprungen
- Standard: `false`
- Akzeptiert keinen Wert


### `--http-cache-hosts`

HTTP-Cache-Hosts
- Erfordert einen Wert


### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei, um die DB-Verbindung über SSL herzustellen
- Standard: &quot;
- Erfordert einen Wert


### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei, um die DB-Verbindung über SSL herzustellen
- Standard: &quot;
- Erfordert einen Wert


### `--db-ssl-ca`

Vollständiger Pfad der Datei mit dem Serverzertifikat, um die DB-Verbindung über SSL herzustellen
- Standard: &quot;
- Erfordert einen Wert


### `--db-ssl-verify`

Serverzertifizierung überprüfen
- Standard: `false`
- Akzeptiert keinen Wert


### `--session-save`

Sitzungsspeicherhandler
- Erfordert einen Wert


### `--session-save-redis-host`

Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets
- Erfordert einen Wert


### `--session-save-redis-port`

Überwachungsanschluss des Redis-Servers
- Erfordert einen Wert


### `--session-save-redis-password`

Redis-Serverkennwort
- Erfordert einen Wert


### `--session-save-redis-timeout`

Zeitüberschreitung bei Verbindung in Sekunden
- Erfordert einen Wert


### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen
- Erfordert einen Wert


### `--session-save-redis-db`

Rediv-Datenbanknummer
- Erfordert einen Wert


### `--session-save-redis-compression-threshold`

Schwelle für Rediv-Komprimierung
- Erfordert einen Wert


### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy
- Erfordert einen Wert


### `--session-save-redis-log-level`

Redis log level. Werte: 0 (am wenigsten ausführlich) bis 7 (am ausführlichsten)
- Erfordert einen Wert


### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperrung einer Sitzung warten können
- Erfordert einen Wert


### `--session-save-redis-break-after-frontend`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, ein Schloss für die Frontend-Sitzung zu brechen
- Erfordert einen Wert


### `--session-save-redis-break-after-adminhtml`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, eine Sperre für die Admin-Sitzung zu unterbrechen
- Erfordert einen Wert


### `--session-save-redis-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Nicht-Bots beim ersten Schreiben (verwenden Sie 0, um zu deaktivieren)
- Erfordert einen Wert


### `--session-save-redis-bot-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Bots beim ersten Schreiben (verwenden Sie 0 zur Deaktivierung)
- Erfordert einen Wert


### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (verwenden Sie 0 zur Deaktivierung)
- Erfordert einen Wert


### `--session-save-redis-disable-locking`

Redis deaktivieren die Sperrung. Werte: false (Standard), true
- Erfordert einen Wert


### `--session-save-redis-min-lifetime`

Redis min session lifetime in seconds
- Erfordert einen Wert


### `--session-save-redis-max-lifetime`

Gibt die maximale Sitzungslebensdauer in Sekunden zurück.
- Erfordert einen Wert


### `--session-save-redis-sentinel-master`

Redis Sentinel Übergeordnet
- Erfordert einen Wert


### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommas getrennt
- Erfordert einen Wert


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifizieren Übergeordnet. Werte: false (Standard), true
- Erfordert einen Wert


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel Connect-Neuversuche.
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

Überwachungsanschluss des Redis-Servers
- Erfordert einen Wert


### `--cache-backend-redis-password`

Redis-Serverkennwort
- Erfordert einen Wert


### `--cache-backend-redis-compress-data`

Auf 0 setzen, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)
- Erfordert einen Wert


### `--cache-backend-redis-compression-lib`

Zu verwendende Komprimierungsbibliothek [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)
- Erfordert einen Wert


### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel
- Erfordert einen Wert


### `--allow-parallel-generation`

Cache nicht blockieren lassen
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

Überwachungsanschluss des Redis-Servers
- Erfordert einen Wert


### `--page-cache-redis-password`

Redis-Serverkennwort
- Erfordert einen Wert


### `--page-cache-redis-compress-data`

Auf 1 setzen, um den gesamten Seiten-Cache zu komprimieren (verwenden Sie 0, um ihn zu deaktivieren)
- Erfordert einen Wert


### `--page-cache-redis-compression-lib`

Zu verwendende Komprimierungsbibliothek [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)
- Erfordert einen Wert


### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel
- Erfordert einen Wert


### `--lock-provider`

Name des Anbieters sperren
- Erfordert einen Wert


### `--lock-db-prefix`

Installation-spezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten
- Erfordert einen Wert


### `--lock-zookeeper-host`

Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster. Beispiel: 127.0.0.1:2181
- Erfordert einen Wert


### `--lock-zookeeper-path`

Der Pfad, in dem Zookeeper Sperren speichert. Der Standardpfad lautet: /magento/lock
- Erfordert einen Wert


### `--lock-file-path`

Der Pfad, in dem Dateisperren gespeichert werden.
- Erfordert einen Wert


### `--document-root-is-pub`

Flag zum Anzeigen, ob Pub sich auf dem Stamm befindet, kann nur &quot;true&quot;oder &quot;false&quot;sein
- Erfordert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-data:upgrade`

Installiert und aktualisiert Daten in der DB

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-patch`

Erstellen Sie einen Patch und legen Sie ihn in einen bestimmten Ordner.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

<!-- app.name --> <!-- command.usage -->

### `module`

Modulname
- Erforderlich

   <!-- argument -->

### `patch`

Patch name
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--revertable`

Überprüfen Sie, ob der Patch rückgängig gemacht werden kann oder nicht.
- Standard: `false`
- Akzeptiert einen Wert


### `--type`

Finden Sie heraus, welcher Patch-Typ generiert werden soll. Verfügbare Werte: `data`, `schema`.
- Standard: `data`
- Akzeptiert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-whitelist`

Generieren einer Whitelist von Tabellen und Spalten, die vom Deklarationinstallationsprogramm bearbeitet werden dürfen

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--module-name`

Name des Moduls, für das eine Whitelist generiert wird
- Standard: `all`
- Akzeptiert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-schema:add-slave`

Checkout-zifferbezogene Tabellen in einen separaten DB-Server verschieben

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

DB-Server-Host auswählen
- Standard: `localhost`
- Erfordert einen Wert


### `--dbname`

Slave-Datenbankname
- Erfordert einen Wert


### `--username`

DB-Benutzername herunterladen
- Standard: `root`
- Erfordert einen Wert


### `--password`

DB-Benutzerkennwort speichern
- Akzeptiert einen Wert


### `--connection`

Slave-Verbindungsname
- Standard: `default`
- Akzeptiert einen Wert


### `--resource`

Slave-Ressourcenname
- Standard: `default`
- Akzeptiert einen Wert


### `--maxAllowedLag`

Max. zulässige Lag-Slave-Verbindung (in Sekunden)
- Standard: &quot;
- Akzeptiert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-schema:split-quote`

Verschieben Sie die mit Checkout verbundenen Tabellen an einen separaten DB-Server. Veraltet seit 2.4.2 und wird entfernt

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Checkout für DB Server-Host
- Erfordert einen Wert


### `--dbname`

Checkout-Datenbankname
- Erfordert einen Wert


### `--username`

Checkout DB-Benutzername
- Erfordert einen Wert


### `--password`

DB-Benutzerkennwort auschecken
- Akzeptiert einen Wert


### `--connection`

Checkout-Verbindungsname
- Standard: `checkout`
- Akzeptiert einen Wert


### `--resource`

Checkout-Ressourcenname
- Standard: `checkout`
- Akzeptiert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-schema:split-sales`

Verschieben Sie umsatzbezogene Tabellen auf einen separaten DB-Server. Veraltet seit 2.4.2 und wird entfernt

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Sales DB Server-Host
- Erfordert einen Wert


### `--dbname`

Name der Verkaufsdatenbank
- Erfordert einen Wert


### `--username`

Name des DB-Vertriebsbenutzers
- Erfordert einen Wert


### `--password`

Benutzerpasswort von Sales DB
- Akzeptiert einen Wert


### `--connection`

Name der Verkaufsverbindung
- Standard: `sales`
- Akzeptiert einen Wert


### `--resource`

Name der Verkaufsressource
- Standard: `sales`
- Akzeptiert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db-schema:upgrade`

Installation und Aktualisierung des DB-Schemas

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--convert-old-scripts`

Konvertiert alte Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml
- Standard: `false`
- Akzeptiert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:db:status`

Prüft, ob für das DB-Schema oder die Daten eine Aktualisierung erforderlich ist

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:di:compile`

Generiert ID-Konfiguration und alle fehlenden Klassen, die automatisch generiert werden können

```bash
bin/magento setup:di:compile
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:install`

Installation der Magento-Anwendung

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Backend-Frontname (wird automatisch generiert, wenn fehlt)
- Erfordert einen Wert


### `--enable-debug-logging`

Debug-Protokollierung aktivieren
- Erfordert einen Wert


### `--enable-syslog-logging`

Aktivieren der syslog-Protokollierung
- Erfordert einen Wert


### `--remote-storage-driver`

Remote-Speichertreiber
- Erfordert einen Wert


### `--remote-storage-prefix`

Remote-Speicherpräfix
- Standard: &quot;
- Erfordert einen Wert


### `--remote-storage-endpoint`

Remote-Speicherendpunkt
- Erfordert einen Wert


### `--remote-storage-bucket`

Remote-Speicher-Bucket
- Erfordert einen Wert


### `--remote-storage-region`

Remote-Speicherregion
- Erfordert einen Wert


### `--remote-storage-key`

Zugriffsschlüssel für Remote-Speicher
- Standard: &quot;
- Erfordert einen Wert


### `--remote-storage-secret`

geheimer Schlüssel für Remote-Speicher
- Standard: &quot;
- Erfordert einen Wert


### `--remote-storage-path-style`

Pfad für Remote-Speicher - Stil
- Standard: `0`
- Erfordert einen Wert


### `--checkout-async`

Asynchrone Auftragsverarbeitung aktivieren? 1 - Ja, 0 - Nein
- Erfordert einen Wert


### `--amqp-host`

AMQP-Server-Host
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-port`

AMQP-Server-Anschluss
- Standard: `5672`
- Erfordert einen Wert


### `--amqp-user`

AMQP-Server-Benutzername
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-password`

AMQP-Server-Kennwort
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-virtualhost`

Amqp virtualhost
- Standard: `/`
- Erfordert einen Wert


### `--amqp-ssl`

AMQP SSL
- Standard: &quot;
- Erfordert einen Wert


### `--amqp-ssl-options`

AMQP-SSL-Optionen (JSON)
- Standard: &quot;
- Erfordert einen Wert


### `--consumers-wait-for-messages`

Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein
- Erfordert einen Wert


### `--queue-default-connection`

Die Standardverbindung der Nachrichtenwarteschlangen wird festgelegt. Kann &#39;db&#39;, &#39;amqp&#39; oder ein benutzerdefiniertes Warteschlangensystem sein. Das Warteschlangensystem muss installiert und konfiguriert sein, andernfalls werden Nachrichten nicht korrekt verarbeitet.
- Erfordert einen Wert


### `--deferred-total-calculating`

Verzögerte Gesamtberechnung aktivieren? 1 - Ja, 0 - Nein
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

Benutzername des Datenbankservers
- Erfordert einen Wert


### `--db-engine`

Datenbank-Server-Engine
- Erfordert einen Wert


### `--db-password`

Datenbankserver-Kennwort
- Erfordert einen Wert


### `--db-prefix`

Datenbanktabellenpräfix
- Erfordert einen Wert


### `--db-model`

Datenbanktyp
- Erfordert einen Wert


### `--db-init-statements`

Grundmenge an Befehlen in der Datenbank
- Erfordert einen Wert



### `--skip-db-validation`, `-s`



Wenn angegeben, wird die Überprüfung der db-Verbindung übersprungen
- Standard: `false`
- Akzeptiert keinen Wert


### `--http-cache-hosts`

HTTP-Cache-Hosts
- Erfordert einen Wert


### `--db-ssl-key`

Vollständiger Pfad der Client-Schlüsseldatei, um die DB-Verbindung über SSL herzustellen
- Standard: &quot;
- Erfordert einen Wert


### `--db-ssl-cert`

Vollständiger Pfad der Client-Zertifikatdatei, um die DB-Verbindung über SSL herzustellen
- Standard: &quot;
- Erfordert einen Wert


### `--db-ssl-ca`

Vollständiger Pfad der Datei mit dem Serverzertifikat, um die DB-Verbindung über SSL herzustellen
- Standard: &quot;
- Erfordert einen Wert


### `--db-ssl-verify`

Serverzertifizierung überprüfen
- Standard: `false`
- Akzeptiert keinen Wert


### `--session-save`

Sitzungsspeicherhandler
- Erfordert einen Wert


### `--session-save-redis-host`

Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets
- Erfordert einen Wert


### `--session-save-redis-port`

Überwachungsanschluss des Redis-Servers
- Erfordert einen Wert


### `--session-save-redis-password`

Redis-Serverkennwort
- Erfordert einen Wert


### `--session-save-redis-timeout`

Zeitüberschreitung bei Verbindung in Sekunden
- Erfordert einen Wert


### `--session-save-redis-persistent-id`

Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen
- Erfordert einen Wert


### `--session-save-redis-db`

Rediv-Datenbanknummer
- Erfordert einen Wert


### `--session-save-redis-compression-threshold`

Schwelle für Rediv-Komprimierung
- Erfordert einen Wert


### `--session-save-redis-compression-lib`

Redis-Komprimierungsbibliothek. Werte: gzip (Standard), lzf, lz4, snappy
- Erfordert einen Wert


### `--session-save-redis-log-level`

Redis log level. Werte: 0 (am wenigsten ausführlich) bis 7 (am ausführlichsten)
- Erfordert einen Wert


### `--session-save-redis-max-concurrency`

Maximale Anzahl von Prozessen, die auf eine Sperrung einer Sitzung warten können
- Erfordert einen Wert


### `--session-save-redis-break-after-frontend`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, ein Schloss für die Frontend-Sitzung zu brechen
- Erfordert einen Wert


### `--session-save-redis-break-after-adminhtml`

Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, eine Sperre für die Admin-Sitzung zu unterbrechen
- Erfordert einen Wert


### `--session-save-redis-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Nicht-Bots beim ersten Schreiben (verwenden Sie 0, um zu deaktivieren)
- Erfordert einen Wert


### `--session-save-redis-bot-first-lifetime`

Lebensdauer (in Sekunden) der Sitzung für Bots beim ersten Schreiben (verwenden Sie 0 zur Deaktivierung)
- Erfordert einen Wert


### `--session-save-redis-bot-lifetime`

Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen (verwenden Sie 0 zur Deaktivierung)
- Erfordert einen Wert


### `--session-save-redis-disable-locking`

Redis deaktivieren die Sperrung. Werte: false (Standard), true
- Erfordert einen Wert


### `--session-save-redis-min-lifetime`

Redis min session lifetime in seconds
- Erfordert einen Wert


### `--session-save-redis-max-lifetime`

Gibt die maximale Sitzungslebensdauer in Sekunden zurück.
- Erfordert einen Wert


### `--session-save-redis-sentinel-master`

Redis Sentinel Übergeordnet
- Erfordert einen Wert


### `--session-save-redis-sentinel-servers`

Redis Sentinel-Server, durch Kommas getrennt
- Erfordert einen Wert


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifizieren Übergeordnet. Werte: false (Standard), true
- Erfordert einen Wert


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel Connect-Neuversuche.
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

Überwachungsanschluss des Redis-Servers
- Erfordert einen Wert


### `--cache-backend-redis-password`

Redis-Serverkennwort
- Erfordert einen Wert


### `--cache-backend-redis-compress-data`

Auf 0 setzen, um die Komprimierung zu deaktivieren (Standard ist 1, aktiviert)
- Erfordert einen Wert


### `--cache-backend-redis-compression-lib`

Zu verwendende Komprimierungsbibliothek [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)
- Erfordert einen Wert


### `--cache-id-prefix`

ID-Präfix für Cache-Schlüssel
- Erfordert einen Wert


### `--allow-parallel-generation`

Cache nicht blockieren lassen
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

Überwachungsanschluss des Redis-Servers
- Erfordert einen Wert


### `--page-cache-redis-password`

Redis-Serverkennwort
- Erfordert einen Wert


### `--page-cache-redis-compress-data`

Auf 1 setzen, um den gesamten Seiten-Cache zu komprimieren (verwenden Sie 0, um ihn zu deaktivieren)
- Erfordert einen Wert


### `--page-cache-redis-compression-lib`

Zu verwendende Komprimierungsbibliothek [snappy,lzf,l4z,zstd,gzip] (Leer lassen, um automatisch zu bestimmen)
- Erfordert einen Wert


### `--page-cache-id-prefix`

ID-Präfix für Cache-Schlüssel
- Erfordert einen Wert


### `--lock-provider`

Name des Anbieters sperren
- Erfordert einen Wert


### `--lock-db-prefix`

Installation-spezifisches Sperrpräfix zur Vermeidung von Sperrkonflikten
- Erfordert einen Wert


### `--lock-zookeeper-host`

Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster. Beispiel: 127.0.0.1:2181
- Erfordert einen Wert


### `--lock-zookeeper-path`

Der Pfad, in dem Zookeeper Sperren speichert. Der Standardpfad lautet: /magento/lock
- Erfordert einen Wert


### `--lock-file-path`

Der Pfad, in dem Dateisperren gespeichert werden.
- Erfordert einen Wert


### `--document-root-is-pub`

Flag zum Anzeigen, ob Pub sich auf dem Stamm befindet, kann nur &quot;true&quot;oder &quot;false&quot;sein
- Erfordert einen Wert


### `--base-url`

URL, unter der der Store verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url
- Erfordert einen Wert


### `--language`

Standardsprachcode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code
- Erfordert einen Wert


### `--timezone`

Standardmäßiger Zeitzonen-Code. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone
- Erfordert einen Wert


### `--currency`

Standardwährungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow
- Erfordert einen Wert


### `--use-rewrites`

Verwenden Sie Neuschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites
- Erfordert einen Wert


### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend
- Erfordert einen Wert


### `--base-url-secure`

Basis-URL für SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url
- Erfordert einen Wert


### `--use-secure-admin`

Führen Sie die Admin-Oberfläche mit SSL aus. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml
- Erfordert einen Wert


### `--admin-use-security-key`

Gibt an, ob eine Funktion des &quot;Sicherheitsschlüssels&quot;in Magento-Admin-URLs und -Formularen verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key .
- Erfordert einen Wert


### `--admin-user`

Admin-Benutzer
- Akzeptiert einen Wert


### `--admin-password`

Administratorkennwort
- Akzeptiert einen Wert


### `--admin-email`

Admin-E-Mail
- Akzeptiert einen Wert


### `--admin-firstname`

Vorname des Administrators
- Akzeptiert einen Wert


### `--admin-lastname`

Nachname des Administrators
- Akzeptiert einen Wert


### `--search-engine`

Suchmaschine. Werte: elasticsearch5, elasticsearch6, elasticsearch7
- Erfordert einen Wert


### `--elasticsearch-host`

Elasticsearch-Server-Host.
- Erfordert einen Wert


### `--elasticsearch-port`

Elasticsearch-Server-Anschluss.
- Erfordert einen Wert


### `--elasticsearch-enable-auth`

Auf 1 setzen, um die Authentifizierung zu aktivieren. (Standardwert ist 0, deaktiviert)
- Erfordert einen Wert


### `--elasticsearch-username`

Benutzername des Elasticsearchs. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist
- Erfordert einen Wert


### `--elasticsearch-password`

Passwort des Elasticsearchs. Nur anwendbar, wenn HTTP-Authentifizierung aktiviert ist
- Erfordert einen Wert


### `--elasticsearch-index-prefix`

Elasticsearch-Indexpräfix.
- Erfordert einen Wert


### `--elasticsearch-timeout`

Zeitüberschreitung des Elasticsearch-Servers.
- Erfordert einen Wert


### `--cleanup-database`

Bereinigen der Datenbank vor der Installation
- Standard: `false`
- Akzeptiert keinen Wert


### `--sales-order-increment-prefix`

Präfix der Bestellnummer
- Erfordert einen Wert


### `--use-sample-data`

Beispieldaten verwenden
- Standard: `false`
- Akzeptiert keinen Wert


### `--enable-modules`

Liste mit kommagetrennten Modulnamen. Dies muss während der Installation enthalten sein. Verfügbarer Zauberparam &quot;all&quot;.
- Akzeptiert einen Wert


### `--disable-modules`

Liste mit kommagetrennten Modulnamen. Dies muss während der Installation vermieden werden. Verfügbarer Zauberparam &quot;all&quot;.
- Akzeptiert einen Wert


### `--convert-old-scripts`

Konvertiert alte Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml
- Standard: `false`
- Akzeptiert einen Wert



### `--interactive`, `-i`



Installation interaktiver Magentos
- Standard: `false`
- Akzeptiert keinen Wert


### `--safe-mode`

Sichere Installation von Magento mit Dumps auf destruktiven Vorgängen, z. B. Spaltenentfernung
- Akzeptiert einen Wert


### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps
- Akzeptiert einen Wert


### `--dry-run`

Magento-Installation wird im Trockenlaufmodus ausgeführt
- Standard: `false`
- Akzeptiert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:performance:generate-fixtures`

Generiert Fehlerbehebungen

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

<!-- app.name --> <!-- command.usage -->

### `profile`

Pfad zur Profilkonfigurationsdatei
- Erforderlich

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-reindex`, `-s`



Neuindizierung überspringen
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:rollback`

Zurücksetzen von Magento Application Codebase, Media und Datenbank

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--code-file`, `-c`



Name der Code-Sicherungsdatei in var/backup
- Erfordert einen Wert



### `--media-file`, `-m`



Name der Mediensicherungsdatei in var/backup
- Erfordert einen Wert



### `--db-file`, `-d`



Name der Datenbanksicherungsdatei in var/backup
- Erfordert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:static-content:deploy`

Stellt statische Ansichtsdateien bereit

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

<!-- app.name --> <!-- command.usage -->

### `languages`

Durch Leerzeichen getrennte Liste von ISO-639-Sprachcodes, für die statische Ansichtsdateien ausgegeben werden sollen.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Bereitstellen von Dateien in einem beliebigen Modus.
- Standard: `false`
- Akzeptiert keinen Wert



### `--strategy`, `-s`



Stellen Sie Dateien mithilfe der angegebenen Strategie bereit.
- Standard: `quick`
- Akzeptiert einen Wert



### `--area`, `-a`



Generieren Sie Dateien nur für die angegebenen Bereiche.
- Standard: `all`
- Akzeptiert mehrere Werte


### `--exclude-area`

Generieren Sie keine Dateien für die angegebenen Bereiche.
- Standard: `none`
- Akzeptiert mehrere Werte



### `--theme`, `-t`



Generieren Sie statische Ansichtsdateien nur für die angegebenen Designs.
- Standard: `all`
- Akzeptiert mehrere Werte


### `--exclude-theme`

Generieren Sie keine Dateien für die angegebenen Designs.
- Standard: `none`
- Akzeptiert mehrere Werte



### `--language`, `-l`



Generieren Sie Dateien nur für die angegebenen Sprachen.
- Standard: `all`
- Akzeptiert mehrere Werte


### `--exclude-language`

Generieren Sie keine Dateien für die angegebenen Sprachen.
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

Erstellen Sie Symlinks für die Dateien dieser Gebietsschemas, die zur Bereitstellung übergeben werden, aber keine Anpassungen aufweisen.
- Standard: `false`
- Akzeptiert keinen Wert


### `--content-version`

Benutzerdefinierte Version von statischem Inhalt kann verwendet werden, wenn die Bereitstellung auf mehreren Knoten ausgeführt wird, um sicherzustellen, dass die statische Inhaltsversion identisch ist und die Zwischenspeicherung ordnungsgemäß funktioniert.
- Erfordert einen Wert


### `--refresh-content-version-only`

Das Aktualisieren der Version statischer Inhalte kann nur verwendet werden, um statische Inhalte im Browser-Cache und CDN-Cache zu aktualisieren.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-javascript`

Stellen Sie keine JavaScript-Dateien bereit.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-js-bundle`

Stellen Sie keine JavaScript-Bundle-Dateien bereit.
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

Stellen Sie keine Bilder bereit.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-fonts`

Stellen Sie keine Schriftartdateien bereit.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-html`

Stellen Sie keine HTML-Dateien bereit.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-misc`

Stellen Sie keine Dateien anderer Typen (.md, .jbf, .csv usw.) bereit.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-html-minify`

Minimieren Sie keine HTML-Dateien.
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-parent`

Kompilieren Sie keine übergeordneten Designs. Wird nur in schnellen und standardmäßigen Strategien unterstützt.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:store-config:set`

Installiert die Store-Konfiguration. Veraltet seit 2.2.0. Verwenden Sie stattdessen config:set .

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--base-url`

URL, unter der der Store verfügbar sein soll. Veraltet, verwenden Sie config:set mit dem Pfad web/unsecure/base_url
- Erfordert einen Wert


### `--language`

Standardsprachcode. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/code
- Erfordert einen Wert


### `--timezone`

Standardmäßiger Zeitzonen-Code. Veraltet, verwenden Sie config:set mit dem Pfad general/locale/timezone
- Erfordert einen Wert


### `--currency`

Standardwährungscode. Veraltet, verwenden Sie config:set mit dem Pfad currency/options/base, currency/options/default und currency/options/allow
- Erfordert einen Wert


### `--use-rewrites`

Verwenden Sie Neuschreibungen. Veraltet, verwenden Sie config:set mit dem Pfad web/seo/use_rewrites
- Erfordert einen Wert


### `--use-secure`

Verwenden Sie sichere URLs. Aktivieren Sie diese Option nur, wenn SSL verfügbar ist. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_frontend
- Erfordert einen Wert


### `--base-url-secure`

Basis-URL für SSL-Verbindung. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/base_url
- Erfordert einen Wert


### `--use-secure-admin`

Führen Sie die Admin-Oberfläche mit SSL aus. Veraltet, verwenden Sie config:set mit dem Pfad web/secure/use_in_adminhtml
- Erfordert einen Wert


### `--admin-use-security-key`

Gibt an, ob eine Funktion des &quot;Sicherheitsschlüssels&quot;in Magento-Admin-URLs und -Formularen verwendet werden soll. Veraltet, verwenden Sie config:set mit dem Pfad admin/security/use_form_key .
- Erfordert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:uninstall`

Deinstalliert die Magento-Anwendung

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `setup:upgrade`

Aktualisieren der Magento-Anwendung, DB-Daten und des Schemas

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep-generated`

Verhindert das Löschen generierter Dateien. Wir empfehlen, diese Option nur bei der Bereitstellung in der Produktion zu verwenden. Weitere Informationen erhalten Sie von Ihrem Systemintegrator oder -administrator.
- Standard: `false`
- Akzeptiert keinen Wert


### `--convert-old-scripts`

Konvertiert alte Skripte (InstallSchema, UpgradeSchema) in das Format db_schema.xml
- Standard: `false`
- Akzeptiert einen Wert


### `--safe-mode`

Sichere Installation von Magento mit Dumps auf destruktiven Vorgängen, z. B. Spaltenentfernung
- Akzeptiert einen Wert


### `--data-restore`

Wiederherstellen entfernter Daten aus Dumps
- Akzeptiert einen Wert


### `--dry-run`

Magento-Installation wird im Trockenlaufmodus ausgeführt
- Standard: `false`
- Akzeptiert einen Wert


### `--magento-init-params`

Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter des Magentos anzupassen. Beispiel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `store:list`

Zeigt die Liste der Stores an

```bash
bin/magento store:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `store:website:list`

Zeigt die Liste der Websites an

```bash
bin/magento store:website:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `support:backup:code`

Codesicherung erstellen

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--name`

Dump Name
- Akzeptiert einen Wert



### `--output`, `-o`



Ausgabepfad
- Akzeptiert einen Wert



### `--logs`, `-l`



Logs einschließen
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `support:backup:db`

DB-Backup erstellen

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--name`

Dump Name
- Akzeptiert einen Wert



### `--output`, `-o`



Ausgabepfad
- Akzeptiert einen Wert



### `--logs`, `-l`



Logs einschließen
- Standard: `false`
- Akzeptiert keinen Wert



### `--ignore-sanitize`, `-i`



Ignore sanitize
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `support:utility:check`

Überprüfen der erforderlichen Backup-Dienstprogramme

```bash
bin/magento support:utility:check [--hide-paths]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--hide-paths`

Nur erforderliche Konsolenprogramme überprüfen
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `support:utility:paths`

Liste mit Dienstprogrammpfaden erstellen

```bash
bin/magento support:utility:paths [-f|--force]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Stärke
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `theme:uninstall`

Deinstalliert das Design

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

<!-- app.name --> <!-- command.usage -->

### `theme`

Pfad des Designs. Der Designpfad sollte als vollständiger Pfad angegeben werden, der sich aus Bereich/Anbieter/Name zusammensetzt. Beispiel: frontend/Magento/blank

- Standard: `[]`
- Erforderlich

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--backup-code`

Codesicherung durchführen (ohne temporäre Dateien)
- Standard: `false`
- Akzeptiert keinen Wert



### `--clear-static-content`, `-c`



Löschen Sie die generierten statischen Ansichtsdateien.
- Standard: `false`
- Akzeptiert keinen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size -->

## `varnish:vcl:generate`

Generiert Varnish VCL und echnet es an die Befehlszeile

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access-list`

IP-Zugriffsliste, die &quot;Varnish&quot;bereinigen kann
- Standard: `localhost`
- Erfordert einen Wert


### `--backend-host`

Host des Web-Backend
- Standard: `localhost`
- Erfordert einen Wert


### `--backend-port`

Anschluss des Web-Backend
- Standard: `8080`
- Erfordert einen Wert


### `--export-version`

Die Version der Datei &quot;Varnish&quot;
- Standard: `4`
- Erfordert einen Wert


### `--grace-period`

Übergangsphase in Sekunden
- Standard: `300`
- Erfordert einen Wert


### `--output-file`

Pfad zur Datei, in die vcl geschrieben werden soll
- Erfordert einen Wert



### `--help`, `-h`



Diese Hilfemeldung anzeigen
- Standard: `false`
- Akzeptiert keinen Wert



### `--quiet`, `-q`



Keine Nachricht ausgeben
- Standard: `false`
- Akzeptiert keinen Wert



### `--verbose`, `-v|-vv|-vvv`



Erhöhen Sie die Ausführlichkeit von Nachrichten: 1 für normale Ausgabe, 2 für ausführlichere Ausgabe und 3 für Debugging
- Standard: `false`
- Akzeptiert keinen Wert



### `--version`, `-V`



Diese Anwendungsversion anzeigen
- Standard: `false`
- Akzeptiert keinen Wert


### `--ansi`

ANSI-Ausgabe erzwingen
- Standard: `false`
- Akzeptiert keinen Wert


### `--no-ansi`

ANSI-Ausgabe deaktivieren
- Standard: `false`
- Akzeptiert keinen Wert



### `--no-interaction`, `-n`



Interaktive Fragen stellen
- Standard: `false`
- Akzeptiert keinen Wert <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->