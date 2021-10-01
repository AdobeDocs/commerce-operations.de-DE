---
title: AEM Leistungsoptimierung
description: Optimieren Sie Ihre standardmäßige Adobe Experience Manager-Konfiguration, um eine hohe Belastung von Adobe Commerce zu unterstützen.
source-git-commit: 6ad72d5110ae3e3a7cf341282f2af9b700874f09
workflow-type: tm+mt
source-wordcount: '2253'
ht-degree: 0%

---


# AEM Leistungsoptimierungen unter Last von Standardkonfigurationen

Der AEM Dispatcher ist ein Reverse-Proxy, mit dem eine Umgebung bereitgestellt werden kann, die sowohl schnell als auch dynamisch ist. Es funktioniert als Teil eines statischen HTML-Servers, wie z. B. Apache HTTP Server, mit dem Ziel, einen möglichst großen Teil des Site-Inhalts in Form von statischen Ressourcen zu speichern (oder &quot;zwischenspeichern&quot;). Dieser Ansatz soll die Notwendigkeit minimieren, so weit wie möglich auf die Rendering-Funktion der AEM und den Commerce-GraphQL-Dienst der Adobe zuzugreifen. Das Ergebnis der Bereitstellung eines Großteils der Seiten als statisches HTML, CSS und JS bietet Benutzern Leistungsvorteile und reduziert die Infrastrukturanforderungen in der Umgebung. Jede Seite oder Abfrage, die von Benutzer zu Benutzer mit hoher Wahrscheinlichkeit identisch wiederholt wird, sollte für die Zwischenspeicherung berücksichtigt werden.

Die folgenden Abschnitte zeigen auf hoher Ebene den empfohlenen technischen Fokusbereich, der überprüft werden soll, um eine effektive Zwischenspeicherung auf AEM in einer CIF/Adobe Commerce-Umgebung zu ermöglichen.

## TTL-basierte Zwischenspeicherung auf AEM Dispatcher

Das Caching eines möglichst großen Teils der Website auf den Dispatchern ist Best Practice für AEM Projekt. Durch die Verwendung der zeitbasierten Cache-Invalidierung werden serverseitig gerenderte CIF-Seiten für eine bestimmte begrenzte Zeit zwischengespeichert. Nachdem die festgelegte Zeit abgelaufen ist, erstellt die nächste Anfrage die Seite aus dem AEM Publisher und Adobe Commerce GraphQL neu und speichert sie bis zur nächsten Invalidierung erneut im Dispatcher-Cache.

Die TTL-Caching-Funktion kann in AEM mit der Verwendung der &quot;Dispatcher TTL&quot;-Komponente innerhalb des ACS AEM Commons-Pakets und der Einstellung /enableTTL &quot;1&quot;in der Konfigurationsdatei dispatcher.any konfiguriert werden.

Wenn diese Option aktiviert ist, bewertet der Dispatcher die Antwortheader aus dem Backend. Wenn sie ein maximales Alter von Cache-Control oder ein Ablaufdatum enthalten, wird eine leere Hilfsdatei neben der Cachedatei erstellt, deren Änderungszeitpunkt dem Ablaufdatum entspricht. Wenn die zwischengespeicherte Datei nach dem Änderungszeitpunkt angefordert wird, wird sie automatisch erneut vom Backend angefordert. Dies bietet einen wirksamen Caching-Mechanismus, der kein manuelles Eingreifen oder keine Wartung erfordert, sobald die Produktaktualisierungsverzögerung (TTL) von den Interessenträgern im Unternehmen anerkannt und akzeptiert wurde.

## Browser-Zwischenspeicherung

Der oben beschriebene Dispatcher-TTL-Ansatz reduziert die Anforderungen und lädt auf den Publisher. Es gibt jedoch einige Assets, die sich sehr wahrscheinlich nicht ändern werden. Daher können sogar Anforderungen an den Dispatcher reduziert werden, indem relevante Dateien lokal im Browser eines Benutzers zwischengespeichert werden. Beispielsweise muss das Logo der Site, das auf jeder Seite der Site in der Site-Vorlage angezeigt wird, nicht jedes Mal an den Dispatcher angefordert werden. Dies kann stattdessen im Browser-Cache des Benutzers gespeichert werden. Die Verringerung der Bandbreitenanforderungen für jedes Laden von Seiten hätte einen großen Einfluss auf die Reaktionsschnelligkeit der Website und die Seitenladezeiten.

Die Zwischenspeicherung auf Browserebene erfolgt normalerweise über die &quot;Cache-Control: max-age=&quot; Antwort-Header. Die Maxage-Einstellung teilt dem Browser mit, für wie viele Sekunden die Datei zwischengespeichert werden soll, bevor er versucht, sie erneut zu &quot;überprüfen&quot;oder von der Site anzufordern. Dieses Konzept der Cache-Maximaldauer wird häufig als &quot;Cache Expiration&quot;oder TTL (&quot;Time to Live&quot;) bezeichnet. Skaliertes Bereitstellen von Commerce-Erlebnissen - Mit Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Zu den Bereichen einer AEM/CIF/Adobe Commerce-Site, die im Browser des Kunden zwischengespeichert werden können, gehören:

- Bilder (innerhalb der AEM-Vorlage selbst, z. B. Website-Logo und Vorlagenentwurfsbilder - Katalogproduktbilder werden von Adobe Commerce über Fastly aufgerufen, die Zwischenspeicherung dieser Bilder wird später erläutert)
- HTML-Dateien (für selten geänderte Seiten - Seiten mit Nutzungsbedingungen usw.)
- CSS-Dateien
- Alle Site-JavaScript-Dateien - einschließlich CIF-JavaScript-Dateien

## Optimierung der Dispatcher-Statusebene und Übergangsphase

Die standardmäßige Dispatcher-Konfiguration verwendet die Einstellung /statfilelevel &quot;0&quot;. Das bedeutet, dass eine einzelne &quot;.stat&quot;-Datei im Stammverzeichnis von htdocs (Basisverzeichnis des Dokuments) gespeichert wird. Wenn eine Seite oder Datei in AEM geändert wird, wird die Änderungszeit dieser einzelnen stat-Datei auf den Zeitpunkt der Änderung aktualisiert. Wenn die Zeit kürzer ist als die Bearbeitungszeit der Ressource, berücksichtigt der Dispatcher, dass alle Ressourcen invalidiert wurden und jede nachfolgende Anforderung einer invalidierten Ressource einen Aufruf an die Veröffentlichungsinstanz Trigger. Mit dieser Einstellung wird also bei jeder Aktivierung der gesamte Cache invalidiert.

Für jede Site, insbesondere Commerce-Sites mit hoher Auslastung, würde dies eine unnötige Menge an Last auf die AEM-Veröffentlichungsstufe bringen, damit die gesamte Site-Struktur mit nur einer einzelnen Seitenaktualisierung ungültig gemacht wird.

Stattdessen kann die Einstellung statfilelevel in einen höheren Wert geändert werden, der der Tiefe der Unterverzeichnisse im htdocs-Verzeichnis aus dem Basisverzeichnis des Dokuments entspricht. Wenn eine Datei auf einer bestimmten Ebene invalidiert wird, werden nur Dateien auf dieser .stat-Ordnerebene und darunter aktualisiert.

Beispiel: Nehmen wir an, Sie haben eine Produktseitenvorlage unter:

```
content/ecommerce/us/en/products/product-page.html
```

Jede Ordnerebene hätte eine &quot;stat-Ebene&quot;- wie in der obigen Tabelle aufgeschlüsselt dargestellt.

| Inhalt (Basisverzeichnis) | E-Commerce | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 3 | 2 | 3 | 4 | - |

Wenn Sie in diesem Fall die statfilelevel-Eigenschaft auf den Standardwert &quot;0&quot;gesetzt hatten und die Vorlage &quot;product-page.html&quot;aktualisiert und aktiviert wurde, wodurch eine Invalidierung ausgelöst wird, wird jede STAT-Datei vom Basisverzeichnis auf Ebene 4 berührt und Dateien werden invalidiert, wodurch eine weitere Anfrage von den AEM Veröffentlichungsinstanzen für alle Seiten der Site (einschließlich anderer Websites, Länder und Sprachen) von dieser Änderung verursacht wird.

Wenn die statfilelevel-Eigenschaft jedoch auf Ebene 4 festgelegt ist und eine Änderung an der Datei &quot;product-page.html&quot;vorgenommen wird, würde nur die STAT-Datei im Produktverzeichnis für diese bestimmte Website/Land/Sprache geändert.

Beachten Sie, dass die .stat-Dateiebene nicht auf ein zu hohes Niveau gesetzt werden sollte - mehr als 20 davon können Leistungseinbußen verursachen. Wenn Sie eine Massendatei-Aktivierung ausführen, während Sie einen Leistungstest durchführen, sollten Sie das richtige Level erhalten, auf das Sie Ihre stat-Ebene anpassen sollten.

Eine weitere Dispatcher-Einstellung, die beim Konfigurieren der statfilelevel-Einstellung optimiert werden soll, ist die Einstellung gracePeriod . Dies definiert die Anzahl der Sekunden, die eine veraltete, automatisch invalidierte Ressource nach der letzten Aktivierung weiterhin aus dem Cache bereitgestellt werden kann. Automatisch invalidierte Ressourcen werden durch jede Aktivierung invalidiert (wenn ihr Pfad mit dem Dispatcher/invalidate-Abschnitt und der in der statfileslevel-Eigenschaft angegebenen Ebene übereinstimmt). Wenn Sie die Einstellung gracePeriod auf 2 Sekunden festlegen, können Sie verhindern, dass ein Szenario mit mehreren Anfragen an den Herausgeber gesendet wird, auch wenn der Herausgeber noch dabei ist, die neue Seite zu erstellen.

>[!NOTE]
>
> Weitere detaillierte Informationen zu diesem Thema finden Sie im GitHub-Repository [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod).

## CIF - GraphQL-Zwischenspeicherung über Komponenten

Einzelne Komponenten in AEM können auf Zwischenspeicherung festgelegt werden, was bedeutet, dass die GraphQL-Anfrage an die Adobe
Commerce wird einmal aufgerufen und nachfolgende Anforderungen werden bis zum konfigurierten Zeitlimit aus dem AEM-Cache abgerufen und werden nicht weiter in Adobe Commerce geladen. Beispiele wären eine Site-Navigation basierend auf einem Kategorienbaum, der auf jeder Seite angezeigt wird, und Optionen innerhalb einer facettierten Suchfunktion. Dies sind nur zwei Bereiche, für die ressourcenintensive Abfragen zum Erstellen von Adobe Commerce erforderlich sind. Es wäre jedoch unwahrscheinlich, dass sie sich regelmäßig ändern, und wäre daher eine gute Wahl für die Zwischenspeicherung. Auf diese Weise würde beispielsweise die ressourcenintensive GraphQL-Anforderung für den Navigations-Build, selbst wenn eine PDP oder PLP vom Publisher neu erstellt wird, nicht den Adobe Commerce beeinträchtigen und könnte aus dem GraphQL-Cache auf AEM CIF abgerufen werden.

Ein Beispiel unten ist, dass die Navigationskomponente zwischengespeichert wird, da sie dieselbe GraphQL-Abfrage auf allen Seiten der Site sendet. Die folgende Anfrage speichert die letzten 100 Einträge für 10 Minuten für die Navigationsstruktur zwischen:

```
venia/components/structure/navigation:true:100:600
```

Im folgenden Beispiel werden die letzten 100 facettierten Suchoptionen auf einer Suchseite 1 Stunde lang zwischengespeichert:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

Die Anforderung einschließlich aller benutzerdefinierten HTTP-Header und -Variablen muss exakt übereinstimmen, damit der Cache &quot;Treffer&quot;erhält und ein erneuter Aufruf von Adobe Commerce verhindert wird. Es sollte darauf hingewiesen werden, dass es nach dem Festlegen nicht einfach ist, diesen Cache manuell zu invalidieren. Dies könnte bedeuten, dass beim Hinzufügen einer neuen Kategorie in Adobe Commerce diese erst dann in der Navigation angezeigt wird, wenn die im obigen Cache festgelegte Ablaufzeit abgelaufen ist und die GraphQL-Anforderung aktualisiert wurde. Dasselbe für Suchfacetten. Angesichts der Leistungsvorteile, die durch diese Zwischenspeicherung erzielt werden müssen, ist dies normalerweise ein akzeptabler Kompromiss.

Die obigen Zwischenspeicherungsoptionen können mithilfe der AEM OSGi-Konfigurationskonsole in &quot;GraphQL Client&quot;festgelegt werden
Konfigurationsfactory&quot;. Jeder Cache-Konfigurationseintrag kann im folgenden Format angegeben werden:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Hybride Zwischenspeicherung - clientseitige GraphQL-Anforderungen innerhalb zwischengespeicherter Dispatcher-Seiten

Es ist auch möglich, einen hybriden Ansatz zum Zwischenspeichern von Seiten zu wählen: Es ist möglich, dass eine CIF-Seite Komponenten enthält, die immer die neuesten Informationen von Adobe Commerce direkt über den Kundenbrowser anfordern. Dies kann für bestimmte Bereiche der Seite innerhalb einer Vorlage nützlich sein, die mit Echtzeitinformationen auf dem neuesten Stand gehalten werden müssen: Produktpreise innerhalb einer Produktdetailseite, z. B. Wenn sich die Preise aufgrund eines dynamischen Preisabgleichs häufig ändern, können diese Informationen so konfiguriert werden, dass sie nicht auf dem Dispatcher zwischengespeichert werden. Stattdessen können die Preise im Kundenbrowser direkt über GraphQL-APIs mit AEM CIF-Webkomponenten aus Adobe Commerce abgerufen werden.

Dies kann über die Einstellungen der AEM-Komponenten konfiguriert werden. Informationen zu Preisen auf Produktlistenseiten finden Sie in der Produktlistenvorlage. Wählen Sie dazu die Produktlistenkomponente in den Seiteneinstellungen aus und aktivieren Sie die Option &quot;Preise laden&quot;. Derselbe Ansatz würde für die Lagerbestände funktionieren.

Die oben genannten Methoden sollten nur verwendet werden, wenn Echtzeitinformationen, die ständig auf dem neuesten Stand sind, erforderlich sind. Im obigen Beispiel mit Preisgestaltung könnte es mit Interessengruppen aus der Wirtschaft vereinbart werden, die Preise nur täglich zu niedrigen Traffic-Zeiten zu aktualisieren und dann den Cache-Leerung durchzuführen. Dadurch entfällt die Notwendigkeit, Preisinformationen in Echtzeit zu erhalten und anschließend beim Erstellen jeder Seite, auf der Preisinformationen angezeigt werden, zusätzlich in Adobe Commerce zu laden.

## Nicht zwischenspeicherbare GraphQL-Anforderungen

Bestimmte dynamische Datenkomponenten innerhalb von Seiten sollten nicht zwischengespeichert werden und erfordern immer einen GraphQL-Aufruf an Adobe Commerce, z. B. für den Warenkorb und Aufrufe über die Checkout-Seiten hinweg. Diese Informationen sind benutzerspezifisch und ändern sich ständig aufgrund der Aktivitäten des Kunden auf der Site, z. B. durch Hinzufügen von Produkten zum Warenkorb.

GraphQL-Abfrageergebnisse sollten für angemeldete Kunden nicht zwischengespeichert werden, wenn das Design der Site je nach Benutzerrolle unterschiedliche Antworten liefert. Sie können beispielsweise mehrere Kundengruppen erstellen und für jede Gruppe unterschiedliche Produktpreise oder eine andere Produktkategorietreue einrichten. Zwischenspeicherungsergebnisse wie diese können dazu führen, dass Kunden die Preise einer anderen Kundengruppe sehen oder falsche Kategorien angezeigt werden.

## Ignorieren von Tracking-Parametern im AEM Dispatcher-Cache

E-Commerce-Sites können den Traffic zu ihrer Site über PPC-Suchanzeigen oder Social-Media-Kampagnen lenken.

Durch die Verwendung dieser Medien wird dem ausgehenden Link von dieser Plattform aus eine Tracking-ID hinzugefügt. Beispielsweise fügt Facebook der URL eine Facebook Click ID (fbclid) hinzu, Google Adverts fügt eine Google Click ID (gclid) hinzu. Dadurch werden eingehende Links zu Ihrem AEM Frontend wie unten dargestellt:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

Die gclid und fbclid ändern sich bei jedem Benutzer, der auf die Anzeige klickt. Dies dient zu Tracking-Zwecken. Mit den Standardeinstellungen würde AEM jede Anfrage jedoch als eindeutige Seite sehen, wodurch der Dispatcher umgangen und unnötige zusätzliche Ladevorgänge für den Publisher und den Adobe Commerce generiert würden.

Bei einem Aufprallereignis kann dies sogar dazu führen, dass die AEM Publisher überlastet werden und nicht reagieren. Wenn ein Parameter so eingestellt ist, dass er für eine Seite ignoriert wird, wird die Seite beim ersten Anfordern der Seite zwischengespeichert. Nachfolgende Anforderungen für die Seite werden auf der zwischengespeicherten Seite bereitgestellt, unabhängig vom Wert des Parameters in der Anfrage.

>[!NOTE]
>
>Weitere Informationen zur Wichtigkeit der Einstellung von `ignoreUrlParams` finden Sie im GitHub-Repository [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) .

Es sollte daher so konfiguriert werden, dass alle Parameter standardmäßig in &quot;ignoreUrlParams&quot;ignoriert werden, es sei denn, es wird ein GET-Parameter verwendet, der die HTML-Struktur einer Seite ändert. Ein Beispiel hierfür wäre eine Suchseite, auf der der Suchbegriff als GET-Parameter in der URL enthalten ist. In diesem Fall sollten Sie dann manuell ignoreUrlParams konfigurieren, um Parameter wie gclid, fbclid und andere Tracking-Parameter, die Ihre Werbekanäle verwenden, zu ignorieren, wobei die für normale Site-Vorgänge erforderlichen GET Parameter unberührt bleiben.

## Begrenzung der Zahl der MPM-Mitarbeiter auf Dispatcher

Bei den MPM-Worker-Einstellungen handelt es sich um eine erweiterte Apache-HTTP-Serverkonfiguration, die gründliche Tests erfordert, um die Optimierung auf der Grundlage der verfügbaren CPU und RAM Ihres Dispatchers zu ermöglichen. Im Rahmen dieses Whitepaper empfehlen wir jedoch, ServerLimit und MaxRequestWorkers so weit zu erweitern, dass die verfügbare CPU und der verfügbare RAM des Servers unterstützt werden, und anschließend die MinSpareThreads und MaxSpareThreads auf ein Niveau zu erhöhen, das den MaxRequestWorkers entspricht.

Bei dieser Konfiguration würde Apache HTTP eine &quot;vollständige Bereitschaftseinstellung&quot;aufweisen, bei der es sich um eine Hochleistungskonfiguration für Server mit beträchtlichem RAM und mehreren CPU-Kernen handelt. Diese Konfiguration erzeugt die bestmöglichen Reaktionszeiten von Apache HTTP, indem persistente offene Verbindungen, die für Anfragen bereit sind, beibehalten werden. Außerdem würde sie Verzögerungen beim Erstellen neuer Prozesse als Reaktion auf plötzliche Traffic-Spitzen, z. B. bei Flash-Verkäufen, beseitigen.
