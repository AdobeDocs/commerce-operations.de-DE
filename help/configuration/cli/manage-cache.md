---
title: Cache verwalten
description: Verwalten von Cache-Typen und Anzeigen des Cache-Status über die Befehlszeile mithilfe der Commerce-CLI
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 1070291396144f866cadd5e42ebca3e77a484a9b
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Cache verwalten

{{file-system-owner}}

## Cache-Typen

Sie können das Cache-Management-System von Adobe Commerce verwenden, um die Leistung Ihrer Site zu verbessern. In diesem Thema wird erläutert, wie Systemadministratoren oder Entwickler mit Zugriff auf den Commerce-Anwendungsserver Caches über die Befehlszeile verwalten können.

>[!NOTE]
>
>
>Commerce-Site-Administratoren können den Cache über die Admin mithilfe des Tools Cache Management System verwalten. Siehe [Cache-Verwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) in der _Handbuch für Admin-Systeme_.


## Anzeigen des Cache-Status

Zeigen Sie in der Befehlszeile des Commerce-Anwendungs-Servers den Status des Caches mithilfe der `cache:status` Commerce-CLI-Befehl.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Es folgt ein Beispiel:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Eine ausführliche Beschreibung der von Adobe Commerce unterstützten Standard-Cache-Typen finden Sie unter [Caches](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) in der _Handbuch für Admin-Systeme_.


## Aktivieren oder Deaktivieren von Cache-Typen

Mit diesem Befehl können Sie alle oder nur die von Ihnen angegebenen Cache-Typen aktivieren oder deaktivieren. Die Deaktivierung von Cache-Typen ist während der Entwicklung nützlich, da die Ergebnisse der Änderungen angezeigt werden, ohne dass der Cache geleert werden muss. Die Deaktivierung von Cache-Typen hat jedoch negative Auswirkungen auf die Leistung.

>[!INFO]
>
>Ab Version 2.2 können Sie Cache-Typen nur über die Befehlszeile aktivieren oder deaktivieren, während Sie Commerce im Produktionsmodus ausführen. Wenn Sie Commerce im Entwicklermodus ausführen, können Sie Cache-Typen über die Befehlszeile oder manuell aktivieren oder deaktivieren. Bevor Sie dies tun, müssen Sie manuell `<magento_root>/app/etc/env.php` Schreibbar durch die [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).

Sie können Folgendes bereinigen (auch als _Flush_ oder _auffrischen_) Cache-Typen, die entweder die Befehlszeile oder den Administrator verwenden.

Befehlsoptionen:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Wobei weggelassen wird `[type]` Aktiviert oder deaktiviert alle Cache-Typen gleichzeitig. Die `type` ist eine durch Leerzeichen getrennte Liste von Cache-Typen.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Auflisten der Cache-Typen und ihres Status:

```bash
bin/magento cache:status
```

So deaktivieren Sie beispielsweise den vollständigen Seiten-Cache und den DDL-Cache:

```bash
bin/magento cache:disable db_ddl full_page
```

Beispielergebnis:

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Durch die Aktivierung eines Cache-Typs wird dieser Cache-Typ automatisch gelöscht.

>[!INFO]
>
>Ab Version 2.3.4 speichert Commerce alle EAV-Attribute des Systems zwischen, wenn sie abgerufen werden. Das Caching von EAV-Attributen auf diese Weise verbessert die Leistung, da es die Anzahl der Einfüge-/Auswahlanfragen an die DB verringert. Es erhöht jedoch auch die Cache-Netzwerkgröße. Entwickler können benutzerdefinierte EAV-Attribute zwischenspeichern, indem sie die `bin/magento config:set dev/caching/cache_user_defined_attributes 1` Befehl. Dies kann auch über die Admin in erfolgen. [Entwicklermodus](../bootstrap/application-modes.md) nach Einstellung **Stores** > Einstellungen **Konfiguration** > **Erweitert** > **Entwickler** > **Caching-Einstellungen** > **Benutzerdefinierte Attribute zwischenspeichern** bis **Ja**.

## Cache-Typen bereinigen und leeren

>[!NOTE]
>
>Der Cache für mehrere Seiten kann gleichzeitig und automatisch ungültig gemacht werden **_ohne_** Diese Entitäten werden bearbeitet. Dies ist beispielsweise der Fall, wenn ein Produkt im Katalog einer Kategorie zugewiesen ist oder wenn [!UICONTROL related product rule] wurde geändert.

Um veraltete Elemente aus dem Cache zu löschen, haben Sie folgende Möglichkeiten _sauber_ oder _Flush_ Cache-Typen:

- Das Bereinigen eines Cache-Typs löscht nur alle Elemente aus aktivierten Commerce-Cache-Typen. Mit anderen Worten: Diese Option wirkt sich nicht auf andere Prozesse oder Anwendungen aus, da sie nur den Cache bereinigt, den Commerce verwendet.

  Deaktivierte Cache-Typen werden nicht bereinigt.

  >[!TIP]
  >
  >Bereinigen Sie den Cache immer, nachdem Sie Versionen von Magento Open Source oder Adobe Commerce aktualisiert haben, von Magento Open Source auf Adobe Commerce aktualisiert haben oder B2B für Adobe Commerce oder ein beliebiges Modul installiert haben.

- Durch Leeren eines Cache-Typs wird der Cache-Speicher gelöscht, was sich auf andere Prozesse und Anwendungen auswirken kann, die denselben Speicher verwenden.

Leeren Sie Cache-Typen, wenn Sie bereits versucht haben, den Cache zu bereinigen, und weiterhin Probleme auftreten, die Sie nicht isolieren können.

Befehlsverwendung:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Hierbei gilt `[type]` ist eine durch Leerzeichen getrennte Liste von Cache-Typen. Weglassen `[type]` Bereinigt oder leert alle Cache-Typen gleichzeitig. Um beispielsweise alle Cache-Typen zu leeren, geben Sie Folgendes ein

```bash
   bin/magento cache:flush
```

Beispielergebnis:

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>Sie können Cache-Typen auch in Admin bereinigen und leeren. Zu gehen **System** > **Tools** > **Cache-Verwaltung**. **Cache-Speicher leeren** entspricht `bin/magento cache:flush`. **Leeren des Magento-Cache** entspricht `bin/magento cache:clean`.
