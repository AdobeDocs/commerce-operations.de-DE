---
title: Anwendungsserver für GraphQL-APIs
description: Befolgen Sie diese Anweisungen zum Aktivieren des Anwendungsservers für GraphQL-APIs in Ihrer Adobe Commerce-Bereitstellung.
badgeCoreBeta: label="2.4.7-beta1" type="informative"
source-git-commit: 28bfc54e0f15ba4f4f941acc7d1fb4825702cdf3
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Anwendungsserver für GraphQL-APIs

Der Commerce-Anwendungsserver für GraphQL-APIs ermöglicht Adobe Commerce, den Status zwischen Commerce GraphQL-API-Anfragen beizubehalten, und verkürzt die Bootstrapping-Zeit für jede Anfrage. Durch die gemeinsame Nutzung des Anwendungszustands zwischen den Prozessen werden API-Anfragen deutlich effizienter.

Diese Betaversion von Application Server ist nur für lokale Bereitstellungen verfügbar, die PHP 8.1 oder 8.2 ausführen. Cloud-basierte Implementierungen werden nicht unterstützt. B2B GraphQL-Funktionen werden noch nicht unterstützt. GraphQL-Anfragen funktionieren möglicherweise nicht wie erwartet in lokalen Implementierungen, wenn diese Version des PHP-Anwendungsservers konfiguriert ist.

## Wer kann Application Server verwenden?

Der Anwendungsserver ist nur für lokale Commerce-Bereitstellungen verfügbar.

## Anwendungsserver für GraphQL-APIs aktivieren

Die `ApplicationServer` module (`Magento/ApplicationServer/`) aktiviert den Anwendungsserver für GraphQL-APIs.

Für das Ausführen des Anwendungsservers sind die Installation der Open Source-Erweiterung und eine geringfügige Änderung der Nginx-Konfigurationsdatei Ihrer Bereitstellung erforderlich, damit dieser Anwendungsserver lokal ausgeführt werden kann.

### Bevor Sie beginnen

Führen Sie diese beiden Aufgaben aus, bevor Sie die `ApplicationServer` -Modul:

* Nginx konfigurieren

* Installieren und Konfigurieren der Open Swoole v22-Erweiterung

### Nginx konfigurieren

Ihre spezifische Commerce-Bereitstellung bestimmt, wie Nginx konfiguriert wird. Im Allgemeinen erhält die Nginx-Konfigurationsdatei standardmäßig den Namen `nginx.conf` und wird in einem dieser Verzeichnisse platziert: `/usr/local/nginx/conf`, `/etc/nginx`oder `/usr/local/etc/nginx`. Siehe [Anfängerhandbuch](http://nginx.org/en/docs/beginners_guide.html) für weitere Informationen zur Konfiguration von Nginx.

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

## Beispiel: Installieren von Open Source (OSX)

Dieses Verfahren zeigt, wie die Open Swoole-Erweiterung auf PHP 8.2 für OSX-basierte Systeme installiert wird. Es ist eine von mehreren Möglichkeiten, die Open Swoole-Erweiterung zu installieren.

Sie können sowohl die Open Swoole-Erweiterung für PHP (v22) als auch die Composer-Pakete installieren, die diese Erweiterung mit einem Befehl erfordert.

### Open Swoole installieren

Eingabe:

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Während der Installation zeigt Adobe Commerce die Aufforderung an, den Support für `openssl`, `mysqlnd`, `sockets`, `http2`und `postgres`. Eingabe `yes` für alle Optionen außer `postgres`.

### Installation von Open Swoole bestätigen

Ausführen `php -m | grep openswoole` , um zu bestätigen, dass die Erweiterung erfolgreich aktiviert wurde.

### Häufige Fehler bei der Open Swoole-Installation

Fehler, die während der Open Swoolinstallation auftreten, treten normalerweise während der `pecl` Installationsphase. Typische Fehler beinhalten fehlende `openssl.h` und `pcre2.h` Dateien. Um diese Fehler zu beheben, stellen Sie sicher, dass diese beiden Pakete in Ihrem lokalen System installiert sind.

* Standort überprüfen `openssl` durch Ausführen:

```bash
openssl version -d
```

Dieser Befehl zeigt den Pfad, in dem `openssl` installiert ist.

* Standort überprüfen `pcre2` durch Ausführen:

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

Beheben von Problemen im Zusammenhang mit `openssl`, ausführen:

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

