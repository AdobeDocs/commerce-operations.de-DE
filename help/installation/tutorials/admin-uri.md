---
title: Anzeigen oder Ändern des Admin-URI
description: Führen Sie diese Schritte aus, um den URI Ihrer Adobe Commerce Admin-Anwendung anzuzeigen und zu ändern.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Anzeigen oder Ändern des Admin-URI

Bevor Sie diesen Befehl ausführen, müssen Sie [die Bereitstellungskonfiguration erstellen oder aktualisieren](deployment.md).

## Anzeigen des Admin-URI

In diesem Abschnitt wird beschrieben, wie Sie mit der Befehlszeile die Admin Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) anzeigen.

Befehlsoptionen:

```bash
bin/magento info:adminuri
```

Ein Beispielergebnis:

```
Admin Panel URI: /admin_1wgrah
```

Sie können den Admin-URI auch in &quot;`<magento_root>/app/etc/env.php`&quot;anzeigen. Ein Snippet folgt:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Ändern der Admin-URL

Verwenden Sie den Befehl [`magento setup:config:set`](deployment.md) , um den Admin-URI zu ändern.
