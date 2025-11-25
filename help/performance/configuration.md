---
title: Best Practices für die Konfiguration
description: Erfahren Sie mehr über Best Practices für die Konfiguration zur Optimierung der Adobe Commerce-Leistung. Entdecken Sie Einstellungen und Tools zur Verbesserung der Reaktionszeit und des Durchsatzes.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: be13bed02b6307d0906e9c640962ee7d8c05d855
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 0%

---

# Best Practices für die Konfiguration

Commerce bietet viele Einstellungen und Tools, mit denen Sie die Antwortzeit auf den Seiten verbessern und einen höheren Durchsatz erzielen können.

## Cron-Aufträge

Alle asynchronen Vorgänge in [!DNL Commerce] werden mit dem Linux-`cron`-Befehl ausgeführt. Siehe [Konfigurieren und Ausführen von cron](../configuration/cli/configure-cron-jobs.md), um es korrekt zu konfigurieren.

## Indexer

Ein Indexer kann im **[!UICONTROL Update on Save]**- oder **[!UICONTROL Update on Schedule]** ausgeführt werden. Der **[!UICONTROL Update on Save]** indiziert sofort, wenn sich Ihr Katalog oder andere Daten ändern. Dieser Modus setzt eine niedrige Intensität von Aktualisierungs- und Browservorgängen in Ihrem Store voraus. Dies kann zu erheblichen Verzögerungen und Datenausfällen bei hoher Auslastung führen. Es wird empfohlen **aus Leistungsgründen „Planmäßig aktualisieren** zu verwenden, da Informationen zu Datenaktualisierungen gespeichert werden und die Indexierung anteilig im Hintergrund über einen bestimmten Cron-Auftrag durchgeführt wird. Sie können den Modus jedes [!DNL Commerce] Indexers separat auf der Seite **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** ändern. Der [!UICONTROL Customer Grid]-Index muss immer auf den **[!UICONTROL Update on Save]**-Modus eingestellt sein.

>[!TIP]
>
>Die Neuindizierung auf MariaDB 10.4 und 10.6 dauert im Vergleich zu anderen MariaDB- oder [!DNL MySQL]-Versionen länger. Wir empfehlen, die standardmäßige MariaDB-Konfigurationseinstellung zu ändern, die unter [&#x200B; beschrieben wird](../installation/prerequisites/database/mysql.md).

## Caches

Wenn Sie Ihren Store in der Produktion starten, aktivieren Sie alle Caches auf der Seite **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** . Wir empfehlen dringend die Verwendung von [!DNL Varnish], da es sich um eine effiziente Produktions-Seiten-Cache-Lösung handelt.

## Asynchrone E-Mail-Benachrichtigungen

Durch Aktivierung der Einstellung „Asynchrone E-Mail-Benachrichtigungen“ werden Prozesse, die E-Mail-Benachrichtigungen zur Checkout- und Bestellverarbeitung verarbeiten, in den Hintergrund verschoben. Um diese Funktion zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails) im _Admin_ Benutzerhandbuch.

## Asynchrone Auftragsdatenverarbeitung

Es kann vorkommen, dass intensive Verkäufe an einer Storefront gleichzeitig mit der intensiven Auftragsverarbeitung durch [!DNL Commerce] erfolgen. Sie können [!DNL Commerce] so konfigurieren, dass diese beiden Traffic-Muster auf Datenbankebene unterschieden werden, um Konflikte zwischen Lese- und Schreibvorgängen in den entsprechenden Tabellen zu vermeiden. Sie können Bestelldaten asynchron speichern und indizieren. Bestellungen werden temporär gespeichert und ohne Kollisionen stapelweise in das Order Management-Raster verschoben. Sie können diese Option unter **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]** aktivieren. Weitere Informationen finden [&#x200B; unter „Geplante &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing)&quot; im _Admin_ Benutzerhandbuch.

>[!WARNING]
>
>Die Registerkarte &quot;**[!UICONTROL Developer]**&quot; und die Optionen sind nur im [Entwicklermodus“ &#x200B;](../configuration/cli/set-mode.md). [Adobe Commerce in der Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)Infrastruktur unterstützt den `Developer` nicht.

## Asynchrone Konfiguration speichern

Bei Projekten mit einer großen Anzahl von Konfigurationen auf Store-Ebene kann das Speichern einer Store-Konfiguration übermäßig viel Zeit in Anspruch nehmen oder zu einer Zeitüberschreitung führen. Das _Async Config_-Modul ermöglicht asynchrone Konfigurationsspeicherungen durch Ausführen eines Cron-Auftrags, der einen Verbraucher verwendet, um das Speichern in einer Nachrichtenwarteschlange zu verarbeiten. AsyncConfig ist **deaktiviert** standardmäßig.

Sie können AsyncConfig über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --config-async 1
```

Der Befehl `set` schreibt Folgendes in die `app/etc/env.php`:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Starten Sie den folgenden Verbraucher, um mit der Verarbeitung der Nachrichten in der Warteschlange zu beginnen, und zwar nach dem Prinzip „first-in-first-out“:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Zurückgestellte Aktienaktualisierung

In Zeiten intensiver Verkäufe können [!DNL Commerce] Lageraktualisierungen im Zusammenhang mit Bestellungen aufschieben. Dies minimiert die Anzahl der Vorgänge und beschleunigt den Bestellvorgang. Diese Option ist jedoch riskant und kann nur verwendet werden, wenn Nachbestellungen im Geschäft aktiviert sind, da diese Option zu negativen Lagermengen führen kann. Diese Option kann zu erheblichen Leistungsverbesserungen bei Checkout-Flüssen für Geschäfte führen, die ihren Bestand bei Bedarf einfach nachfüllen können. Um verzögerte Stock-Updates auf Ihrer Site zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Weitere Informationen [&#x200B; Sie &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) _Adobe Commerce-Benutzerhandbuch_ unter Verwalten des Inventars.

>[!INFO]
>
>Diese Option ist nur verfügbar, wenn **[!UICONTROL Backorder with any mode]** aktiviert ist.

>[!INFO]
>
>Diese Option funktioniert auch mit [asynchroner Auftragserteilung](high-throughput-order-processing.md#asynchronous-order-placement) in Kombination mit [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Client-seitige Optimierungseinstellungen

Um die Reaktionsfähigkeit Ihrer [!DNL Commerce]-Instanz zu verbessern, wechseln Sie zum Administrator im Standard- oder Entwicklermodus und ändern Sie die folgenden Einstellungen:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Gruppe Einstellungen | Einstellung | Wert |
| ------------------- | -------------------------- | ------ |
| Rastereinstellungen | Asynchrone Indizierung | Aktivieren |
| CSS-Einstellungen | Minimieren von CSS-Dateien | Ja |
| [!DNL JavaScript] | Minimieren von [!DNL JavaScript] | Ja |
| [!DNL JavaScript] | [!DNL JavaScript] aktivieren | Ja |
| Vorlageneinstellungen | HTML minimieren | Ja |

>[!INFO]
>
>Die Registerkarte &quot;**[!UICONTROL Developer]**&quot; und die Optionen sind nur im [Entwicklermodus“ &#x200B;](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] on Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) unterstützt den `Developer` nicht.

Wenn Sie die Option &quot;**[!UICONTROL Enable [!DNL JavaScript] Bundling]**&quot; aktivieren, lassen Sie zu, dass Commerce alle JS-Ressourcen zu einem oder mehreren Bundles zusammenführt, die in Storefront-Seiten geladen werden. Die Bündelung von JS führt zu weniger Anfragen an den Server, was die Seitenleistung verbessert. Dies hilft dem Browser auch, JS-Ressourcen beim ersten Aufruf zwischenzuspeichern und sie für alle weiteren Suchvorgänge wiederzuverwenden. Diese Option bietet auch eine verzögerte Auswertung, da alle JS als Text geladen werden. Sie initiiert die Analyse und Auswertung des Codes erst, nachdem bestimmte Aktionen auf der Seite ausgelöst wurden. Diese Einstellung wird jedoch nicht für Stores empfohlen, in denen die Ladezeit der ersten Seite äußerst kritisch ist, da der gesamte JS-Inhalt beim ersten Aufruf geladen wird.

>[!INFO]
>
>Weitere [&#x200B; zur Optimierung von CSS &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/optimize-css-js-files) JavaScript finden Sie unter „Optimieren von Ressourcendateien“.

### Tipps zur Bündelung

* Es wird empfohlen, Tools von Drittanbietern für die Minimierung und Bündelung zu verwenden (z. B. [.js](https://requirejs.org/)). [!DNL Commerce] integrierten Mechanismen sind nicht optimal und werden als Ausweichalternativen bereitgestellt.
* Die Aktivierung des HTTP/2-Protokolls kann eine gute Alternative zur Verwendung des JS-Bundles sein. Das Protokoll bietet viele der gleichen Vorteile. Sie ist in Adobe Commerce standardmäßig für Cloud-Infrastrukturprojekte aktiviert.
* Es wird nicht empfohlen, veraltete Einstellungen wie das Zusammenführen von JS- und CSS-Dateien zu verwenden, da sie nur für synchron geladene JS im Abschnitt &quot;HEAD&quot; der Seite entwickelt wurden. Die Verwendung dieser Technik kann zu einer fehlerhaften Bündelung führen und erfordert, dass die JS-Logik nicht korrekt funktioniert.

## Validierung von Kundensegmenten

Händler, die über eine große Anzahl von [Kundensegmenten](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) verfügen, können durch Kundenaktionen, wie z. B. die Kundenanmeldung und das Hinzufügen von Produkten zum Warenkorb, eine erhebliche Leistungsbeeinträchtigung erfahren.

Kundenaktionen : Trigger eines Validierungsprozesses für Kundensegmente, der zu Leistungseinbußen führen kann. Standardmäßig validiert Adobe Commerce jedes Segment in Echtzeit, um zu definieren, welche Kundensegmente abgeglichen werden und welche nicht.

Um eine Leistungsbeeinträchtigung zu vermeiden, können Sie die **[!UICONTROL Real-time Check if Customer is Matched by Segment]** Systemkonfigurationsoption auf &quot;**&quot; setzen** um Kundensegmente durch eine einzelne kombinierte SQL-Abfrage zu validieren.

Um diese Optimierung zu aktivieren, navigieren Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Diese Einstellung verbessert die Leistung der Validierung von Kundensegmenten, wenn es viele Kundensegmente im System gibt. Dies funktioniert jedoch nicht mit Implementierungen [Split-Datenbank](../configuration/storage/multi-master.md) oder wenn keine registrierten Kunden vorhanden sind.

## Zeitplan für die Datenbankwartung {#database}

Es wird empfohlen, regelmäßige Datenbanksicherungen für Ihre Staging- und Produktionsinstanzen durchzuführen. Aufgrund der I/O-intensiven Natur von Backup-Vorgängen können langsamere Backups und potenzielle Probleme auftreten. Das gleichzeitige Ausführen von Datenbankprozessen für mehrere Umgebungen kann aufgrund von Konflikten bei den verfügbaren Ressourcen möglicherweise langsamer ausgeführt werden.

Um eine bessere Leistung zu erzielen, sollten Sie die Backups so planen, dass sie nacheinander, einzeln und zu Nebenzeiten ausgeführt werden. Durch diese Methode werden I/O-Konflikte vermieden und die Ausführungszeit verkürzt, insbesondere bei kleineren Instanzen, größeren Datenbanken usw.

Wir empfehlen beispielsweise, ein Backup der Produktionsdatenbank und anschließend die Staging-Datenbank zu planen, wenn die Stores weniger Besuche erleben.

## Anzahl der Produkte im Raster begrenzen

Um die Leistung des Produktrasters für große Kataloge zu verbessern, empfehlen wir, die Anzahl der Produkte im Raster mit der Einstellung **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** Systemkonfiguration zu begrenzen.

Diese Systemkonfigurationseinstellung ist standardmäßig deaktiviert. Durch Aktivierung können Sie die Anzahl der Produkte im Raster auf einen bestimmten Wert begrenzen. **[!UICONTROL Records Limit]** ist eine anpassbare Einstellung mit dem standardmäßigen Mindestwert `20000`.
Wenn die **[!UICONTROL Limit Number of Products in Grid]** aktiviert ist und die Anzahl der Produkte im Raster die Datensatzgrenze überschreitet, wird die begrenzte Sammlung von Datensätzen zurückgegeben. Wenn das Limit erreicht ist, werden die insgesamt gefundenen Datensätze, die Anzahl der ausgewählten Datensätze und die Paginierungselemente in der Rasterkopfzeile ausgeblendet.

Wenn die Gesamtzahl der Produkte im Raster begrenzt ist, wirkt sich dies nicht auf die Massenaktionen der Produktraster aus. Sie wirkt sich nur auf die Präsentationsebene des Produktrasters aus. Beispielsweise ist die Anzahl der `20000` Produkte im Raster begrenzt, der Benutzer klickt auf **[!UICONTROL Select All]**, wählt die Aktion „Masse **[!UICONTROL Update attributes]**&quot; aus und aktualisiert einige Attribute. Infolgedessen werden alle Produkte aktualisiert, nicht die begrenzte Sammlung von `20000`.

Die Begrenzung des Produktrasters betrifft nur Produktsammlungen, die von Benutzeroberflächenkomponenten verwendet werden. Daher sind nicht alle Produktraster von dieser Einschränkung betroffen. Nur diejenigen, die `Magento\Catalog\Ui\DataProvider\Product\ProductCollection` verwenden.
Produktrastersammlungen können nur auf den folgenden Seiten beschränkt werden:

* Katalog-Produktraster
* Verknüpftes Raster/Up-Sell-/Crosssell-Produktraster hinzufügen
* Produkte zum Produktpaket hinzufügen
* Produkte zu Produktgruppe hinzufügen
* Admin-Seite „Bestellung erstellen“

Wenn Ihr Produktraster nicht beschränkt werden soll, empfehlen wir Ihnen, Filter präziser zu verwenden, damit die Ergebnissammlung weniger Elemente als **[!UICONTROL Records Limit]** enthält.
