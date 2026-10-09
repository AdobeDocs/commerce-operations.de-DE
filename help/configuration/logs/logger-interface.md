---
title: Logger-Oberfläche
description: Erfahren Sie, wie Sie die Protokollierungsschnittstelle in Adobe Commerce für die benutzerdefinierte Protokollierung verwenden. Lernen Sie die PSR-3-Implementierung und -Protokollfunktionen kennen.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Logger-Oberfläche

Um mit einer Protokollierung zu arbeiten, müssen Sie eine Instanz von `\Psr\Log\LoggerInterface` erstellen. Mit dieser Schnittstelle können Sie die folgenden Funktionen aufrufen, um Daten in Protokolldateien zu schreiben:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [Kritisch()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Notfall()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [Hinweis()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [Warnung(en)](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Eine Möglichkeit, dies zu tun, wird im Beispiel [Datenbankaktivität protokollieren](../logs/database-activity.md) erläutert.

Es folgt ein anderer Weg:

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

Das vorherige Beispiel zeigt, dass `SomeModel` ein `\Psr\Log\LoggerInterface`-Objekt mithilfe der Konstruktorinjektion empfängt. Wenn in einer Methode `doSomething` ein Fehler aufgetreten ist, wird er in einer `critical` protokolliert (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definiert acht Protokollebenen (Debug, Info, Hinweis, Warnung, Fehler, Kritisch, Warnhinweis und Notfall).
