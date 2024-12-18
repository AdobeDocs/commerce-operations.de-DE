---
title: Webserver konfigurieren
description: Erfahren Sie, wie Sie Ihren Webserver für die Verwendung von Varnish konfigurieren.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Konfigurieren des Webservers

Konfigurieren Sie Ihren Webserver so, dass er an einem anderen Port als dem Standard-Port 80 lauscht, da Varnish direkt auf eingehende HTTP-Anfragen reagiert, nicht auf den Webserver.

In den folgenden Abschnitten wird Port 8080 als Beispiel verwendet.

**So ändern Sie den Apache 2.4-Lauschanschluss**:

1. Öffnen Sie `/etc/httpd/conf/httpd.conf` in einem Texteditor.
1. Suchen Sie die `Listen`.
1. Ändern Sie den Wert des Listen-Ports in `8080`. (Sie können einen beliebigen verfügbaren Listen-Port verwenden.)
1. Speichern Sie Ihre Änderungen in `httpd.conf` und beenden Sie den Texteditor.

## Ändern der Konfiguration des Lacksystems

So ändern Sie die Konfiguration des Lacksystems:

1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie Ihre Vanish-Konfigurationsdatei in einem Texteditor:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Stellen Sie den Lacklauschanschluss auf 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Stellen Sie bei Varnish 4.x sicher, dass DAEMON_OPTS den richtigen Listening-Port für den `-a`-Parameter enthält (auch wenn VARNISH_LISTEN_PORT auf den richtigen Wert gesetzt ist):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Speichern Sie Ihre Änderungen in der Varnish-Konfigurationsdatei und beenden Sie den Texteditor.

### Standard-VCL ändern

In diesem Abschnitt wird beschrieben, wie Sie eine minimale Konfiguration bereitstellen, damit Varnish HTTP-Antwort-Header zurückgibt. Auf diese Weise können Sie überprüfen, ob Varnish funktioniert, bevor Sie die [!DNL Commerce] für die Verwendung von Varnish konfigurieren.

So konfigurieren Sie Lack minimal:

1. `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Öffnen Sie `/etc/varnish/default.vcl` in einem Texteditor.
1. Suchen Sie die folgende Strophe:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Ersetzen Sie den Wert von `.host` durch den vollqualifizierten Hostnamen oder die IP-Adresse und den Listen-Port des _Backend_ oder _Ursprungs-Servers_, d. h. der Server, der den Inhalt bereitstellt, beschleunigt Varnish.

   Normalerweise ist dies Ihr Webserver. Siehe [Backend-Server](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) im _Handbuch zum Lackieren_.

1. Ersetzen Sie den Wert von `.port` durch den Überwachungs-Port des Webservers (in diesem Beispiel 8080).

   Beispiel: Apache wird auf Host 192.0.2.55 installiert und Apache überwacht Port 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Wenn Varnish und Apache auf demselben Host laufen, empfiehlt Adobe, eine IP-Adresse oder einen Hostnamen und nicht `localhost` zu verwenden.

1. Speichern Sie Ihre Änderungen in `default.vcl` und beenden Sie den Texteditor.

1. Lack neu starten:

   ```bash
   service varnish restart
   ```

Wenn Varnish nicht gestartet werden kann, versuchen Sie, es wie folgt über die Befehlszeile auszuführen:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Dadurch sollten Fehlermeldungen angezeigt werden.


>[!INFO]
>
>Wenn Varnish nicht als Dienst startet, müssen Sie SELinux-Regeln konfigurieren, um die Ausführung zuzulassen.

## Überprüfen, ob der Lack funktioniert

In den folgenden Abschnitten wird beschrieben, wie Sie sicherstellen können, dass Varnish funktioniert, aber _ohne_ Commerce für die Verwendung konfigurieren können. Sie sollten dies vor der Konfiguration von Commerce ausprobieren.

Führen Sie die in den folgenden Abschnitten beschriebenen Aufgaben in der angegebenen Reihenfolge aus:

- [Anlauflack](#start-varnish)
- [`netstat`](#netstat)

### Anlauflack

Eingeben: `service varnish start`

Wenn Varnish nicht als Service gestartet werden kann, starten Sie es wie folgt über die Befehlszeile:

1. Starten Sie die Lackierungs-CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Untergeordneten Prozess „Lackieren“ starten:

   Geben Sie bei Aufforderung `start` ein

   Die folgenden Meldungen werden angezeigt, um einen erfolgreichen Start zu bestätigen:

   ```
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Melden Sie sich beim Lackierserver an und geben Sie den folgenden Befehl ein:

```bash
netstat -tulpn
```

Achten Sie insbesondere auf die folgende Ausgabe:

```
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

Oben sehen Sie Varnish, das auf Port 80 und Apache, das auf Port 8080 läuft.

Wenn die Ausgabe für `varnishd` nicht angezeigt wird, stellen Sie sicher, dass „Varnish“ ausgeführt wird.

Siehe [`netstat` Optionen](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installieren der Commerce-Software

Installieren Sie die Commerce-Software, falls noch nicht geschehen. Wenn Sie nach einer Basis-URL gefragt werden, verwenden Sie den Varnish-Host und Port 80 (für Varnish), da Varnish alle eingehenden HTTP-Anfragen empfängt.

Mögliche Fehlermeldung bei der Installation von Commerce:

```
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Wenn dieser Fehler auftritt, bearbeiten Sie `default.vcl` und fügen Sie der `backend` wie folgt eine maximale Wartezeit hinzu:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP-Antwortkopfzeilen überprüfen

Jetzt können Sie überprüfen, ob Varnish Seiten bereitstellt, indem Sie sich die von einer beliebigen Seite zurückgegebenen HTML-Antwort-Header ansehen.

Bevor Sie Kopfzeilen betrachten können, müssen Sie Commerce für den Entwicklermodus festlegen. Es gibt mehrere Möglichkeiten, dies zu tun, wobei die einfachste die Änderung von `.htaccess` im Commerce-Anwendungsstamm ist. Sie können auch den Befehl [`magento deploy:mode:set`](../cli/set-mode.md) verwenden.

### Festlegen von Commerce für den Entwicklermodus

Um Commerce für den Entwicklermodus festzulegen, verwenden Sie den [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode).

### Das Lackprotokoll ansehen

Stellen Sie sicher, dass Varnish ausgeführt wird, und geben Sie dann den folgenden Befehl auf dem Varnish-Server ein:

```bash
varnishlog
```

Wechseln Sie in einem Webbrowser zu einer beliebigen Commerce-Seite.

Im Eingabeaufforderungsfenster wird eine lange Liste von Antwort-Headern angezeigt. Suchen Sie nach Kopfzeilen wie den folgenden:

```
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Wenn Kopfzeilen wie diese nicht _werden_ stoppen Sie „Lackieren“, überprüfen Sie Ihre `default.vcl` und versuchen Sie es erneut.

### HTML-Antwortkopfzeilen ansehen

Es gibt mehrere Möglichkeiten, Antwort-Header zu betrachten, einschließlich der Verwendung eines Browser-Plug-ins oder eines Browser-Inspektors.

Im folgenden Beispiel wird `curl` verwendet. Sie können diesen Befehl von jedem Computer aus eingeben, der über HTTP auf den Commerce-Server zugreifen kann.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Beispiel:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Suchen Sie nach Kopfzeilen wie den folgenden:

```
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
