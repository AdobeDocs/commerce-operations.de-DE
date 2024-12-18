---
title: ESI-Block Lack
description: Erfahren Sie mehr über Edge Side Includes und wie Sie sie zum Einbetten von Web-Seiten verwenden können.
badge: label="Ein Beitrag von Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# ESI-Block Lack

Edge Side Includes (ESI) sind spezielle Anweisungen, mit denen Sie Web-Seiten in andere Web-Seiten einschließen können.

Ein Beispiel:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Varnish ruft Inhalte aus `http://domain.com/index.php/page_cache/block/esi/blocks` ab und ersetzt das `<esi>`-Tag damit.

## Commerce und Lack ESI

Das Commerce-Framework erstellt ein ESI-Tag, wenn die folgenden Bedingungen erfüllt sind:

- Die Caching-Anwendung ist auf `Varnish Cache` festgelegt
- Ein XML-Layout-`block` wird mit einem `ttl` hinzugefügt

### Beispiel

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Im obigen Beispiel fügt das `block`-Element Inhalte aus der `esi.phtml`-Vorlage zu einer Homepage hinzu und aktualisiert sie automatisch alle 30 Sekunden.

## Einschränkungen

Derzeit unterstützt Varnish ESI nicht über HTTPS, sodass es automatisch zu HTTP wechselt.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
