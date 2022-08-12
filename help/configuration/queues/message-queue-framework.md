---
title: Übersicht über Nachrichtenwarteschlangen
description: Erfahren Sie mehr über das Nachrichtenwarteschlange-Framework und dessen Funktionsweise mit der Adobe Commerce- und Magento Open Source-Anwendung.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Übersicht über Nachrichtenwarteschlangen

Das Message Queue Framework (MQF) ist ein System, das eine [Modul](https://glossary.magento.com/module) , um Nachrichten in Warteschlangen zu veröffentlichen. Außerdem werden die Verbraucher definiert, die die Nachrichten asynchron erhalten. Der MQF verwendet [RabbitMQ](https://www.rabbitmq.com) als Messaging Broker, der eine skalierbare Plattform für den Versand und Empfang von Nachrichten bietet. Es enthält auch einen Mechanismus zum Speichern nicht zugestellter Nachrichten. RabbitMQ basiert auf der AMQP-Spezifikation 0.9.1 (Advanced Message Queuing Protocol).

Das folgende Diagramm zeigt das Message Queue Framework:

![Message Queue Framework](../../assets/configuration/mq-framework.png)

- A [publisher](https://glossary.magento.com/publisher-subscriber-pattern) ist eine Komponente, die Nachrichten an einen Austausch sendet. Sie weiß, an welchen Austausch sie veröffentlichen soll und welches Format sie sendet.

- Ein Austausch empfängt Nachrichten von Herausgebern und sendet sie an Warteschlangen. Obwohl RabbitMQ mehrere Arten von Austauschen unterstützt, verwendet Commerce nur den Themenaustausch. Ein Thema enthält einen Routing-Schlüssel, der durch Punkte getrennte Textzeichenfolgen enthält. Das Format für einen Themennamen lautet `string1.string2`: Beispiel: `customer.created` oder `customer.sent.email`.

   Der Broker ermöglicht Ihnen die Verwendung von Platzhaltern bei der Festlegung von Regeln für die Weiterleitung von Nachrichten. Sie können ein Sternchen (`*`) zu ersetzen _one_ Zeichenfolge oder Rautezeichen (`#`), um 0 oder mehr Zeichenfolgen zu ersetzen. Beispiel: `customer.*` würde nach `customer.create` und `customer.delete`, aber nicht `customer.sent.email`. Jedoch `customer.#` würde nach `customer.create`,  `customer.delete`und `customer.sent.email`.

- Eine Warteschlange ist ein Puffer, der Nachrichten speichert.

- Ein Verbraucher erhält Nachrichten. Er weiß, welche Warteschlange zu verbrauchen ist. Er kann Prozessoren der Nachricht einer bestimmten Warteschlange zuordnen.

Ein einfaches Nachrichtenwarteschlangesystem kann auch ohne RabbitMQ eingerichtet werden. In diesem System eine MySQL [Adapter](https://glossary.magento.com/adapter) speichert Nachrichten in der Datenbank. Drei Datenbanktabellen (`queue`, `queue_message`und `queue_message_status`) den Arbeitsaufwand für die Nachrichtenwarteschlange verwalten. Cron-Aufträge stellen sicher, dass die Verbraucher Nachrichten empfangen können. Diese Lösung ist nicht sehr skalierbar. RabbitMQ sollte nach Möglichkeit verwendet werden.