---
title: Installieren von Adobe Commerce
description: Führen Sie die folgenden Schritte aus, um Adobe Commerce auf der von Ihnen verwalteten Infrastruktur zu installieren.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 47525e8d8379061b254bfa90ab46e27a1ee2f524
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 0%

---

# Installieren von Adobe Commerce

Bevor Sie beginnen, führen Sie die folgenden Schritte aus:

* Stellen Sie sicher, dass Ihr System die unter (Systemanforderungen[&#x200B; beschriebenen Anforderungen &#x200B;](../system-requirements.md).

* Alle ([) Aufgaben &#x200B;](../prerequisites/overview.md).

* Führen Sie die ersten Installationsschritte aus. Siehe [Ihr Installations- oder Aktualisierungspfad](../overview.md).

* Wechseln Sie nach der Anmeldung beim Anwendungsserver [zum Dateisystembesitzer](../prerequisites/file-system/overview.md).

* Lesen Sie [&#x200B; Übersicht über „Erste Schritte mit der Befehlszeileninstallation](../composer.md).

>[!NOTE]
>
>Sie müssen die Anwendung über ihr `bin`-Unterverzeichnis installieren.

Sie können das Installationsprogramm mehrmals mit verschiedenen Optionen ausführen, um Installationsaufgaben wie die folgenden durchzuführen:

* Die Installation erfolgt in Phasen. Nachdem Sie beispielsweise Ihren Webserver für SSL (Secure Sockets Layer) konfiguriert haben, können Sie das Installationsprogramm erneut ausführen, um SSL-Optionen festzulegen.

* Fehler in früheren Installationen korrigieren.

* Installieren Sie die Anwendung in einer anderen Datenbankinstanz.

>[!NOTE]
>
>Standardmäßig überschreibt das Installationsprogramm die Datenbank nicht, wenn Sie die Commerce-Software in derselben Datenbankinstanz installieren. Mit dem optionalen `cleanup-database` können Sie dieses Verhalten ändern.

Siehe auch [Aktualisieren, Neu installieren, Deinstallieren](uninstall.md).

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Hilfe-Befehle des Installationsprogramms

Sie können die folgenden Befehle ausführen, um Werte für einige erforderliche Argumente zu finden:

| Installer-Argument | Befehl |
| ------------------ | ------------------------------- |
| Sprache | `magento info:language:list` |
| Währung | `magento info:currency:list` |
| Zeitzone | `magento info:timezone:list` |

>[!NOTE]
>
>Wenn bei der Ausführung dieser Befehle ein Fehler angezeigt wird, stellen Sie sicher, dass Sie die Installationsabhängigkeiten aktualisiert haben, wie unter [Aktualisieren von Installationsabhängigkeiten](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/) beschrieben.

## Installieren über die Befehlszeile

Der Installationsbefehl verwendet das folgende Format:

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

In den folgenden Tabellen werden die Namen und Werte der Installationsoptionen, z. B. Installationsbefehle, beschrieben. Siehe [Beispiel für localhost-Installationen](#sample-localhost-installations).

>[!NOTE]
>
>Optionen, die Leerzeichen oder Sonderzeichen enthalten, müssen entweder in einfachen oder doppelten Anführungszeichen gesetzt werden.

**Admin-Anmeldedaten:**

Die folgenden Optionen geben die Benutzerinformationen und Anmeldeinformationen für den Admin-Benutzer an.

In Adobe Commerce Version 2.2.8 und höher können Sie den Admin-Benutzer während oder nach der Installation erstellen. Wenn Sie den Benutzer während der Installation erstellen, sind alle Variablen mit Administratorberechtigungen erforderlich. Siehe [Beispiel für localhost-Installationen](#sample-localhost-installations).

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--admin-firstname` | Vorname des Admin-Benutzers. | Ja |
| `--admin-lastname` | Nachname des Administrator-Benutzers. | Ja |
| `--admin-email` | E-Mail-Adresse des Administrator-Benutzers. | Ja |
| `--admin-user` | Benutzername des Administrators. | Ja |
| `--admin-password` | Administratorkennwort Das Kennwort muss mindestens 7 Zeichen lang sein und mindestens ein alphabetisches und mindestens ein numerisches Zeichen enthalten. Wir empfehlen ein längeres, komplexeres Kennwort. Schließen Sie die gesamte Kennwortzeichenfolge in einfachen Anführungszeichen ein. Beispiel: `--admin-password='A0b9%t3g'` | Ja |

**Site- und Datenbankkonfigurationsoptionen:**

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--base-url` | Basis-URL für den Zugriff auf Ihre Admin- und Storefront in einem der folgenden Formate:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Hinweis:** Das Schema (http:// oder https://) und ein Schrägstrich am Ende sind beide erforderlich.<br><br>`<your install dir>` ist der docroot-relative Pfad, in dem die Anwendung installiert werden soll. Je nachdem, wie Sie Ihren Webserver und die virtuellen Hosts einrichten, kann der Pfad Magento2 oder leer sein.<br><br>Um auf die Anwendung auf localhost zuzugreifen, können Sie entweder `http://127.0.0.1/<your install dir>/` oder `http://127.0.0.1/<your install dir>/` verwenden.<br><br> - `{{base_url}}`, die eine Basis-URL darstellt, die durch eine Virtual-Host-Einstellung oder eine Virtualisierungsumgebung wie Docker definiert ist. Wenn Sie beispielsweise einen virtuellen Host mit dem Host-Namen commerce.example.com einrichten, können Sie die Anwendung mit `--base-url={{base_url}}` installieren und mit einer URL wie `http://commerce.example.com/admin` auf den Admin zugreifen. | Ja |
| `--backend-frontname` | URI (Uniform Resource Identifier) für den Zugriff auf den Administrator. Sie können diesen Parameter auslassen, damit die Anwendung einen zufälligen URI mit dem folgenden Muster generiert <code>admin_jkhgdfq</code>.<br><br>Aus Sicherheitsgründen wird ein zufälliger URI empfohlen. Ein zufälliger URI ist für Hacker oder bösartige Software schwieriger auszunutzen.<br><br>Der URI wird am Ende der Installation angezeigt. Sie können ihn jederzeit mithilfe des Befehls `magento info:adminuri` anzeigen.<br><br>Wenn Sie einen Wert eingeben möchten, empfehlen wir, kein gängiges Wort wie „admin“ oder „backend“ zu verwenden. Der Admin-URI kann nur alphanumerische Werte und den Unterstrich (`_`) enthalten. | Nein |
| `--db-host` | Verwenden Sie eine der folgenden Optionen:<br><br>- Der voll qualifizierte Hostname oder die IP-Adresse des Datenbankservers.<br><br>- `localhost` (Standard) oder `127.0.0.1`, wenn sich Ihr Datenbankserver auf demselben Host wie Ihr Webserver befindet.localhost bedeutet, dass die MySQL-Client-Bibliothek UNIX-Sockets verwendet, um eine Verbindung zur Datenbank herzustellen. `127.0.0.1` verwendet die Client-Bibliothek das TCP-Protokoll. Weitere Informationen zu Sockets finden Sie in der [PHP PDO_MYSQL-Dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Hinweis:** Sie können optional den Datenbank-Server-Port in seinem Hostnamen wie www.example.com angeben:9000 | Ja |
| `--db-name` | Name der Datenbankinstanz, in der die Datenbanktabellen installiert werden sollen.<br><br>Der Standardwert ist `magento2`. | Ja |
| `--db-user` | Benutzername des Inhabers der Datenbankinstanz.<br><br>Der Standardwert ist `root`. | Ja |
| `--db-password` | Kennwort des Besitzers der Datenbankinstanz. | Ja |
| `--db-prefix` | Verwenden Sie diese Option nur, wenn Sie die Datenbanktabellen in einer Datenbankinstanz installieren, in der bereits Adobe Commerce-Tabellen vorhanden sind.<br><br>Verwenden Sie in diesem Fall ein Präfix, um die Tabellen für diese Installation zu identifizieren. Bei einigen Kunden wird mehr als eine Adobe Commerce-Instanz auf einem Server ausgeführt, wobei alle Tabellen in derselben Datenbank vorhanden sind.<br><br>Das Präfix darf maximal fünf Zeichen lang sein. Sie muss mit einem Buchstaben beginnen und darf nur Buchstaben, Zahlen und Unterstriche enthalten.<br><br>Mit dieser Option können diese Kunden den Datenbank-Server für mehr als eine Installation freigeben. | Nein |
| `--db-ssl-key` | Pfad zum Clientschlüssel. | Nein |
| `--db-ssl-cert` | Pfad zum Client-Zertifikat. | Nein |
| `--db-ssl-ca` | Pfad zum Serverzertifikat. | Nein |
| `--language` | Sprach-Code, der in der Admin- und Storefront verwendet werden soll. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Sprach-Codes anzeigen, indem Sie `magento info:language:list` aus dem Verzeichnis bin eingeben.) | Nein |
| `--currency` | Standardwährung für die Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Währungen anzeigen, indem Sie `magento info:currency:list` aus dem Verzeichnis bin eingeben.) | Nein |
| `--timezone` | Standardmäßige Zeitzone für Admin und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Zeitzonen anzeigen, indem Sie `magento info:timezone:list` aus dem Verzeichnis bin eingeben.) | Nein |
| `--use-rewrites` | `1` bedeutet, dass Sie Webserver-Neuschreibungen für generierte Links in der Storefront und in Admin verwenden.<br><br>`0` Deaktiviert die Verwendung von Webserver-Neuschreibungen. Dies ist der Standardwert. | Nein |
| `--use-secure` | `1` ermöglicht die Verwendung von SSL (Secure Sockets Layer) in Storefront-URLs. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` deaktiviert die Verwendung von SSL. In diesem Fall wird davon ausgegangen, dass alle anderen sicheren URL-Optionen ebenfalls 0 sind. Dies ist der Standardwert. | Nein |
| `--base-url-secure` | Sichere Basis-URL für den Zugriff auf Admin und Storefront im folgenden Format: `http[s]://<host or ip>/<your install dir>/` | Nein |
| `--use-secure-admin` | `1` bedeutet, dass Sie SSL verwenden, um auf den Administrator zuzugreifen. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` bedeutet, dass Sie SSL nicht mit dem Administrator verwenden. Dies ist der Standardwert. | Nein |
| `--admin-use-security-key` | 1 Veranlasst die Anwendung, einen zufällig generierten Schlüsselwert zu verwenden, um auf Seiten in Admin und in Formularen zuzugreifen. Diese Schlüsselwerte helfen, Angriffe durch Cross-Site-Script-Forgery zu verhindern. Dies ist der Standardwert.<br><br>`0` Deaktiviert die Verwendung des Schlüssels. | Nein |
| `--session-save` | Verwenden Sie eine der folgenden Optionen:<br><br>- `db`, um Sitzungsdaten in der Datenbank zu speichern. Wählen Sie Datenbankspeicher, wenn Sie eine geclusterte Datenbank haben. Andernfalls gibt es möglicherweise keinen großen Vorteil gegenüber dateibasiertem Speicher.<br><br> - `files`, Sitzungsdaten im Dateisystem zu speichern. Die dateibasierte Sitzungsspeicherung ist geeignet, es sei denn, der Dateisystemzugriff ist langsam, Sie verfügen über eine geclusterte Datenbank oder Sie möchten Sitzungsdaten in Redis speichern.<br><br> - `redis` zum Speichern von Sitzungsdaten in Redis. Wenn Sie Redis für das Standard- oder Seiten-Caching verwenden, muss Redis bereits installiert sein. Weitere Informationen zum Konfigurieren der Unterstützung für Redis finden Sie unter Verwenden von Redis für den Sitzungsspeicher . | Nein |
| `--key` | Wenn Sie über einen verfügen, geben Sie einen Schlüssel zum Verschlüsseln sensibler Daten in der Datenbank an. Wenn Sie noch keinen haben, generiert das Programm einen für Sie. | Ja |
| `--cleanup-database` | Um Datenbanktabellen vor der Installation der Anwendung abzulegen, geben Sie diesen Parameter ohne Wert an. Andernfalls bleibt die Datenbank intakt. | Nein |
| `--db-init-statements` | Erweiterter MySQL-Konfigurationsparameter. Verwendet Anweisungen zur Datenbankinitialisierung, die beim Herstellen einer Verbindung mit der MySQL-Datenbank ausgeführt werden. Konsultieren Sie eine Referenz wie diese, bevor Sie Werte festlegen.<br><br>Der Standardwert ist `SET NAMES utf8;`. | Nein |
| `--sales-order-increment-prefix` | Geben Sie einen Zeichenfolgenwert an, der als Präfix für Kundenaufträge verwendet werden soll. In der Regel wird dies verwendet, um eindeutige Bestellnummern für Zahlungsverarbeiter zu garantieren. | Nein |

>[!TIP]
>
>Informationen zum Aktivieren von Remote-Speicherdiensten während der Installation finden Sie [Konfigurieren von Remote](../../configuration/remote-storage/remote-storage.md) im _Konfigurationshandbuch_.

**Konfigurationsoptionen für Suchmaschinen:**

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--search-engine` | Die Version der Suchmaschine. Mögliche Werte sind `elasticsearch7`, `elasticsearch6` und `elasticsearch5`. Der Standardwert lautet `elasticsearch7`. Wenn Sie OpenSearch als Suchmaschine installiert haben, geben Sie den Wert `elasticsearch7` an. Elasticsearch 5 ist veraltet und wird nicht empfohlen. | Nein |
| `--elasticsearch-host` | Der Host-Name oder die IP-Adresse, auf dem/der die Suchmaschine läuft. Der Standardwert lautet `localhost`. | Nein |
| `--elasticsearch-port` | Der Port für eingehende HTTP-Anfragen. Der Standardwert lautet `9200`. | Nein |
| `--elasticsearch-index-prefix` | Ein Präfix, das den Suchindex identifiziert. Der Standardwert lautet `magento2`. | Nein |
| `--elasticsearch-timeout` | Die Anzahl der Sekunden, nach denen das System eine Zeitüberschreitung aufweist. Der Standardwert lautet `15`. | Nein |
| `--elasticsearch-enable-auth` | Aktiviert die Authentifizierung auf dem Suchmaschinenserver. Der Standardwert lautet `false`. | Nein |
| `--elasticsearch-username` | Die zu authentifizierende Benutzer-ID | Nein, außer die Authentifizierung ist aktiviert |
| `--elasticsearch-password` | Das zu authentifizierende Kennwort | Nein, außer die Authentifizierung ist aktiviert |

**[!DNL RabbitMQ]Konfigurationsoptionen:**

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--amqp-host` | Verwenden Sie die `--amqp` nur, wenn Sie bereits eine Installation von [!DNL RabbitMQ] eingerichtet haben. Weitere Informationen [!DNL RabbitMQ] Installieren und Konfigurieren von [!DNL RabbitMQ] finden Sie unter Installation .<br><br>Der Hostname, auf dem [!DNL RabbitMQ] installiert ist. | Nein |
| `--amqp-port` | Der Port, über den eine Verbindung zu [!DNL RabbitMQ] hergestellt wird. Der Standardwert lautet 5672. | Nein |
| `--amqp-user` | Der Benutzername für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht die standardmäßige `guest`. | Nein |
| `--amqp-password` | Das Kennwort für die Verbindung mit [!DNL RabbitMQ]. Verwenden Sie nicht die `guest` Standardkennwort. | Nein |
| `--amqp-virtualhost` | Der virtuelle Host für die Verbindung mit [!DNL RabbitMQ]. Der Standardwert lautet `/`. | Nein |
| `--amqp-ssl` | Gibt an, ob eine Verbindung zu [!DNL RabbitMQ] hergestellt werden soll. Der Standardwert lautet `false`. Siehe [!DNL RabbitMQ] für Informationen zum Einrichten von SSL für [!DNL RabbitMQ]. | Nein |
| `--consumers-wait-for-messages` | Sollen Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein | Nein |

**ActiveMQ Artemis-Konfigurationsoptionen:**

>[!NOTE]
>
>ActiveMQ Artemis wurde in Adobe Commerce 2.4.6 und höheren Versionen eingeführt.

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--stomp-host` | Verwenden Sie die `--stomp` nur, wenn Sie bereits eine Installation von ActiveMQ Artemis eingerichtet haben. Weitere Informationen zum Installieren und Konfigurieren von ActiveMQ Artemis finden Sie unter ActiveMQ Artemis-Installation .<br><br>Der Hostname, auf dem ActiveMQ Artemis installiert ist. | Nein |
| `--stomp-port` | Der Port, der für die Verbindung mit ActiveMQ Artemis verwendet werden soll. Der Standardwert lautet 61613. | Nein |
| `--stomp-user` | Der Benutzername für die Verbindung mit ActiveMQ Artemis. Verwenden Sie nicht die standardmäßige `artemis`. | Nein |
| `--stomp-password` | Das Passwort für die Verbindung mit ActiveMQ Artemis. Verwenden Sie nicht die `artemis` Standardkennwort. | Nein |
| `--stomp-ssl` | Gibt an, ob eine Verbindung zu ActiveMQ Artemis über SSL hergestellt werden soll. Der Standardwert lautet `false`. Informationen zum Einrichten von SSL für ActiveMQ Artemis finden Sie unter ActiveMQ Artemis . | Nein |
| `--consumers-wait-for-messages` | Sollen Verbraucher auf eine Nachricht aus der Warteschlange warten? 1 - Ja, 0 - Nein | Nein |

**Remote-Speicheroptionen:**

| -Name | Beschreibung | Erforderlich? |
|--- |--- |--- |
| `remote-storage-driver` | Adaptername<br>Mögliche Werte:<br>**file**: Deaktiviert den Remotespeicher und verwendet das lokale Dateisystem <br>**aws-s3**: Verwenden Sie den [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) | Nein |
| `remote-storage-bucket` | Objektspeicher- oder Container-Name | Nein |
| `remote-storage-prefix` | Optionales Präfix (Speicherort innerhalb des Objektspeichers) | Nein |
| `remote-storage-region` | Name der Region | Nein |
| `remote-storage-key` | Optionaler Zugriffsschlüssel | Nein |
| `remote-storage-secret` | Optionaler geheimer Schlüssel | Nein |

**Konfigurationsoptionen sperren:**

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--lock-provider` | Anbieternamen sperren.<br><br>Verfügbare Schlossanbieter: `db`, `zookeeper`, `file`.<br><br>Der standardmäßige Sperranbieter: `db` | Nein |
| `--lock-db-prefix` | Das spezifische DB-Präfix, um Sperrkonflikte bei der Verwendung `db` Sperranbieters zu vermeiden.<br><br>Der Standardwert: `NULL` | Nein |
| `--lock-zookeeper-host` | Host und Port für die Verbindung mit dem ZooKeeper-Cluster bei Verwendung `zookeeper` Sperranbieters.<br><br>Beispiel: `127.0.0.1:2181` | Ja, wenn Sie `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Der Pfad, in dem ZooKeeper Sperren speichert.<br><br>Der Standardpfad lautet: `/magento/locks` | Nein |
| `--lock-file-path` | Der Pfad, in dem Dateisperren gespeichert werden. | Ja, wenn Sie `--lock-provider=file` |

**Konfigurationsoptionen für Verbraucher:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Informationen zum Aktivieren oder Deaktivieren von Modulen nach der Installation der Anwendung finden Sie unter [Module aktivieren und deaktivieren](manage-modules.md).

**Sensible Daten:**

{{$include /help/_includes/sensitive-data.md}}

### Beispiele für localhost-Installationen

Die folgenden Beispiele zeigen die Befehle zum lokalen Installieren von Adobe Commerce mit verschiedenen Optionen.

#### Beispiel 1: Einfache Installation mit Administrator-Benutzerkonto

Im folgenden Beispiel wird die Anwendung mit den folgenden Optionen installiert:

* Die Anwendung wird im `magento2`-Verzeichnis relativ zum Webserver-Stammverzeichnis auf `localhost` installiert und der Pfad zum Admin wird `admin`. Daher:

  Ihre Storefront-URL ist `http://127.0.0.1`

* Der Datenbankserver befindet sich auf demselben Host wie der Webserver.

  Der Datenbankname ist `magento` und der Benutzername und das Kennwort sind beide `magento`

* Verwendet Server-Neuschreibungen

* Der Administrator verfügt über die folgenden Eigenschaften:

   * Vor- und Nachnamen sind `Commerce User`
   * Benutzername ist `admin` und das Kennwort `admin123`
   * E-Mail-Adresse ist `user@example.com`

* Die Standardsprache ist `en_US` (Englisch (USA))
* Die Standardwährung ist US-Dollar
* Die standardmäßige Zeitzone ist US Central (America/Chicago)
* Elasticsearch 7 ist auf `es-host.example.com` installiert und verbindet sich mit Port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Meldungen ähnlich der folgenden werden angezeigt, um eine erfolgreiche Installation anzuzeigen:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Beispiel 2: Standardinstallation ohne Administratorkonto

Sie können die Anwendung installieren, ohne den Administrator-Benutzer zu erstellen, wie im folgenden Beispiel gezeigt.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Meldungen wie die folgende werden angezeigt, wenn die Installation erfolgreich war:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Nach der Installation können Sie mit dem Befehl `admin:user:create` einen Admin-Benutzer erstellen:
[Erstellen oder Bearbeiten eines Administrators](admin.md#create-or-edit-an-administrator)

#### Beispiel 3: Installation mit zusätzlichen Optionen

Im folgenden Beispiel wird die Anwendung mit den folgenden Optionen installiert:

* Die Anwendung Maga wird im `magento2`-Verzeichnis relativ zum Webserver-Basisverzeichnis auf `localhost` installiert. Der Pfad zum Administrator wird `admin`. Daher:

  Ihre Storefront-URL ist `http://127.0.0.1`

* Der Datenbankserver befindet sich auf demselben Host wie der Webserver.

  Der Datenbankname ist `magento` und der Benutzername und das Kennwort sind beide `magento`

* Der Administrator verfügt über die folgenden Eigenschaften:

   * Vor- und Nachnamen sind `Commerce User`
   * Benutzername ist `admin` und das Kennwort `admin123`
   * E-Mail-Adresse ist `user@example.com`

* Die Standardsprache ist `en_US` (Englisch (USA))
* Die Standardwährung ist US-Dollar
* Die standardmäßige Zeitzone ist US Central (America/Chicago)
* Das Installationsprogramm bereinigt zunächst die Datenbank, bevor die Tabellen und das Schema installiert werden
* Sie verwenden ein Inkrementpräfix für `ORD$` Kundenaufträge (da es ein [`$`] enthält, muss der Wert in doppelte Anführungszeichen gesetzt werden)
* Sitzungsdaten werden in der Datenbank gespeichert
* Verwendet Server-Neuschreibungen
* Elasticsearch 7 ist auf `es-host.example.com` installiert und verbindet sich mit Port 9200

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
>Sie müssen den Befehl entweder in einer einzelnen Zeile oder, wie im vorherigen Beispiel, mit einem `\` am Ende jeder Zeile eingeben.

Meldungen wie die folgende werden angezeigt, wenn die Installation erfolgreich war:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Beispiel 4: Installation mit ActiveMQ Artemis

Das folgende Beispiel zeigt, wie Sie Adobe Commerce mit ActiveMQ Artemis als Nachrichtenbroker installieren:

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>Für die Installation von ActiveMQ Artemis ist Adobe Commerce 2.4.6 oder höher erforderlich.

>[!TIP]
>
>Wenn Sie über ein Benutzerkonto verfügen, um auf den Anwendungsserver zuzugreifen, finden Sie weitere Informationen unter [Einrichten einer Ummaske](../next-steps/set-umask.md). Diese Art der Einrichtung ist typisch für das freigegebene Hosting.

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
