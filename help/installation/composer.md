---
title: Schnellstart-On-Premise-Installation
description: Erfahren Sie, wie Sie Adobe Commerce mithilfe von Composer in Ihrer eigenen Infrastruktur installieren. Erfahren Sie mehr über Schnellstartschritte und Konfigurationsanforderungen.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Schnellstart-On-Premise-Installation

Die Anweisungen auf dieser Seite beschreiben, wie Sie Adobe Commerce auf einer selbstgehosteten Infrastruktur installieren. Eine Anleitung zum Aktualisieren einer vorhandenen Installation finden Sie im [_Upgrade-Handbuch_](../upgrade/overview.md).

Adobe verwendet [Composer](https://getcomposer.org/) um Adobe Commerce-Komponenten und ihre Abhängigkeiten zu verwalten. Die Verwendung von Composer zum Abrufen des Adobe Commerce-Metapakets bietet die folgenden Vorteile:

- Wiederverwenden von Drittanbieterbibliotheken ohne Bündelung mit Quellcode
- Verringern Sie Erweiterungskonflikte und Kompatibilitätsprobleme mithilfe einer komponentenbasierten Architektur mit robuster Abhängigkeitsverwaltung
- Einhaltung der Standards [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)
- Magento Open Source mit anderen Komponenten neu packen
- Verwenden der Adobe Commerce-Software in einer Produktionsumgebung

>[!NOTE]
>
>Entwickler, die zu Magento Open Source beitragen, sollten die [Git-basierte](https://developer.adobe.com/commerce/contributor/guides/install) Installationsmethode verwenden.

## Voraussetzungen

Bevor Sie fortfahren, müssen Sie Folgendes tun:

- Alle [erforderlichen Aufgaben“ &#x200B;](system-requirements.md).
- [Composer installieren](https://getcomposer.org/download/).
- Abrufen [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) zum Adobe Commerce Composer-Repository.

## Als Dateisystembesitzer anmelden

Erfahren Sie mehr über Eigentümerschaft, Berechtigungen und den Dateisystembesitzer im Thema [Übersicht über Eigentümerschaft und Berechtigungen](prerequisites/file-system/overview.md).

So wechseln Sie zum Dateisystembesitzer:

1. Melden Sie sich beim Anwendungsserver als Benutzer an oder wechseln Sie zu einem Benutzer mit Berechtigungen zum Schreiben in das Dateisystem.

   Wenn Sie die Bash-Shell verwenden, können Sie die folgende Syntax verwenden, um zum Dateisystembesitzer zu wechseln und den Befehl gleichzeitig einzugeben:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Wenn der Dateisystembesitzer keine Anmeldungen zulässt, können Sie Folgendes tun:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Um CLI-Befehle aus einem beliebigen Verzeichnis auszuführen, fügen Sie `<app_root>/bin` zu Ihrem `PATH` hinzu.

   Da Shell unterschiedliche Syntaxen haben, sollten Sie einen Verweis wie [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables) heranziehen.

   Beispiel-Bash-Shell für CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Optional können Sie die Befehle wie folgt ausführen:

   - `cd <app_root>/bin` und als `./magento <command name>` ausführen
   - `app_root>/bin/magento <command name>`
   - `<app_root>` ist ein Unterverzeichnis Ihres Webserver-Stammverzeichnisses

## Abrufen des Metapakets

So rufen Sie das Adobe Commerce-Metapaket ab:

1. Melden Sie sich bei Ihrem Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](prerequisites/file-system/overview.md).
1. Wechseln Sie in das Verzeichnis des Webservers docroot oder in ein Verzeichnis, das Sie als virtuellen Host docroot konfiguriert haben.
1. Erstellen Sie ein Composer-Projekt mit einem Commerce-Metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Geben Sie nach Aufforderung Ihre Authentifizierungsschlüssel ein. Öffentliche und private Schlüssel werden aus [Commerce Marketplace - Zugriffsschlüssel](https://commercemarketplace.adobe.com/customer/account/login/) erstellt und konfiguriert. Kopieren Sie für die `[!UICONTROL username]` den Wert des öffentlichen Schlüssels und fügen Sie ihn ein. Kopieren Sie für die `[!UICONTROL password]` den Wert für den privaten Schlüssel und fügen Sie ihn ein.

   >[!NOTE]
   >
   > Wenn Sie eine Composer `[auth.json](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/authentication-keys)`-Datei oder Umgebungsvariable verwenden, die mit Ihren Commerce-Authentifizierungsschlüsseln konfiguriert wurde, werden Sie nicht aufgefordert, Authentifizierungsschlüssel einzugeben.

   Wenn Fehler wie `Could not find package...` oder `...no matching package found` auftreten, stellen Sie sicher, dass der Befehl keine Tippfehler enthält. Wenn weiterhin Fehler auftreten, sind Sie möglicherweise nicht berechtigt, Adobe Commerce herunterzuladen. Wenden Sie sich an den [Adobe Commerce](https://support.magento.com/hc/en-us)Support, um Hilfe zu erhalten.

   Siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360033818091) für Hilfe bei weiteren Fehlern.

### Beispiel - Nebenversion

Nebenversionen enthalten neue Funktionen, Qualitätskorrekturen und Sicherheitskorrekturen. Verwenden Sie Composer, um eine Nebenversion anzugeben. Um beispielsweise das Metapaket Adobe Commerce 2.4.6 anzugeben:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Beispiel - Qualitäts-Patch

Qualitäts-Patches enthalten hauptsächlich funktionale _und_ Sicherheitskorrekturen. Sie können jedoch manchmal auch neue, abwärtskompatible Funktionen enthalten. Verwenden Sie Composer, um einen Qualitäts-Patch herunterzuladen. Um beispielsweise das Metapaket Adobe Commerce 2.4.6 anzugeben:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Beispiel - Sicherheits-Patch

Sicherheits-Patches enthalten nur Sicherheitskorrekturen. Sie wurden entwickelt, um den Upgrade-Prozess schneller und einfacher zu machen.

Sicherheits-Patches verwenden die Composer-Namenskonvention `2.4.6-px`. Verwenden Sie Composer, um einen Patch anzugeben. So laden Sie beispielsweise das Adobe Commerce 2.4.6-p1-Metapaket herunter:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Dateiberechtigungen festlegen

Sie müssen vor der Installation von Adobe Commerce Lese- und Schreibberechtigungen für die Webservergruppe festlegen. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installieren des Programms

Sie müssen die Befehlszeile verwenden, um Adobe Commerce zu installieren.

In diesem Beispiel wird davon ausgegangen, dass der Installationsordner `magento2ee` heißt, sich der `db-host` auf demselben Computer befindet (`localhost`) und dass die `db-name`, `db-user` und `db-password` alle `magento` sind:

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
>Sie können den Admin-URI mit der Option `--backend-frontname` anpassen. Adobe empfiehlt jedoch, diese Option wegzulassen und zuzulassen, dass der Installationsbefehl automatisch einen zufälligen URI generiert. Ein zufälliger URI ist für Hacker oder bösartige Software schwieriger auszunutzen. Der URI wird nach Abschluss der Installation in Ihrer Konsole angezeigt.

>[!TIP]
>
>Eine vollständige Beschreibung der CLI-Installationsoptionen finden Sie unter [Installieren der Anwendung über die Befehlszeile](advanced.md).

## Befehlsübersicht

Um eine vollständige Liste der Befehle anzuzeigen, geben Sie Folgendes ein:

```bash
bin/magento list
```

Um Hilfe zu einem bestimmten Befehl zu erhalten, geben Sie Folgendes ein:

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

In der folgenden Tabelle sind die verfügbaren Befehle zusammengefasst. Befehle werden nur in Form einer Zusammenfassung angezeigt. Weitere Informationen zu einem Befehl erhalten Sie, wenn Sie auf den Link in der Spalte Befehl klicken.

| Befehl | Beschreibung | Voraussetzungen |
|--- |--- |--- |
| `magento setup:install` | Installiert die Anwendung | Keine |
| `magento setup:uninstall` | Entfernt die Anwendung. | Installierte Anwendung |
| `magento setup:upgrade` | Aktualisiert die Anwendung. | Bereitstellungskonfiguration |
| `magento maintenance:{enable/disable}` | Aktiviert oder deaktiviert den Wartungsmodus (im Wartungsmodus können nur ausgeschlossene IP-Adressen auf die Admin- oder Storefront zugreifen). | Installierte Anwendung |
| `magento setup:config:set` | Erstellt oder aktualisiert die Bereitstellungskonfiguration. | Keine |
| `magento module:{enable/disable}` | Module aktivieren oder deaktivieren. | Keine |
| `magento setup:store-config:set` | Legt Optionen für die Storefront fest, z. B. Basis-URL, Sprache, Zeitzone. | Bereitstellungskonfiguration |
| `magento setup:db-schema:upgrade` | Aktualisiert das Datenbankschema. | Bereitstellungskonfiguration |
| `magento setup:db-data:upgrade` | Aktualisiert die Datenbankdaten. | Bereitstellungskonfiguration |
| `magento setup:db:status` | Überprüft, ob die Datenbank mit dem Code auf dem neuesten Stand ist. | Bereitstellungskonfiguration |
| `magento admin:user:create` | Erstellt einen Administrator-Benutzer. | Sie können Benutzer für Folgendes erstellen:<br><br>Bereitstellungskonfiguration<br><br>Aktivieren Sie mindestens die `Magento_User` und `Magento_Authorization` Module<br><br>Datenbank (am einfachsten verwenden Sie `bin/magento setup:upgrade`) |
| `magento list` | Listet alle verfügbaren Befehle auf. | Keine |
| `magento help` | Stellt Hilfe für den angegebenen Befehl bereit. | Keine |

### Häufige Argumente

Die folgenden Argumente gelten für alle Befehle. Diese Befehle können entweder vor oder nach der Installation der Anwendung ausgeführt werden:

| Lange Version | Kurzversion | Bedeutung |
|--- |--- |--- |
| `--help` | `-h` | Hilfe zu jedem Befehl. Beispiel: `./magento help setup:install` oder `./magento help setup:config:set`. |
| `--quiet` | `-q` | Ruhiger Modus; keine Ausgabe. |
| `--no-interaction` | `-n` | Keine interaktiven Fragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Ausführlichkeitsstufe. Beispielsweise zeigt `--verbose=3` oder `-vvv` die ausführlichste Ausgabe als Debugging-Ausführlichkeit an. Der Standardwert ist `--verbose=1` oder `-v`. |
| `--version` | `-V` | Diese Anwendungsversion anzeigen |
| `--ansi` | Nicht zutreffend | ANSI-Ausgabe erzwingen |
| `--no-ansi` | Nicht zutreffend | ANSI-Ausgabe deaktivieren |

>[!NOTE]
>
>Herzlichen Glückwunsch! Sie haben die Schnellinstallation abgeschlossen. Benötigen Sie erweiterte Hilfe? Sehen Sie sich das [Erweiterte &#x200B;](advanced.md)&quot; an.
