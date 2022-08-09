---
title: Benutzerdefinierte Protokollierung
description: Erfahren Sie, wie Sie mithilfe der benutzerdefinierten Protokollierung Fehler untersuchen können.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Übersicht über die benutzerdefinierte Protokollierung

Protokolle bieten Einblick in die Systemprozesse. z. B. Debugging von Informationen, die Sie dabei unterstützen, zu verstehen, wann ein Fehler aufgetreten ist oder was zu dem Fehler geführt hat.

Dieses Thema konzentriert sich auf die dateibasierte Protokollierung, obwohl Commerce die Flexibilität bietet, Protokolle auch in der Datenbank zu speichern.

Adobe empfiehlt aus folgenden Gründen die Verwendung der zentralisierten Anwendungsprotokollierung:

- Dies ermöglicht die Speicherung von Protokollen auf einem anderen Server als dem Anwendungsserver und verringert die I/O-Vorgänge der Festplatte, wodurch die Unterstützung des Anwendungsservers vereinfacht wird.

- Die Verarbeitung von Protokolldaten wird durch die Verwendung spezieller Tools effizienter, z. B. [Logstash], [Logplex]oder [fließend]—ohne Auswirkungen auf einen Produktionsserver.

   >[!INFO]
   >
   >Adobe empfiehlt keine bestimmte Protokollierungslösung oder befürwortet sie.

## PSR-3-Konformität

Die [PSR-3-Standard][laminas] definiert eine gängige PHP-Schnittstelle für die Protokollierung von Bibliotheken. Das Hauptziel von PSR-3 besteht darin, Bibliotheken das Empfangen von `Psr\Log\LoggerInterface` -Objekt zu erstellen und Protokolle darauf auf einfache und universelle Weise zu schreiben.

Dadurch kann die Implementierung problemlos ersetzt werden, ohne dass befürchtet wird, dass eine solche Ersetzung den Anwendungs-Code beschädigen könnte. Es garantiert auch, dass eine benutzerdefinierte Komponente auch dann funktioniert, wenn die Log-Implementierung in einer zukünftigen Version des Systems geändert wird.

## Monolog

Commerce 2 entspricht dem PSR-3-Standard. Standardmäßig verwendet Commerce [Monolog]. Monolog wurde als Präferenz für `Psr\Log\LoggerInterface` in der Commerce-Anwendung [`di.xml`][di].

Monolog ist eine beliebte PHP-Protokollierungslösung mit einer Vielzahl von Handlern, die es Ihnen ermöglichen, erweiterte Protokollierungsstrategien zu entwickeln. Im Folgenden finden Sie eine Zusammenfassung der Funktionsweise von Monolog.

A Monolog _Logger_ ist ein Kanal mit einem eigenen Satz von _Handler_. Monolog verfügt über viele Handler, darunter:

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
