---
title: Geteilte Datenbank wiederherstellen
description: Kehren Sie von einer veralteten Implementierung der geteilten Datenbank zu einer einzigen Datenbankimplementierung zurück.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Aus Aufspaltungsdatenbank zurücksetzen

{{ee-only}}

Für Adobe Commerce-Kunden, die [Aufspaltungsdatenbank](multi-master.md), wird im folgenden Thema beschrieben, wie Sie eine einzelne Datenbank wiederherstellen oder wiederherstellen können. Es wird empfohlen, dass Adobe Commerce-Händler, die derzeit die Split Database verwenden, ein Upgrade auf 2.4.2 planen und diese Schritte sowie unsere [Mitteilung](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) zur geplanten Einstellung der Aufspaltung der Datenbank.

Das Zurücksetzen von einer geteilten Datenbank auf eine einzelne Datenbank umfasst die Erstellung von Backups der `magento_quote` und `magento_sales` Datenbanken vor dem Laden in eine einzige `magento_main` Datenbank.

In diesem Beispiel melden wir uns bei allen drei Datenbanken an, die auf demselben Host installiert sind (`magento2-mysql`) als &quot;root&quot;-Benutzer. Sie müssen diese Werte durch die entsprechenden Werte für Ihre Datenbanken ersetzen.

1. Erstellen Sie eine Sicherungskopie des `magento_quote` Datenbank:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Erstellen Sie eine Sicherungskopie des `magento_sales` Datenbank:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Laden Sie die `magento_quote` in die Datenbank `magento_main` Datenbank:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Laden Sie die `magento_sales` in die Datenbank `magento_main` Datenbank:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Legen Sie die `magento_sales` Datenbank:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Legen Sie die `magento_quote` Datenbank:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Entfernen Sie die Bereitstellungskonfiguration für `checkout` und `sales` im `connections` und `resources` der `env.php` -Datei.
1. Fremdschlüssel wiederherstellen:

   ```bash
   bin/magento setup:upgrade
   ```

## Überprüfen der Arbeit

Um sicherzustellen, dass Ihre Implementierung der einzelnen Datenbank ordnungsgemäß funktioniert, führen Sie die folgenden Aufgaben aus und vergewissern Sie sich, dass Daten zum `magento_main` Datenbanktabellen mithilfe eines Datenbank-Tools wie [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Überprüfen Sie, ob Fremdschlüssel wiederhergestellt wurden. Beispiel: die `QUOTE_STORE_ID_STORE_STORE_ID` Schlüssel in der `quote` Datenbanktabelle.
1. Stellen Sie sicher, dass Kunden Bestellungen über die Storefront tätigen können.
1. Stellen Sie sicher, dass die vor der Wiederherstellung der geteilten Datenbank erstellten Bestellungen in der Admin-Konsole verfügbar sind.
