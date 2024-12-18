---
title: Admin-URI anzeigen oder ändern
description: Führen Sie diese Schritte aus, um den URI Ihrer Adobe Commerce Admin-Anwendung anzuzeigen und zu ändern.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Admin-URI anzeigen oder ändern

Bevor Sie diesen Befehl ausführen, müssen Sie [die Bereitstellungskonfiguration erstellen oder aktualisieren](deployment.md).

## Admin-URI anzeigen

In diesem Abschnitt wird die Verwendung der Befehlszeile zum Anzeigen der Admin-URI (Uniform Resource Identifier[ beschrieben](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2).

Befehlsoptionen:

```bash
bin/magento info:adminuri
```

Es folgt ein Beispielergebnis:

```
Admin Panel URI: /admin_1wgrah
```

Sie können den Admin-URI auch in `<magento_root>/app/etc/env.php` anzeigen. Es folgt ein Snippet:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Admin-URL ändern

Um den Admin-URI zu ändern, verwenden Sie den [`magento setup:config:set`](deployment.md).
