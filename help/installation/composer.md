---
title: Schnellstart für die Installation vor Ort
description: Führen Sie diese Schritte aus, um Adobe Commerce in Ihrer Infrastruktur zu installieren.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Schnellstart für die Installation vor Ort

Die Anweisungen auf dieser Seite beschreiben, wie Adobe Commerce in der [selbstgehosteten](../implementation-playbook/infrastructure/self-hosting/overview.md) -Infrastruktur installiert wird. Eine Anleitung zum Aktualisieren einer vorhandenen Installation finden Sie im [_Upgrade-Handbuch_](../upgrade/overview.md).

Adobe verwendet [Composer](https://getcomposer.org/), um Adobe Commerce-Komponenten und ihre Abhängigkeiten zu verwalten. Die Verwendung von Composer zum Abrufen des Adobe Commerce-Metapakets bietet die folgenden Vorteile:

- Wiederverwenden von Bibliotheken von Drittanbietern ohne Bundle mit Quellcode
- Reduzieren von Erweiterungskonflikten und Kompatibilitätsproblemen durch Verwendung einer komponentenbasierten Architektur mit robuster Abhängigkeitsverwaltung
- Einhaltung der [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)-Standards
- Magento Open Source mit anderen Komponenten umpacken
- Verwenden der Adobe Commerce-Software in einer Produktionsumgebung

>[!NOTE]
>
>Entwickler, die zur Magento Open Source beitragen, sollten die [git-basierte](https://developer.adobe.com/commerce/contributor/guides/install/) -Installationsmethode verwenden.

## Voraussetzungen

Bevor Sie fortfahren, müssen Sie Folgendes tun:

- Führen Sie alle erforderlichen [Aufgaben ](system-requirements.md) aus.
- [Install Composer](https://getcomposer.org/download/).
- Rufen Sie [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) in das Adobe Commerce Composer-Repository ab.

## Als Dateisysteminhaber anmelden

Erfahren Sie mehr über Eigentümer, Berechtigungen und den Dateisysteminhaber im Thema [Überblick über Eigentümer und Berechtigungen](prerequisites/file-system/overview.md).

So wechseln Sie zum Dateisysteminhaber:

1. Melden Sie sich beim Anwendungsserver als Benutzer an oder wechseln Sie zu einem Benutzer mit Schreibberechtigung für das Dateisystem.

   Wenn Sie die Bash-Shell verwenden, können Sie die folgende Syntax verwenden, um zum Dateisysteminhaber zu wechseln und den Befehl gleichzeitig einzugeben:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Wenn der Dateisysteminhaber keine Anmeldung zulässt, können Sie Folgendes tun:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Um CLI-Befehle aus einem beliebigen Verzeichnis auszuführen, fügen Sie `<app_root>/bin` zu Ihrem System `PATH` hinzu.

   Da Muscheln unterschiedliche Syntaxen haben, sollten Sie einen Verweis wie [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables) lesen.

   Beispiel-Bash-Shell für CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Optional können Sie die Befehle wie folgt ausführen:

   - `cd <app_root>/bin` und führen Sie sie als `./magento <command name>` aus
   - `app_root>/bin/magento <command name>`
   - `<app_root>` ist ein Unterverzeichnis Ihres Webserver-Basisverzeichnisses.

## Metapaket abrufen

So rufen Sie das Adobe Commerce-Metapaket ab:

1. Melden Sie sich bei Ihrem Anwendungsserver als [Dateisysteminhaber](prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Basisverzeichnis des Webservers oder zu einem Ordner, den Sie als virtuelles Host-Basisverzeichnis konfiguriert haben.
1. Erstellen Sie ein Composer-Projekt mit einem Commerce-Metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Geben Sie bei Aufforderung die Authentifizierungsschlüssel ein. Öffentliche und private Schlüssel werden in Ihrem [Commerce Marketplace](https://commercemarketplace.adobe.com/customer/account/login/) erstellt und konfiguriert.

   >[!NOTE]
   >
   > Bei Verwendung einer Composer `auth.json` -Datei oder Umgebungsvariablen werden Sie nicht aufgefordert, Ihre Authentifizierungsschlüssel einzugeben.

   Wenn Fehler wie `Could not find package...` oder `...no matching package found` auftreten, stellen Sie sicher, dass Ihr Befehl keine Tippfehler enthält. Sollten dennoch Fehler auftreten, sind Sie möglicherweise nicht berechtigt, Adobe Commerce herunterzuladen. Wenden Sie sich für Hilfe an den [Adobe Commerce-Support](https://support.magento.com/hc/en-us).

   Weitere Informationen zu Fehlern finden Sie unter [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360033818091) .

### Beispiel - Nebenversion

Nebenversionen enthalten neue Funktionen, Qualitätsverbesserungen und Sicherheitskorrekturen. Verwenden Sie Composer , um eine Nebenversion anzugeben. So legen Sie beispielsweise das Adobe Commerce 2.4.6-Metapaket fest:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Beispiel - Qualitäts-Patch

Qualitäts-Patches enthalten in erster Linie funktionale Sicherheitskorrekturen für _und_. Manchmal können sie jedoch auch neue, abwärtskompatible Funktionen enthalten. Verwenden Sie Composer , um einen Qualitäts-Patch herunterzuladen. So legen Sie beispielsweise das Adobe Commerce 2.4.6-Metapaket fest:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Beispiel - Sicherheits-Patch

Sicherheits-Patches enthalten nur Sicherheitskorrekturen. Sie sind so konzipiert, dass der Aktualisierungsprozess schneller und einfacher wird.

Sicherheits-Patches verwenden die Composer-Namenskonvention `2.4.6-px`. Verwenden Sie Composer, um einen Patch anzugeben. So laden Sie beispielsweise das Metapaket Adobe Commerce 2.4.6-p1 herunter:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Festlegen von Dateiberechtigungen

Sie müssen Lese- und Schreibberechtigungen für die Webservergruppe festlegen, bevor Sie Adobe Commerce installieren. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installieren des Programms

Sie müssen die Befehlszeile verwenden, um Adobe Commerce zu installieren.

In diesem Beispiel wird davon ausgegangen, dass der Installationsordner den Namen `magento2ee` hat, sich der `db-host` auf demselben Computer befindet (`localhost`) und dass die `db-name`, `db-user` und `db-password` alle `magento` sind:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>Sie können den Admin-URI mit der Option `--backend-frontname` anpassen. Adobe empfiehlt jedoch, diese Option wegzulassen und dem Installationsbefehl zu erlauben, automatisch einen zufälligen URI zu generieren. Eine zufällige URI ist für Hacker oder böswillige Software schwieriger zu nutzen. Der URI wird in Ihrer Konsole angezeigt, wenn die Installation abgeschlossen ist.

>[!TIP]
>
>Eine vollständige Beschreibung der CLI-Installationsoptionen finden Sie unter [Installieren der Anwendung über die Befehlszeile](advanced.md).

## Befehlszusammenfassung

Geben Sie Folgendes ein, um eine vollständige Liste der Befehle anzuzeigen:

```bash
bin/magento list
```

Um Hilfe für einen bestimmten Befehl zu erhalten, geben Sie Folgendes ein:

```bash
bin/magento help <command>
```

Beispiel:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

Die folgende Tabelle fasst die verfügbaren Befehle zusammen. Befehle werden nur in der Zusammenfassung angezeigt. Weitere Informationen zu einem Befehl erhalten Sie, wenn Sie in der Spalte Befehl auf den Link klicken.

| Befehl | Beschreibung | Voraussetzungen |
|--- |--- |--- |
| `magento setup:install` | Installation des Programms | Keines |
| `magento setup:uninstall` | Entfernt die Anwendung. | Anwendung installiert |
| `magento setup:upgrade` | Aktualisiert die Anwendung. | Bereitstellungskonfiguration |
| `magento maintenance:{enable/disable}` | Aktiviert oder deaktiviert den Wartungsmodus (im Wartungsmodus können nur ausgenommene IP-Adressen auf die Admin- oder Storefront zugreifen). | Anwendung installiert |
| `magento setup:config:set` | Erstellt oder aktualisiert die Bereitstellungskonfiguration. | Keines |
| `magento module:{enable/disable}` | Aktivieren oder deaktivieren Sie Module. | Keines |
| `magento setup:store-config:set` | Legt Storefront-bezogene Optionen fest, z. B. Basis-URL, Sprache und Zeitzone. | Bereitstellungskonfiguration |
| `magento setup:db-schema:upgrade` | Aktualisiert das Datenbankschema. | Bereitstellungskonfiguration |
| `magento setup:db-data:upgrade` | Aktualisiert die Datenbankdaten. | Bereitstellungskonfiguration |
| `magento setup:db:status` | Überprüft, ob die Datenbank mit dem Code auf dem neuesten Stand ist. | Bereitstellungskonfiguration |
| `magento admin:user:create` | Erstellt einen Administratorbenutzer. | Sie können Benutzer für Folgendes erstellen:<br><br>Bereitstellungskonfiguration<br><br>Aktivieren Sie mindestens die Datenbank `Magento_User` und die Module `Magento_Authorization`<br><br>Datenbank (die einfachste Methode ist die Verwendung von `bin/magento setup:upgrade`) |
| `magento list` | Führt alle verfügbaren Befehle auf. | Keines |
| `magento help` | Bietet Hilfe für den angegebenen Befehl. | Keines |

### Allgemeine Argumente

Die folgenden Argumente gelten für alle Befehle. Diese Befehle können vor oder nach der Installation der Anwendung ausgeführt werden:

| Lange Version | Kurzversion | Bedeutung |
|--- |--- |--- |
| `--help` | `-h` | Erhalten Sie Hilfe für jeden Befehl. Beispiel: `./magento help setup:install` oder `./magento help setup:config:set`. |
| `--quiet` | `-q` | Ruhig, keine Ausgabe. |
| `--no-interaction` | `-n` | Keine interaktiven Fragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbosity level. Beispielsweise zeigt `--verbose=3` oder `-vvv` Debug-Ausführlichkeit an, die die ausführlichste Ausgabe ist. Der Standardwert ist `--verbose=1` oder `-v`. |
| `--version` | `-V` | Diese Anwendungsversion anzeigen |
| `--ansi` | Nicht zutreffend | ANSI-Ausgabe erzwingen |
| `--no-ansi` | Nicht zutreffend | ANSI-Ausgabe deaktivieren |

>[!NOTE]
>
>Herzlichen Glückwunsch! Sie haben die Schnellinstallation abgeschlossen. Sie benötigen weiterführende Hilfe? Sehen Sie sich das Handbuch [Erweiterte Installation](advanced.md) an.
