---
title: Verwalten des Cache
description: Verwalten Sie Cachetypen und zeigen Sie den Cache-Status an.
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 604e2a1461e2cbbcc498dfed6018ba640efe8cde
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---

# Verwalten des Cache

{{file-system-owner}}

## Cachetypen

Commerce 2 verfügt über die folgenden Cache-Typen:

| Cache type &quot;friendly&quot; name | Codename des Cachetyps | Beschreibung |
|--- |--- |--- |
| Konfiguration | config | Commerce erfasst die Konfiguration aus allen Modulen, führt sie zusammen und speichert das zusammengeführte Ergebnis im Cache. Dieser Cache enthält auch speicherspezifische Einstellungen, die im Dateisystem und in der Datenbank gespeichert sind. Löschen oder leeren Sie diesen Cache-Typ, nachdem Sie die Konfigurationsdateien geändert haben. |
| Layout | layout | Kompilierte Seitenlayouts (d. h. die Layoutkomponenten aus allen Komponenten). Löschen oder leeren Sie diesen Cache-Typ, nachdem Sie die Layout-Dateien geändert haben. |
| Blockausgabe HTML | block_html | HTML von Seitenfragmenten pro Block. Entfernen oder leeren Sie diesen Cache-Typ, nachdem Sie die Ansichtsebene geändert haben. |
| Sammlungsdaten | Sammlungen | Ergebnisse von Datenbankabfragen. Bei Bedarf bereinigt Commerce diesen Cache automatisch, aber Drittanbieter können alle Daten in jedes Segment des Caches einfügen. Entfernen oder leeren Sie diesen Cache-Typ, wenn Ihr benutzerdefiniertes Modul Logik verwendet, die zu Cache-Einträgen führt, die Commerce nicht bereinigen kann. |
| DDL | db_ddl | Datenbankschema. Bei Bedarf bereinigt Commerce diesen Cache automatisch, aber Drittanbieter können alle Daten in jedes Segment des Caches einfügen. Löschen oder leeren Sie diesen Cache-Typ, nachdem Sie benutzerdefinierte Änderungen am Datenbankschema vorgenommen haben. (Mit anderen Worten, Aktualisierungen, die Commerce nicht selbst vornimmt.) Eine Möglichkeit, das Datenbankschema automatisch zu aktualisieren, ist die Verwendung der `magento setup:db-schema:upgrade` Befehl. |
| Kompilierte Konfiguration | compiled_config | Kompilierungskonfiguration |
| Entitätsattributwert (EAV) | eav | Metadaten im Zusammenhang mit EAV-Attributen (z. B. Store-Bezeichnungen, Links zum zugehörigen PHP-Code, Attribut-Rendering, Sucheinstellungen usw.). Normalerweise sollten Sie diesen Cache-Typ nicht bereinigen oder leeren müssen. |
| Seiten-Cache | full_page | Generierte HTML-Seiten. Bei Bedarf bereinigt Commerce diesen Cache automatisch, aber Drittanbieter können alle Daten in jedes Segment des Caches einfügen. Entfernen oder leeren Sie diesen Cache-Typ, nachdem Sie die Codeebene geändert haben, die sich auf die HTML-Ausgabe auswirkt. Es wird empfohlen, diesen Cache aktiviert zu halten, da das Zwischenspeichern von HTML die Leistung erheblich verbessert. |
| Reflektion | Reflexion | Entfernt eine Abhängigkeit zwischen dem Webapi-Modul und dem Kundenmodul. |
| Übersetzungen | translate | Nach dem Zusammenführen von Übersetzungen aus allen Modulen wird der Fusion-Cache bereinigt. |
| Integrationskonfiguration | config_integration | Kompilierte Integrationen. Löschen oder leeren Sie diesen Cache, nachdem Sie Integrationen geändert oder hinzugefügt haben. |
| Integration API-Konfiguration | config_integration_api | Konfiguration der kompilierten Integrations-APIs der Store-Integrationen. |
| Konfiguration von Webdiensten | config_webservice | Zwischenspeichern der Web-API-Struktur. |
| Kundenbenachrichtigung | customer_notification | Vorübergehende Benachrichtigungen, die in der Benutzeroberfläche angezeigt werden. |
| Admin UI SDK-Cache | admin_ui_sdk | Caches Admin-Anpassungen, die mit der [Adobe Commerce Admin UI SDK](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/). |
| Webhooks-Antwort-Cache | webhooks_response | Zwischenspeichert Antworten auf [Webhook-Anforderungen](https://developer.adobe.com/commerce/extensibility/webhooks/). |

## Cache-Status anzeigen

Um den Cache-Status anzuzeigen, geben Sie

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Ein Beispiel:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## Cache-Typen aktivieren oder deaktivieren

Mit diesem Befehl können Sie alle oder nur die angegebenen Cache-Typen aktivieren oder deaktivieren. Das Deaktivieren von Cache-Typen ist während der Entwicklung nützlich, da Sie die Ergebnisse Ihrer Änderungen sehen, ohne den Cache leeren zu müssen. Das Deaktivieren von Cache-Typen hat jedoch negative Auswirkungen auf die Leistung.

>[!INFO]
>
>Ab Version 2.2 können Sie Cache-Typen nur über die Befehlszeile aktivieren oder deaktivieren, während Sie Commerce im Produktionsmodus ausführen. Wenn Sie Commerce im Entwicklermodus ausführen, können Sie Cache-Typen über die Befehlszeile oder manuell aktivieren oder deaktivieren. Dazu müssen Sie zuvor manuell `<magento_root>/app/etc/env.php` schreibbar durch [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).

Sie können reinigen (auch als _flush_ oder _Aktualisieren_) Cache-Typen, die entweder die Befehlszeile oder den Admin verwenden.

Befehlsoptionen:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Wo weggelassen wird `[type]` aktiviert oder deaktiviert alle Cache-Typen gleichzeitig. Die `type` ist eine durch Leerzeichen getrennte Liste von Cache-Typen.

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
>Ab Version 2.3.4 speichert Commerce alle System-EAV-Attribute beim Abrufen zwischen. Das Zwischenspeichern von EAV-Attributen auf diese Weise verbessert die Leistung, da dadurch die Anzahl der Einfüge-/Auswahlanfragen an die DB verringert wird. Es erhöht jedoch auch die Größe des Cache-Netzwerks. Entwickler können benutzerdefinierte EAV-Attribute zwischenspeichern, indem sie die `bin/magento config:set dev/caching/cache_user_defined_attributes 1` Befehl. Dies kann auch vom Administrator während der [Entwicklermodus](../bootstrap/application-modes.md) durch Festlegen **Stores** > Einstellungen **Konfiguration** > **Erweitert** > **Entwickler** > **Caching-Einstellungen** > **Benutzerdefinierte Attribute zwischenspeichern** nach **Ja**.

## Cache-Typen leeren

>[!NOTE]
>
>Der Cache mehrerer Seiten kann gleichzeitig und automatisch ungültig gemacht werden **_without_** diese Entitäten bearbeiten. Wenn beispielsweise ein beliebiges Produkt im Katalog einer Kategorie zugewiesen ist oder [!UICONTROL related product rule] geändert.

Um veraltete Elemente aus dem Cache zu löschen, können Sie _clean_ oder _flush_ Cache-Typen:

- Beim Löschen eines Cache-Typs werden nur alle Elemente aus aktivierten Commerce-Cache-Typen gelöscht. Mit anderen Worten: Diese Option wirkt sich nicht auf andere Prozesse oder Anwendungen aus, da sie nur den von Commerce verwendeten Cache löscht.

  Deaktivierte Cache-Typen werden nicht bereinigt.

  >[!TIP]
  >
  >Bereinigen Sie den Cache immer, nachdem Sie die Versionen von Magento Open Source oder Adobe Commerce aktualisiert, von Magento Open Source auf Adobe Commerce aktualisiert oder B2B für Adobe Commerce oder ein beliebiges Modul installiert haben.

- Beim Löschen eines Cache-Typs wird der Cache-Speicher geleert, was sich möglicherweise auf andere Prozessanwendungen auswirkt, die denselben Speicher verwenden.

Cache-Typen leeren, wenn Sie bereits versucht haben, den Cache zu bereinigen, und weiterhin Probleme auftreten, die Sie nicht isolieren können.

Befehlsverwendung:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Wo `[type]` ist eine durch Leerzeichen getrennte Liste von Cache-Typen. Auslassen `[type]` löscht oder löscht alle Cache-Typen gleichzeitig. Um beispielsweise alle Cache-Typen zu leeren, geben Sie

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
   config_webservice
   translate
```

>[!TIP]
>
>Sie können Cache-Typen auch in Admin löschen und leeren. Navigieren Sie zu **System** > **Instrumente** > **Cacheverwaltung**. **Cache-Speicher leeren** entspricht `bin/magento cache:flush`. **Magento-Cache leeren** entspricht `bin/magento cache:clean`.
