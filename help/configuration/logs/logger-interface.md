---
title: Logger-Benutzeroberfläche
description: Erste Schritte mit der Logger-Oberfläche.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Logger-Benutzeroberfläche

Um mit einer Protokollfunktion zu arbeiten, müssen Sie eine Instanz von `\Psr\Log\LoggerInterface`. Mit dieser Schnittstelle können Sie die folgenden Funktionen aufrufen, um Daten in Protokolldateien zu schreiben:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Eine Möglichkeit dazu wird im Abschnitt [Aktivität &quot;Logdatenbank&quot;](../logs/database-activity.md) Beispiel.

Eine andere Möglichkeit:

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

Das obige Beispiel zeigt Folgendes: `SomeModel` empfängt eine `\Psr\Log\LoggerInterface` -Objekt mit Konstruktor-Injektion. In einer Methode `doSomething`, wenn ein Fehler aufgetreten ist, wird er bei einer Methode protokolliert `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definiert acht Protokollebenen (Debugging, Info, Hinweis, Warnung, Fehler, kritisch, Warnhinweis und Notfall).
