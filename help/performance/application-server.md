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

GraphQL Application Server ist nur für Adobe Commerce verfügbar. Es steht nicht zur Magento Open Source zur Verfügung. Sie müssen [Senden eines Adobe Commerce-Supports](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) Ticket zum Aktivieren von GraphQL Application Server für Pro-Projekte.

>[!NOTE]
>
>GraphQL Application Server ist derzeit nicht kompatibel mit [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Adobe Commerce auf Cloud-Infrastruktur-Kunden, die derzeit verwenden [!DNL AWS S3] für [Remote-Speicher](../configuration/remote-storage/cloud-support.md) kann den GraphQL-Anwendungsserver erst verwenden, wenn die Adobe einen Hotfix später im Jahr 2024 veröffentlicht.

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

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert GraphQL Application Server.

### Pro-Projekte aktivieren

>[!NOTE]
>
>Der Anwendungsserver ist eine Opt-in-Funktion in Cloud Pro-Instanzen. Senden Sie dazu eine Support-Anfrage.

Nachdem die Funktion &quot;Anwendungsserver&quot;für Ihr Pro-Projekt aktiviert wurde, führen Sie die folgenden Schritte aus, bevor Sie GraphQL Application Server bereitstellen:

1. Stellen Sie Adobe Commerce in der Cloud-Infrastruktur mithilfe der Cloud-Vorlage aus dem [2.4.7-Anwendungsserver-Verzweigung](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen [kompatibel](https://developer.adobe.com/commerce/php/development/components/app-server/) mit GraphQL Application Server.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Passen Sie bei Bedarf Einstellungen in der Datei &quot;application-server/nginx.conf.sample&quot;an.
1. Kommentieren Sie den aktiven Abschnitt &quot;Web&quot;aus unter `project_root/.magento.app.yaml` -Datei.
1. Entfernen Sie die Auskommentierung der folgenden &quot;Web&quot;-Abschnittskonfiguration in `project_root/.magento.app.yaml` -Datei, die den GraphQL-Anwendungsserver enthält `start` Befehl.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Stellen Sie sicher, dass `/application-server/start.sh` ist ausführbar, indem Sie den folgenden Befehl ausführen:

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

1. Stellen Sie Adobe Commerce in der Cloud-Infrastruktur mithilfe der Cloud-Vorlage aus dem [2.4.7-Anwendungsserver-Verzweigung](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen mit GraphQL Application Server kompatibel sind.
1. Vergewissern Sie sich, dass `CRYPT_KEY` Umgebungsvariable für Ihre Instanz festgelegt ist. Sie können den Status dieser Variablen im Cloud Project Portal (Onboarding-Benutzeroberfläche) überprüfen.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Umbenennen `application-server/.magento/.magento.app.yaml.sample` nach `application-server/.magento/.magento.app.yaml` und passen Sie bei Bedarf die Einstellungen in .magento.app.yaml an.
1. Entfernen Sie den Kommentar für die Konfiguration der folgenden Route in der `project_root/.magento/routes.yaml` -Datei umleiten `/graphql` Traffic zum GraphQL-Anwendungsserver.

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
>Stellen Sie sicher, dass alle benutzerdefinierten Einstellungen in Ihrem Stammverzeichnis `.magento.app.yaml` -Datei entsprechend in die `application-server/.magento/.magento.app.yaml` -Datei. Nach dem `application-server/.magento/.magento.app.yaml` -Datei zu Ihrem Projekt hinzugefügt wurde, sollten Sie sie zusätzlich zum Stammverzeichnis beibehalten `.magento.app.yaml` -Datei. Wenn Sie beispielsweise [rabbitmq konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) oder [Webeigenschaften verwalten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) Sie sollten dieselbe Konfiguration zu `application-server/.magento/.magento.app.yaml` sowie.

### Bereitstellen von Starter-Projekten

Nach Abschluss der Aktivierung [Schritte](#before-you-begin-a-cloud-starter-deployment), Push-Änderungen an Ihr Git-Repository senden, um GraphQL Application Server bereitzustellen:

```bash
git push
```

### Überprüfung der Aktivierung für Cloud-Projekte

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

1. Sie können auch überprüfen, ob GraphQL Application Server ausgeführt wird, indem Sie den folgenden Befehl ausführen:

   ```bash
   ps aux|grep php
   ```

   Sie sollten eine `bin/magento server:run` mit mehreren Threads verarbeitet werden.

Wenn diese Überprüfungsschritte erfolgreich sind, wird GraphQL Application Server ausgeführt und bereitgestellt. `/graphql` -Anfragen.

## Aktivieren von lokalen Projekten

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert GraphQL Application Server für GraphQL-APIs.

Das lokale Ausführen des GraphQL-Anwendungsservers erfordert die Installation der Swoole-Erweiterung und eine geringfügige Änderung der Nginx-Konfigurationsdatei Ihrer Bereitstellung.

### Voraussetzungen

Führen Sie die folgenden Schritte aus, bevor Sie die `ApplicationServer` -Modul:

* Nginx konfigurieren
* Installieren und Konfigurieren der Swoole v5+-Erweiterung

#### Nginx konfigurieren

Ihre spezifische Commerce-Bereitstellung bestimmt, wie Nginx konfiguriert wird. Im Allgemeinen erhält die Nginx-Konfigurationsdatei standardmäßig den Namen `nginx.conf` und wird in einem dieser Verzeichnisse platziert: `/usr/local/nginx/conf`, `/etc/nginx`oder `/usr/local/etc/nginx`. Siehe [Anfängerhandbuch](https://nginx.org/en/docs/beginners_guide.html) für weitere Informationen zur Konfiguration von Nginx.

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

Während der Installation zeigt Adobe Commerce Aufforderungen an, um den Support für `openssl`, `mysqlnd`, `sockets`, `http2`, und `postgres`. Eingabe `yes` für alle Optionen außer `postgres`.

### Swoolinstallation überprüfen

Vergewissern Sie sich, dass die Erweiterung erfolgreich aktiviert wurde:

```bash
php -m | grep swoole
```

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

* Überprüfen Sie die `/var/log/application-server.log` -Datei für Einträge, die sich auf verarbeitete GraphQL-Anforderungen beziehen.
* Versuchen Sie, eine Verbindung zum HTTP-Anschluss herzustellen, an dem der GraphQL-Anwendungsserver ausgeführt wird. Beispiel: `curl -g 'http://localhost:9501/graph`.

### Vergewissern Sie sich, dass GraphQL-Anforderungen verarbeitet werden

GraphQL Application Server fügt die `X-Backend` Antwortheader mit dem Wert `graphql_server` für jede Anfrage, die verarbeitet wird. Um zu überprüfen, ob eine Anforderung vom GraphQL-Anwendungsserver verarbeitet wurde, suchen Sie nach diesem Antwortheader.

### Kompatibilität von Erweiterung und Anpassung bestätigen

Entwickler und Händler von Erweiterungen sollten zunächst überprüfen, ob ihr Erweiterungs- und Anpassungscode den technischen Richtlinien entspricht, die unter [Technische Leitlinien](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Beachten Sie diese Richtlinien bei der Code-Bewertung:

* Dienstklassen (d. h. Klassen, die Verhalten, aber keine Daten bereitstellen, z. B. `EventManager`) sollte keinen veränderlichen Status aufweisen.
* Vermeiden Sie eine zeitliche Kopplung.

## GraphQL Application Server deaktivieren

Die Verfahren zum Deaktivieren des GraphQL-Anwendungsservers variieren je nachdem, ob der Server in einer lokalen oder Cloud-Bereitstellung ausgeführt wird.

### GraphQL Application Server deaktivieren (Cloud)

1. Entfernen Sie alle neuen Dateien und alle anderen Codeänderungen, die im `AppServer Enabled` während Ihrer Bereitstellungsvorbereitungen.

1. Bestätigen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Stellen Sie diese Änderungen mit diesem Befehl bereit:

   ```bash
   git push
   ```

### GraphQL Application Server deaktivieren (vor Ort)

1. Kommentieren Sie die `/graphql` Abschnitt `nginx.conf` -Datei, die Sie beim Aktivieren von GraphQL Application Server hinzugefügt haben.
1. Starten Sie nginx neu.

Diese Methode zur Deaktivierung des GraphQL-Anwendungsservers kann hilfreich sein, um die Leistung schnell zu testen oder zu vergleichen.

### Vergewissern Sie sich, dass GraphQL Application Server deaktiviert ist.

So bestätigen Sie, dass GraphQL-Anforderungen von `php-fpm` Geben Sie anstelle von GraphQL Application Server folgenden Befehl ein: `ps aux | grep php`.

Nachdem der GraphQL-Anwendungsserver deaktiviert wurde:

* `bin/magento server:run` ist inaktiv.
* `var/log/application-server.log` enthält keine Einträge nach GraphQL-Anforderungen.

## Integrations- und Funktionstests für GraphQL Application Server

Erweiterungsentwickler können zwei Integrationstests ausführen, um die Kompatibilität der Erweiterung mit GraphQL Application Server zu überprüfen: `GraphQlStateTest` und `ResetAfterRequestTest`.

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

Entwickler von Erweiterungen sollten bei der Bereitstellung von GraphQL Application Server WebAPI-Funktionstests für GraphQL sowie benutzerdefinierte automatisierte oder manuelle Funktionstests für GraphQL durchführen. Mithilfe dieser Funktionstests können Entwickler potenzielle Fehler oder Kompatibilitätsprobleme erkennen.

#### Statusanzeigemodus

Beim Ausführen von Funktionstests (oder manuellen Tests) kann der Anwendungsserver mit `--state-monitor mode` aktiviert wurde, um zu helfen, Klassen zu finden, in denen der Status unbeabsichtigt wiederverwendet wird. Starten Sie den Anwendungsserver normal, außer fügen Sie die `--state-monitor` -Parameter.

```
bin/magento server:run --state-monitor
```

Nachdem jede Anfrage verarbeitet wurde, wird eine neue Datei zum `tmp` -Verzeichnis, z. B.: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Nach Abschluss des Tests können diese Dateien mit der `bin/magento server:state-monitor:aggregate-output` -Befehl, der zwei zusammengeführte Dateien erstellt, eine in `XML` und ein `JSON`.

Beispiele:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Diese Dateien können mit jedem Tool, das Sie zum Anzeigen von XML oder JSON verwenden, überprüft werden, das die geänderten Eigenschaften von Dienstobjekten wie GraphQlStateTest zeigt. Die `--state-monitor` verwendet dieselbe Liste und Filterliste wie GraphQlStateTest.

>[!NOTE]
>
>Verwenden Sie nicht das `--state-monitor` -Modus in der Produktion. Sie ist nur für Entwicklung und Tests konzipiert. Es werden viele Ausgabedateien erstellt und langsamer als normal ausgeführt.

>[!NOTE]
>
>`--state-monitor` ist nicht kompatibel mit PHP-Versionen `8.3.0` - `8.3.4` wegen eines Fehlers im PHP-Speicherberater. Wenn Sie PHP 8.3 verwenden, müssen Sie ein Upgrade auf `8.3.5` oder neuer, um diese Funktion verwenden zu können.
