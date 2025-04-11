---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '3444'
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

Die `composer.json`-Datei deklariert die Liste der Pakete, während die `composer.lock`-Datei eine vollständige Liste der Pakete speichert (eine Vollversion jedes Pakets und seiner Abhängigkeiten), die zum Erstellen einer Installation von Magento Open Source verwendet werden.

Die folgende Referenzdokumentation wird aus der `composer.lock` generiert und behandelt die erforderlichen Pakete in Magento Open Source 2.4.8.

## Abhängigkeiten

`magento/product-community-edition 2.4.8` weist die folgenden Abhängigkeiten auf:

- adobe-commerce/os-extensions-metapackage: 1.0.1
- colinmollenhour/cache-backend-file: ^1.4
- colinmollenhour/cache-backend-redis: ^1.16
- Colinmollenhour/Credits: ^1,15
- colinmollenhour/php-redis-session-abstract: ^2.0
- Komponist/Komponist: ^2.0, !=2.2.16
- duoSecurity/duo_api_php: ^1.1
- duoSecurity/duo_universal_php: ^1.0
- elasticsearch/elasticsearch: ^8.15
- ext-bcmMath: *
- ext-type: *
- ext-curl: *
- ext-dom: *
- ext-ftp: *
- ext-gd: *
- ext-hash: *
- ext-iconv: *
- ext-intl: *
- ext-mbString: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simpleXML: *
- ext-soap: *
- Ext-Natrium: *
- ext-xsl: *
- ext-zip: *
- ezyang/htmlPurifier: ^4.17
- guzzlehttp/guzzle: ^7.5
- laminas/laminas-captcha: ^2.18
- Laminas/Laminas-Code: ^4.13
- laminas/laminas-di: ^3.15
- Laminas/Laminas-Escaper: ^2.13
- laminas/laminas-eventManager: ^3.11
- lamellen/lamellen-Vorschub: ^2.22
- laminas/laminas-filter: ^2.33
- laminas/laminas-http: ^2.15
- Laminas/Laminas-I18N: ^2.17
- laminas/laminas-modulemanager: ^2.11
- Laminas/Laminas-MVC: ^3.6
- laminas/laminas-permissions-acl: ^2.10
- laminas/laminas-serviceManager: ^3.16
- laminas/laminas-soap: ^2.10
- laminas/laminas-stdlib: ^3.11
- laminas/laminas-uri: ^2.9
- laminas/laminas-validator: ^2.23
- Liga/FlySystem: ^3.0
- League/Flysystem-AWS-S3-V3: ^3.0
- lib-libxml: *
- Magento/Composer: ^1.10.1-beta1
- magento/composer-dependency-version-audit-plugin: ^0.1
- Magento/Framework: 103.0.8
- Magento/Framework-AMQP: 100.4.6
- Magento/Framework-Bulk: 101.0.4
- magento/framework-message-queue: 100.4.8
- magento/inventory-metapackage: 1.2.8
- Magento/language-de_de: 100.4.0
- Magento/language-en_US: 100.4.0
- Magento/language-es_es: 100.4.0
- Magento/language-FR_FR: 100.4.0
- magento/language-nl_nl: 100.4.0
- Magento/language-PT_BR: 100.4.0
- Magento/language-zh_hans_cn: 100.4.0
- Magento/Magento-Composer-Installer: >=0.4.0
- Magento/Magento-ZF-DB: ^3.21.0
- Magento/Magento2-Base: 2.4.8
- [magento/module-admin-analytics](https://developer.adobe.com/commerce/php/module-reference/module-admin-analytics/): 100.4.7
- [magento/module-admin-notification](https://developer.adobe.com/commerce/php/module-reference/module-admin-notification/): 100.4.7
- [magento/module-advanced-price-import-export](https://developer.adobe.com/commerce/php/module-reference/module-advanced-pricing-import-export/): 100.4.8
- [magento/module-advanced-search](https://developer.adobe.com/commerce/php/module-reference/module-advanced-search/): 100.4.6
- [magento/module-amqp](https://developer.adobe.com/commerce/php/module-reference/module-amqp/): 100.4.5
- [magento/module-analytics](https://developer.adobe.com/commerce/php/module-reference/module-analytics/): 100.4.8
- [magento/module-application-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor/): 100.4.1
- [magento/module-application-performance-monitor-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor-new-relic/): 100.4.1
- [magento/module-async-config](https://developer.adobe.com/commerce/php/module-reference/module-async-config/): 100.4.1
- [magento/module-asynchronous-operations](https://developer.adobe.com/commerce/php/module-reference/module-asynchronous-operations/): 100.4.8
- [magento/module-authorization](https://developer.adobe.com/commerce/php/module-reference/module-authorization/): 100.4.8
- [magento/module-aws-s3](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3/): 100.4.6
- [magento/module-backend](https://developer.adobe.com/commerce/php/module-reference/module-backend/): 102.0.8
- [magento/module-backup](https://developer.adobe.com/commerce/php/module-reference/module-backup/): 100.4.8
- [magento/module-bundle](https://developer.adobe.com/commerce/php/module-reference/module-bundle/): 101.0.8
- [magento/module-bundle-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-bundle-graph-ql/): 100.4.8
- [magento/module-bundle-import-export](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export/): 100.4.7
- [magento/module-cache-invalidate](https://developer.adobe.com/commerce/php/module-reference/module-cache-invalidate/): 100.4.6
- [magento/module-captcha](https://developer.adobe.com/commerce/php/module-reference/module-captcha/): 100.4.8
- [magento/module-cardinal-commerce](https://developer.adobe.com/commerce/php/module-reference/module-cardinal-commerce/): 100.4.6
- [magento/module-catalog](https://developer.adobe.com/commerce/php/module-reference/module-catalog/): 104.0.8
- [magento/module-catalog-analytics](https://developer.adobe.com/commerce/php/module-reference/module-catalog-analytics/): 100.4.5
- [magento/module-catalog-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-cms-graph-ql/): 100.4.4
- [magento/module-catalog-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-customer-graph-ql/): 100.4.7
- [magento/module-catalog-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-graph-ql/): 100.4.8
- [magento/module-catalog-import-export](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export/): 101.1.8
- [magento/module-catalog-inventory](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory/): 100.4.8
- [magento/module-catalog-inventory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-graph-ql/): 100.4.5
- [magento/module-catalog-rule](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule/): 101.2.8
- [magento/module-catalog-rule-configurable](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-configurable/): 100.4.7
- [magento/module-catalog-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-graph-ql/): 100.4.5
- [magento/module-catalog-search](https://developer.adobe.com/commerce/php/module-reference/module-catalog-search/): 102.0.8
- [magento/module-catalog-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite/): 100.4.8
- [magento/module-catalog-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-graph-ql/): 100.4.6
- [magento/module-catalog-widget](https://developer.adobe.com/commerce/php/module-reference/module-catalog-widget/): 100.4.8
- [magento/module-checkout](https://developer.adobe.com/commerce/php/module-reference/module-checkout/): 100.4.8
- [magento/module-checkout-agreement](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements/): 100.4.7
- [magento/module-checkout-agreement-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements-graph-ql/): 100.4.4
- [magento/module-cms](https://developer.adobe.com/commerce/php/module-reference/module-cms/): 104.0.8
- [magento/module-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-graph-ql/): 100.4.5
- [magento/module-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite/): 100.4.7
- [magento/module-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite-graph-ql/): 100.4.6
- [magento/module-compare-list-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-compare-list-graph-ql/): 100.4.4
- [magento/module-config](https://developer.adobe.com/commerce/php/module-reference/module-config/): 101.2.8
- [magento/module-configurable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-configurable-import-export/): 100.4.6
- [magento/module-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product/): 100.4.8
- [magento/module-configurable-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-graph-ql/): 100.4.8
- [magento/module-configurable-product-sales](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-sales/): 100.4.5
- [magento/module-contact](https://developer.adobe.com/commerce/php/module-reference/module-contact/): 100.4.7
- [magento/module-contact-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-contact-graph-ql/): 100.4.1
- [magento/module-cookie](https://developer.adobe.com/commerce/php/module-reference/module-cookie/): 100.4.8
- [magento/module-cron](https://developer.adobe.com/commerce/php/module-reference/module-cron/): 100.4.8
- [magento/module-csp](https://developer.adobe.com/commerce/php/module-reference/module-csp/): 100.4.7
- [magento/module-currency-symbol](https://developer.adobe.com/commerce/php/module-reference/module-currency-symbol/): 100.4.6
- [magento/module-customer](https://developer.adobe.com/commerce/php/module-reference/module-customer/): 103.0.8
- [magento/module-customer-analytics](https://developer.adobe.com/commerce/php/module-reference/module-customer-analytics/): 100.4.5
- [magento/module-customer-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-downloadable-graph-ql/): 100.4.4
- [magento/module-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-graph-ql/): 100.4.8
- [magento/module-customer-import-export](https://developer.adobe.com/commerce/php/module-reference/module-customer-import-export/): 100.4.8
- [magento/module-deploy](https://developer.adobe.com/commerce/php/module-reference/module-deploy/): 100.4.8
- [magento/module-developer](https://developer.adobe.com/commerce/php/module-reference/module-developer/): 100.4.8
- [magento/module-DHL](https://developer.adobe.com/commerce/php/module-reference/module-dhl/): 100.4.7
- [magento/module-directory](https://developer.adobe.com/commerce/php/module-reference/module-directory/): 100.4.8
- [magento/module-directory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-directory-graph-ql/): 100.4.6
- [magento/module-downloadable](https://developer.adobe.com/commerce/php/module-reference/module-downloadable/): 100.4.8
- [magento/module-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-graph-ql/): 100.4.8
- [magento/module-downloadable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-import-export/): 100.4.7
- [magento/module-eav](https://developer.adobe.com/commerce/php/module-reference/module-eav/): 102.1.8
- [magento/module-eav-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-eav-graph-ql/): 100.4.5
- [magento/module-elasticsearch](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch/): 101.0.8
- [magento/module-elasticsearch-8](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-8/): 101.0.0
- [magento/module-email](https://developer.adobe.com/commerce/php/module-reference/module-email/): 101.1.8
- [magento/module-encryption-key](https://developer.adobe.com/commerce/php/module-reference/module-encryption-key/): 100.4.6
- [magento/module-fedex](https://developer.adobe.com/commerce/php/module-reference/module-fedex/): 100.4.6
- [magento/module-gift-message](https://developer.adobe.com/commerce/php/module-reference/module-gift-message/): 100.4.7
- [magento/module-gift-message-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-graph-ql/): 100.4.6
- [magento/module-google-adwords](https://developer.adobe.com/commerce/php/module-reference/module-google-adwords/): 100.4.5
- [magento/module-google-analytics](https://developer.adobe.com/commerce/php/module-reference/module-google-analytics/): 100.4.4
- [magento/module-google-gtag](https://developer.adobe.com/commerce/php/module-reference/module-google-gtag/): 100.4.3
- [magento/module-google-optimizer](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer/): 100.4.7
- [magento/module-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql/): 100.4.8
- [magento/module-graph-ql-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-cache/): 100.4.5
- [magento/module-graph-ql-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-new-relic/): 100.4.1
- [magento/module-graph-ql-resolver-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-resolver-cache/): 100.4.1
- [magento/module-grouped-catalog-inventory](https://developer.adobe.com/commerce/php/module-reference/module-grouped-catalog-inventory/): 100.4.5
- [magento/module-grouped-import-export](https://developer.adobe.com/commerce/php/module-reference/module-grouped-import-export/): 100.4.6
- [magento/module-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product/): 100.4.8
- [magento/module-grouped-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-graph-ql/): 100.4.8
- [magento/module-import-export](https://developer.adobe.com/commerce/php/module-reference/module-import-export/): 101.0.8
- [magento/module-indexer](https://developer.adobe.com/commerce/php/module-reference/module-indexer/): 100.4.8
- [Magento/module-Instant-Purchase](https://developer.adobe.com/commerce/php/module-reference/module-instant-purchase/): 100.4.7
- [magento/module-integration](https://developer.adobe.com/commerce/php/module-reference/module-integration/): 100.4.8
- [magento/module-integration-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-integration-graph-ql/): 100.4.1
- [magento/module-jwt-framework-adapter](https://developer.adobe.com/commerce/php/module-reference/module-jwt-framework-adapter/): 100.4.4
- [magento/module-jwt-user-token](https://developer.adobe.com/commerce/php/module-reference/module-jwt-user-token/): 100.4.3
- [magento/module-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation/): 100.4.8
- [magento/module-login-as-customer](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer/): 100.4.8
- [magento/module-login-as-customer-admin-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-admin-ui/): 100.4.8
- [magento/module-login-as-customer-api](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-api/): 100.4.7
- [magento/module-login-as-customer-Assistance](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-assistance/): 100.4.7
- [magento/module-login-as-customer-frontend-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-frontend-ui/): 100.4.7
- [magento/module-login-as-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-graph-ql/): 100.4.5
- [magento/module-login-as-customer-log](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-log/): 100.4.6
- [magento/module-login-as-customer-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-page-cache/): 100.4.7
- [magento/module-login-as-customer-quote](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-quote/): 100.4.6
- [magento/module-login-as-customer-sales](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-sales/): 100.4.7
- [magento/module-marketplace](https://developer.adobe.com/commerce/php/module-reference/module-marketplace/): 100.4.6
- [magento/module-media-content](https://developer.adobe.com/commerce/php/module-reference/module-media-content/): 100.4.6
- [magento/module-media-content-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-api/): 100.4.7
- [magento/module-media-content-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog/): 100.4.6
- [magento/module-media-content-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-cms/): 100.4.6
- [magento/module-media-content-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization/): 100.4.7
- [magento/module-media-content-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-api/): 100.4.6
- [magento/module-media-content-synchronization-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-catalog/): 100.4.5
- [magento/module-media-content-synchronization-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-cms/): 100.4.5
- [magento/module-media-gallery](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery/): 100.4.7
- [magento/module-media-gallery-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-api/): 101.0.7
- [magento/module-media-gallery-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog/): 100.4.5
- [magento/module-media-gallery-catalog-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-integration/): 100.4.5
- [magento/module-media-gallery-catalog-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-ui/): 100.4.5
- [magento/module-media-gallery-cms-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-cms-ui/): 100.4.5
- [magento/module-media-gallery-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-integration/): 100.4.7
- [magento/module-media-gallery-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata/): 100.4.6
- [magento/module-media-gallery-metadata-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata-api/): 100.4.5
- [magento/module-media-gallery-renditions](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions/): 100.4.6
- [magento/module-media-gallery-renditions-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions-api/): 100.4.5
- [magento/module-media-gallery-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization/): 100.4.7
- [magento/module-media-gallery-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-api/): 100.4.6
- [magento/module-media-gallery-synchronization-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-metadata/): 100.4.4
- [magento/module-media-gallery-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui/): 100.4.7
- [magento/module-media-gallery-ui-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui-api/): 100.4.6
- [magento/module-media-storage](https://developer.adobe.com/commerce/php/module-reference/module-media-storage/): 100.4.7
- [magento/module-message-queue](https://developer.adobe.com/commerce/php/module-reference/module-message-queue/): 100.4.8
- [magento/module-msrp](https://developer.adobe.com/commerce/php/module-reference/module-msrp/): 100.4.7
- [magento/module-msrp-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-configurable-product/): 100.4.5
- [magento/module-msrp-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-grouped-product/): 100.4.5
- [magento/module-multishipping](https://developer.adobe.com/commerce/php/module-reference/module-multishipping/): 100.4.8
- [magento/module-mysql-mq](https://developer.adobe.com/commerce/php/module-reference/module-mysql-mq/): 100.4.6
- [magento/module-new-relic-reporting](https://developer.adobe.com/commerce/php/module-reference/module-new-relic-reporting/): 100.4.6
- [magento/module-newsletter](https://developer.adobe.com/commerce/php/module-reference/module-newsletter/): 100.4.8
- [magento/module-newsletter-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-newsletter-graph-ql/): 100.4.5
- [magento/module-offline-payments](https://developer.adobe.com/commerce/php/module-reference/module-offline-payments/): 100.4.6
- [magento/module-offline-shipping](https://developer.adobe.com/commerce/php/module-reference/module-offline-shipping/): 100.4.7
- [magento/module-open-search](https://developer.adobe.com/commerce/php/module-reference/module-open-search/): 100.4.2
- [magento/module-order-cancelation](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation/): 100.4.1
- [magento/module-order-cancelation-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-graph-ql/): 100.4.1
- [magento/module-order-cancelation-ui](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-ui/): 100.4.1
- [magento/module-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-page-cache/): 100.4.8
- [Magento/Modul-Zahlung](https://developer.adobe.com/commerce/php/module-reference/module-payment/): 100.4.8
- [magento/module-payment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-payment-graph-ql/): 100.4.3
- [magento/module-paypal](https://developer.adobe.com/commerce/php/module-reference/module-paypal/): 101.0.8
- [magento/module-paypal-captcha](https://developer.adobe.com/commerce/php/module-reference/module-paypal-captcha/): 100.4.5
- [magento/module-paypal-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-paypal-graph-ql/): 100.4.6
- [magento/module-persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/): 100.4.8
- [magento/module-product-alert](https://developer.adobe.com/commerce/php/module-reference/module-product-alert/): 100.4.7
- [magento/module-product-video](https://developer.adobe.com/commerce/php/module-reference/module-product-video/): 100.4.8
- [magento/module-quote](https://developer.adobe.com/commerce/php/module-reference/module-quote/): 101.2.8
- [magento/module-quote-analytics](https://developer.adobe.com/commerce/php/module-reference/module-quote-analytics/): 100.4.7
- [magento/module-quote-bundle-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-bundle-options/): 100.4.4
- [magento/module-quote-configurable-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-configurable-options/): 100.4.4
- [magento/module-quote-downloadable-links](https://developer.adobe.com/commerce/php/module-reference/module-quote-downloadable-links/): 100.4.4
- [magento/module-quote-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-graph-ql/): 100.4.8
- [magento/module-related-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-related-product-graph-ql/): 100.4.5
- [magento/module-release-notification](https://developer.adobe.com/commerce/php/module-reference/module-release-notification/): 100.4.6
- [magento/module-remote-storage](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage/): 100.4.6
- [magento/module-reports](https://developer.adobe.com/commerce/php/module-reference/module-reports/): 100.4.8
- [magento/module-Require-js](https://developer.adobe.com/commerce/php/module-reference/module-require-js/): 100.4.4
- [magento/module-review](https://developer.adobe.com/commerce/php/module-reference/module-review/): 100.4.8
- [magento/module-review-analytics](https://developer.adobe.com/commerce/php/module-reference/module-review-analytics/): 100.4.5
- [magento/module-review-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-review-graph-ql/): 100.4.4
- [magento/module-robots](https://developer.adobe.com/commerce/php/module-reference/module-robots/): 101.1.4
- [magento/module-rss](https://developer.adobe.com/commerce/php/module-reference/module-rss/): 100.4.6
- [magento/module-rule](https://developer.adobe.com/commerce/php/module-reference/module-rule/): 100.4.7
- [magento/module-sales](https://developer.adobe.com/commerce/php/module-reference/module-sales/): 103.0.8
- [magento/module-sales-analytics](https://developer.adobe.com/commerce/php/module-reference/module-sales-analytics/): 100.4.5
- [magento/module-sales-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-graph-ql/): 100.4.8
- [magento/module-sales-inventory](https://developer.adobe.com/commerce/php/module-reference/module-sales-inventory/): 100.4.5
- [magento/module-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule/): 101.2.8
- [magento/module-sales-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-graph-ql/): 100.4.1
- [magento/module-sales-sequence](https://developer.adobe.com/commerce/php/module-reference/module-sales-sequence/): 100.4.5
- [magento/module-sample-data](https://developer.adobe.com/commerce/php/module-reference/module-sample-data/): 100.4.6
- [magento/module-search](https://developer.adobe.com/commerce/php/module-reference/module-search/): 101.1.8
- [magento/module-security](https://developer.adobe.com/commerce/php/module-reference/module-security/): 100.4.8
- [magento/module-send-friend](https://developer.adobe.com/commerce/php/module-reference/module-send-friend/): 100.4.6
- [magento/module-send-friend-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-send-friend-graph-ql/): 100.4.4
- [Magento/Modul-Versand](https://developer.adobe.com/commerce/php/module-reference/module-shipping/): 100.4.8
- [magento/module-sitemap](https://developer.adobe.com/commerce/php/module-reference/module-sitemap/): 100.4.7
- [magento/module-store](https://developer.adobe.com/commerce/php/module-reference/module-store/): 101.1.8
- [magento/module-store-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-store-graph-ql/): 100.4.6
- [magento/module-swagger](https://developer.adobe.com/commerce/php/module-reference/module-swagger/): 100.4.7
- [magento/module-swagger-webapi](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi/): 100.4.4
- [magento/module-swagger-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi-async/): 100.4.4
- [magento/module-swatches](https://developer.adobe.com/commerce/php/module-reference/module-swatches/): 100.4.8
- [magento/module-swatches-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-swatches-graph-ql/): 100.4.6
- [magento/module-swatches-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-swatches-layered-navigation/): 100.4.4
- [magento/module-tax](https://developer.adobe.com/commerce/php/module-reference/module-tax/): 100.4.8
- [magento/module-tax-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-tax-graph-ql/): 100.4.4
- [magento/module-tax-import-export](https://developer.adobe.com/commerce/php/module-reference/module-tax-import-export/): 100.4.7
- [magento/module-theme](https://developer.adobe.com/commerce/php/module-reference/module-theme/): 101.1.8
- [magento/module-theme-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-theme-graph-ql/): 100.4.5
- [magento/module-translation](https://developer.adobe.com/commerce/php/module-reference/module-translation/): 100.4.8
- [magento/module-ui](https://developer.adobe.com/commerce/php/module-reference/module-ui/): 101.2.8
- [magento/module-ups](https://developer.adobe.com/commerce/php/module-reference/module-ups/): 100.4.8
- [magento/module-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite/): 102.0.7
- [magento/module-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite-graph-ql/): 100.4.7
- [magento/module-user](https://developer.adobe.com/commerce/php/module-reference/module-user/): 101.2.8
- [magento/module-usps](https://developer.adobe.com/commerce/php/module-reference/module-usps/): 100.4.7
- [magento/module-variable](https://developer.adobe.com/commerce/php/module-reference/module-variable/): 100.4.6
- [magento/module-vault](https://developer.adobe.com/commerce/php/module-reference/module-vault/): 101.2.8
- [magento/module-vault-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-vault-graph-ql/): 100.4.4
- [magento/module-version](https://developer.adobe.com/commerce/php/module-reference/module-version/): 100.4.5
- [magento/module-webapi](https://developer.adobe.com/commerce/php/module-reference/module-webapi/): 100.4.7
- [magento/module-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-webapi-async/): 100.4.6
- [magento/module-webapi-security](https://developer.adobe.com/commerce/php/module-reference/module-webapi-security/): 100.4.5
- [magento/module-weee](https://developer.adobe.com/commerce/php/module-reference/module-weee/): 100.4.8
- [magento/module-weee-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-weee-graph-ql/): 100.4.5
- [magento/module-widget](https://developer.adobe.com/commerce/php/module-reference/module-widget/): 101.2.8
- [magento/module-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-wishlist/): 101.2.8
- [magento/module-wishlist-analytics](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-analytics/): 100.4.6
- [magento/module-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-graph-ql/): 100.4.8
- Magento/Page-Builder: 1.7.5
- Magento/security-package: 1.1.7
- magento/theme-adminhtml-backend: 100.4.8
- magento/theme-frontend-blank: 100.4.8
- magento/theme-frontend-luma: 100.4.8
- Magento/Zend-Cache: ^1.16
- Magento/Zend-DB: ^1.16
- Magento/Zend-PDF: ^1.16
- monolog/monolog: ^3.6
- opensearch-project/opensearch-php: ^2.3
- Pelago/Demogrifier: ^7.0
- PHP: ~8.2.0||~8.3.0||~8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- PSR/Log: ^2 || ^3
- Ramsey/UUID: ^4.2
- symfony/console: ^6.4
- symfony/intl: ^6.4
- symfony/mailer: ^6.4
- symfony/mime: ^6.4
- symfony/process: ^6.4
- symfony/string: ^6.4
- TEDIVM/JShrink: ^1.4
- tubalmartin/cssmin: ^4.1
- Web-Token/JWT-Framework: ^3.4
- WebOnyx/GraphQL-PHP: ^15.0
- wikimedia/less.php: ^5.0

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
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
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
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Adobe Stock-API-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS Common Runtime für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS SDK für PHP - Verwenden von Amazon Web Services in Ihrem PHP-Projekt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">open-telemetry/api</a>
    </td>
    <td>Bibliothek</td>
    <td>API für OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">open-telemetry/context</a>
    </td>
    <td>Bibliothek</td>
    <td>Kontext-Implementierung für OpenTelemetry PHP.</td>
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
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
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
      <a href="https://github.com/Bacon/BaconQrCode">bacon/bacon-qr-code</a>
    </td>
    <td>Bibliothek</td>
    <td>BaconQrCode ist ein QR-Code-Generator für PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">Dasprid/Enum</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 7.1 Enum-Implementierung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">WebImpress/Safe-Writer</a>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Magento-module</td>
    <td>Das Backend der Stock-Zend_Cache_Backend_File-Datei hat eine extrem schlechte Leistung für die Reinigung von Tags, wodurch es unbrauchbar wird, wenn die Anzahl der zwischengespeicherten Elemente steigt. Dieses Backend nimmt viele Änderungen vor, die zu einer enormen Leistungssteigerung führen, insbesondere bei der Tag-Reinigung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein Redis-basierter Sitzungs-Handler mit optimistischer Sperrung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Implementierung des Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">Firebase/php-jwt</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Bibliothek zum Codieren und Decodieren von JSON Web Tokens (JWT) in PHP. Sollte der aktuellen Spezifikation entsprechen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>Bibliothek</td>
    <td>Generieren und Validieren von CAPTCHAs mit Fillets, Bildern, ReCAPTCHA und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>Bibliothek</td>
    <td>Erweiterungen der PHP Reflection API, statisches Codescannen und Codegenerierung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt eine auf verschachtelten Objekteigenschaften basierende Benutzeroberfläche für den Zugriff auf diese Konfigurationsdaten im Anwendungscode bereit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>Bibliothek</td>
    <td>Automatisierte Injektion von Abhängigkeiten für PSR-11-Container</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">Laminas/Laminas-Escaper</a>
    </td>
    <td>Bibliothek</td>
    <td>Sicheres und sicheres Maskieren von HTML, HTML-Attributen, JavaScript, CSS und URLs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventManager</a>
    </td>
    <td>Bibliothek</td>
    <td>Trigger und Überwachen von Ereignissen in einer PHP-Anwendung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">laminas/laminas-feed</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet Funktionen zum Erstellen und Verwenden von RSS- und Atom-Feeds</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">LAMINAS/LAMINAS-FILTER</a>
    </td>
    <td>Bibliothek</td>
    <td>Programmgesteuertes Filtern und Normalisieren von Daten und Dateien</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine einfache Schnittstelle zum Ausführen von HTTP-Anfragen (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">LAMINAS/LAMINAS-I18N</a>
    </td>
    <td>Bibliothek</td>
    <td>Übersetzungen für Ihre Anwendung bereitstellen und internationalisierte Werte filtern und validieren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>Bibliothek</td>
    <td>bietet praktische Methoden zum Serialisieren von nativem PHP zu JSON und zum Dekodieren von JSON zu nativem PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">LAMINAS/LAMINAS-LOADER</a>
    </td>
    <td>Bibliothek</td>
    <td>Strategien zum automatischen Laden und Laden von Plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>Bibliothek</td>
    <td>Modulares Applikationssystem für Laminas-MVC-Anwendungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">LAMINAS/LAMINAS-MVC</a>
    </td>
    <td>Bibliothek</td>
    <td>Die ereignisgesteuerte MVC-Schicht von Laminas, einschließlich MVC-Anwendungen, Controller und Plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine einfache und flexible Implementierung der Zugriffssteuerungsliste (ACL) für die Verwaltung von Berechtigungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-reCAPTCHA</a>
    </td>
    <td>Bibliothek</td>
    <td>OOP-Wrapper für den ReCaptcha-Webservice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexibles Routing-System für HTTP- und Konsolenanwendungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">LAMINAS/LAMINAS-SERVER</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen von Reflection-basierten RPC-Servern</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-serviceManager</a>
    </td>
    <td>Bibliothek</td>
    <td>werkseitiger Injektor für die Injektion von Abhängigkeiten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>Bibliothek</td>
    <td>Objektorientierte Schnittstelle zu PHP-Sitzungen und -Speicher</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminas/laminas-soap</a>
    </td>
    <td>Bibliothek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>Bibliothek</td>
    <td>SPL-Erweiterungen, Array-Dienstprogramme, Fehler-Handler und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>Bibliothek</td>
    <td>Erstellen von Feigenblättern und textbasierten Tabellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>Bibliothek</td>
    <td>Schnittstellen für die Übersetzerkomponente von laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Komponente, die bei der Bearbeitung und Validierung von „URIs“ (Uniform Resource Identifiers) hilft</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>Bibliothek</td>
    <td>Validierungsklassen für eine Vielzahl von Domains und die Möglichkeit, Validatoren zu verketten, um komplexe Validierungskriterien zu erstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>Bibliothek</td>
    <td>Flexible Ansichtsebene unterstützt und bietet mehrere Ansichtsebenen, Helper und mehr</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>Bibliothek</td>
    <td>Einfache und schnelle Implementierung von Auflistungen mit nativem PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein in PHP geschriebener PHP-Parser</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/reCAPTCHA</a>
    </td>
    <td>Bibliothek</td>
    <td>Client-Bibliothek für reCAPTCHA von Google für PHP 8.4 und höher</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jsShrink</a>
    </td>
    <td>Bibliothek</td>
    <td>In PHP eingebauter JavaScript-Minimierer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Magento-module</td>
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
      <a href="https://github.com/paragonie/sodium_compat">Paragonie/Natrium_compat</a>
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
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlPurifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardkonformer HTML-Filter in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
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
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>Bibliothek</td>
    <td>Braintree PHP-Client-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">Stein/Mathematik</a>
    </td>
    <td>Bibliothek</td>
    <td>Arithmetische Bibliothek mit beliebiger Genauigkeit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">brick/varexporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine leistungsstarke Alternative zu var_export(), die Schließungen und Objekte ohne __set_state() exportieren kann</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">Christian-Riesen/base32</a>
    </td>
    <td>Bibliothek</td>
    <td>Base32 Encoder/Decoder nach RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinmollenhour/credis</a>
    </td>
    <td>Bibliothek</td>
    <td>Credis ist eine einfache Schnittstelle zum Redis-Schlüssel-Wert-Store, der die phpredis-Bibliothek umschließt, wenn sie für eine bessere Leistung verfügbar ist.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">composer/ca-bundle</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Suche nach einem Pfad zum System-CA-Bundle und beinhaltet ein Fallback zum Mozilla CA-Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">composer/class-map-generator</a>
    </td>
    <td>Bibliothek</td>
    <td>Dienstprogramme zum Scannen von PHP-Code und Generieren von Klassenzuordnungen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">Komponist/Komponist</a>
    </td>
    <td>Bibliothek</td>
    <td>Composer unterstützt Sie beim Deklarieren, Verwalten und Installieren von Abhängigkeiten von PHP-Projekten. Dadurch wird sichergestellt, dass Sie überall den richtigen Stack haben.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">composer/metadata-minifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Kleine Dienstprogrammbibliothek, die für die Minimierung und Erweiterung von Metadaten zuständig ist.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">Composer/PCRE</a>
    </td>
    <td>Bibliothek</td>
    <td>PCRE Wrapping-Bibliothek, die typsichere Preg_*-Ersetzungen bietet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">Komponist/Semver</a>
    </td>
    <td>Bibliothek</td>
    <td>Server-Bibliothek, die Dienstprogramme, das Analysieren von Versionsbeschränkungen und die Validierung bietet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">composer/spdx-licenses</a>
    </td>
    <td>Bibliothek</td>
    <td>SPDX-Lizenzliste und Validierungsbibliothek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">composer/xdebug-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Startet einen Prozess ohne Xdebug neu.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">Doktrin/Lexer</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Doctrine Lexer Parser-Bibliothek, die in rekursiven Top-Down-Parsern verwendet werden kann.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Bibliothek zum Validieren von E-Mails mit mehreren RFCs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">Elastisch/Transport</a>
    </td>
    <td>Bibliothek</td>
    <td>HTTP-Transport-PHP-Bibliothek für Elastic-Produkte</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP-Client für Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>Bibliothek</td>
    <td>Endroid-QR-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>Bibliothek</td>
    <td>Abspaltung von Guzzle/Streams (aufgegeben) zur Verwendung mit Elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Abspaltung von guzzle/RingPHP (aufgegeben) zur Verwendung mit elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>Bibliothek</td>
    <td>Guzzle ist eine PHP HTTP Client-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promises</a>
    </td>
    <td>Bibliothek</td>
    <td>Guzzle-Versprechensbibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>Bibliothek</td>
    <td>PSR-7-Nachrichtenimplementierung, die auch gängige Dienstprogrammmethoden bereitstellt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">JustInRainbow/JSON-Schema</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine Bibliothek zum Überprüfen eines JSON-Schemas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">League/Flysystem</a>
    </td>
    <td>Bibliothek</td>
    <td>Dateispeicherabstraktion für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">League/Flysystem-AWS-S3-V3</a>
    </td>
    <td>Bibliothek</td>
    <td>AWS S3-Dateisystemadapter für Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">League/Flysystem-local</a>
    </td>
    <td>Bibliothek</td>
    <td>Lokaler Dateisystemadapter für Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">League/MIME-Typ-Erkennung</a>
    </td>
    <td>Bibliothek</td>
    <td>MIME-Erkennung für Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monolog/monolog</a>
    </td>
    <td>Bibliothek</td>
    <td>Sendet Ihre Protokolle an Dateien, Sockets, Posteingänge, Datenbanken und verschiedene Web-Services</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>Bibliothek</td>
    <td>Deklarativ angeben, wie Elemente aus einem JSON-Dokument extrahiert werden sollen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>Bibliothek</td>
    <td>Implementierungen der RFC-4648-Codierung in konstanten Zeiten (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x Polyfill für random_bytes() und random_int() von PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emogrifier</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Stile in HTML-Code in Inline-Stilattribute</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-Plug-in</td>
    <td>Findet und installiert PSR-7-, PSR-17-, PSR-18- und HTTPlug-Implementierungen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>Bibliothek</td>
    <td>HTTPlug, die HTTP-Client-Abstraktion für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">PHP-HTTP/Promise</a>
    </td>
    <td>Bibliothek</td>
    <td>Promise für asynchrone HTTP-Anfragen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertieren von CSS-Selektoren in XPath-Abfragen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>Bibliothek</td>
    <td>Moderne DOM-API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>Bibliothek</td>
    <td>Eigenschaftenaccessor- und -mutatorfunktionen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP 5.x-8.x Polyfill für mcrypt Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>Bibliothek</td>
    <td>PHP Secure Communications Library - Pure-PHP-Implementierungen von RSA, AES, SSH2, SFTP, X.509 etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">PSR/Cache</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Schnittstelle zum Zwischenspeichern von Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">PSR/CLOCK</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle zum Lesen der Uhr.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">PSR/Container</a>
    </td>
    <td>Bibliothek</td>
    <td>Common Container Interface (PHP-Abb. PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">PSR/event-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Standardschnittstellen für die Ereignisbehandlung.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">PSR/HTTP-Client</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle für HTTP-Clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">PSR/HTTP-Factory</a>
    </td>
    <td>Bibliothek</td>
    <td>PSR-17: Gemeinsame Schnittstellen für PSR-7-HTTP-Nachrichten-Factories</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">PSR/HTTP-Nachricht</a>
    </td>
    <td>Bibliothek</td>
    <td>Gemeinsame Schnittstelle für HTTP-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">PSR/LOG</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Benutzeroberfläche für die Protokollierung von Bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getAllHeaders</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein Polyfill für getAllHeaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">Ramsey/Collection</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zur Darstellung und Bearbeitung von Sammlungen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">Ramsey/UUID</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zum Generieren und Verwenden von Universally Unique Identifiers (UUIDs).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">React/Promise</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine einfache Implementierung von CommonJS Promises/A für PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>Bibliothek</td>
    <td>Parser für in PHP geschriebene CSS-Dateien</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>Bibliothek</td>
    <td>JSON-Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>Bibliothek</td>
    <td>PHAR-Dateiformat-Dienstprogramme, für den Fall, dass PHP Sie startet</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">SELD/Signal-Handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Einfacher Unix-Signal-Handler, der im Hintergrund ausfällt, wenn Signale nicht unterstützt werden, um eine einfache plattformübergreifende Entwicklung zu ermöglichen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Bibliothek</td>
    <td>AES Key Wrap für PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine PHP-Bibliothek zur Erzeugung von Einmalkennwörtern nach RFC 4226 (HOTP-Algorithmus) und RFC 6238 (TOTP-Algorithmus), die mit dem Google Authenticator kompatibel sind</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>Bibliothek</td>
    <td>Ein PHP-Framework für die Verwaltung von Public-Key-Infrastrukturen. Sie umfasst X.509-Zertifikate mit öffentlichem Schlüssel, Attributzertifikate, Zertifizierungsanfragen und die Validierung des Zertifizierungspfads.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilft Ihnen beim Suchen, Laden, Kombinieren, automatischen Ausfüllen und Überprüfen von Konfigurationswerten jeglicher Art</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">symfony/console</a>
    </td>
    <td>Bibliothek</td>
    <td>Erleichtert die Erstellung von schönen und testbaren Befehlszeilenschnittstellen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>Bibliothek</td>
    <td>Konvertiert CSS-Selektoren in XPath-Ausdrücke</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symfony/dependency-jection</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Standardisierung und Zentralisierung der Objekterstellung in der Anwendung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">Symfony/Deprecation-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Eine generische Funktion und Konvention für Hinweise zum Verwerfen von Triggern</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet Tools zur Fehlerverwaltung und einfacheren Fehlerbehebung in PHP-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt Tools bereit, mit denen Ihre Anwendungskomponenten miteinander kommunizieren können, indem Ereignisse gesendet und überwacht werden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen im Zusammenhang mit dem Dispatching-Ereignis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt grundlegende Dienstprogramme für das Dateisystem bereit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>Bibliothek</td>
    <td>Findet Dateien und Verzeichnisse über eine intuitive, flüssige Oberfläche</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet leistungsstarke Methoden zum synchronen oder asynchronen Abrufen von HTTP-Ressourcen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen in Bezug auf HTTP-Clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>Bibliothek</td>
    <td>Definiert eine objektorientierte Ebene für die HTTP-Spezifikation</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt einen strukturierten Prozess zum Konvertieren einer Anfrage in eine Antwort bereit</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht den Zugriff auf die Lokalisierungsdaten der ICU-Bibliothek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>Bibliothek</td>
    <td>Hilft beim Senden von E-Mails</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht die Bearbeitung von MIME-Nachrichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für ctype-Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für intl's grapheme_* Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für die Funktionen „idn_to_ascii“ und „idn_to_utf8“ von Intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für Intl's Normalizer-Klasse und zugehörige Funktionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill für die MBstring-Erweiterung</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 7.3+ Funktionen zur Reduzierung von PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 8.0+ Funktionen zur Reduzierung von PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 8.1+ Funktionen zur Reduzierung von PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 8.2+-Funktionen zur Reduzierung von PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>Bibliothek</td>
    <td>Symfony Polyfill unterstützt einige PHP 8.3+ Funktionen zu niedrigeren PHP-Versionen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/process</a>
    </td>
    <td>Bibliothek</td>
    <td>Führt Befehle in Teilprozessen aus</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">symfony/service-Contracts</a>
    </td>
    <td>Bibliothek</td>
    <td>Allgemeine Abstraktionen im Zusammenhang mit Schreibdiensten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/string</a>
    </td>
    <td>Bibliothek</td>
    <td>Bietet eine objektorientierte API für Zeichenfolgen und verarbeitet Bytes, UTF-8-Code-Punkte und Graphem-Cluster einheitlich</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>Bibliothek</td>
    <td>Stellt Mechanismen bereit, um beliebige PHP-Variablen zu durchlaufen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-Exporter</a>
    </td>
    <td>Bibliothek</td>
    <td>Ermöglicht den Export jeder serialisierbaren PHP-Datenstruktur in reinen PHP-Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>Bibliothek</td>
    <td>Lädt YAML-Dateien und gibt deren Speicherinhalt aus</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">Web-Token/JWT-Framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>JSON Object Signing and Encryption Library für PHP und Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
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
    <td>Magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>Magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2-module</td>
    <td>Nicht zutreffend</td>
  </tr>
  <tr>
    <td>
      PayPal/Modul-Braintree-Belohnung
    </td>
    <td>Magento2-module</td>
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
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
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
      <th>Typ</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>Magento2-module</td>
    <td>Verzweigung aus dem Magento Braintree 2.2.0 Modul von Gene Commerce für PayPal.</td>
  </tr>
  </tbody>
</table>
