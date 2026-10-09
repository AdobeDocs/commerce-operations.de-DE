---
title: Geteilte Datenbank überprüfen
description: Erfahren Sie, wie Sie überprüfen können, ob eine Commerce Split-Datenbankkonfiguration ordnungsgemäß funktioniert.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
