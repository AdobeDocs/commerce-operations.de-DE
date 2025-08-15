---
title: Split-Datenbank zurücksetzen
description: Kehren Sie von einer veralteten Split-Datenbankimplementierung zu einer einzelnen Datenbankimplementierung zurück.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Aus Split-Datenbank zurücksetzen

{{ee-only}}

Adobe Commerce-Kunden, die [Split-Datenbank](multi-master.md) implementiert haben, wird im folgenden Thema beschrieben, wie Sie eine Wiederherstellung oder Migration zu einer einzelnen Datenbank durchführen. Wir empfehlen Adobe Commerce-Händlern, die derzeit die Split-Datenbank verwenden und ein Upgrade auf 2.4.2 planen. Überprüfen Sie diese Schritte sowie unsere [Ankündigung](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) zur geplanten Einstellung der Split-Datenbank.

Bei der Wiederherstellung von einer geteilten Datenbank auf eine einzelne Datenbank werden Sicherungen der `magento_quote`- und `magento_sales`-Datenbanken erstellt, bevor sie in die einzelne `magento_main`-Datenbank geladen werden.

In diesem Beispiel melden wir uns bei allen drei Datenbanken an, die auf demselben Host (`magento2-mysql`) installiert sind wie der „Root“-Benutzer. Sie müssen diese Werte durch die entsprechenden Werte für Ihre Datenbanken ersetzen.

1. Erstellen Sie eine Sicherung der `magento_quote`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Erstellen Sie eine Sicherung der `magento_sales`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Laden Sie die `magento_quote` Datenbank in die `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Laden Sie die `magento_sales` Datenbank in die `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. `magento_sales` ablegen:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. `magento_quote` ablegen:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Entfernen Sie die Bereitstellungskonfiguration für `checkout` und `sales` in den Abschnitten `connections` und `resources` der `env.php`.
1. Foreign keys:

   ```bash
   bin/magento setup:upgrade
   ```

## Überprüfen der Arbeit

Um sicherzustellen, dass Ihre Einzeldatenbankimplementierung ordnungsgemäß funktioniert, führen Sie die folgenden Aufgaben aus und überprüfen Sie mithilfe eines Datenbank-Tools wie „phpMyAdmin`magento_main`, dass den [ Datenbanktabellen Daten hinzugefügt ](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Stellen Sie sicher, dass Fremdschlüssel wiederhergestellt wurden. Beispielsweise den `QUOTE_STORE_ID_STORE_STORE_ID` Schlüssel in der `quote` Datenbanktabelle.
1. Überprüfen Sie, ob Kunden Bestellungen in der Storefront aufgeben können.
1. Überprüfen Sie, ob die erstellten Bestellungen, bevor die aufgeteilte Datenbank auf eine einzelne Datenbank zurückgesetzt wird, in der Admin Console verfügbar sind.
