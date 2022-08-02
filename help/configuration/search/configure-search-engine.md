---
title: Suchmaschinenkonfiguration
description: Konfigurieren Sie eine Suchmaschine mit Adobe Commerce und Magento Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Suchmaschinenkonfiguration

In diesem Abschnitt werden die Mindesteinstellungen erläutert, die Sie zum Testen von Elasticsearch oder OpenSearch mit Adobe Commerce und Magento Open Source auswählen müssen. Ab den Versionen 2.4.4 und 2.4.3-p2 werden alle Felder mit der Beschriftung **Elasticsearch** gilt auch für OpenSearch.

Weitere Informationen zum Konfigurieren der Suchmaschine finden Sie in der [Benutzerhandbuch](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html).

## Konfigurieren der Suchmaschine über den Administrator

So konfigurieren Sie Ihr System für die Verwendung von Elasticsearch oder OpenSearch:

1. Melden Sie sich bei Admin als Administrator an.
1. Klicken **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Katalog** > **Katalogsuche**.
1. Aus dem **Suchmaschine** die entsprechende Version Ihrer Suchmaschine auswählen. Wenn Sie OpenSearch verwenden, müssen Sie Elasticsearch7 auswählen.

   In der folgenden Tabelle sind die erforderlichen Konfigurationsoptionen zum Konfigurieren und Testen der Verbindung mit Commerce aufgeführt.
Sofern Sie die Servereinstellungen Ihrer Suchmaschine nicht geändert haben, sollten die Standardeinstellungen funktionieren. Fahren Sie mit dem nächsten Schritt fort.

   | Option | Beschreibung |
   |--- |--- |
   | **Hostname des Elasticsearch-Servers** | Geben Sie den vollständig qualifizierten Hostnamen oder die IP-Adresse des Computers ein, auf dem Elasticsearch oder OpenSearch ausgeführt wird.<br>Adobe Commerce über Cloud-Infrastruktur: Rufen Sie diesen Wert von Ihrem Integrationssystem ab. |
   | **Elasticsearch-Server-Port** | Geben Sie den Proxyanschluss des Webservers ein. Der Standardwert ist 9200.<br>Adobe Commerce über Cloud-Infrastruktur: Rufen Sie diesen Wert von Ihrem Integrationssystem ab. |
   | **Elasticsearch-Indexpräfix** | Geben Sie das Suchmaschinen-Indexpräfix ein. Wenn Sie eine einzelne Instanz für mehr als eine Commerce-Installation verwenden (Staging- und Produktionsumgebungen), müssen Sie für jede Installation ein eindeutiges Präfix angeben. Andernfalls können Sie das standardmäßige Präfix magento2 verwenden. |
   | **Aktivieren der Elasticsearch-HTTP-Autorisierung** | Klicken **Ja** nur dann, wenn Sie die Authentifizierung für Ihren Suchmaschinenserver aktiviert haben. Wenn ja, geben Sie in den angegebenen Feldern einen Benutzernamen und ein Kennwort ein. |

1. Klicken **Verbindung testen**.

   Beispielantwort:

   ![success](../../assets/configuration/elastic_test-success.png)

   Fahren Sie fort mit:

   - [Konfigurieren von Apache für Ihre Suchmaschine](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html)
   - [Konfigurieren von nginx für Ihre Suchmaschine](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html)

   oder Sie sehen:

   ![failed](../../assets/configuration/elastic_test-fail.png)

Wenn ja, versuchen Sie Folgendes:

- Stellen Sie sicher, dass der Suchmaschinenserver ausgeführt wird.
- Wenn sich der Server auf einem anderen Host als Commerce befindet, melden Sie sich beim Commerce-Server an und pingen Sie den Suchmaschinen-Host. Beheben Sie Probleme mit der Netzwerkverbindung und testen Sie die Verbindung erneut.
- Überprüfen Sie das Befehlsfenster, in dem Sie Elasticsearch gestartet haben, oder OpenSearch auf Stacktraces und Ausnahmen. Sie müssen diese auflösen, bevor Sie fortfahren. Stellen Sie insbesondere sicher, dass Sie Ihre Suchmaschine als Benutzer mit `root` Berechtigungen.
- Stellen Sie sicher, dass [UNIX-Firewall und SELinux](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#firewall-selinux) sind beide deaktiviert oder legen Regeln fest, mit denen Ihre Suchmaschine und Ihr Commerce miteinander kommunizieren können.
- Überprüfen Sie den Wert der **Hostname des Elasticsearch-Servers** -Feld. Stellen Sie sicher, dass der Server verfügbar ist. Sie können stattdessen die IP-Adresse des Servers ausprobieren.
- Verwenden Sie die `netstat -an | grep <listen-port>` -Befehl, um zu überprüfen, ob der im **Elasticsearch-Server-Port** nicht von einem anderen Prozess verwendet wird.

   Um beispielsweise zu sehen, ob Ihre Suchmaschine an ihrem Standardanschluss ausgeführt wird, verwenden Sie den folgenden Befehl:

   ```bash
   netstat -an | grep 9200
   ```

   Wenn sie auf Port 9200 ausgeführt wird, wird sie in etwa wie folgt angezeigt:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Neuindizieren der Katalogsuche und Aktualisieren des gesamten Seiten-Caches

Nachdem Sie die Suchmaschinenkonfiguration geändert haben, müssen Sie den Katalogsuchindex neu indizieren und den gesamten Seiten-Cache mit der Admin- oder Befehlszeile aktualisieren.

So aktualisieren Sie den Cache mit dem Admin:

1. Klicken Sie im Admin auf **System** > **Cacheverwaltung**.
1. Aktivieren Sie das Kontrollkästchen neben **Seiten-Cache**.
1. Aus dem **Aktionen** Liste oben rechts, klicken Sie auf **Aktualisieren**.

   ![Cacheverwaltung](../../assets/configuration/refresh-cache.png)

So leeren Sie den Cache mit der Befehlszeile: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

So fügen Sie eine Neuindizierung mithilfe der Befehlszeile ein:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zu der [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Geben Sie einen der folgenden Befehle ein:

   Geben Sie den folgenden Befehl ein, um nur den Katalogsuchindex neu zu indizieren:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Geben Sie den folgenden Befehl ein, um alle Indexer neu zu indizieren:

   ```bash
   bin/magento indexer:reindex
   ```

1. Warten Sie, bis die Neuindizierung abgeschlossen ist.

   >[!INFO]
   >
   >Im Gegensatz zum Cache werden Indexer durch einen Cron-Auftrag aktualisiert. Stellen Sie sicher [cron ist aktiviert](../cli/configure-cron-jobs.md) bevor Sie mit der Verwendung Ihrer Suchmaschine beginnen.

