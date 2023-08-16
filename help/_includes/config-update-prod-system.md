---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Produktionssystem aktualisieren

**So aktualisieren Sie das Produktionssystem**:

1. Melden Sie sich beim Produktionssystem als Eigentümer des Dateisystems an.
1. Wechseln Sie zum Stammverzeichnis der Anwendung und aktivieren Sie den Wartungsmodus.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Weitere Optionen, wie die Möglichkeit, eine IP-Adressen-Whitelist festzulegen, finden Sie unter [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Beenden Sie alle laufenden Warteschlangen-Sekundäre, indem Sie `cron_run` nach `false` in `app/etc/env.php` wie folgt:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Aktualisieren Sie die Konfiguration.

   ```bash
   bin/magento app:config:import
   ```

1. Schließlich `kill` alle aktiven Verbraucherprozesse.

   ```bash
   kill <PID>
   ```

   Wo `PID` die Prozess-ID, die beendet werden soll, beispielsweise:

   ```bash
   kill 1234
   ```

1. Rufen Sie Code aus der Quell-Code-Verwaltung ab.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Aktualisieren Sie die Konfiguration.

   ```bash
   bin/magento app:config:import
   ```

1. Bereinigen Sie den Cache.

   ```bash
   bin/magento cache:clean
   ```

1. Wartungsmodus beenden.

   ```bash
   bin/magento maintenance:disable
   ```
