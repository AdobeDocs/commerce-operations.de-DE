---
title: Geteilte Datenbank überprüfen
description: Erfahren Sie, wie Sie überprüfen können, ob eine Commerce-geteilte Datenbankkonfiguration ordnungsgemäß funktioniert.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Geteilte Datenbank überprüfen

{#ee-only}

{{deprecate-split-db}}

Nach der Konfiguration werden die Übergeordneten Datenbanken wie folgt konfiguriert:

- Wichtigste Commerce-Datenbank: 369 Tabellen
- Handel [Anführungszeichen](https://glossary.magento.com/quote) Datenbank: 11 Tabellen
- Commerce-Verkaufsdatenbank: 55 Tabellen

Um sicherzustellen, dass Ihre geteilten Datenbanken ordnungsgemäß funktionieren, führen Sie die folgenden Aufgaben aus und überprüfen Sie mithilfe eines Datenbank-Tools wie [phpmyadmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

| Was zu überprüfen ist | Überprüfen |
| -------------- | ------------- |
| Angebotsdatenbank funktioniert | Fügen Sie Artikel zu einem Warenkorb hinzu. Überprüfen Sie, ob der Datenbank Ihrer Zitate Zeilen hinzugefügt wurden. `quote`, `quote_address`und `quote_item` -Tabellen. |
| Verkaufsdatenbank funktioniert | Führen Sie eine Bestellung aus (jede Zahlungsmethode, einschließlich Scheck-/Geldbestellung). Stellen Sie sicher, dass der Datenbank Zeilen hinzugefügt wurden. `sales_order_address`, `sales_order_item`und `sales_order_payment` -Tabellen. |

>[!WARNING]
>
>Sie müssen die beiden zusätzlichen Datenbankinstanzen manuell sichern. Commerce sichert nur die Hauptdatenbankinstanz. Die [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) -Befehl und Admin-Optionen sichern die zusätzlichen Tabellen nicht.
