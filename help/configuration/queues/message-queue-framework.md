---
title: Übersicht über Nachrichtenwarteschlangen
description: Erfahren Sie mehr über das Meldungswarteschlangen-Framework und seine Funktionsweise mit der Adobe Commerce-Anwendung.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Übersicht über Nachrichtenwarteschlangen

Das Message Queue Framework (MQF) ist ein System, das einem Modul das Veröffentlichen von Nachrichten in Warteschlangen ermöglicht. Außerdem werden die [Verbraucher](consumers.md) definiert, die die Nachrichten asynchron erhalten. Der MQF verwendet [[!DNL RabbitMQ]](https://www.rabbitmq.com) als Messaging-Broker, der eine skalierbare Plattform für den Versand und Empfang von Nachrichten bietet. Sie enthält auch einen Mechanismus zum Speichern nicht zugestellter Nachrichten. [!DNL RabbitMQ] basiert auf der Spezifikation des Advanced Message Queuing Protocol (AMQP) 0.9.1.

Die folgende Abbildung zeigt das Message Queue-Framework:

![Message Queue-Framework](../../assets/configuration/mq-framework.png)

- Ein Publisher ist eine Komponente, die Nachrichten an einen Exchange sendet. Er weiß, in welchem Exchange er veröffentlicht werden soll, und kennt das Format der gesendeten Nachrichten.

- Ein Exchange empfängt Nachrichten von Herausgebern und sendet sie an Warteschlangen. Obwohl [!DNL RabbitMQ] mehrere Arten von Austauschen unterstützt, verwendet Commerce nur Themenaustausche. Ein Thema enthält einen Routing-Schlüssel, der Textzeichenfolgen enthält, die durch Punkte getrennt sind. Das Format für einen Themennamen ist `string1.string2`: z. B. `customer.created` oder `customer.sent.email`.

  Der Broker ermöglicht die Verwendung von Platzhaltern beim Festlegen von Regeln für die Weiterleitung von Nachrichten. Sie können ein Sternchen (`*`) verwenden, um _eine Zeichenfolge_ oder ein Rautenzeichen (`#`), um 0 oder mehr Zeichenfolgen zu ersetzen. `customer.*` würden beispielsweise nach `customer.create` und `customer.delete` filtern, jedoch nicht nach `customer.sent.email`. `customer.#` würden jedoch nach `customer.create`, `customer.delete` und `customer.sent.email` filtern.

- Eine Warteschlange ist ein Puffer, der Nachrichten speichert.

- Ein Verbraucher erhält Nachrichten. Es weiß, welche Warteschlange verbraucht werden soll. Er kann Prozessoren der Nachricht einer bestimmten Warteschlange zuordnen.

Ein einfaches Meldungswarteschlangen-System kann auch ohne [!DNL RabbitMQ] eingerichtet werden. In diesem System speichert ein MySQL-Adapter Nachrichten in der Datenbank. Drei Datenbanktabellen (`queue`, `queue_message` und `queue_message_status`) verwalten die Arbeitslast für die Nachrichtenwarteschlange. Cron-Aufträge stellen sicher, dass die Verbraucher Nachrichten empfangen können. Diese Lösung ist nicht sehr skalierbar. [!DNL RabbitMQ] sollte nach Möglichkeit verwendet werden.
