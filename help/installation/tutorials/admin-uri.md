---
title: Admin-URI anzeigen oder ändern
description: Führen Sie diese Schritte aus, um den URI Ihrer Adobe Commerce Admin-Anwendung anzuzeigen und zu ändern.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Admin-URI anzeigen oder ändern

Bevor Sie diesen Befehl ausführen, müssen Sie [die Bereitstellungskonfiguration erstellen oder aktualisieren](deployment.md).

## Admin-URI anzeigen

In diesem Abschnitt wird die Verwendung der Befehlszeile zum Anzeigen der Admin-URI (Uniform Resource Identifier[ beschrieben](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2).

Befehlsoptionen:

```shell
bin/magento info:adminuri
```

Es folgt ein Beispielergebnis:

```text
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
