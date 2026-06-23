---
title: Konfigurieren von nginx für das Zwischenspeichern von Lacken
description: Erfahren Sie, wie Sie Ihren Webserver für die Verwendung des Lackzwischenspeichers für Adobe Commerce konfigurieren. Erfahren Sie mehr über die Konfiguration und Einrichtung von Ports.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# Konfigurieren von nginx für das Zwischenspeichern von Lacken {#configure-web-server-for-varnish-caching}

Wenn Varnish als Vollseiten-Cache vor Adobe Commerce verwendet wird, überwacht Varnish normalerweise den öffentlichen HTTP-Port und leitet Anfragen an nginx an einen nicht standardmäßigen Backend-Port wie 8080 weiter. Aktualisieren Sie die Nginx-Site-Konfiguration für Ihren Commerce-Ursprungs-Server, um den Backend-Port zu überwachen, den Varnish verwenden wird.

{{varnish-config-cloud}}

In den folgenden Abschnitten wird Port 8080 als Beispiel verwendet.

**Ändern Sie den Nginx-Lauschanschluss für den Commerce-Ursprungsserver**:

1. Öffnen Sie die Nginx-Site-Konfiguration für Ihren Adobe Commerce-Ursprungsserver in einem Texteditor.

Der Speicherort hängt von Ihrem Betriebssystem und dem nginx-Layout ab. Zum Beispiel verwendet Ubuntu oft eine Datei unter `/etc/nginx/sites-available/`.

1. Ändern Sie im `server` für die Commerce-Site die `listen`-Direktive vom öffentlichen HTTP-Port auf den Backend-Port, den Varnish verwendet, um nginx zu erreichen.

   Ändern Sie beispielsweise

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   in:

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. Speichern Sie die Datei.

1. Überprüfen Sie die nginx-Konfiguration:

   ```shell
   nginx -t
   ```

1. Nginx neu starten:

   ```shell
   systemctl restart nginx
   ```

## Ändern der Konfiguration des Lacksystems

Nachdem Sie nginx so aktualisiert haben, dass es auf dem Backend-Port lauscht, konfigurieren Sie Varnish so, dass Anfragen an diesen Host und Port weitergeleitet werden. Beispiel:

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### Standard-VCL ändern

In diesem Abschnitt wird beschrieben, wie Sie eine minimale Konfiguration bereitstellen, damit Varnish HTTP-Antwort-Header zurückgibt. Auf diese Weise können Sie überprüfen, ob Varnish funktioniert, bevor Sie die [!DNL Commerce] für die Verwendung von Varnish konfigurieren.

So konfigurieren Sie Lack minimal:

1. `default.vcl`:

   ```shell
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

   Beispiel: nginx ist auf Host 192.0.2.55 installiert und lauscht auf Port 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Wenn Varnish und nginx auf demselben Host ausgeführt werden, empfiehlt Adobe, eine IP-Adresse oder einen Hostnamen und nicht `localhost` zu verwenden.

1. Speichern Sie Ihre Änderungen in `default.vcl` und beenden Sie den Texteditor.

1. Lack neu starten:

   ```shell
   service varnish restart
   ```

Wenn Varnish nicht gestartet werden kann, versuchen Sie, es wie folgt über die Befehlszeile auszuführen:

```shell
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

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Untergeordneten Prozess „Lackieren“ starten:

   Geben Sie bei Aufforderung `start` ein

   Die folgenden Meldungen werden angezeigt, um einen erfolgreichen Start zu bestätigen:

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Melden Sie sich beim Lackierserver an und geben Sie den folgenden Befehl ein:

```shell
netstat -tulpn
```

Achten Sie insbesondere auf die folgende Ausgabe:

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

Oben sehen Sie Lack mit Port 80 und nginx mit Port 8080.

Wenn die Ausgabe für `varnishd` nicht angezeigt wird, stellen Sie sicher, dass „Varnish“ ausgeführt wird.

Siehe [`netstat` Optionen](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installieren der Commerce-Software

Installieren Sie die Commerce-Software, falls noch nicht geschehen. Wenn Sie nach einer Basis-URL gefragt werden, verwenden Sie den Varnish-Host und Port 80 (für Varnish), da Varnish alle eingehenden HTTP-Anfragen empfängt.

Mögliche Fehlermeldung bei der Installation von Commerce:

```text
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

Jetzt können Sie überprüfen, ob Varnish Seiten bereitstellt, indem Sie sich die HTML-Antwort-Header ansehen, die von einer beliebigen Seite zurückgegeben werden.

Bevor Sie Kopfzeilen betrachten können, müssen Sie Commerce für den Entwicklermodus festlegen. Es gibt mehrere Möglichkeiten, dies zu tun, wobei die einfachste die Änderung von `.htaccess` im Commerce-Anwendungsstamm ist. Sie können auch den Befehl [`magento deploy:mode:set`](../cli/set-mode.md) verwenden.

### Festlegen von Commerce für den Entwicklermodus

Um Commerce für den Entwicklermodus festzulegen, verwenden Sie den [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode).

### Das Lackprotokoll ansehen

Stellen Sie sicher, dass Varnish ausgeführt wird, und geben Sie dann den folgenden Befehl auf dem Varnish-Server ein:

```shell
varnishlog
```

Wechseln Sie in einem Webbrowser zu einer beliebigen Commerce-Seite.

Im Eingabeaufforderungsfenster wird eine lange Liste von Antwort-Headern angezeigt. Suchen Sie nach Kopfzeilen wie den folgenden:

```text
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

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

Beispiel:

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Suchen Sie nach Kopfzeilen wie den folgenden:

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
