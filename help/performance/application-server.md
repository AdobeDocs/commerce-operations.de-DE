---
title: GraphQL Application Server
description: Befolgen Sie diese Anweisungen zum Aktivieren des GraphQL-Anwendungsservers in Ihrer Adobe Commerce-Bereitstellung.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: c2f48db87f40498a84b2bf41569bb46202565701
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 0%

---


# GraphQL Application Server

Der Commerce GraphQL-Anwendungsserver ermöglicht Adobe Commerce, den Status unter den Commerce GraphQL-API-Anfragen zu verwalten. GraphQL Application Server, der auf der Swoole-Erweiterung basiert, fungiert als Prozess mit Worker-Threads, die die Anforderungsverarbeitung handhaben. Durch Beibehaltung eines Bootstrapping-Anwendungszustands zwischen GraphQL-API-Anforderungen verbessert GraphQL Application Server die Anforderungsverarbeitung und die Gesamtproduktleistung. API-Anfragen werden deutlich effizienter.

GraphQL Application Server ist nur für Adobe Commerce verfügbar. Es steht nicht zur Magento Open Source zur Verfügung. Sie müssen ein Ticket für den Adobe Commerce-Support senden, um GraphQL Application Server für Pro-Projekte zu aktivieren.[](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)

>[!NOTE]
>
>GraphQL Application Server ist derzeit nicht mit [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/) kompatibel. Kunden von Adobe Commerce in Cloud-Infrastruktur, die derzeit [!DNL AWS S3] für [Remote-Speicher](../configuration/remote-storage/cloud-support.md) verwenden, können den GraphQL-Anwendungsserver erst verwenden, wenn Adobe später im Jahr 2024 einen Hotfix veröffentlicht hat.

## Architektur

Der GraphQL-Anwendungsserver behält den Status zwischen Commerce GraphQL-API-Anfragen bei und macht Bootstrapping nicht mehr erforderlich. Durch die prozessübergreifende Freigabe des Anwendungszustands werden GraphQL-Anforderungen deutlich effizienter, wodurch die Reaktionszeiten um bis zu 30 % verkürzt werden.

Das Share-Nichts PHP Ausführungsmodell stellt aus der Sicht der Latenz eine Herausforderung dar, da jede Anfrage das Bootstrapping des Frameworks erfordert. Dieser Bootstrapping-Prozess umfasst zeitaufwendige Aufgaben wie die Lesekonfiguration, das Einrichten des Bootstrap-Prozesses und das Erstellen von Dienstklassenobjekten.

Die Umstellung der Anforderungsverarbeitungslogik auf eine Ereignisschleife auf Anwendungsebene scheint die Herausforderung zu bewältigen, die Anforderungsverarbeitung auf Unternehmensebene zu optimieren. Dadurch entfällt die Notwendigkeit, das Bootstrapping während des Lebenszyklus der Anforderungsausführung durchzuführen.

## Vorteile

Mit GraphQL Application Server kann Adobe Commerce den Status zwischen aufeinander folgenden Commerce GraphQL-API-Anfragen aufrechterhalten. Die Freigabe des Anwendungsstatus über Anforderungen hinweg verbessert die Effizienz von API-Anfragen, indem der Verarbeitungsaufwand minimiert und die Anforderungsverarbeitung optimiert wird. Daher kann die Reaktionszeit von GraphQL-Anfragen auf bis zu 30 % reduziert werden.

## Systemanforderungen

Für das Ausführen von GraphQL Application Server ist Folgendes erforderlich:

* PHP 8.2 oder höher
* Installierte einzelne PHP-Erweiterung v5+
* Angemessener RAM und CPU basierend auf der erwarteten Belastung

## Aktivieren und Bereitstellen in der Cloud-Infrastruktur

Das Modul `ApplicationServer` (`Magento/ApplicationServer/`) aktiviert den GraphQL-Anwendungsserver.

### Pro-Projekte aktivieren

>[!NOTE]
>
>Der Anwendungsserver ist eine Opt-in-Funktion in Cloud Pro-Instanzen. Senden Sie dazu eine Support-Anfrage.

Nachdem die Funktion &quot;Anwendungsserver&quot;für Ihr Pro-Projekt aktiviert wurde, führen Sie die folgenden Schritte aus, bevor Sie GraphQL Application Server bereitstellen:

1. Stellen Sie Adobe Commerce in der Cloud-Infrastruktur mithilfe der Cloud-Vorlage aus der Verzweigung [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver) bereit.
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen [kompatibel](https://developer.adobe.com/commerce/php/development/components/app-server/) mit GraphQL Application Server sind.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Passen Sie bei Bedarf Einstellungen in der Datei &quot;application-server/nginx.conf.sample&quot;an.
1. Kommentieren Sie den aktiven Abschnitt &quot;Web&quot;in der Datei `project_root/.magento.app.yaml` vollständig aus.
1. Heben Sie die Auskommentierung der folgenden &quot;Web&quot;-Abschnittskonfiguration in der Datei &quot;`project_root/.magento.app.yaml`&quot;auf, die den Befehl &quot;GraphQL Application Server `start`&quot;enthält.

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

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Bereitstellen von Pro-Projekten

Nach Abschluss der Aktivierungsschritte müssen Sie Änderungen an Ihr Git-Repository senden, um GraphQL Application Server bereitzustellen:

```bash
git push
```

### Aktivieren von Starterprojekten

Führen Sie die folgenden Schritte aus, bevor Sie GraphQL Application Server in Starterprojekten bereitstellen:

1. Stellen Sie Adobe Commerce in der Cloud-Infrastruktur mithilfe der Cloud-Vorlage aus der Verzweigung [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver) bereit.
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen mit GraphQL Application Server kompatibel sind.
1. Vergewissern Sie sich, dass die Umgebungsvariable `CRYPT_KEY` für Ihre Instanz festgelegt ist. Sie können den Status dieser Variablen im Cloud Project Portal (Onboarding-Benutzeroberfläche) überprüfen.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Benennen Sie `application-server/.magento/.magento.app.yaml.sample` in `application-server/.magento/.magento.app.yaml` um und passen Sie bei Bedarf die Einstellungen in .magento.app.yaml an.
1. Heben Sie die Auskommentierung der Konfiguration der folgenden Route in der Datei `project_root/.magento/routes.yaml` auf, um den Traffic von `/graphql` an den GraphQL-Anwendungsserver umzuleiten.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Fügen Sie aktualisierte Dateien zum Git-Index hinzu:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Übernehmen Sie Ihre Änderungen:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Stellen Sie sicher, dass alle benutzerdefinierten Einstellungen in Ihrer Stammdatei `.magento.app.yaml` ordnungsgemäß in die Datei `application-server/.magento/.magento.app.yaml` migriert werden. Nachdem die Datei `application-server/.magento/.magento.app.yaml` zu Ihrem Projekt hinzugefügt wurde, sollten Sie sie zusätzlich zur Stammdatei `.magento.app.yaml` beibehalten. Wenn Sie beispielsweise [rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) oder [Webeigenschaften verwalten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) konfigurieren müssen, sollten Sie auch `application-server/.magento/.magento.app.yaml` dieselbe Konfiguration hinzufügen.

### Bereitstellen von Starter-Projekten

Nachdem Sie die Aktivierung [Schritte](#before-you-begin-a-cloud-starter-deployment) abgeschlossen haben, pushen Sie Änderungen an Ihr Git-Repository, um GraphQL Application Server bereitzustellen:

```bash
git push
```

### Überprüfung der Aktivierung für Cloud-Projekte

1. Führen Sie eine GraphQL-Abfrage oder -Mutation für Ihre Instanz durch, um sicherzustellen, dass der Endpunkt `graphql` zugänglich ist. Beispiel:

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

1. Verwenden Sie SSH, um auf Ihre Cloud-Instanz zuzugreifen. Der `project_root/var/log/application-server.log` sollte einen neuen Protokolldatensatz für jede GraphQL-Anfrage enthalten.

1. Sie können auch überprüfen, ob GraphQL Application Server ausgeführt wird, indem Sie den folgenden Befehl ausführen:

   ```bash
   ps aux|grep php
   ```

   Es sollte ein `bin/magento server:run` -Prozess mit mehreren Threads angezeigt werden.

Wenn diese Überprüfungsschritte erfolgreich sind, wird GraphQL Application Server ausgeführt und `/graphql` -Anforderungen bereitgestellt.

## Aktivieren von lokalen Projekten

Das Modul `ApplicationServer` (`Magento/ApplicationServer/`) aktiviert den GraphQL-Anwendungsserver für GraphQL-APIs.

Das lokale Ausführen des GraphQL-Anwendungsservers erfordert die Installation der Swoole-Erweiterung und eine geringfügige Änderung der Nginx-Konfigurationsdatei Ihrer Bereitstellung.

### Voraussetzungen

Führen Sie die folgenden Schritte aus, bevor Sie das Modul `ApplicationServer` aktivieren:

* Nginx konfigurieren
* Installieren und Konfigurieren der Swoole v5+-Erweiterung

#### Nginx konfigurieren

Ihre spezifische Commerce-Bereitstellung bestimmt, wie Nginx konfiguriert wird. Im Allgemeinen trägt die Nginx-Konfigurationsdatei standardmäßig den Namen `nginx.conf` und befindet sich in einem dieser Verzeichnisse: `/usr/local/nginx/conf`, `/etc/nginx` oder `/usr/local/etc/nginx`. Weitere Informationen zur Konfiguration von Nginx finden Sie im [Anfängerhandbuch](https://nginx.org/en/docs/beginners_guide.html) .

Beispiel-Nginx-Konfiguration:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Installieren und Konfigurieren von Swoole

Um den GraphQL-Anwendungsserver lokal auszuführen, installieren Sie die Swoole-Erweiterung (v5.0 oder höher). Es gibt mehrere Möglichkeiten, diese Erweiterung zu installieren.

Im folgenden Verfahren wird beschrieben, wie Sie die Swoole-Erweiterung für PHP 8.2 auf OSX-basierten Systemen installieren. Es ist eine von mehreren Möglichkeiten, die Swoole-Erweiterung zu installieren.

```bash
pecl install swoole
```

Während der Installation zeigt Adobe Commerce die Aufforderung an, die Unterstützung für `openssl`, `mysqlnd`, `sockets`, `http2` und `postgres` zu aktivieren. Geben Sie `yes` für alle Optionen außer `postgres` ein.

### Swoolinstallation überprüfen

Vergewissern Sie sich, dass die Erweiterung erfolgreich aktiviert wurde:

```bash
php -m | grep swoole
```

### Häufige Fehler bei der Installation von Swoole

Fehler, die während der Installation auftreten, treten normalerweise während der `pecl` -Installationsphase auf. Zu den typischen Fehlern zählen fehlende `openssl.h` - und `pcre2.h` -Dateien. Um diese Fehler zu beheben, stellen Sie sicher, dass diese beiden Pakete in Ihrem lokalen System installiert sind.

* Überprüfen Sie den Speicherort von `openssl` , indem Sie Folgendes ausführen:

```bash
openssl version -d
```

Dieser Befehl zeigt den Pfad, in dem `openssl` installiert ist.

* Überprüfen Sie den Speicherort von `pcre2` , indem Sie Folgendes ausführen:

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

Um Probleme im Zusammenhang mit `openssl` zu beheben, führen Sie Folgendes aus:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Vergewissern Sie sich, dass Sie den Pfad aus Ihrer lokalen `dev`-Umgebung verwenden.

#### Validierung der Lösung von Problemen im Zusammenhang mit Öffnungen

Sie können den folgenden Befehl erneut ausführen, um zu überprüfen, ob Probleme im Zusammenhang mit &quot;openssl&quot;behoben wurden:

```bash
pecl install swoole
```

#### Beheben von Problemen mit pcre2.h

Um Probleme im Zusammenhang mit `pcre2.h` zu beheben, verknüpfen Sie den Pfad `pcre2.h` mit Ihrem installierten PHP-Erweiterungsverzeichnis. Ihre spezifische installierte Version von PHP und `pcr2.h` bestimmt die jeweilige Version des Befehls, die Sie verwenden sollten.

### GraphQL Application Server ausführen

Starten Sie GraphQL Application Server:

```bash
bin/magento server:run
```

Dieser Befehl startet einen HTTP-Anschluss auf 9501. Sobald der GraphQL-Anwendungsserver gestartet wird, wird Port 9501 zu einem HTTP-Proxyserver für alle GraphQL-Abfragen.

So überprüfen Sie, ob GraphQL Application Server in Ihrer Bereitstellung ausgeführt wird:

```bash
ps aux | grep php
```

Weitere Möglichkeiten zur Überprüfung der Ausführung von GraphQL Application Server sind:

* Überprüfen Sie die Datei `/var/log/application-server.log` auf Einträge, die sich auf verarbeitete GraphQL-Anforderungen beziehen.
* Versuchen Sie, eine Verbindung zum HTTP-Anschluss herzustellen, an dem der GraphQL-Anwendungsserver ausgeführt wird. Beispiel: `curl -g 'http://localhost:9501/graph`.

### Vergewissern Sie sich, dass GraphQL-Anforderungen verarbeitet werden

GraphQL Application Server fügt den Antwortheader `X-Backend` mit dem Wert `graphql_server` zu jeder von ihm verarbeiteten Anforderung hinzu. Um zu überprüfen, ob eine Anforderung vom GraphQL-Anwendungsserver verarbeitet wurde, suchen Sie nach diesem Antwortheader.

### Kompatibilität von Erweiterung und Anpassung bestätigen

Entwickler und Händler von Erweiterungen sollten zunächst überprüfen, ob ihr Erweiterungs- und Anpassungscode den technischen Richtlinien entspricht, die in [Technische Richtlinien](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/) beschrieben sind.

Beachten Sie diese Richtlinien bei der Code-Bewertung:

* Dienstklassen (d. h. Klassen, die Verhalten, aber keine Daten bereitstellen, wie z. B. `EventManager`) sollten keinen veränderlichen Status aufweisen.
* Vermeiden Sie eine zeitliche Kopplung.

## GraphQL Application Server deaktivieren

Die Verfahren zum Deaktivieren des GraphQL-Anwendungsservers variieren je nachdem, ob der Server in einer lokalen oder Cloud-Bereitstellung ausgeführt wird.

### GraphQL Application Server deaktivieren (Cloud)

1. Entfernen Sie alle neuen Dateien und alle anderen Code-Änderungen, die während der Bereitstellungsvorbereitungen im `AppServer Enabled` -Commit enthalten waren.

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Stellen Sie diese Änderungen mit diesem Befehl bereit:

   ```bash
   git push
   ```

### GraphQL Application Server deaktivieren (vor Ort)

1. Kommentieren Sie den Abschnitt `/graphql` der Datei `nginx.conf` aus, die Sie beim Aktivieren von GraphQL Application Server hinzugefügt haben.
1. Starten Sie nginx neu.

Diese Methode zur Deaktivierung des GraphQL-Anwendungsservers kann hilfreich sein, um die Leistung schnell zu testen oder zu vergleichen.

### Vergewissern Sie sich, dass GraphQL Application Server deaktiviert ist.

Geben Sie den folgenden Befehl ein, um sicherzustellen, dass GraphQL-Anforderungen von `php-fpm` anstelle von GraphQL Application Server verarbeitet werden: `ps aux | grep php`.

Nachdem der GraphQL-Anwendungsserver deaktiviert wurde:

* `bin/magento server:run` ist inaktiv.
* `var/log/application-server.log` enthält keine Einträge nach GraphQL-Anforderungen.

## Integrations- und Funktionstests für GraphQL Application Server

Erweiterungsentwickler können zwei Integrationstests ausführen, um die Kompatibilität der Erweiterung mit dem GraphQL-Anwendungsserver zu überprüfen: `GraphQlStateTest` und `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` erkennt Status in freigegebenen Objekten, die nicht für mehrere Anforderungen wiederverwendet werden sollen.

Dieser Test dient der Erkennung von Statusänderungen in Dienstobjekten, die von der `ObjectManager` erzeugt werden. Der Test führt identische GraphQL-Abfragen zweimal aus und vergleicht den Dienstobjektstatus vor und nach der zweiten Abfrage.

#### GraphQlStateTest-Fehler und potenzielle Behebung

* **Eine Liste kann nicht hinzugefügt, übersprungen oder gefiltert werden**. Wenn ein Fehler auftritt, der darauf hindeutet, dass es nicht sicher ist, eine Liste hinzuzufügen, zu überspringen oder zu filtern, sollten Sie überlegen, ob die Klasse auf abwärtskompatible Weise umgestaltet werden kann, um die Fabriken der Dienstklassen mit veränderlichem Status zu verwenden.

* **Klasse weist einen veränderlichen Status auf**. Wenn die Klasse selbst einen veränderlichen Status aufweist, versuchen Sie, Ihren Code neu zu schreiben, um diesen Status zu umgehen. Wenn der veränderliche Status aus Leistungsgründen erforderlich ist, implementieren Sie `ResetAfterRequestInterface` und verwenden Sie `_resetState()`, um das Objekt auf seinen ursprünglichen konstruierten Status zurückzusetzen.

* **Eingegebene Eigenschaft $x darf nicht vor der Initialisierungsmeldung aufgerufen werden**. Fehler mit diesem Nachrichtentyp weisen darauf hin, dass die angegebene Eigenschaft nicht vom Konstruktor initialisiert wurde. Dies ist eine Form der zeitlichen Kopplung, die auftritt, da das Objekt nach der anfänglichen Konstruktion nicht mehr verwendet werden kann. Diese Kopplung tritt auch dann auf, wenn die Eigenschaft privat ist, da der Collector, der die Daten aus den Eigenschaften abruft, die PHP Reflektionsfunktion verwendet. Versuchen Sie in diesem Fall, die Klasse zu refaktorieren, um eine zeitliche Kopplung zu vermeiden und einen veränderlichen Status zu vermeiden. Wenn diese Refaktorierung den Fehler nicht behebt, können Sie den Eigenschaftstyp in einen nullbaren Typ ändern, damit er auf null initialisiert werden kann.  Wenn die Eigenschaft ein Array ist, versuchen Sie, die Eigenschaft als leeres Array zu initialisieren.

Führen Sie `GraphQlStateTest` aus, indem Sie `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php` ausführen.

### ResetAfterRequestTest

`ResetAfterRequestTest` sucht nach allen Klassen, die `ResetAfterRequestInterface` implementieren, und stellt sicher, dass die `_resetState()` -Methode den Status eines Objekts in dem Zustand zurückgibt, in dem es sich nach der Erstellung durch `ObjectManager` befindet.  Dieser Test erstellt ein Dienstobjekt mit `ObjectManager`, klont dieses Objekt dann, ruft `_resetState()` auf und vergleicht dann beide Objekte. Der Test ruft zwischen der Objektinstanziierung und `_resetState()` keine Methoden auf, daher wird nicht bestätigt, dass ein veränderlicher Status zurückgesetzt wird. Es gibt jedoch Probleme, bei denen ein Fehler oder Typo in `_resetState()` den Status auf etwas Anderes als ursprünglich festlegen kann.

#### ResetAfterRequestTest-Fehler und potenzielle Behebung

* **Klasse weist inkonsistente Eigenschaftswerte auf**. Wenn dieser Test fehlschlägt, überprüfen Sie, ob eine Klasse mit dem Ergebnis geändert wurde, dass das Objekt nach der Erstellung andere Eigenschaftswerte aufweist als nach dem Aufruf der `_resetState()` -Methode. Wenn die Klasse, an der Sie arbeiten, nicht die `_resetState()` -Methode selbst enthält, überprüfen Sie die Klassenhierarchie auf eine Superklasse, die sie implementiert.

* **Eingegebene Eigenschaft $x darf nicht vor der Initialisierungsmeldung aufgerufen werden**. Dieses Problem tritt auch bei `GraphQlStateTest` auf.

  Führen Sie `ResetAfterRequestTest` aus, indem Sie Folgendes ausführen: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Funktionstests

Entwickler von Erweiterungen sollten bei der Bereitstellung von GraphQL Application Server WebAPI-Funktionstests für GraphQL sowie benutzerdefinierte automatisierte oder manuelle Funktionstests für GraphQL durchführen. Mithilfe dieser Funktionstests können Entwickler potenzielle Fehler oder Kompatibilitätsprobleme erkennen.

#### Statusanzeigemodus

Beim Ausführen von Funktionstests (oder manuellen Tests) kann der Anwendungsserver mit aktiviertem `--state-monitor mode` ausgeführt werden, um Klassen zu finden, in denen der Status unbeabsichtigt wiederverwendet wird. Starten Sie den Anwendungsserver normal, mit Ausnahme des Parameters `--state-monitor` .

```
bin/magento server:run --state-monitor
```

Nachdem jede Anfrage verarbeitet wurde, wird eine neue Datei zum Verzeichnis `tmp` hinzugefügt, z. B.: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Nachdem Sie die Tests abgeschlossen haben, können diese Dateien mit dem Befehl `bin/magento server:state-monitor:aggregate-output` zusammengeführt werden, mit dem zwei zusammengeführte Dateien erstellt werden, eine in `XML` und eine in `JSON`.

Beispiele:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Diese Dateien können mit jedem Tool, das Sie zum Anzeigen von XML oder JSON verwenden, überprüft werden, das die geänderten Eigenschaften von Dienstobjekten wie GraphQlStateTest zeigt. Der Modus `--state-monitor` verwendet dieselbe Liste und Filterliste wie GraphQlStateTest.

>[!NOTE]
>
>Verwenden Sie nicht den `--state-monitor` -Modus in der Produktion. Sie ist nur für Entwicklung und Tests konzipiert. Es werden viele Ausgabedateien erstellt und langsamer als normal ausgeführt.

>[!NOTE]
>
>`--state-monitor` ist nicht mit PHP-Versionen `8.3.0` - `8.3.4` kompatibel, da ein Fehler im PHP-Garbage Collector auftritt. Wenn Sie PHP 8.3 verwenden, müssen Sie auf `8.3.5` oder höher aktualisieren, um diese Funktion nutzen zu können.
