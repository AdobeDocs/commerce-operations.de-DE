---
title: Cron-Aufträge
description: Erfahren Sie mehr über Cron-Gruppen und das Erstellen benutzerdefinierter Cron-Aufträge in Adobe Commerce. Erkunden Sie die Einrichtung geplanter Aufgaben und die Cron-Gruppenkonfiguration.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%
---
# Cron-Aufträge

In diesen Themen wird beschrieben, wie Sie einen benutzerdefinierten Cron-Auftrag und optional eine benutzerdefinierte Cron-Gruppe einrichten. Wenn Ihre Commerce-Erweiterung die regelmäßige Ausführung geplanter Aufgaben erfordert, können Sie diese Themen verwenden, um einen Cron-_Auftrag_ (die geplante Aufgabe) und optional eine _Gruppe_ einzurichten, die benutzerdefinierte Aufgaben gleichzeitig ausführt.

Wenn Sie eine von Commerce bereitgestellte Cron-Gruppe verwenden, müssen Sie keine benutzerdefinierte Cron-Gruppe definieren. Wenn Sie jedoch möchten, dass Ihre Cron-Aufträge nach einem anderen Zeitplan ausgeführt werden oder alle gemeinsam ausgeführt werden sollen, sollten Sie eine Cron-Gruppe definieren

Das Commerce-Programm stellt die folgenden Cron-Gruppen bereit:

- `default`, das die meisten Cron-Aufträge enthält
- `index`, der &quot;[&quot; ](../cli/manage-indexers.md)
- `consumers`, der die Nachrichtenwarteschlange ([) ](../cli/start-message-queues.md)
- Diese Themen sind nur in Adobe Commerce verfügbar
  - `staging`, der [Staging-bezogene) ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging) ausführt
  - `catalog_event` führt Aufgaben für Target- und Warenkorbregeln aus
