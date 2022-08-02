---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Aktualisieren der freigegebenen Konfiguration

**So aktualisieren Sie die Konfiguration**:

1. Melden Sie sich bei Ihrem Entwicklungssystem als Eigentümer des Dateisystems an oder wechseln Sie zu ihm.

1. Wechseln Sie zum Stammverzeichnis der Anwendung und führen Sie den Befehl dump aus.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Wenn beispielsweise Commerce in installiert ist `/var/www/html/magento2`eingeben:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Vergewissern Sie sich, dass `app/etc/config.php` aktualisiert wurde.

   ```bash
   git status
   ```

   Beispielantwort:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Do _not_ Änderungen an `generated`, `pub/media`oder `pub/static` Ordner zur Quell-Code-Verwaltung. Sie generieren diese Dateien auf Ihrem Build-System. Das Entwicklungssystem verfügt wahrscheinlich über Code, Designs usw., die nicht für die Verwendung im Produktionssystem bereit sind.

1. Überprüfen Sie Ihre Änderungen in `app/etc/config.php` nur zur Quell-Code-Verwaltung.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
