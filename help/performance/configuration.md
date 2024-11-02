---
title: Best Practices für die Konfiguration
description: Optimieren Sie die Reaktionszeit Ihrer Adobe Commerce-Bereitstellung mithilfe dieser Best Practices.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# Best Practices bei der Konfiguration

Commerce bietet viele Einstellungen und Tools, mit denen Sie die Reaktionszeit auf den Seiten verbessern und einen höheren Durchsatz erzielen können.

## Cron-Aufträge

Alle asynchronen Vorgänge in [!DNL Commerce] werden mit dem Linux `cron`-Befehl ausgeführt. Siehe [cron konfigurieren und ausführen](../configuration/cli/configure-cron-jobs.md) , um es korrekt zu konfigurieren.

## Indexer

Ein Indexer kann im Modus **[!UICONTROL Update on Save]** oder **[!UICONTROL Update on Schedule]** ausgeführt werden. Der Modus **[!UICONTROL Update on Save]** wird sofort indiziert, wenn sich Ihr Katalog oder andere Daten ändern. Dieser Modus setzt eine geringe Intensität von Aktualisierungs- und Browsing-Vorgängen in Ihrem Store voraus. Dies kann zu beträchtlichen Verzögerungen und zu einer Nichtverfügbarkeit der Daten bei hohen Lasten führen. Es wird empfohlen, **Auf Zeitplan aktualisieren** für Leistungszwecke zu verwenden, da dort Informationen über Datenaktualisierungen gespeichert werden und eine Indexierung nach Portionen im Hintergrund durch einen bestimmten Cron-Auftrag durchgeführt wird. Sie können den Modus jedes [!DNL Commerce]-Indexers separat auf der Konfigurationsseite **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** ändern. Der Index [!UICONTROL Customer Grid] muss immer auf den Modus **[!UICONTROL Update on Save]** eingestellt sein.

>[!TIP]
>
>Die Neuindizierung auf MariaDB 10.4 und 10.6 nimmt im Vergleich zu anderen MariaDB- oder [!DNL MySQL]-Versionen mehr Zeit in Anspruch. Wir empfehlen, die standardmäßige MariaDB-Konfigurationseinstellung zu ändern, die in den [Installationsvoraussetzungen](../installation/prerequisites/database/mysql.md) beschrieben wird.

## Caches

Wenn Sie Ihren Store in Produktion starten, aktivieren Sie alle Caches von der Seite **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** aus. Es wird dringend empfohlen, [!DNL Varnish] zu verwenden, da es sich um eine effiziente Lösung für den Zwischenspeicher von Produktionsseiten handelt.

## Asynchrone E-Mail-Benachrichtigungen

Durch Aktivierung der Einstellung &quot;Asynchrone E-Mail-Benachrichtigungen&quot;werden Prozesse, die E-Mail-Benachrichtigungen zum Checkout und zur Bestellverarbeitung verarbeiten, in den Hintergrund verschoben. Um diese Funktion zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Weitere Informationen finden Sie unter [E-Mails für Vertrieb](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails) im _Benutzerhandbuch für Administratoren_.

## Asynchrone Auftragsdatenverarbeitung

Es kann vorkommen, dass intensive Verkäufe an eine Storefront gleichzeitig erfolgen, während [!DNL Commerce] eine intensive Auftragsverarbeitung durchführt. Sie können [!DNL Commerce] so konfigurieren, dass diese beiden Traffic-Muster auf Datenbankebene unterschieden werden, um Konflikte zwischen Lese- und Schreibvorgängen in den entsprechenden Tabellen zu vermeiden. Sie können Bestelldaten asynchron speichern und indizieren. Bestellungen werden temporär gespeichert und ohne Kollisionen stapelweise in das Order Management-Raster verschoben. Sie können diese Option von **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]** aktivieren. Weitere Informationen finden Sie unter [Geplante Rasteraktualisierungen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) im _Benutzerhandbuch für Administratoren_.

>[!WARNING]
>
>Die Registerkarte **[!UICONTROL Developer]** und die Optionen sind nur im [Entwicklermodus](../configuration/cli/set-mode.md) verfügbar. [Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) unterstützt den `Developer` -Modus nicht.

## Speichern Sie die asynchrone Konfiguration

Bei Projekten mit einer großen Anzahl von Konfigurationen auf Store-Ebene kann das Speichern einer Store-Konfiguration eine übermäßige Zeit in Anspruch nehmen oder zu einem Timeout führen. Das Modul _Async Config_ ermöglicht asynchrone Konfigurationseinstellungen, indem ein Cron-Auftrag ausgeführt wird, der mithilfe eines Verbrauchers das Speichern in einer Nachrichtenwarteschlange verarbeitet. AsyncConfig ist standardmäßig **disabled**.

Sie können AsyncConfig über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --config-async 1
```

Der Befehl `set` schreibt Folgendes in die Datei `app/etc/env.php`:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Starten Sie den folgenden Kunden, um die Verarbeitung der Nachrichten in der Warteschlange auf der Basis des First-in-First-Out zu starten:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Zurückgestellte Bestandsaktualisierung

In Zeiten intensiver Umsätze kann [!DNL Commerce] Lageraktualisierungen im Zusammenhang mit Bestellungen zurückstellen. Dadurch wird die Anzahl der Vorgänge minimiert und der Bestellplatzierungsprozess beschleunigt. Diese Option ist jedoch riskant und kann nur verwendet werden, wenn im Speicher Rückorder aktiviert sind, da diese Option zu negativen Lagermengen führen kann. Diese Option kann zu einer deutlichen Leistungsverbesserung der Checkout-Flüsse für Stores führen, die ihren Lagerbestand bei Bedarf einfach wieder auffüllen können. Um verzögerte Lageraktualisierungen auf Ihrer Site zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Weitere Informationen finden Sie unter [Verwalten des Bestands](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) im _Adobe Commerce-Benutzerhandbuch_ .

>[!INFO]
>
>Diese Option ist nur verfügbar, wenn **[!UICONTROL Backorder with any mode]** aktiviert ist.

>[!INFO]
>
>Diese Option funktioniert auch mit der asynchronen Auftragsplatzierung ](high-throughput-order-processing.md#asynchronous-order-placement) in Kombination mit [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).[

## Einstellungen zur clientseitigen Optimierung

Um die Reaktionsfähigkeit Ihrer [!DNL Commerce] -Instanz im Storefront zu verbessern, wechseln Sie im Standard- oder Entwicklermodus zum Admin und ändern Sie die folgenden Einstellungen:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Einstellungsgruppe | Einstellung | Wert |
| ------------------- | -------------------------- | ------ |
| Rastereinstellungen | Asynchrone Indizierung | Aktivieren |
| CSS-Einstellungen | Minimieren von CSS-Dateien | Ja |
| [!DNL JavaScript] Einstellungen | Minimieren von [!DNL JavaScript] Dateien | Ja |
| [!DNL JavaScript] Einstellungen | Aktivieren des Bundles [!DNL JavaScript] | Ja |
| Vorlageneinstellungen | Minimieren von HTML | Ja |

>[!INFO]
>
>Die Registerkarte **[!UICONTROL Developer]** und die Optionen sind nur im [Entwicklermodus](../configuration/cli/set-mode.md) verfügbar. [Adobe [!DNL Commerce] in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) unterstützt den `Developer` -Modus nicht.

Wenn Sie die Option &quot;**[!UICONTROL Enable [!DNL JavaScript] Bundling]**&quot;aktivieren, gestatten Sie Commerce, alle JS-Ressourcen zu einem oder mehreren Bundles zusammenzuführen, die in Storefront-Seiten geladen werden. Das Bundling von JS führt zu weniger Anforderungen an den Server, was die Seitenleistung verbessert. Es hilft auch dem Browser, JS-Ressourcen beim ersten Aufruf zwischenzuspeichern und sie für alle weiteren Browser wiederzuverwenden. Diese Option bringt auch eine verzögerte Auswertung mit sich, da alle JS als Text geladen werden. Sie initiiert die Analyse und Auswertung von Code erst, nachdem bestimmte Aktionen auf der Seite ausgelöst wurden. Diese Einstellung wird jedoch nicht für Stores empfohlen, bei denen die erste Seitenladezeit äußerst wichtig ist, da der gesamte JS-Inhalt beim ersten Aufruf geladen wird.

>[!INFO]
>
>Weitere Informationen zur Optimierung von CSS und JavaScript finden Sie unter [CSS- und JavaScript-Dateioptimierung für Adobe Commerce in der Cloud-Infrastruktur und Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) im Adobe Commerce Help Center_ .

### Bundle-Tipps

* Wir empfehlen die Verwendung von Drittanbieter-Tools für die Minimierung und das Bundling (z. B. [r.js](https://requirejs.org/)). [!DNL Commerce] integrierte Mechanismen sind nicht optimal und werden als Ausweichalternativen bereitgestellt.
* Die Aktivierung des HTTP/2-Protokolls kann eine gute Alternative zur Verwendung des JS-Bundles sein. Das Protokoll bietet viele der gleichen Vorteile. Sie ist in Adobe Commerce bei Cloud-Infrastrukturprojekten standardmäßig aktiviert.
* Es wird empfohlen, keine veralteten Einstellungen wie das Zusammenführen von JS- und CSS-Dateien zu verwenden, da diese nur für synchron geladene JS im HEAD-Abschnitt der Seite entwickelt wurden. Die Verwendung dieser Technik kann dazu führen, dass die Logik &quot;Bundling&quot;und &quot;requireJS&quot;fehlerhaft funktioniert.

## Validierung von Kundensegmenten

Bei Händlern mit einer großen Anzahl von [Kundensegmenten](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) kann die Leistung durch Kundenaktionen wie die Kundenanmeldung und das Hinzufügen von Produkten zum Warenkorb erheblich beeinträchtigt werden.

Kundenaktionen Trigger eines Validierungsprozesses für Kundensegmente, der zu Leistungsbeeinträchtigungen führen kann. Standardmäßig validiert Adobe Commerce jedes Segment in Echtzeit, um zu definieren, welche Kundensegmente abgeglichen werden und welche nicht.

Um Leistungsbeeinträchtigungen zu vermeiden, können Sie die Systemkonfigurationsoption **[!UICONTROL Real-time Check if Customer is Matched by Segment]** auf **Nein** setzen, um Kundensegmente anhand einer einzigen kombinierten SQL-Abfrage zu validieren.

Um diese Optimierung zu aktivieren, gehen Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Diese Einstellung verbessert die Leistung der Validierung von Kundensegmenten, wenn das System viele Kundensegmente enthält. Es funktioniert jedoch nicht mit [split database](../configuration/storage/multi-master.md) -Implementierungen oder wenn keine registrierten Kunden vorhanden sind.

## Zeitplan für die Datenbankwartung {#database}

Es wird empfohlen, regelmäßige Datenbanksicherungen für Ihre Staging- und Produktionsinstanzen durchzuführen. Aufgrund der I/O-intensiven Natur von Sicherungsvorgängen können Sie auf langsamere Backups und potenzielle Probleme stoßen. Das gleichzeitige Ausführen von Datenbankprozessen für mehrere Umgebungen kann aufgrund von Konflikten um verfügbare Ressourcen möglicherweise langsamer ablaufen.

Planen Sie für eine bessere Leistung nacheinander die Ausführung Ihrer Sicherungen zu Zeiten außerhalb der Spitzenzeiten. Diese Methode vermeidet E/A-Konflikte und verkürzt die Fertigstellungszeit, insbesondere für kleinere Instanzen, größere Datenbanken usw.

Beispielsweise wird empfohlen, eine Sicherung Ihrer Produktionsdatenbank und danach die Staging-Datenbank zu planen, wenn Ihre Stores auf geringere Besuche stoßen.

## Anzahl der Produkte im Raster begrenzen

Um die Leistung des Produktrasters für große Kataloge zu verbessern, empfehlen wir, die Anzahl der Produkte im Raster mit der Systemkonfigurationseinstellung **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** zu begrenzen.

Diese Systemkonfigurationseinstellung ist standardmäßig deaktiviert. Durch Aktivierung dieser Option können Sie die Anzahl der Produkte im Raster auf einen bestimmten Wert begrenzen. **[!UICONTROL Records Limit]** ist eine anpassbare Einstellung mit einem Standardwert von mindestens `20000`.
Wenn die Einstellung **[!UICONTROL Limit Number of Products in Grid]** aktiviert ist und die Anzahl der Produkte im Raster größer als die Datensatzgrenze ist, wird die begrenzte Sammlung von Datensätzen zurückgegeben. Bei Erreichen des Grenzwerts werden die gefundenen Datensätze insgesamt, die Anzahl der ausgewählten Datensätze und die Paginierungselemente aus dem Rasterheader ausgeblendet.

Wenn die Gesamtanzahl der Produkte im Raster begrenzt ist, wirkt sich dies nicht auf Massenaktionen im Produktraster aus. Dies betrifft nur die Darstellungsschicht des Produktraster. Beispielsweise gibt es eine begrenzte Anzahl von `20000` Produkten im Raster, der Benutzer klickt auf **[!UICONTROL Select All]**, wählt die Aktion für die Masse **[!UICONTROL Update attributes]** aus und aktualisiert einige Attribute. Daher werden alle Produkte aktualisiert, nicht die begrenzte Sammlung von `20000` -Datensätzen.

Die Produktrasterbegrenzung betrifft nur Produktsammlungen, die von Benutzeroberflächen-Komponenten verwendet werden. Daher sind nicht alle Produktraster von dieser Einschränkung betroffen. Nur diejenigen, die `Magento\Catalog\Ui\DataProvider\Product\ProductCollection` verwenden.
Sie können Produktraster-Sammlungen nur auf den folgenden Seiten einschränken:

* Katalog-Produktraster
* Hinzufügen von verknüpften/Up-Sell-/Cross-Sell-Produkten-Raster
* Produkte zum Bundle-Produkt hinzufügen
* Produkte zum Gruppenprodukt hinzufügen
* Admin-Bestellseite erstellen

Wenn Sie nicht möchten, dass Ihr Produktraster eingeschränkt wird, empfehlen wir Ihnen, Filter präziser zu verwenden, damit die Ergebnissammlung weniger Elemente als **[!UICONTROL Records Limit]** enthält.
