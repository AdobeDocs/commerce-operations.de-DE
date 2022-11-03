---
title: Best Practices für die Konfiguration von Indexern
description: Behalten und optimieren Sie die Site-Leistung, indem Sie Best Practices für die Indexkonfiguration befolgen.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Best Practices für die Indexkonfiguration

Um die Site-Leistung zu optimieren und zu erhalten, überprüfen und aktualisieren Sie die Indexkonfiguration anhand der in diesem Artikel beschriebenen Best Practices für die Leistung.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Indexer festlegen, die planmäßig aktualisiert werden sollen

Adobe Commerce verfügt über zwei Arten von Indexmodi: [!UICONTROL Update on Save] (Standardeinstellung) und [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** -Modus aktualisiert Indizes sofort, wenn sich Ihr Katalog oder andere Daten ändern. Wenn ein Admin-Benutzer beispielsweise einer Kategorie neue Produkte hinzufügt, wird der Kategorieproduktindex sofort nach dem Speichern der Aktualisierung neu indiziert.

- **[!UICONTROL Update on Schedule]** -Modus speichert Informationen über Datenaktualisierungen. Neuindizierungsvorgänge und Indexaktualisierungen werden von einem Cron-Auftrag verwaltet, der in terminierten Intervallen im Hintergrund ausgeführt wird.

Ein großer Speicher mit mehreren Administratoren, die im Backend arbeiten oder über viele Import- und Export-Trigger verfügen, führt häufige Indexaktualisierungen durch. Wenn Ihre Site-Indexkonfiguration auf [!UICONTROL Update on Save] -Modus beeinträchtigt die häufige Neuindizierung die Datenbankleistung, was die Site-Leistung verlangsamt und zu langen Verzögerungen im Neuindizierungsprozess führt, insbesondere bei großen Geschäften.

Um die Site-Leistung zu maximieren, befolgen Sie die folgenden Best Practices für die Indizierung:

- Überprüfen Sie die Indexkonfiguration.
- Legen Sie die Indexer auf _[!UICONTROL Update on Schedule]_für große Sites und Sites mit häufigen Aktualisierungen und hohem Traffic. Siehe [Indexverwaltung](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Folgen [Best Practices für die Leistung](../../../performance/configuration.md) für die Verwaltung von Indizes.

## Zusätzliche Informationen

- [Indexverwaltung für Admin-Benutzer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexverwaltung mithilfe der Magento-CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Indizierungsübersicht für Entwickler](https://developer.adobe.com/commerce/php/development/components/indexing/)
