---
title: Aktivität "Logdatenbank"
description: Konfigurieren Sie Commerce, um die Datenbankaktivität über die Logger-Oberfläche zu protokollieren.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Aktivität &quot;Logdatenbank&quot;

Das folgende Beispiel zeigt, wie die Aktivität Datenbank mithilfe der [`Magento\Framework\DB\LoggerInterface`][interface], der über zwei Implementierungen verfügt:

- Protokolliert nichts (Standard): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Protokolle zum `var/log` directory: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Sie können die Commerce-CLI für [Datenbankprotokollierung aktivieren und deaktivieren](../cli/enable-logging.md#database-logging).

So ändern Sie die Standardkonfiguration von `\Magento\Framework\DB\Logger\LoggerProxy`, bearbeiten Sie Ihre `app/etc/di.xml`.

Ändern Sie zunächst die Standardwerte von `loggerAlias` und `logCallStack` Argumente an:

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

Geben Sie anschließend den Dateipfad für `Magento\Framework\DB\Logger\File`:

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

Bereinigen Sie den Cache mit:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
