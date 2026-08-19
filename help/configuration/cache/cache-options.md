---
title: Cache-Backend-Optionen und Speicherreferenz
description: Erfahren Sie mehr über die Cache-Backend-Optionen in Adobe Commerce, einschließlich Dateisystem, Redis, Valkey und Datenbankspeicher. Entdecken Sie alte und moderne Ansätze.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 761
ht-degree: 0%

---

# Cache-Backend-Optionen und Speicherreferenz

>[!NOTE]
>
>Auf dieser Seite wird die Konfiguration der On-Premise-`app/etc/env.php` dokumentiert.
>
>Bei [!DNL Adobe Commerce on Cloud] Projekten generiert das `ece-tools`-Paket die resultierende `app/etc/env.php` während der Bereitstellung basierend auf der Konfiguration der Bereitstellungsvariablen in `.magento.env.yaml`. Die `env.php`-Datei wird nicht bearbeitet.  Siehe [Best Practices für die Konfiguration von Valkey und Redis Service](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) und [Variablen bereitstellen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy).

Die Commerce-Anwendung verwendet ein Cache-Frontend und ein Backend auf niedriger Ebene, um Zugriff auf den Cache-Speicher zu gewähren. Commerce unterstützt verschiedene Caching-Backends und -Strategien, die jeweils für verschiedene Anwendungsfälle geeignet sind. Auf dieser Seite werden die verfügbaren Backends und deren Unterschiede beschrieben.

>[!NOTE]
>
>[Varnish](config-varnish-install.md) behandelt das Caching ganzer Seiten auf HTTP-Ebene für lokale Bereitstellungen. Der [Fastly-Service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) übernimmt dies für Cloud-Bereitstellungen. Keine der Lösungen verwendet das Cache-Backend auf niedriger Ebene.

## Backend-Cache-Optionen

In der folgenden Tabelle sind die verfügbaren Backend-Caches zusammengefasst:

| Backend | Beschreibung | Konfigurationshandbuch |
| ------- | ----------- | ------------------- |
| Dateisystem | Standard. Speichert Cache-Daten in Dateien unter `var/cache/`. Keine Konfiguration erforderlich. | Nicht zutreffend |
| Redis | In-Memory-Datenspeicher für leistungsstarkes Caching. | [Redis für Standard-Cache verwenden](redis-pg-cache.md) |
| Tal | Open-Source, Redis-kompatible Alternative. | [Valkey für Standardcache verwenden](valkey-pg-cache.md) |
| Datenbank | Benutzerdefinierte Cache-Engine, die von einer Datenbank unterstützt wird | [Erstellen benutzerdefinierter Cache-Engines](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} (Dokumentation zu Adobe Developer) |

>[!IMPORTANT]
>
>Redis-Cache wird für Adobe Commerce 2.4.9 oder Patch-Versionen nach 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 und 2.4.8-p4 nicht unterstützt. Wenn Sie ein Upgrade auf eine dieser Versionen durchführen, konfigurieren Sie Valley und aktualisieren Sie die Cache-Konfiguration, um es zu verwenden. [!DNL Adobe Commerce on-premises] finden Sie unter [Einrichten von Valkey](config-valkey.md).

## Cache-Backend- und L2-Implementierungen {#implementation-approaches}

Commerce unterstützt direkte Cache-Backends und L2-Caching. Ein direktes Backend wählt Cache-Speicher aus. L2-Caching fügt eine lokale Cache-Ebene vor dem Remote-Speicher hinzu.

### Direkte Cache-Backends

Die folgenden PHP-Beispiele konfigurieren das Cache-Backend in `<Commerce-install-dir>/app/etc/env.php`. Sie ermöglichen kein L2-Caching.

| Commerce-Version | Implementierung | Backend | Konfigurationswert |
| ---------------- | -------------- | ------- | ------------------- |
| 2.4.8 und früher, sofern unterstützt | Veraltet | Dateisystem (Standard) | Keine Konfiguration erforderlich |
| 2.4.8 und früher, sofern unterstützt | Veraltet | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 und früher, sofern unterstützt | Veraltet | Tal | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 und höher sowie unterstützte Backports | Moderner Symfony-Cache | Dateisystem (Standard) | `file` |
| 2.4.9 und höher sowie unterstützte Backports | Moderner Symfony-Cache | Tal | `valkey` |

Informationen zur Unterstützung auf Patch-Ebene finden Sie unter [Systemanforderungen](../../installation/system-requirements.md).

>[!NOTE]
>
>Die moderne Implementierung akzeptiert den Namen des `redis`, aber Redis ist kein offiziell unterstützter Cache-Service, für den Valkey erforderlich ist. Verwenden Sie stattdessen `valkey` .

#### Legacy-Beispiele für Zend-basierte Backends

Bei On-Premise-Bereitstellungen konfigurieren die folgenden Beispiele direkte Cache-Backends in `<Commerce-install-dir>/app/etc/env.php`. Sie ermöglichen kein L2-Caching. Verwenden Sie diese Beispiele nicht für [!DNL Adobe Commerce on Cloud] Bereitstellungen, die das `ece-tools`-Paket verwenden, um die resultierende `app/etc/env.php` während der Bereitstellung zu generieren.

>[!BEGINTABS]

>[!TAB Legacy-Backend-Redis]

Verwenden Sie den vollständigen Redis-Klassennamen nur für Versionen, in denen Redis unterstützt wird:

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Legacy Backend Valkey]

Verwenden Sie den vollständigen Valkey-Klassennamen für Versionen, die das alte Valkey-Backend unterstützen:

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

#### Modernes Symfony-Cache-Backend

Das standardmäßige direkte Backend ist das Dateisystem. Um Valkey mit der modernen Implementierung zu verwenden, verwenden Sie den vereinfachten `valkey`-Backend-Typ.

Das folgende Konfigurationsbeispiel gilt für Adobe Commerce 2.4.9 und höher und unterstützt Backports, bei denen Valkey unterstützt wird, wenn das direkte Standard-Caching mit der modernen Symfony Cache-Implementierung konfiguriert wird.

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TIP]
>
>Die Symfony-Cache-Implementierung unterstützt optionale Leistungsfunktionen wie binäre Serialisierung, Komprimierung, LUA-Skripte und persistente Verbindungen. Weitere Informationen finden Sie unter [Konfigurieren von Valkey für Standard- und Seitencache](valkey-pg-cache.md).

### L2-Cache-Implementierungen

L2-Caching (auf zwei Ebenen) fügt eine lokale Cache-Ebene auf jedem Web-Knoten vor dem gemeinsam genutzten Remote-Cache-Speicher hinzu, wodurch der Netzwerk-Traffic zwischen Commerce und dem Remote-Cache reduziert wird.

| Commerce-Version | L2-Implementierung | Remote-Backend |
| ---------------- | ------------------ | --------------- |
| Vor 2.4.9, sofern unterstützt | RemoteSynchronizedCache | Redis oder Valkey, je nach Commerce-Version und Support-Matrix auf Patch-Ebene |
| 2.4.9 und höher | symfony_l2 | Tal |

Informationen zur lokalen Konfiguration finden Sie unter [L2-Cache-Konfiguration](level-two-cache.md).

Konfigurieren Sie für Cloud-Projekte das L2-Caching mithilfe der Bereitstellungsvariablen, die unter &quot;[&#x200B; bereitstellen“ beschrieben &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}.

#### L2-Cache-Konfiguration

- **[!DNL Adobe Commerce on-premises]** Informationen zur Konfiguration finden Sie unter [L2-Cache-Konfiguration](level-two-cache.md).

- Konfigurieren Sie **[!DNL Adobe Commerce on Cloud]** die L2-Zwischenspeicherung über die entsprechende Bereitstellungsvariable, anstatt `app/etc/env.php` direkt zu bearbeiten. Siehe [Variablen bereitstellen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"} in der Dokumentation zu _Adobe Commerce_ Cloud.
