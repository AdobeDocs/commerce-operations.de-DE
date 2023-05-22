---
title: Erweiterte Varnish-Konfiguration
description: Konfigurieren Sie erweiterte Funktionen für die Färbung, einschließlich Konsistenzprüfung, Grazie und Heiligkeitsmodi.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# Erweiterte Varnish-Konfiguration

Varnish bietet mehrere Funktionen, die verhindern, dass Kunden lange Verzögerungen und Timeouts erleben, wenn der Commerce-Server nicht ordnungsgemäß funktioniert. Diese Funktionen können im Abschnitt `default.vcl` -Datei. Hier werden die von Commerce in der VCL-Datei (Varnish Configuration Language) bereitgestellten Ergänzungen beschrieben, die Sie vom Administrator herunterladen können.

Siehe [Varnish-Referenzhandbuch](https://varnish-cache.org/docs/6.3/reference/index.html) für Details zur Verwendung der Varnish-Konfigurationssprache.

## Konsistenzprüfung

Die Funktion &quot;Varnish-Konsistenzprüfung&quot;fragt den Commerce-Server ab, um festzustellen, ob er zeitnah reagiert. Wenn sie normal reagiert, werden nach Ablauf des TTL-Zeitraums (Time to Live) neue Inhalte generiert. Wenn nicht, stellt Varnish immer veraltete Inhalte bereit.

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

Alle 5 Sekunden ruft diese Konsistenzprüfung die `pub/health_check.php` Skript. Dieses Skript überprüft die Verfügbarkeit des Servers, jeder Datenbank und von Redis (falls installiert). Das Skript muss innerhalb von 2 Sekunden eine Antwort zurückgeben. Wenn das Skript feststellt, dass eine dieser Ressourcen ausgefallen ist, wird ein HTTP-Fehlercode 500 zurückgegeben. Wenn dieser Fehlercode in sechs von zehn Versuchen empfangen wird, gilt das Backend als ungesund.

Die `health_check.php` Das Skript befindet sich im `pub` Verzeichnis. Wenn Ihr Commerce-Stammordner `pub`, dann vergewissern Sie sich, dass Sie den Pfad im `url` Parameter aus `/pub/health_check.php` nach `health_check.php`.

Weitere Informationen finden Sie unter [Tiergesundheitskontrollen](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) Dokumentation.

## Übergangmodus

Der Übergangmodus ermöglicht es Varnish, ein Objekt über seinen TTL-Wert hinaus im Cache zu belassen. Varnish kann dann den abgelaufenen (veralteten) Inhalt bereitstellen, während es eine neue Version abruft. Dadurch wird der Traffic-Fluss verbessert und die Ladezeiten verkürzt. Es wird in den folgenden Situationen verwendet:

- Wenn das Commerce-Backend gesund ist, eine Anforderung jedoch länger dauert als normal
- Wenn das Commerce-Backend nicht gesund ist.

Die `vcl_hit` subroutinemäßig definiert, wie Varnish auf eine Anforderung für Objekte reagiert, die zwischengespeichert wurden.

### Wenn das Commerce-Backend gesund ist

Wenn die Konsistenzprüfungen feststellen, dass das Commerce-Backend gesund ist, prüft Varnish, ob die Zeit in der Übergangsphase verbleibt. Die standardmäßige Übergangsphase beträgt 300 Sekunden, ein Händler kann den Wert jedoch vom Administrator festlegen, wie unter [Konfigurieren von Commerce für die Verwendung von Varnish](configure-varnish-commerce.md). Wenn die Übergangsphase nicht abgelaufen ist, stellt Varnish den veralteten Inhalt bereit und aktualisiert das Objekt asynchron vom Commerce-Server. Wenn die Übergangsphase abgelaufen ist, stellt Varnish den veralteten Inhalt bereit und aktualisiert das Objekt synchron vom Commerce-Backend.

Die maximale Zeit, die Varnish für ein altes Objekt bereitstellt, ist die Summe der Übergangsphase (standardmäßig 300 Sekunden) und des TTL-Werts (standardmäßig 86400 Sekunden).

So ändern Sie die standardmäßige Übergangsphase von innerhalb der `default.vcl` die folgende Zeile in der Datei `vcl_hit` Subroutine:

```conf
if (obj.ttl + 300s > 0s) {
```

### Wenn das Commerce-Backend nicht gesund ist

Wenn das Commerce-Backend nicht responsiv ist, stellt Varnish veraltete Inhalte aus dem Cache drei Tage lang bereit (oder wie in `beresp.grace`) und die verbleibende TTL (die standardmäßig einen Tag beträgt), es sei denn, der zwischengespeicherte Inhalt wird manuell bereinigt.

## Saint-Modus

Der Saint-Modus schließt ungesunde Backends für einen konfigurierbaren Zeitraum aus. Daher können ungesunde Backends keinen Traffic bereitstellen, wenn sie Varnish als Lastenausgleich verwenden. Der SAINT-Modus kann mit dem Übergangmodus verwendet werden, um eine komplexe Handhabung ungesunder Backend-Server zu ermöglichen. Wenn beispielsweise ein Backend-Server ungesund ist, können weitere Versuche an einen anderen Server weitergeleitet werden. Wenn alle anderen Server ausfallen, bedienen Sie veraltete zwischengespeicherte Objekte. Die Backend-Hosts und Blackout-Punkte für den St-Modus werden im Abschnitt `default.vcl` -Datei.

Der SAINT-Modus kann auch verwendet werden, wenn Commerce-Instanzen einzeln offline genommen werden, um Wartungs- und Aktualisierungsaufgaben durchzuführen, ohne die Verfügbarkeit der Commerce-Site zu beeinträchtigen.

### Voraussetzungen für den Saint-Modus

Benennen Sie eine Maschine als primäre Installation. Installieren Sie auf diesem Computer die Hauptinstanz von Commerce, mySQL-Datenbank und Varnish.

Auf allen anderen Computern muss die Commerce-Instanz Zugriff auf die mySQL-Datenbank des primären Computers haben. Die sekundären Maschinen sollten auch Zugriff auf die Dateien der primären Commerce-Instanz haben.

Alternativ kann die Versionierung statischer Dateien auf allen Computern deaktiviert werden. Der Zugriff darauf erfolgt über den Administrator unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler** > **Einstellungen für statische Dateien** > **Statische Dateien unterschreiben** = **Nein**.

Schließlich müssen sich alle Commerce-Instanzen im Produktionsmodus befinden. Bevor Varnish gestartet wird, löschen Sie den Cache auf jeder Instanz. Navigieren Sie im Admin zu **System** > Tools > **Cacheverwaltung** und klicken Sie auf **Magento-Cache leeren**. Sie können auch den folgenden Befehl ausführen, um den Cache zu löschen:

```bash
bin/magento cache:flush
```

### Installation

Der Saint-Modus ist nicht Teil des Varnish-Hauptpakets. Es handelt sich um eine separate Version `vmod` die heruntergeladen und installiert werden müssen. Daher sollten Sie Varnish aus der Quelle neu kompilieren, wie in den folgenden Artikeln beschrieben:

- [Installieren von Varnish 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Installieren von Varnish 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

Nach der Neukompilierung können Sie das Modul Saint-Modus installieren. Gehen Sie im Allgemeinen wie folgt vor:

1. Quellcode abrufen von [Varnish-Module](https://github.com/varnish/varnish-modules). Klonen Sie die Git-Version (Übergeordnete Version), da die Versionen 0.9.x einen Quellcode-Fehler enthalten.
1. Erstellen Sie den Quellcode mit autotools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Siehe [Varnish-Modulsammlung](https://github.com/varnish/varnish-modules) für Informationen zur Installation des Moduls Saint-Modus.

### VCL-Beispieldatei

Das folgende Codebeispiel zeigt den Code, der zu Ihrer VCL-Datei hinzugefügt werden muss, um den Farbmodus zu aktivieren. Platzieren Sie die `import` und `backend` -Definitionen am Anfang der Datei.

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
