---
title: Best Practices für die MySQL-Konfiguration
description: Erfahren Sie, wie MySQL-Trigger und Slave-Verbindungen die Leistung der Commerce-Site beeinflussen und wie Sie sie effektiv nutzen können.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Best Practices für die MySQL-Konfiguration

>[!NOTE]
>
>Dieses Thema enthält branchenübliche Softwarebegriffe, die manche als rassistisch, sexistisch oder repressiv empfinden und die Leser verletzen, traumatisieren oder unwillkommen heißen können. Adobe entfernt diese Begriffe aus Code, Dokumentation und Anwendererlebnissen.

## Trigger

In diesem Artikel wird erläutert, wie sich Leistungsprobleme bei der Verwendung von MySQL-Triggern vermeiden lassen. Trigger werden verwendet, um Änderungen in Audit-Tabellen zu protokollieren.

### Betroffene Produkte und Versionen

- Adobe Commerce On-Premises
- Adobe Commerce auf Cloud-Infrastruktur

>[!WARNING]
>
>Testen Sie bei Adobe Commerce in Cloud-Projekten immer Konfigurationsänderungen in der Staging-Umgebung, bevor Sie die Konfiguration für die Produktionsumgebung ändern.

### Auswirkungen auf die Leistung

Trigger werden als Code interpretiert, was bedeutet, dass MySQL sie nicht vorkompiliert.

Beim Einbinden in den Transaktionsbereich der Abfrage fügen Trigger für jede mit der Tabelle durchgeführte Abfrage einen Mehraufwand für einen Parser und einen Interpreter hinzu. Die Trigger nutzen denselben Transaktionsbereich wie die Originalabfragen. Während diese Abfragen um Tabellensperren konkurrieren, konkurrieren die Trigger unabhängig voneinander um Sperren in einer anderen Tabelle.

Dieser zusätzliche Mehraufwand kann sich negativ auf die Site-Leistung auf der Site auswirken, wenn viele Trigger verwendet werden.

>[!WARNING]
>
>Adobe Commerce unterstützt keine benutzerdefinierten Trigger in der Adobe Commerce-Datenbank, da benutzerdefinierte Trigger Inkompatibilitäten mit zukünftigen Adobe Commerce-Versionen einführen können. Best Practices finden Sie unter [Allgemeine MySQL-Richtlinien](../../../installation/prerequisites/database/mysql.md) in der Dokumentation zu Adobe Commerce.

### Effektive Nutzung

Um Leistungsprobleme bei der Verwendung von Triggern zu vermeiden, befolgen Sie die folgenden Richtlinien:

- Wenn Sie benutzerdefinierte Trigger haben, die einige Daten schreiben, wenn der Trigger ausgeführt wird, verschieben Sie diese Logik stattdessen so, dass sie direkt in die Audit-Tabellen schreibt. Durch Hinzufügen einer zusätzlichen Abfrage im Anwendungscode nach der Abfrage, für die Sie den Trigger erstellen möchten, können Sie dies beispielsweise tun.
- Überprüfen Sie vorhandene benutzerdefinierte Trigger und erwägen Sie, sie zu entfernen und direkt in die Tabellen auf Anwendungsseite zu schreiben. Suchen Sie mithilfe der [`SHOW TRIGGERS` SQL-Anweisung nach vorhandenen Triggern in Ihrer ](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Wenn Sie weitere Hilfe, Fragen oder Bedenken wünschen, [ Sie ein Adobe Commerce Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Slave-Verbindungen

Adobe Commerce kann mehrere Datenbanken asynchron lesen. Wenn Sie eine hohe Auslastung der MySQL-Datenbank einer Commerce-Site erwarten, die auf der Cloud Infrastructure Pro-Architektur bereitgestellt wird, empfiehlt Adobe, die MYSQL-Slave-Verbindung zu aktivieren.

Wenn Sie die MYSQL-Slave-Verbindung aktivieren, verwendet Adobe Commerce eine schreibgeschützte Verbindung zur Datenbank, um schreibgeschützten Traffic auf einem Nicht-Master-Knoten zu empfangen. Die Leistung wird durch den Lastausgleich verbessert, wenn nur ein Knoten Lese-/Schreibdatenverkehr verarbeitet.

### Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur, nur Pro-Architektur

### Konfiguration

In der Adobe Commerce on Cloud-Infrastruktur können Sie die Standardkonfiguration für die MYSQL-Slave-Verbindung überschreiben, indem Sie die Variable [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) festlegen. Legen Sie diese Variable auf `true` fest, um automatisch eine schreibgeschützte Verbindung zur Datenbank zu verwenden.

**So aktivieren Sie die MySQL-Slave-Verbindung**:

1. Wechseln Sie auf Ihrer lokalen Workstation in Ihr Projektverzeichnis.

1. Legen Sie in der `.magento.env.yaml`-Datei den `MYSQL_USE_SLAVE_CONNECTION` auf „true“ fest.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Übergeben Sie die `.magento.env.yaml` Dateiänderungen und übertragen Sie sie in die Remote-Umgebung.

   Nach erfolgreichem Abschluss der Bereitstellung wird die MySQL-Slave-Verbindung für die Cloud-Umgebung aktiviert.
