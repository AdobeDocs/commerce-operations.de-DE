---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Build-System aktualisieren

**So aktualisieren Sie das Build-System**:

1. Melden Sie sich beim Build-System als Eigentümer des Dateisystems an.
1. Wechseln Sie in das Stammverzeichnis der Anwendung.

   ```shell
   cd <Magento root dir>
   ```

1. Abrufen der Änderungen an `app/etc/config.php` aus der Quell-Code-Verwaltung.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Kompilieren Sie Code.

   ```shell
   bin/magento setup:di:compile
   ```

1. Generieren Sie nach dem Kompilieren des Codes statische Ansichtsdateien.

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. Überprüfen Sie die Änderungen in der Quell-Code-Verwaltung.

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
