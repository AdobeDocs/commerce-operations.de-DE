---
title: Webserver konfigurieren
description: Erfahren Sie, wie Sie Ihren Webserver für die Verwendung mit Varnish konfigurieren.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Webserver konfigurieren

Konfigurieren Sie Ihren Webserver so, dass er einen anderen Anschluss als den standardmäßigen Port 80 überwacht, da Varnish direkt auf eingehende HTTP-Anforderungen antwortet, nicht auf den Webserver.

In den folgenden Abschnitten wird als Beispiel Port 8080 verwendet.

**So ändern Sie den Apache 2.4-Überwachungsanschluss**:

1. Öffnen Sie `/etc/httpd/conf/httpd.conf` in einem Texteditor.
1. Suchen Sie die Anweisung `Listen` .
1. Ändern Sie den Wert des Überwachungsanschlusses in `8080`. (Sie können jeden verfügbaren Überwachungsanschluss verwenden.)
1. Speichern Sie Ihre Änderungen in `httpd.conf` und beenden Sie den Texteditor.

## Ändern der Konfiguration des Varnish-Systems

So ändern Sie die Varnish-Systemkonfiguration:

1. Als Benutzer mit `root` -Berechtigungen öffnen Sie die Konfigurationsdatei &quot;Vanish&quot;in einem Texteditor:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Setzen Sie den Varnish-Listener-Port auf 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Stellen Sie für Varnish 4.x sicher, dass DAEMON_OPTS den richtigen Listening-Port für den Parameter `-a` enthält (auch wenn VARNISH_LISTEN_PORT auf den richtigen Wert gesetzt ist):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Speichern Sie Ihre Änderungen in der Varnish-Konfigurationsdatei und beenden Sie den Texteditor.

### Ändern der standardmäßigen VCL

In diesem Abschnitt wird beschrieben, wie Sie eine minimale Konfiguration bereitstellen, sodass Varnish HTTP-Antwortheader zurückgibt. Auf diese Weise können Sie überprüfen, ob Varnish funktioniert, bevor Sie die [!DNL Commerce]-Anwendung für die Verwendung von Varnish konfigurieren.

So konfigurieren Sie Varnish minimal:

1. Sichern Sie `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Öffnen Sie `/etc/varnish/default.vcl` in einem Texteditor.
1. Suchen Sie den folgenden Stanza:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Ersetzen Sie den Wert von `.host` durch den vollständig qualifizierten Hostnamen oder die IP-Adresse und überwachen Sie den Port des Varnish _backend_ oder _origin server_. Das heißt, der Server, der den Inhalt bereitstellt, beschleunigt sich.

   Normalerweise ist dies Ihr Webserver. Siehe [Backend-Server](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) im _Varnish-Handbuch_.

1. Ersetzen Sie den Wert von `.port` durch den Listener Port des Webservers (in diesem Beispiel 8080).

   Beispiel: Apache wird auf dem Host 192.0.2.55 installiert und Apache wartet auf Port 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Wenn Varnish und Apache auf demselben Host ausgeführt werden, empfiehlt Adobe die Verwendung einer IP-Adresse oder eines Hostnamens und nicht von `localhost`.

1. Speichern Sie Ihre Änderungen in `default.vcl` und beenden Sie den Texteditor.

1. Varnish neu starten:

   ```bash
   service varnish restart
   ```

Wenn Varnish nicht gestartet werden kann, führen Sie es wie folgt über die Befehlszeile aus:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Dadurch sollten Fehlermeldungen angezeigt werden.


>[!INFO]
>
>Wenn Varnish nicht als Dienst startet, müssen Sie SELinux-Regeln so konfigurieren, dass sie ausgeführt werden können.

## Überprüfen, ob Varnish funktioniert

In den folgenden Abschnitten wird beschrieben, wie Sie überprüfen können, ob Varnish funktioniert, aber _ohne_, dass Commerce für die Verwendung konfiguriert ist. Versuchen Sie es, bevor Sie Commerce konfigurieren.

Führen Sie die in den folgenden Abschnitten beschriebenen Aufgaben in der angegebenen Reihenfolge aus:

- [Start Varnish](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Start Varnish

Eingabe: `service varnish start`

Wenn Varnish nicht als Dienst gestartet werden kann, starten Sie ihn wie folgt über die Befehlszeile:

1. Starten Sie die Varnish-CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Starten Sie den untergeordneten Varnish-Prozess:

   Geben Sie bei Aufforderung `start` ein.

   Die folgenden Meldungen werden angezeigt, um einen erfolgreichen Start zu bestätigen:

   ```
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Melden Sie sich beim Varnish-Server an und geben Sie den folgenden Befehl ein:

```bash
netstat -tulpn
```

Suchen Sie insbesondere nach der folgenden Ausgabe:

```
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

Die obige Abbildung zeigt Varnish, das auf Port 80 ausgeführt wird, und Apache, das auf Port 8080 ausgeführt wird.

Wenn die Ausgabe für `varnishd` nicht angezeigt wird, stellen Sie sicher, dass Varnish ausgeführt wird.

Siehe [`netstat` options](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installieren der Commerce-Software

Installieren Sie die Commerce-Software, falls noch nicht geschehen. Wenn Sie zur Eingabe einer Basis-URL aufgefordert werden, verwenden Sie den &quot;Varnish&quot;-Host und Port 80 (für &quot;Varnish&quot;), da Varnish alle eingehenden HTTP-Anforderungen erhält.

Mögliche Fehler bei der Installation von Commerce:

```
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Wenn dieser Fehler auftritt, bearbeiten Sie `default.vcl` und fügen Sie dem `backend` -Stanza eine Zeitüberschreitung wie folgt hinzu:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Überprüfen von HTTP-Antwortheadern

Jetzt können Sie überprüfen, ob Varnish Seiten bereitstellt, indem Sie sich die HTML-Antwort-Header ansehen, die von einer beliebigen Seite zurückgegeben werden.

Bevor Sie Kopfzeilen anzeigen können, müssen Sie Commerce für den Entwicklermodus festlegen. Es gibt mehrere Möglichkeiten, dies zu tun. Am einfachsten ist es, `.htaccess` im Commerce-Anwendungsstamm zu ändern. Sie können auch den Befehl [`magento deploy:mode:set`](../cli/set-mode.md) verwenden.

### Commerce für den Entwicklermodus festlegen

Verwenden Sie den Befehl [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) , um Commerce für den Entwicklermodus festzulegen.

### Sehen Sie sich das Varnish-Protokoll an

Vergewissern Sie sich, dass Varnish ausgeführt wird, und geben Sie dann den folgenden Befehl auf dem Varnish-Server ein:

```bash
varnishlog
```

Navigieren Sie in einem Webbrowser zu einer beliebigen Commerce-Seite.

Eine lange Liste von Antwortheadern wird in Ihrem Eingabeaufforderungsfenster angezeigt. Suchen Sie nach Kopfzeilen wie den folgenden:

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

Wenn Kopfzeilen wie diese _nicht_ anzeigen, stoppen Sie &quot;Varnish&quot;, überprüfen Sie Ihre `default.vcl` und versuchen Sie es erneut.

### HTML-Antwort-Header

Es gibt mehrere Möglichkeiten, Antwortheader anzuzeigen, einschließlich der Verwendung eines Browser-Plug-ins oder eines Browser-Inspektors.

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
