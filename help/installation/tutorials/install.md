---
title: Installieren von Adobe Commerce
description: Führen Sie diese Schritte aus, um Adobe Commerce oder Magento Open Source in Ihrer Infrastruktur zu installieren.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '2102'
ht-degree: 0%

---

# Installieren von Adobe Commerce

Führen Sie zuerst die folgenden Schritte aus:

* Stellen Sie sicher, dass Ihr System die in der [Systemanforderungen](../system-requirements.md).

* Alle [Voraussetzung](../prerequisites/overview.md) Aufgaben.

* Führen Sie die ersten Installationsschritte aus. Siehe [Ihren Installations- oder Aktualisierungspfad](../overview.md).

* Nach der Anmeldung beim Anwendungsserver [Wechseln zum Dateisysteminhaber](../prerequisites/file-system/overview.md).

* Überprüfen Sie die [Erste Schritte mit der Befehlszeileninstallation](../composer.md) Übersicht.

>[!NOTE]
>
>Sie müssen das Programm über `bin` -Unterverzeichnis.

Sie können das Installationsprogramm mehrmals mit verschiedenen Optionen ausführen, um Installationsaufgaben wie die folgenden abzuschließen:

* In Phasen installieren - Nachdem Sie beispielsweise Ihren Webserver für Secure Sockets Layer (SSL) konfiguriert haben, können Sie das Installationsprogramm erneut ausführen, um SSL-Optionen festzulegen.

* Korrigieren Sie Fehler in früheren Installationen.

* Installieren Sie die Anwendung in einer anderen Datenbankinstanz.

>[!NOTE]
>
>Standardmäßig überschreibt das Installationsprogramm die Datenbank nicht, wenn Sie die Commerce-Software in derselben Datenbankinstanz installieren. Sie können die optionale `cleanup-database` -Parameter, um dieses Verhalten zu ändern.

Siehe auch [Aktualisieren, Neuinstallieren, Deinstallieren](uninstall.md).

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Hilfebefehle für Installationsprogramme

Sie können die folgenden Befehle ausführen, um Werte für einige erforderliche Argumente zu finden:

| Installationsargument | Befehl |
| ------------------ | ------------------------------- |
| Sprache | `magento info:language:list` |
| Währung | `magento info:currency:list` |
| Zeitzone | `magento info:timezone:list` |

>[!NOTE]
>
>Wenn beim Ausführen dieser Befehle ein Fehler angezeigt wird, überprüfen Sie, ob Sie die Installationsabhängigkeiten aktualisiert haben, wie hier beschrieben: [Aktualisieren von Installationsabhängigkeiten](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installieren über die Befehlszeile

Der Installationsbefehl verwendet das folgende Format:

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

In den folgenden Tabellen werden die Namen und Werte der Installationsoptionen beschrieben, z. B. Installationsbefehle. Siehe [Beispiele für lokale Host-Installationen](#sample-localhost-installations).

>[!NOTE]
>
>Alle Optionen, die Leerzeichen oder Sonderzeichen enthalten, müssen in einfache oder doppelte Anführungszeichen gesetzt werden.

**Administratorberechtigungen:**

Die folgenden Optionen geben die Benutzerinformationen und Anmeldeinformationen für den Admin-Benutzer an.

In Adobe Commerce-Version 2.2.8 und höher können Sie den Admin-Benutzer während oder nach der Installation erstellen. Wenn Sie den Benutzer während der Installation erstellen, sind alle Variablen mit Administratorberechtigungen erforderlich. Siehe [Beispiele für lokale Host-Installationen](#sample-localhost-installations).

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
| `--base-url` | Basis-URL, die für den Zugriff auf Ihr Admin und Ihre Storefront in einem der folgenden Formate verwendet wird:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Hinweis:** Das Schema (http:// oder https://) und ein Schrägstrich sind beide erforderlich.<br><br>`<your install dir>` ist der docroot-relative Pfad, in dem die Anwendung installiert werden soll. Je nachdem, wie Sie Ihren Webserver und virtuelle Hosts einrichten, kann der Pfad magento2 sein oder leer sein.<br><br>Um auf die Anwendung auf localhost zuzugreifen, können Sie entweder `http://127.0.0.1/<your install dir>/` oder `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` , die eine Basis-URL darstellt, die von einer virtuellen Host-Einstellung oder einer Virtualisierungsumgebung wie Docker definiert wird. Wenn Sie beispielsweise einen virtuellen Host mit dem Hostnamen commerce.example.com einrichten, können Sie die Anwendung mit `--base-url={{base_url}}` und greifen Sie mit einer URL wie auf den Administrator zu `http://commerce.example.com/admin`. | Ja |
| `--backend-frontname` | Uniform Resource Identifier (URI) für den Zugriff auf den Admin. Sie können diesen Parameter weglassen, damit die Anwendung einen zufälligen URI mit dem folgenden Muster generiert <code>admin_jkhgdfq</code>.<br><br>Aus Sicherheitsgründen empfehlen wir einen zufälligen URI. Eine zufällige URI ist für Hacker oder böswillige Software schwieriger zu nutzen.<br><br>Der URI wird am Ende der Installation angezeigt. Sie können sie jederzeit mithilfe der `magento info:adminuri` Befehl.<br><br>Wenn Sie einen Wert eingeben möchten, empfehlen wir, kein gemeinsames Wort wie &quot;admin&quot;, &quot;backend&quot;zu verwenden. Der Administrator-URI kann alphanumerische Werte und Unterstriche (`_`). | Nein |
| `--db-host` | Verwenden Sie einen der folgenden Schritte:<br><br>- Der vollständig qualifizierte Hostname oder die IP-Adresse des Datenbankservers.<br><br>- `localhost` (Standard) oder `127.0.0.1` Wenn sich Ihr Datenbankserver auf demselben Host befindet wie Ihr Webserver.localhost bedeutet, dass die MySQL-Client-Bibliothek UNIX-Sockets verwendet, um eine Verbindung zur Datenbank herzustellen. `127.0.0.1` bewirkt, dass die Client-Bibliothek das TCP-Protokoll verwendet. Weitere Informationen zu Sockets finden Sie im Abschnitt [PHP PDO_MYSQL-Dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Hinweis:** Sie können optional den Datenbankserver-Port in seinem Hostnamen angeben, z. B. www.example.com:9000 | Ja |
| `--db-name` | Name der Datenbankinstanz, in der Sie die Datenbanktabellen installieren möchten.<br><br>Der Standardwert ist `magento2`. | Ja |
| `--db-user` | Benutzername des Eigentümers der Datenbankinstanz.<br><br>Der Standardwert ist `root`. | Ja |
| `--db-password` | Passwort des Inhabers der Datenbankinstanz. | Ja |
| `--db-prefix` | Verwenden Sie dies nur, wenn Sie die Datenbanktabellen in einer Datenbankinstanz installieren, in der bereits Adobe Commerce- oder Magento Open Source-Tabellen enthalten sind.<br><br>Verwenden Sie in diesem Fall ein Präfix, um die Tabellen für diese Installation zu identifizieren. Einige Kunden haben mehrere Adobe Commerce-Instanzen, die auf einem Server mit allen Tabellen in derselben Datenbank ausgeführt werden.<br><br>Das Präfix kann maximal fünf Zeichen lang sein. Sie muss mit einem Brief beginnen und darf nur Buchstaben, Zahlen und Unterstriche enthalten.<br><br>Mit dieser Option können diese Kunden den Datenbankserver für mehrere Installationen freigeben. | Nein |
| `--db-ssl-key` | Pfad zum Client-Schlüssel. | Nein |
| `--db-ssl-cert` | Pfad zum Client-Zertifikat. | Nein |
| `--db-ssl-ca` | Pfad zum Serverzertifikat. | Nein |
| `--language` | Sprachcode für die Verwendung in Admin und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Sprachcodes durch Eingabe von `magento info:language:list` aus dem Ordner bin.) | Nein |
| `--currency` | Standardwährung für die Verwendung in der Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Währungen durch Eingabe von `magento info:currency:list` aus dem Ordner bin.) | Nein |
| `--timezone` | Standardzeitzone zur Verwendung in der Admin- und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Zeitzonen durch Eingabe von `magento info:timezone:list` aus dem Ordner bin.) | Nein |
| `--use-rewrites` | `1` bedeutet, dass Sie Webserver-Neuschreibungen für generierte Links in der Storefront und in Admin verwenden.<br><br>`0` deaktiviert die Verwendung von Webserver-Neuschreibungen. Dies ist die Standardeinstellung. | Nein |
| `--use-secure` | `1` ermöglicht die Verwendung von Secure Sockets Layer (SSL) in Storefront-URLs. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` deaktiviert die Verwendung von SSL. In diesem Fall wird angenommen, dass alle anderen sicheren URL-Optionen ebenfalls 0 sind. Dies ist die Standardeinstellung. | Nein |
| `--base-url-secure` | Sichere Basis-URL für den Zugriff auf Ihre Admin- und Storefront im folgenden Format: `http[s]://<host or ip>/<your install dir>/` | Nein |
| `--use-secure-admin` | `1` bedeutet, dass Sie SSL verwenden, um auf den Admin zuzugreifen. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` bedeutet, dass Sie SSL nicht mit dem Administrator verwenden. Dies ist die Standardeinstellung. | Nein |
| `--admin-use-security-key` | 1 bewirkt, dass die Anwendung einen zufällig generierten Schlüsselwert verwendet, um auf Seiten in Admin und in Formularen zuzugreifen. Diese Schlüsselwerte helfen dabei, siteübergreifende Skriptfälschungsangriffe zu verhindern. Dies ist die Standardeinstellung.<br><br>`0` deaktiviert die Verwendung des Schlüssels. | Nein |
| `--session-save` | Verwenden Sie einen der folgenden Schritte:<br><br>- `db` , um Sitzungsdaten in der Datenbank zu speichern. Wählen Sie Datenbankspeicher, wenn Sie über eine Clusterdatenbank verfügen. Andernfalls hat der dateibasierte Speicher möglicherweise keinen großen Vorteil.<br><br>- `files` , um Sitzungsdaten im Dateisystem zu speichern. Eine dateibasierte Sitzungsspeicherung ist angemessen, es sei denn, der Dateisystemzugriff ist langsam, Sie haben eine Clusterdatenbank oder Sie möchten Sitzungsdaten in Redis speichern.<br><br>- `redis` , um Sitzungsdaten in Redis zu speichern. Wenn Sie Redis für Standard- oder Seiten-Caching verwenden, muss Redis bereits installiert sein. Weitere Informationen zum Konfigurieren der Unterstützung für Redis finden Sie unter Verwenden von Redis für die Sitzungsspeicherung . | Nein |
| `--key` | Wenn Sie einen Schlüssel haben, geben Sie einen Schlüssel an, um vertrauliche Daten in der Datenbank zu verschlüsseln. Wenn Sie keine haben, generiert das Programm eine für Sie. | Ja |
| `--cleanup-database` | Um Datenbanktabellen vor der Installation der Anwendung abzulegen, geben Sie diesen Parameter ohne Wert an. Andernfalls bleibt die Datenbank intakt. | Nein |
| `--db-init-statements` | Erweiterter MySQL-Konfigurationsparameter. Verwendet Anweisungen zur Datenbankinitialisierung, die beim Herstellen einer Verbindung zur MySQL-Datenbank ausgeführt werden. Lesen Sie einen ähnlichen Verweis wie diesen, bevor Sie Werte festlegen.<br><br>Der Standardwert ist `SET NAMES utf8;`. | Nein |
| `--sales-order-increment-prefix` | Geben Sie einen Zeichenfolgenwert an, der als Präfix für Verkaufsaufträge verwendet werden soll. Normalerweise wird dies verwendet, um eindeutige Bestellnummern für Zahlungsverarbeiter zu garantieren. | Nein |

>[!TIP]
>
>Informationen zum Aktivieren von Remote-Speicherdiensten während der Installation finden Sie unter [Remote Storage konfigurieren](../../configuration/remote-storage/remote-storage.md) im _Konfigurationshandbuch_.

**Suchmaschinenkonfigurationsoptionen:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--search-engine` | Die Version der Suchmaschine. Mögliche Werte sind `elasticsearch7`, `elasticsearch6`, und `elasticsearch5`. Der Standardwert ist `elasticsearch7`. Wenn Sie OpenSearch als Suchmaschine installiert haben, geben Sie den Wert an `elasticsearch7`. Elasticsearch 5 wird nicht mehr empfohlen. | Nein |
| `--elasticsearch-host` | Der Hostname oder die IP-Adresse, unter der die Suchmaschine ausgeführt wird. Der Standardwert ist `localhost`. | Nein |
| `--elasticsearch-port` | Der Port für eingehende HTTP-Anforderungen. Der Standardwert ist `9200`. | Nein |
| `--elasticsearch-index-prefix` | Ein Präfix, das den Suchindex angibt. Der Standardwert ist `magento2`. | Nein |
| `--elasticsearch-timeout` | Die Anzahl der Sekunden, bevor das System eine Zeitüberschreitung aufweist. Der Standardwert ist `15`. | Nein |
| `--elasticsearch-enable-auth` | Aktiviert die Authentifizierung auf dem Suchmaschinenserver. Der Standardwert ist `false`. | Nein |
| `--elasticsearch-username` | Die zu authentifizierende Benutzer-ID | Nein, sofern die Authentifizierung nicht aktiviert ist |
| `--elasticsearch-password` | Das zu authentifizierende Kennwort | Nein, sofern die Authentifizierung nicht aktiviert ist |

**[!DNL RabbitMQ]Konfigurationsoptionen:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--amqp-host` | Verwenden Sie nicht das `--amqp` Optionen, sofern Sie nicht bereits eine Installation von [!DNL RabbitMQ]. Siehe [!DNL RabbitMQ] Installation für weitere Informationen zur Installation und Konfiguration [!DNL RabbitMQ].<br><br>Der Hostname, in dem [!DNL RabbitMQ] installiert ist. | Nein |
| `--amqp-port` | Der Anschluss, mit dem die Verbindung hergestellt werden soll [!DNL RabbitMQ]. Der Standardwert ist 5672. | Nein |
| `--amqp-user` | Der Benutzername für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht den Standardbenutzer `guest`. | Nein |
| `--amqp-password` | Das Kennwort für die Verbindung zu [!DNL RabbitMQ]. Verwenden Sie nicht das Standardkennwort `guest`. | Nein |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung zu [!DNL RabbitMQ]. Der Standardwert ist `/`. | Nein |
| `--amqp-ssl` | Gibt an, ob eine Verbindung hergestellt werden soll [!DNL RabbitMQ]. Der Standardwert ist `false`. Siehe [!DNL RabbitMQ] Informationen zum Einrichten von SSL für [!DNL RabbitMQ]. | Nein |
| `--consumers-wait-for-messages` | Sollten Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein | Nein |

**Remote-Speicheroptionen:**

| Name | Beschreibung | Erforderlich? |
|--- |--- |--- |
| `remote-storage-driver` | Adaptername<br>Mögliche Werte:<br>**file**: Deaktiviert den Remote-Speicher und verwendet das lokale Dateisystem.<br>**aws-s3**: Verwenden Sie die [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) | Nein |
| `remote-storage-bucket` | Objektspeicherung oder Containername | Nein |
| `remote-storage-prefix` | Optionales Präfix (Speicherort innerhalb des Objektspeichers) | Nein |
| `remote-storage-region` | Regionsname | Nein |
| `remote-storage-key` | Optionaler Zugriffsschlüssel | Nein |
| `remote-storage-secret` | Optionaler geheimer Schlüssel | Nein |

**Konfigurationsoptionen sperren:**

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--lock-provider` | Name des Anbieters sperren.<br><br>Verfügbare Sperranbieter: `db`, `zookeeper`, `file`.<br><br>Der standardmäßige Sperranbieter: `db` | Nein |
| `--lock-db-prefix` | Das spezifische db-Präfix zur Vermeidung von Sperrkonflikten bei der Verwendung von `db` Sperranbieter.<br><br>Der Standardwert: `NULL` | Nein |
| `--lock-zookeeper-host` | Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster bei Verwendung von `zookeeper` Sperranbieter.<br><br>Beispiel: `127.0.0.1:2181` | Ja, wenn Sie `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Der Pfad, in dem Zookeeper Sperren speichert.<br><br>Der Standardpfad lautet: `/magento/locks` | Nein |
| `--lock-file-path` | Der Pfad, in dem Dateisperren gespeichert werden. | Ja, wenn Sie `--lock-provider=file` |

**Konfigurationsoptionen für Verbraucher:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Informationen zum Aktivieren oder Deaktivieren von Modulen nach der Installation des Programms finden Sie unter [Module aktivieren und deaktivieren](manage-modules.md).

**Sensible Daten:**

{{$include /help/_includes/sensitive-data.md}}

### Beispiele für lokale Host-Installationen

Die folgenden Beispiele zeigen die Befehle zur lokalen Installation von Adobe Commerce mit verschiedenen Optionen.

#### Beispiel 1: Grundlegende Installation mit einem Administratorkonto

Im folgenden Beispiel wird die Anwendung mit den folgenden Optionen installiert:

* Das Programm wird im `magento2` Verzeichnis relativ zum Basisverzeichnis des Webservers `localhost` und der Pfad zum Admin lautet `admin`; daher:

  Ihre Storefront-URL lautet: `http://127.0.0.1`

* Der Datenbankserver befindet sich auf demselben Host wie der Webserver.

  Der Datenbankname lautet `magento`und Benutzername und Kennwort beide `magento`

* Verwendet Server-Neuschreibungen

* Der Administrator verfügt über die folgenden Eigenschaften:

   * Vor- und Nachnamen sind `Commerce User`
   * Benutzername ist `admin` und das Kennwort lautet `admin123`
   * E-Mail-Adresse ist `user@example.com`

* Standardsprache ist `en_US` (Englisch in den USA)
* Die Standardwährung ist US-Dollar.
* Die standardmäßige Zeitzone ist US Central (Amerika/Chicago).
* Elasticsearch 7 ist auf installiert. `es-host.example.com` und Verbindungen an Port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Meldungen, die der folgenden Anzeige ähneln, zeigen eine erfolgreiche Installation an:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Beispiel 2: Grundlegende Installation ohne Administratorkonto

Sie können die Anwendung installieren, ohne den Administrator-Benutzer zu erstellen, wie im folgenden Beispiel gezeigt.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Meldungen wie die folgende werden bei erfolgreicher Installation angezeigt:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Nach der Installation können Sie einen Administrator mithilfe der `admin:user:create` command:
[Erstellen oder Bearbeiten von Administratoren](admin.md#create-or-edit-an-administrator)

#### Beispiel 3: Installation mit zusätzlichen Optionen

Im folgenden Beispiel wird die Anwendung mit den folgenden Optionen installiert:

* Die Magapplication wird im `magento2` Verzeichnis relativ zum Basisverzeichnis des Webservers `localhost` und der Pfad zum Admin lautet `admin`; daher:

  Ihre Storefront-URL lautet: `http://127.0.0.1`

* Der Datenbankserver befindet sich auf demselben Host wie der Webserver.

  Der Datenbankname lautet `magento`und Benutzername und Kennwort beide `magento`

* Der Administrator verfügt über die folgenden Eigenschaften:

   * Vor- und Nachnamen sind `Commerce User`
   * Benutzername ist `admin` und das Kennwort lautet `admin123`
   * E-Mail-Adresse ist `user@example.com`

* Standardsprache ist `en_US` (Englisch in den USA)
* Die Standardwährung ist US-Dollar.
* Die standardmäßige Zeitzone ist US Central (Amerika/Chicago).
* Das Installationsprogramm bereinigt zunächst die Datenbank, bevor die Tabellen und das Schema installiert werden
* Sie verwenden eine `ORD$` Inkrementierungspräfix für Verkaufsaufträge (da es ein Sonderzeichen enthält) [`$`], muss der Wert in doppelte Anführungszeichen gesetzt werden.)
* Sitzungsdaten werden in der Datenbank gespeichert
* Verwendet Server-Neuschreibungen
* Elasticsearch 7 ist auf installiert. `es-host.example.com` und Verbindungen an Port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>Sie müssen den Befehl entweder in einer einzigen Zeile oder, wie im obigen Beispiel, in einem `\` am Ende jeder Zeile.

Meldungen wie die folgende werden bei erfolgreicher Installation angezeigt:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>Wenn Sie über ein Benutzerkonto für den Zugriff auf den Anwendungsserver verfügen, lesen Sie [Setzen Sie einen Umschalter](../next-steps/set-umask.md). Dieser Einrichtungstyp ist typisch für freigegebenes Hosting.
