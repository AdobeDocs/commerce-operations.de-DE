---
title: Fortgeschrittene Installation vor Ort
description: Erfahren Sie mehr über erweiterte Installationsszenarios für Adobe Commerce in Ihrer Infrastruktur.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 0%

---

# Fortgeschrittene Installation vor Ort

>[!TIP]
>
>Verloren? Benötige eine helfende Hand? Probieren Sie unsere Handbücher für die [Schnellstart-Installation](composer.md) oder die [Contributor-Installation](https://developer.adobe.com/commerce/contributor/guides/install/) aus.

>[!NOTE]
>
>Wenn Sie SELinux aktiviert haben, lesen Sie [SELinux und iptables](prerequisites/security.md).

## Befehlszeilenschnittstelle (CLI)

Adobe Commerce verfügt über eine einzige Befehlszeilenschnittstelle für Installations- und Konfigurationsaufgaben: `<magento_root>/bin/magento`. Die Oberfläche führt mehrere Aufgaben durch, darunter:

* Installation (und damit verbundene Aufgaben wie Erstellen oder Aktualisieren des Datenbankschemas, Erstellen der Bereitstellungskonfiguration).
* Löschen des Cache
* Verwalten von Indizes, einschließlich Neuindizierung.
* Erstellen von Übersetzungswörterbüchern und Übersetzungspaketen.
* Generieren nicht vorhandener Klassen wie Fabriken und Abfänger für Plug-ins, Generieren der Konfiguration für die Injektion der Abhängigkeit für den Objektmanager.
* Bereitstellen von statischen Ansichtsdateien.
* Erstellen von CSS aus weniger.

Weitere Vorteile:

* Ein einzelner Befehl (`<magento_root>/bin/magento list`) listet alle verfügbaren Installations- und Konfigurationsbefehle auf.
* Konsistente Benutzeroberfläche basierend auf Symfony.
* Die CLI ist erweiterbar, sodass Entwickler von Drittanbietern sie &quot;einbinden&quot;können. Dies hat den zusätzlichen Vorteil, dass die Lernkurve der Benutzer entfernt wird.
* Befehle für deaktivierte Module werden nicht angezeigt.

In diesem Thema wird die Installation der Adobe Commerce-Software mithilfe des CLI erläutert. Weitere Informationen zur Konfiguration finden Sie im [Konfigurationshandbuch](../configuration/overview.md).

Das Installationsprogramm kann bei Bedarf mehrmals ausgeführt werden, damit Sie Folgendes tun können:

* Bereitstellung verschiedener Werte

  Nachdem Sie beispielsweise Ihren Webserver für Secure Sockets Layer (SSL) konfiguriert haben, können Sie das Installationsprogramm ausführen, um SSL-Optionen festzulegen.

* Korrigieren von Fehlern in früheren Installationen
* Installieren von Adobe Commerce in einer anderen Datenbankinstanz

## Vor Beginn der Installation

Führen Sie zuerst die folgenden Schritte aus:

* Stellen Sie sicher, dass Ihr System die in [Systemanforderungen](system-requirements.md) beschriebenen Anforderungen erfüllt.

* Führen Sie alle Aufgaben für [Voraussetzung](prerequisites/overview.md) aus.

* Führen Sie die ersten Installationsschritte aus. Siehe [Ihren Installations- oder Aktualisierungspfad](overview.md).

* Nachdem Sie sich beim Anwendungsserver angemeldet haben, wechseln Sie [zum Dateisysteminhaber](prerequisites/file-system/overview.md).

* Überprüfen Sie die Übersicht über den [Schnellstart für die Installation](composer.md).

>[!NOTE]
>
>Sie müssen Adobe Commerce aus dem Unterverzeichnis `bin` installieren.

Sie können das Installationsprogramm mehrmals mit verschiedenen Optionen ausführen, um Installationsaufgaben wie die folgenden abzuschließen:

* In Phasen installieren - Nachdem Sie beispielsweise Ihren Webserver für Secure Sockets Layer (SSL) konfiguriert haben, können Sie das Installationsprogramm erneut ausführen, um SSL-Optionen festzulegen.

* Korrigieren Sie Fehler in früheren Installationen.

* Installieren Sie Adobe Commerce in einer anderen Datenbankinstanz.

>[!NOTE]
>
>Standardmäßig überschreibt das Installationsprogramm die Datenbank nicht, wenn Sie die Software in derselben Datenbankinstanz installieren. Sie können den optionalen Parameter `cleanup-database` verwenden, um dieses Verhalten zu ändern.

Siehe auch [Aktualisieren, Neuinstallieren, Deinstallieren](tutorials/uninstall.md).

### Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Hilfebefehle für Installationsprogramme

Sie können die folgenden Befehle ausführen, um Werte für einige erforderliche Argumente zu finden:

| Installationsargument | Befehl |
| ------------------ | ------------------------------- |
| Sprache | `bin/magento info:language:list` |
| Währung | `bin/magento info:currency:list` |
| Zeitzone | `bin/magento info:timezone:list` |

>[!NOTE]
>
>Wenn beim Ausführen dieser Befehle ein Fehler angezeigt wird, überprüfen Sie, ob Sie die Installationsabhängigkeiten aktualisiert haben, wie unter [Aktualisieren der Installationsabhängigkeiten](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/) beschrieben.

## Installieren über die Befehlszeile

Der Installationsbefehl verwendet das folgende Format:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

In den folgenden Tabellen werden die Namen und Werte der Installationsoptionen beschrieben. Beispiel für Installationsbefehle finden Sie unter [Beispiele für lokale Host-Installationen](#sample-localhost-installations).

>[!NOTE]
>
>Alle Optionen, die Leerzeichen oder Sonderzeichen enthalten, müssen in einfache oder doppelte Anführungszeichen gesetzt werden.

**Administratorberechtigungen:**

Die folgenden Optionen geben die Benutzerinformationen und Anmeldeinformationen für den Admin-Benutzer an.

Sie können den Admin-Benutzer während oder nach der Installation erstellen. Wenn Sie den Benutzer während der Installation erstellen, sind alle Variablen mit Administratorberechtigungen erforderlich. Siehe [Beispiel für lokale Host-Installationen](#sample-localhost-installations).

Die folgenden Tabellen enthalten viele, aber nicht alle verfügbaren Installationsparameter. Eine vollständige Liste finden Sie in der [Befehlszeilen-Tools-Referenz](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--admin-firstname` | Vorname des Administratorbenutzers. | Ja |
| `--admin-lastname` | Nachname des Administratorbenutzers. | Ja |
| `--admin-email` | E-Mail-Adresse des Administrators. | Ja |
| `--admin-user` | Administrator-Benutzername. | Ja |
| `--admin-password` | Administratorkennwort. Das Kennwort muss mindestens 7 Zeichen lang sein und mindestens ein alphabetisches und ein numerisches Zeichen enthalten. Wir empfehlen ein längeres, komplexeres Passwort. Schließen Sie die gesamte Kennwortzeichenfolge in einfache Anführungszeichen ein. Beispiel: `--admin-password='A0b9%t3g'` | Ja |

**Site- und Datenbankkonfigurationsoptionen:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--base-url` | Basis-URL für den Zugriff auf Ihren Admin und Ihre Storefront in einem der folgenden Formate:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Hinweis:** Das Schema (http:// oder https://) und ein Schrägstrich sind beide erforderlich.<br><br>`<your install dir>` ist der docroot-relative Pfad zum Installieren der Adobe Commerce-Software. Je nachdem, wie Sie Ihren Webserver und virtuelle Hosts einrichten, kann der Pfad magento2 sein oder leer sein.<br><br>Verwenden Sie für den Zugriff auf Adobe Commerce oder MagenAdobe Commerce entweder `http://127.0.0.1/<your install dir>/` oder `http://127.0.0.1/<your install dir>/`.<br><br> - `{{base_url}}` , was eine Basis-URL darstellt, die von einer virtuellen Host-Einstellung oder einer Virtualisierungsumgebung wie Docker definiert wird. Wenn Sie beispielsweise einen virtuellen Host mit dem Hostnamen `magento.example.com` einrichten, können Sie die Software mit `--base-url={{base_url}}` installieren und mit einer URL wie `http://magento.example.com/admin` auf den Admin zugreifen. | Ja |
| `--backend-frontname` | Uniform Resource Identifier (URI) für den Zugriff auf den Admin. Sie können diesen Parameter weglassen, damit die Anwendung einen zufälligen URI für Sie mit dem folgenden Muster generiert: <code>admin_jkhgdfq</code>.<br><br>Aus Sicherheitsgründen empfehlen wir einen zufälligen URI. Eine zufällige URI ist für Hacker oder böswillige Software schwieriger zu nutzen.<br><br>Der URI wird am Ende der Installation angezeigt. Sie können es jederzeit mit dem Befehl `bin/magento info:adminuri` anzeigen.<br><br>Wenn Sie einen Wert eingeben möchten, empfehlen wir, kein gemeinsames Wort wie &quot;admin&quot;, &quot;backend&quot;zu verwenden. Der Admin-URI kann nur alphanumerische Werte und das Unterstrichzeichen (`_`) enthalten. | Nein |
| `--db-host` | Verwenden Sie einen der folgenden Schritte:<br><br> - Der vollständig qualifizierte Hostname oder die IP-Adresse des Datenbankservers.<br><br>- `localhost` (Standard) oder `127.0.0.1` , wenn sich Ihr Datenbankserver auf demselben Host wie Ihr Webserver befindet. localhost bedeutet, dass die MySQL-Client-Bibliothek UNIX-Sockets verwendet, um eine Verbindung zur Datenbank herzustellen. `127.0.0.1` bewirkt, dass die Client-Bibliothek das TCP-Protokoll verwendet. Weitere Informationen zu Sockets finden Sie in der [PHP PDO_MYSQL-Dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Hinweis:** Sie können optional den Datenbankserver-Port in seinem Hostnamen angeben, z. B. www.example.com:9000 | Ja |
| `--db-name` | Name der Datenbankinstanz, in der Sie die Datenbanktabellen installieren möchten.<br><br>Der Standardwert ist `magento2`. | Ja |
| `--db-user` | Benutzername des Eigentümers der Datenbankinstanz.<br><br>Der Standardwert ist `root`. | Ja |
| `--db-password` | Passwort des Inhabers der Datenbankinstanz. | Ja |
| `--db-prefix` | Verwenden Sie dies nur, wenn Sie die Datenbanktabellen in einer Datenbankinstanz installieren, in der bereits Adobe Commerce-Tabellen enthalten sind.<br><br>Verwenden Sie in diesem Fall ein Präfix, um die Tabellen für diese Installation zu identifizieren. Einige Kunden verfügen über mehr als einen Adobe Commerce- oder MagenAdobe Commerce-Server mit allen Tabellen in derselben Datenbank.<br><br>Das Präfix kann maximal fünf Zeichen lang sein. Sie muss mit einem Brief beginnen und darf nur Buchstaben, Zahlen und Unterstriche enthalten.<br><br>Mit dieser Option können diese Kunden den Datenbankserver für mehrere Adobe Commerce-Installationen freigeben. |
| `--db-ssl-key` | Pfad zum Client-Schlüssel. | Nein |
| `--db-ssl-cert` | Pfad zum Client-Zertifikat. | Nein |
| `--db-ssl-ca` | Pfad zum Serverzertifikat. | Nein |
| `--language` | Sprachcode für die Verwendung in Admin und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Sprachcodes anzeigen, indem Sie `bin/magento info:language:list` aus dem Ordner bin eingeben.) | Nein |
| `--currency` | Standardwährung für die Verwendung in der Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Währungen durch Eingabe von `bin/magento info:currency:list` aus dem Ordner bin anzeigen.) | Nein |
| `--timezone` | Standardzeitzone zur Verwendung in der Admin- und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Zeitzonen anzeigen, indem Sie `bin/magento info:timezone:list` aus dem Verzeichnis `bin/` eingeben.) | Nein |
| `--use-rewrites` | `1` bedeutet, dass Sie Webserver-Neuschreibungen für generierte Links in der Storefront und in Admin verwenden.<br><br>`0` deaktiviert die Verwendung von Webserver-Neuschreibungen. Dies ist die Standardeinstellung. | Nein |
| `--use-secure` | `1` ermöglicht die Verwendung von Secure Sockets Layer (SSL) in Storefront-URLs. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` deaktiviert die Verwendung von SSL. In diesem Fall wird angenommen, dass alle anderen sicheren URL-Optionen ebenfalls 0 sind. Dies ist die Standardeinstellung. | Nein |
| `--base-url-secure` | Sichere Basis-URL für den Zugriff auf Ihren Admin und Ihre Storefront im folgenden Format: `http[s]://<host or ip>/<your install dir>/` | Nein |
| `--use-secure-admin` | `1` bedeutet, dass Sie SSL verwenden, um auf den Admin zuzugreifen. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` bedeutet, dass Sie SSL nicht mit dem Administrator verwenden. Dies ist die Standardeinstellung. | Nein |
| `--admin-use-security-key` | 1 bewirkt, dass die Anwendung einen zufällig generierten Schlüsselwert verwendet, um auf Seiten in Admin und in Formularen zuzugreifen. Diese Schlüsselwerte helfen dabei, siteübergreifende Skriptfälschungsangriffe zu verhindern. Dies ist die Standardeinstellung.<br><br>`0` deaktiviert die Verwendung des Schlüssels. | Nein |
| `--session-save` | Verwenden Sie einen der folgenden Schritte:<br><br> - `db` , um Sitzungsdaten in der Datenbank zu speichern. Wählen Sie Datenbankspeicher, wenn Sie über eine Clusterdatenbank verfügen. Andernfalls hat der dateibasierte Speicher möglicherweise keinen großen Vorteil.<br><br>- `files` , um Sitzungsdaten im Dateisystem zu speichern. Eine dateibasierte Sitzungsspeicherung ist angemessen, es sei denn, der Dateisystemzugriff ist langsam, Sie haben eine Clusterdatenbank oder Sie möchten Sitzungsdaten in Redis speichern.<br><br> - `redis` , um Sitzungsdaten in Redis zu speichern. Wenn Sie Redis für Standard- oder Seiten-Caching verwenden, muss Redis bereits installiert sein. Weitere Informationen zum Konfigurieren der Unterstützung für Redis finden Sie unter Verwenden von Redis für die Sitzungsspeicherung . | Nein |
| `--key` | Wenn Sie einen Schlüssel haben, geben Sie einen Schlüssel an, um vertrauliche Daten in der Datenbank zu verschlüsseln. Wenn Sie keine haben, generiert das Programm eine für Sie. | Ja |
| `--cleanup-database` | Um Datenbanktabellen vor der Installation von Adobe Commerce abzulegen, geben Sie diesen Parameter ohne Wert an. Andernfalls bleibt die Datenbank intakt. | Nein |
| `--db-init-statements` | Erweiterter MySQL-Konfigurationsparameter. Verwendet Anweisungen zur Datenbankinitialisierung, die beim Herstellen einer Verbindung zur MySQL-Datenbank ausgeführt werden. Lesen Sie einen ähnlichen Verweis wie diesen, bevor Sie Werte festlegen.<br><br>Der Standardwert ist `SET NAMES utf8;`. | Nein |
| `--sales-order-increment-prefix` | Geben Sie einen Zeichenfolgenwert an, der als Präfix für Verkaufsaufträge verwendet werden soll. Normalerweise wird dies verwendet, um eindeutige Bestellnummern für Zahlungsverarbeiter zu garantieren. | Nein |

**Suchmaschinenkonfigurationsoptionen:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--search-engine` | Die Version von Elasticsearch oder OpenSearch, die als Suchmaschine verwendet werden soll. Der Standardwert ist `elasticsearch7`. Elasticsearch 5 wird nicht mehr empfohlen. | Nein |
| `--elasticsearch-host` | Der Hostname oder die IP-Adresse, unter der Elasticsearch ausgeführt wird. Der Standardwert ist `localhost`. | Nein |
| `--elasticsearch-port` | Der Elasticsearch-Port für eingehende HTTP-Anforderungen. Der Standardwert ist `9200`. | Nein |
| `--elasticsearch-index-prefix` | Ein Präfix, das den Suchindex des Elasticsearchs angibt. Der Standardwert ist `magento2`. | Nein |
| `--elasticsearch-timeout` | Die Anzahl der Sekunden, bevor das System eine Zeitüberschreitung aufweist. Der Standardwert ist `15`. | Nein |
| `--elasticsearch-enable-auth` | Aktiviert die Authentifizierung auf dem Elasticsearch-Server. Der Standardwert ist `false`. | Nein |
| `--elasticsearch-username` | Die Benutzer-ID für die Authentifizierung beim Elasticsearch-Server. | Nein, sofern die Authentifizierung nicht aktiviert ist |
| `--elasticsearch-password` | Das Kennwort für die Authentifizierung beim Elasticsearchserver. | Nein, sofern die Authentifizierung nicht aktiviert ist |
| `--opensearch-host` | Der Hostname oder die IP-Adresse, unter der OpenSearch ausgeführt wird. Der Standardwert ist `localhost`. | Nein |
| `--opensearch-port` | Der OpenSearch-Port für eingehende HTTP-Anforderungen. Der Standardwert ist `9200`. | Nein |
| `--opensearch-index-prefix` | Ein Präfix, das den OpenSearch-Suchindex angibt. Der Standardwert ist `magento2`. | Nein |
| `--opensearch-timeout` | Die Anzahl der Sekunden, bevor das System eine Zeitüberschreitung aufweist. Der Standardwert ist `15`. | Nein |
| `--opensearch-enable-auth` | Aktiviert die Authentifizierung auf dem OpenSearch-Server. Der Standardwert ist `false`. | Nein |
| `--opensearch-username` | Die Benutzer-ID für die Authentifizierung beim OpenSearch-Server. | Nein, sofern die Authentifizierung nicht aktiviert ist |
| `--opensearch-password` | Das Kennwort für die Authentifizierung beim OpenSearch-Server. | Nein, sofern die Authentifizierung nicht aktiviert ist |

**[!DNL RabbitMQ]Konfigurationsoptionen:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--amqp-host` | Verwenden Sie die `--amqp` -Optionen nur, wenn Sie bereits eine Installation von [!DNL RabbitMQ] eingerichtet haben. Weitere Informationen zum Installieren und Konfigurieren von [!DNL RabbitMQ] finden Sie unter [!DNL RabbitMQ] Installation .<br><br>Der Hostname, auf dem [!DNL RabbitMQ] installiert ist. | Nein |
| `--amqp-port` | Der Anschluss, über den eine Verbindung zu [!DNL RabbitMQ] hergestellt werden soll. Der Standardwert ist 5672. | Nein |
| `--amqp-user` | Der Benutzername für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht den Standardbenutzer `guest`. | Nein |
| `--amqp-password` | Das Kennwort für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht das Standardkennwort `guest`. | Nein |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung mit [!DNL RabbitMQ]. Der Standardwert ist `/`. | Nein |
| `--amqp-ssl` | Gibt an, ob eine Verbindung zu [!DNL RabbitMQ] hergestellt werden soll. Der Standardwert ist `false`. Informationen zum Einrichten von SSL für [!DNL RabbitMQ] finden Sie unter [!DNL RabbitMQ] . | Nein |
| `--consumers-wait-for-messages` | Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein | Nein |

**Konfigurationsoptionen sperren:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--lock-provider` | Name des Anbieters sperren.<br><br>Verfügbare Sperranbieter: `db`, `zookeeper`, `file`.<br><br>Der standardmäßige Sperranbieter: `db` | Nein |
| `--lock-db-prefix` | Das spezifische db-Präfix, um Sperrkonflikte bei der Verwendung des `db` -Sperranbieters zu vermeiden.<br><br>Der Standardwert: `NULL` | Nein |
| `--lock-zookeeper-host` | Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster bei Verwendung des `zookeeper`-Sperranbieters.<br><br>Beispiel: `127.0.0.1:2181` | Ja, wenn Sie `--lock-provider=zookeeper` festlegen |
| `--lock-zookeeper-path` | Der Pfad, in dem Zookeeper Sperren speichert.<br><br>Der Standardpfad lautet: `/magento/locks` | Nein |
| `--lock-file-path` | Der Pfad, in dem Dateisperren gespeichert werden. | Ja, wenn Sie `--lock-provider=file` festlegen |

**Konfigurationsoptionen für Verbraucher:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Informationen zum Aktivieren oder Deaktivieren von Modulen nach der Installation von Adobe Commerce finden Sie unter [Module aktivieren und deaktivieren](tutorials/manage-modules.md).

**Vertrauliche Daten:**

{{$include /help/_includes/sensitive-data.md}}

### Beispiele für lokale Host-Installationen

Die folgenden Beispiele zeigen die Befehle zur lokalen Installation von Adobe Commerce mit verschiedenen Optionen.

#### Beispiel 1: Grundlegende Installation mit einem Administratorkonto

Im folgenden Beispiel wird Adobe Commerce mit den folgenden Optionen installiert:

* Das Programm wird im Ordner &quot;`magento2`&quot; relativ zum Basisverzeichnis des Webservers unter &quot;`localhost`&quot; installiert und der Pfad zum Admin ist &quot;`admin`&quot;. Daher gilt:

  Ihre Storefront-URL lautet `http://127.0.0.1`

* Der Datenbankserver befindet sich auf demselben Host wie der Webserver.

  Der Datenbankname ist `magento` und der Benutzername und das Kennwort sind beide `magento`

* Verwendet Server-Neuschreibungen

* Der Administrator verfügt über die folgenden Eigenschaften:

   * Vor- und Nachnamen lauten `Magento User`
   * Benutzername ist `admin` und das Kennwort ist `admin123`
   * E-Mail-Adresse ist `user@example.com`

* Die Standardsprache ist `en_US` (US-Englisch).
* Die Standardwährung ist US-Dollar.
* Die standardmäßige Zeitzone ist US Central (Amerika/Chicago).
* OpenSearch 1.2 ist auf `os-host.example.com` installiert und verbindet sich mit Port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Meldungen, die der folgenden Anzeige ähneln, zeigen eine erfolgreiche Installation an:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Beispiel 2: Grundlegende Installation ohne Administratorkonto

Sie können Adobe Commerce installieren, ohne den Administratorbenutzer zu erstellen, wie im folgenden Beispiel gezeigt.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Meldungen wie die folgende werden bei erfolgreicher Installation angezeigt:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Nach der Installation können Sie einen Admin-Benutzer mithilfe des Befehls `admin:user:create` erstellen:
[Erstellen oder Bearbeiten eines Administrators](tutorials/admin.md#create-or-edit-an-administrator)

#### Beispiel 3: Installation mit zusätzlichen Optionen

Im folgenden Beispiel wird Adobe Commerce mit den folgenden Optionen installiert:

* Das Programm wird im Ordner &quot;`magento2`&quot; relativ zum Basisverzeichnis des Webservers unter &quot;`localhost`&quot; installiert und der Pfad zum Admin ist &quot;`admin`&quot;. Daher gilt:

  Ihre Storefront-URL lautet `http://127.0.0.1`

* Der Datenbankserver befindet sich auf demselben Host wie der Webserver.

  Der Datenbankname ist `magento` und der Benutzername und das Kennwort sind beide `magento`

* Der Administrator verfügt über die folgenden Eigenschaften:

   * Vor- und Nachnamen lauten `Magento User`
   * Benutzername ist `admin` und das Kennwort ist `admin123`
   * E-Mail-Adresse ist `user@example.com`

* Die Standardsprache ist `en_US` (US-Englisch).
* Die Standardwährung ist US-Dollar.
* Die standardmäßige Zeitzone ist US Central (Amerika/Chicago).
* Das Installationsprogramm bereinigt zunächst die Datenbank, bevor die Tabellen und das Schema installiert werden
* Sie können das Inkrementierungs-Präfix `ORD$` für die Bestellung verwenden (da es das Sonderzeichen [`$`] enthält, muss der Wert in doppelte Anführungszeichen gesetzt werden)
* Sitzungsdaten werden in der Datenbank gespeichert
* Verwendet Server-Neuschreibungen
* OpenSearch ist auf `os-host.example.com` installiert und verbindet sich mit Port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>Sie müssen den Befehl entweder in einer einzelnen Zeile oder, wie im vorangehenden Beispiel, mit dem Zeichen `\` am Ende jeder Zeile eingeben.

Meldungen wie die folgende werden bei erfolgreicher Installation angezeigt:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
