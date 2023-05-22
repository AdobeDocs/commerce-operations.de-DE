---
title: Suchmaschinenkonfiguration
description: Konfigurieren Sie eine Suchmaschine für lokale Bereitstellungen von Adobe Commerce und Magento Open Source.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Suchmaschinenkonfiguration

In diesem Abschnitt werden die Mindesteinstellungen erläutert, die Sie zum Testen von Elasticsearch oder OpenSearch mit lokalen Implementierungen von Adobe Commerce und Magento Open Source auswählen müssen.

>[!TIP]
>
>In den Versionen 2.4.4 und 2.4.3-p2 werden alle Felder mit der Beschriftung **Elasticsearch** gilt auch für OpenSearch.
>Als die Unterstützung für Elasticsearch 8.x in Version 2.4.6 eingeführt wurde, wurden neue Bezeichnungen erstellt, um zwischen Elasticsearch- und OpenSearch-Konfigurationen zu unterscheiden.

Weitere Informationen zum Konfigurieren der Suchmaschine finden Sie in der [Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## Konfigurieren der Suchmaschine über den Administrator

>[!TIP]
>
>Anweisungen zum Upgrade auf eine neue Suchmaschinenversion finden Sie unter [Upgrade-Voraussetzungen](../../upgrade/prepare/prerequisites.md).

So konfigurieren Sie Ihr System für die Verwendung von Elasticsearch oder OpenSearch:

1. Melden Sie sich bei Admin als Administrator an.
1. Klicken **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Aus dem **[!UICONTROL Search Engine]** auswählen, wählen Sie die entsprechende Version Ihrer Suchmaschine aus.

   In der folgenden Tabelle sind die erforderlichen Optionen zum Konfigurieren und Testen der Verbindung mit Commerce aufgeführt. Sofern Sie die Servereinstellungen Ihrer Suchmaschine nicht geändert haben, sollten die Standardeinstellungen funktionieren. Fahren Sie mit dem nächsten Schritt fort.

   | Option | Beschreibung |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Geben Sie den vollständig qualifizierten Hostnamen oder die IP-Adresse des Computers ein, auf dem Elasticsearch oder OpenSearch ausgeführt wird.<br>Adobe Commerce über Cloud-Infrastruktur: Rufen Sie diesen Wert von Ihrem Integrationssystem ab. |
   | **[!UICONTROL Server Port]** | Geben Sie den Proxyanschluss des Webservers ein. Der Standardwert ist 9200.<br>Adobe Commerce über Cloud-Infrastruktur: Rufen Sie diesen Wert von Ihrem Integrationssystem ab. |
   | **[!UICONTROL Index Prefix]** | Geben Sie das Suchmaschinen-Indexpräfix ein. Wenn Sie eine einzelne Instanz für mehr als eine Commerce-Installation verwenden (Staging- und Produktionsumgebungen), müssen Sie für jede Installation ein eindeutiges Präfix angeben. Andernfalls können Sie das standardmäßige Präfix magento2 verwenden. |
   | **[!UICONTROL Enable HTTP Auth]** | Klicken **[!UICONTROL Yes]** nur dann, wenn Sie die Authentifizierung für Ihren Suchmaschinenserver aktiviert haben. Wenn ja, geben Sie in den angegebenen Feldern einen Benutzernamen und ein Kennwort ein. |
   | **[!UICONTROL Server Timeout]** | Geben Sie die Wartezeit (in Sekunden) ein, wenn Sie versuchen, eine Verbindung zum Elasticsearch- oder OpenSearch-Server herzustellen. |

1. Klicken **[!UICONTROL Test Connection]**.

   Beispielantwort:

   ![success](../../assets/configuration/elastic_test-success.png)

   Fahren Sie fort mit:

   - [Konfigurieren von Apache für Ihre Suchmaschine](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Konfigurieren von nginx für Ihre Suchmaschine](../../installation/prerequisites/search-engine/configure-nginx.md)

   oder Sie sehen:

   ![failed](../../assets/configuration/elastic_test-fail.png)

Wenn ja, versuchen Sie Folgendes:

- Stellen Sie sicher, dass der Suchmaschinenserver ausgeführt wird.
- Wenn sich der Server auf einem anderen Host als Commerce befindet, melden Sie sich beim Commerce-Server an und pingen Sie den Suchmaschinen-Host. Beheben Sie Probleme mit der Netzwerkverbindung und testen Sie die Verbindung erneut.
- Überprüfen Sie das Befehlsfenster, in dem Sie Elasticsearch gestartet haben, oder OpenSearch auf Stacktraces und Ausnahmen. Sie müssen diese auflösen, bevor Sie fortfahren. Stellen Sie insbesondere sicher, dass Sie Ihre Suchmaschine als Benutzer mit `root` Berechtigungen.
- Stellen Sie sicher, dass [UNIX-Firewall und SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) sind beide deaktiviert oder legen Regeln fest, mit denen Ihre Suchmaschine und Ihr Commerce miteinander kommunizieren können.
- Überprüfen Sie den Wert der **[!UICONTROL Server Hostname]** -Feld. Stellen Sie sicher, dass der Server verfügbar ist. Sie können stattdessen die IP-Adresse des Servers ausprobieren.
- Verwenden Sie die `netstat -an | grep <listen-port>` -Befehl, um zu überprüfen, ob der im **[!UICONTROL Server Port]** nicht von einem anderen Prozess verwendet wird.

   Um beispielsweise zu sehen, ob Ihre Suchmaschine an ihrem Standardanschluss ausgeführt wird, verwenden Sie den folgenden Befehl:

   ```bash
   netstat -an | grep 9200
   ```

   Wenn sie auf Port 9200 ausgeführt wird, wird sie in etwa wie folgt angezeigt:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Neuindizieren der Katalogsuche und Aktualisieren des gesamten Seiten-Cache

Nachdem Sie die Suchmaschinenkonfiguration geändert haben, müssen Sie den Katalogsuchindex neu indizieren und den gesamten Seiten-Cache mit der Admin- oder Befehlszeile aktualisieren.

So aktualisieren Sie den Cache mit dem Admin:

1. Klicken Sie im Admin auf **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Aktivieren Sie das Kontrollkästchen neben **[!UICONTROL Page Cache]**.
1. Aus dem **[!UICONTROL Actions]** Liste oben rechts, klicken Sie auf **Aktualisieren**.

   ![Cacheverwaltung](../../assets/configuration/refresh-cache.png)

So leeren Sie den Cache mit der Befehlszeile: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

So fügen Sie eine Neuindizierung mithilfe der Befehlszeile ein:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zu der [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
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
