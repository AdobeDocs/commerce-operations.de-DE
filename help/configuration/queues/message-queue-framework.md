---
title: Übersicht über Nachrichtenwarteschlangen
description: Erfahren Sie mehr über das Meldungswarteschlangen-Framework und seine Funktionsweise mit der Adobe Commerce-Anwendung.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Übersicht über Nachrichtenwarteschlangen

Das Message Queue Framework (MQF) ist ein System, das einem Modul das Veröffentlichen von Nachrichten in Warteschlangen ermöglicht. Außerdem werden die [Verbraucher](consumers.md) definiert, die die Nachrichten asynchron erhalten. MQF unterstützt mehrere Messaging-Broker:

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** : Der primäre Messaging-Broker, der eine skalierbare Plattform für das Senden und Empfangen von Nachrichten bietet. Es enthält einen Mechanismus zum Speichern nicht zugestellter Nachrichten und basiert auf der Spezifikation Advanced Message Queuing Protocol (AMQP) 0.9.1 .
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** - Ein alternativer Messaging-Broker, der das STOMP (Simple Text Oriented Messaging Protocol) für zuverlässiges und skalierbares Messaging verwendet. Einführung in Adobe Commerce 2.4.5 und neueren Versionen.

## RabbitMQ (AMQP)

Die folgende Abbildung zeigt das Message Queue-Framework:

![Message Queue-Framework](../../assets/configuration/mq-framework.png)

- Ein Publisher ist eine Komponente, die Nachrichten an einen Exchange sendet. Er weiß, in welchem Exchange er veröffentlicht werden soll, und kennt das Format der gesendeten Nachrichten.

- Ein Exchange empfängt Nachrichten von Herausgebern und sendet sie an Warteschlangen. Obwohl [!DNL RabbitMQ] mehrere Arten von Austauschen unterstützt, verwendet Commerce nur Themenaustausche. Ein Thema enthält einen Routing-Schlüssel, der Textzeichenfolgen enthält, die durch Punkte getrennt sind. Das Format für einen Themennamen ist `string1.string2`: z. B. `customer.created` oder `customer.sent.email`.

  Der Broker ermöglicht die Verwendung von Platzhaltern beim Festlegen von Regeln für die Weiterleitung von Nachrichten. Sie können ein Sternchen (`*`) verwenden, um _eine Zeichenfolge_ oder ein Rautenzeichen (`#`), um 0 oder mehr Zeichenfolgen zu ersetzen. `customer.*` würden beispielsweise nach `customer.create` und `customer.delete` filtern, jedoch nicht nach `customer.sent.email`. `customer.#` würden jedoch nach `customer.create`, `customer.delete` und `customer.sent.email` filtern.

- Eine Warteschlange ist ein Puffer, der Nachrichten speichert.

- Ein Verbraucher erhält Nachrichten. Es weiß, welche Warteschlange verbraucht werden soll. Er kann Prozessoren der Nachricht einer bestimmten Warteschlange zuordnen.

## Apache ActiveMQ Artemis (STOMP)

Als Alternative zu RabbitMQ unterstützt Adobe Commerce auch [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/) als Messaging-Broker unter Verwendung des Simple Text Oriented Messaging Protocol (STOMP).

>[!NOTE]
>
>ActiveMQ Artemis wurde in Adobe Commerce 2.4.5 und höheren Versionen eingeführt.

Das folgende Diagramm veranschaulicht das STOMP-Framework mit ActiveMQ Artemis:

![STOMP-Framework](../../assets/configuration/stomp-framework.png)

### STOMP-Framework-Komponenten

- Ein **Publisher** ist eine Komponente, die Nachrichten an ein Ziel (Warteschlange oder Thema) sendet. Er weiß, an welchem Ziel er veröffentlichen soll, und kennt das Format der gesendeten Nachrichten.

- Ein **Ziel** in STOMP erfüllt eine ähnliche Rolle wie Austausche in AMQP, indem es Nachrichten von Publishern empfängt und weiterleitet. STOMP verwendet die direkte Zieladressierung mit einem hierarchischen Benennungsmuster anhand von Punkten: z. B. `customer.created` oder `inventory.updated`.

  Adobe Commerce verwendet **ANYCAST** Adressierungsmodus für STOMP-Ziele, der die Punkt-zu-Punkt-Nachrichtenübermittlung ermöglicht. Im ANYCAST-Modus werden Nachrichten aus einem Pool verfügbarer Verbraucher nur an einen Verbraucher gesendet, was einen Lastenausgleich und eine Arbeitsverteilung über mehrere Verbraucherinstanzen ermöglicht.

- Eine **Warteschlange** ist ein Puffer, der Nachrichten speichert. Bei der ANYCAST-Adressierung stellt die Warteschlange sicher, dass Nachrichten nur an einen Verbraucher gesendet werden, selbst wenn mehrere Verbraucher mit demselben Ziel verbunden sind.

- Ein **Verbraucher** erhält Nachrichten von Zielen. Es weiß, welches Ziel abonniert werden soll, und kann Nachrichten mit verschiedenen Bestätigungsmodi (automatisch, Client oder Client-individuell) verarbeiten.

## MySQL-Adapter (Fallback)

Ein einfaches Meldungswarteschlangen-System kann auch ohne Verwendung externer Meldungsbroker eingerichtet werden. In diesem System speichert ein MySQL-Adapter Nachrichten in der Datenbank. Drei Datenbanktabellen (`queue`, `queue_message` und `queue_message_status`) verwalten die Arbeitslast für die Nachrichtenwarteschlange. Cron-Aufträge stellen sicher, dass die Verbraucher Nachrichten empfangen können. Diese Lösung ist nicht sehr skalierbar. Externe Nachrichtenbroker wie [!DNL RabbitMQ] oder Apache ActiveMQ Artemis sollten nach Möglichkeit für Produktionsumgebungen verwendet werden.

## Verwandte Informationen

Für Installations- und Konfigurationsanweisungen:

- [Installieren und Konfigurieren von RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [Installieren und Konfigurieren von ActiveMQ Artemis](../../installation/prerequisites/activemq.md)
- [Verwalten von Nachrichtenwarteschlangen](manage-message-queues.md)
- [Nachrichtenwarteschlangen-Verbraucher](consumers.md)
