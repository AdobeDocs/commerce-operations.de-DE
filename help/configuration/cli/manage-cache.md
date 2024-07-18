---
title: Verwalten des Cache
description: Verwalten von Cache-Typen und Anzeigen des Cache-Status über die Befehlszeile mithilfe der Commerce-CLI
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Verwalten des Cache

{{file-system-owner}}

## Cachetypen

Sie können das Cache-Management-System von Adobe Commerce verwenden, um die Leistung Ihrer Site zu verbessern. In diesem Thema wird erläutert, wie Systemadministratoren oder Entwickler mit Zugriff auf den Commerce-Anwendungsserver Caches über die Befehlszeile verwalten können.

>[!NOTE]
>
>
>Community-Site-Administratoren können den Cache vom Admin mithilfe des Tools Cache Management System verwalten. Siehe [Cache-Verwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) im _Administratorsystemhandbuch_.


## Cache-Status anzeigen

Zeigen Sie in der Befehlszeile des Commerce-Anwendungsservers den Cache-Status mit dem Befehl `cache:status` Commerce CLI an.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Ein Beispiel:

```
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
>Eine ausführliche Beschreibung der von Adobe Commerce unterstützten Standard-Cache-Typen finden Sie unter [Caches](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) im _Administratorsystemhandbuch_.


## Cache-Typen aktivieren oder deaktivieren

Mit diesem Befehl können Sie alle oder nur die angegebenen Cache-Typen aktivieren oder deaktivieren. Das Deaktivieren von Cache-Typen ist während der Entwicklung nützlich, da Sie die Ergebnisse Ihrer Änderungen sehen, ohne den Cache leeren zu müssen. Das Deaktivieren von Cache-Typen hat jedoch negative Auswirkungen auf die Leistung.

>[!INFO]
>
>Ab Version 2.2 können Sie Cache-Typen nur über die Befehlszeile aktivieren oder deaktivieren, während Commerce im Produktionsmodus ausgeführt wird. Wenn Sie Commerce im Entwicklermodus ausführen, können Sie Cache-Typen über die Befehlszeile oder manuell aktivieren oder deaktivieren. Bevor Sie dies tun, müssen Sie `<magento_root>/app/etc/env.php` vom [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) manuell schreiben können.

Sie können Cache-Typen entweder über die Befehlszeile oder den Administrator bereinigen (auch als _flush_ oder _refresh_ bezeichnet).

Befehlsoptionen:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Wenn `[type]` weggelassen wird, werden alle Cache-Typen gleichzeitig aktiviert oder deaktiviert. Die Option `type` ist eine durch Leerzeichen getrennte Liste von Cache-Typen.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

So listen Sie Cache-Typen und ihren Status auf:

```bash
bin/magento cache:status
```

So deaktivieren Sie beispielsweise den vollständigen Seiten-Cache und den DDL-Cache:

```bash
bin/magento cache:disable db_ddl full_page
```

Beispielergebnis:

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Durch die Aktivierung eines Cache-Typs wird dieser Cache-Typ automatisch gelöscht.

>[!INFO]
>
>Ab Version 2.3.4 speichert Commerce alle System-EAV-Attribute beim Abrufen zwischen. Das Zwischenspeichern von EAV-Attributen auf diese Weise verbessert die Leistung, da dadurch die Anzahl der Einfüge-/Auswahlanfragen an die DB verringert wird. Es erhöht jedoch auch die Größe des Cache-Netzwerks. Entwickler können benutzerdefinierte EAV-Attribute zwischenspeichern, indem sie den Befehl `bin/magento config:set dev/caching/cache_user_defined_attributes 1` ausführen. Dies kann auch vom Administrator im [Entwicklermodus](../bootstrap/application-modes.md) durchgeführt werden, indem **Stores** > Einstellungen **Konfiguration** > **Erweitert** > **Entwickler** > **Caching-Einstellungen** > **Benutzerdefinierte Attribute zwischenspeichern** auf **Ja** eingestellt werden.

## Cache-Typen leeren

>[!NOTE]
>
>Der Cache mehrerer Seiten kann gleichzeitig und automatisch mit **_ohne_** ungültig gemacht werden. Wenn beispielsweise ein Produkt im Katalog einer Kategorie zugewiesen wird oder eine beliebige [!UICONTROL related product rule] geändert wird.

Um veraltete Elemente aus dem Cache zu löschen, können Sie die Cache-Typen _clean_ oder _flush_ löschen:

- Beim Löschen eines Cache-Typs werden nur alle Elemente aus aktivierten Commerce-Cache-Typen gelöscht. Mit anderen Worten: Diese Option wirkt sich nicht auf andere Prozesse oder Anwendungen aus, da sie nur den von Commerce verwendeten Cache löscht.

  Deaktivierte Cache-Typen werden nicht bereinigt.

  >[!TIP]
  >
  >Bereinigen Sie den Cache immer, nachdem Sie Adobe Commerce-Versionen aktualisiert, von Magento Open Source auf Adobe Commerce aktualisiert oder B2B für Adobe Commerce oder ein beliebiges Modul installiert haben.

- Beim Löschen eines Cache-Typs wird der Cache-Speicher geleert, was sich möglicherweise auf andere Prozessanwendungen auswirkt, die denselben Speicher verwenden.

Cache-Typen leeren, wenn Sie bereits versucht haben, den Cache zu bereinigen, und weiterhin Probleme auftreten, die Sie nicht isolieren können.

Befehlsverwendung:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Wobei `[type]` eine durch Leerzeichen getrennte Liste von Cache-Typen ist. Wenn Sie `[type]` auslassen, werden alle Cache-Typen gleichzeitig geleert oder geleert. Um beispielsweise alle Cache-Typen zu leeren, geben Sie

```bash
   bin/magento cache:flush
```

Beispielergebnis:

```
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
>Sie können Cache-Typen auch in Admin löschen und leeren. Wechseln Sie zu &quot;**System**&quot;> &quot;**Tools**&quot;> &quot;**Cache-Verwaltung**&quot;. **Cache-Speicher leeren** entspricht `bin/magento cache:flush`. **Magento-Cache leeren** entspricht `bin/magento cache:clean`.
