---
title: Datenbankaktivität protokollieren
description: Konfigurieren Sie Commerce, um Datenbankaktivitäten mithilfe der Logger-Oberfläche zu protokollieren.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Datenbankaktivität protokollieren

Das folgende Beispiel zeigt, wie Sie Datenbankaktivitäten mit dem [`Magento\Framework\DB\LoggerInterface`][interface] protokollieren, der zwei Implementierungen aufweist:

- Keine Protokolle (Standard): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Protokolle im `var/log`: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Sie können die Commerce-CLI verwenden, um [Datenbankprotokollierung zu aktivieren und zu deaktivieren](../cli/enable-logging.md#database-logging).

Um die Standardkonfiguration von `\Magento\Framework\DB\Logger\LoggerProxy` zu ändern, bearbeiten Sie Ihre `app/etc/di.xml`.

Ändern Sie zunächst die Standardwerte der `loggerAlias` und `logCallStack` Argumente in:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

Geben Sie anschließend den Dateipfad für `Magento\Framework\DB\Logger\File` an:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Kompilieren Sie den Code schließlich mit:

```bash
bin/magento setup:di:compile
```

Und den Cache bereinigen mit:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
