---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
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

   Wenn beispielsweise Commerce in `/var/www/html/magento2` installiert ist, geben Sie Folgendes ein:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Bestätigen Sie, dass `app/etc/config.php` aktualisiert wurde.

   ```bash
   git status
   ```

   Beispielantwort:

   ```
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Übermitteln Sie _nicht_ Änderungen an den Verzeichnissen `generated`, `pub/media` oder `pub/static` an die Quell-Code-Verwaltung. Sie generieren diese Dateien auf Ihrem Build-System. Das Entwicklungssystem verfügt wahrscheinlich über Code, Designs usw., die nicht für die Verwendung im Produktionssystem bereit sind.

1. Checken Sie Ihre Änderungen an `app/etc/config.php` nur für die Quell-Code-Verwaltung ein.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
