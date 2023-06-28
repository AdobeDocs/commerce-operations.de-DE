---
title: Effektive Cacheplanung
description: Informationen zum erfolgreichen Laden Ihrer Site finden Sie unter den empfohlenen Benchmarks für die Zwischenspeicherung .
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
feature: Integration, Cache
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Planen effektiver Zwischenspeicherung für E-Commerce-Erfolg unter Last

Die Bereitstellung eines Einkaufserlebnisses unter Last erfordert eine gut geplante Cachestrategie. Während die Anfrage von geschäftlichen Stakeholdern zunächst darin bestehen kann, Kunden immer Echtzeit-Produktdaten zu präsentieren, ist dies keine optimale Nutzung von Systemressourcen, und die Auswirkungen der Site-Performance von Endbenutzern würden die Vorteile einer konsistenten Anzeige von Echtzeitinformationen deutlich überwiegen.

Der erste Schritt bei der Cachestrategie sollte daher darin bestehen, mit den relevanten Interessenträgern eine Matrix zulässiger Zwischenspeicherzeiten für die verschiedenen Bereiche der Site zu definieren, z. B.:

| Caching-Bereich | Wie oft ändert sich? | Auswirkungen auf veraltete Inhalte, die aus dem Cache bereitgestellt werden | Zulässige Caching-Time-to-Live (TTL)? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Seiten mit Site-Content-HTML, aktualisiert über CMS | selten | Niedrig | 1 Tag |
| Site-Inhaltsvorlage Medien/Assets - Logo, CSS-Design, Bilder | selten | Niedrig | 1 Woche |
| Produktlistenseiten (PLP) | selten | Mittel | 1 Tag |
| Produktdetailseite (PDP) | Manchmal | Mittel | 1 Stunde |
| Produktkategorien | selten | Mittel | 1 Tag |
| Preise | Häufig | Hoch | Kein Cache |
| Bestand/Lager | Häufig | Hoch | Kein Cache |
| Site-Suche | Die meisten Unique Users | Mittel | Cache-Ergebnisse aus den 100 wichtigsten Suchbegriffen für 1 Tag |
| Checkout | Jeder einzelne Benutzer | Sehr hoch | Kein Cache |
| Warenkorb | Jeder einzelne Benutzer | Sehr hoch | Kein Cache |
| Zahlungsseiten | Jeder einzelne Benutzer | Sehr hoch | Kein Cache |

Nach Abschluss dieser ersten Planung kann die technische Konfiguration eingerichtet werden, um Caches entsprechend diesen Anforderungen zu konfigurieren.

Selbst wenn der Inhalt aktualisiert wird und in der Caching-TTL live geschaltet werden muss, ist es in den meisten Fällen möglich, die Caches für die [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) und [Adobe Commerce](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) selektiv für diesen Inhalt zwischenspeichern, was bedeutet, dass dringende Änderungen sofort übernommen werden. Der Prozess zum manuellen Cache-Löschen sollte ebenfalls im Voraus geplant und getestet werden, sodass, wenn es notwendig ist, ein Update für einige Inhalte manuell zu erzwingen, es in einem Runbook für Site-Vorgänge dokumentiert wird und klar ist, wie und wer beteiligt werden muss, um dies zu tun.
