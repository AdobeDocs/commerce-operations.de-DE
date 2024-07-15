---
title: Erweiterte Varnish-Konfiguration
description: Konfigurieren Sie erweiterte Funktionen für die Färbung, einschließlich Konsistenzprüfung, Grazie und Heiligkeitsmodi.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Erweiterte Varnish-Konfiguration

Varnish bietet mehrere Funktionen, die verhindern, dass Kunden lange Verzögerungen und Timeouts erleben, wenn der Commerce-Server nicht ordnungsgemäß funktioniert. Diese Funktionen können in der Datei `default.vcl` konfiguriert werden. Hier werden die Ergänzungen beschrieben, die Commerce in der VCL-Datei (Varnish Configuration Language) bereitstellt, die Sie vom Administrator herunterladen.

Weitere Informationen zur Verwendung der Varnish-Konfigurationssprache finden Sie im [Varnish Reference Manual](https://varnish-cache.org/docs/index.html) .

## Konsistenzprüfung

Die Funktion &quot;Varnish-Konsistenzprüfung&quot;fragt den Commerce-Server ab, um zu ermitteln, ob er zeitnah reagiert. Wenn sie normal reagiert, werden nach Ablauf des TTL-Zeitraums (Time to Live) neue Inhalte generiert. Wenn nicht, stellt Varnish immer veraltete Inhalte bereit.

Commerce definiert die folgende standardmäßige Konsistenzprüfung:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Alle 5 Sekunden ruft diese Konsistenzprüfung das Skript `pub/health_check.php` auf. Dieses Skript überprüft die Verfügbarkeit des Servers, jeder Datenbank und von Redis (falls installiert). Das Skript muss innerhalb von 2 Sekunden eine Antwort zurückgeben. Wenn das Skript feststellt, dass eine dieser Ressourcen ausgefallen ist, wird ein HTTP-Fehlercode 500 zurückgegeben. Wenn dieser Fehlercode in sechs von zehn Versuchen empfangen wird, gilt das Backend als ungesund.

Das Skript `health_check.php` befindet sich im Verzeichnis `pub` . Wenn Ihr Commerce-Stammordner &quot;`pub`&quot; lautet, müssen Sie den Pfad im Parameter &quot;`url`&quot; von &quot;`/pub/health_check.php`&quot; in &quot;`health_check.php`&quot; ändern.

Weitere Informationen finden Sie in der Dokumentation [Varnish health checks](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks) .

## Übergangmodus

Der Übergangmodus ermöglicht es Varnish, ein Objekt über seinen TTL-Wert hinaus im Cache zu belassen. Varnish kann dann den abgelaufenen (veralteten) Inhalt bereitstellen, während es eine neue Version abruft. Dadurch wird der Traffic-Fluss verbessert und die Ladezeiten verkürzt. Es wird in den folgenden Situationen verwendet:

- Wenn das Commerce-Backend gesund ist, eine Anforderung jedoch länger dauert als normal
- Wenn das Commerce-Backend nicht gesund ist.

Die UnterRoutine &quot;`vcl_hit`&quot; definiert, wie &quot;Varnish&quot;auf eine Anforderung für Objekte reagiert, die zwischengespeichert wurden.

### Wenn das Commerce-Backend gesund ist

Wenn die Konsistenzprüfungen feststellen, dass das Commerce-Backend gesund ist, prüft Varnish, ob die Zeit in der Übergangsphase verbleibt. Die standardmäßige Übergangsphase beträgt 300 Sekunden. Ein Händler kann jedoch den Wert aus dem Admin festlegen, wie unter [Konfigurieren von Commerce für die Verwendung von Varnish](configure-varnish-commerce.md) beschrieben. Wenn die Übergangsphase nicht abgelaufen ist, stellt Varnish den veralteten Inhalt bereit und aktualisiert das Objekt asynchron vom Commerce-Server. Wenn die Übergangsphase abgelaufen ist, stellt Varnish den veralteten Inhalt bereit und aktualisiert das Objekt synchron vom Commerce-Backend.

Die maximale Zeit, die Varnish für ein altes Objekt bereitstellt, ist die Summe der Übergangsphase (standardmäßig 300 Sekunden) und des TTL-Werts (standardmäßig 86400 Sekunden).

Um die standardmäßige Übergangsphase innerhalb der Datei `default.vcl` zu ändern, bearbeiten Sie die folgende Zeile in der UnterRoutine `vcl_hit` :

```conf
if (obj.ttl + 300s > 0s) {
```

### Wenn das Commerce-Backend nicht gesund ist

Wenn das Commerce-Backend nicht responsiv ist, stellt Varnish veraltete Inhalte aus dem Cache drei Tage lang (oder wie in `beresp.grace` definiert) plus die verbleibende TTL (standardmäßig ein Tag) bereit, es sei denn, der zwischengespeicherte Inhalt wird manuell bereinigt.

## Saint-Modus

Der Saint-Modus schließt ungesunde Backends für einen konfigurierbaren Zeitraum aus. Daher können ungesunde Backends keinen Traffic bereitstellen, wenn sie Varnish als Lastenausgleich verwenden. Der SAINT-Modus kann mit dem Übergangmodus verwendet werden, um eine komplexe Handhabung ungesunder Backend-Server zu ermöglichen. Wenn beispielsweise ein Backend-Server ungesund ist, können weitere Versuche an einen anderen Server weitergeleitet werden. Wenn alle anderen Server ausfallen, bedienen Sie veraltete zwischengespeicherte Objekte. Die Backend-Hosts und Blackout-Punkte des Saint-Modus werden in der Datei `default.vcl` definiert.

Der SAINT-Modus kann auch verwendet werden, wenn Commerce-Instanzen einzeln offline genommen werden, um Wartungs- und Aktualisierungsaufgaben durchzuführen, ohne dass sich dies auf die Verfügbarkeit der Commerce-Site auswirkt.

### Voraussetzungen für den Saint-Modus

Benennen Sie eine Maschine als primäre Installation. Installieren Sie auf diesem Computer die Hauptinstanz von Commerce, MySQL-Datenbank und Varnish.

Auf allen anderen Computern muss die Commerce-Instanz Zugriff auf die MySQL-Datenbank des primären Computers haben. Die sekundären Computer sollten auch Zugriff auf die Dateien der primären Commerce-Instanz haben.

Alternativ kann die Versionierung statischer Dateien auf allen Computern deaktiviert werden. Der Zugriff darauf erfolgt über den Administrator unter **Speicher** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler** > **Statische Dateieinstellungen** > **Statische Dateien signieren** = **Nein**.

Schließlich müssen sich alle Commerce-Instanzen im Produktionsmodus befinden. Bevor Varnish gestartet wird, löschen Sie den Cache auf jeder Instanz. Wechseln Sie im Admin zu **System** > Tools > **Cache-Verwaltung** und klicken Sie auf **Magento-Cache leeren**. Sie können auch den folgenden Befehl ausführen, um den Cache zu löschen:

```bash
bin/magento cache:flush
```

### Installation

Der Saint-Modus ist nicht Teil des Varnish-Hauptpakets. Es handelt sich um eine gesonderte Version `vmod`, die heruntergeladen und installiert werden muss. Daher müssen Sie Varnish aus der Quelle neu kompilieren, wie in den [Installationsanweisungen](https://varnish-cache.org/docs/index.html) für Ihre Version von Varnish beschrieben.

Nach der Neukompilierung können Sie das Modul Saint-Modus installieren. Gehen Sie im Allgemeinen wie folgt vor:

1. Rufen Sie den Quellcode von [Varnish modules](https://github.com/varnish/varnish-modules) ab. Klonen Sie die Git-Version (Master-Version), da die Versionen 0.9.x einen Quellcode-Fehler enthalten.
1. Erstellen Sie den Quellcode mit autotools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Informationen zum Installieren des Saint-Modus-Moduls finden Sie unter [Varnish module collection](https://github.com/varnish/varnish-modules) .

### VCL-Beispieldatei

Das folgende Codebeispiel zeigt den Code, der zu Ihrer VCL-Datei hinzugefügt werden muss, um den Farbmodus zu aktivieren. Platzieren Sie die `import` -Anweisungen und die `backend` -Definitionen am Anfang der Datei.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
