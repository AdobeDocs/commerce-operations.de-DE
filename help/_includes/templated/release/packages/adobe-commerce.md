---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---
# Adobe Commerce-Pakete

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce verwendet Composer, um PHP-Pakete zu verwalten.

Die `composer.json`-Datei deklariert die Liste der Pakete, während die `composer.lock`-Datei eine vollständige Liste der Pakete speichert (eine Vollversion jedes Pakets und seiner Abhängigkeiten), die zum Erstellen einer Installation von Adobe Commerce verwendet werden.

Die folgende Referenzdokumentation wird aus der `composer.lock` generiert und behandelt die erforderlichen Pakete in Adobe Commerce 2.4.7-p1.

## Abhängigkeiten

`magento/product-enterprise-edition 2.4.7-p1` weist die folgenden Abhängigkeiten auf:

```config
adobe-commerce/extensions-metapackage: ~2.0
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
ext-spl: *
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
magento/framework-foreign-key: 100.4.6
magento/magento-composer-installer: >=0.4.0
magento/magento2-ee-base: 2.4.7-p1
magento/module-admin-gws: 100.4.7
magento/module-admin-gws-configurable-product: 100.4.4
magento/module-admin-gws-staging: 100.4.4
magento/module-advanced-catalog: 100.4.4
magento/module-advanced-checkout: 100.4.7
magento/module-advanced-rule: 100.4.4
magento/module-advanced-sales-rule: 100.4.4
magento/module-application-server: 100.4.0
magento/module-application-server-new-relic: 100.4.0
magento/module-application-server-performance-monitor: 100.4.0
magento/module-application-server-state-monitor: 100.4.0
magento/module-application-server-state-monitor-graph-ql: 100.4.0
magento/module-async-order: 100.4.3
magento/module-async-order-graph-ql: 100.4.2
magento/module-aws-s3-customer-custom-attributes: 100.4.4
magento/module-aws-s3-gift-card-import-export: 100.4.4
magento/module-aws-s3-scheduled-import-export: 100.4.4
magento/module-banner: 101.2.7
magento/module-banner-customer-segment: 100.4.5
magento/module-banner-graph-ql: 100.4.3
magento/module-banner-staging: 100.4.1
magento/module-bundle-import-export-staging: 100.4.4
magento/module-bundle-staging: 100.4.7
magento/module-catalog-event: 101.1.6
magento/module-catalog-import-export-staging: 100.4.4
magento/module-catalog-inventory-staging: 100.4.5
magento/module-catalog-permissions: 100.4.7
magento/module-catalog-permissions-graph-ql: 100.4.5
magento/module-catalog-rule-staging: 100.4.7
magento/module-catalog-staging: 100.4.7
magento/module-catalog-staging-graph-ql: 100.4.6
magento/module-catalog-url-rewrite-staging: 100.4.6-p1
magento/module-checkout-address-search: 100.4.6
magento/module-checkout-address-search-gift-registry: 100.4.3
magento/module-checkout-staging: 100.4.6
magento/module-cms-staging: 100.4.7
magento/module-configurable-product-staging: 100.4.6
magento/module-custom-attribute-management: 100.4.6
magento/module-customer-balance: 100.4.7
magento/module-customer-balance-graph-ql: 100.4.4
magento/module-customer-custom-attributes: 100.4.7
magento/module-customer-custom-attributes-graph-ql: 100.4.0
magento/module-customer-finance: 100.4.4
magento/module-customer-segment: 102.1.7
magento/module-customer-segment-graph-ql: 100.4.0
magento/module-deferred-total-calculating: 100.4.2
magento/module-downloadable-staging: 100.4.6
magento/module-elasticsearch-catalog-permissions: 100.4.3
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.2
magento/module-enterprise: 100.4.5
magento/module-gift-card: 101.3.7
magento/module-gift-card-account: 101.2.7
magento/module-gift-card-account-graph-ql: 100.4.5
magento/module-gift-card-graph-ql: 100.4.7
magento/module-gift-card-import-export: 100.4.4
magento/module-gift-card-staging: 100.4.4
magento/module-gift-message-staging: 100.4.4
magento/module-gift-registry: 101.2.7
magento/module-gift-registry-graph-ql: 100.4.3
magento/module-gift-wrapping: 101.2.6
magento/module-gift-wrapping-graph-ql: 100.4.4
magento/module-gift-wrapping-staging: 100.4.4
magento/module-google-optimizer-staging: 100.4.4
magento/module-google-tag-manager: 100.4.7
magento/module-grouped-product-staging: 100.4.5
magento/module-import-csv: 100.4.1
magento/module-import-csv-api: 100.4.1
magento/module-import-json: 100.4.0
magento/module-import-json-api: 100.4.0
magento/module-invitation: 100.4.6
magento/module-layered-navigation-staging: 100.4.4
magento/module-logging: 101.2.7
magento/module-login-as-customer-logging: 100.4.7
magento/module-login-as-customer-website-restriction: 100.4.5
magento/module-media-content-catalog-staging: 100.4.4
magento/module-msrp-staging: 100.4.5
magento/module-multicoupon: 100.4.0
magento/module-multicoupon-graph-ql: 100.4.0
magento/module-multicoupon-ui: 100.4.0
magento/module-multiple-wishlist: 100.4.7
magento/module-multiple-wishlist-graph-ql: 100.4.3
magento/module-payment-staging: 100.4.4
magento/module-persistent-history: 100.4.4
magento/module-price-permissions: 100.4.3
magento/module-product-video-staging: 100.4.4
magento/module-promotion-permissions: 100.4.4
magento/module-quote-commerce-graph-ql: 100.4.0
magento/module-quote-gift-card-options: 100.4.4
magento/module-quote-staging: 100.4.4
magento/module-reminder: 101.2.6
magento/module-remote-storage-commerce: 100.4.3
magento/module-resource-connections: 100.4.4
magento/module-review-staging: 100.4.4
magento/module-reward: 101.2.7
magento/module-reward-graph-ql: 100.4.6
magento/module-reward-staging: 100.4.4
magento/module-rma: 101.2.7
magento/module-rma-graph-ql: 100.4.6-p1
magento/module-rma-staging: 100.4.4
magento/module-sales-archive: 101.0.5
magento/module-sales-rule-staging: 100.4.6
magento/module-scalable-checkout: 100.4.6
magento/module-scalable-inventory: 100.4.5
magento/module-scalable-oms: 100.4.5
magento/module-scheduled-import-export: 101.2.7
magento/module-search-staging: 100.4.5
magento/module-staging: 101.2.7
magento/module-staging-graph-ql: 100.4.4
magento/module-support: 101.2.6
magento/module-swat: 100.4.5
magento/module-target-rule: 101.2.7
magento/module-target-rule-graph-ql: 100.4.4
magento/module-versions-cms: 101.2.7
magento/module-versions-cms-page-cache: 100.4.3
magento/module-versions-cms-url-rewrite: 100.4.5
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.3
magento/module-visual-merchandiser: 100.4.7
magento/module-website-restriction: 100.4.6
magento/module-weee-staging: 100.4.4
magento/module-wishlist-gift-card: 100.4.3
magento/module-wishlist-gift-card-graph-ql: 100.4.3
magento/page-builder-commerce: 1.7.4-p1
magento/product-community-edition: 2.4.7-p1
magento/security-package-ee: 1.0.2-p1
magento/theme-adminhtml-spectrum: 100.4.2
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

### Apache-2.0, nur LGPL-2.1

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
    <td>PHP-Client für OpenSearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

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
      PayPal/Modul-Braintree
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
    <td>PHP 7.1 Enum-Implementierung</td>
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
      <th>-Name</th>
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
    <td>Das Backend der Stock-Zend_Cache_Backend_File-Datei hat eine extrem schlechte Leistung für die Reinigung von Tags, wodurch es unbrauchbar wird, wenn die Anzahl der zwischengespeicherten Elemente steigt. Dieses Backend nimmt viele Änderungen vor, die zu einer enormen Leistungssteigerung führen, insbesondere bei der Tag-Reinigung.</td>
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
      <a href="https://github.com/firebase/php-jwt.git">Firebase/php-jwt</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Bibliothek zum Codieren und Decodieren von JSON Web Tokens (JWT) in PHP. Sollte der aktuellen Spezifikation entsprechen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">Google/reCAPTCHA</a>
    </td>
    <td>Bibliothek</td>
    <td>Client-Bibliothek für reCAPTCHA, einen kostenlosen Service, der Websites vor Spam und Missbrauch schützt.</td>
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
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>Bibliothek</td>
    <td>Starke Verschlüsselungstools und Passwort-Hashing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>Bibliothek</td>
    <td>Implementierungen von Datenbankabstraktionsebenen, SQL-Abstraktionen, Ergebnissatzabstraktionen sowie RowDataGateway- und TableDataGateway-Implementierungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>Bibliothek</td>
    <td>Automatisierte Injektion von Abhängigkeiten für PSR-11-Container</td>
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
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Klassendateien suchen</td>
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
    <td>Bietet eine einfache Schnittstelle zum Ausführen von HTTP-Anfragen (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">LAMINAS/LAMINAS-I18N</a>
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
      <a href="https://github.com/laminas/laminas-loader.git">LAMINAS/LAMINAS-LOADER</a>
    </td>
    <td>Bibliothek</td>
    <td>Strategien zum automatischen Laden und Laden von Plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet allgemeine Funktionen zum Erstellen und Senden von Text und MIME-kompatiblen mehrteiligen E-Mail-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen Sie kryptografisch sichere Pseudozufallszahlen und verwalten Sie große Ganzzahlen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen und Analysieren von MIME-Nachrichten und -Teilen</td>
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
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>Bibliothek</td>
    <td></td>
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
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Komponente, die bei der Bearbeitung und Validierung von „URIs“ (Uniform Resource Identifiers) hilft</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>Bibliothek</td>
    <td>Validierungsklassen für eine Vielzahl von Domains und die Möglichkeit, Validatoren zu verketten, um komplexe Validierungskriterien zu erstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexible Ansichtsebene unterstützt und bietet mehrere Ansichtsebenen, Helper und mehr</td>
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
    <td>Vormals videlalvaro/php-amqplib.  Diese Bibliothek ist eine reine PHP-Implementierung des AMQP-Protokolls. Es wurde gegen RabbitMQ getestet.</td>
  </tr>
  </tbody>
</table>

### MIT

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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>Bibliothek</td>
    <td>Braintree PHP Client-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">Stein/Mathematik</a>
    </td>
    <td>Bibliothek</td>
    <td>Arithmetische Bibliothek mit beliebiger Genauigkeit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine leistungsstarke Alternative zu var_export(), die Schließungen und Objekte ohne __set_state() exportieren kann</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">Christian-Riesen/base32</a>
    </td>
    <td>Bibliothek</td>
    <td>Base32 Encoder/Decoder nach RFC 4648</td>
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
    <td>Abspaltung von Guzzle/Streams (aufgegeben) zur Verwendung mit Elasticsearch-php</td>
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
      <a href="https://github.com/thephpleague/mime-type-detection.git">League/MIME-Typ-Erkennung</a>
    </td>
    <td>Bibliothek</td>
    <td>MIME-Erkennung für Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monolog/monolog</a>
    </td>
    <td>Bibliothek</td>
    <td>Sendet Ihre Protokolle an Dateien, Sockets, Posteingänge, Datenbanken und verschiedene Web-Services</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>Bibliothek</td>
    <td>Deklarativ angeben, wie Elemente aus einem JSON-Dokument extrahiert werden sollen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>Bibliothek</td>
    <td>Implementierungen der RFC-4648-Codierung in konstanten Zeiten (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x Polyfill für random_bytes() und random_int() von PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Stile in Inline-Stilattribute im HTML-Code</td>
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
    <td>PHP 5.x-8.x Polyfill für mcrypt Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Secure Communications Library - Pure-PHP-Implementierungen von RSA, AES, SSH2, SFTP, X.509 etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">PSR/Cache</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Schnittstelle zum Zwischenspeichern von Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">PSR/CLOCK</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle zum Lesen der Uhr.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">PSR/Container</a>
    </td>
    <td>Bibliothek</td>
    <td>Common Container Interface (PHP-Abb. PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">PSR/event-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardschnittstellen für die Ereignisbehandlung.</td>
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
    <td>PSR-17: Gemeinsame Schnittstellen für PSR-7-HTTP-Nachrichten-Factories</td>
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
    <td>Allgemeine Benutzeroberfläche für die Protokollierung von Bibliotheken</td>
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
    <td>JSON-Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>Bibliothek</td>
    <td>PHAR-Dateiformat-Dienstprogramme, für den Fall, dass PHP Sie startet</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">SELD/Signal-Handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Einfacher Unix-Signal-Handler, der im Hintergrund ausfällt, wenn Signale nicht unterstützt werden, um eine einfache plattformübergreifende Entwicklung zu ermöglichen</td>
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
    <td>Eine PHP-Bibliothek zur Erzeugung von Einmalkennwörtern nach RFC 4226 (HOTP-Algorithmus) und RFC 6238 (TOTP-Algorithmus), die mit dem Google Authenticator kompatibel sind</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Framework für die Verwaltung von Public-Key-Infrastrukturen. Sie umfasst X.509-Zertifikate mit öffentlichem Schlüssel, Attributzertifikate, Zertifizierungsanfragen und die Validierung des Zertifizierungspfads.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilft Ihnen beim Suchen, Laden, Kombinieren, automatischen Ausfüllen und Überprüfen von Konfigurationswerten jeglicher Art</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>Bibliothek</td>
    <td>Erleichtert die Erstellung von schönen und testbaren Befehlszeilenschnittstellen</td>
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
    <td>Findet Dateien und Verzeichnisse über eine intuitive, flüssige Oberfläche</td>
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
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 7.2+-Funktionen zur Reduzierung von PHP-Versionen</td>
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
    <td>Symfony Polyfill unterstützt einige PHP 8.1+ Funktionen zur Reduzierung von PHP-Versionen</td>
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
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine objektorientierte API für Zeichenfolgen und verarbeitet Bytes, UTF-8-Code-Punkte und Graphem-Cluster einheitlich</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt Mechanismen bereit, um beliebige PHP-Variablen zu durchlaufen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-Exporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht den Export jeder serialisierbaren PHP-Datenstruktur in reinen PHP-Code</td>
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
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>Bibliothek</td>
    <td>Assertionen zur Validierung der Methodeneingabe/-ausgabe mit netten Fehlermeldungen.</td>
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
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2-Modul</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
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

### proprietär

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

### geschützt

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
      paypal/module-braintree-core
    </td>
    <td>Magento2-Modul</td>
    <td>Abspaltung vom Magento Braintree 2.2.0 Modul von Gene Commerce für PayPal.</td>
  </tr>
  </tbody>
</table>
