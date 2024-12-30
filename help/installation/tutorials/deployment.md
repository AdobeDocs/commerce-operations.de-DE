---
title: Erstellen oder Aktualisieren der Bereitstellungskonfiguration
description: Führen Sie diese Schritte aus, um Ihre Adobe Commerce-Bereitstellungskonfiguration zu verwalten.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Erstellen oder Aktualisieren der Bereitstellungskonfiguration

Für die Verwendung dieses Befehls gibt es keine Voraussetzungen.

## Erstellen oder Aktualisieren der Bereitstellungskonfiguration

[Bereitstellungskonfiguration](../../configuration/reference/deployment-files.md) stellt die Informationen bereit, die die Anwendung zum Initialisieren und Bootstrapping benötigt.

Sie können diesen Befehl verwenden, wenn:

* Sie haben die Anwendung zuvor installiert und möchten die Bereitstellungskonfiguration ändern
* Sie möchten nur die Bereitstellungskonfiguration erstellen und die Installation auf eine andere Weise fortsetzen
* So aktualisieren Sie die Bereitstellungskonfiguration ohne Auswirkungen auf andere Elemente

Befehlsoptionen:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

In der folgenden Tabelle werden die Bedeutungen von Installationsparametern und -werten erläutert.

| Parameter | Wert | Erforderlich? |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) für den Zugriff auf den Admin.<br><br>Um Exploits zu verhindern, empfehlen wir, kein gängiges Wort wie admin, backend zu verwenden. Der Admin-URI kann nur alphanumerische Werte und den Unterstrich (`_`) enthalten. | Nein |
| `--db-host` | Verwenden Sie eine der folgenden Optionen:<br><br>- Der voll qualifizierte Hostname oder die IP-Adresse des Datenbankservers.<br><br>- `localhost` (Standard) oder `127.0.0.1`, wenn sich Ihr Datenbankserver auf demselben Host wie Ihr Webserver befindet. localhost bedeutet, dass die MySQL-Client-Bibliothek UNIX-Sockets für die Verbindung mit der Datenbank verwendet. `127.0.0.1` verwendet die Client-Bibliothek das TCP-Protokoll. Weitere Informationen zu Sockets finden Sie in der [PHP PDO_MYSQL-Dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Hinweis:** Sie können optional den Datenbank-Server-Port in seinem Hostnamen wie `www.example.com:9000` angeben | Nein |
| `--db-name` | Name der Datenbankinstanz, in der die Datenbanktabellen installiert werden sollen.<br><br>Der Standardwert ist `magento2`. | Nein |
| `--db-user` | Benutzername des Inhabers der Datenbankinstanz.<br><br>Der Standardwert ist `root`. | Nein |
| `--db-password` | Kennwort des Besitzers der Datenbankinstanz. | Nein |
| `--db-prefix` | Verwenden Sie diese Option nur, wenn Sie die Datenbanktabellen in einer Datenbankinstanz installieren, in der bereits Adobe Commerce-Tabellen vorhanden sind.<br><br>Verwenden Sie in diesem Fall ein Präfix, um die Tabellen für diese Installation zu identifizieren. Bei einigen Kunden wird mehr als eine Adobe Commerce-Instanz auf einem Server ausgeführt, wobei alle Tabellen in derselben Datenbank vorhanden sind.<br><br>Das Präfix darf maximal fünf Zeichen lang sein. Sie muss mit einem Buchstaben beginnen und darf nur Buchstaben, Zahlen und Unterstriche enthalten.<br><br>Mit dieser Option können diese Kunden den Datenbankserver für mehr als eine Adobe Commerce-Installation freigeben. | Nein |
| `--session-save` | Verwenden Sie eine der folgenden Möglichkeiten:<br><br>- `db`, um Sitzungsdaten in der [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) zu speichern. Wählen Sie Datenbankspeicher, wenn Sie eine geclusterte Datenbank haben. Andernfalls gibt es möglicherweise keinen großen Vorteil gegenüber dateibasiertem Speicher.<br><br> - `files`, Sitzungsdaten im Dateisystem zu speichern. Die dateibasierte Sitzungsspeicherung ist geeignet, es sei denn, der Dateisystemzugriff ist langsam, Sie verfügen über eine geclusterte Datenbank oder Sie möchten Sitzungsdaten in Redis speichern.<br><br>- `redis` zum Speichern von Sitzungsdaten in [Verwenden Sie Redis für die Sitzungsspeicherung](../../configuration/cache/config-redis.md). Wenn Sie Redis für das Standard- oder Seiten-Caching verwenden, muss Redis bereits installiert sein. | Nein |
| `--key` | Wenn Sie über einen verfügen, geben Sie einen Schlüssel zum Verschlüsseln [sensibler Daten](#sensitive-data) in der Datenbank an. Wenn Sie noch keinen haben, generiert das Programm einen für Sie. | Nein |
| `--db-init-statements` | Erweiterter MySQL-Konfigurationsparameter. Verwendet Anweisungen zur Datenbankinitialisierung, die beim Herstellen einer Verbindung mit der MySQL-Datenbank ausgeführt werden.<br><br>Der Standardwert ist `SET NAMES utf8;`.<br><br>Konsultieren Sie eine Referenz wie [diese](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) bevor Sie Werte festlegen. | Nein |
| `--http-cache-hosts` | Liste der HTTP-Cache-Gateway-Hosts, an die Bereinigungsanfragen gesendet werden sollen, durch Kommata getrennt (Zum Beispiel Server lackieren.) Verwenden Sie diesen Parameter, um den Host oder die Hosts anzugeben, die in derselben Anfrage bereinigt werden sollen. (Es spielt keine Rolle, ob Sie nur einen oder mehrere Hosts haben.)<br><br>Format muss `<hostname or ip>:<listen port>` sein, wobei `<listen port>` weggelassen werden kann, wenn es sich um Port 80 handelt. Beispiel: `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Trennen Sie Hosts nicht durch Leerzeichen. | Nein |

## Konfigurationsdaten importieren

Beim Einrichten eines Produktionssystems empfiehlt es sich, Konfigurationseinstellungen aus `config.php` und `env.php` in die Datenbank zu importieren.
Zu diesen Einstellungen gehören Konfigurationspfade und -werte, Websites, Stores, Store-Ansichten und Designs.

Nach dem Import von Websites, Stores, Store-Ansichten und Designs können Sie Produktattribute erstellen und sie auf Websites, Stores und Store-Ansichten im Produktionssystem anwenden.

Führen Sie auf dem Produktionssystem den folgenden Befehl aus, um Daten aus den Konfigurationsdateien (`config.php` und `env.php`) in die Datenbank zu importieren:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Mit der optionalen `[-n, --no-interaction]`-Markierung kann der Befehl ohne zusätzliche Bestätigungen ausgeführt werden.

Weitere Informationen finden Sie unter [Daten aus Konfigurationsdateien importieren](../../configuration/cli/import-configuration.md)

### Sensible Daten

{{$include /help/_includes/sensitive-data.md}}
