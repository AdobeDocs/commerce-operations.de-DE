---
title: Schreiben in eine benutzerdefinierte Protokolldatei
description: Erfahren Sie, wie Sie benutzerdefinierte Protokolldateien einrichten.
feature: Configuration, Logs
badge: label="Beitragt von Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Schreiben in eine benutzerdefinierte Protokolldatei

Das Modul `Magento\Framework\Logger` enthält die folgenden Handler-Klassen:

| Klasse | Protokolldatei |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Sie können sie im Verzeichnis `lib/internal/Magento/Framework/Logger/Handler` finden.

Sie können einen der folgenden Ansätze zum Anmelden bei einer benutzerdefinierten Datei verwenden:

- Einrichten einer benutzerdefinierten Protokolldatei im `di.xml`
- Einrichten einer benutzerdefinierten Datei in der benutzerdefinierten Logger-Handler-Klasse

## Einrichten einer benutzerdefinierten Protokolldatei im `di.xml`

In diesem Beispiel wird gezeigt, wie [virtuelle Typen](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) verwendet werden, um `debug` -Meldungen in einer benutzerdefinierten Protokolldatei anstatt in einer standardmäßigen `/var/log/debug.log` zu protokollieren.

1. Definieren Sie in der Datei `di.xml` Ihres Moduls eine benutzerdefinierte Protokolldatei als [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   Der `name` -Wert von `Magento\Payment\Model\Method\MyCustomDebug` muss eindeutig sein.

1. Definieren Sie den Handler in einem anderen [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) mit einer eindeutigen `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Spritzen Sie den `MyCustomLogger` [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in das Objekt `Magento\Payment\Model\Method\Logger` :

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Die virtuelle Klasse `Magento\Payment\Model\Method\MyCustomDebug` wird in den `debug` -Handler der Eigenschaft `$logger` in der Klasse `Magento\Payment\Model\Method\Logger` eingefügt.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Ausnahmemeldungen werden in der Datei `/var/log/payment.log` protokolliert.

## Einrichten einer benutzerdefinierten Protokolldatei in der Logger-Handler-Klasse

In diesem Beispiel wird gezeigt, wie mit einer benutzerdefinierten Logger-Handler-Klasse `error` -Meldungen in einer bestimmten Protokolldatei protokolliert werden.

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

1. Definieren Sie den Handler für diese Klasse als [virtuellen Typ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in der `di.xml` -Datei des Moduls.

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

1. Geben Sie in der Definition `type` den Klassennamen an, in den der benutzerdefinierte Logger-Handler eingefügt wird. Verwenden Sie den Namen des virtuellen Typs aus dem vorherigen Schritt als Argument für diesen Typ.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Source-Code der `Vendor\ModuleName\Observer\MyObserver` -Klasse:

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

1. Die Klasse `Vendor\ModuleName\Logger\Handler\ErrorHandler` wird in den `error` -Handler der Eigenschaft `$logger` im `Vendor\ModuleName\Observer\MyObserver` eingefügt.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Ausnahmemeldungen werden in der Datei `/var/log/my_custom_logger/error.log` protokolliert.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
