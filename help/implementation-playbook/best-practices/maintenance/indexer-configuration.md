---
title: Best Practices für die Konfiguration von Indexern
description: Behalten und optimieren Sie die Site-Leistung, indem Sie Best Practices für die Indexkonfiguration befolgen.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Best Practices für die Indexkonfiguration

Um die Site-Leistung zu optimieren und zu erhalten, überprüfen und aktualisieren Sie die Indexkonfiguration anhand der in diesem Artikel beschriebenen Best Practices für die Leistung.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Indexer festlegen, die planmäßig aktualisiert werden sollen

Adobe Commerce verfügt über zwei Typen von Indexmodi: [!UICONTROL Update on Save] (Standardeinstellung) und [!DNL Update on Schedule].

- Der Modus **[!UICONTROL Update on Save]** aktualisiert Indizes sofort, wenn sich Ihr Katalog oder andere Daten ändern. Wenn ein Admin-Benutzer beispielsweise einer Kategorie neue Produkte hinzufügt, wird der Kategorieproduktindex sofort nach dem Speichern der Aktualisierung neu indiziert.

- Der Modus **[!UICONTROL Update on Schedule]** speichert Informationen über Datenaktualisierungen, und Neuindizierungsvorgänge und Indexaktualisierungen werden von einem Cron-Auftrag verwaltet, der in terminierten Intervallen im Hintergrund ausgeführt wird. Der Cron-Auftrag führt nicht immer bei jeder Ausführung eine Neuindizierung durch. Er wird nur dann neu indiziert, wenn neue Einträge in den Indexänderungsprotokollen vorhanden sind (z. B. gibt es einen Rückstand bei den Indexern).

Ein großer Speicher mit mehreren Administratoren, die im Backend arbeiten oder über viele Import- und Export-Trigger verfügen, führt häufige Indexaktualisierungen durch. Wenn für Ihre Site-Indexkonfiguration der Modus &quot;[!UICONTROL Update on Save]&quot; eingestellt ist, beeinträchtigt die häufige Neuindizierung die Datenbankleistung, was die Site-Leistung verlangsamt und zu langen Verzögerungen beim Neuindizierungsprozess führt, insbesondere bei großen Stores.

Um die Site-Leistung zu maximieren, befolgen Sie die folgenden Best Practices für die Indizierung:

- Überprüfen Sie die Indexkonfiguration.
- Setzen Sie die Indexer für große Sites auf &quot;_[!UICONTROL Update on Schedule]_&quot;, für Sites mit häufigen Aktualisierungen und hohem Traffic. Siehe [Indexverwaltung](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Befolgen Sie [Best Practices zur Performance](../../../performance/configuration.md) für die Verwaltung von Indizes.

>[!IMPORTANT]
>
>Die [!DNL Customer Grid] -Option kann nur mit der [!UICONTROL Update on Save] -Option neu indiziert werden. Dieser Index unterstützt die `Update by Schedule` -Option nicht.

## Weitere Informationen

- [Indexverwaltung für Admin-Benutzer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexverwaltung mithilfe der Magento-CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Indizierungsübersicht für Entwickler](https://developer.adobe.com/commerce/php/development/components/indexing/)
