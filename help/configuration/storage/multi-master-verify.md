---
title: Geteilte Datenbank überprüfen
description: Erfahren Sie, wie Sie überprüfen können, ob eine Commerce Split-Datenbankkonfiguration ordnungsgemäß funktioniert.
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
- Commerce-Angebotsdatenbank: 11 Tabellen
- Commerce-Verkaufsdatenbank: 55 Tabellen

Um sicherzustellen, dass Ihre aufgeteilten Datenbanken ordnungsgemäß funktionieren, führen Sie die folgenden Aufgaben aus und überprüfen Sie, ob Daten mit einem Datenbank-Tool wie „phpmyadmin[&#x200B; zu den Datenbanktabellen hinzugefügt &#x200B;](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Zu überprüfende Elemente | Vorgehensweise bei der Verifizierung |
| -------------- | ------------- |
| Angebotsdatenbank funktioniert | Artikel zu einem Warenkorb hinzufügen. Stellen Sie sicher, dass den `quote`-, `quote_address`- und `quote_item`-Tabellen Ihrer Angebotdatenbank Zeilen hinzugefügt wurden. |
| Verkaufsdatenbank funktioniert | Abschließen einer Bestellung (jede Zahlungsmethode, einschließlich Scheck/Zahlungsanweisung). Stellen Sie sicher, dass den `sales_order_address`-, `sales_order_item`- und `sales_order_payment`-Tabellen Ihrer Verkaufsdatenbank Zeilen hinzugefügt wurden. |

>[!WARNING]
>
>Sie müssen die beiden zusätzlichen Datenbankinstanzen manuell sichern. Commerce sichert nur die Hauptdatenbankinstanz. Mit den [`magento setup:backup --db`](../../installation/tutorials/backup.md) Befehls- und Admin-Optionen werden die zusätzlichen Tabellen nicht gesichert.
