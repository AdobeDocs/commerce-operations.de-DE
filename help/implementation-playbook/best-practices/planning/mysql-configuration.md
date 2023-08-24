---
title: Best Practices für die MySQL-Konfiguration
description: Erfahren Sie, wie MySQL-Trigger und Slave-Verbindungen die Performance von Commerce-Sites beeinflussen und wie sie effektiv verwendet werden.
role: Developer
feature: Best Practices
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Best Practices für die MySQL-Konfiguration

>[!NOTE]
>
>Dieses Thema enthält branchenübliche Softwarebegriffe, die einige als rassistisch, sexistisch oder unterdrückend empfinden und die dazu führen können, dass sich der Leser verletzt, traumatisiert oder unerwünscht fühlt. Adobe arbeitet daran, diese Begriffe aus Code, Dokumentation und Benutzererlebnissen zu entfernen.

## Trigger

In diesem Artikel wird erläutert, wie Sie Leistungsprobleme bei der Verwendung von MySQL-Triggern vermeiden können. Trigger werden verwendet, um Änderungen in Audit-Tabellen zu protokollieren.

### Betroffene Produkte und Versionen

- Adobe Commerce vor Ort
- Adobe Commerce auf Cloud-Infrastruktur

>[!WARNING]
>
>Testen Sie bei Adobe Commerce in Cloud-Projekten immer Konfigurationsänderungen in der Staging-Umgebung, bevor Sie die Konfiguration für die Produktionsumgebung ändern.

### Leistungsbeeinträchtigungen

Trigger werden als Code interpretiert, was bedeutet, dass MySQL sie nicht vorkompiliert.

Wenn Sie sich die Transaktionsfläche der Abfrage ansehen, fügen Trigger einem Parser und Interpreter Mehraufwand für jede mit der Tabelle ausgeführte Abfrage hinzu. Die Trigger teilen sich denselben Transaktionsraum wie die ursprünglichen Abfragen. Während diese Abfragen um Sperren in der Tabelle konkurrieren, konkurrieren die Trigger unabhängig voneinander um Sperren in einer anderen Tabelle.

Dieser zusätzliche Mehraufwand kann sich negativ auf die Site-Leistung auf der Site auswirken, wenn viele Trigger verwendet werden.

>[!WARNING]
>
>Adobe Commerce unterstützt keine benutzerdefinierten Trigger in der Adobe Commerce-Datenbank, da benutzerdefinierte Trigger Inkompatibilitäten mit zukünftigen Adobe Commerce-Versionen verursachen können. Best Practices finden Sie unter [Allgemeine MySQL-Richtlinien](../../../installation/prerequisites/database/mysql.md) in der Adobe Commerce-Dokumentation.

### Wirksame Anwendung

Um Leistungsprobleme bei der Verwendung von Triggern zu vermeiden, befolgen Sie die folgenden Richtlinien:

- Wenn Sie über benutzerdefinierte Trigger verfügen, die bei der Ausführung des Triggers Daten schreiben, verschieben Sie diese Logik, um stattdessen direkt in die Audit-Tabellen zu schreiben. Fügen Sie beispielsweise im Anwendungscode nach der Abfrage, für die Sie den Trigger erstellen möchten, eine zusätzliche Abfrage hinzu.
- Überprüfen Sie vorhandene benutzerdefinierte Trigger und erwägen Sie, sie zu entfernen und direkt von der Anwendungsseite aus in die Tabellen zu schreiben. Suchen Sie mithilfe der [`SHOW TRIGGERS` SQL-Anweisung](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Für zusätzliche Unterstützung, Fragen oder Bedenken: [Senden eines Adobe Commerce Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Slave-Verbindungen

Adobe Commerce kann mehrere Datenbanken asynchron lesen. Wenn Sie eine hohe Belastung der MySQL-Datenbank einer Commerce-Site erwarten, die in der Cloud Infrastructure Pro-Architektur bereitgestellt wird, empfiehlt Adobe die Aktivierung der MYSQL-Slave-Verbindung.

Wenn Sie die MYSQL-Slave-Verbindung aktivieren, verwendet Adobe Commerce eine schreibgeschützte Verbindung zur Datenbank, um schreibgeschützten Traffic auf einem Nicht-Master-Knoten zu empfangen. Die Leistung verbessert sich durch den Lastenausgleich, wenn nur ein Knoten Lese- und Schreibvorgänge-Traffic verarbeitet.

### Betroffene Versionen

Adobe Commerce in Cloud-Infrastruktur, nur Pro-Architektur

### Konfiguration

In der Cloud-Infrastruktur von Adobe Commerce können Sie die Standardkonfiguration für die MYSQL-Slave-Verbindung außer Kraft setzen, indem Sie die [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) -Variable. Setzen Sie diese Variable auf `true` , um automatisch eine schreibgeschützte Verbindung zur Datenbank zu verwenden.

**Aktivieren der MySQL-Slave-Verbindung**:

1. Wechseln Sie auf Ihrer lokalen Workstation zum Projektverzeichnis.

1. Im `.magento.env.yaml` -Datei, legen Sie die `MYSQL_USE_SLAVE_CONNECTION` auf &quot;true&quot;.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Bestätigen Sie die `.magento.env.yaml` Dateiänderungen und Push-Benachrichtigungen an die Remote-Umgebung.

   Nach erfolgreichem Abschluss der Bereitstellung wird die MySQL-Slave-Verbindung für die Cloud-Umgebung aktiviert.
