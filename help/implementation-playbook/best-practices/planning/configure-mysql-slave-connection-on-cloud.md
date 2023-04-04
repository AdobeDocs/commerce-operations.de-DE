---
title: Best Practice zum Konfigurieren der MySQL-Slave-Verbindung
description: Erfahren Sie, wie Sie die MySQL-Slave-Verbindung für Adobe Commerce-Sites konfigurieren, die in der Cloud-Infrastruktur bereitgestellt werden.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Best Practice zum Konfigurieren der MySQL-Slave-Verbindung

>[!NOTE]
>
>Dieser Artikel enthält branchenübliche Softwarebegriffe, die einige als rassistisch, sexistisch oder unterdrückend empfinden und die dazu führen können, dass sich der Leser verletzt, traumatisiert oder unerwünscht fühlt. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.

Für Adobe Commerce-Sites, die in der Cloud Infrastructure Pro-Architektur bereitgestellt werden, empfiehlt Adobe standardmäßig die Aktivierung der MYSQL-Slave-Verbindung für die Datenbank.

Adobe Commerce kann mehrere Datenbanken asynchron lesen. Wenn Sie die MYSQL-Slave-Verbindung aktivieren, verwendet Adobe Commerce eine schreibgeschützte Verbindung zur Datenbank, um schreibgeschützten Traffic auf einem nicht Übergeordneten Knoten zu empfangen. Die Leistung verbessert sich durch den Lastenausgleich, wenn nur ein Knoten Lese- und Schreibvorgänge-Traffic verarbeitet.

## Betroffene Versionen

Adobe Commerce in Cloud-Infrastruktur, Pro-Architektur

## MySQL-Slave-Verbindung konfigurieren

In der Cloud-Infrastruktur von Adobe Commerce können Sie die Standardkonfiguration für die MYSQL-Slave-Verbindung außer Kraft setzen, indem Sie die [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) -Variable. Setzen Sie diese Variable auf &quot;true&quot;, um automatisch eine schreibgeschützte Verbindung zur Datenbank zu verwenden.

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

Erfahren Sie mehr über das Anpassen der Cloud-Umgebung durch Überschreiben Ihrer bestehenden Commerce-Konfiguration mit [Umgebungsvariablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) im _Handbuch zur Cloud-Infrastruktur für Adobe Commerce_.

## Zusätzliche Informationen

- [Engpässe bei hoher MySQL-Auslastung in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](database-on-cloud.md)
