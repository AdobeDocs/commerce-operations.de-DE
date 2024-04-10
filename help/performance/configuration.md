---
title: Best Practices für die Konfiguration
description: Optimieren Sie die Reaktionszeit Ihrer Adobe Commerce- oder Magento Open Source-Bereitstellung mithilfe dieser Best Practices.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 0%

---

# Best Practices für die Konfiguration

Commerce bietet viele Einstellungen und Tools, mit denen Sie die Antwortzeit auf den Seiten verbessern und einen höheren Durchsatz erzielen können.

## Cron-Aufträge

Alle asynchronen Vorgänge in [!DNL Commerce] werden unter Linux durchgeführt `cron` Befehl. Siehe [Konfigurieren und Ausführen von Cron](../configuration/cli/configure-cron-jobs.md) , um es korrekt zu konfigurieren.

## Indexer

Ein Indexer kann ausgeführt werden in **[!UICONTROL Update on Save]** oder **[!UICONTROL Update on Schedule]** Modus. Die **[!UICONTROL Update on Save]** -Modus indiziert sofort, wenn sich Ihr Katalog oder andere Daten ändern. Dieser Modus geht von einer geringen Intensität der Aktualisierungs- und Browser-Vorgänge in Ihrem Store aus. Dies kann bei hoher Auslastung zu erheblichen Verzögerungen und Nichtverfügbarkeit von Daten führen. Es wird empfohlen, zu verwenden **Aktualisierung planmäßig** Zu Leistungszwecken, da Informationen über Datenaktualisierungen gespeichert werden und die Indexierung im Hintergrund über einen bestimmten Cron-Auftrag portionsweise durchgeführt wird. Sie können den Modus jedes [!DNL Commerce] Indexer separat auf dem  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** Konfigurationsseite. Die [!UICONTROL Customer Grid] Der Index muss immer auf gesetzt sein. **[!UICONTROL Update on Save]** Modus.

>[!TIP]
>
>Die Neuindizierung auf MariaDB 10.4 und 10.6 dauert im Vergleich zu anderen MariaDB- oder [!DNL MySQL] Versionen. Wir empfehlen, die standardmäßige MariaDB-Konfigurationseinstellung zu ändern, die in der [Voraussetzungen für die Installation](../installation/prerequisites/database/mysql.md).

## Caches

Wenn Sie Ihren Store in der Produktion starten, aktivieren Sie alle Caches aus dem **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** Seite. Es wird dringend empfohlen, Folgendes zu verwenden [!DNL Varnish], da es sich um eine effiziente Produktions-Seiten-Cache-Lösung handelt.

## Asynchrone E-Mail-Benachrichtigungen

Durch die Aktivierung der Einstellung „Asynchrone E-Mail-Benachrichtigungen“ werden Prozesse, die E-Mail-Benachrichtigungen zum Auschecken und zur Bestellabwicklung verarbeiten, in den Hintergrund verschoben. Um diese Funktion zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Siehe [Verkaufs-E-Mails](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) in der _Benutzerhandbuch zu Magento Open Source_ für weitere Informationen.

## asynchrone Auftragsdatenverarbeitung

Es kann Situationen geben, in denen intensive Verkäufe an einer Storefront gleichzeitig mit dem [!DNL Commerce] führt eine intensive Auftragsverarbeitung durch. Sie können Folgendes konfigurieren [!DNL Commerce] Um Konflikte zwischen Lese- und Schreibvorgängen in den entsprechenden Tabellen zu vermeiden, sollten diese beiden Traffic-Muster auf Datenbankebene unterschieden werden. Sie können Bestelldaten asynchron speichern und indizieren. Bestellungen werden temporär gespeichert und ohne Kollisionen stapelweise in das Order Management-Raster verschoben. Sie können diese Option aktivieren unter **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Siehe [Geplante Rasteraktualisierungen](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) in der _Benutzerhandbuch zu Magento Open Source_ für weitere Informationen.

>[!WARNING]
>
>Die **[!UICONTROL Developer]** Registerkarten und Optionen sind nur in verfügbar [Entwicklermodus](../configuration/cli/set-mode.md). [Adobe Commerce auf Cloud-Infrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) Unterstützt nicht `Developer` Modus.

## Asynchrone Konfiguration speichern

Bei Projekten mit einer großen Anzahl von Konfigurationen auf Store-Ebene kann das Speichern einer Store-Konfiguration übermäßig viel Zeit in Anspruch nehmen oder zu einer Zeitüberschreitung führen. Die _Async-Konfiguration_ Das -Modul ermöglicht asynchrone Konfigurationsspeicherungen, indem ein Cron-Auftrag ausgeführt wird, der einen -Verbraucher verwendet, um das Speichern in einer Nachrichtenwarteschlange zu verarbeiten. AsyncConfig ist **deaktiviert** Standardmäßig.

Sie können AsyncConfig über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --config-async 1
```

Die `set` -Befehl schreibt Folgendes in die `app/etc/env.php` Datei:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Starten Sie den folgenden Verbraucher, um die Verarbeitung der Nachrichten in der Warteschlange nach dem Prinzip „first-in-first-out“ zu starten:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Zurückgestellte Aktienaktualisierung

In Zeiten intensiver Verkäufe, [!DNL Commerce] Kann Lageraktualisierungen im Zusammenhang mit Bestellungen aufschieben. Dies minimiert die Anzahl der Vorgänge und beschleunigt den Bestellvorgang. Diese Option ist jedoch riskant und kann nur verwendet werden, wenn Nachbestellungen im Geschäft aktiviert sind, da diese Option zu negativen Lagermengen führen kann. Diese Option kann zu erheblichen Leistungsverbesserungen bei Checkout-Flüssen für Geschäfte führen, die ihren Bestand bei Bedarf einfach nachfüllen können. Um verzögerte Stock-Updates auf Ihrer Site zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Siehe [Verwalten von Inventar](https://docs.magento.com/user-guide/catalog/inventory.html) in der _Adobe Commerce-Benutzerhandbuch_ für weitere Informationen.

>[!INFO]
>
>Diese Option ist nur verfügbar, wenn **[!UICONTROL Backorder with any mode]** ist aktiviert.

>[!INFO]
>
>Diese Option funktioniert auch mit [Asynchrone Auftragserteilung](high-throughput-order-processing.md#asynchronous-order-placement) in Kombination mit [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Client-seitige Optimierungseinstellungen

So verbessern Sie die Reaktionsfähigkeit Ihrer Storefront [!DNL Commerce] Wechseln Sie in der -Instanz zu „Admin“ im Standard- oder Entwicklermodus und ändern Sie die folgenden Einstellungen:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Gruppe Einstellungen | Einstellung | Wert |
| ------------------- | -------------------------- | ------ |
| Rastereinstellungen | asynchrone Indizierung | Aktivieren |
| CSS-Einstellungen | Minimieren von CSS-Dateien | Ja |
| [!DNL JavaScript] Einstellungen | Minify [!DNL JavaScript] Dateien | Ja |
| [!DNL JavaScript] Einstellungen | Aktivieren [!DNL JavaScript] Bündelung | Ja |
| Vorlageneinstellungen | HTML minimieren | Ja |

>[!INFO]
>
>Die **[!UICONTROL Developer]** Registerkarten und Optionen sind nur in verfügbar [Entwicklermodus](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] auf Cloud-Infrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) Unterstützt nicht `Developer` Modus.

Beim Aktivieren von **[!UICONTROL Enable [!DNL JavaScript] Bundling]** ermöglicht es Ihnen, alle JS-Ressourcen in einem oder mehreren Bundles zusammenzuführen, die in Storefront-Seiten geladen werden. Die Bündelung von JS führt zu weniger Anfragen an den Server, was die Seitenleistung verbessert. Dies hilft dem Browser auch, JS-Ressourcen beim ersten Aufruf zwischenzuspeichern und sie für das weitere Browsen wiederzuverwenden. Diese Option bietet auch eine verzögerte Auswertung, da alle JS als Text geladen werden. Sie initiiert die Analyse und Auswertung des Codes erst, nachdem bestimmte Aktionen auf der Seite ausgelöst wurden. Diese Einstellung wird jedoch nicht für Stores empfohlen, in denen die Ladezeit der ersten Seite äußerst kritisch ist, da der gesamte JS-Inhalt beim ersten Aufruf geladen wird.

>[!INFO]
>
>Siehe [CSS- und JavaScript-Dateioptimierung auf Adobe Commerce in Cloud-Infrastrukturen und Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) im Adobe Commerce Help Center_ finden Sie weitere Informationen zur Optimierung von CSS und JavaScript.

### Tipps zur Bündelung

* Es wird empfohlen, Tools von Drittanbietern zur Minimierung und Bündelung zu verwenden (z. B. [r.js](https://requirejs.org/)). [!DNL Commerce] Integrierte Mechanismen sind nicht optimal und werden als Ausweichalternativen bereitgestellt.
* Die Aktivierung des HTTP/2-Protokolls kann eine gute Alternative zur Verwendung des JS-Bundles sein. Das Protokoll bietet viele der gleichen Vorteile. Sie ist in Adobe Commerce standardmäßig für Cloud-Infrastrukturprojekte aktiviert.
* Es wird nicht empfohlen, veraltete Einstellungen wie das Zusammenführen von JS- und CSS-Dateien zu verwenden, da sie nur für synchron geladene JS im Abschnitt HEAD der Seite entwickelt wurden. Die Verwendung dieser Technik kann dazu führen, dass die Bündelung fehlerhaft ist und die JS-Logik fehlerhaft funktioniert.

## Validierung von Kundensegmenten

Händler, die über eine große Anzahl von [Kundensegmente](https://docs.magento.com/user-guide/marketing/customer-segments.html) kann es bei Kundenaktionen zu erheblichen Leistungseinbußen kommen, z. B. bei der Kundenanmeldung und beim Hinzufügen von Produkten zum Warenkorb.

Kundenaktionen : Trigger eines Validierungsprozesses für Kundensegmente, der zu Leistungseinbußen führen kann. Standardmäßig validiert Adobe Commerce jedes Segment in Echtzeit, um zu definieren, welche Kundensegmente abgeglichen werden und welche nicht.

Um eine Leistungsbeeinträchtigung zu vermeiden, können Sie Folgendes festlegen **[!UICONTROL Real-time Check if Customer is Matched by Segment]** Systemkonfigurationsoption bis **Nein** , um Kundensegmente anhand einer einzigen kombinierten SQL-Abfrage zu validieren.

Um diese Optimierung zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Diese Einstellung verbessert die Leistung der Validierung von Kundensegmenten, wenn es viele Kundensegmente im System gibt. Es funktioniert jedoch nicht mit [Datenbank teilen](../configuration/storage/multi-master.md) Implementierungen oder wenn keine registrierten Kunden vorhanden sind.

## Zeitplan für die Datenbankwartung {#database}

Es wird empfohlen, regelmäßige Datenbanksicherungen für Ihre Staging- und Produktionsinstanzen durchzuführen. Aufgrund der I/O-intensiven Natur von Backup-Vorgängen können langsamere Backups und potenzielle Probleme auftreten. Das gleichzeitige Ausführen von Datenbankprozessen für mehrere Umgebungen kann aufgrund von Konflikten bei den verfügbaren Ressourcen möglicherweise langsamer ausgeführt werden.

Um eine bessere Leistung zu erzielen, sollten Sie Ihre Backups so planen, dass sie nacheinander, einzeln und zu Nebenzeiten ausgeführt werden. Durch diese Methode werden I/O-Konflikte vermieden und die Zeit bis zur Fertigstellung verkürzt, insbesondere bei kleineren Instanzen, größeren Datenbanken usw.

Wir empfehlen beispielsweise, ein Backup der Produktionsdatenbank und anschließend die Staging-Datenbank zu planen, wenn die Stores weniger häufig besucht werden.

## Anzahl der Produkte im Raster begrenzen

Um die Leistung des Produktrasters für große Kataloge zu verbessern, empfehlen wir, die Anzahl der Produkte im Raster mithilfe der **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** Systemkonfigurationseinstellung.

Diese Systemkonfigurationseinstellung ist standardmäßig deaktiviert. Durch Aktivierung können Sie die Anzahl der Produkte im Raster auf einen bestimmten Wert begrenzen. **[!UICONTROL Records Limit]** ist eine anpassbare Einstellung mit dem standardmäßigen Mindestwert . `20000`.
Wenn die **[!UICONTROL Limit Number of Products in Grid]** Wenn die Einstellung aktiviert ist und die Anzahl der Produkte im Raster das Datensatzlimit überschreitet, wird die begrenzte Sammlung von Datensätzen zurückgegeben. Wenn das Limit erreicht ist, werden die insgesamt gefundenen Datensätze, die Anzahl der ausgewählten Datensätze und die Paginierungselemente in der Rasterkopfzeile ausgeblendet.

Wenn die Gesamtzahl der Produkte im Raster begrenzt ist, wirkt sich dies nicht auf die Massenaktionen des Produktrasters aus. Dies wirkt sich nur auf die Präsentationsebene des Produktrasters aus. Beispielsweise gibt es nur eine begrenzte Anzahl von `20000` Produkte im Raster, auf die der Benutzer klickt **[!UICONTROL Select All]**, wählt die **[!UICONTROL Update attributes]** Massenaktion und aktualisiert einige Attribute. Infolgedessen werden alle Produkte aktualisiert, nicht die begrenzte Sammlung von `20000` Einträge.

Die Begrenzung des Produktrasters betrifft nur Produktsammlungen, die von Benutzeroberflächenkomponenten verwendet werden. Daher sind nicht alle Produktraster von dieser Einschränkung betroffen. Nur die, die verwenden `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Sie können Produktrastersammlungen nur auf den folgenden Seiten einschränken:

* Katalog-Produktraster
* Verknüpftes Raster/Up-Sell-/Crossselling-Produktraster hinzufügen
* Produkte zum Produktpaket hinzufügen
* Produkte zu Produktgruppe hinzufügen
* Admin-Seite „Bestellung erstellen“

Wenn Sie das Produktraster nicht beschränken möchten, empfehlen wir Ihnen, Filter präziser zu verwenden, damit die Ergebnissammlung weniger Elemente enthält als **[!UICONTROL Records Limit]**.
