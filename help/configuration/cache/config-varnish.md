---
title: Konfigurieren und Verwenden von Varnish
description: Erfahren Sie, wie Varnish Dateien speichert und den HTTP-Traffic verbessert.
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# Konfigurieren von Varnish

[Varnish Cache] ist ein Open-Source-Beschleuniger für Webanwendungen (auch als _HTTP-Beschleuniger_ oder _Zwischenspeichern von HTTP-Reverse-Proxy_). Variabel speichert (oder speichert) Dateien oder Dateifragmente im Speicher, was es Varnish ermöglicht, die Antwortzeit und den Verbrauch an Netzwerkbandbreite bei zukünftigen, äquivalenten Anforderungen zu reduzieren. Im Gegensatz zu Webservern wie Apache und Nginx wurde Varnish ausschließlich für die Verwendung mit dem HTTP-Protokoll entwickelt.

[Systemanforderungen](../../installation/system-requirements.md) listet die unterstützten Versionen von Varnish auf.

>[!WARNING]
>
>Wir _dringend empfehlen_ Sie verwenden Varnish in der Produktion. Die integrierte vollständige Zwischenspeicherung - entweder im Dateisystem oder [Datenbank](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)—ist viel langsamer als Varnish und Varnish wurde entwickelt, um den HTTP-Traffic zu beschleunigen.

Weitere Informationen zu Varnish finden Sie unter:

- [Der große arnistische Bild]
- [Varnish-Startoptionen]
- [Varianten und Website-Leistung]

## Varnisches Topologiediagramm

Die folgende Abbildung zeigt eine grundlegende Ansicht von Varnish in Ihrer Commerce-Topologie.

![Grundlegendes Absatzdiagramm](../../assets/configuration/varnish-basic.png)

In der obigen Abbildung führen HTTP-Anfragen von Benutzern über das Internet zu zahlreichen Anfragen für CSS, HTML, JavaScript und Bilder (gemeinsam als _Assets_). Varnish befindet sich vor dem Webserver und sendet diese Anfragen an den Webserver.

Wenn der Webserver Assets zurückgibt, werden zwischenspeicherbare Assets in &quot;Varnish&quot;gespeichert. Alle nachfolgenden Anfragen für diese Assets werden von Varnish erfüllt (d. h. die Anfragen erreichen den Webserver nicht). Varnish gibt zwischengespeicherten Inhalt extrem schnell zurück. Die Ergebnisse sind schnellere Antwortzeiten, um den Inhalt an Benutzer zurückzugeben, und eine geringere Anzahl von Anforderungen, die von Commerce erfüllt werden müssen.

Von Varnish zwischengespeicherte Assets laufen in einem konfigurierbaren Intervall ab oder werden durch neuere Versionen derselben Assets ersetzt. Sie können den Cache auch manuell löschen, indem Sie entweder den Administrator oder die [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) Befehl.

## Prozessübersicht

In diesem Thema wird erläutert, wie Varnish zunächst mit einer minimalen Anzahl von Parametern installiert und getestet werden kann, ob es funktioniert. Exportieren Sie dann eine Varnish-Konfiguration vom Commerce Admin und testen Sie sie erneut.

Der Prozess kann wie folgt zusammengefasst werden:

1. Installieren Sie Varnish und testen Sie es, indem Sie auf eine beliebige Commerce-Seite zugreifen, um zu sehen, ob HTTP-Antwort-Header vorliegen, die darauf hinweisen, dass Varnish funktioniert.
1. Installieren Sie die Commerce-Software und erstellen Sie mit dem Admin eine Varnish-Konfigurationsdatei.
1. Ersetzen Sie Ihre vorhandene Varnish-Konfigurationsdatei durch die vom Administrator erstellte.
1. Testen Sie alles erneut.

   Wenn nichts in Ihrer `<magento_root>/var/page_cache` Verzeichnis, haben Sie Varnish erfolgreich mit Commerce konfiguriert!

>[!NOTE]
>
>- Sofern nicht angegeben, müssen Sie alle in diesem Thema behandelten Befehle als Benutzer mit `root` -Berechtigungen.
>
>- Dieses Thema wurde für Varnish auf CentOS und Apache 2.4 geschrieben. Wenn Sie Varnish in einer anderen Umgebung einrichten, können einige Befehle unterschiedlich sein. Weitere Informationen finden Sie in der Dokumentation zu Varnish .

## Bekannte Probleme

Wir kennen die folgenden Probleme mit Varnish:

- [Varnish unterstützt SSL nicht]

  Verwenden Sie alternativ SSL-Terminierung oder einen SSL-Terminierungsproxy.

- Wenn Sie den Inhalt der `<magento_root>/var/cache` Verzeichnis, müssen Sie Varnish neu starten.

- Mögliche Fehler bei der Installation von Commerce:

  ```terminal
  Error 503 Service Unavailable
  Service Unavailable
  XID: 303394517
  Varnish cache server
  ```

  Wenn dieser Fehler auftritt, bearbeiten Sie `default.vcl` und fügen Sie dem `backend` Stanza wie folgt:

  ```conf
  backend default {
      .host = "127.0.0.1";
      .port = "8080";
      .first_byte_timeout = 600s;
  }
  ```

## Übersicht über die Zwischenspeicherung in verschiedenen Sprachen

Die Varnish-Zwischenspeicherung funktioniert mit Commerce mithilfe von:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) aus dem Magento 2 GitHub-Repository
- `.htaccess` verteilte Konfigurationsdatei für Apache mit Commerce
- `default.vcl` Konfiguration der mithilfe der Variablen [Admin](../cache/configure-varnish-commerce.md)

>[!INFO]
>
>Dieses Thema behandelt nur die Standardoptionen in der vorherigen Liste. Es gibt viele andere Möglichkeiten, die Zwischenspeicherung in komplexen Szenarien zu konfigurieren (z. B. mithilfe eines Content Delivery Network). Diese Methoden werden nicht in dieses Handbuch einbezogen.

Bei der ersten Browser-Anforderung werden zwischenspeicherbare Assets aus &quot;Varnish&quot;an den Client-Browser gesendet und im Browser zwischengespeichert.

Darüber hinaus verwendet Varnish ein Entity-Tag (ETag) für statische Assets. Das ETag bietet eine Möglichkeit, festzustellen, wann sich statische Dateien auf dem Server ändern. Daher werden statische Assets an den Client gesendet, wenn sie sich auf dem Server ändern - entweder bei einer neuen Anforderung eines Browsers oder beim Aktualisieren des Browser-Caches durch den Client, normalerweise durch Drücken von F5 oder Strg+F5.

Weitere Informationen finden Sie in den folgenden Abschnitten.

## Zwischenspeicherung nach Browser-Anforderung

In diesem Abschnitt wird mithilfe eines Browser-Inspektors gezeigt, wie Assets in der ersten Anforderung an den Browser gesendet und anschließend aus dem lokalen Browser-Cache geladen werden.

### Erste Browser-Anfrage

`nginx.conf.sample` und `.htaccess` bietet Optionen für die Client-Zwischenspeicherung. Wenn die erste Anforderung von einem Browser für ein zwischenspeicherbares Objekt erfolgt, stellt Varnish es an den Client bereit.

Die folgende Abbildung zeigt ein Beispiel für die Verwendung eines Browser-Inspektors:

![Wenn zum ersten Mal eine Anfrage für ein zwischenspeicherbares Objekt gestellt wird, stellt Varnish es an den Browser bereit](../../assets/configuration/varnish-apache-first-visit.png)

Das obige Beispiel zeigt eine Anforderung für die Hauptseite der Storefront (`m2_ce_my`). CSS- und JavaScript-Assets werden im Client-Browser zwischengespeichert.

>[!NOTE]
>
>Die meisten statischen Assets verfügen über einen HTTP-Statuscode 200 (OK), der angibt, dass das Asset vom Server abgerufen wurde.

### Zweite Browser-Anfrage

Wenn derselbe Browser dieselbe Seite erneut anfordert, werden diese Assets aus dem lokalen Browser-Cache bereitgestellt, wie in der folgenden Abbildung dargestellt.

![Wenn das nächste Mal dasselbe Objekt angefordert wird, werden Assets aus dem lokalen Browser-Cache geladen](../../assets/configuration/varnish-apache-second-visit.png)

Beachten Sie den Unterschied in der Antwortzeit zwischen der ersten und der zweiten Anforderung. Auch hier haben statische Assets einen Antwortcode von 200 (OK), da sie zum ersten Mal aus dem lokalen Cache bereitgestellt werden.

## Wie Commerce Etag verwendet

Das folgende Beispiel zeigt Antwort-Header für ein bestimmtes statisches Asset.

![Das ETag erleichtert die Bestimmung, ob ein statisches Asset geändert wurde oder nicht](../../assets/configuration/varnish-etag.png)

`calendar.css` verfügt über einen ETag-Antwortheader, was bedeutet, dass die CSS-Datei im Clientbrowser mit der Datei auf dem Server verglichen werden kann.

Darüber hinaus werden statische Assets mit dem HTTP-Statuscode 304 (Nicht geändert) zurückgegeben, wie in der folgenden Abbildung dargestellt.

![Der HTTP-Antwortcode 304 (Nicht geändert) zeigt an, dass das statische Asset im lokalen Cache mit dem auf dem Server identisch ist](../../assets/configuration/varnish-304.png)

Der Statuscode 304 tritt auf, da der Benutzer seinen lokalen Cache invalidiert hat und sich der Inhalt auf dem Server nicht geändert hat. Aufgrund des 304-Status-Codes wird das statische Asset _content_ wird nicht übertragen; nur HTTP-Header werden in den Browser heruntergeladen.

Wenn sich der Inhalt auf dem Server ändert, lädt der Client das statische Asset mit einem HTTP-Statuscode 200 (OK) und einem neuen ETag herunter.

<!-- Link Definitions -->

[Der große arnistische Bild]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Varnish Cache]: https://varnish-cache.org
[Varnish-Startoptionen]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Varianten und Website-Leistung]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Varnish unterstützt SSL nicht]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
