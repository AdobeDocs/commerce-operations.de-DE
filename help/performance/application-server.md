---
title: Anwendungsserver für GraphQL-APIs
description: Befolgen Sie diese Anweisungen zum Aktivieren des Anwendungsservers für GraphQL-APIs in Ihrer Adobe Commerce-Bereitstellung.
badgeCoreBeta: label="2.4.7-Beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 1fdb29c1a6666aeeef7e546bc7d57a83a40b7542
workflow-type: tm+mt
source-wordcount: '1844'
ht-degree: 0%

---

# Anwendungsserver für GraphQL-APIs

Der Commerce-Anwendungsserver für GraphQL-APIs ermöglicht es Adobe Commerce, den Status unter Commerce GraphQL-API-Anfragen zu erhalten. Der Anwendungsserver, der auf der Swoole-Erweiterung basiert, fungiert als Prozess mit Worker-Threads, die die Anforderungsverarbeitung handhaben. Durch die Beibehaltung eines Bootstrapping-Anwendungszustands zwischen GraphQL-API-Anforderungen verbessert Application Server die Anforderungsverarbeitung und die Gesamtproduktleistung. API-Anfragen werden deutlich effizienter.

Anwendungsserver wird nur in Adobe Commerce auf Cloud-Infrastruktur-Starter- und Pro-Projekt unterstützt. Sie steht nicht für Magento Open Source-Projekte zur Verfügung. Adobe bietet keine Unterstützung für lokale Bereitstellungen von Application Server.

## Übersicht über die Anwendungsserverarchitektur

Der Anwendungsserver behält den Status zwischen Commerce GraphQL-API-Anfragen bei und macht Bootstrapping nicht mehr erforderlich. Durch die prozessübergreifende Freigabe des Anwendungszustands werden GraphQL-Anforderungen deutlich effizienter, wodurch die Reaktionszeiten um bis zu 30 % verkürzt werden.

Das Share-Nichts PHP Ausführungsmodell stellt aus der Sicht der Latenz eine Herausforderung dar, da jede Anfrage das Bootstrapping des Frameworks erfordert. Dieser Bootstrapping-Prozess umfasst zeitaufwendige Aufgaben wie die Lesekonfiguration, das Einrichten des Bootstrap-Prozesses und das Erstellen von Dienstklassenobjekten.

Die Umstellung der Anforderungsverarbeitungslogik auf eine Ereignisschleife auf Anwendungsebene scheint die Herausforderung zu bewältigen, die Anforderungsverarbeitung auf Unternehmensebene zu optimieren. Dadurch entfällt die Notwendigkeit, das Bootstrapping während des Lebenszyklus der Anforderungsausführung durchzuführen.

## Vorteile der Verwendung des Anwendungsservers

Der Anwendungsserver ermöglicht es Adobe Commerce, den Status zwischen aufeinander folgenden Commerce GraphQL-API-Anfragen aufrechtzuerhalten. Die Freigabe des Anwendungsstatus über Anforderungen hinweg verbessert die Effizienz von API-Anfragen, indem der Verarbeitungsaufwand minimiert und die Anforderungsverarbeitung optimiert wird. Daher kann die Reaktionszeit von GraphQL-Anfragen auf bis zu 30 % reduziert werden.

## Systemanforderungen

Für das Ausführen des Anwendungsservers ist Folgendes erforderlich:

* PHP 8.2 oder höher
* Installierte einzelne PHP-Erweiterung v5+
* Angemessener RAM und CPU basierend auf der erwarteten Belastung

## Anwendungsserver aktivieren

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert den Anwendungsserver für GraphQL-APIs. Der Anwendungsserver wird in lokalen und Cloud-Implementierungen unterstützt.

## Aktivieren des Anwendungsservers in Cloud Pro

Führen Sie die folgenden Aufgaben aus, bevor Sie den Anwendungsserver in Cloud Pro bereitstellen:

1. Vergewissern Sie sich mithilfe der Cloud-Vorlagenversion 2.4.7 oder höher, dass Adobe Commerce auf dem Commerce Cloud installiert ist.
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen [kompatibel](https://developer.adobe.com/commerce/php/development/components/app-server/) mit dem Anwendungsserver.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Passen Sie bei Bedarf Einstellungen in der Datei &quot;application-server/nginx.conf.sample&quot;an.
1. Kommentieren Sie den aktiven Abschnitt &quot;Web&quot;aus unter `project_root/.magento.app.yaml` -Datei.
1. Entfernen Sie die Auskommentierung der folgenden &quot;Web&quot;-Abschnittskonfiguration in `project_root/.magento.app.yaml` -Datei, die den Startbefehl des Anwendungsservers enthält.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Fügen Sie mit diesem Befehl aktualisierte Dateien zum Git-Index hinzu:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Bereitstellen des Anwendungsservers auf Cloud Pro

Stellen Sie nach dem Ausführen der erforderlichen Aufgaben den Anwendungsserver mithilfe dieses Befehls bereit:

```bash
git push
```

### Vor der Implementierung von Cloud Starter

Führen Sie die folgenden Aufgaben aus, bevor Sie den Anwendungsserver in Cloud Starter bereitstellen:

1. Vergewissern Sie sich mithilfe der Cloud-Vorlagenversion 2.4.7 oder höher, dass Adobe Commerce auf dem Commerce Cloud installiert ist.
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen mit Application Server kompatibel sind.
1. Vergewissern Sie sich, dass `CRYPT_KEY` Umgebungsvariable für Ihre Instanz festgelegt ist. Sie können den Status dieser Variablen im Cloud Project Portal (Onboarding-Benutzeroberfläche) überprüfen.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Benennen Sie &quot;application-server/.magento/.magento.app.yaml.sample&quot;in &quot;application-server/.magento/.magento.app.yaml&quot;um und passen Sie bei Bedarf die Einstellungen in .magento.app.yaml an.
1. Entfernen Sie den Kommentar für die Konfiguration der folgenden Route in der `project_root/.magento/routes.yaml` -Datei umleiten `/graphql` Traffic zum Anwendungsserver.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Fügen Sie dem Git-Index aktualisierte Dateien mit dem folgenden Befehl hinzu:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Bereitstellen des Anwendungsservers auf Cloud Starter

Nach Abschluss der [Voraussetzungen](#before-you-begin-a-cloud-starter-deployment), stellen Sie den Anwendungsserver mithilfe dieses Befehls bereit:

```bash
git push
```

### Überprüfung der Aktivierung des Anwendungsservers in Cloud Starter

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

1. Verwenden Sie SSH, um auf Ihre Cloud-Instanz zuzugreifen. Die `project_root/var/log/application-server.log` sollte einen neuen Protokolldatensatz für jede GraphQL-Anfrage enthalten.

1. Sie können auch überprüfen, ob Application Server ausgeführt wird, indem Sie den folgenden Befehl ausführen:

   ```bash
   ps aux|grep php
   ```

   Sie sollten eine `bin/magento server:run` mit mehreren Threads verarbeitet werden.

Wenn diese Überprüfungsschritte erfolgreich sind, wird der Anwendungsserver ausgeführt und `/graphql` -Anfragen.


## Aktivieren von Application Server bei lokalen Bereitstellungen

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert den Anwendungsserver für GraphQL-APIs.

Lokales Ausführen des Anwendungsservers erfordert die Installation der Swoole-Erweiterung und eine geringfügige Änderung der NGINX-Konfigurationsdatei Ihrer Bereitstellung.

### Bevor Sie mit der Bereitstellung vor Ort beginnen

Führen Sie diese beiden Aufgaben aus, bevor Sie die `ApplicationServer` -Modul:

* Nginx konfigurieren

* Installieren und Konfigurieren der Swoole v5+-Erweiterung

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

### Installieren und Konfigurieren von Swoole

Um den Anwendungsserver lokal auszuführen, installieren Sie die Swoole-Erweiterung (v5.0 oder höher). Es gibt mehrere Möglichkeiten, diese Erweiterung zu installieren.

## Anwendungsserver ausführen

Starten Sie den Anwendungsserver:

```bash
bin/magento server:run
```

Dieser Befehl startet einen HTTP-Anschluss auf 9501. Sobald der Anwendungsserver gestartet wird, wird Port 9501 zu einem HTTP-Proxyserver für alle GraphQL-Abfragen.

## Beispiel: Installation von Swoole (OSX)

Dieses Verfahren zeigt, wie die Swoole-Erweiterung auf PHP 8.2 für OSX-basierte Systeme installiert wird. Es ist eine von mehreren Möglichkeiten, die Swoole-Erweiterung zu installieren.

### Swoole installieren

Geben Sie ein:

```bash
pecl install swoole
```

Während der Installation zeigt Adobe Commerce Aufforderungen an, um den Support für `openssl`, `mysqlnd`, `sockets`, `http2`, und `postgres`. Eingabe `yes` für alle Optionen außer `postgres`.

### Installation von Swoole bestätigen

Ausführen `php -m | grep swoole` , um zu bestätigen, dass die Erweiterung erfolgreich aktiviert wurde.

### Häufige Fehler bei der Installation von Swoole

Fehler, die während der Installation auftreten, treten normalerweise während der `pecl` Installationsphase. Typische Fehler beinhalten fehlende `openssl.h` und `pcre2.h` -Dateien. Um diese Fehler zu beheben, stellen Sie sicher, dass diese beiden Pakete in Ihrem lokalen System installiert sind.

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
pecl install swoole
```

#### Beheben von Problemen mit pcre2.h

Beheben von Problemen im Zusammenhang mit `pcre2.h`, verknüpfen Sie die `pcre2.h` Pfad zu Ihrem installierten PHP-Erweiterungsverzeichnis. Ihre spezifische installierte Version von PHP und `pcr2.h` bestimmt die jeweilige Version des Befehls, den Sie verwenden sollten.

### Überprüfen, ob der Anwendungsserver ausgeführt wird

Führen Sie den folgenden Befehl aus, um sicherzustellen, dass der Anwendungsserver in Ihrer Bereitstellung ausgeführt wird:

```bash
ps aux | grep php
```

Zu den weiteren Möglichkeiten, um zu überprüfen, ob der Anwendungsserver ausgeführt wird, gehören:

* Überprüfen Sie die `/var/log/application-server.log` -Datei für Einträge, die sich auf verarbeitete GraphQL-Anforderungen beziehen.
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
* `var/log/application-server.log` enthält keine Einträge nach GraphQL-Anforderungen.

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
