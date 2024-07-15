---
title: Verhindern von Clickjacking-Exploits
description: Verhindern Sie Clickjacking-Exploits, indem Sie die Kopfzeile "X-Frame-Options"verwenden, um Seitenrenderungen zu steuern.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Verhindern von Clickjacking-Exploits

Verhindern Sie [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) -Exploits, indem Sie den HTTP-Anforderungsheader [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) in Anfragen an Ihre Storefront einbeziehen.

Mit der Kopfzeile `X-Frame-Options` können Sie angeben, ob ein Browser eine Seite in einem `<frame>`, `<iframe>` oder `<object>` wie folgt rendern darf:

- `DENY`: Die Seite kann nicht in einem Frame angezeigt werden.
- `SAMEORIGIN`: (Standard) Die Seite kann nur in einem Frame mit derselben Herkunft wie die Seite selbst angezeigt werden.

>[!WARNING]
>
>Die Option `ALLOW-FROM <uri>` wird nicht mehr unterstützt, da sie von Commerce unterstützte Browser nicht mehr unterstützen. Siehe [Browserkompatibilität](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Aus Sicherheitsgründen empfiehlt Adobe dringend, die Commerce-Storefront nicht in einem Frame auszuführen.

## Implementieren von `X-Frame-Options`

Legen Sie einen Wert für `X-Frame-Options` in `<project-root>/app/etc/env.php` fest. Der Standardwert wird wie folgt festgelegt:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Stellen Sie sie erneut bereit, damit Änderungen an der `env.php`-Datei wirksam werden.

>[!TIP]
>
>Es ist sicherer, die Datei `env.php` zu bearbeiten, als einen Wert in Admin festzulegen.

## Überprüfen Sie Ihre Einstellung für `X-Frame-Options`

Um Ihre Einstellung zu überprüfen, sehen Sie sich die HTTP-Header auf jeder Storefront-Seite an. Dazu gibt es mehrere Möglichkeiten, einschließlich der Verwendung eines Webbrowser-Inspektors.

Im folgenden Beispiel wird &quot;curl&quot;verwendet, das Sie von jedem Computer aus ausführen können, der über das HTTP-Protokoll eine Verbindung zu Ihrem Commerce-Server herstellen kann.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Suchen Sie in den Kopfzeilen nach dem Wert `X-Frame-Options` .
