---
title: Erstellen oder Aktualisieren der Bereitstellungskonfiguration
description: Führen Sie diese Schritte aus, um Ihre Adobe Commerce- oder Magento Open Source-Implementierungskonfiguration zu verwalten.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Erstellen oder Aktualisieren der Bereitstellungskonfiguration

Für die Verwendung dieses Befehls sind keine Voraussetzungen erforderlich.

## Erstellen oder Aktualisieren der Bereitstellungskonfiguration

[Bereitstellungskonfiguration](../../configuration/reference/deployment-files.md) stellt die Informationen bereit, die die Anwendung initialisieren und bootstrapping durchführen muss.

Sie können diesen Befehl in folgenden Fällen verwenden:

* Sie haben die Anwendung zuvor installiert und möchten die Bereitstellungskonfiguration ändern
* Sie möchten nur die Bereitstellungskonfiguration erstellen und die Installation auf andere Weise fortsetzen
* So aktualisieren Sie die Bereitstellungskonfiguration, ohne andere Auswirkungen zu haben

Befehlsoptionen:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

In der folgenden Tabelle werden die Bedeutungen von Installationsparametern und -werten erläutert.

| Parameter | Wert | Erforderlich? |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)), um auf den Admin zuzugreifen.<br><br>Um Exploits zu verhindern, empfehlen wir, kein gemeinsames Wort wie &quot;admin&quot;, &quot;backend&quot;zu verwenden. Der Administrator-URI kann alphanumerische Werte und Unterstriche (`_`). | Nein |
| `--db-host` | Verwenden Sie einen der folgenden Schritte:<br><br>- Der vollständig qualifizierte Hostname oder die IP-Adresse des Datenbankservers.<br><br>- `localhost` (Standard) oder `127.0.0.1` wenn sich Ihr Datenbankserver auf demselben Host wie Ihr Webserver befindet. localhost bedeutet, dass die MySQL-Client-Bibliothek UNIX-Sockets verwendet, um eine Verbindung zur Datenbank herzustellen. `127.0.0.1` bewirkt, dass die Client-Bibliothek das TCP-Protokoll verwendet. Weitere Informationen zu Sockets finden Sie im Abschnitt [PHP PDO_MYSQL-Dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Hinweis:** Sie können optional den Datenbankserver-Port in seinem Hostnamen angeben, z. B. `www.example.com:9000` | Nein |
| `--db-name` | Name der Datenbankinstanz, in der Sie die Datenbanktabellen installieren möchten.<br><br>Der Standardwert ist `magento2`. | Nein |
| `--db-user` | Benutzername des Eigentümers der Datenbankinstanz.<br><br>Der Standardwert ist `root`. | Nein |
| `--db-password` | Passwort des Inhabers der Datenbankinstanz. | Nein |
| `--db-prefix` | Verwenden Sie dies nur, wenn Sie die Datenbanktabellen in einer Datenbankinstanz installieren, in der bereits Adobe Commerce- und Magento Open Source-Tabellen enthalten sind.<br><br>Verwenden Sie in diesem Fall ein Präfix, um die Tabellen für diese Installation zu identifizieren. Einige Kunden haben mehr als eine Adobe Commerce- oder Magento Open Source-Instanz, die auf einem Server mit allen Tabellen in derselben  ausgeführt wird.<br><br>Das Präfix kann maximal fünf Zeichen lang sein. Sie muss mit einem Brief beginnen und darf nur Buchstaben, Zahlen und Unterstriche enthalten.<br><br>Mit dieser Option können diese Kunden den Datenbankserver für mehrere Adobe Commerce- oder Magento Open Source-Installationen freigeben. | Nein |
| `--session-save` | Verwenden Sie einen der folgenden Schritte:<br><br>- `db` zum Speichern von Sitzungsdaten im [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Wählen Sie Datenbankspeicher, wenn Sie über eine Clusterdatenbank verfügen. Andernfalls hat der dateibasierte Speicher möglicherweise keinen großen Vorteil.<br><br>- `files` , um Sitzungsdaten im Dateisystem zu speichern. Eine dateibasierte Sitzungsspeicherung ist angemessen, es sei denn, der Dateisystemzugriff ist langsam, Sie haben eine Clusterdatenbank oder Sie möchten Sitzungsdaten in Redis speichern.<br><br>- `redis` zum Speichern von Sitzungsdaten in [Verwenden von Redizes für die Sitzungsspeicherung](../../configuration/cache/config-redis.md). Wenn Sie Redis für Standard- oder Seiten-Caching verwenden, muss Redis bereits installiert sein. | Nein |
| `--key` | Wenn Sie einen Schlüssel haben, geben Sie einen zu verschlüsselnden Schlüssel an [vertrauliche Daten](#sensitive-data) in der Datenbank. Wenn Sie keine haben, generiert das Programm eine für Sie. | Nein |
| `--db-init-statements` | Erweiterter MySQL-Konfigurationsparameter. Verwendet Anweisungen zur Datenbankinitialisierung, die beim Herstellen einer Verbindung zur MySQL-Datenbank ausgeführt werden.<br><br>Der Standardwert ist `SET NAMES utf8;`.<br><br>Referenz ähnlich [dieses](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) bevor Sie Werte festlegen. | Nein |
| `--http-cache-hosts` | Kommagetrennte Liste von HTTP-Cache-Gateway-Hosts, an die Bereinigungsanforderungen gesendet werden sollen. (z. B. &quot;Varnish&quot;-Server.) Verwenden Sie diesen Parameter, um den oder die Hosts anzugeben, die in derselben Anforderung bereinigt werden sollen. (Es spielt keine Rolle, ob Sie nur einen oder mehrere Hosts haben.)<br><br>Format muss `<hostname or ip>:<listen port>`, wo Sie weglassen können `<listen port>` wenn es Port 80 ist. Beispiel, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Trennen Sie Hosts nicht durch Leerzeichen. | Nein |

## Konfigurationsdaten importieren

Beim Einrichten eines Produktionssystems empfiehlt es sich, Konfigurationseinstellungen aus zu importieren. `config.php` und `env.php` in die Datenbank ein.
Zu diesen Einstellungen gehören Konfigurationspfade und -werte, Websites, Stores, Store-Ansichten und Designs.

Nach dem Import von Websites, Geschäften, Ansichten und Designs können Sie Produktattribute erstellen und auf Websites, Stores und Store-Ansichten im Produktionssystem anwenden.

Führen Sie im Produktionssystem den folgenden Befehl aus, um Daten aus den Konfigurationsdateien zu importieren (`config.php` und `env.php`) in die Datenbank:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Das optionale `[-n, --no-interaction]` -Flag ermöglicht die Ausführung des Befehls ohne zusätzliche Bestätigungen.

Weitere Informationen finden Sie im [Daten aus Konfigurationsdateien importieren](../../configuration/cli/import-configuration.md)

### Sensible Daten

{{$include /help/_includes/sensitive-data.md}}
