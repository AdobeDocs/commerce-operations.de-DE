---
title: Verhindern von Clickjacking-Angriffen
description: Verhindern Sie Clickjacking-Exploits, indem Sie die Kopfzeile „X-Frame-Options“ verwenden, um das Rendern der Seite zu steuern.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%
---
# Verhindern von Clickjacking-Angriffen

Verhindern Sie [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking)-Exploits, indem Sie die [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP-Anfrage-Kopfzeile in Anfragen an Ihre Storefront einschließen.

Mit dem `X-Frame-Options`-Header können Sie wie folgt angeben, ob ein Browser berechtigt ist, eine Seite in einem `<frame>`, `<iframe>` oder `<object>` zu rendern:

- `DENY`: Seite kann nicht in einem Frame angezeigt werden.
- `SAMEORIGIN`: (Standard) Die Seite kann nur in einem Frame angezeigt werden, der auf demselben Ursprung liegt wie die Seite selbst.

>[!WARNING]
>
>Die `ALLOW-FROM <uri>`-Option wird nicht mehr unterstützt, da sie von Commerce unterstützte Browser nicht mehr unterstützen. Siehe [Browser-Kompatibilität](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Aus Sicherheitsgründen empfiehlt Adobe dringend, die Commerce-Storefront nicht in einem Frame auszuführen.

## Implementieren von `X-Frame-Options`

Legen Sie einen Wert für `X-Frame-Options` in `<project-root>/app/etc/env.php` fest. Der Standardwert wird wie folgt festgelegt:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Stellen Sie erneut bereit, damit Änderungen an der `env.php` wirksam werden.

>[!TIP]
>
>Es ist sicherer, die `env.php`-Datei zu bearbeiten, als einen Wert im Admin-Bereich festzulegen.

## Überprüfen der Einstellung für `X-Frame-Options`

Um Ihre Einstellung zu überprüfen, zeigen Sie die HTTP-Kopfzeilen auf einer beliebigen Storefront-Seite an. Dazu gibt es mehrere Möglichkeiten, einschließlich der Verwendung eines Webbrowser-Inspektors.

Im folgenden Beispiel wird curl verwendet, das Sie auf jedem Computer ausführen können, der über das HTTP-Protokoll eine Verbindung zu Ihrem Commerce-Server herstellen kann.

```shell
curl -I -v --location-trusted '<storefront-URL>'
```

Suchen Sie in den Kopfzeilen nach dem Wert `X-Frame-Options` .
