---
title: Konfigurieren des Lack-ESI-Blocks
description: Erfahren Sie mehr über Varnish Edge Side Includes (ESI) und darüber, wie Sie Web-Seiten für Adobe Commerce einbetten. Entdecken Sie die Implementierung und Optimierung von ESI-Blöcken.
badge: label="Ein Beitrag von Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T22:02:08.706Z'
TQID: 'https://experienceleague.adobe.com/hzsfaZyHuUhzfb86anO43PfP-62WRPOoMbYOh-H1vqo'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%
---
# Konfigurieren des Lack-ESI-Blocks {#varnish-esi-block}

{{varnish-config-cloud}}

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
