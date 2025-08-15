---
title: Die Registerkarte [[!UICONTROL [!DNL RabbitMQ]]
description: Erfahren Sie mehr über die Registerkarte [[!UICONTROL [!DNL RabbitMQ]] von [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Die Registerkarte [!UICONTROL [!DNL RabbitMQ]]

Die Registerkarte **[!UICONTROL [!DNL RabbitMQ]]** enthält Informationen, die auf [!DNL RabbitMQ] Signale ausgerichtet sind.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastrukturereignisse](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

Der **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** zeigt Infrastrukturereignisse an, die [!DNL RabbitMQ] betreffen, die im ausgewählten Zeitraum aufgetreten sind:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) als `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) als `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) als `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) als `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) als `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) als `node2_timeout_exceeded`
* `%401 Unauthorized%`) als `401_unauth`
* `%401 Unauthorized%`) als `401_unauth`
* `%Service restarted: rabbitmq-server%`) als `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) als `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) als `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) als `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) als `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) als `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) als `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) als `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) als `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

Start-/Stopp-Signale ![[!DNL RabbitMQ] Dienstes](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Dieser Frame zeigt [!DNL RabbitMQ] Start-/Stopp-Signale für den Dienst an, die während des ausgewählten Zeitraums aufgetreten sind:

* `%RabbitMQ is asked to stop...%`) als `rabbitmq_stop`
* `%Starting RabbitMQ%`) als `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] Fehler](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Dieser Frame zeigt [!DNL RabbitMQ] Fehler an, die während des ausgewählten Zeitraums aufgetreten sind:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` als `exit_timeout`
* `%client unexpectedly closed TCP connection%`) als `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) als `undef_exit`
* `%Connection attempt from disallowed node%`) als `disallowed_node`
* `%closing AMQP connection%`) als `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] Knotenstatus](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) als `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) als `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) als `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) als `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) als `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) als `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] des Status der allgemeinen Nachrichtenübersicht nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

Das **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** Diagramm zeigt die Anzahl der veröffentlichten Nachrichten durch die [!DNL RabbitMQ] für den ausgewählten Zeitraum an.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Zusammenfassung der Nachrichtendetails](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) als `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) als `queue_err`
* `%authenticated and granted access to vhost%`) als `auth`
* `%closing AMQP connection%`) als `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ]-Warteschlangenverbrauch MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

Das **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** Diagramm zeigt die Anzahl der Bytes an, die von jeder [!DNL RabbitMQ]-Warteschlange im ausgewählten Zeitraum verbraucht wurden.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] von veröffentlichten Nachrichten nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

Das **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** Diagramm zeigt die Anzahl der Bytes an, die von jeder [!DNL RabbitMQ]-Warteschlange im ausgewählten Zeitraum verbraucht wurden.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] den Durchsatz veröffentlichter Nachrichten nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

Das **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** Diagramm zeigt die durchschnittliche Anzahl der veröffentlichten Nachrichten pro Sekunde für jede [!DNL RabbitMQ] im ausgewählten Zeitraum an.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Nachrichtendurchsatz pro Warteschlange insgesamt](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

Das **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** Diagramm zeigt die durchschnittliche Gesamtzahl der Nachrichten pro Sekunde für jede [!DNL RabbitMQ]-Warteschlange im ausgewählten Zeitraum an.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

Verbraucher nach Warteschlange ![[!DNL RabbitMQ]](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

Das **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** Diagramm zeigt die durchschnittliche Gesamtanzahl der Verbraucher pro [!DNL RabbitMQ] im ausgewählten Zeitraum an.
