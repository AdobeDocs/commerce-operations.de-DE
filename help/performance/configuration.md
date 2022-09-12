---
title: Best Practices für die Konfiguration
description: Optimieren Sie die Reaktionszeit Ihrer Adobe Commerce- oder Magento Open Source-Bereitstellung mithilfe dieser Best Practices.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---


# Best Practices bei der Konfiguration

Commerce bietet viele Einstellungen und Tools, mit denen Sie die Reaktionszeit auf den Seiten verbessern und einen höheren Durchsatz erzielen können.

## Cron-Aufträge

Alle asynchronen Vorgänge in [!DNL Commerce] werden mit Linux ausgeführt `cron` Befehl. Siehe [Cron konfigurieren und ausführen](../configuration/cli/configure-cron-jobs.md) , um sie korrekt zu konfigurieren.

## Indexer

Ein Indexer kann in **[!UICONTROL Update on Save]** oder **[!UICONTROL Update on Schedule]** -Modus. Die **[!UICONTROL Update on Save]** sofort indiziert werden, wenn sich Ihr Katalog oder andere Daten ändern. Dieser Modus setzt eine geringe Intensität von Aktualisierungs- und Browsing-Vorgängen in Ihrem Store voraus. Dies kann zu beträchtlichen Verzögerungen und zu einer Nichtverfügbarkeit der Daten bei hohen Lasten führen. Wir empfehlen, **Planmäßig aktualisieren** -Modus in der Produktion verwendet werden, da dort Informationen über Datenaktualisierungen gespeichert werden und die Indizierung anhand von Teilen im Hintergrund über einen bestimmten Cron-Auftrag durchgeführt wird. Sie können den Modus der einzelnen [!DNL Commerce] Indexer separat auf der  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** Konfigurationsseite.

Die Neuindizierung auf MariaDB 10.4 nimmt im Vergleich zu anderen MariaDB mehr Zeit in Anspruch. [!DNL MySQL] Versionen. Als Problemumgehung empfehlen wir, die standardmäßige MariaDB-Konfiguration zu ändern und die folgenden Parameter festzulegen:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Caches

Wenn Sie Ihren Store in Produktion starten, aktivieren Sie alle Caches aus dem **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** Seite. Es wird dringend empfohlen, [!DNL Varnish], da es sich um eine effiziente Lösung für den Zwischenspeicher von Produktionsseiten handelt.

## Asynchrone E-Mail-Benachrichtigungen

Durch Aktivierung der Einstellung &quot;Asynchrone E-Mail-Benachrichtigungen&quot;werden Prozesse, die E-Mail-Benachrichtigungen zum Checkout und zur Bestellverarbeitung verarbeiten, in den Hintergrund verschoben. Um diese Funktion zu aktivieren, navigieren Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Siehe [Verkaufs-E-Mails](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) im _Magento Open Source-Benutzerhandbuch_ für weitere Informationen.

## Asynchrone Auftragsdatenverarbeitung

Es kann vorkommen, dass intensive Verkäufe an eine Storefront gleichzeitig mit [!DNL Commerce] führt eine intensive Auftragsverarbeitung durch. Sie können [!DNL Commerce] um diese beiden Traffic-Muster auf Datenbankebene zu unterscheiden, um Konflikte zwischen Lese- und Schreibvorgängen in den entsprechenden Tabellen zu vermeiden. Sie können Bestelldaten asynchron speichern und indizieren. Bestellungen werden temporär gespeichert und ohne Kollisionen stapelweise in das Order Management-Raster verschoben. Sie können diese Option aktivieren, indem Sie **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Siehe [Geplante Rasteraktualisierungen](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) im _Magento Open Source-Benutzerhandbuch_ für weitere Informationen.

>[!WARNING]
>
>Die **[!UICONTROL Developer]** Registerkarten und Optionen sind nur in [Entwicklermodus](../configuration/cli/set-mode.md). [Adobe Commerce auf Cloud-Infrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) unterstützt nicht `Developer` -Modus.

## Zurückgestellte Bestandsaktualisierung

In Zeiten intensiver Verkäufe, [!DNL Commerce] kann Lageraktualisierungen im Zusammenhang mit Bestellungen zurückstellen. Dadurch wird die Anzahl der Vorgänge minimiert und der Bestellplatzierungsprozess beschleunigt. Diese Option ist jedoch riskant und kann nur verwendet werden, wenn im Speicher Rückorder aktiviert sind, da diese Option zu negativen Lagermengen führen kann. Diese Option kann zu einer deutlichen Leistungsverbesserung der Checkout-Flüsse für Stores führen, die ihren Lagerbestand bei Bedarf einfach wieder auffüllen können. Um verzögerte Lageraktualisierungen auf Ihrer Site zu aktivieren, navigieren Sie zu **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Siehe [Verwalten des Bestands](https://docs.magento.com/user-guide/catalog/inventory.html) im _Adobe Commerce-Benutzerhandbuch_ für weitere Informationen.

>[!INFO]
>
>Diese Option ist nur verfügbar, wenn **[!UICONTROL Backorder with any mode]** aktiviert ist.

## Einstellungen zur clientseitigen Optimierung

So verbessern Sie die Reaktionsfähigkeit Ihrer Storefront [!DNL Commerce] Wechseln Sie im Modus Standard oder Entwickler zum Admin und ändern Sie die folgenden Einstellungen:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Einstellungsgruppe | Einstellung | Wert |
| ------------------- | -------------------------- | ------ |
| Rastereinstellungen | Asynchrone Indizierung | Aktivieren |
| CSS-Einstellungen | Minimieren von CSS-Dateien | Ja |
| [!DNL JavaScript] Einstellungen | Minimieren [!DNL JavaScript] Dateien | Ja |
| [!DNL JavaScript] Einstellungen | Aktivieren [!DNL JavaScript] Bundle | Ja |
| Vorlageneinstellungen | Minimieren von HTML | Ja |

>[!INFO]
>
>Die **[!UICONTROL Developer]** Registerkarten und Optionen sind nur in [Entwicklermodus](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] zur Cloud-Infrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) unterstützt nicht `Developer` -Modus.

Wenn Sie die **[!UICONTROL Enable [!DNL JavaScript] Bundling]** können Sie Commerce alle JS-Ressourcen in einem oder mehreren Bundles zusammenführen, die in Storefront-Seiten geladen werden. Das Bundling von JS führt zu weniger Anforderungen an den Server, was die Seitenleistung verbessert. Es hilft auch dem Browser, JS-Ressourcen beim ersten Aufruf zwischenzuspeichern und sie für alle weiteren Browser wiederzuverwenden. Diese Option bringt auch eine verzögerte Auswertung mit sich, da alle JS als Text geladen werden. Sie initiiert die Analyse und Auswertung von Code erst, nachdem bestimmte Aktionen auf der Seite ausgelöst wurden. Diese Einstellung wird jedoch nicht für Stores empfohlen, bei denen die erste Seitenladezeit äußerst wichtig ist, da der gesamte JS-Inhalt beim ersten Aufruf geladen wird.

>[!INFO]
>
>Siehe [CSS- und JavaScript-Dateioptimierung in Adobe Commerce auf Cloud-Infrastruktur und Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) im Adobe Commerce Help Center_ finden Sie weitere Informationen zur Optimierung von CSS und JavaScript.

### Bundle-Tipps

* Wir empfehlen die Verwendung von Drittanbieter-Tools für die Minimierung und das Bundling (wie [r.js](https://requirejs.org/)). [!DNL Commerce] integrierte Mechanismen sind nicht optimal und werden als Ausweichalternativen bereitgestellt.
* Die Aktivierung des HTTP2-Protokolls kann eine gute Alternative zur Verwendung des JS-Bundles sein. Das Protokoll bietet fast die gleichen Vorteile.
* Es wird empfohlen, keine veralteten Einstellungen wie das Zusammenführen von JS- und CSS-Dateien zu verwenden, da diese nur für synchron geladene JS im HEAD-Abschnitt der Seite entwickelt wurden. Die Verwendung dieser Technik kann dazu führen, dass die Logik &quot;Bundling&quot;und &quot;requireJS&quot;fehlerhaft funktioniert.

## Zeitplan für die Datenbankwartung {#database}

Es wird empfohlen, regelmäßige Datenbanksicherungen für Ihre Staging- und Produktionsinstanzen durchzuführen. Aufgrund der I/O-intensiven Natur von Sicherungsvorgängen können Sie auf langsamere Backups und potenzielle Probleme stoßen. Das gleichzeitige Ausführen von Datenbankprozessen für mehrere Umgebungen kann aufgrund von Konflikten um verfügbare Ressourcen möglicherweise langsamer ablaufen.

Planen Sie für eine bessere Leistung nacheinander die Ausführung Ihrer Sicherungen zu Zeiten außerhalb der Spitzenzeiten. Diese Methode vermeidet E/A-Konflikte und verkürzt die Fertigstellungszeit, insbesondere für kleinere Instanzen, größere Datenbanken usw.

Beispielsweise wird empfohlen, eine Sicherung Ihrer Produktionsdatenbank und danach die Staging-Datenbank zu planen, wenn Ihre Stores auf geringere Besuche stoßen.
