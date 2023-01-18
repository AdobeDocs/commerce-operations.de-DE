---
title: Best Practice zum Konfigurieren der MySQL-Slave-Verbindung
description: Erfahren Sie, wie Sie die MySQL-Slave-Verbindung für Adobe Commerce-Sites konfigurieren, die in der Cloud-Infrastruktur bereitgestellt werden.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: a5a6e25e3fd303e07a07110b85aa1d460f53cd54
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Best Practice zum Konfigurieren der MySQL-Slave-Verbindung

>[!NOTE]
>
>Wir wissen, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthält, die einige rassistisch, sexistisch oder unterdrückend finden und die den Leser verletzen, traumatisiert oder unwillkommen machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.

Für Adobe Commerce-Sites, die in der Cloud Infrastructure Pro-Architektur bereitgestellt werden, empfiehlt Adobe standardmäßig die Aktivierung der MYSQL-Slave-Verbindung für die Datenbank.

Adobe Commerce kann mehrere Datenbanken asynchron lesen.  Wenn Sie die MYSQL-Slave-Verbindung aktivieren, verwendet Adobe Commerce eine schreibgeschützte Verbindung zur Datenbank, um schreibgeschützten Traffic auf einem nicht Übergeordneten Knoten zu empfangen. Dies verbessert die Leistung durch Lastenausgleich, da nur ein Knoten Lese- und Schreibvorgänge-Traffic verarbeiten muss.

## Betroffene Versionen

Adobe Commerce in Cloud-Infrastruktur, Pro-Architektur

## MySQL-Slave-Verbindung konfigurieren

Die Konfiguration für die MYSQL-Slave-Verbindung wird von der [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) -Variable in Adobe Commerce in der Konfigurationsdatei der Cloud-Infrastruktur bereitstellen, `.magento.env.yaml`. Setzen Sie diese Variable auf `true` , um die Verbindung zu aktivieren.

So aktivieren Sie die MySQL-Slave-Verbindung:

1. Bearbeiten Sie Ihre `.magento.env.yaml` Datei und überprüfen Sie, ob `MYSQL_USE_SLAVE_CONNECTION` aktiviert ist.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Übertragen Sie alle Änderungen und geben Sie sie an die Umgebungsverzweigung weiter, um die Aktualisierung bereitzustellen.

   Nach erfolgreichem Abschluss der Bereitstellung wird die MySQL-Slave-Verbindung in Ihrer Cloud-Infrastruktur aktiviert.

## Zusätzliche Informationen

- [Umgebungsvariablen](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [Engpässe bei hoher MySQL-Auslastung in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](database-on-cloud.md)
