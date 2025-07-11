---
title: Best Practices für die Konfiguration von Indexern
description: Verwalten und optimieren Sie die Site-Performance, indem Sie die Best Practices für die Indexerkonfiguration befolgen.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Best Practices für die Indexerkonfiguration

Um die Leistung der Site zu optimieren und aufrechtzuerhalten, überprüfen und aktualisieren Sie die Indexerkonfiguration mithilfe der in diesem Artikel beschriebenen Best Practices zur Leistung.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Festlegen der zu aktualisierenden Indexer auf einen Zeitplan

Adobe Commerce verfügt über zwei Indexermodi: [!UICONTROL Update on Save] und [!DNL Update on Schedule].

- Der **[!UICONTROL Update on Save]** aktualisiert Indizes sofort, wenn sich Ihr Katalog oder andere Daten ändern. Wenn beispielsweise ein Administrator einer Kategorie neue Produkte hinzufügt, wird der Kategorieproduktindex sofort neu indiziert, wenn die Aktualisierung gespeichert wird.

- **[!UICONTROL Update on Schedule]** Modus speichert Informationen zu Datenaktualisierungen, und Neuindizierungsvorgänge und Indexaktualisierungen werden von einem Cron-Auftrag verwaltet, der im Hintergrund in terminierten Intervallen ausgeführt wird. Der Cron-Auftrag führt nicht immer bei jeder Ausführung eine Neuindizierung durch. Die Neuindizierung erfolgt nur, wenn in den Änderungsprotokollen des Indexers neue Einträge vorhanden sind (z. B. ein Rückstand bei den Indexern).

Einen großen Store mit mehreren Administratoren im Backend oder mit vielen Importen und Exporten zu haben, führt häufige Indexaktualisierungen durch Trigger. Wenn die Site-Indexkonfiguration auf den [!UICONTROL Update on Save]-Modus eingestellt ist, beeinträchtigt eine häufige Neuindizierung die Datenbankleistung, was die Site-Leistung verlangsamt und zu langen Verzögerungen beim Neuindizierungsprozess führt, insbesondere bei großen Stores.

Um die Site-Performance zu maximieren, befolgen Sie die folgenden Best Practices für die Indizierung:

- Überprüfen Sie die Indexkonfiguration.
- Legen Sie die Indexer auf _[!UICONTROL Update on Schedule]_für große Websites und Websites mit häufigen Aktualisierungen und hohem Traffic fest. Siehe [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Befolgen Sie [Best Practices zur Leistung](../../../performance/configuration.md) für die Verwaltung von Indizes.

>[!IMPORTANT]
>
>Das [!DNL Customer Grid] Indexerverhalten hat sich in Version 2.4.8 geändert:
>
>- **Vor 2.4.8**: Der [!DNL Customer Grid]-Indexer kann nur mithilfe der Option &quot;[!UICONTROL Update on Save]&quot; neu indiziert werden und unterstützt die Option &quot;[!UICONTROL Update by Schedule]&quot; nicht.
>- **2.4.8 und höher**: Der [!DNL Customer Grid] Indexer unterstützt sowohl [!UICONTROL Update on Save]- als auch [!UICONTROL Update by Schedule] Modi und [!UICONTROL Update by Schedule] standardmäßig.

## Weitere Informationen

- [Indexverwaltung für Admin-Benutzer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexverwaltung mithilfe der Magento-CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Übersicht über die Indizierung für Entwickler](https://developer.adobe.com/commerce/php/development/components/indexing/)
