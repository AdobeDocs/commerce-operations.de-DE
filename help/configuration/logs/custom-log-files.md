---
title: Schreiben in benutzerdefinierte Protokolldatei
description: Erfahren Sie, wie Sie benutzerdefinierte Protokolldateien in Adobe Commerce erstellen und konfigurieren. Entdecken Sie Logger-Handler und benutzerdefinierte Protokollierungsimplementierung.
feature: Configuration, Logs
badge: label="Von Atwix beigetragen" type="Informative" url="https://www.atwix.com/" tooltip="ATWIX"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Schreiben in eine benutzerdefinierte Protokolldatei

Das `Magento\Framework\Logger`-Modul enthält die folgenden Handler-Klassen:

| Klasse | Protokolldatei |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Sie finden sie möglicherweise im `lib/internal/Magento/Framework/Logger/Handler`.

Sie können einen der folgenden Ansätze für die Anmeldung bei einer benutzerdefinierten Datei verwenden:

- Einrichten einer benutzerdefinierten Protokolldatei im `di.xml`
- Einrichten einer benutzerdefinierten Datei in der benutzerdefinierten Logger-Handler-Klasse

## Einrichten einer benutzerdefinierten Protokolldatei im `di.xml`

In diesem Beispiel wird gezeigt, wie [virtuelle Typen](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) verwendet werden, um `debug` Meldungen in einer benutzerdefinierten Protokolldatei anstelle eines `/var/log/debug.log` zu protokollieren.

1. Definieren Sie in der `di.xml` Ihres Moduls eine benutzerdefinierte Protokolldatei als [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   Der `name` Wert von `Magento\Payment\Model\Method\MyCustomDebug` muss eindeutig sein.

1. Definieren Sie den Handler in einem anderen [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) mit einem eindeutigen `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Fügen Sie den `MyCustomLogger` [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in das `Magento\Payment\Model\Method\Logger` ein:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Die virtuelle Klasse `Magento\Payment\Model\Method\MyCustomDebug` wird in den `debug`-Handler der `$logger`-Eigenschaft in der `Magento\Payment\Model\Method\Logger`-Klasse eingefügt.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Ausnahmemeldungen werden in der `/var/log/payment.log`-Datei protokolliert.

## Einrichten einer benutzerdefinierten Protokolldatei in der Logger-Handler-Klasse

In diesem Beispiel wird gezeigt, wie mit einer benutzerdefinierten Logger-Handler-Klasse `error` Meldungen in einer bestimmten Protokolldatei protokolliert werden.

1. Erstellen Sie eine Klasse, die Daten protokolliert. In diesem Beispiel wird die Klasse in `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php` definiert.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Definieren Sie den Handler für diese Klasse als [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in der `di.xml` des Moduls.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` ist eine eindeutige Kennung.

1. Geben Sie in der `type` den Klassennamen an, in den der benutzerdefinierte Logger-Handler eingefügt werden soll. Verwenden Sie den Namen des virtuellen Typs aus dem vorherigen Schritt als Argument für diesen Typ.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Source-Code `Vendor\ModuleName\Observer\MyObserver` Klasse:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. Die Klasse `Vendor\ModuleName\Logger\Handler\ErrorHandler` wird in den `error`-Handler der `$logger`-Eigenschaft in der `Vendor\ModuleName\Observer\MyObserver` eingefügt.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Ausnahmemeldungen werden in der `/var/log/my_custom_logger/error.log`-Datei protokolliert.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
