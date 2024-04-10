---
title: GraphQL-Anwendungsserver
description: Befolgen Sie diese Anweisungen, um den GraphQL-Anwendungsserver in Ihrer Adobe Commerce-Bereitstellung zu aktivieren.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: a1e548c1b1bffd634e0d5b1df0a77ef65c5997f8
workflow-type: tm+mt
source-wordcount: '1880'
ht-degree: 0%

---


# GraphQL-Anwendungsserver

Mit dem Commerce GraphQL Application Server kann Adobe Commerce den Status bei Commerce GraphQL-API-Anfragen beibehalten. GraphQL Application Server, der auf der Swoole-Erweiterung basiert, arbeitet als Prozess mit Worker-Threads, die die Anforderungsverarbeitung verarbeiten. Durch die Beibehaltung des Status eines Bootstrapping-Programms bei GraphQL-API-Anfragen verbessert GraphQL Application Server die Anforderungsverarbeitung und die Gesamtleistung des Produkts. API-Anfragen werden deutlich effizienter.

GraphQL Application Server ist nur für Adobe Commerce verfügbar. Es steht nicht zur Magento Open Source zur Verfügung. Sie müssen [Senden eines Adobe Commerce-Supports](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) Ticket zur Aktivierung des GraphQL Application Servers in Pro-Projekten.

>[!NOTE]
>
>GraphQL Application Server ist derzeit nicht kompatibel mit [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Kunden mit Adobe Commerce auf Cloud-Infrastruktur, die derzeit verwenden [!DNL AWS S3] für [Fernspeicher](../configuration/remote-storage/cloud-support.md) GraphQL Application Server kann erst verwendet werden, wenn Adobe im Laufe des Jahres 2024 einen Hotfix veröffentlicht.

## Architektur

GraphQL Application Server erhält den Status zwischen Commerce GraphQL-API-Anfragen aufrecht und macht das Bootstrapping überflüssig. Durch die prozessübergreifende gemeinsame Nutzung des Anwendungsstatus werden GraphQL-Anfragen deutlich effizienter, wodurch die Antwortzeiten um bis zu 30 % verkürzt werden.

Das PHP-Ausführungsmodell share-Nothing stellt aus der Perspektive der Latenz eine Herausforderung dar, da jede Anfrage das Bootstrapping des Frameworks erfordert. Dieser Bootstrapping-Prozess umfasst zeitaufwendige Aufgaben wie das Lesen der Konfiguration, das Einrichten des Bootstrap-Prozesses und das Erstellen von Dienstklassenobjekten.

Die Umstellung der Logik für die Anforderungsverarbeitung auf eine Ereignisschleife auf Anwendungsebene scheint die Herausforderung der Optimierung der Anforderungsverarbeitung auf Unternehmensebene zu bewältigen. Durch diesen Ansatz wird das Bootstrapping während des Lebenszyklus der Anforderungsausführung überflüssig.

## Vorteile

GraphQL Application Server ermöglicht es Adobe Commerce, den Status zwischen aufeinander folgenden Commerce-GraphQL-API-Anfragen aufrechtzuerhalten. Durch die anforderungsübergreifende Freigabe des Anwendungsstatus wird die Effizienz von API-Anfragen verbessert, indem der Verarbeitungsaufwand minimiert und die Anfrageverarbeitung optimiert wird. Dadurch kann die Reaktionszeit von GraphQL-Anfragen um bis zu 30 % verkürzt werden.

## Systemanforderungen

Die Ausführung von GraphQL Application Server erfordert Folgendes:

* PHP 8.2 oder höher
* Swoole PHP-Erweiterung v5+ installiert
* Ausreichend RAM und CPU basierend auf der erwarteten Auslastung

## Aktivieren und Bereitstellen in der Cloud-Infrastruktur

Die `ApplicationServer` Modul (`Magento/ApplicationServer/`) aktiviert GraphQL Application Server.

### Pro-Projekte aktivieren

Führen Sie die folgenden Schritte aus, bevor Sie GraphQL Application Server in Pro-Projekten bereitstellen:

1. Bereitstellen von Adobe Commerce in der Cloud-Infrastruktur mithilfe der Cloud-Vorlage aus der [2.4.7-Anwendungsserver-Verzweigung](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen [vereinbar](https://developer.adobe.com/commerce/php/development/components/app-server/) mit GraphQL Application Server.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Passen Sie bei Bedarf die Einstellungen in der Datei &quot;application-server/nginx.conf.sample“ an.
1. Kommentieren Sie den aktiven Abschnitt „Web“ in aus. `project_root/.magento.app.yaml` Datei vollständig.
1. Entfernen Sie den Kommentar für die folgende Konfiguration des Abschnitts „Web“ im `project_root/.magento.app.yaml` Datei, die den GraphQL-Anwendungsserver enthält `start` Befehl.

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

1. Übertragen Sie Ihre Änderungen mit diesem Befehl:

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

1. Bereitstellen von Adobe Commerce in der Cloud-Infrastruktur mithilfe der Cloud-Vorlage aus der [2.4.7-Anwendungsserver-Verzweigung](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Stellen Sie sicher, dass alle Ihre Commerce-Anpassungen und -Erweiterungen mit GraphQL Application Server kompatibel sind.
1. Bestätigen Sie, dass die `CRYPT_KEY` Die Umgebungsvariable wird für Ihre Instanz festgelegt. Sie können den Status dieser Variablen im Cloud-Projektportal (Onboarding-Benutzeroberfläche) überprüfen.
1. Klonen Sie Ihr Commerce Cloud-Projekt.
1. Umbenennen `application-server/.magento/.magento.app.yaml.sample` bis `application-server/.magento/.magento.app.yaml` Ändern Sie bei Bedarf die Einstellungen in „.magento.app.yaml„.
1. Entfernen Sie den Kommentar für die Konfiguration der folgenden Route in der `project_root/.magento/routes.yaml` Umzuleitende Datei `/graphql` Traffic zum GraphQL-Anwendungsserver.

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
>Stellen Sie sicher, dass alle benutzerdefinierten Einstellungen im Stammverzeichnis `.magento.app.yaml` -Dateien werden entsprechend zum migriert `application-server/.magento/.magento.app.yaml` -Datei. Nach dem `application-server/.magento/.magento.app.yaml` -Datei zu Ihrem Projekt hinzugefügt wird, sollten Sie sie zusätzlich zum Stammverzeichnis beibehalten `.magento.app.yaml` -Datei. Wenn Sie beispielsweise [Konfigurieren von RabbitMQ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) oder [Web-Eigenschaften verwalten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) Sie sollten dieselbe Konfiguration zu hinzufügen `application-server/.magento/.magento.app.yaml` Und auch.

### Bereitstellen von Ausgangsprojekten

Nach Abschluss der Aktivierung [Schritte](#before-you-begin-a-cloud-starter-deployment)übertragen Sie Änderungen an Ihr Git-Repository, um GraphQL Application Server bereitzustellen:

```bash
git push
```

### Überprüfen der Aktivierung in Cloud-Projekten

1. Führen Sie eine GraphQL-Abfrage oder Mutation für Ihre Instanz durch, um zu bestätigen, dass die `graphql` Endpunkt ist zugänglich. Beispiel:

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

1. Verwenden Sie SSH, um auf Ihre Cloud-Instanz zuzugreifen. Die `project_root/var/log/application-server.log` sollte für jede GraphQL-Anfrage einen neuen Protokolldatensatz enthalten.

1. Sie können auch überprüfen, ob GraphQL Application Server ausgeführt wird, indem Sie den folgenden Befehl ausführen:

   ```bash
   ps aux|grep php
   ```

   Sie sollten eine sehen `bin/magento server:run` Prozess mit mehreren Threads.

Wenn diese Überprüfungsschritte erfolgreich sind, wird der GraphQL-Anwendungs-Server ausgeführt und bereitgestellt `/graphql` Anfragen.

## Aktivieren von On-Premise-Projekten

Die `ApplicationServer` Modul (`Magento/ApplicationServer/`) aktiviert GraphQL Application Server für GraphQL-APIs.

Wenn GraphQL Application Server lokal ausgeführt wird, muss die Swoole-Erweiterung installiert und die Nginx-Konfigurationsdatei Ihrer Bereitstellung geringfügig geändert werden.

### Voraussetzungen

Führen Sie die folgenden Schritte aus, bevor Sie den aktivieren `ApplicationServer` Modul:

* Konfigurieren von nginx
* Installieren und Konfigurieren der Swoole v5+-Erweiterung

#### Konfigurieren von nginx

Ihre spezifische Commerce-Bereitstellung bestimmt, wie Nginx konfiguriert wird. Im Allgemeinen erhält die Nginx-Konfigurationsdatei standardmäßig den Namen `nginx.conf` und in einem der folgenden Verzeichnisse abgelegt ist: `/usr/local/nginx/conf`, `/etc/nginx`, oder `/usr/local/etc/nginx`. Siehe [Anfängerführer](https://nginx.org/en/docs/beginners_guide.html) für weitere Informationen zur Konfiguration von Nginx.

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

Im folgenden Verfahren wird beschrieben, wie Sie die Swoole-Erweiterung für PHP 8.2 auf OSX-basierten Systemen installieren. Dies ist eine von mehreren Möglichkeiten, die Swoole-Erweiterung zu installieren.

```bash
pecl install swoole
```

Während der Installation zeigt Adobe Commerce Eingabeaufforderungen an, um die Unterstützung für zu aktivieren `openssl`, `mysqlnd`, `sockets`, `http2`, und `postgres`. eintreten in `yes` Für alle Optionen außer `postgres`.

### Überprüfen der Swoole-Installation

Bestätigen Sie, dass die Erweiterung erfolgreich aktiviert wurde:

```bash
php -m | grep swoole
```

### Häufige Fehler bei der Swoole-Installation

Alle Fehler, die während der Swoole-Installation auftreten, treten typischerweise während der `pecl` Installationsphase. Typische Fehler sind fehlende `openssl.h` und `pcre2.h` -Dateien. Um diese Fehler zu beheben, stellen Sie sicher, dass diese beiden Pakete auf Ihrem lokalen System installiert sind.

* Überprüfen Sie den Speicherort von `openssl` durch Ausführen von:

```bash
openssl version -d
```

Dieser Befehl zeigt den Pfad an, bei dem `openssl` ist installiert.

* Überprüfen Sie den Speicherort von `pcre2` durch Ausführen von:

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

So beheben Sie Probleme im Zusammenhang mit `openssl`, Ausführen:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Vergewissern Sie sich, dass Sie den Pfad aus Ihrem lokalen `dev` Umgebung.

#### Bestätigen der Lösung von OpenSSL-bezogenen Problemen

Sie können den folgenden Befehl erneut ausführen, um zu überprüfen, ob Probleme im Zusammenhang mit OpenSSL behoben wurden:

```bash
pecl install swoole
```

#### Beheben von Problemen mit pcre2.h

So beheben Sie Probleme im Zusammenhang mit `pcre2.h`, der Symlink `pcre2.h` Pfad zum installierten PHP-Erweiterungsverzeichnis. Ihre spezifische installierte Version von PHP und `pcr2.h` Bestimmt die jeweilige Version des Befehls, die Sie verwenden sollten.

### Ausführen des GraphQL-Anwendungsservers

Starten Sie den GraphQL-Anwendungsserver:

```bash
bin/magento server:run
```

Dieser Befehl startet einen HTTP-Port auf 9501. Sobald GraphQL Application Server gestartet wird, wird Port 9501 zu einem HTTP-Proxy-Server für alle GraphQL-Abfragen.

So bestätigen Sie, dass der GraphQL-Anwendungsserver in Ihrer Bereitstellung ausgeführt wird:

```bash
ps aux | grep php
```

Zu den zusätzlichen Möglichkeiten, um zu überprüfen, ob GraphQL Application Server ausgeführt wird, gehören:

* Überprüfen Sie die `/var/log/application-server.log` -Datei für Einträge, die sich auf verarbeitete GraphQL-Anfragen beziehen.
* Versuchen Sie, eine Verbindung mit dem HTTP-Port herzustellen, über den der GraphQL-Anwendungsserver ausgeführt wird. Beispiel: `curl -g 'http://localhost:9501/graph`.

### Vergewissern Sie sich, dass GraphQL-Anfragen verarbeitet werden

GraphQL Application Server fügt hinzu `X-Backend` Antwort-Header mit dem Wert `graphql_server` auf jede Anfrage, die er verarbeitet. Um zu überprüfen, ob eine Anfrage vom GraphQL-Anwendungsserver verarbeitet wurde, überprüfen Sie diese Antwort-Kopfzeile.

### Bestätigen der Kompatibilität von Erweiterungen und Anpassungen

Entwickler und Händler von Erweiterungen sollten zunächst überprüfen, ob ihr Erweiterungs- und Anpassungs-Code den unter beschriebenen technischen Richtlinien entspricht [Technische Leitlinien](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Beachten Sie diese Richtlinien bei der Code-Auswertung:

* Dienstklassen (d. h. Klassen, die Verhaltensdaten, aber keine Daten bereitstellen, z. B. `EventManager`) sollte keinen veränderlichen Status haben.
* Zeitliche Kopplung vermeiden.

## GraphQL-Anwendungsserver deaktivieren

Die Verfahren zum Deaktivieren des GraphQL-Anwendungsservers hängen davon ab, ob der Server in einer lokalen oder in einer Cloud-Bereitstellung ausgeführt wird.

### GraphQL Application Server (Cloud) deaktivieren

1. Entfernen Sie alle neuen Dateien und alle anderen Code-Änderungen, die im enthalten waren. `AppServer Enabled` Bestätigung während der Bereitstellungsvorbereitungen.

1. Übertragen Sie Ihre Änderungen mit diesem Befehl:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Stellen Sie diese Änderungen mit diesem Befehl bereit:

   ```bash
   git push
   ```

### GraphQL-Anwendungsserver deaktivieren (lokal)

1. Kommentieren Sie die `/graphql` Abschnitt von `nginx.conf` -Datei, die Sie beim Aktivieren des GraphQL-Anwendungsservers hinzugefügt haben.
1. Starten Sie nginx neu.

Diese Methode zum Deaktivieren des GraphQL-Anwendungsservers kann nützlich sein, um die Leistung schnell zu testen oder zu vergleichen.

### Bestätigen Sie, dass GraphQL Application Server deaktiviert ist

So bestätigen Sie, dass GraphQL-Anfragen von verarbeitet werden `php-fpm` Geben Sie anstelle von GraphQL Application Server diesen Befehl ein: `ps aux | grep php`.

Nachdem der GraphQL-Anwendungsserver deaktiviert wurde:

* `bin/magento server:run` ist inaktiv.
* `var/log/application-server.log` enthält nach GraphQL-Anfragen keine Einträge.

## Integrations- und Funktionstests für GraphQL Application Server

Erweiterungsentwickler können zwei Integrationstests ausführen, um die Kompatibilität der Erweiterungen mit dem GraphQL-Anwendungsserver zu überprüfen: `GraphQlStateTest` und `ResetAfterRequestTest`.

### GraphQLstateTest

`GraphQlStateTest` Erkennt Status in freigegebenen Objekten, die nicht für mehrere Anfragen wiederverwendet werden sollten.

Dieser Test dient der Erkennung von Statusänderungen in Service-Objekten, die vom `ObjectManager`. Der Test führt identische GraphQL-Abfragen zweimal aus und vergleicht den Status des Service-Objekts vor und nach der zweiten Abfrage.

#### GraphQLstateTest-Fehler und potenzielle Behebung

* **Liste kann nicht hinzugefügt, übersprungen oder gefiltert werden**. Wenn ein Fehler auftritt, der darauf hindeutet, dass es nicht sicher ist, eine Liste hinzuzufügen, zu überspringen oder zu filtern, überlegen Sie, ob die Klasse auf abwärtskompatible Weise umgestaltet werden kann, um die Factories der Service-Klassen mit veränderlichem Status zu verwenden.

* **Klasse weist einen veränderlichen Status auf**. Wenn die Klasse selbst einen veränderlichen Status aufweist, versuchen Sie, den Code neu zu schreiben, um diesen Status zu umgehen. Wenn der veränderliche Status aus Leistungsgründen erforderlich ist, implementieren Sie `ResetAfterRequestInterface` und verwenden `_resetState()` , um das Objekt in seinen ursprünglichen Zustand zurückzusetzen.

* **Auf die eingegebene Eigenschaft $x darf vor der Initialisierungsmeldung nicht zugegriffen werden.**. Fehler bei diesem Nachrichtentyp deuten darauf hin, dass die angegebene Eigenschaft nicht vom Konstruktor initialisiert wurde. Dies ist eine Form der zeitlichen Kopplung, die auftritt, weil das Objekt nach seiner anfänglichen Konstruktion nicht mehr verwendet werden kann. Diese Kopplung erfolgt auch dann, wenn die Eigenschaft privat ist, da der Collector, der die Daten aus den Eigenschaften abruft, die PHP-Reflexionsfunktion verwendet. Versuchen Sie in diesem Fall, die Klasse umzustrukturieren, um eine zeitliche Kopplung und einen veränderlichen Zustand zu vermeiden. Wenn diese Umgestaltung den Fehler nicht behebt, können Sie den Eigenschaftstyp in einen Typ ändern, der NULL-Werte zulässt, damit er auf null initialisiert werden kann.  Wenn die Eigenschaft ein Array ist, versuchen Sie, die Eigenschaft als leeres Array zu initialisieren.

Durchgang `GraphQlStateTest` durch Ausführen von `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` Sucht nach allen Klassen, die Folgendes implementieren `ResetAfterRequestInterface` und überprüft, ob der `_resetState()` -Methode den Status eines -Objekts in denselben Zustand zurück, in dem es sich nach der Erstellung durch `ObjectManager`.  Dieser Test erstellt ein Service-Objekt mit `ObjectManager`klont dann dieses Objekt, ruft auf `_resetState()`und vergleicht dann beide Objekte. Der Test ruft keine Methoden zwischen der Objektinstanziierung und auf `_resetState()`Daher wird das Zurücksetzen veränderlicher Status nicht bestätigt. Es findet Probleme, wo ein Fehler oder Tippfehler eintritt `_resetState()` kann den Status auf etwas Anderes setzen, als er ursprünglich war.

#### ResetAfterRequestTest-Fehler und potenzielle Behebung

* **Klasse hat inkonsistente Eigenschaftswerte**. Wenn dieser Test fehlschlägt, überprüfen Sie, ob eine Klasse so geändert wurde, dass das Objekt nach der Erstellung andere Eigenschaftswerte hat als nach dem `_resetState()` Die Methode wird aufgerufen. Wenn die Klasse, an der Sie arbeiten, Folgendes nicht enthält `_resetState()` die Methode selbst, und überprüfen Sie dann die Klassenhierarchie auf eine Oberklasse, die sie implementiert.

* **Auf die eingegebene Eigenschaft $x darf vor der Initialisierungsmeldung nicht zugegriffen werden.**. Dieses Problem tritt auch bei auf. `GraphQlStateTest`.

  Durchgang `ResetAfterRequestTest` Durch Ausführen von: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Funktionstests

Erweiterungsentwickler sollten während der Bereitstellung von GraphQL Anwendungs-Server WebAPI-Funktionstests für GraphQL sowie alle benutzerdefinierten automatisierten oder manuellen Funktionstests für GraphQL ausführen. Diese Funktionstests helfen Entwicklern, potenzielle Fehler oder Kompatibilitätsprobleme zu identifizieren.
