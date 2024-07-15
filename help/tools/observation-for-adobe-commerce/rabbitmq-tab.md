---
title: Registerkarte "[!UICONTROL [!DNL RabbitMQ]"
description: Erfahren Sie mehr über die Registerkarte "[!UICONTROL [!DNL RabbitMQ]" von  [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Registerkarte [!UICONTROL [!DNL RabbitMQ]]

Der Tab **[!UICONTROL [!DNL RabbitMQ]]** enthält Informationen, die sich auf [!DNL RabbitMQ] -Signale konzentrieren.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastrukturereignisse](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

Der Frame **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** zeigt Infrastrukturereignisse mit [!DNL RabbitMQ] an, die während des ausgewählten Zeitraums aufgetreten sind:

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
* `%Entity modified: queue/exclusive%`) als `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) als `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) als `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) als `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) als `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] Start-/Stopp-Signale des Dienstes](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Dieser Frame zeigt die [!DNL RabbitMQ] Start-/Stopp-Signale des Diensts, die während des ausgewählten Zeitrahmens aufgetreten sind:

* `%RabbitMQ is asked to stop...%`) als `rabbitmq_stop`
* `%Starting RabbitMQ%`) als `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errors](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Dieser Frame zeigt [!DNL RabbitMQ] Fehler, die während des ausgewählten Zeitrahmens aufgetreten sind:

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

![[!DNL RabbitMQ] Message High Level Summary status by Queue](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

Das Diagramm **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** zeigt die Anzahl der veröffentlichten Nachrichten durch die [!DNL RabbitMQ]-Warteschlange für den ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Zusammenfassung der Nachrichtendetails](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) als `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) als `queue_err`
* `%authenticated and granted access to vhost%`) als `auth`
* `%closing AMQP connection%`) als `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Warteschlangenkonsum MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

Das Diagramm **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** zeigt die Anzahl der Bytes an, die von jeder [!DNL RabbitMQ]-Warteschlange im ausgewählten Zeitraum verbraucht wurden.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Veröffentlichte Nachrichten nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

Das Diagramm **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** zeigt die Anzahl der Bytes an, die von jeder [!DNL RabbitMQ]-Warteschlange im ausgewählten Zeitraum verbraucht wurden.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Veröffentlichter Nachrichtendurchsatz nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

Das Diagramm **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** zeigt die durchschnittliche Anzahl der veröffentlichten Nachrichten pro Sekunde durch jede [!DNL RabbitMQ] Warteschlange im ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Gesamtdurchsatz der Nachrichten nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

Das Diagramm **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** zeigt die durchschnittliche Gesamtzahl der Nachrichten pro Sekunde nach jeder [!DNL RabbitMQ] Warteschlange im ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Verbraucher nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

Das Diagramm **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** zeigt die durchschnittliche Gesamtzahl der Verbraucher nach jeder [!DNL RabbitMQ]-Warteschlange im ausgewählten Zeitraum.
