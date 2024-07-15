---
title: Suchmaschinenkonfiguration
description: Konfigurieren Sie eine Suchmaschine für lokale Bereitstellungen von Adobe Commerce.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Suchmaschinenkonfiguration

In diesem Abschnitt werden die Mindesteinstellungen erläutert, die Sie zum Testen von Elasticsearch oder OpenSearch mit lokalen Implementierungen von Adobe Commerce auswählen müssen.

>[!TIP]
>
>In den Versionen 2.4.4 und 2.4.3-p2 gelten alle Felder mit der Bezeichnung **Elasticsearch** auch für OpenSearch.
>Als die Unterstützung für Elasticsearch 8.x in Version 2.4.6 eingeführt wurde, wurden neue Bezeichnungen erstellt, um zwischen Elasticsearch- und OpenSearch-Konfigurationen zu unterscheiden.

Weitere Informationen zum Konfigurieren der Suchmaschine finden Sie im [Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## Konfigurieren der Suchmaschine über den Administrator

>[!TIP]
>
>Anweisungen zum Aktualisieren auf eine neue Suchmaschinenversion finden Sie unter [Upgrade-Voraussetzungen](../../upgrade/prepare/prerequisites.md).

So konfigurieren Sie Ihr System für die Verwendung von Elasticsearch oder OpenSearch:

1. Melden Sie sich bei Admin als Administrator an.
1. Klicken Sie auf **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Wählen Sie in der Liste **[!UICONTROL Search Engine]** die entsprechende Version Ihrer Suchmaschine aus.

   In der folgenden Tabelle sind die erforderlichen Optionen zum Konfigurieren und Testen der Verbindung mit Commerce aufgeführt. Sofern Sie die Servereinstellungen Ihrer Suchmaschine nicht geändert haben, sollten die Standardeinstellungen funktionieren. Fahren Sie mit dem nächsten Schritt fort.

   | Option | Beschreibung |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Geben Sie den vollständig qualifizierten Hostnamen oder die IP-Adresse des Computers ein, auf dem Elasticsearch oder OpenSearch ausgeführt wird.<br>Adobe Commerce in der Cloud-Infrastruktur: Rufen Sie diesen Wert von Ihrem Integrationssystem ab. |
   | **[!UICONTROL Server Port]** | Geben Sie den Proxyanschluss des Webservers ein. Der Standardwert ist 9200<br>Adobe Commerce in der Cloud-Infrastruktur: Rufen Sie diesen Wert aus Ihrem Integrationssystem ab. |
   | **[!UICONTROL Index Prefix]** | Geben Sie das Suchmaschinen-Indexpräfix ein. Wenn Sie eine Instanz für mehr als eine Commerce-Installation verwenden (Staging- und Produktionsumgebungen), müssen Sie für jede Installation ein eindeutiges Präfix angeben. Andernfalls können Sie das standardmäßige Präfix magento2 verwenden. |
   | **[!UICONTROL Enable HTTP Auth]** | Klicken Sie nur dann auf **[!UICONTROL Yes]** , wenn Sie die Authentifizierung für Ihren Suchmaschinenserver aktiviert haben. Wenn ja, geben Sie in den angegebenen Feldern einen Benutzernamen und ein Kennwort ein. |
   | **[!UICONTROL Server Timeout]** | Geben Sie die Wartezeit (in Sekunden) ein, wenn Sie versuchen, eine Verbindung zum Elasticsearch- oder OpenSearch-Server herzustellen. |

1. Klicken Sie auf **[!UICONTROL Test Connection]**.

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
- Überprüfen Sie das Befehlsfenster, in dem Sie Elasticsearch gestartet haben, oder OpenSearch auf Stacktraces und Ausnahmen. Sie müssen diese auflösen, bevor Sie fortfahren. Stellen Sie insbesondere sicher, dass Sie Ihre Suchmaschine als Benutzer mit `root` -Berechtigungen gestartet haben.
- Stellen Sie sicher, dass sowohl die [UNIX-Firewall als auch SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) deaktiviert sind, oder legen Sie Regeln fest, die es Ihrer Suchmaschine und Commerce ermöglichen, miteinander zu kommunizieren.
- Überprüfen Sie den Wert des Felds **[!UICONTROL Server Hostname]** . Stellen Sie sicher, dass der Server verfügbar ist. Sie können stattdessen die IP-Adresse des Servers ausprobieren.
- Verwenden Sie den Befehl `netstat -an | grep <listen-port>` , um sicherzustellen, dass der im Feld **[!UICONTROL Server Port]** angegebene Anschluss nicht von einem anderen Prozess verwendet wird.

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
1. Klicken Sie in der Liste **[!UICONTROL Actions]** oben rechts auf **Aktualisieren**.

   ![Cache-Verwaltung](../../assets/configuration/refresh-cache.png)

So leeren Sie den Cache mit der Befehlszeile: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

So fügen Sie eine Neuindizierung mithilfe der Befehlszeile ein:

1. Melden Sie sich bei Ihrem Commerce-Server als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
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
   >Im Gegensatz zum Cache werden Indexer durch einen Cron-Auftrag aktualisiert. Stellen Sie sicher, dass [cron aktiviert ist](../cli/configure-cron-jobs.md), bevor Sie mit der Verwendung Ihrer Suchmaschine beginnen.
