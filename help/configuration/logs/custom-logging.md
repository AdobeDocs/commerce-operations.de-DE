---
title: Benutzerdefinierte Protokollierung
description: Erfahren Sie, wie Sie Fehler mithilfe der benutzerdefinierten Protokollierung untersuchen können.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Übersicht über die benutzerdefinierte Protokollierung

Protokolle bieten Einblick in Systemprozesse, z. B. Debugging-Informationen, die Ihnen dabei helfen zu verstehen, wann ein Fehler aufgetreten ist oder was zu dem Fehler geführt hat.

Der Schwerpunkt dieses Artikels liegt auf der dateibasierten Protokollierung. Commerce bietet jedoch auch die Flexibilität, Protokolle in der Datenbank zu speichern.

Adobe empfiehlt aus den folgenden Gründen die Verwendung einer zentralen Anwendungsprotokollierung:

- Es ermöglicht die Speicherung von Protokollen auf einem anderen Server als dem Anwendungsserver und verringert Datenträger-E/A-Vorgänge, wodurch die Unterstützung des Anwendungsservers vereinfacht wird.

- Die Verarbeitung von Protokolldaten wird durch spezielle Tools wie [Logstash], [Logplex] oder [fluentd] effektiver, ohne dass sich dies auf den Produktionsserver auswirkt.

  >[!INFO]
  >
  >Adobe empfiehlt oder unterstützt keine bestimmte Protokollierungslösung.

## PSR-3-Konformität

Der [PSR-3-Standard][laminas] definiert eine gemeinsame PHP-Schnittstelle für die Protokollierung von Bibliotheken. Das Hauptziel von PSR-3 besteht darin, Bibliotheken zu ermöglichen, ein `Psr\Log\LoggerInterface` Objekt zu empfangen und Protokolle auf einfache und universelle Weise darauf zu schreiben.

Dadurch kann die Implementierung einfach ersetzt werden, ohne dass befürchtet werden muss, dass durch einen solchen Austausch der Anwendungs-Code beschädigt wird. Sie garantiert außerdem, dass eine benutzerdefinierte Komponente auch dann funktioniert, wenn die Protokollimplementierung in einer zukünftigen Version des Systems geändert wird.

## Monolog

Commerce 2 erfüllt den PSR-3-Standard. Standardmäßig verwendet Commerce [Monolog]. Monolog wird als Voreinstellung für `Psr\Log\LoggerInterface` im Commerce-Programm-[`di.xml`][di] implementiert.

Monolog ist eine beliebte PHP-Protokollierungslösung mit einer Vielzahl von Handlern, die es Ihnen ermöglichen, erweiterte Protokollierungsstrategien zu erstellen. Im Folgenden finden Sie eine Zusammenfassung der Funktionsweise von Monolog.

Ein Monolog _Logger_ ist ein Kanal mit einem eigenen Satz von _Handlern_. Monolog verfügt über viele Handler, darunter:

- In Dateien und syslog protokollieren
- Senden von Warnhinweisen und E-Mails
- Protokollspezifische Server und Netzwerkprotokollierung
- Logging in der Entwicklungsumgebung (unter anderem Integration mit FireBug und Chrome Logger)
- Bei Datenbank anmelden

Jeder Handler kann entweder die Eingabemeldung verarbeiten und die Weiterleitung stoppen oder das Steuerelement an den nächsten Handler in einer Kette übergeben.

Protokollmeldungen können auf viele verschiedene Arten verarbeitet werden. Sie können beispielsweise alle Debugging-Informationen in einer Datei auf der Festplatte speichern, die Meldungen mit höheren Protokollebenen in eine Datenbank einfügen und schließlich Meldungen mit der Protokollebene „Kritisch“ per E-Mail senden.

Andere Kanäle können einen anderen Satz von Handlern und Logiken aufweisen.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fließend]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Trackinglogs]: https://www.elastic.co/products/logstash
[Monolog]: https://github.com/Seldaek/monolog
