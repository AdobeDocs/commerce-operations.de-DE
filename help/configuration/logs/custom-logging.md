---
title: Benutzerdefinierte Protokollierung
description: Erfahren Sie, wie Sie mithilfe der benutzerdefinierten Protokollierung Fehler untersuchen können.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Übersicht über die benutzerdefinierte Protokollierung

Protokolle bieten Einblicke in Systemprozesse, z. B. Debugging-Informationen, die Ihnen dabei helfen zu verstehen, wann ein Fehler aufgetreten ist oder was zu dem Fehler geführt hat.

Dieses Thema konzentriert sich auf die dateibasierte Protokollierung. Commerce bietet jedoch auch die Flexibilität, Protokolle in der Datenbank zu speichern.

Adobe empfiehlt aus folgenden Gründen die Verwendung der zentralisierten Anwendungsprotokollierung:

- Dies ermöglicht die Speicherung von Protokollen auf einem anderen Server als dem Anwendungsserver und verringert die I/O-Vorgänge der Festplatte, wodurch die Unterstützung des Anwendungsservers vereinfacht wird.

- Dadurch wird die Verarbeitung von Protokolldaten effizienter, indem spezielle Tools wie [Logstash], [Logplex] oder [fluentd] verwendet werden, ohne dass dies Auswirkungen auf einen Produktionsserver hat.

  >[!INFO]
  >
  >Adobe empfiehlt oder unterstützt keine bestimmte Protokollierungslösung.

## PSR-3-Konformität

Der [PSR-3-Standard][laminas] definiert eine allgemeine PHP-Schnittstelle für die Protokollierung von Bibliotheken. Das Hauptziel von PSR-3 besteht darin, Bibliotheken zu ermöglichen, ein `Psr\Log\LoggerInterface` -Objekt zu empfangen und Protokolle auf einfache und universelle Weise darauf zu schreiben.

Dadurch kann die Implementierung problemlos ersetzt werden, ohne dass befürchtet wird, dass eine solche Ersetzung den Anwendungs-Code beschädigen könnte. Es garantiert auch, dass eine benutzerdefinierte Komponente auch dann funktioniert, wenn die Log-Implementierung in einer zukünftigen Version des Systems geändert wird.

## Monolog

Commerce 2 entspricht dem PSR-3-Standard. Standardmäßig verwendet Commerce [Monolog]. Monolog wurde als Voreinstellung für `Psr\Log\LoggerInterface` in der Commerce-Anwendung [`di.xml`][di] implementiert.

Monolog ist eine beliebte PHP-Protokollierungslösung mit einer Vielzahl von Handlern, die es Ihnen ermöglichen, erweiterte Protokollierungsstrategien zu entwickeln. Im Folgenden finden Sie eine Zusammenfassung der Funktionsweise von Monolog.

Ein Monolog _logger_ ist ein Kanal, der über einen eigenen Satz von _Handlern_ verfügt. Monolog verfügt über viele Handler, darunter:

- Log to files and syslog
- Warnhinweise und E-Mails senden
- Protokollspezifische Server und Netzwerkprotokollierung
- Protokollierung in der Entwicklung (Integration unter anderem mit FireBug und Chrome Logger)
- Bei der Datenbank anmelden

Jeder Handler kann die Eingabemeldung verarbeiten und die Weiterleitung stoppen oder das Steuerelement an den nächsten Handler in einer Kette übergeben.

Protokollmeldungen können auf viele verschiedene Arten verarbeitet werden. Sie können beispielsweise alle Debugging-Informationen in einer Datei auf der Festplatte speichern, die Nachrichten mit höheren Protokollebenen in eine Datenbank einfügen und schließlich Nachrichten mit der Protokollebene &quot;kritisch&quot;per E-Mail senden.

Andere Kanäle können einen anderen Satz von Handlern und Logik aufweisen.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fließend]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monolog]: https://github.com/Seldaek/monolog
