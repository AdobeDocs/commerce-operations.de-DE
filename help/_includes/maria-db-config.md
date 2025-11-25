---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# MariaDB-Konfigurationseinstellungen

Die Neuindizierung auf MariaDB 10.4 und 10.6 dauert im Vergleich zu früheren MariaDB- oder MySQL-Versionen länger. Um die Neuindizierung zu beschleunigen, empfehlen wir die folgenden MariaDB-Konfigurationsparameter festzulegen:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

Wenn nach dem Upgrade auf MariaDB 10.6 eine Leistungsbeeinträchtigung auftritt, die nicht mit einer Indizierung in Zusammenhang steht, sollten Sie die [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) aktivieren. Beispiel: `--query-cache-type=ON`.

Vor einem Upgrade von Adobe Commerce in Cloud-Infrastrukturprojekten müssen Sie möglicherweise auch MariaDB aktualisieren ([siehe Best Practices für MariaDB-Upgrades](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)).

Beispiel:

* Adobe Commerce 2.4.6 mit MariaDB-Version 10.5.1 oder höher
* Adobe Commerce 2.3.5 mit MariaDB Version 10.3 oder früher

Zusätzlich zu diesen Empfehlungen sollten Sie sich mit Ihrem Datenbankadministrator über die Konfiguration der folgenden Parameter beraten:

>[!NOTE]
>
>Diese Einstellungen sind nur für lokale Bereitstellungen verfügbar. Kunden von Adobe Commerce in Cloud-Infrastrukturen haben keinen Zugriff auf diese Einstellungen.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
