---
title: Verhindern von Clickjacking-Exploits
description: Verhindern Sie Clickjacking-Exploits, indem Sie die Kopfzeile "X-Frame-Options"verwenden, um Seitenrenderungen zu steuern.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Verhindern von Clickjacking-Exploits

Verhindern [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) Exploits durch Einbeziehung der [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP-Anfrage-Header in -Anfragen an Ihre Storefront.

Die `X-Frame-Options` -Kopfzeile ermöglicht Ihnen anzugeben, ob ein Browser eine Seite in einem `<frame>`, `<iframe>`oder `<object>` wie folgt:

- `DENY`: Seite kann nicht in einem Frame angezeigt werden.
- `SAMEORIGIN`: (Standard) Seite kann nur in einem Frame mit demselben Ursprung wie die Seite selbst angezeigt werden.

>[!WARNING]
>
>Die `ALLOW-FROM <uri>` -Option ist veraltet, da sie von Commerce-unterstützten Browsern nicht mehr unterstützt wird. Siehe [Browserkompatibilität](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Aus Sicherheitsgründen empfiehlt Adobe dringend, die Commerce-Storefront nicht in einem Frame auszuführen.

## Implementierung `X-Frame-Options`

Legen Sie einen Wert für `X-Frame-Options` in `<project-root>/app/etc/env.php`. Der Standardwert wird wie folgt festgelegt:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Stellen Sie für alle Änderungen am `env.php` -Datei zu aktivieren.

>[!TIP]
>
>Es ist sicherer, die `env.php` als einen Wert in Admin festzulegen.

## Überprüfen Sie die Einstellung für `X-Frame-Options`

Um Ihre Einstellung zu überprüfen, sehen Sie sich die HTTP-Header auf jeder Storefront-Seite an. Dazu gibt es mehrere Möglichkeiten, einschließlich der Verwendung eines Webbrowser-Inspektors.

Im folgenden Beispiel wird curl verwendet, das Sie von jedem Computer aus ausführen können, der über das HTTP-Protokoll eine Verbindung zu Ihrem Commerce-Server herstellen kann.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Suchen Sie nach `X-Frame-Options` -Wert in den Kopfzeilen.
