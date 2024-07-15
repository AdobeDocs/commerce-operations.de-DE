---
title: Geteilte Datenbank überprüfen
description: Erfahren Sie, wie Sie überprüfen können, ob eine Commerce-Aufspaltungsdatenbankkonfiguration ordnungsgemäß funktioniert.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Geteilte Datenbank überprüfen

{{ee-only}}

{{deprecate-split-db}}

Nach der Konfiguration werden die Master-Datenbanken wie folgt konfiguriert:

- Commerce-Hauptdatenbank: 369 Tabellen
- Commerce-Anführungsdatenbank: 11 Tabellen
- Commerce-Verkaufsdatenbank: 55 Tabellen

Um sicherzustellen, dass Ihre geteilten Datenbanken ordnungsgemäß funktionieren, führen Sie die folgenden Aufgaben aus und stellen Sie mithilfe eines Datenbank-Tools wie [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin) sicher, dass Daten zu den Datenbanktabellen hinzugefügt werden:

| Was zu überprüfen ist | Überprüfen |
| -------------- | ------------- |
| Angebotsdatenbank funktioniert | Fügen Sie Artikel zu einem Warenkorb hinzu. Vergewissern Sie sich, dass den Tabellen `quote`, `quote_address` und `quote_item` Ihrer Anführungsdatenbank Zeilen hinzugefügt wurden. |
| Verkaufsdatenbank funktioniert | Führen Sie eine Bestellung aus (jede Zahlungsmethode, einschließlich Scheck-/Geldbestellung). Vergewissern Sie sich, dass den Tabellen `sales_order_address`, `sales_order_item` und `sales_order_payment` Ihrer Verkaufsdatenbank Zeilen hinzugefügt wurden. |

>[!WARNING]
>
>Sie müssen die beiden zusätzlichen Datenbankinstanzen manuell sichern. Commerce sichert nur die Hauptdatenbankinstanz. Die Optionen [`magento setup:backup --db`](../../installation/tutorials/backup.md) und &quot;Admin&quot;sichern die zusätzlichen Tabellen nicht.
