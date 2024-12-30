---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Build-System aktualisieren

**So aktualisieren Sie das Build-System**:

1. Melden Sie sich beim Build-System als Eigentümer des Dateisystems an.
1. Wechseln Sie in das Stammverzeichnis der Anwendung.

   ```bash
   cd <Magento root dir>
   ```

1. Abrufen der Änderungen an `app/etc/config.php` aus der Quell-Code-Verwaltung.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Kompilieren Sie Code.

   ```bash
   bin/magento setup:di:compile
   ```

1. Generieren Sie nach dem Kompilieren des Codes statische Ansichtsdateien.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Überprüfen Sie die Änderungen in der Quell-Code-Verwaltung.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
