---
title: X-Frame-Options-Kopfzeile
description: Verwenden Sie X-Frame-Options zum Steuern von Seiten-Renderings.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# X-Frame-Options-Kopfzeile

So verhindern Sie [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) Exploits verwenden, haben wir eine Option zur Verwendung der [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP-Anfrage-Header in -Anfragen an Ihre Storefront.

Die `X-Frame-Options` -Kopfzeile ermöglicht Ihnen anzugeben, ob ein Browser eine Seite in einem `<frame>`, `<iframe>`oder `<object>` wie folgt:

- `DENY`: Seite kann nicht in einem Frame angezeigt werden.
- `SAMEORIGIN`: (Standard) Die Seite kann nur in einem Frame mit derselben Herkunft wie die Seite selbst angezeigt werden.

>[!WARNING]
>
>Die `ALLOW-FROM <uri>` -Option ist veraltet, da sie von Commerce-unterstützten Browsern nicht mehr unterstützt wird. Siehe [Browserkompatibilität](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Aus Sicherheitsgründen empfiehlt Adobe dringend, die Commerce-Storefront nicht in einem Frame auszuführen.

## Implementierung `X-Frame-Options`

Legen Sie einen Wert für `X-Frame-Options` in `<magento_root>/app/etc/env.php`. Der Standardwert lautet:

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>Es ist sicherer, die `env.php` als einen Wert in Admin festzulegen.

## Überprüfen Sie die Einstellung für `X-Frame-Options`

Um Ihre Einstellung zu überprüfen, zeigen Sie HTTP-Header auf jeder Storefront-Seite an. Dazu gibt es mehrere Möglichkeiten, einschließlich der Verwendung eines Webbrowser-Inspektors.

Im folgenden Beispiel wird curl verwendet, das Sie von jedem Computer aus ausführen können, der über das HTTP-Protokoll eine Verbindung zu Ihrem Commerce-Server herstellen kann.

Verwenden Sie den folgenden Befehl:

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

Suchen Sie nach `X-Frame-Options` -Wert in den Kopfzeilen.
