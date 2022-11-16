---
title: "Die [!UICONTROL [!DNL RabbitMQ]] tab"
description: Erfahren Sie mehr über die [!UICONTROL [!DNL RabbitMQ]] Registerkarte von [!DNL Observation for Adobe Commerce].
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Die [!UICONTROL [!DNL RabbitMQ]] tab

Die **[!UICONTROL [!DNL RabbitMQ]]** -Tab enthält Informationen, die sich auf [!DNL RabbitMQ] Signale.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastrukturereignisse](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** frame zeigt Infrastrukturereignisse, die Folgendes beinhalten: [!DNL RabbitMQ] die während des ausgewählten Zeitrahmens aufgetreten sind:

* %Antwort [error] für Knoten [rabbit@host1]: unerwartete http-Antwort von%&#39;) als &#39;unerwartetes_resp_node1&#39;
* &#39;%Response [error] für Knoten [rabbit@host2]: unerwartete HTTP-Antwort von%&#39;) als &#39;unerwarteter_resp_node2&#39;
* &#39;%Response [error] für Knoten [rabbit@host3]: unerwartete HTTP-Antwort von%&#39;) als &#39;unerwartetes_resp_node3&#39;
* &#39;%Response [error] für Knoten [rabbit@host3]: Get &quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot;: Kontextdatum überschritten%&quot;) als &quot;node3_timeout_exceeded&quot;
* &#39;%Response [error] für Knoten [rabbit@host1]: Get &quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot;: context deadline exceeded%&#39;) as &#39;node1_timeout_exceeded
* &#39;%Response [error] für Knoten [rabbit@host2]: Get &quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot;: Kontextdatum überschritten%&quot;) als &quot;node2_timeout_exceeded&quot;
* &quot;%401 Unauthorized%&quot;) als &#39;401_unauth&#39;
* &#39;%401 Unauthorized%&#39;) as &#39;401_unauth&#39;
* %Service neu gestartet: rabbitmq-server%&#39;) als &#39;rmq_service_restart&#39;
* &#39;%Response [failed] für Knoten [rabbit@host1]: nodedown%&#39;) als &#39;rmq_node1_down&#39;
* &#39;%Response [failed] für Knoten [rabbit@host2]: nodedown%&#39;) als &#39;rmq_node2_down&#39;
* &#39;%Response [failed] für Knoten [rabbit@host2]: nodedown%&#39;) als &#39;rmq_node2_down&#39;
* &#39;%Entität geändert: exchange/bindings.destination%&#39;) als &#39;rmq_entity_modified&#39;
* &#39;%Entität geändert: exchange/bindings.destination%&#39;) als &#39;rmq_entity_modified&#39;
* &#39;%Entität geändert: queue/exklusiv%&#39;) als &#39;rmq_entity_created_q_exclusive&#39;&#39;%Entität geändert: queue/auto_delete%&#39;) als &#39;rmq_entity_q_delete&#39;
* &#39;%Entität geändert: queue/durable%&#39;) als &#39;rmq_entity_modified_q_durable&#39;
* &#39;%Entität geändert: version/management%&#39;) als &#39;rmq_entity_modified_ver_mgt&#39;
* &#39;%Entität geändert: version/management%&#39;) als &#39;rmq_entity_modified_ver_mgt&#39;

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] Start-/Stopp-Signale des Dienstes](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Dieser Rahmen zeigt [!DNL RabbitMQ] Start-/Stopp-Signale des Dienstes, die während des ausgewählten Zeitrahmens aufgetreten sind:

* &#39;%[!DNL RabbitMQ] wird gebeten zu stoppen...%&#39;) as &#39;rabbitmq_stop&#39;
* &#39;%Starting [!DNL RabbitMQ]%&#39;) als &#39;rabbitmq_start&#39;

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errors](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Dieser Rahmen zeigt [!DNL RabbitMQ] Fehler, die während des ausgewählten Zeitrahmens aufgetreten sind:

* &#39;%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%&#39;} as &#39;exit_timeout&#39;
* &#39;%Client unerwartet geschlossene TCP-Verbindung%&#39;) als &#39;client_closed_tcp_conn&#39;
* &#39;%at undefined exit with reason shutdown in context shutdown_error%&#39;) as &#39;undef_exit&#39;
* &#39;%Verbindungsversuch von unzulässigem Knoten%&#39;) als &#39;disallowed_node&#39;
* &#39;%schließend AMQP connection%&#39;) as &#39;rmq_err_amqp_conn&#39;

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] Knotenstatus](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* &#39;%rabbit on node rabbit@host1 down%&#39;) as &#39;rmq_node1_down&#39;
* &#39;%rabbit on node rabbit@host2 down%&#39;) as &#39;rmq_node2_down&#39;
* &#39;%rabbit on node rabbit@host3 down%&#39;) as &#39;rmq_node3_down&#39;
* &#39;%rabbit on node rabbit@host1 up%&#39;) as &#39;rmq_node1_up&#39;
* &#39;%rabbit on node rabbit@host2 up%&#39;) as &#39;rmq_node2_up&#39;
* &#39;%rabbit on node rabbit@host3 up%&#39;) as &#39;rmq_node3_up&#39;

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] Message High Level Summary status by Queue](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** Das Diagramm zeigt die Anzahl der veröffentlichten Nachrichten nach [!DNL RabbitMQ] Warteschlange für den ausgewählten Zeitrahmen.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Zusammenfassung der Nachrichtendetails](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* &#39;%report.ERROR: Cron Job consumer_runner hat einen Fehler: NOT_FOUND - no queue%&#39;) as &#39;queue_err&#39;
* &#39;%report.ERROR: Cron Job consumer_runner hat einen Fehler: NOT_FOUND - no queue%&#39;) as &#39;queue_err&#39;
* &#39;%authenticated and allowed access to vhost%&#39;) as &#39;auth&#39;
* &#39;%schließend AMQP connection%&#39;) als &#39;close_conn&#39;

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Warteschlangenverbrauch MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** gibt die Anzahl der Bytes an, die von jedem [!DNL RabbitMQ] Warteschlange über den ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Veröffentlichte Nachrichten nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** gibt die Anzahl der Bytes an, die von jedem [!DNL RabbitMQ] Warteschlange über den ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Veröffentlichter Nachrichtendurchsatz nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** Das Diagramm zeigt die durchschnittliche Anzahl der veröffentlichten Nachrichten pro Sekunde nach [!DNL RabbitMQ] Warteschlange über den ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Gesamtdurchsatz der Nachrichten nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** Das Diagramm zeigt die durchschnittliche Gesamtzahl der Nachrichten pro Sekunde nach [!DNL RabbitMQ] Warteschlange über den ausgewählten Zeitraum.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Verbraucher nach Warteschlange](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

Die **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** Das Diagramm zeigt die durchschnittliche Gesamtanzahl der Verbraucher nach [!DNL RabbitMQ] Warteschlange über den ausgewählten Zeitraum.
