---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '2073'
ht-degree: 0%

---
# Magento Open Source-Pakete

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source verwendet Composer, um PHP-Pakete zu verwalten.

Die `composer.json` Datei deklariert die Liste von Paketen, während die `composer.lock` Datei eine vollständige Liste der Pakete (eine Vollversion jedes Pakets und seiner Abhängigkeiten) speichert, die verwendet werden, um eine Installation von Magento Open Source zu Build.

Die folgende Referenzdokumentation wird von der `composer.lock` Datei generiert und behandelt erforderliche Pakete, die in Magento Open Source 2.4.8 enthalten sind.

## Abhängigkeiten

`magento/product-community-edition 2.4.8` weist die folgenden Abhängigkeiten auf:

```config
adobe-commerce/os-extensions-metapackage: 1.0.1
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ^2.0
composer/composer: ^2.0, !=2.2.16
duosecurity/duo_api_php: ^1.1
duosecurity/duo_universal_php: ^1.0
elasticsearch/elasticsearch: ^8.15
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-ftp: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.18
laminas/laminas-code: ^4.13
laminas/laminas-di: ^3.15
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^3.0
league/flysystem-aws-s3-v3: ^3.0
lib-libxml: *
magento/composer: ^1.10.1-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.8
magento/framework-amqp: 100.4.6
magento/framework-bulk: 101.0.4
magento/framework-message-queue: 100.4.8
magento/inventory-metapackage: 1.2.8
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento-zf-db: ^3.21.0
magento/magento2-base: 2.4.8
magento/module-admin-analytics: 100.4.7
magento/module-admin-notification: 100.4.7
magento/module-advanced-pricing-import-export: 100.4.8
magento/module-advanced-search: 100.4.6
magento/module-amqp: 100.4.5
magento/module-analytics: 100.4.8
magento/module-application-performance-monitor: 100.4.1
magento/module-application-performance-monitor-new-relic: 100.4.1
magento/module-async-config: 100.4.1
magento/module-asynchronous-operations: 100.4.8
magento/module-authorization: 100.4.8
magento/module-aws-s3: 100.4.6
magento/module-backend: 102.0.8
magento/module-backup: 100.4.8
magento/module-bundle: 101.0.8
magento/module-bundle-graph-ql: 100.4.8
magento/module-bundle-import-export: 100.4.7
magento/module-cache-invalidate: 100.4.6
magento/module-captcha: 100.4.8
magento/module-cardinal-commerce: 100.4.6
magento/module-catalog: 104.0.8
magento/module-catalog-analytics: 100.4.5
magento/module-catalog-cms-graph-ql: 100.4.4
magento/module-catalog-customer-graph-ql: 100.4.7
magento/module-catalog-graph-ql: 100.4.8
magento/module-catalog-import-export: 101.1.8
magento/module-catalog-inventory: 100.4.8
magento/module-catalog-inventory-graph-ql: 100.4.5
magento/module-catalog-rule: 101.2.8
magento/module-catalog-rule-configurable: 100.4.7
magento/module-catalog-rule-graph-ql: 100.4.5
magento/module-catalog-search: 102.0.8
magento/module-catalog-url-rewrite: 100.4.8
magento/module-catalog-url-rewrite-graph-ql: 100.4.6
magento/module-catalog-widget: 100.4.8
magento/module-checkout: 100.4.8
magento/module-checkout-agreements: 100.4.7
magento/module-checkout-agreements-graph-ql: 100.4.4
magento/module-cms: 104.0.8
magento/module-cms-graph-ql: 100.4.5
magento/module-cms-url-rewrite: 100.4.7
magento/module-cms-url-rewrite-graph-ql: 100.4.6
magento/module-compare-list-graph-ql: 100.4.4
magento/module-config: 101.2.8
magento/module-configurable-import-export: 100.4.6
magento/module-configurable-product: 100.4.8
magento/module-configurable-product-graph-ql: 100.4.8
magento/module-configurable-product-sales: 100.4.5
magento/module-contact: 100.4.7
magento/module-contact-graph-ql: 100.4.1
magento/module-cookie: 100.4.8
magento/module-cron: 100.4.8
magento/module-csp: 100.4.7
magento/module-currency-symbol: 100.4.6
magento/module-customer: 103.0.8
magento/module-customer-analytics: 100.4.5
magento/module-customer-downloadable-graph-ql: 100.4.4
magento/module-customer-graph-ql: 100.4.8
magento/module-customer-import-export: 100.4.8
magento/module-deploy: 100.4.8
magento/module-developer: 100.4.8
magento/module-dhl: 100.4.7
magento/module-directory: 100.4.8
magento/module-directory-graph-ql: 100.4.6
magento/module-downloadable: 100.4.8
magento/module-downloadable-graph-ql: 100.4.8
magento/module-downloadable-import-export: 100.4.7
magento/module-eav: 102.1.8
magento/module-eav-graph-ql: 100.4.5
magento/module-elasticsearch: 101.0.8
magento/module-elasticsearch-8: 101.0.0
magento/module-email: 101.1.8
magento/module-encryption-key: 100.4.6
magento/module-fedex: 100.4.6
magento/module-gift-message: 100.4.7
magento/module-gift-message-graph-ql: 100.4.6
magento/module-google-adwords: 100.4.5
magento/module-google-analytics: 100.4.4
magento/module-google-gtag: 100.4.3
magento/module-google-optimizer: 100.4.7
magento/module-graph-ql: 100.4.8
magento/module-graph-ql-cache: 100.4.5
magento/module-graph-ql-new-relic: 100.4.1
magento/module-graph-ql-resolver-cache: 100.4.1
magento/module-grouped-catalog-inventory: 100.4.5
magento/module-grouped-import-export: 100.4.6
magento/module-grouped-product: 100.4.8
magento/module-grouped-product-graph-ql: 100.4.8
magento/module-import-export: 101.0.8
magento/module-indexer: 100.4.8
magento/module-instant-purchase: 100.4.7
magento/module-integration: 100.4.8
magento/module-integration-graph-ql: 100.4.1
magento/module-jwt-framework-adapter: 100.4.4
magento/module-jwt-user-token: 100.4.3
magento/module-layered-navigation: 100.4.8
magento/module-login-as-customer: 100.4.8
magento/module-login-as-customer-admin-ui: 100.4.8
magento/module-login-as-customer-api: 100.4.7
magento/module-login-as-customer-assistance: 100.4.7
magento/module-login-as-customer-frontend-ui: 100.4.7
magento/module-login-as-customer-graph-ql: 100.4.5
magento/module-login-as-customer-log: 100.4.6
magento/module-login-as-customer-page-cache: 100.4.7
magento/module-login-as-customer-quote: 100.4.6
magento/module-login-as-customer-sales: 100.4.7
magento/module-marketplace: 100.4.6
magento/module-media-content: 100.4.6
magento/module-media-content-api: 100.4.7
magento/module-media-content-catalog: 100.4.6
magento/module-media-content-cms: 100.4.6
magento/module-media-content-synchronization: 100.4.7
magento/module-media-content-synchronization-api: 100.4.6
magento/module-media-content-synchronization-catalog: 100.4.5
magento/module-media-content-synchronization-cms: 100.4.5
magento/module-media-gallery: 100.4.7
magento/module-media-gallery-api: 101.0.7
magento/module-media-gallery-catalog: 100.4.5
magento/module-media-gallery-catalog-integration: 100.4.5
magento/module-media-gallery-catalog-ui: 100.4.5
magento/module-media-gallery-cms-ui: 100.4.5
magento/module-media-gallery-integration: 100.4.7
magento/module-media-gallery-metadata: 100.4.6
magento/module-media-gallery-metadata-api: 100.4.5
magento/module-media-gallery-renditions: 100.4.6
magento/module-media-gallery-renditions-api: 100.4.5
magento/module-media-gallery-synchronization: 100.4.7
magento/module-media-gallery-synchronization-api: 100.4.6
magento/module-media-gallery-synchronization-metadata: 100.4.4
magento/module-media-gallery-ui: 100.4.7
magento/module-media-gallery-ui-api: 100.4.6
magento/module-media-storage: 100.4.7
magento/module-message-queue: 100.4.8
magento/module-msrp: 100.4.7
magento/module-msrp-configurable-product: 100.4.5
magento/module-msrp-grouped-product: 100.4.5
magento/module-multishipping: 100.4.8
magento/module-mysql-mq: 100.4.6
magento/module-new-relic-reporting: 100.4.6
magento/module-newsletter: 100.4.8
magento/module-newsletter-graph-ql: 100.4.5
magento/module-offline-payments: 100.4.6
magento/module-offline-shipping: 100.4.7
magento/module-open-search: 100.4.2
magento/module-order-cancellation: 100.4.1
magento/module-order-cancellation-graph-ql: 100.4.1
magento/module-order-cancellation-ui: 100.4.1
magento/module-page-cache: 100.4.8
magento/module-payment: 100.4.8
magento/module-payment-graph-ql: 100.4.3
magento/module-paypal: 101.0.8
magento/module-paypal-captcha: 100.4.5
magento/module-paypal-graph-ql: 100.4.6
magento/module-persistent: 100.4.8
magento/module-product-alert: 100.4.7
magento/module-product-video: 100.4.8
magento/module-quote: 101.2.8
magento/module-quote-analytics: 100.4.7
magento/module-quote-bundle-options: 100.4.4
magento/module-quote-configurable-options: 100.4.4
magento/module-quote-downloadable-links: 100.4.4
magento/module-quote-graph-ql: 100.4.8
magento/module-related-product-graph-ql: 100.4.5
magento/module-release-notification: 100.4.6
magento/module-remote-storage: 100.4.6
magento/module-reports: 100.4.8
magento/module-require-js: 100.4.4
magento/module-review: 100.4.8
magento/module-review-analytics: 100.4.5
magento/module-review-graph-ql: 100.4.4
magento/module-robots: 101.1.4
magento/module-rss: 100.4.6
magento/module-rule: 100.4.7
magento/module-sales: 103.0.8
magento/module-sales-analytics: 100.4.5
magento/module-sales-graph-ql: 100.4.8
magento/module-sales-inventory: 100.4.5
magento/module-sales-rule: 101.2.8
magento/module-sales-rule-graph-ql: 100.4.1
magento/module-sales-sequence: 100.4.5
magento/module-sample-data: 100.4.6
magento/module-search: 101.1.8
magento/module-security: 100.4.8
magento/module-send-friend: 100.4.6
magento/module-send-friend-graph-ql: 100.4.4
magento/module-shipping: 100.4.8
magento/module-sitemap: 100.4.7
magento/module-store: 101.1.8
magento/module-store-graph-ql: 100.4.6
magento/module-swagger: 100.4.7
magento/module-swagger-webapi: 100.4.4
magento/module-swagger-webapi-async: 100.4.4
magento/module-swatches: 100.4.8
magento/module-swatches-graph-ql: 100.4.6
magento/module-swatches-layered-navigation: 100.4.4
magento/module-tax: 100.4.8
magento/module-tax-graph-ql: 100.4.4
magento/module-tax-import-export: 100.4.7
magento/module-theme: 101.1.8
magento/module-theme-graph-ql: 100.4.5
magento/module-translation: 100.4.8
magento/module-ui: 101.2.8
magento/module-ups: 100.4.8
magento/module-url-rewrite: 102.0.7
magento/module-url-rewrite-graph-ql: 100.4.7
magento/module-user: 101.2.8
magento/module-usps: 100.4.7
magento/module-variable: 100.4.6
magento/module-vault: 101.2.8
magento/module-vault-graph-ql: 100.4.4
magento/module-version: 100.4.5
magento/module-webapi: 100.4.7
magento/module-webapi-async: 100.4.6
magento/module-webapi-security: 100.4.5
magento/module-weee: 100.4.8
magento/module-weee-graph-ql: 100.4.5
magento/module-widget: 101.2.8
magento/module-wishlist: 101.2.8
magento/module-wishlist-analytics: 100.4.6
magento/module-wishlist-graph-ql: 100.4.8
magento/page-builder: 1.7.5
magento/security-package: 1.1.7
magento/theme-adminhtml-backend: 100.4.8
magento/theme-frontend-blank: 100.4.8
magento/theme-frontend-luma: 100.4.8
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^3.6
opensearch-project/opensearch-php: ^2.3
pelago/emogrifier: ^7.0
php: ~8.2.0||~8.3.0||~8.4.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/mailer: ^6.4
symfony/mime: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.4
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^5.0
```

## Drittanbieterlizenzen

### Nur Apache 2.0, LGPL-2.1

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Art</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Client für OpenSearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Adobe Stock-API-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS Common Runtime für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS SDK für PHP - Verwenden von Amazon Web Services in Ihrem PHP-Projekt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api.git">open-telemetry/api</a>
    </td>
    <td>Bibliothek</td>
    <td>API für OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context.git">open-telemetry/context</a>
    </td>
    <td>Bibliothek</td>
    <td>Kontext-Implementierung für OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      PayPal/Modul-braintree
    </td>
    <td>Metapaket</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Port des LESS-Prozessors</td>
  </tr>
  </tbody>
</table>

### BSD-2-Satz

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>Bibliothek</td>
    <td>BaconQrCode ist ein QR-Code-Generator für PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">Dasprid/Enum</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 7.1 enum Implementierung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">WebImpress/Safe-Writer</a>
    </td>
    <td>Bibliothek</td>
    <td>Tool zum sicheren Schreiben von Dateien, um Wettlaufsituationen zu vermeiden</td>
  </tr>
  </tbody>
</table>

### BSD-3-Satz

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Art</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-Modul</td>
    <td>Das Standard Zend_Cache_Backend_Datei Backend Backend hat eine extrem schlechte Performance für die Bereinigung durch Tags, was es unbrauchbar macht, wenn die Anzahl der zwischengespeicherten Elemente zunimmt. Dieses Backend nimmt viele Änderungen vor, die zu einer enormen Leistungssteigerung führen, insbesondere für die Tag Reinigung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein Redis-basierter Sitzungs-Handler mit optimistischer Sperrung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php.git">duosecurity/duo_universal_php</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Implementierung des Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">Firebase/php-jwt</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Bibliothek zum Codieren und Decodieren von JSON Web Tokens (JWT) in PHP. Sollte der aktuellen Spezifikation entsprechen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>Bibliothek</td>
    <td>Generieren und Validieren von CAPTCHAs mit Fillets, Bildern, ReCAPTCHA und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>Bibliothek</td>
    <td>Erweiterungen der PHP Reflection API, statisches Codescannen und Codegenerierung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt eine auf verschachtelten Objekteigenschaften basierende Benutzeroberfläche für den Zugriff auf diese Konfigurationsdaten im Anwendungscode bereit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>Bibliothek</td>
    <td>Automatisierte Abhängigkeitsinjektion für PSR-11-Container</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">Laminas/Laminas-Escaper</a>
    </td>
    <td>Bibliothek</td>
    <td>Sicheres und sicheres Maskieren von HTML, HTML-Attributen, JavaScript, CSS und URLs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventManager</a>
    </td>
    <td>Bibliothek</td>
    <td>Trigger und Überwachen von Ereignissen in einer PHP-Anwendung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-feed</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet Funktionen zum Erstellen und Verwenden von RSS- und Atom-Feeds</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">LAMINAS/LAMINAS-FILTER</a>
    </td>
    <td>Bibliothek</td>
    <td>Programmgesteuertes Filtern und Normalisieren von Daten und Dateien</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine einfache Schnittstelle zum Ausführen von HTTP-Anforderungen (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">Laminas/Laminas-I18N</a>
    </td>
    <td>Bibliothek</td>
    <td>Übersetzungen für Ihre Anwendung bereitstellen und internationalisierte Werte filtern und validieren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet praktische Methoden zum Serialisieren von nativem PHP zu JSON und zum Dekodieren von JSON zu nativem PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">Laminas/Laminas-Lader</a>
    </td>
    <td>Bibliothek</td>
    <td>Strategien für automatisches Laden und Plug-in Laden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>Bibliothek</td>
    <td>Modulares Applikationssystem für Laminas-MVC-Anwendungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">LAMINAS/LAMINAS-MVC</a>
    </td>
    <td>Bibliothek</td>
    <td>Die ereignisgesteuerte MVC-Schicht von Laminas, einschließlich MVC-Anwendungen, Controller und Plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine einfache und flexible Implementierung der Zugriffssteuerungsliste (ACL) für die Verwaltung von Berechtigungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-reCAPTCHA</a>
    </td>
    <td>Bibliothek</td>
    <td>OOP-Wrapper für den ReCaptcha-Webservice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexibles Routing-System für HTTP- und Konsolenanwendungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">LAMINAS/LAMINAS-SERVER</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen von Reflection-basierten RPC-Servern</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-serviceManager</a>
    </td>
    <td>Bibliothek</td>
    <td>werkseitiger Injektor für die Injektion von Abhängigkeiten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>Bibliothek</td>
    <td>Objektorientierte Schnittstelle zu PHP-Sitzungen und -Speicher</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminas/laminas-soap</a>
    </td>
    <td>Bibliothek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>Bibliothek</td>
    <td>SPL-Erweiterungen, Array-Dienstprogramme, Fehler-Handler und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen von Feigenblättern und textbasierten Tabellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator.git">Laminas/Laminas-Übersetzer</a>
    </td>
    <td>Bibliothek</td>
    <td>Schnittstellen für die Übersetzerkomponente von laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">Laminas/Laminas-URI</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Komponente, die die Bearbeitung und Überprüfung von » Einheitlich Ressource Identifiers (URIs) unterstützt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>Bibliothek</td>
    <td>Validierungsklassen für eine Vielzahl von Domänen und die Möglichkeit, Validatoren zu verketten, um komplexe Tauglichkeitsprüfung Kriterien zu erstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">Lamellen/Lamellen-Ansicht</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexibler Ansicht Layer, der mehrere Ansicht Layer, Helfer und mehr unterstützt und bereitstellt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum.git">marc-mabe/php-enum</a>
    </td>
    <td>Bibliothek</td>
    <td>Einfache und schnelle Implementierung von Auflistungen mit nativem PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein in PHP geschriebener PHP-Parser</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha.git">phpfui/reCAPTCHA</a>
    </td>
    <td>Bibliothek</td>
    <td>Client-Bibliothek für reCAPTCHA von Google für PHP 8.4 und höher</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jsShrink</a>
    </td>
    <td>Bibliothek</td>
    <td>In PHP eingebauter JavaScript-Minimierer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Port des YUI CSS-Kompressors</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause-Modifikation

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Magento-Modul</td>
    <td>Zend_Cache-Backend mit Redis mit voller Unterstützung für Tags.</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat.git">Paragonie/Natrium_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>Reine PHP-Implementierung von libnati; verwendet die PHP-Erweiterung, falls vorhanden</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-or-later

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlPurifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardkonformer HTML-Filter in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>Bibliothek</td>
    <td>Ehemals videlalvaro/php-amqplib.  Bei dieser Bibliothek handelt es sich um eine reine PHP-Implementierung des AMQP-Protokolls. Es wurde mit RabbitMQ getestet.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Art</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">Braintree/braintree_php</a>
    </td>
    <td>Bibliothek</td>
    <td>Braintree PHP Client Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">Stein/Mathematik</a>
    </td>
    <td>Bibliothek</td>
    <td>Arithmetik mit beliebiger Genauigkeit Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine leistungsstarke Alternative zu var_export(), die Closures und Objekte ohne __set_state() exportieren kann</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">Christian-Riesen/Base32</a>
    </td>
    <td>Bibliothek</td>
    <td>Base32-Encoder/Decoder nach RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>Bibliothek</td>
    <td>Credis ist eine einfache Schnittstelle zum Redis-Schlüssel-Wert-Store, der die phpredis-Bibliothek umschließt, wenn sie für eine bessere Leistung verfügbar ist.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Suche nach einem Pfad zum System-CA-Bundle und beinhaltet ein Fallback zum Mozilla CA-Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>Bibliothek</td>
    <td>Dienstprogramme zum Scannen von PHP-Code und Generieren von Klassenzuordnungen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">Komponist/Komponist</a>
    </td>
    <td>Bibliothek</td>
    <td>Composer unterstützt Sie beim Deklarieren, Verwalten und Installieren von Abhängigkeiten von PHP-Projekten. Dadurch wird sichergestellt, dass Sie überall den richtigen Stack haben.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Kleine Dienstprogrammbibliothek, die für die Minimierung und Erweiterung von Metadaten zuständig ist.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">Composer/PCRE</a>
    </td>
    <td>Bibliothek</td>
    <td>PCRE Wrapping-Bibliothek, die typsichere Preg_*-Ersetzungen bietet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">Komponist/Semver</a>
    </td>
    <td>Bibliothek</td>
    <td>Server-Bibliothek, die Dienstprogramme, das Analysieren von Versionsbeschränkungen und die Validierung bietet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>Bibliothek</td>
    <td>SPDX-Lizenzliste und Validierungsbibliothek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Startet einen Prozess ohne Xdebug neu.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">Doktrin/Lexer</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Doctrine Lexer Parser Bibliothek, der in rekursiven Top-Down-Parsern verwendet werden kann.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator.git">egulias/email-validator</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Bibliothek zum Validieren von E-Mails gegen mehrere RFCs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php.git">elastisch/transport</a>
    </td>
    <td>Bibliothek</td>
    <td>HTTP-Transport PHP-Bibliothek für Elastic-Produkte</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Client für Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">Endroid/QR-Code</a>
    </td>
    <td>Bibliothek</td>
    <td>Endroid QR Symbol</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>Bibliothek</td>
    <td>Fork von guzzle/streams (abgebrochen) zur Verwendung mit elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Abspaltung von guzzle/RingPHP (aufgegeben) zur Verwendung mit elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>Bibliothek</td>
    <td>Guzzle ist eine PHP HTTP Client-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promises</a>
    </td>
    <td>Bibliothek</td>
    <td>Guzzle-Versprechensbibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>Bibliothek</td>
    <td>PSR-7-Nachrichtenimplementierung, die auch gängige Dienstprogrammmethoden bereitstellt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git">JustInRainbow/JSON-Schema</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Bibliothek zum Überprüfen eines JSON-Schemas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">League/Flysystem</a>
    </td>
    <td>Bibliothek</td>
    <td>Dateispeicherabstraktion für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">League/Flysystem-AWS-S3-V3</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS S3-Dateisystemadapter für Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local.git">League/Flysystem-local</a>
    </td>
    <td>Bibliothek</td>
    <td>Lokaler Dateisystemadapter für Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">League/MIME-Typ-Erkennung</a>
    </td>
    <td>Bibliothek</td>
    <td>Mime-Typ-Erkennung für Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">Monolog/Monolog</a>
    </td>
    <td>Bibliothek</td>
    <td>Sendet Ihre Protokolle an Dateien, Sockets, Posteingänge, Datenbanken und verschiedene Webdienste</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>Bibliothek</td>
    <td>Geben Sie deklarativ an, wie Elemente aus einer JSON-Dokument extrahiert werden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">Paragonie/constant_time_encoding</a>
    </td>
    <td>Bibliothek</td>
    <td>Zeitkonstante Implementierungen der RFC 4648-Kodierung (Basis-64, Basis-32, Basis-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">Paragonie/random_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x Polyfill für random_bytes() und random_int() ab PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">Pelago/Emogrifikator</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Stile in Inline-Stilattribute in Ihrem HTML Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery.git">php-http/discovery</a>
    </td>
    <td>Komponist-Plug-in</td>
    <td>Findet und installiert PSR-7-, PSR-17-, PSR-18- und HTTPlug-Implementierungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug.git">php-http/httplug</a>
    </td>
    <td>Bibliothek</td>
    <td>HTTPlug, die HTTP-Client-Abstraktion für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise.git">PHP-HTTP/Promise</a>
    </td>
    <td>Bibliothek</td>
    <td>Promise für asynchrone HTTP-Anfragen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertieren von CSS-Selektoren in XPath-Abfragen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>Bibliothek</td>
    <td>Moderne DOM-API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>Bibliothek</td>
    <td>Eigenschaftenaccessor- und -mutatorfunktionen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x-8.x Polyfill für mcrypt-Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Secure Communications Bibliothek - Reine PHP-Implementierungen von RSA, AES, SSH2, SFTP, X.509 usw.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">PSR/Cache</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Benutzeroberfläche für Caching Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">PSR/CLOCK</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle zum Ablesen der Uhr.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">PSR/Container</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Containerschnittstelle (PHP, FIG, PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/Ereignis-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardmäßig Schnittstellen für die Ereignis Handhabung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">PSR/HTTP-Client</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle für HTTP-Clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">PSR/HTTP-Factory</a>
    </td>
    <td>Bibliothek</td>
    <td>PSR-17: Gemeinsame Schnittstellen für PSR-7 HTTP Message Factory</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">PSR/HTTP-Nachricht</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle für HTTP-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">PSR/LOG</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Benutzeroberfläche für Protokollierung Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getAllHeaders</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein Polyfill für getAllHeaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">Ramsey/Collection</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zur Darstellung und Bearbeitung von Sammlungen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">Ramsey/UUID</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zum Generieren und Verwenden von Universally Unique Identifiers (UUIDs).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">React/Promise</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Implementierung von CommonJS Promises/A für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>Bibliothek</td>
    <td>Parser für in PHP geschriebene CSS-Dateien</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>Bibliothek</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>Bibliothek</td>
    <td>PHAR-Dateiformat-Dienstprogramme, für den Fall, dass PHP Sie auffordert</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">Seld/Signal-Handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Einfacher Unix-Signal-Handler, der stillschweigend fehlschlägt, wenn Signale nicht unterstützt werden, um eine einfache über mehrere Plattformen hinweg Entwicklung zu ermöglichen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Bibliothek</td>
    <td>AES Key Wrap für PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Bibliothek zur Generierung von Einmalpasswörtern nach RFC 4226 (HOTP-Algorithmus) und RFC 6238 (TOTP-Algorithmus) und kompatibel mit Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-Framework</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Framework zur Verwaltung von Public-Key-Infrastrukturen. Es umfasst X.509-Public-Key-Zertifikate, Attributzertifikate, Zertifizierungsanforderungen und Zertifizierungen Pfad Tauglichkeitsprüfung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilft Ihnen, Konfigurationswerte jeglicher Art zu finden, zu laden, zu kombinieren, automatisch auszufüllen und zu überprüfen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">Symfony/Konsole</a>
    </td>
    <td>Bibliothek</td>
    <td>Vereinfacht die Erstellung ansprechender und testbarer Befehlszeilenschnittstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-Selektor</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Selektoren in XPath-Ausdrücke</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-jection</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Standardisierung und Zentralisierung der Objekterstellung in der Anwendung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">Symfony/Deprecation-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine generische Funktion und Konvention für Hinweise zum Verwerfen von Triggern</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet Tools zur Fehlerverwaltung und einfacheren Fehlerbehebung in PHP-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt Tools bereit, mit denen Ihre Anwendungskomponenten miteinander kommunizieren können, indem Ereignisse gesendet und überwacht werden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen im Zusammenhang mit dem Dispatching-Ereignis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt grundlegende Dienstprogramme für das Dateisystem bereit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>Bibliothek</td>
    <td>Findet Dateien und Verzeichnisse über eine intuitive, fließende Benutzeroberfläche</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/HTTP-Client</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet leistungsstarke Methoden zum synchronen oder asynchronen Abrufen von HTTP-Ressourcen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen in Bezug auf HTTP-Clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>Bibliothek</td>
    <td>Definiert eine objektorientierte Ebene für die HTTP-Spezifikation</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt einen strukturierten Prozess zum Konvertieren einer Anfrage in eine Antwort bereit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht den Zugriff auf die Lokalisierungsdaten der ICU-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer.git">symfony/mailer</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilft beim Senden von E-Mails</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime.git">symfony/mime</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Bearbeitung von MIME-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für ctype-Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für intl's grapheme_* Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für die Funktionen „idn_to_ascii“ und „idn_to_utf8“ von Intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für Intl's Normalizer-Klasse und zugehörige Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für die MBstring-Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 7.3+ Funktionen zur Reduzierung von PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 8.0+ Funktionen zur Reduzierung von PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill portiert einige PHP 8.1+ Funktionen auf niedrigere PHP-Versionen zurück</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82.git">symfony/polyfill-php82</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill, das einige PHP 8.2+ Funktionen auf niedrigere PHP-Versionen zurückportiert</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 8.3+ Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>Bibliothek</td>
    <td>Führt Befehle in Teilprozessen aus</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen im Zusammenhang mit Schreibdiensten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">Symfonye/Streicher</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine objektorientierte API für Zeichenfolgen und verarbeitet Bytes, UTF-8-Codepunkte und Graphem-Cluster auf einheitliche Weise</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet Mechanismen zum Durchlaufen beliebiger PHP-Variable</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht den Export jeder serialisierbaren PHP-Datenstruktur in reinen PHP-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml.git">Symfony/YAML</a>
    </td>
    <td>Bibliothek</td>
    <td>Lädt YAML-Dateien und gibt deren Speicherinhalt aus</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">Web-Token/JWT-Framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>JSON Object Signing and Encryption Library für PHP und Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Port der GraphQL-Referenzimplementierung</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      PayPal/Modul-braintree-geschenkverpackung
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      PayPal/Modul-braintree-reward
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>Bibliothek</td>
    <td>CBOR-Encoder für PHP</td>
  </tr>
  </tbody>
</table>

### geschützt

<table>
  <thead>
    <tr>
      <th>-Name</th>
      <th>Art</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      PayPal/Modul-braintree-core
    </td>
    <td>Magento2-Modul</td>
    <td>Verzweigung aus dem Magento Braintree 2.2.0 Modul von Gene Commerce für PayPal.</td>
  </tr>
  </tbody>
</table>
