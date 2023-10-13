---
title: Anwendungsserver für GraphQL-APIs
description: Befolgen Sie diese Anweisungen zum Aktivieren des Anwendungsservers für GraphQL-APIs in Ihrer Adobe Commerce-Bereitstellung.
badgeCoreBeta: label="2.4.7-Beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b7639e8830b2cab971e3e22285d91105b64e9a6e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# Anwendungsserver für GraphQL-APIs

Der Commerce-Anwendungsserver für GraphQL-APIs ermöglicht es Adobe Commerce, den Status unter Commerce GraphQL-API-Anfragen zu erhalten. Der Anwendungsserver, der auf der Open Source-Erweiterung basiert, fungiert als Prozess mit Worker-Threads, die die Anforderungsverarbeitung handhaben. Durch die Beibehaltung eines Bootstrapping-Anwendungszustands zwischen GraphQL-API-Anforderungen verbessert Application Server die Anforderungsverarbeitung und die Gesamtproduktleistung. API-Anfragen werden deutlich effizienter.

Der Anwendungsserver wird nur in Cloud Starter- und lokalen Implementierungen unterstützt. Sie ist nicht für Cloud Pro-Instanzen während der Beta-Phase verfügbar. Sie ist nicht für Magento Open Source-Implementierungen verfügbar.

## Übersicht über die Anwendungsserverarchitektur

Der Anwendungsserver behält den Status zwischen Commerce GraphQL-API-Anfragen bei und macht Bootstrapping nicht mehr erforderlich. Durch die prozessübergreifende Freigabe des Anwendungszustands werden GraphQL-Anforderungen deutlich effizienter, wodurch die Reaktionszeiten um bis zu 30 % verkürzt werden.

Das Share-Nichts PHP Ausführungsmodell stellt aus der Sicht der Latenz eine Herausforderung dar, da jede Anfrage das Bootstrapping des Frameworks erfordert. Dieser Bootstrapping-Prozess umfasst zeitaufwendige Aufgaben wie die Lesekonfiguration, das Einrichten des Bootstrap-Prozesses und das Erstellen von Dienstklassenobjekten.

Die Umstellung der Anforderungsverarbeitungslogik auf eine Ereignisschleife auf Anwendungsebene scheint die Herausforderung zu bewältigen, die Anforderungsverarbeitung auf Unternehmensebene zu optimieren. Dadurch entfällt die Notwendigkeit, das Bootstrapping während des Lebenszyklus der Anforderungsausführung durchzuführen.

## Vorteile der Verwendung des Anwendungsservers

Der Anwendungsserver ermöglicht es Adobe Commerce, den Status zwischen aufeinander folgenden Commerce GraphQL-API-Anfragen aufrechtzuerhalten. Die Freigabe des Anwendungsstatus über Anforderungen hinweg verbessert die Effizienz von API-Anfragen, indem der Verarbeitungsaufwand minimiert und die Anforderungsverarbeitung optimiert wird. Daher kann die Reaktionszeit von GraphQL-Anfragen auf bis zu 30 % reduziert werden.

## Systemanforderungen

Für das Ausführen des Anwendungsservers ist Folgendes erforderlich:

* PHP 8.2 oder höher
* Open Swoole PHP-Erweiterung v22+ installiert
* Angemessener RAM und CPU basierend auf der erwarteten Belastung

## Anwendungsserver für Cloud Starter aktivieren

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert den Anwendungsserver für GraphQL-APIs. Der Anwendungsserver wird nur in lokalen und Cloud Starter-Implementierungen unterstützt. Sie ist nicht für Cloud Pro-Instanzen während der Beta-Phase verfügbar.

### Vor der Implementierung von Cloud Starter

Führen Sie die folgenden Aufgaben vor der Bereitstellung des Anwendungsservers aus:

1. Vergewissern Sie sich, dass Adobe Commerce auf dem Commerce Cloud installiert ist.
1. Vergewissern Sie sich, dass `CRYPT_KEY` Umgebungsvariable für Ihre Instanz festgelegt ist. Sie können den Status dieser Variablen im Cloud Project Portal (Onboarding-Benutzeroberfläche) überprüfen.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Erstellen Sie eine `graphql` Ordner in `project_root` Ordner.
1. Hinzufügen des zusätzlichen benutzerdefinierten `.magento.app.yaml` in der Datei [magento.app.yaml-Dateiinhalt](#magento.app.yaml-file-content) Thema in `project_root/graphql` Ordner.
1. Bearbeiten Sie die `project_root/.magento/routes.yaml` -Datei, die diese Anweisungen enthält:

   ```yaml
   # The routes of the project.
   #
   # Each route describes how an incoming URL is going to be processed.
   
   "http://{default}/":
     type: upstream
     upstream: "mymagento:http"
   
   "http://{default}/graphql":
     type: upstream
     upstream: "graphql:http"
   ```

1. Fügen Sie mit diesem Befehl aktualisierte Dateien zum Git-Index hinzu:

   ```bash
   git add -f php.ini graphql/.magento.app.yaml .magento/routes.yaml swoole.so
   ```

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Bereitstellen des Anwendungsservers auf Cloud Starter

Stellen Sie nach dem Ausführen der erforderlichen Aufgaben den Anwendungsserver mithilfe dieses Befehls bereit:

```bash
git push
```

### Überprüfung der Aktivierung des Anwendungsservers in Cloud Starter

1. Öffnen Sie die Benutzeroberfläche Ihres Cloud-Projekts. Sie sollten einen zusätzlichen SSH-Zugriffspunkt für die `graphql` Anwendung.

1. Verwenden Sie SSH, um über den Access Point der grafischen Anwendung auf Ihre Cloud-Instanz zuzugreifen, und führen Sie dann den folgenden Befehl aus:

   ```bash
   ps aux|grep php
   ```

1. Führen Sie eine GraphQL-Abfrage oder -Mutation für Ihre Instanz durch, um zu bestätigen, dass die Variable `graphql` -Endpunkt ist verfügbar. Beispiel:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   Die erwartete Antwort sollte diesem Beispiel ähneln:

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Verwenden Sie SSH, um über den GraphQL-Anwendungs-Zugriffspunkt auf Ihre Cloud-Instanz zuzugreifen. Die `project_root/var/log/magento-server.log` sollte einen neuen Protokolldatensatz für jede GraphQL-Anfrage enthalten.

Wenn diese Überprüfungsschritte erfolgreich sind, können Sie mit der Ausführung des Testzyklus fortfahren.


## Aktivieren von Application Server bei lokalen Bereitstellungen

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert den Anwendungsserver für GraphQL-APIs.

Für das Ausführen des Anwendungsservers sind die Installation der Open Source-Erweiterung und eine geringfügige Änderung der Nginx-Konfigurationsdatei Ihrer Bereitstellung erforderlich, damit dieser Anwendungsserver lokal ausgeführt werden kann.

### Bevor Sie mit der Bereitstellung vor Ort beginnen

Führen Sie diese beiden Aufgaben aus, bevor Sie die `ApplicationServer` -Modul:

* Nginx konfigurieren

* Installieren und Konfigurieren der Open Swoole v22-Erweiterung

### Nginx konfigurieren

Ihre spezifische Commerce-Bereitstellung bestimmt, wie Nginx konfiguriert wird. Im Allgemeinen erhält die Nginx-Konfigurationsdatei standardmäßig den Namen `nginx.conf` und wird in einem dieser Verzeichnisse platziert: `/usr/local/nginx/conf`, `/etc/nginx`oder `/usr/local/etc/nginx`. Siehe [Anfängerhandbuch](https://nginx.org/en/docs/beginners_guide.html) für weitere Informationen zur Konfiguration von Nginx.

Beispiel-Nginx-Konfiguration:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Installieren und Konfigurieren von Open Swoole

Um den Anwendungsserver lokal auszuführen, installieren Sie die Open Swoole v22-Erweiterung. Es gibt mehrere Möglichkeiten, diese Erweiterung zu installieren.

## Anwendungsserver ausführen

Starten Sie den Anwendungsserver:

```bash
bin/magento server:run
```

Dieser Befehl startet einen HTTP-Anschluss auf 9501. Sobald der Anwendungsserver gestartet wird, wird Port 9501 zu einem HTTP-Proxyserver für alle GraphQL-Abfragen.

## Beispiel: Open Swoole (OSX) installieren

Dieses Verfahren zeigt, wie die Open Swoole-Erweiterung auf PHP 8.2 für OSX-basierte Systeme installiert wird. Es ist eine von mehreren Möglichkeiten, die Open Swoole-Erweiterung zu installieren.

### Open Swoole installieren

Geben Sie ein:

```bash
pecl install openswoole-22.0.0
composer require openswoole/core:22.1.1
```

Während der Installation zeigt Adobe Commerce Aufforderungen an, um den Support für `openssl`, `mysqlnd`, `sockets`, `http2`, und `postgres`. Eingabe `yes` für alle Optionen außer `postgres`.

### Installation von Open Swoole bestätigen

Ausführen `php -m | grep openswoole` , um zu bestätigen, dass die Erweiterung erfolgreich aktiviert wurde.

### Häufige Fehler bei der Open Swoole-Installation

Fehler, die während der Open Swoolinstallation auftreten, treten normalerweise während der `pecl` Installationsphase. Typische Fehler beinhalten fehlende `openssl.h` und `pcre2.h` -Dateien. Um diese Fehler zu beheben, stellen Sie sicher, dass diese beiden Pakete in Ihrem lokalen System installiert sind.

* Überprüfen Sie den Speicherort von `openssl` durch Ausführen:

```bash
openssl version -d
```

Dieser Befehl zeigt den Pfad, in dem `openssl` installiert ist.

* Überprüfen Sie den Speicherort von `pcre2` durch Ausführen:

```bash
pcre2-config --prefix 
```

Verwenden Sie Homebrew, um die fehlenden Pakete zu installieren, wenn die Befehlsausgabe anzeigt, dass Dateien fehlen:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Beheben von Problemen mit openssl

Beheben von Problemen im Zusammenhang mit `openssl`, führen Sie aus:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Vergewissern Sie sich, dass Sie den Pfad aus Ihrer lokalen `dev` Umgebung.

#### Validierung der Lösung von Problemen im Zusammenhang mit Öffnungen

Sie können den folgenden Befehl erneut ausführen, um zu überprüfen, ob Probleme im Zusammenhang mit &quot;openssl&quot;behoben wurden:

```bash
pecl install openswoole-22.0.0
```

#### Beheben von Problemen mit pcre2.h

Beheben von Problemen im Zusammenhang mit `pcre2.h`, verknüpfen Sie die `pcre2.h` Pfad zu Ihrem installierten PHP-Erweiterungsverzeichnis. Ihre spezifische installierte Version von PHP und `pcr2.h` bestimmt die jeweilige Version des Befehls, den Sie verwenden sollten.

### Überprüfen, ob der Anwendungsserver ausgeführt wird

Führen Sie den folgenden Befehl aus, um sicherzustellen, dass der Anwendungsserver in Ihrer Bereitstellung ausgeführt wird:

```bash
ps aux | grep php
```

Zu den weiteren Möglichkeiten, um zu überprüfen, ob der Anwendungsserver ausgeführt wird, gehören:

* Überprüfen Sie die `/var/log/magento-server.log` -Datei für Einträge, die sich auf verarbeitete GraphQL-Anforderungen beziehen.
* Versuchen Sie, eine Verbindung zum HTTP-Anschluss herzustellen, an dem der Anwendungsserver ausgeführt wird. Beispiel: `curl -g 'http://localhost:9501/graph`.

### Vergewissern Sie sich, dass GraphQL-Anforderungen von Application Server verarbeitet werden

Der Anwendungsserver fügt die `X-Backend` Antwortheader mit dem Wert `graphql_server` für jede Anfrage, die verarbeitet wird. Um zu überprüfen, ob eine Anfrage vom Anwendungsserver verarbeitet wurde, suchen Sie nach diesem Antwortheader.

### Überprüfen der Kompatibilität von Erweiterung und Anpassung mit dem Anwendungsserver

Entwickler und Händler von Erweiterungen sollten zunächst überprüfen, ob ihr Erweiterungs- und Anpassungscode den technischen Richtlinien entspricht, die unter [Technische Leitlinien](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Beachten Sie diese Richtlinien bei der Code-Bewertung:

* Dienstklassen (d. h. Klassen, die Verhalten, aber keine Daten bereitstellen, z. B. `EventManager`) sollte keinen veränderlichen Status aufweisen.
* Vermeiden Sie eine zeitliche Kopplung.

## Anwendungsserver deaktivieren

Die Verfahren zum Deaktivieren des Anwendungsservers hängen davon ab, ob der Server in einer lokalen oder Cloud-Bereitstellung ausgeführt wird.

### Anwendungsserver in Cloud Starter deaktivieren

1. Entfernen Sie alle neuen Dateien und alle anderen Codeänderungen, die im `AppServer Enabled` während Ihrer Bereitstellungsvorbereitungen.

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Stellen Sie diese Änderungen mit diesem Befehl bereit:

   ```bash
   git push
   ```

### Anwendungsserver deaktivieren

1. Kommentieren Sie die `/graphql` Abschnitt `nginx.conf` -Datei, die Sie beim Aktivieren von Application Server hinzugefügt haben.
1. Starten Sie nginx neu.

Diese Methode zum Deaktivieren des Anwendungsservers kann nützlich sein, um die Leistung schnell zu testen oder zu vergleichen.

### Vergewissern Sie sich, dass der Anwendungsserver deaktiviert ist.

So bestätigen Sie, dass GraphQL-Anforderungen von `php-fpm` Geben Sie anstelle des Anwendungsservers folgenden Befehl ein: `ps aux | grep php`.

Nachdem der Anwendungsserver deaktiviert wurde:

* `bin/magento server:run` ist inaktiv.
* `var/log/magento-server.log` enthält keine Einträge nach GraphQL-Anforderungen.

## Integration und Funktionstests für PHP Application Server

Erweiterungsentwickler können zwei Integrationstests ausführen, um die Kompatibilität der Erweiterung mit dem Anwendungsserver zu überprüfen: `GraphQlStateTest` und `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` erkennt Status in freigegebenen Objekten, die nicht für mehrere Anforderungen wiederverwendet werden sollen.

Dieser Test dient der Erkennung von Statusänderungen in Dienstobjekten, die von der `ObjectManager`. Der Test führt identische GraphQL-Abfragen zweimal aus und vergleicht den Dienstobjektstatus vor und nach der zweiten Abfrage. 

#### GraphQlStateTest-Fehler und potenzielle Behebung

* **Liste kann nicht hinzugefügt, übersprungen oder gefiltert werden**. Wenn ein Fehler auftritt, der darauf hindeutet, dass es nicht sicher ist, eine Liste hinzuzufügen, zu überspringen oder zu filtern, sollten Sie überlegen, ob die Klasse auf abwärtskompatible Weise umgestaltet werden kann, um die Fabriken der Dienstklassen mit veränderlichem Status zu verwenden.

* **Klasse weist einen veränderlichen Status auf**. Wenn die Klasse selbst einen veränderlichen Status aufweist, versuchen Sie, Ihren Code neu zu schreiben, um diesen Status zu umgehen. Wenn der veränderliche Status aus Leistungsgründen erforderlich ist, implementieren Sie `ResetAfterRequestInterface` und Verwendung `_resetState()` , um das Objekt auf seinen ursprünglichen konstruierten Status zurückzusetzen.

* **Der Zugriff auf die eingegebene Eigenschaft $x darf nicht vor der Initialisierungsmeldung erfolgen**. Fehler mit diesem Nachrichtentyp weisen darauf hin, dass die angegebene Eigenschaft nicht vom Konstruktor initialisiert wurde. Dies ist eine Form der zeitlichen Kopplung, die auftritt, da das Objekt nach der anfänglichen Konstruktion nicht mehr verwendet werden kann. Diese Kopplung tritt auch dann auf, wenn die Eigenschaft privat ist, da der Collector, der die Daten aus den Eigenschaften abruft, die PHP Reflektionsfunktion verwendet. Versuchen Sie in diesem Fall, die Klasse zu refaktorieren, um eine zeitliche Kopplung zu vermeiden und einen veränderlichen Status zu vermeiden. Wenn diese Refaktorierung den Fehler nicht behebt, können Sie den Eigenschaftstyp in einen nullbaren Typ ändern, damit er auf null initialisiert werden kann.  Wenn die Eigenschaft ein Array ist, versuchen Sie, die Eigenschaft als leeres Array zu initialisieren.

Ausführen `GraphQlStateTest` durch Ausführung `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` sucht nach allen Klassen, die `ResetAfterRequestInterface` und überprüft, ob die `_resetState()` -Methode gibt den Status eines Objekts in dem Status zurück, den es nach der Erstellung durch `ObjectManager`.  Dieser Test erstellt ein Dienstobjekt mit `ObjectManager`, dann klonen Sie dieses Objekt, ruft `_resetState()`und vergleicht dann beide Objekte. Der Test ruft zwischen der Objektinstanziierung und `_resetState()`, sodass das Zurücksetzen eines veränderlichen Status nicht bestätigt wird. Es gibt Probleme, bei denen ein Fehler oder Typo in `_resetState()` kann den Status auf etwas Anderes festlegen als ursprünglich.

#### ResetAfterRequestTest-Fehler und potenzielle Behebung

* **Klasse hat inkonsistente Eigenschaftswerte**. Wenn dieser Test fehlschlägt, überprüfen Sie, ob eine Klasse mit dem Ergebnis geändert wurde, dass das Objekt nach der Erstellung andere Eigenschaftswerte aufweist als nach der `_resetState()` -Methode aufgerufen wird. Wenn die Klasse, an der Sie arbeiten, die `_resetState()` -Methode an und überprüfen Sie dann die Klassenhierarchie auf eine Superklasse, die sie implementiert.

* **Der Zugriff auf die eingegebene Eigenschaft $x darf nicht vor der Initialisierungsmeldung erfolgen**. Dieses Problem tritt auch bei `GraphQlStateTest`.
 
Ausführen `ResetAfterRequestTest` durch Ausführung: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Funktionstests

Entwickler von Erweiterungen sollten bei der Bereitstellung des Anwendungsservers WebAPI-Funktionstests für GraphQL sowie benutzerdefinierte automatisierte oder manuelle Funktionstests für GraphQL durchführen. Mithilfe dieser Funktionstests können Entwickler potenzielle Fehler oder Kompatibilitätsprobleme erkennen.

## magento.app.yaml-Dateiinhalt

Siehe [Vor der Implementierung von Cloud Starter](#Before-you-begin-a-Cloud-Starter-deployment) Anweisungen zum Hinzufügen des folgenden Codes zu Ihrem `project_root/graphql` Ordner.

```yaml
name: graphql
# The toolstack used to build the application.
type: php:8.2
build:
    flavor: none
 
source:
    root: /
dependencies:
    php:
        composer/composer: '2.5.5'
 
# Enable extensions required by Magento 2
runtime:
    extensions:
        - xsl
        - sodium
 
# The relationships of the application with services or other applications.
# The left-hand side is the name of the relationship as it will be exposed
# to the application in the environment variable. The right-hand
# side is in the form `<service name>:<endpoint name>`.
relationships:
    database: "mysql:mysql"
    redis: "redis:redis"
    opensearch: "opensearch:opensearch"
 
# The configuration of app when it is exposed to the web.
web:
    commands:
        start: "php -dopcache.enable_cli=1 -dopcache.validate_timestamps=0 bin/magento server:run -vvv  --port=${PORT:-80} > ${MAGENTO_CLOUD_APP_DIR}/var/log/magento-server.log 2>&1"
    upstream:
        socket_family: tcp
        protocol: http
    locations:
        '/':
            root: "pub"
            passthru: true
 
# The size of the persistent disk of the application (in MB).
disk: 5120
 
# The mounts that will be performed when the package is deployed.
mounts:
    "var": "shared:files/var"
    "app/etc": "shared:files/etc"
    "pub/media": "shared:files/media"
    "pub/static": "shared:files/static"
 
hooks:
    # We run build hooks before your application has been packaged.
    build: |
        set -e
        composer install
        php ./vendor/bin/ece-tools run scenario/build/generate.xml
        php ./vendor/bin/ece-tools run scenario/build/transfer.xml
    # We run deploy hook after your application has been deployed and started.
    deploy: |
        php ./vendor/bin/ece-tools run scenario/deploy.xml
    # We run post deploy hook to clean and warm the cache. Available with ECE-Tools 2002.0.10.
    post_deploy: |
        php ./vendor/bin/ece-tools run scenario/post-deploy.xml
```
