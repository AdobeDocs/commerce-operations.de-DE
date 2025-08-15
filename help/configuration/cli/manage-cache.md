---
title: Cache verwalten
description: Verwalten Sie Cache-Typen und zeigen Sie den Cache-Status über die Befehlszeile mithilfe der Commerce-CLI an
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Cache verwalten

{{file-system-owner}}

## Cache-Typen

Sie können das Cache-Management-System von Adobe Commerce verwenden, um die Leistung Ihrer Site zu verbessern. In diesem Abschnitt wird erläutert, wie Systemadministratoren oder Entwickler mit Zugriff auf den Commerce-Anwendungsserver Caches über die Befehlszeile verwalten können.

>[!NOTE]
>
>
>Commerce-Site-Administratoren können den Cache über das Tool Cache Management System von der Admin-Instanz aus verwalten. Siehe [Cache-Verwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) im _Admin-_.


## Cache-Status anzeigen

Zeigen Sie in der Befehlszeile des Commerce-Anwendungsservers den Cache-Status mithilfe des `cache:status` Commerce-CLI-Befehls an.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Es folgt ein Beispiel:

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
>Eine ausführliche Beschreibung der von Adobe Commerce unterstützten Standard-Cache-Typen finden Sie unter [Caches](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) im _Admin-_.


## Cache-Typen aktivieren oder deaktivieren

Mit diesem Befehl können Sie alle oder nur die angegebenen Cache-Typen aktivieren oder deaktivieren. Das Deaktivieren von Cache-Typen ist während der Entwicklung nützlich, da Sie die Ergebnisse Ihrer Änderungen sehen, ohne den Cache leeren zu müssen. Die Deaktivierung von Cache-Typen hat jedoch negative Auswirkungen auf die Leistung.

>[!INFO]
>
>Ab Version 2.2 können Sie Cache-Typen nur über die Befehlszeile aktivieren oder deaktivieren, während Sie Commerce im Produktionsmodus ausführen. Wenn Sie Commerce im Entwicklermodus ausführen, können Sie Cache-Typen über die Befehlszeile oder manuell aktivieren oder deaktivieren. Zuvor müssen Sie `<magento_root>/app/etc/env.php` manuell vom [Dateisystembesitzer“ überschreibbar ](../../installation/prerequisites/file-system/overview.md).

Sie können Cache-Typen (auch als __ oder _Aktualisieren_ bezeichnet) entweder über die Befehlszeile oder über Admin bereinigen.

Befehlsoptionen:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Wenn Sie `[type]` auslassen, werden alle Cache-Typen gleichzeitig aktiviert oder deaktiviert. Die `type` Option ist eine durch Leerzeichen getrennte Liste von Cache-Typen.

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
>Ab Version 2.3.4 speichert Commerce alle EAV-Systemattribute im Zwischenspeicher, sobald sie abgerufen werden. Das Caching von EAV-Attributen auf diese Weise verbessert die Leistung, da es die Anzahl der INSERT/SELECT-Anfragen an die DB verringert. Es erhöht jedoch auch die Cache-Netzwerkgröße. Entwickler können benutzerdefinierte EAV-Attribute zwischenspeichern, indem sie den `bin/magento config:set dev/caching/cache_user_defined_attributes 1`-Befehl ausführen. Im Entwicklermodus können Sie dies auch von der Admin aus tun[ ](../bootstrap/application-modes.md) indem Sie **Stores** > Einstellungen **Konfiguration** > **Erweitert** > **Entwickler** > **Caching-Einstellungen** > **Cache User Defined Attributes** auf **Ja** einstellen.

## Cache-Typen bereinigen und leeren

>[!NOTE]
>
>Der Cache für mehrere Seiten kann gleichzeitig und automatisch ungültig gemacht werden **_ohne dass_** Entitäten bearbeitet werden müssen. Dies ist beispielsweise der Fall, wenn ein Produkt im Katalog einer Kategorie zugewiesen ist oder wenn eine [!UICONTROL related product rule] geändert wird.

Um veraltete Elemente aus dem Cache zu entfernen, können Sie _Cache-Typen_ bereinigen _oder_:

- Das Bereinigen eines Cache-Typs löscht nur alle Elemente aus aktivierten Commerce-Cache-Typen. Mit anderen Worten: Diese Option hat keine Auswirkungen auf andere Prozesse oder Anwendungen, da sie nur den von Commerce verwendeten Cache bereinigt.

  Deaktivierte Cache-Typen werden nicht bereinigt.

  >[!TIP]
  >
  >Bereinigen Sie den Cache immer, nachdem Sie Versionen von Adobe Commerce aktualisiert haben, von Magento Open Source auf Adobe Commerce aktualisiert haben oder B2B für Adobe Commerce oder ein beliebiges Modul installiert haben.

- Durch das Leeren eines Cache-Typs wird der Cache-Speicher bereinigt, was sich auf andere Prozesse und Anwendungen auswirken kann, die denselben Speicher verwenden.

Leeren Sie Cache-Typen, wenn Sie bereits versucht haben, den Cache zu bereinigen, und weiterhin Probleme auftreten, die Sie nicht isolieren können.

Befehlsverwendung:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Dabei ist `[type]` eine durch Leerzeichen getrennte Liste von Cache-Typen. Wenn Sie `[type]` auslassen, werden alle Cache-Typen gleichzeitig bereinigt oder geleert. Um beispielsweise alle Cache-Typen zu leeren, geben Sie ein.

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
>Sie können Cache-Typen auch in Admin bereinigen und leeren. Navigieren Sie **System** > **Tools** > **Cache-Verwaltung**. **Leeren des Cache** entspricht `bin/magento cache:flush`. **Leeren des Magento** Cache entspricht `bin/magento cache:clean`.
