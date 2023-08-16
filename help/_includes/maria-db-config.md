---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%

---
# MariaDB-Konfigurationseinstellungen

Die Neuindizierung auf MariaDB 10.4 und 10.6 nimmt im Vergleich zu früheren MariaDB- oder MySQL-Versionen mehr Zeit in Anspruch. Um die Neuindizierung zu beschleunigen, empfehlen wir, diese MariaDB-Konfigurationsparameter festzulegen:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Wenn die Leistung nach der Aktualisierung auf MariaDB 10.6 nicht mit der Indexierung in Zusammenhang steht, sollten Sie die Option [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) -Einstellung. Beispiel, `--query-cache-type=ON`.

Zusätzlich zu diesen Empfehlungen sollten Sie sich an Ihren Datenbankadministrator wenden, um die folgenden Parameter zu konfigurieren:

>[!NOTE]
>
>Diese Einstellungen sind nur für lokale Bereitstellungen verfügbar. Kunden von Adobe Commerce in der Cloud-Infrastruktur haben keinen Zugriff auf diese Einstellungen.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
