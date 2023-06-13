---
source-git-commit: e883ab0e6fca468bd3701e6789ac5132c7f1ee4d
workflow-type: tm+mt
source-wordcount: '2492'
ht-degree: 0%

---
# Adobe Commerce-Packages

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock_beta.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock_beta.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce verwendet Composer zur Verwaltung von PHP-Paketen.

Die `composer.json` -Datei deklariert die Liste der Pakete, während die `composer.lock` -Datei speichert eine vollständige Liste der Pakete (eine Vollversion jedes Pakets und seiner Abhängigkeiten), die zum Erstellen einer Installation von Adobe Commerce oder Magento Open Source verwendet werden.

Die folgende Referenzdokumentation wird aus der `composer.lock` und es umfasst erforderliche Pakete, die in Adobe Commerce 2.4.7-beta1 enthalten sind.

## Abhängigkeiten

`magento/product-enterprise-edition 2.4.7-beta1` weist die folgenden Abhängigkeiten auf:

```config
adobe-commerce/extensions-metapackage: ~2.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.14
colinmollenhour/credis: ^1.13
colinmollenhour/php-redis-session-abstract: ^1.5
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
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.16
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ^4.5
laminas/laminas-db: ^2.15
laminas/laminas-di: ^3.7
laminas/laminas-escaper: ^2.10
laminas/laminas-eventmanager: ^3.5
laminas/laminas-feed: ^2.17
laminas/laminas-file: ^2.11
laminas/laminas-filter: ^2.17
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.3
laminas/laminas-oauth: ^2.4
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.11
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.9.0
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework-foreign-key: 100.4.5
magento/magento-composer-installer: >=0.4.0
magento/magento2-ee-base: 2.4.7-beta1
magento/module-admin-gws: 100.4.7-beta1
magento/module-admin-gws-configurable-product: 100.4.3
magento/module-admin-gws-staging: 100.4.3
magento/module-advanced-catalog: 100.4.3
magento/module-advanced-checkout: 100.4.7-beta1
magento/module-advanced-rule: 100.4.4-beta1
magento/module-advanced-sales-rule: 100.4.4-beta1
magento/module-application-server: 100.4.0-beta1
magento/module-async-order: 100.4.3-beta1
magento/module-async-order-graph-ql: 100.4.1
magento/module-aws-s3-customer-custom-attributes: 100.4.3
magento/module-aws-s3-gift-card-import-export: 100.4.3
magento/module-aws-s3-scheduled-import-export: 100.4.3
magento/module-banner: 101.2.7-beta1
magento/module-banner-customer-segment: 100.4.5-beta1
magento/module-banner-graph-ql: 100.4.3-beta1
magento/module-banner-staging: 100.4.1-beta1
magento/module-bundle-import-export-staging: 100.4.3
magento/module-bundle-staging: 100.4.7-beta1
magento/module-catalog-event: 101.1.6-beta1
magento/module-catalog-import-export-staging: 100.4.4-beta1
magento/module-catalog-inventory-staging: 100.4.5-beta1
magento/module-catalog-permissions: 100.4.7-beta1
magento/module-catalog-permissions-graph-ql: 100.4.5-beta1
magento/module-catalog-rule-staging: 100.4.7-beta1
magento/module-catalog-staging: 100.4.7-beta1
magento/module-catalog-staging-graph-ql: 100.4.6-beta1
magento/module-catalog-url-rewrite-staging: 100.4.6-beta1
magento/module-checkout-address-search: 100.4.6-beta1
magento/module-checkout-address-search-gift-registry: 100.4.2
magento/module-checkout-staging: 100.4.6-beta1
magento/module-cms-staging: 100.4.7-beta1
magento/module-configurable-product-staging: 100.4.6-beta1
magento/module-custom-attribute-management: 100.4.6-beta1
magento/module-customer-balance: 100.4.7-beta1
magento/module-customer-balance-graph-ql: 100.4.3
magento/module-customer-custom-attributes: 100.4.7-beta1
magento/module-customer-custom-attributes-graph-ql: 100.4.0-beta1
magento/module-customer-finance: 100.4.3
magento/module-customer-segment: 102.1.7-beta1
magento/module-deferred-total-calculating: 100.4.2-beta1
magento/module-downloadable-staging: 100.4.6-beta1
magento/module-elasticsearch-catalog-permissions: 100.4.3-beta1
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.2-beta1
magento/module-enterprise: 100.4.5-beta1
magento/module-gift-card: 101.3.7-beta1
magento/module-gift-card-account: 101.2.7-beta1
magento/module-gift-card-account-graph-ql: 100.4.4
magento/module-gift-card-graph-ql: 100.4.7-beta1
magento/module-gift-card-import-export: 100.4.3
magento/module-gift-card-staging: 100.4.4-beta1
magento/module-gift-message-staging: 100.4.4-beta1
magento/module-gift-registry: 101.2.7-beta1
magento/module-gift-registry-graph-ql: 100.4.2
magento/module-gift-wrapping: 101.2.6-beta1
magento/module-gift-wrapping-graph-ql: 100.4.3
magento/module-gift-wrapping-staging: 100.4.4-beta1
magento/module-google-optimizer-staging: 100.4.4-beta1
magento/module-google-tag-manager: 100.4.7-beta1
magento/module-grouped-product-staging: 100.4.5-beta1
magento/module-import-csv: 100.4.1-beta1
magento/module-import-csv-api: 100.4.1-beta1
magento/module-invitation: 100.4.6-beta1
magento/module-layered-navigation-staging: 100.4.4-beta1
magento/module-logging: 101.2.7-beta1
magento/module-login-as-customer-logging: 100.4.7-beta1
magento/module-login-as-customer-website-restriction: 100.4.4
magento/module-media-content-catalog-staging: 100.4.4-beta1
magento/module-msrp-staging: 100.4.5-beta1
magento/module-multiple-wishlist: 100.4.7-beta1
magento/module-multiple-wishlist-graph-ql: 100.4.2
magento/module-payment-staging: 100.4.4-beta1
magento/module-persistent-history: 100.4.4-beta1
magento/module-price-permissions: 100.4.3-beta1
magento/module-product-video-staging: 100.4.4-beta1
magento/module-promotion-permissions: 100.4.4-beta1
magento/module-quote-gift-card-options: 100.4.3
magento/module-quote-staging: 100.4.4-beta1
magento/module-reminder: 101.2.6-beta1
magento/module-remote-storage-commerce: 100.4.2
magento/module-resource-connections: 100.4.4-beta1
magento/module-review-staging: 100.4.4-beta1
magento/module-reward: 101.2.7-beta1
magento/module-reward-graph-ql: 100.4.5
magento/module-reward-staging: 100.4.4-beta1
magento/module-rma: 101.2.7-beta1
magento/module-rma-graph-ql: 100.4.6-beta1
magento/module-rma-staging: 100.4.4-beta1
magento/module-sales-archive: 101.0.5-beta1
magento/module-sales-rule-staging: 100.4.6-beta1
magento/module-scalable-checkout: 100.4.6-beta1
magento/module-scalable-inventory: 100.4.5-beta1
magento/module-scalable-oms: 100.4.5-beta1
magento/module-scheduled-import-export: 101.2.7-beta1
magento/module-search-staging: 100.4.5-beta1
magento/module-staging: 101.2.7-beta1
magento/module-staging-graph-ql: 100.4.3
magento/module-support: 101.2.6-beta1
magento/module-swat: 100.4.4
magento/module-target-rule: 101.2.7-beta1
magento/module-target-rule-graph-ql: 100.4.4-beta1
magento/module-versions-cms: 101.2.7-beta1
magento/module-versions-cms-page-cache: 100.4.2
magento/module-versions-cms-url-rewrite: 100.4.5-beta1
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.2
magento/module-visual-merchandiser: 100.4.7-beta1
magento/module-website-restriction: 100.4.5
magento/module-weee-staging: 100.4.4-beta1
magento/module-wishlist-gift-card: 100.4.2
magento/module-wishlist-gift-card-graph-ql: 100.4.2
magento/page-builder-commerce: 1.7.4-beta1
magento/product-community-edition: 2.4.7-beta1
magento/security-package-ee: 1.0.2-beta1
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0, <2.0.1
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
ramsey/uuid: ^4.2
symfony/console: ^5.4
symfony/intl: ^5.4
symfony/process: ^5.4
symfony/string: ^5.4
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
      elasticsearch/elasticsearch
    </td>
    <td>Bibliothek</td>
    <td>PHP Client für Elasticsearch</td>
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
      <a href="https://github.com/beberlei/assert.git">beberlei/assert</a>
    </td>
    <td>Bibliothek</td>
    <td>Thin Assertion Library für die Eingabevalidierung in Geschäftsmodellen.</td>
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
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
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
      <a href="https://github.com/laminas/laminas-feed.git">Lamina/Lamina-Feed</a>
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
    <td>Bietet eine einfache und flexible ACL-Implementierung (Access Control List) für die Berechtigungsverwaltung</td>
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
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>Bibliothek</td>
    <td>Alias veraltete ZF-Klassennamen zu Laminas Project-Entsprechungen.</td>
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
    <td>Standardkonformer HTML-Filter, geschrieben in PHP</td>
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
      <a href="https://github.com/composer/pcre.git">Composer/pcre</a>
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
      <a href="https://github.com/doctrine/annotations.git">Dokumentation/Anmerkungen</a>
    </td>
    <td>Bibliothek</td>
    <td>Parser für Dokumentanmerkungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/deprecations.git">doctrine/deprections</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine kleine Ebene über der Trigger_error(E_USER_DEPRECATED)- oder PSR-3-Protokollierung mit Optionen zum Deaktivieren aller veralteten Versionen oder selektiv für Pakete.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">doktrin/lexer</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Doctrine Lexer Parser-Bibliothek, die in Top-Down-, Rekursiv-Descent Parsers verwendet werden kann.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>Bibliothek</td>
    <td>Endroid QR Code</td>
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
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
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
    <td>Die moderne DOM-API für PHP-Projekte.</td>
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
    <td>Gemeinsame Schnittstellen für PSR-7-HTTP-Nachrichtenfabriken</td>
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
      <a href="https://github.com/reactphp/promise.git">response/promise</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Implementierung von CommonJS Promises/A für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberwurm/php-css-parser</a>
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
    <td>Stellt eine PHP-Ersetzungsschicht für die C intl-Erweiterung bereit, die zusätzliche Daten aus der ICU-Bibliothek enthält</td>
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
      <a href="https://github.com/thecodingmachine/safe.git">Thekodingmachine/safe</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Kernfunktionen, die Ausnahmen ausgeben, anstatt FALSE bei Fehler zurückzugeben</td>
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
  <tr>
    <td>
      temando/module-shipping-remover
    </td>
    <td>magento2-module</td>
    <td>Entfernt die Versanderweiterung "Temando Multi-Carrier"aus Magento 2</td>
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
  <tr>
    <td>
      temando/module-shipping
    </td>
    <td>metapackage</td>
    <td>Temando-Erweiterung für die Schifffahrt mit mehreren Luftfahrtunternehmen für Magento 2</td>
  </tr>
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

### Proprietär

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
    <td>Verzweigung aus dem Modul Magento Braintree 2.2.0 von Gene Commerce für PayPal.</td>
  </tr>
  </tbody>
</table>
