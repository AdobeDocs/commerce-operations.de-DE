---
title: System-Setup erstellen
description: Erfahren Sie, wie Sie Commerce in einem Build-System bereitstellen.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Einrichten von Systemen

Sie können über ein Buildsystem verfügen, das die folgenden Anforderungen erfüllt:

- Der gesamte Commerce-Code unterliegt der Quell-Code-Kontrolle im selben Repository wie die Entwicklungs- und Produktionssysteme
- Stellen Sie sicher, dass alle folgenden Elemente _enthalten_ in der Quell-Code-Verwaltung:

   - `app/etc/config.php`
   - `generated` Verzeichnis (und Unterverzeichnisse)
   - `pub/media` directory
   - `pub/media/wysiwyg` Verzeichnis (und Unterverzeichnisse)
   - `pub/static` Verzeichnis (und Unterverzeichnisse)

- Muss eine kompatible PHP-Version installiert haben
- Muss Composer installiert haben
- Sie verfügt über Dateisystemeigentümer und -berechtigungen, wie hier beschrieben: [Voraussetzungen für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/technical-details.md).
- Das Build-System muss Commerce nicht installieren, aber der Code muss verfügbar sein.

>[!WARNING]
>
>Die Datenbankverbindung ist nicht erforderlich, wenn sie bereits in `config.php`; see [Konfiguration exportieren](../cli/export-configuration.md). Andernfalls ist die Datenbankverbindung erforderlich.

>[!INFO]
>
>Der Build-Computer kann sich auf seinem eigenen Host oder auf demselben Host befinden wie ein installiertes Commerce-System.

## Build-Computer konfigurieren

In den folgenden Abschnitten wird beschrieben, wie Sie den Build-Computer konfigurieren.

### Installation Composer

Überprüfen Sie zunächst, ob Composer bereits installiert ist:

Geben Sie an einer Eingabeaufforderung einen der folgenden Befehle ein:

- `composer --help`
- `composer list --help`

Wenn die Befehlshilfe angezeigt wird, ist Composer bereits installiert.

Wenn ein Fehler angezeigt wird, führen Sie die folgenden Schritte aus, um Composer zu installieren.

So installieren Sie Composer:

1. Wechseln Sie zu oder erstellen Sie ein leeres Verzeichnis auf Ihrem Commerce-Server.

1. Geben Sie die folgenden Befehle ein:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Weitere Installationsoptionen finden Sie unter [Dokumentation zur Installation von Composer][composer].

### PHP installieren

Installieren Sie PHP auf [CentOS] oder [Ubuntu].

### Einrichten des Build-Systems

So richten Sie das Build-System ein:

1. Melden Sie sich beim Build-System als Eigentümer des Dateisystems an oder wechseln Sie zu ihm.
1. Rufen Sie den Commerce-Code aus der Quell-Code-Verwaltung ab.

   Wenn Sie Git verwenden, verwenden Sie den folgenden Befehl:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Wechseln Sie zum Stammverzeichnis für Commerce und geben Sie Folgendes ein:

   ```bash
   composer install
   ```

1. Warten Sie, bis die Abhängigkeiten aktualisiert wurden.
1. Legen Sie den Besitz fest:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Beispiel:

   ```bash
   chown -R commerce-username:apache .
   ```

1. Wenn Sie Git verwenden, öffnen Sie `.gitignore` in einem Texteditor.
1. Beginnen Sie jede der folgenden Zeilen mit einem `#` -Zeichen, um sie herauszukommentieren:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Speichern Sie Ihre Änderungen in `.gitignore` und beenden Sie den Texteditor.
1. Wenn Sie Git verwenden, verwenden Sie die folgenden Befehle, um die Änderung zu übertragen:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Siehe [`.gitignore` reference](../reference/config-reference-gitignore.md) für weitere Informationen.

1. Das Build-System sollte [Standardmodus](../bootstrap/application-modes.md#default-mode) oder [Entwicklermodus](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` ist erforderlich. Es kann entweder `default` oder `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
