---
title: GraphQL-Anwendungsserver
description: Befolgen Sie diese Anweisungen, um den GraphQL-Anwendungsserver in Ihrer Adobe Commerce-Bereitstellung zu aktivieren.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 2f8396a367cbe1191bdf67aec75bd56f64d3fda8
workflow-type: tm+mt
source-wordcount: '2074'
ht-degree: 0%

---


# GraphQL-Anwendungsserver

Der Commerce GraphQL-Anwendungsserver ermöglicht es Adobe Commerce, den Status zwischen Commerce GraphQL-API-Anfragen beizubehalten. GraphQL Application Server, der auf der Swoole-Erweiterung basiert, fungiert als Prozess mit Worker-Threads, die die Anforderungsverarbeitung verarbeiten. Durch die Beibehaltung des Status eines Bootstrapping-Programms bei GraphQL-API-Anfragen verbessert GraphQL Application Server die Anforderungsverarbeitung und die Gesamtproduktleistung. API-Anfragen werden deutlich effizienter.

Der GraphQL-Anwendungs-Server ist nur für Adobe Commerce verfügbar. Es ist nicht für Magento Open Source verfügbar. Bei Cloud Pro-Projekten müssen Sie [ein Adobe Commerce-Support-Ticket ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide), um den GraphQL-Anwendungsserver zu aktivieren.

>[!NOTE]
>
>Der GraphQL-Anwendungs-Server ist derzeit nicht mit [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/) kompatibel. Adobe Commerce on Cloud Infrastructure-Kunden, die derzeit [!DNL AWS S3] für [Remote-Speicher](../configuration/remote-storage/cloud-support.md) verwenden, können GraphQL Application Server nicht verwenden.

## Architektur

Der GraphQL-Anwendungsserver erhält den Status zwischen Commerce GraphQL-API-Anfragen aufrecht und macht das Bootstrapping überflüssig. Durch die prozessübergreifende Freigabe des Anwendungsstatus werden GraphQL-Anfragen erheblich effizienter und die Antwortzeiten um bis zu 30 % verringert.

Das PHP-Ausführungsmodell stellt aus der Perspektive der Latenz eine Herausforderung dar, da jede Anfrage das Bootstrapping des Frameworks erfordert. Dieser Bootstrapping-Prozess umfasst zeitaufwendige Aufgaben wie das Lesen der Konfiguration, das Einrichten des Bootstrap-Prozesses und das Erstellen von Dienstklassenobjekten.

Die Umstellung der Logik für die Anforderungsverarbeitung auf eine Ereignisschleife auf Anwendungsebene scheint die Herausforderung der Optimierung der Anforderungsverarbeitung auf Unternehmensebene zu bewältigen. Durch diesen Ansatz ist das Bootstrapping während des Lebenszyklus der Anforderungsausführung nicht mehr erforderlich.

## Vorteile

GraphQL Application Server ermöglicht es Adobe Commerce, den Status zwischen aufeinander folgenden Commerce GraphQL-API-Anfragen aufrechtzuerhalten. Durch die anforderungsübergreifende Freigabe des Anwendungsstatus wird die Effizienz von API-Anfragen verbessert, indem der Verarbeitungsaufwand minimiert und die Anfrageverarbeitung optimiert wird. Dadurch kann die Reaktionszeit von GraphQL-Anfragen um bis zu 30 % reduziert werden.

## Systemanforderungen

Die Ausführung von GraphQL Application Server erfordert Folgendes:

* Commerce ab Version 2.4.7
* PHP 8.2 oder höher
* Swoole PHP-Erweiterung v5+ installiert
* Ausreichend RAM und CPU basierend auf der erwarteten Auslastung

## Aktivieren und Bereitstellen in der Cloud-Infrastruktur

Das `ApplicationServer` (`Magento/ApplicationServer/`) ermöglicht den GraphQL-Anwendungsserver.

### Pro Projekte aktivieren

>[!NOTE]
>
>Der Anwendungs-Server ist eine Opt-in-Funktion in Cloud Pro-Instanzen. Um sie zu aktivieren, senden Sie eine Support-Anfrage.

Nachdem die Anwendungsserverfunktion in Ihrem Pro-Projekt aktiviert wurde, führen Sie die folgenden Schritte aus, bevor Sie GraphQL Application Server bereitstellen:

1. Stellen Sie Adobe Commerce mithilfe der Cloud-Vorlage aus der Verzweigung [2.4.7-appserver“ in der Cloud-Infrastruktur ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Stellen Sie sicher, dass alle Commerce-Anpassungen und -Erweiterungen mit [ Anwendungs-](https://developer.adobe.com/commerce/php/development/components/app-server/) von GraphQL kompatibel sind.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Passen Sie die Einstellungen in der Datei &quot;application-server/nginx.conf.sample“ bei Bedarf an.
1. Kommentieren Sie den aktiven „web“-Abschnitt in `project_root/.magento.app.yaml` Datei vollständig aus.
1. Entfernen Sie den Kommentar für die folgende „web“-Abschnittskonfiguration in der `project_root/.magento.app.yaml`-Datei, die den `start`-Befehl des GraphQL-Anwendungsservers enthält.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Stellen Sie sicher, dass `/application-server/start.sh` ausführbar ist, indem Sie den folgenden Befehl ausführen:

   ```bash
   chmod +x application-server/start.sh
   ```

1. Fügen Sie mit diesem Befehl aktualisierte Dateien zum Git-Index hinzu:

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Übergeben Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Pro-Projekte bereitstellen

Pushen Sie nach Abschluss der Aktivierungsschritte Änderungen an Ihr Git-Repository, um den GraphQL-Anwendungsserver bereitzustellen:

```bash
git push
```

### Startprojekte aktivieren

Führen Sie die folgenden Schritte aus, bevor Sie den GraphQL-Anwendungsserver in Startprojekten bereitstellen:

1. Stellen Sie Adobe Commerce mithilfe der Cloud-Vorlage aus der Verzweigung [2.4.7-appserver“ in der Cloud-Infrastruktur ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Stellen Sie sicher, dass alle Commerce-Anpassungen und -Erweiterungen mit GraphQL Application Server kompatibel sind.
1. Vergewissern Sie sich, dass die Umgebungsvariable `CRYPT_KEY` für Ihre Instanz festgelegt ist. Sie können den Status dieser Variablen in der Cloud-Konsole überprüfen.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Benennen Sie `application-server/.magento/.magento.app.yaml.sample` in `application-server/.magento/.magento.app.yaml` um und passen Sie die Einstellungen bei Bedarf in &quot;.magento.app.yaml“ an.
1. Entfernen Sie den Kommentar für die Konfiguration der folgenden Route in der `project_root/.magento/routes.yaml`-Datei, um `/graphql` Traffic an den GraphQL-Anwendungsserver weiterzuleiten.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Fügen Sie aktualisierte Dateien zum Git-Index hinzu:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Übergeben Sie Ihre Änderungen:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Stellen Sie sicher, dass alle benutzerdefinierten Einstellungen in Ihrer Root-`.magento.app.yaml`-Datei ordnungsgemäß in die `application-server/.magento/.magento.app.yaml`-Datei migriert werden. Nachdem die `application-server/.magento/.magento.app.yaml` Datei zu Ihrem Projekt hinzugefügt wurde, sollten Sie sie zusätzlich zur Stammdatei `.magento.app.yaml` beibehalten. Wenn Sie z. B. [den RabbitMQ-Service konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) oder [Web-Eigenschaften verwalten](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) sollten Sie `application-server/.magento/.magento.app.yaml` dieselbe Konfiguration hinzufügen.

### Bereitstellen von Ausgangsprojekten

Pushen Sie nach Abschluss [ Aktivierungsschritte ](#before-you-begin-a-cloud-starter-deployment) Änderungen an Ihr Git-Repository, um den GraphQL-Anwendungsserver bereitzustellen:

```bash
git push
```

### Überprüfen der Aktivierung in Cloud-Projekten

1. Führen Sie eine GraphQL-Abfrage oder Mutation für Ihre Instanz aus, um zu bestätigen, dass auf den `graphql`-Endpunkt zugegriffen werden kann. Beispiel:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   Die erwartete Antwort sollte diesem Beispiel ähneln:

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Verwenden Sie SSH, um auf Ihre Cloud-Instanz zuzugreifen. Die `project_root/var/log/application-server.log` sollte für jede GraphQL-Anfrage einen neuen Protokolldatensatz enthalten.

1. Sie können auch überprüfen, ob der GraphQL-Anwendungsserver ausgeführt wird, indem Sie den folgenden Befehl ausführen:

   ```bash
   ps aux|grep php
   ```

   Es sollte ein `bin/magento server:run` Prozess mit mehreren Threads angezeigt werden.

Wenn diese Überprüfungsschritte erfolgreich sind, wird der GraphQL-Anwendungs-Server ausgeführt und stellt `/graphql`.

## Aktivieren von lokalen Projekten

Das `ApplicationServer`-Modul (`Magento/ApplicationServer/`) ermöglicht GraphQL Application Server für GraphQL-APIs.

Wenn GraphQL Application Server lokal ausgeführt wird, muss die Swoole-Erweiterung installiert und die Nginx-Konfigurationsdatei Ihrer Bereitstellung geringfügig geändert werden.

### Voraussetzungen

Führen Sie die folgenden Schritte aus, bevor Sie das `ApplicationServer` aktivieren:

* Konfigurieren von nginx
* Installieren und Konfigurieren der Swoole v5+-Erweiterung

#### Konfigurieren von nginx

Ihre spezifische Commerce-Bereitstellung bestimmt, wie Nginx konfiguriert wird. Im Allgemeinen heißt die Nginx-Konfigurationsdatei standardmäßig `nginx.conf` und wird in einem der folgenden Verzeichnisse abgelegt: `/usr/local/nginx/conf`, `/etc/nginx` oder `/usr/local/etc/nginx`. Weitere Informationen _[Konfigurieren von Nginx finden ](https://nginx.org/en/docs/beginners_guide.html)_ im „Anfängerhandbuch“.

Nginx-Beispielkonfiguration:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Installieren und Konfigurieren von Swoole

Um den GraphQL-Anwendungsserver lokal auszuführen, installieren Sie die Swoole-Erweiterung (v5.0 oder höher). Es gibt mehrere Möglichkeiten, diese Erweiterung zu installieren.

Das folgende Verfahren beschreibt die Installation der Swoole-Erweiterung für PHP 8.2 auf OSX-basierten Systemen. Dies ist eine von mehreren Möglichkeiten, die Swoole-Erweiterung zu installieren.

```bash
pecl install swoole
```

Während der Installation zeigt Adobe Commerce Eingabeaufforderungen an, um die Unterstützung für `openssl`, `mysqlnd`, `sockets`, `http2` und `postgres` zu aktivieren. Geben Sie `yes` für alle Optionen außer `postgres` ein.

### Überprüfen der Swoole-Installation

Bestätigen Sie, dass die Erweiterung erfolgreich aktiviert wurde:

```bash
php -m | grep swoole
```

### Häufige Fehler bei der Swoole-Installation

Alle Fehler, die während der Swoole-Installation auftreten, treten typischerweise während der `pecl` Installationsphase auf. Typische Fehler sind fehlende `openssl.h` und `pcre2.h`. Um diese Fehler zu beheben, stellen Sie sicher, dass diese beiden Pakete auf Ihrem lokalen System installiert sind.

* Überprüfen Sie den Speicherort von `openssl`, indem Sie Folgendes ausführen:

```bash
openssl version -d
```

Dieser Befehl zeigt den Pfad an, in dem `openssl` installiert ist.

* Überprüfen Sie den Speicherort von `pcre2`, indem Sie Folgendes ausführen:

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

#### Probleme mit OpenSSL beheben

Um Probleme im Zusammenhang mit `openssl` zu beheben, führen Sie Folgendes aus:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Vergewissern Sie sich, dass Sie den Pfad aus Ihrer lokalen `dev` verwenden.

#### Lösung von OpenSSL-bezogenen Problemen bestätigen

Sie können den folgenden Befehl erneut ausführen, um zu überprüfen, ob die OpenSSL-bezogenen Probleme behoben wurden:

```bash
pecl install swoole
```

#### Beheben von Problemen mit pcre2.h

Um Probleme im Zusammenhang mit `pcre2.h` zu beheben, symbolisieren Sie den `pcre2.h` Pfad zu Ihrem installierten PHP-Erweiterungsverzeichnis. Ihre spezifische installierte Version von PHP und `pcr2.h` bestimmt die jeweilige Version des Befehls, den Sie verwenden sollten.

### Ausführen des GraphQL-Anwendungsservers

Starten Sie den GraphQL-Anwendungsserver:

```bash
bin/magento server:run
```

Dieser Befehl startet einen HTTP-Port auf 9501. Sobald der GraphQL-Anwendungs-Server gestartet wird, wird Port 9501 zu einem HTTP-Proxy-Server für alle GraphQL-Abfragen.

So bestätigen Sie, dass der GraphQL-Anwendungs-Server in Ihrer Bereitstellung ausgeführt wird:

```bash
ps aux | grep php
```

Weitere Möglichkeiten, um zu bestätigen, dass der GraphQL-Anwendungsserver ausgeführt wird, sind:

* Überprüfen Sie die `/var/log/application-server.log` auf Einträge, die im Zusammenhang mit verarbeiteten GraphQL-Anfragen stehen.
* Versuchen Sie, eine Verbindung mit dem HTTP-Port herzustellen, über den der GraphQL-Anwendungsserver ausgeführt wird. Beispiel: `curl -g 'http://localhost:9501/graph`.

### Vergewissern Sie sich, dass GraphQL-Anfragen verarbeitet werden

GraphQL Application Server fügt jeder verarbeiteten Anfrage die `X-Backend`-Antwort-Kopfzeile mit dem Wert `graphql_server` hinzu. GraphQL Um zu überprüfen, ob ein Server eine Anfrage verarbeitet hat, überprüfen Sie diese Antwort-Kopfzeile.

### Bestätigen der Kompatibilität von Erweiterungen und Anpassungen

Entwickler und Händler von Erweiterungen sollten zunächst überprüfen, ob ihr Erweiterungs- und Anpassungs-Code den in _[Technische Richtlinien](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_ beschriebenen Richtlinien entspricht.

Beachten Sie diese Richtlinien bei der Code-Auswertung:

* Dienstklassen (d. h. Klassen, die Verhalten, aber keine Daten bereitstellen, z. B. `EventManager`) sollten keinen veränderlichen Status haben.
* Zeitliche Kopplung vermeiden.

## GraphQL-Anwendungsserver deaktivieren

Die Verfahren zum Deaktivieren des GraphQL-Anwendungsservers hängen davon ab, ob der Server in einer lokalen oder in einer Cloud-Bereitstellung ausgeführt wird.

### GraphQL-Anwendungsserver (Cloud) deaktivieren

1. Entfernen Sie alle neuen Dateien und alle anderen Code-Änderungen, die während der Vorbereitungen für die Bereitstellung im `AppServer Enabled`-Commit enthalten waren.

1. Übergeben Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Stellen Sie diese Änderungen mit diesem Befehl bereit:

   ```bash
   git push
   ```

### GraphQL-Anwendungsserver deaktivieren (lokal)

1. Kommentieren Sie den `/graphql` Abschnitt `nginx.conf` Datei aus, die Sie beim Aktivieren des GraphQL-Anwendungsservers hinzugefügt haben.
1. Starten Sie nginx neu.

Diese Methode zum Deaktivieren des GraphQL-Anwendungsservers kann nützlich sein, um die Leistung schnell zu testen oder zu vergleichen.

### Überprüfen, ob der GraphQL-Anwendungsserver deaktiviert ist

Um zu bestätigen, dass `php-fpm` GraphQL-Anfragen anstelle des GraphQL-Anwendungsservers verarbeitet, geben Sie folgenden Befehl ein: `ps aux | grep php`.

Nachdem der GraphQL-Anwendungsserver deaktiviert wurde:

* `bin/magento server:run` ist inaktiv.
* `var/log/application-server.log` enthält nach GraphQL-Anfragen keine Einträge.

## Integrations- und Funktionstests für den GraphQL-Anwendungsserver

Erweiterungsentwickler können zwei Integrationstests ausführen, um die Kompatibilität der Erweiterungen mit dem GraphQL-Anwendungsserver zu überprüfen: `GraphQlStateTest` und `ResetAfterRequestTest`.

### GraphQLstateTest

Der `GraphQlStateTest` erkennt den Status in freigegebenen Objekten, die nicht für mehrere Anfragen wiederverwendet werden sollten.

Dieser Test dient der Erkennung von Statusänderungen in Service-Objekten, die vom `ObjectManager` erzeugt werden. Der Test führt identische GraphQL-Abfragen zweimal aus und vergleicht den Status des Service-Objekts vor und nach der zweiten Abfrage.

#### GraphQLstateTest-Fehler und potenzielle Behebung

* **Liste kann nicht hinzugefügt, übersprungen oder gefiltert**. Wenn beim Hinzufügen, Überspringen oder Filtern einer Liste ein Fehler auftritt, überlegen Sie, ob Sie die Klasse abwärtskompatibel umgestalten können, um die Factories von Dienstklassen mit veränderlichem Status zu verwenden.

* **Klasse weist einen veränderlichen Status auf**. Wenn die Klasse selbst einen veränderlichen Status aufweist, versuchen Sie, den Code neu zu schreiben, um diesen Status zu umgehen. Wenn der veränderliche Status aus Leistungsgründen erforderlich ist, implementieren Sie `ResetAfterRequestInterface` und verwenden Sie `_resetState()` , um das Objekt in den ursprünglichen konstruierten Status zurückzusetzen.

* **Auf die eingegebene Eigenschaft $x darf vor der Initialisierungsmeldung nicht zugegriffen werden**. Fehler bei diesem Nachrichtentyp deuten darauf hin, dass die angegebene Eigenschaft nicht vom Konstruktor initialisiert wurde. Dies ist eine Form der zeitlichen Kopplung, die auftritt, weil das Objekt nach seiner anfänglichen Konstruktion nicht mehr verwendet werden kann. Diese Kopplung erfolgt auch dann, wenn die Eigenschaft privat ist, da der Collector, der die Daten aus den Eigenschaften abruft, die PHP-Reflexionsfunktion verwendet. Versuchen Sie in diesem Fall, die Klasse zu refaktorieren, um eine zeitliche Kopplung und einen veränderlichen Zustand zu vermeiden. Wenn diese Umgestaltung den Fehler nicht behebt, können Sie den Eigenschaftstyp in einen Typ ändern, der NULL-Werte zulässt, damit er auf null initialisiert werden kann.  Wenn die Eigenschaft ein Array ist, versuchen Sie, die Eigenschaft als leeres Array zu initialisieren.

Führen Sie `GraphQlStateTest` durch Ausführen von `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php` aus.

### resetAfterRequestTest

Der `ResetAfterRequestTest` sucht nach allen Klassen, die `ResetAfterRequestInterface` implementieren, und überprüft, ob die `_resetState()`-Methode den Status eines Objekts in denselben Zustand zurückgibt, in dem es sich nach der Erstellung durch `ObjectManager` befand.  Dieser Test erstellt ein Service-Objekt mit `ObjectManager`, klont dieses Objekt, ruft `_resetState()` auf und vergleicht dann beide Objekte. Der Test ruft keine Methoden zwischen der Objektinstanziierung und der `_resetState()` auf und bestätigt daher nicht das Zurücksetzen eines veränderlichen Status. Es werden Probleme gefunden, bei denen ein Fehler oder Tippfehler in `_resetState()` den Status auf etwas Anderes setzen kann als ursprünglich.

#### ResetAfterRequestTest-Fehler und potenzielle Behebung

* **Klasse hat inkonsistente Eigenschaftswerte**. Wenn dieser Test fehlschlägt, überprüfen Sie, ob eine Klasse geändert wurde, sodass das Objekt nach der Erstellung andere Eigenschaftswerte hat als nach dem Aufruf der `_resetState()`. Wenn die Klasse, an der Sie arbeiten, nicht die `_resetState()` Methode selbst enthält, überprüfen Sie die Klassenhierarchie auf eine Oberklasse, die sie implementiert.

* **Auf die eingegebene Eigenschaft $x darf vor der Initialisierungsmeldung nicht zugegriffen werden**. Dieses Problem tritt auch bei `GraphQlStateTest` auf.

  Führen Sie `ResetAfterRequestTest` durch Ausführen von aus: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Funktionstests

Bei der Bereitstellung des GraphQL-Anwendungsservers sollten Erweiterungsentwickler WebAPI-Funktionstests und alle benutzerdefinierten automatisierten oder manuellen Funktionstests für GraphQL ausführen. Diese Funktionstests helfen Entwicklern, potenzielle Fehler oder Kompatibilitätsprobleme zu identifizieren.

#### Statusüberwachungsmodus

Beim Ausführen von Funktionstests (oder manuellen Tests) kann der GraphQL-Anwendungs-Server mit aktiviertem `--state-monitor mode` ausgeführt werden, um Klassen zu finden, bei denen der Status unbeabsichtigt wiederverwendet wird. Starten Sie den Anwendungsserver normal, mit Ausnahme des Parameters `--state-monitor` hinzufügen.

```
bin/magento server:run --state-monitor
```

Nachdem jede Anfrage verarbeitet wurde, wird dem `tmp` eine neue Datei hinzugefügt, z. B.: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Sobald Sie die Tests abgeschlossen haben, können diese Dateien mit dem Befehl `bin/magento server:state-monitor:aggregate-output` zusammengeführt werden, der zwei zusammengeführte Dateien erstellt, eine in `XML` und eine in `JSON`.

Beispiele:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Diese Dateien können mit jedem Tool überprüft werden, mit dem Sie XML oder JSON anzeigen können, das die geänderten Eigenschaften von Service-Objekten anzeigt, wie `GraphQlStateTest` es tut. Der `--state-monitor` verwendet dieselbe Liste zum Überspringen und Filtern wie GraphQlStateTest.

>[!NOTE]
>
>Verwenden Sie den `--state-monitor`-Modus nicht in der Produktion. Es ist nur für Entwicklung und Tests konzipiert. Es werden viele Ausgabedateien erstellt und langsamer als normal ausgeführt.

>[!NOTE]
>
>`--state-monitor` ist nicht kompatibel mit PHP-Versionen `8.3.0` - `8.3.4` aufgrund eines Fehlers im PHP Garbage Collector. Wenn Sie PHP 8.3 verwenden, müssen Sie auf `8.3.5` oder höher aktualisieren, um diese Funktion nutzen zu können.
