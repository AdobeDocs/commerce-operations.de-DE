---
title: Schreiben in eine benutzerdefinierte Protokolldatei
description: Erfahren Sie, wie Sie benutzerdefinierte Protokolldateien einrichten.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# Schreiben in eine benutzerdefinierte Protokolldatei

Die `Magento\Framework\Logger` -Modul enthält die folgenden Handler-Klassen:

| Klasse | Protokolldatei |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Sie können sie im `lib/internal/Magento/Framework/Logger/Handler` Verzeichnis.

Sie können einen der folgenden Ansätze zum Anmelden bei einer benutzerdefinierten Datei verwenden:

- Richten Sie eine benutzerdefinierte Protokolldatei im `di.xml`
- Einrichten einer benutzerdefinierten Datei in der benutzerdefinierten Logger-Handler-Klasse

## Richten Sie eine benutzerdefinierte Protokolldatei im `di.xml`

In diesem Beispiel wird gezeigt, wie [virtuelle Typen](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) zum Protokoll `debug` Nachrichten in eine benutzerdefinierte Protokolldatei anstelle einer standardmäßigen `/var/log/debug.log`.

1. Im `di.xml` -Datei Ihres Moduls eine benutzerdefinierte Protokolldatei als [virtueller Typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   Die `name` Wert von `Magento\Payment\Model\Method\MyCustomDebug` muss eindeutig sein.

1. Definieren des Handlers in einem anderen [virtueller Typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) mit einer eindeutigen `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Spritzen Sie die `MyCustomLogger` [virtueller Typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) im `Magento\Payment\Model\Method\Logger` -Objekt:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Die virtuelle Klasse `Magento\Payment\Model\Method\MyCustomDebug` wird in die `debug` Handler der `$logger` -Eigenschaft in `Magento\Payment\Model\Method\Logger` -Klasse.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Ausnahmemeldungen werden bei der `/var/log/payment.log` -Datei.

## Einrichten einer benutzerdefinierten Protokolldatei in der Logger-Handler-Klasse

In diesem Beispiel wird gezeigt, wie eine benutzerdefinierte Logger-Handler-Klasse zur Protokollierung verwendet wird `error` Nachrichten in eine bestimmte Protokolldatei.

1. Erstellen Sie eine Klasse, die Daten protokolliert. In diesem Beispiel wird die Klasse definiert in `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. Definieren Sie den Handler für diese Klasse als [virtueller Typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) im Modul `di.xml` -Datei.

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

1. Im `type` -Definition geben Sie den Klassennamen an, in den der benutzerdefinierte Logger-Handler eingefügt wird. Verwenden Sie den Namen des virtuellen Typs aus dem vorherigen Schritt als Argument für diesen Typ.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Quellcode von `Vendor\ModuleName\Observer\MyObserver` -Klasse:

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

1. Die Klasse `Vendor\ModuleName\Logger\Handler\ErrorHandler` wird in die `error` Handler der `$logger` -Eigenschaft in `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Ausnahmemeldungen werden im `/var/log/my_custom_logger/error.log` -Datei.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
