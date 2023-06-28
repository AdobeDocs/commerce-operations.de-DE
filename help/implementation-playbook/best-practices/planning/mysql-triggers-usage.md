---
title: Verwendung von MySQL-Triggern
description: Erfahren Sie, wie Sie MySQL-Trigger effektiv mit Adobe Commerce verwenden können.
role: Developer
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Best Practices für die Verwendung von MySQL-Triggern

In diesem Artikel wird erläutert, wie Sie Leistungsprobleme bei der Verwendung von MySQL-Triggern vermeiden können. Trigger werden verwendet, um Änderungen in Audit-Tabellen zu protokollieren.

## Betroffene Produkte und Versionen

- Adobe Commerce vor Ort
- Adobe Commerce auf Cloud-Infrastruktur

>[!WARNING]
>
>Testen Sie bei Adobe Commerce in Cloud-Projekten immer Konfigurationsänderungen in der Staging-Umgebung, bevor Sie die Konfiguration für die Produktionsumgebung ändern.

## Auswirkungen auf die Leistung

Trigger werden als Code interpretiert, was bedeutet, dass MySQL sie nicht vorkompiliert.

Wenn Sie sich die Transaktionsfläche der Abfrage ansehen, fügen Trigger einem Parser und Interpreter Mehraufwand für jede mit der Tabelle ausgeführte Abfrage hinzu. Die Trigger teilen sich denselben Transaktionsraum wie die ursprünglichen Abfragen. Während diese Abfragen um Sperren in der Tabelle konkurrieren, konkurrieren die Trigger unabhängig voneinander um Sperren in einer anderen Tabelle.

Dieser zusätzliche Mehraufwand kann sich negativ auf die Site-Leistung auf der Site auswirken, wenn viele Trigger verwendet werden.

>[!WARNING]
>
>Adobe Commerce unterstützt keine benutzerdefinierten Trigger in der Adobe Commerce-Datenbank, da benutzerdefinierte Trigger Inkompatibilitäten mit zukünftigen Adobe Commerce-Versionen verursachen können. Best Practices finden Sie unter [Allgemeine MySQL-Richtlinien](../../../installation/prerequisites/database/mysql.md) in der Adobe Commerce-Dokumentation.

## Effektives Verwenden von Triggern

Um Leistungsprobleme bei der Verwendung von Triggern zu vermeiden, befolgen Sie die folgenden Richtlinien:

- Wenn Sie über benutzerdefinierte Trigger verfügen, die bei der Ausführung des Triggers Daten schreiben, verschieben Sie diese Logik, um stattdessen direkt in die Audit-Tabellen zu schreiben. Fügen Sie beispielsweise im Anwendungscode nach der Abfrage, für die Sie den Trigger erstellen möchten, eine zusätzliche Abfrage hinzu.
- Überprüfen Sie vorhandene benutzerdefinierte Trigger und erwägen Sie, sie zu entfernen und direkt von der Anwendungsseite aus in die Tabellen zu schreiben. Suchen Sie mithilfe der [`SHOW TRIGGERS` SQL-Anweisung](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Für zusätzliche Unterstützung, Fragen oder Bedenken: [Senden eines Adobe Commerce Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Zusätzliche Informationen

- [MySQL-Voraussetzungen](../../../installation/prerequisites/database/mysql.md)
- [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](database-on-cloud.md)
