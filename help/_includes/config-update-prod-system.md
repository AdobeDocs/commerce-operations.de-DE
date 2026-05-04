---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Aktualisieren des Produktionssystems

**So aktualisieren Sie das Produktionssystem**:

1. Melden Sie sich beim Produktionssystem als Eigentümer des Dateisystems an.
1. Wechseln Sie zum Anwendungsstamm und aktivieren Sie den Wartungsmodus.

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   Weitere Optionen, z. B. die Möglichkeit, eine IP-Adressen-Zulassungsliste festzulegen, finden Sie unter [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Beenden Sie alle ausgeführten Warteschlangenarbeitnehmer, indem Sie `cron_run` wie folgt auf `false` in `app/etc/env.php` setzen:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Aktualisieren Sie die Konfiguration.

   ```shell
   bin/magento app:config:import
   ```

1. `kill` Sie abschließend alle aktiven Verbraucherprozesse.

   ```shell
   kill <PID>
   ```

   Dabei ist `PID` die Prozess-ID, die abgebrochen werden soll, z. B.:

   ```shell
   kill 1234
   ```

1. Code aus der Quellcodeverwaltung abrufen.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Aktualisieren Sie die Konfiguration.

   ```shell
   bin/magento app:config:import
   ```

1. Reinigen Sie den Cache.

   ```shell
   bin/magento cache:clean
   ```

1. Wartungsmodus beenden

   ```shell
   bin/magento maintenance:disable
   ```
