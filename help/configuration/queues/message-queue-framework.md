---
title: Übersicht über Nachrichtenwarteschlangen
description: Erfahren Sie mehr über das Nachrichtenwarteschlange-Framework und dessen Funktionsweise mit der Adobe Commerce-Anwendung.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Übersicht über Nachrichtenwarteschlangen

Das Message Queue Framework (MQF) ist ein System, mit dem ein Modul Nachrichten in Warteschlangen veröffentlichen kann. Außerdem werden die [consumer](consumers.md) definiert, die die Nachrichten asynchron empfangen. Der MQF verwendet [[!DNL RabbitMQ]](https://www.rabbitmq.com) als Messaging-Broker, der eine skalierbare Plattform zum Senden und Empfangen von Nachrichten bietet. Es enthält auch einen Mechanismus zum Speichern nicht zugestellter Nachrichten. [!DNL RabbitMQ] basiert auf der AMQP-Spezifikation 0.9.1 (Advanced Message Queuing Protocol).

Das folgende Diagramm zeigt das Message Queue Framework:

![Message Queue Framework](../../assets/configuration/mq-framework.png)

- Ein Herausgeber ist eine Komponente, die Nachrichten an einen Austausch sendet. Sie weiß, an welchen Austausch sie veröffentlichen soll und welches Format sie sendet.

- Ein Austausch empfängt Nachrichten von Herausgebern und sendet sie an Warteschlangen. Obwohl [!DNL RabbitMQ] mehrere Arten von Austauschen unterstützt, verwendet Commerce nur den Themenaustausch. Ein Thema enthält einen Routing-Schlüssel, der durch Punkte getrennte Textzeichenfolgen enthält. Das Format für einen Themennamen ist `string1.string2`: z. B. `customer.created` oder `customer.sent.email`.

  Der Broker ermöglicht Ihnen die Verwendung von Platzhaltern bei der Festlegung von Regeln für die Weiterleitung von Nachrichten. Sie können ein Sternchen (`*`) verwenden, um die Zeichenfolge _one_ oder ein Rautenzeichen (`#`) zu ersetzen, um 0 oder mehr Zeichenfolgen zu ersetzen. Beispielsweise würde `customer.*` nach `customer.create` und `customer.delete` filtern, aber nicht nach `customer.sent.email`. `customer.#` würde jedoch nach `customer.create`, `customer.delete` und `customer.sent.email` filtern.

- Eine Warteschlange ist ein Puffer, der Nachrichten speichert.

- Ein Verbraucher erhält Nachrichten. Er weiß, welche Warteschlange zu verbrauchen ist. Er kann Prozessoren der Nachricht einer bestimmten Warteschlange zuordnen.

Ein einfaches Nachrichtenwarteschlangesystem kann auch ohne Verwendung von [!DNL RabbitMQ] eingerichtet werden. In diesem System speichert ein MySQL-Adapter Nachrichten in der Datenbank. Drei Datenbanktabellen (`queue`, `queue_message` und `queue_message_status`) verwalten die Arbeitslast der Nachrichtenwarteschlange. Cron-Aufträge stellen sicher, dass die Verbraucher Nachrichten empfangen können. Diese Lösung ist nicht sehr skalierbar. [!DNL RabbitMQ] sollte nach Möglichkeit verwendet werden.
