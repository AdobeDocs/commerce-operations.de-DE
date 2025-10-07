---
title: Erweiterte Lackkonfiguration
description: Erfahren Sie, wie Sie erweiterte Lackfunktionen für Adobe Commerce konfigurieren, einschließlich Konsistenzprüfungen, Anmut- und Sanktionsmodi. Entdecken Sie Techniken zur VCL-Optimierung.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# Erweiterte Lackkonfiguration

Varnish bietet mehrere Funktionen, die verhindern, dass Kunden lange Verzögerungen und Zeitüberschreitungen erleben, wenn der Commerce-Server nicht ordnungsgemäß funktioniert. Diese Funktionen können in der `default.vcl` konfiguriert werden. In diesem Thema werden die Ergänzungen beschrieben, die Commerce in der VCL-Datei (Varnish Configuration Language) bereitstellt, die Sie vom Admin-Team herunterladen.

Siehe [Varnish-Referenzhandbuch](https://varnish-cache.org/docs/index.html) für Details zur Verwendung der Varnish-Konfigurationssprache.

## Konsistenzprüfung

Die Funktion „Konsistenzprüfung der Lackierung“ fragt den Commerce-Server ab, um festzustellen, ob er zeitnah reagiert. Wenn er normal reagiert, werden neue Inhalte nach Ablauf des TTL-Zeitraums (Time to Live) neu generiert. Wenn nicht, stellt Varnish immer veraltete Inhalte bereit.

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

Alle 5 Sekunden ruft diese Konsistenzprüfung das `pub/health_check.php`-Skript auf. Dieses Skript überprüft die Verfügbarkeit des Servers, jeder Datenbank und von Redis (falls installiert). Das Skript muss innerhalb von 2 Sekunden eine Antwort zurückgeben. Wenn das Skript feststellt, dass eine dieser Ressourcen ausgefallen ist, wird ein HTTP-Fehler-Code von 500 zurückgegeben. Wenn dieser Fehler-Code in sechs von zehn Versuchen empfangen wird, wird das Backend als ungesund betrachtet.

Das `health_check.php` befindet sich im `pub`. Wenn Ihr Commerce-Stammordner `pub` ist, ändern Sie den Pfad im `url` von `/pub/health_check.php` in `health_check.php`.

Weitere Informationen finden Sie in der [Varnish-Konsistenzprüfungen](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks) Dokumentation.

## Gnadenmodus

Der Übergangsmodus ermöglicht es Varnish, ein Objekt über seinen TTL-Wert hinaus im Cache zu belassen. Der Lack kann dann den abgelaufenen (veralteten) Inhalt bereitstellen, während er eine neue Version abruft. Dies verbessert den Verkehrsfluss und verringert die Ladezeiten. Es wird in den folgenden Situationen verwendet:

- Wenn das Commerce-Backend fehlerfrei ist, eine Anfrage jedoch länger als gewöhnlich dauert
- Wenn das Commerce-Backend nicht einwandfrei funktioniert.

Die `vcl_hit`-Unterroutine definiert, wie Varnish auf eine Anforderung von Objekten antwortet, die zwischengespeichert wurden.

### Wenn das Commerce-Backend in Ordnung ist

Wenn die Konsistenzprüfungen ergeben, dass das Commerce-Backend fehlerfrei ist, prüft Varnish, ob die Zeit in der Übergangsphase bleibt. Die standardmäßige Übergangsphase beträgt 300 Sekunden, aber ein Händler kann den Wert über den Administrator festlegen, wie in [Konfigurieren von Commerce für die Verwendung von &#x200B;](configure-varnish-commerce.md)) beschrieben. Wenn die Übergangsphase nicht abgelaufen ist, liefert Varnish den veralteten Inhalt und aktualisiert das -Objekt asynchron vom Commerce-Server. Wenn die Übergangsphase abgelaufen ist, stellt Varnish den veralteten Inhalt bereit und aktualisiert das -Objekt synchron vom Commerce-Backend.

Die maximale Zeitspanne, die Varnish für die Bereitstellung eines veralteten Objekts verwendet, ist die Summe aus der Übergangsphase (standardmäßig 300 Sekunden) und dem TTL-Wert (standardmäßig 86400 Sekunden).

Um die standardmäßige Übergangsphase innerhalb der `default.vcl`-Datei zu ändern, bearbeiten Sie die folgende Zeile in der `vcl_hit`-Unterroutine:

```conf
if (obj.ttl + 300s > 0s) {
```

### Wenn das Commerce-Backend nicht einwandfrei funktioniert

Wenn das Commerce-Backend nicht responsiv ist, stellt Varnish veraltete Inhalte aus dem Cache für drei Tage (oder wie in `beresp.grace` definiert) plus die verbleibende TTL (die standardmäßig einen Tag beträgt) bereit, es sei denn, der zwischengespeicherte Inhalt wird manuell bereinigt.

## Saint-Modus

Der Saint-Modus schließt ungesunde Backends für einen konfigurierbaren Zeitraum aus. Daher können ungesunde Backends bei Verwendung von Lack als Lastenausgleich keinen Traffic bereitstellen. Der Saint-Modus kann mit dem Grace-Modus verwendet werden, um eine komplexe Handhabung von ungesunden Backend-Servern zu ermöglichen. Wenn beispielsweise ein Backend-Server fehlerhaft ist, können weitere Zustellversuche an einen anderen Server weitergeleitet werden. Wenn alle anderen Server ausgefallen sind, dann veraltete zwischengespeicherte Objekte bereitstellen. Die Backend-Hosts und Blackout-Perioden des Saint-Modus sind in der `default.vcl`-Datei definiert.

Der Saint-Modus kann auch verwendet werden, wenn Commerce-Instanzen einzeln offline geschaltet werden, um Wartungs- und Upgrade-Aufgaben durchzuführen, ohne die Verfügbarkeit der Commerce-Site zu beeinträchtigen.

### Voraussetzungen für den Sanktionsmodus

Bestimmen Sie einen Computer als primäre Installation. Installieren Sie auf diesem Computer die Hauptinstanz von Commerce, die MySQL-Datenbank und Varnish.

Auf allen anderen Computern muss die Commerce-Instanz Zugriff auf die MySQL-Datenbank des primären Computers haben. Die sekundären Computer sollten außerdem Zugriff auf die Dateien der primären Commerce-Instanz haben.

Statische Dateiversionen können auf allen Computern deaktiviert werden. Diese können Sie vom Administrator unter **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **Entwickler** > **Statische Dateieinstellungen** > **Statische Dateien signieren** = **Nein**.

Schließlich müssen sich alle Commerce-Instanzen im Produktionsmodus befinden. Bevor Varnish gestartet wird, löschen Sie den Cache auf jeder Instanz. Gehen Sie in der Admin zu **System** > Tools > **Cache-Verwaltung** und klicken Sie auf **Magento-Cache leeren**. Sie können auch den folgenden Befehl ausführen, um den Cache zu löschen:

```bash
bin/magento cache:flush
```

### Installation

Saint Mode ist nicht Teil des Hauptpakets Lack. Es handelt sich um eine separat versionierte `vmod`, die heruntergeladen und installiert werden muss. Daher müssen Sie Varnish aus der Quelle neu kompilieren, wie in den [Installationsanweisungen](https://varnish-cache.org/docs/index.html) für Ihre Version von Varnish beschrieben.

Nach dem Neukompilieren können Sie das Modul Saint-Modus installieren. Führen Sie im Allgemeinen die folgenden Schritte aus:

1. Beziehen Sie den Quell-Code aus [Varnish-Modulen](https://github.com/varnish/varnish-modules). Klonen Sie die Git-Version (Master-Version), da die Versionen 0.9.x einen Quellcodefehler enthalten.
1. Erstellen Sie den Quell-Code mit AutoTools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Siehe [Lackmodul-Sammlung](https://github.com/varnish/varnish-modules) für Informationen zur Installation des Saint-Modus-Moduls.

### VCL-Beispieldatei

Das folgende Codebeispiel zeigt den Code, der Ihrer VCL-Datei hinzugefügt werden muss, um den Heiligen Modus zu aktivieren. Platzieren Sie die `import` Anweisungen und `backend` Definitionen am Anfang der Datei.

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
