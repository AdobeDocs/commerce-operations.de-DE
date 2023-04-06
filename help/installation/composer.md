---
title: Schnellstart für die Installation vor Ort
description: Führen Sie diese Schritte aus, um Adobe Commerce oder Magento Open Source in Ihrer Infrastruktur zu installieren.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---


# Schnellstart für die Installation vor Ort

Wir verwenden [Verfasser](https://getcomposer.org/) um Adobe Commerce- und Magento Open Source-Komponenten und deren Abhängigkeiten zu verwalten. Die Verwendung von Composer zum Abrufen des Adobe Commerce- und Magento Open Source-Metapakets bietet die folgenden Vorteile:

- Wiederverwenden von Bibliotheken von Drittanbietern ohne Bundle mit Quellcode
- Reduzieren von Erweiterungskonflikten und Kompatibilitätsproblemen durch Verwendung einer komponentenbasierten Architektur mit robuster Abhängigkeitsverwaltung
- Einhaltung von [Interoperabilitätsgruppe PHP-Framework (FIG)](https://www.php-fig.org/) Standards
- Magento Open Source mit anderen Komponenten umpacken
- Verwenden der Adobe Commerce- oder Magento Open Source-Software in einer Produktionsumgebung

>[!NOTE]
>
>Entwickler, die zur Magento Open Source beitragen, sollten die [git-basiert](https://developer.adobe.com/commerce/contributor/guides/install/) Installationsmethode.

## Voraussetzungen

Bevor Sie fortfahren, müssen Sie Folgendes tun:

- Alle [Voraussetzungen](system-requirements.md).
- [Installation Composer](https://getcomposer.org/download/).
- Get [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) in das Adobe Commerce- und Magento Open Source Composer-Repository.

## Als Dateisysteminhaber anmelden

Erfahren Sie mehr über Eigentum, Berechtigungen und den Eigentümer des Dateisystems in unserer [Überblick über das Thema &quot;Eigentum und Berechtigungen&quot;](prerequisites/file-system/overview.md).

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

1. Um CLI-Befehle aus einem beliebigen Verzeichnis auszuführen, fügen Sie `<app_root>/bin` auf Ihr System `PATH`.

   Da Muscheln eine andere Syntax haben, sollten Sie einen Verweis wie [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Beispiel-Bash-Shell für CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Optional können Sie die Befehle wie folgt ausführen:

   - `cd <app_root>/bin` und führen Sie sie als `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` ist ein Unterverzeichnis Ihres Webserver-Basisverzeichnisses

## Metapaket abrufen

So rufen Sie das Adobe Commerce- oder Magento Open Source-Metapaket ab:

1. Melden Sie sich bei Ihrem Anwendungsserver als an oder wechseln Sie zu der [Dateisysteminhaber](prerequisites/file-system/overview.md).
1. Wechseln Sie zum Basisverzeichnis des Webservers oder zu einem Ordner, den Sie als virtuelles Host-Basisverzeichnis konfiguriert haben.
1. Erstellen Sie ein Composer-Projekt mit dem Adobe Commerce- oder Magento Open Source-Metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Geben Sie bei Aufforderung die Authentifizierungsschlüssel ein. Öffentliche und private Schlüssel werden in Ihrer [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   Wenn Fehler auftreten, z. B. `Could not find package...` oder `...no matching package found`, stellen Sie sicher, dass Ihr Befehl keine Tippfehler enthält. Sollten dennoch Fehler auftreten, sind Sie möglicherweise nicht berechtigt, Adobe Commerce herunterzuladen. Kontakt [Adobe Commerce-Support](https://support.magento.com/hc/en-us) für Hilfe.

   Siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360033818091) für Hilfe bei mehr Fehlern.

   >[!NOTE]
   >
   >Adobe Commerce-Kunden können zwei Wochen vor dem Datum der allgemeinen Verfügbarkeit (GA) auf Patches zugreifen. Vorabversionspakete sind nur über Composer verfügbar. Sie können erst auf Vorversionen im Entwicklerportal oder GitHub zugreifen, wenn die allgemeine Verfügbarkeit erreicht ist. Wenn Sie diese Pakete nicht in Composer finden können, wenden Sie sich an den Adobe Commerce-Support.

### Beispiel - Nebenversion

Nebenversionen enthalten neue Funktionen, Qualitätsverbesserungen und Sicherheitskorrekturen. Verwenden Sie Composer , um eine Nebenversion anzugeben. So legen Sie beispielsweise das Adobe Commerce 2.4.5-Metapaket fest:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Beispiel - Qualitäts-Patch

Qualitäts-Patches enthalten in erster Linie Funktionen _und_ Sicherheitskorrekturen. Manchmal können sie jedoch auch neue, abwärtskompatible Funktionen enthalten. Verwenden Sie Composer , um einen Qualitäts-Patch herunterzuladen. So legen Sie beispielsweise das Adobe Commerce 2.4.5-Metapaket fest:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Beispiel - Sicherheits-Patch

Sicherheits-Patches enthalten nur Sicherheitskorrekturen. Sie sind so konzipiert, dass der Aktualisierungsprozess schneller und einfacher wird.

Sicherheits-Patches verwenden die Composer-Namenskonvention `2.4.5-px`. Verwenden Sie Composer, um einen Patch anzugeben. So laden Sie beispielsweise das Metapaket Adobe Commerce 2.4.5-p1 herunter:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## Festlegen von Dateiberechtigungen

Sie müssen Lese- und Schreibberechtigungen für die Webservergruppe festlegen, bevor Sie Adobe Commerce oder Magento Open Source installieren. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installieren des Programms

Sie müssen die Befehlszeile verwenden, um Adobe Commerce oder Magento Open Source zu installieren.

In diesem Beispiel wird davon ausgegangen, dass der Installationsordner `magento2ee`, die `db-host` auf demselben Computer (`localhost`) und dass die `db-name`, `db-user`und `db-password` alle `magento`:

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
>Sie können den Admin-URI mit dem `--backend-frontname` -Option. Es wird jedoch empfohlen, diese Option wegzulassen und dem Installationsbefehl zu erlauben, automatisch einen zufälligen URI zu generieren. Eine zufällige URI ist für Hacker oder böswillige Software schwieriger zu nutzen. Der URI wird in Ihrer Konsole angezeigt, wenn die Installation abgeschlossen ist.

>[!TIP]
>
>Eine vollständige Beschreibung der CLI-Installationsoptionen finden Sie unter [Installieren Sie das Programm über die Befehlszeile](advanced.md).

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

Die folgende Tabelle fasst die verfügbaren Befehle zusammen. Befehle werden nur in der Zusammenfassung angezeigt. Weitere Informationen zu einem Befehl erhalten Sie, wenn Sie in der Spalte &quot;Befehl&quot;auf den Link klicken.

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
| `magento admin:user:create` | Erstellt einen Administratorbenutzer. | Sie können Benutzer für Folgendes erstellen:<br><br>Bereitstellungskonfiguration<br><br>Mindestens aktivieren `Magento_User` und `Magento_Authorization` Module<br><br>Datenbank (einfachste Methode zur Verwendung `bin/magento setup:upgrade`) |
| `magento list` | Führt alle verfügbaren Befehle auf. | Keines |
| `magento help` | Bietet Hilfe für den angegebenen Befehl. | Keines |

### Allgemeine Argumente

Die folgenden Argumente gelten für alle Befehle. Diese Befehle können vor oder nach der Installation der Anwendung ausgeführt werden:

| Lange Version | Kurzversion | Bedeutung |
|--- |--- |--- |
| `--help` | `-h` | Erhalten Sie Hilfe für jeden Befehl. Beispiel: `./magento help setup:install` oder `./magento help setup:config:set`. |
| `--quiet` | `-q` | Ruhezustand; keine Ausgabe. |
| `--no-interaction` | `-n` | Keine interaktiven Fragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbosity level. Beispiel: `--verbose=3` oder `-vvv` zeigt Debug-Ausführlichkeit an, die die ausführlichste Ausgabe ist. Der Standardwert ist `--verbose=1` oder `-v`. |
| `--version` | `-V` | Diese Anwendungsversion anzeigen |
| `--ansi` | Nicht zutreffend | ANSI-Ausgabe erzwingen |
| `--no-ansi` | Nicht zutreffend | ANSI-Ausgabe deaktivieren |

>[!NOTE]
>
>Herzlichen Glückwunsch! Sie haben die Schnellinstallation abgeschlossen. Sie benötigen weiterführende Hilfe? Sehen Sie sich unsere [Erweiterte Installation](advanced.md) Handbuch.
