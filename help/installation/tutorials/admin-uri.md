---
title: Anzeigen oder Ändern des Admin-URI
description: Führen Sie diese Schritte aus, um den URI Ihrer Adobe Commerce- oder Magento Open Source Admin-Anwendung anzuzeigen und zu ändern.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Anzeigen oder Ändern des Admin-URI

Bevor Sie diesen Befehl ausführen, müssen Sie [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md).

## Anzeigen des Admin-URI

In diesem Abschnitt wird beschrieben, wie Sie mit der Befehlszeile die Admin Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Befehlsoptionen:

```bash
bin/magento info:adminuri
```

Ein Beispielergebnis:

```terminal
Admin Panel URI: /admin_1wgrah
```

Sie können den Admin-URI auch in `<magento_root>/app/etc/env.php`. Ein Snippet folgt:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Ändern der Admin-URL

Um den Admin-URI zu ändern, verwenden Sie die [`magento setup:config:set`](deployment.md) Befehl.
