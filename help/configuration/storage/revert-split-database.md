---
title: Geteilte Datenbank wiederherstellen
description: Kehren Sie von einer veralteten Implementierung der geteilten Datenbank zu einer einzigen Datenbankimplementierung zurück.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Aus Aufspaltungsdatenbank zurücksetzen

{{ee-only}}

Für Adobe Commerce-Kunden, die die [Aufspaltungsdatenbank](multi-master.md) implementiert haben, wird im folgenden Thema beschrieben, wie Sie eine einzige Datenbank wiederherstellen oder wiederherstellen können. Es wird empfohlen, dass Adobe Commerce-Händler, die derzeit die Split Database verwenden, ein Upgrade auf 2.4.2 planen und diese Schritte später lesen, sowie unsere [Mitteilung](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) zur geplanten Einstellung der Aufspaltung der Datenbank.

Das Zurücksetzen von einer geteilten Datenbank auf eine einzelne Datenbank umfasst die Erstellung von Sicherungen der `magento_quote` - und `magento_sales` -Datenbanken, bevor sie in die einzelne `magento_main` -Datenbank geladen werden.

In diesem Beispiel melden wir uns bei allen drei Datenbanken an, die auf demselben Host (`magento2-mysql`) wie der Benutzer &quot;root&quot;installiert sind. Sie müssen diese Werte durch die entsprechenden Werte für Ihre Datenbanken ersetzen.

1. Erstellen Sie eine Sicherung der `magento_quote` -Datenbank:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Erstellen Sie eine Sicherung der `magento_sales` -Datenbank:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Laden Sie die `magento_quote` -Datenbank in die `magento_main` -Datenbank:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Laden Sie die `magento_sales` -Datenbank in die `magento_main` -Datenbank:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Legen Sie die `magento_sales` -Datenbank ab:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Legen Sie die `magento_quote` -Datenbank ab:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Entfernen Sie die Bereitstellungskonfiguration für `checkout` und `sales` in den Abschnitten `connections` und `resources` der Datei `env.php`.
1. Fremdschlüssel wiederherstellen:

   ```bash
   bin/magento setup:upgrade
   ```

## Überprüfen der Arbeit

Um sicherzustellen, dass Ihre einzelne Datenbankimplementierung ordnungsgemäß funktioniert, führen Sie die folgenden Aufgaben aus und vergewissern Sie sich mithilfe eines Datenbank-Tools wie [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin), dass den `magento_main` -Datenbanktabellen Daten hinzugefügt werden:

1. Überprüfen Sie, ob Fremdschlüssel wiederhergestellt wurden. Beispielsweise den Schlüssel `QUOTE_STORE_ID_STORE_STORE_ID` in der Datenbanktabelle `quote`.
1. Stellen Sie sicher, dass Kunden Bestellungen über die Storefront tätigen können.
1. Stellen Sie sicher, dass die vor der Wiederherstellung der geteilten Datenbank erstellten Bestellungen in der Admin-Konsole verfügbar sind.
