---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---
# Magento Open Source Packages

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source verwendet Composer zur Verwaltung von PHP-Paketen.

Die `composer.json` -Datei deklariert die Liste der Pakete, während die `composer.lock` -Datei speichert eine vollständige Liste der Pakete (eine Vollversion jedes Pakets und seiner Abhängigkeiten), die zum Erstellen einer Magento Open Source-Installation verwendet werden.

Die folgende Referenzdokumentation wird aus der `composer.lock` -Datei, und es umfasst die erforderlichen Pakete, die in Magento Open Source 2.4.7-p1 enthalten sind.

## Abhängigkeiten

`magento/product-community-edition 2.4.7-p1` weist die folgenden Abhängigkeiten auf:

```config
adobe-commerce/os-extensions-metapackage: ~1.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ~1.5.3
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
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
laminas/laminas-captcha: ^2.17
laminas/laminas-code: ^4.13
laminas/laminas-db: ^2.19
laminas/laminas-di: ^3.13
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-file: ^2.13
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-oauth: ^2.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.16
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.10.0-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.7-p1
magento/framework-amqp: 100.4.5
magento/framework-bulk: 101.0.3
magento/framework-message-queue: 100.4.7
magento/inventory-metapackage: 1.2.7-p1
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento2-base: 2.4.7-p1
magento/module-admin-analytics: 100.4.6
magento/module-admin-notification: 100.4.6
magento/module-advanced-pricing-import-export: 100.4.7
magento/module-advanced-search: 100.4.5
magento/module-amqp: 100.4.4
magento/module-analytics: 100.4.7
magento/module-application-performance-monitor: 100.4.0
magento/module-application-performance-monitor-new-relic: 100.4.0
magento/module-async-config: 100.4.0
magento/module-asynchronous-operations: 100.4.7
magento/module-authorization: 100.4.7
magento/module-aws-s3: 100.4.5
magento/module-backend: 102.0.7
magento/module-backup: 100.4.7
magento/module-bundle: 101.0.7
magento/module-bundle-graph-ql: 100.4.7
magento/module-bundle-import-export: 100.4.6
magento/module-cache-invalidate: 100.4.5
magento/module-captcha: 100.4.7
magento/module-cardinal-commerce: 100.4.5
magento/module-catalog: 104.0.7-p1
magento/module-catalog-analytics: 100.4.4
magento/module-catalog-cms-graph-ql: 100.4.3
magento/module-catalog-customer-graph-ql: 100.4.6
magento/module-catalog-graph-ql: 100.4.7
magento/module-catalog-import-export: 101.1.7
magento/module-catalog-inventory: 100.4.7
magento/module-catalog-inventory-graph-ql: 100.4.4
magento/module-catalog-rule: 101.2.7
magento/module-catalog-rule-configurable: 100.4.6
magento/module-catalog-rule-graph-ql: 100.4.4
magento/module-catalog-search: 102.0.7
magento/module-catalog-url-rewrite: 100.4.7
magento/module-catalog-url-rewrite-graph-ql: 100.4.5
magento/module-catalog-widget: 100.4.7
magento/module-checkout: 100.4.7
magento/module-checkout-agreements: 100.4.6
magento/module-checkout-agreements-graph-ql: 100.4.3
magento/module-cms: 104.0.7
magento/module-cms-graph-ql: 100.4.4
magento/module-cms-url-rewrite: 100.4.6
magento/module-cms-url-rewrite-graph-ql: 100.4.5
magento/module-compare-list-graph-ql: 100.4.3
magento/module-config: 101.2.7
magento/module-configurable-import-export: 100.4.5
magento/module-configurable-product: 100.4.7
magento/module-configurable-product-graph-ql: 100.4.7
magento/module-configurable-product-sales: 100.4.4
magento/module-contact: 100.4.6
magento/module-contact-graph-ql: 100.4.0
magento/module-cookie: 100.4.7
magento/module-cron: 100.4.7
magento/module-csp: 100.4.6
magento/module-currency-symbol: 100.4.5
magento/module-customer: 103.0.7-p1
magento/module-customer-analytics: 100.4.4
magento/module-customer-downloadable-graph-ql: 100.4.3
magento/module-customer-graph-ql: 100.4.7
magento/module-customer-import-export: 100.4.7
magento/module-deploy: 100.4.7
magento/module-developer: 100.4.7
magento/module-dhl: 100.4.6
magento/module-directory: 100.4.7
magento/module-directory-graph-ql: 100.4.5
magento/module-downloadable: 100.4.7
magento/module-downloadable-graph-ql: 100.4.7
magento/module-downloadable-import-export: 100.4.6
magento/module-eav: 102.1.7
magento/module-eav-graph-ql: 100.4.4
magento/module-elasticsearch: 101.0.7
magento/module-elasticsearch-7: 100.4.7
magento/module-email: 101.1.7
magento/module-encryption-key: 100.4.5
magento/module-fedex: 100.4.5
magento/module-gift-message: 100.4.6
magento/module-gift-message-graph-ql: 100.4.5
magento/module-google-adwords: 100.4.4
magento/module-google-analytics: 100.4.3
magento/module-google-gtag: 100.4.2
magento/module-google-optimizer: 100.4.6
magento/module-graph-ql: 100.4.7
magento/module-graph-ql-cache: 100.4.4
magento/module-graph-ql-new-relic: 100.4.0
magento/module-graph-ql-resolver-cache: 100.4.0
magento/module-grouped-catalog-inventory: 100.4.4
magento/module-grouped-import-export: 100.4.5
magento/module-grouped-product: 100.4.7
magento/module-grouped-product-graph-ql: 100.4.7
magento/module-import-export: 101.0.7
magento/module-indexer: 100.4.7
magento/module-instant-purchase: 100.4.6
magento/module-integration: 100.4.7
magento/module-integration-graph-ql: 100.4.0
magento/module-jwt-framework-adapter: 100.4.3
magento/module-jwt-user-token: 100.4.2
magento/module-layered-navigation: 100.4.7
magento/module-login-as-customer: 100.4.7
magento/module-login-as-customer-admin-ui: 100.4.7
magento/module-login-as-customer-api: 100.4.6
magento/module-login-as-customer-assistance: 100.4.6
magento/module-login-as-customer-frontend-ui: 100.4.6
magento/module-login-as-customer-graph-ql: 100.4.4
magento/module-login-as-customer-log: 100.4.5
magento/module-login-as-customer-page-cache: 100.4.6
magento/module-login-as-customer-quote: 100.4.5
magento/module-login-as-customer-sales: 100.4.6
magento/module-marketplace: 100.4.5
magento/module-media-content: 100.4.5
magento/module-media-content-api: 100.4.6
magento/module-media-content-catalog: 100.4.5
magento/module-media-content-cms: 100.4.5
magento/module-media-content-synchronization: 100.4.6
magento/module-media-content-synchronization-api: 100.4.5
magento/module-media-content-synchronization-catalog: 100.4.4
magento/module-media-content-synchronization-cms: 100.4.4
magento/module-media-gallery: 100.4.6
magento/module-media-gallery-api: 101.0.6
magento/module-media-gallery-catalog: 100.4.4
magento/module-media-gallery-catalog-integration: 100.4.4
magento/module-media-gallery-catalog-ui: 100.4.4
magento/module-media-gallery-cms-ui: 100.4.4
magento/module-media-gallery-integration: 100.4.6
magento/module-media-gallery-metadata: 100.4.5
magento/module-media-gallery-metadata-api: 100.4.4
magento/module-media-gallery-renditions: 100.4.5
magento/module-media-gallery-renditions-api: 100.4.4
magento/module-media-gallery-synchronization: 100.4.6
magento/module-media-gallery-synchronization-api: 100.4.5
magento/module-media-gallery-synchronization-metadata: 100.4.3
magento/module-media-gallery-ui: 100.4.6
magento/module-media-gallery-ui-api: 100.4.5
magento/module-media-storage: 100.4.6
magento/module-message-queue: 100.4.7
magento/module-msrp: 100.4.6
magento/module-msrp-configurable-product: 100.4.4
magento/module-msrp-grouped-product: 100.4.4
magento/module-multishipping: 100.4.7
magento/module-mysql-mq: 100.4.5
magento/module-new-relic-reporting: 100.4.5
magento/module-newsletter: 100.4.7
magento/module-newsletter-graph-ql: 100.4.4
magento/module-offline-payments: 100.4.5
magento/module-offline-shipping: 100.4.6
magento/module-open-search: 100.4.1
magento/module-order-cancellation: 100.4.0
magento/module-order-cancellation-graph-ql: 100.4.0
magento/module-order-cancellation-ui: 100.4.0
magento/module-page-cache: 100.4.7
magento/module-payment: 100.4.7
magento/module-payment-graph-ql: 100.4.2
magento/module-paypal: 101.0.7
magento/module-paypal-captcha: 100.4.4
magento/module-paypal-graph-ql: 100.4.5
magento/module-persistent: 100.4.7
magento/module-product-alert: 100.4.6
magento/module-product-video: 100.4.7
magento/module-quote: 101.2.7-p1
magento/module-quote-analytics: 100.4.6
magento/module-quote-bundle-options: 100.4.3
magento/module-quote-configurable-options: 100.4.3
magento/module-quote-downloadable-links: 100.4.3
magento/module-quote-graph-ql: 100.4.7
magento/module-related-product-graph-ql: 100.4.4
magento/module-release-notification: 100.4.5
magento/module-remote-storage: 100.4.5
magento/module-reports: 100.4.7
magento/module-require-js: 100.4.3
magento/module-review: 100.4.7
magento/module-review-analytics: 100.4.4
magento/module-review-graph-ql: 100.4.3
magento/module-robots: 101.1.3
magento/module-rss: 100.4.5
magento/module-rule: 100.4.6
magento/module-sales: 103.0.7-p1
magento/module-sales-analytics: 100.4.4
magento/module-sales-graph-ql: 100.4.7
magento/module-sales-inventory: 100.4.4
magento/module-sales-rule: 101.2.7
magento/module-sales-rule-graph-ql: 100.4.0
magento/module-sales-sequence: 100.4.4
magento/module-sample-data: 100.4.5
magento/module-search: 101.1.7
magento/module-security: 100.4.7
magento/module-send-friend: 100.4.5
magento/module-send-friend-graph-ql: 100.4.3
magento/module-shipping: 100.4.7
magento/module-sitemap: 100.4.6
magento/module-store: 101.1.7
magento/module-store-graph-ql: 100.4.5
magento/module-swagger: 100.4.6
magento/module-swagger-webapi: 100.4.3
magento/module-swagger-webapi-async: 100.4.3
magento/module-swatches: 100.4.7
magento/module-swatches-graph-ql: 100.4.5
magento/module-swatches-layered-navigation: 100.4.3
magento/module-tax: 100.4.7
magento/module-tax-graph-ql: 100.4.3
magento/module-tax-import-export: 100.4.6
magento/module-theme: 101.1.7
magento/module-theme-graph-ql: 100.4.4
magento/module-translation: 100.4.7
magento/module-ui: 101.2.7
magento/module-ups: 100.4.7-p1
magento/module-url-rewrite: 102.0.6
magento/module-url-rewrite-graph-ql: 100.4.6
magento/module-user: 101.2.7
magento/module-usps: 100.4.6
magento/module-variable: 100.4.5
magento/module-vault: 101.2.7
magento/module-vault-graph-ql: 100.4.3
magento/module-version: 100.4.4
magento/module-webapi: 100.4.6-p1
magento/module-webapi-async: 100.4.5
magento/module-webapi-security: 100.4.4
magento/module-weee: 100.4.7
magento/module-weee-graph-ql: 100.4.4
magento/module-widget: 101.2.7
magento/module-wishlist: 101.2.7
magento/module-wishlist-analytics: 100.4.5
magento/module-wishlist-graph-ql: 100.4.7
magento/page-builder: 1.7.4-p1
magento/security-package: 1.1.6-p1
magento/theme-adminhtml-backend: 100.4.7-p1
magento/theme-frontend-blank: 100.4.7-p1
magento/theme-frontend-luma: 100.4.7-p1
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0||~8.3.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

## Drittanbieterlizenzen

### Apache-2.0, LGPL-2.1-only

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
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Client für Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Client für OpenSearch</td>
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
    <td>Adobe Stock API-Bibliothek</td>
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
      paypal/module-braintree
    </td>
    <td>metapackage</td>
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

### BSD-2-Clause

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
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>Bibliothek</td>
    <td>BaconQrCode ist ein QR-Code-Generator für PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 7.1 Enum-Implementierung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>Bibliothek</td>
    <td>Tool zum sicheren Schreiben von Dateien, um Wettlaufsituationen zu vermeiden</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Magento-Modul</td>
    <td>Das Stock Zend_Cache_Backend_File Backend hat eine extrem schlechte Leistung bei der Reinigung durch Tags, sodass es unbrauchbar wird, wenn die Anzahl zwischengespeicherter Elemente zunimmt. Dieses Backend nimmt viele Änderungen vor, die zu einer enormen Leistungssteigerung führen, insbesondere bei der Tag-Reinigung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein Redis-basierter Sitzungs-Handler mit optimistischer Sperre</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Bibliothek zum Kodieren und Dekodieren von JSON Web Tokens (JWT) in PHP. Sollte der aktuellen Spezifikation entsprechen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">Google/Recaptcha</a>
    </td>
    <td>Bibliothek</td>
    <td>Client-Bibliothek für reCAPTCHA, einen kostenlosen Service, der Websites vor Spam und Missbrauch schützt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">Laminas/Laminas-Captcha</a>
    </td>
    <td>Bibliothek</td>
    <td>Generieren und Validieren von CAPTCHAs mit Figlets, Bildern, ReCaptcha und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">Laminas/Laminatcode</a>
    </td>
    <td>Bibliothek</td>
    <td>Erweiterung der PHP Reflection API, statisches Scannen von Code und Codegenerierung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet eine verschachtelte, auf Objekteigenschaften basierende Benutzeroberfläche für den Zugriff auf diese Konfigurationsdaten im Anwendungscode</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>Bibliothek</td>
    <td>Starke Verschlüsselungs-Tools und Passwort-Hashing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>Bibliothek</td>
    <td>Abstraktionsebene der Datenbank, SQL-Abstraktion, Abstraktion der Ergebnismenge und Implementierung von RowDataGateway und TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">Laminas/Laminas-di</a>
    </td>
    <td>Bibliothek</td>
    <td>Automatisierte Abhängigkeitseinspritzung für PSR-11-Container</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">Lamina/Lamina-Escaper</a>
    </td>
    <td>Bibliothek</td>
    <td>Sicheres und sicheres Escape von HTML, HTML-Attributen, JavaScript, CSS und URLs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>Bibliothek</td>
    <td>Trigger und Abhören von Ereignissen in einer PHP-Anwendung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">Laminas/Laminatfeed</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet Funktionen zum Erstellen und Verwenden von RSS- und Atom-Feeds.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Klassendateien suchen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">Laminas/Lamina-Filter</a>
    </td>
    <td>Bibliothek</td>
    <td>Daten und Dateien programmgesteuert filtern und normalisieren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">Laminas/Laminas-http</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine einfache Schnittstelle für die Ausführung von HTTP (Hyper-Text Transfer Protocol)-Anfragen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">Laminas/Laminas-i18n</a>
    </td>
    <td>Bibliothek</td>
    <td>Übersetzungen für Ihre Anwendung bereitstellen sowie internationalisierte Werte filtern und validieren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet praktische Methoden zum Serialisieren von nativem PHP in JSON und Dekodieren von JSON in natives PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">Laminas/Laminas-Loader</a>
    </td>
    <td>Bibliothek</td>
    <td>Strategien zum Laden und Laden von Plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">Laminas/Laminas-mail</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet allgemeine Funktionen zum Erstellen und Senden von Text- und MIME-kompatiblen mehrteiligen E-Mail-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen kryptografisch sicherer Pseudo-Zufallszahlen und Verwalten großer Ganzzahlen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">Lamina/Lamina-mime</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen und Analysieren von MIME-Nachrichten und -Teilen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>Bibliothek</td>
    <td>Modulare Anwendungssysteme für Laminas-mvc-Anwendungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">Laminas/Laminas-mvc</a>
    </td>
    <td>Bibliothek</td>
    <td>Die ereignisgesteuerte MVC-Schicht von Laminas, einschließlich MVC-Anwendungen, Controller und Plugins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">Laminas/Laminas-Oauth</a>
    </td>
    <td>Bibliothek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine einfache und flexible ACL-Implementierung (Access Control List) für die Verwaltung von Berechtigungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">Laminas/Laminas-Recaptcha</a>
    </td>
    <td>Bibliothek</td>
    <td>OOP-Wrapper für den ReCaptcha-Webdienst</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">Laminas/Laminas-Router</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexibles Routing-System für HTTP- und Konsolenanwendungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen reflektionsbasierter RPC-Server</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>Bibliothek</td>
    <td>Werksgesteuerter Container für die Injektion von Abhängigkeiten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>Bibliothek</td>
    <td>Objektorientierte Schnittstelle für PHP-Sitzungen und -Speicherung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">Lamina/Lamina-Seife</a>
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
    <td>Erstellen von FIGlets und textbasierten Tabellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">Lamina/Laminas-uri</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Komponente, die die Bearbeitung und Validierung von Uniform Resource Identifiers (URIs) unterstützt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">Laminas/Laminas-validator</a>
    </td>
    <td>Bibliothek</td>
    <td>Validierungsklassen für eine Vielzahl von Domänen und die Möglichkeit, Validatoren zu ketten, um komplexe Validierungskriterien zu erstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">Lamina/Lamina-Ansicht</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexible Ansichtsebene zur Unterstützung und Bereitstellung mehrerer Ansichtsebenen, Helfer und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Parser, der in PHP geschrieben wurde</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jschreink</a>
    </td>
    <td>Bibliothek</td>
    <td>JavaScript-Minifier in PHP erstellt</td>
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

### BSD-3-Clause-Modification

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
      <th>Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/Natrium_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>Reine PHP-Implementierung von libNatrium; verwendet die PHP-Erweiterung, falls sie existiert</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-oder-höher

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
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlfilter</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardkonformer HTML-Filter in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>Bibliothek</td>
    <td>Früher Videlalvaro/php-amqplib.  Diese Bibliothek ist eine reine PHP-Implementierung des AMQP-Protokolls. Es wurde mit RabbitMQ getestet.</td>
  </tr>
  </tbody>
</table>

### MIT

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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>Bibliothek</td>
    <td>Braintree PHP Client Library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">Backstein/Mathematik</a>
    </td>
    <td>Bibliothek</td>
    <td>Arithmetische Bibliothek mit beliebiger Genauigkeit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">Backstein/Varexporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine leistungsstarke Alternative zu var_export(), die Verschlüsse und Objekte ohne __set_state() exportieren kann</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>Bibliothek</td>
    <td>Base32-Encoder/Decoder nach RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>Bibliothek</td>
    <td>Credis ist eine einfache Schnittstelle zum Schlüssel-Wert-Store von Redis, der die phpredis-Bibliothek umschließt, wenn sie für eine bessere Leistung verfügbar ist.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">Composer/ca-bundle</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht es Ihnen, einen Pfad zum System-CA-Bundle zu finden und eine Ausweichmöglichkeit zum Mozilla CA-Bundle einzuschließen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">Composer/class-map-generator</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilfsprogramme zum Scannen von PHP-Code und Generieren von Klassenkarten.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">Verfasser/Verfasser</a>
    </td>
    <td>Bibliothek</td>
    <td>Composer hilft Ihnen, Abhängigkeiten von PHP-Projekten zu deklarieren, zu verwalten und zu installieren. Dadurch wird sichergestellt, dass Sie überall den richtigen Stapel haben.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">Composer/metadata-minifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Kleine Dienstprogrammbibliothek, die die Metadaten-Minimierung und -Erweiterung verarbeitet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">Composer/PC</a>
    </td>
    <td>Bibliothek</td>
    <td>PCRE-Wrapping-Bibliothek, die typsichere preg_*-Ersetzungen bietet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">Composer/Semver</a>
    </td>
    <td>Bibliothek</td>
    <td>Semver-Bibliothek, die Dienstprogramme, Versionsbegrenzungs-Parsing und Validierung bietet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">Composer/spdx-licenses</a>
    </td>
    <td>Bibliothek</td>
    <td>SPDX-Lizenzliste und -Validierungsbibliothek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">Composer/xdebug-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Startet einen Prozess ohne Xdebug neu.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>Bibliothek</td>
    <td>Endroid-QR-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>Bibliothek</td>
    <td>Gabel/Ströme (aufgegeben) zur Verwendung mit Elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Gabel von guzzle/RingPHP (aufgegeben) zur Verwendung mit elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>Bibliothek</td>
    <td>Guzzle ist eine PHP HTTP-Client-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/tries</a>
    </td>
    <td>Bibliothek</td>
    <td>Guzzle verspricht Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>Bibliothek</td>
    <td>Implementierung der PSR-7-Nachricht, die auch gemeinsame Methoden für das Dienstprogramm bereitstellt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Bibliothek zum Validieren eines JSON-Schemas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">Liga/Flysystem</a>
    </td>
    <td>Bibliothek</td>
    <td>Abstraktion der Dateispeicherung für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS S3-Dateisystemadapter für Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">Erkennung von Klassen/MIME-Typen</a>
    </td>
    <td>Bibliothek</td>
    <td>MIME-Typ-Erkennung für Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monolog/monolog</a>
    </td>
    <td>Bibliothek</td>
    <td>Sendet Ihre Protokolle an Dateien, Sockets, Postfächer, Datenbanken und verschiedene Webdienste</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>Bibliothek</td>
    <td>Deklarativ angeben, wie Elemente aus einem JSON-Dokument extrahiert werden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/konstante_time_encoding</a>
    </td>
    <td>Bibliothek</td>
    <td>Konstante Implementierungen der RFC 4648-Kodierung (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x-Polyfill für random_bytes() und random_int() von PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Stile in Inline-Stilattribute in Ihrem HTML-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertieren Sie CSS-Selektoren in XPath-Abfragen.</td>
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
    <td>Eigenschaften-Accessor- und Mutatorfunktionen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x-8.x-Polyfill für Mcrypt-Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>Bibliothek</td>
    <td>Sichere PHP-Kommunikationsbibliothek - reine-PHP-Implementierungen von RSA, AES, SSH2, SFTP, X.509 usw.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Benutzeroberfläche für das Zwischenspeichern von Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/uhr</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Oberfläche zum Lesen der Uhr.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Container-Oberfläche (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardschnittstellen für die Ereignisverarbeitung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Schnittstelle für HTTP-Clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>Bibliothek</td>
    <td>PSR-17: Gemeinsame Schnittstellen für PSR-7 HTTP-Nachrichtenfabriken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Schnittstelle für HTTP-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Benutzeroberfläche für die Protokollierung von Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein Polyfill für getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">Rammsey/Sammlung</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zum Darstellen und Bearbeiten von Kollektionen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zum Generieren und Arbeiten mit Universally Unique Identifiers (UUIDs).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Implementierung von CommonJS Promises/A für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberwurm/php-css-parser</a>
    </td>
    <td>Bibliothek</td>
    <td>Parser für CSS-Dateien in PHP geschrieben</td>
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
    <td>PHAR-Dateiformat-Dienstprogramme, wenn PHP Sie anruft</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Einfacher Unix-Signalhandler, der bei fehlender Unterstützung von Signalen für einfache plattformübergreifende Entwicklung leise fehlschlägt</td>
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
    <td>Eine PHP-Bibliothek zum Generieren einmaliger Passwörter gemäß RFC 4226 (HOTP-Algorithmus) und RFC 6238 (TOTP-Algorithmus) und kompatibel mit Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Framework für die Verwaltung von Public Key-Infrastrukturen. Sie umfasst X.509 Public-Key-Zertifikate, Attributzertifikate, Zertifizierungsanfragen und die Validierung des Zertifizierungspfads.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilft Ihnen, Konfigurationswerte jeder Art zu finden, zu laden, zu kombinieren, automatisch auszufüllen und zu validieren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>Bibliothek</td>
    <td>Erleichtert die Erstellung schöner und testbarer Befehlszeilenschnittstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Selektoren in XPath-Ausdrücke</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-jection</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Standardisierung und Zentralisierung der Art und Weise, wie Objekte in Ihrer Anwendung erstellt werden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contract</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine allgemeine Funktion und Konvention für Hinweise zur Einstellung von Triggern</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet Tools zur Verwaltung von Fehlern und zur Vereinfachung des Debuggens von PHP-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet Tools, mit denen Ihre Anwendungskomponenten miteinander kommunizieren können, indem sie Ereignisse senden und ihnen zuhören</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contract</a>
    </td>
    <td>Bibliothek</td>
    <td>Generische Abstraktionen im Zusammenhang mit dem Dispatcher-Ereignis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt grundlegende Hilfsprogramme für das Dateisystem bereit</td>
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
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet leistungsstarke Methoden zum synchronen oder asynchronen Abrufen von HTTP-Ressourcen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-contract</a>
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
    <td>Bietet einen strukturierten Prozess zum Konvertieren einer Anforderung in eine Antwort</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht Zugriff auf die Lokalisierungsdaten der ICU-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-type</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill für Typfunktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill für intl's grapheme_*-Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill für die Funktionen idn_to_ascii und idn_to_utf8</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill für intl's Normalizer-Klasse und zugehörige Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill für die Mbstring-Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill-Backporting einige PHP 7.2+-Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill-Backporting einige PHP 7.3+-Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill-Backport einiger PHP 8.0+-Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill-Backport einiger PHP 8.1+-Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony polyfill-Backporting einiger PHP 8.3+-Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>Bibliothek</td>
    <td>Führt Befehle in Unterprozessen aus</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-contract</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen im Zusammenhang mit Schreibdiensten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine objektorientierte API für Zeichenfolgen und behandelt Bytes, UTF-8-Codepunkte und Graphem-Cluster einheitlich</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet Mechanismen, um beliebige PHP-Variablen zu durchlaufen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporting</a>
    </td>
    <td>Bibliothek</td>
    <td>Exportiert jede serialisierbare PHP-Datenstruktur in reinen PHP-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>JSON Object Signing and Encryption Library für PHP und Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>Bibliothek</td>
    <td>Zuweisungen zur Validierung der Methodeneingabe/-ausgabe mit schönen Fehlermeldungen.</td>
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
      <th>Name</th>
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Name</th>
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
      <th>Name</th>
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

### proprietär

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
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>Fork vom Magento Braintree 2.2.0-Modul von Gene Commerce für PayPal.</td>
  </tr>
  </tbody>
</table>
