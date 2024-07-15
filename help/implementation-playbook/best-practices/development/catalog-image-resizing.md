---
title: Best Practices für die Größenanpassung von Katalogbildern
description: Erfahren Sie, wie Sie eine Leistungsbeeinträchtigung vor dem Start der Adobe Commerce-Site durch die Produktion verhindern können.
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Best Practices für die Größenanpassung von Katalogbildern

Alle Katalogbilder sollten in der Größe angepasst werden, bevor ein Store in die Produktion aufgenommen wird. Wenn die Bildgröße vor der Produktion nicht geändert werden kann, wird die Bildgröße beim Laden der Seite erzwungen, wodurch die Site-Geschwindigkeit erheblich reduziert und die Server-Last in den ersten Tagen bis Wochen nach dem Start erhöht wird.

## Der langsame Weg

Verwenden Sie den standardmäßigen CLI-Befehl, um die Größe aller Bilder zu ändern:

```bash
bin/magento catalog:images:resize
```

Zu den Nachteilen dieses Ansatzes zählen:

- Der Prozess ist einprozessgestützt
- Der Prozess ändert die Größe von Bildern, deren Größe bereits geändert wurde
- Der Prozess kann nicht unterbrochen werden, was Tage dauern kann

## Der schnelle (er) Weg

Die asynchrone Bildanpassung wurde in Adobe Commerce 2.4 eingeführt und kann die Bildgröße beschleunigen.

1. Starten Sie auf jedem Webserver einige zusätzliche Warteschlangen-Handler vorübergehend (doppelt so viele physische Prozessoren pro Server):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Stellen Sie sicher, dass die Warteschlangen-Handler ausgeführt werden:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Füllen Sie die Warteschlange mit allen Bildgrößenanforderungen aus:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Nachdem die Größe aller Bilder geändert wurde, beenden Sie den Prozess:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## Der schnelle Weg

Es gibt eine andere Möglichkeit, die Größe von Bildern mithilfe des Frontend zu ändern.

Zu den Vorteilen dieses Ansatzes zählen:

- Der Prozess ist mehrprozessgestützt
- Der Prozess erfolgt über mehrere Server (wenn Sie mehrere Webknoten, einen Lastenausgleich und freigegebenen Speicherplatz für den Ordner &quot;`media/`&quot;haben).
- Der Prozess überspringt Bilder, deren Größe bereits geändert wurde

Bei diesem Ansatz wird die Größe von 100.000 Bildern in weniger als 8 Stunden geändert, während der CLI-Befehl 6 Tage dauert.

1. Melden Sie sich beim Server an.
1. Navigieren Sie zu &quot;`pub/media/catalog/product`&quot;und notieren Sie sich einen der Hashes (z. B. 0047d83143a5a3a4683afdf116df680).
1. Ersetzen Sie in den folgenden Beispielen `www.example.com` durch die Domäne Ihres Stores und ersetzen Sie den Hash durch den Hash, den Sie notiert haben.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB Belagerung]

Der Nachteil von `siege` besteht darin, dass alle URLs in den 10-mal aufgerufen werden, wenn die Parallelität auf 10 gesetzt ist.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

Das Argument `-P` bestimmt die Anzahl der Threads.

>[!TAB Bash One-Liner]

Das Einliner für das Beispiel `find/curl` , falls Sie `curl` von demselben Computer aus ausführen können, auf dem sich die Bilder befinden:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Ersetzen Sie erneut `www.example.com` durch die Domäne Ihrer Website und legen Sie `-P` auf die Anzahl der Threads fest, die Ihr Server ohne Abstürze verarbeiten kann.

>[!ENDTABS]

Die Ausgabe gibt eine Liste aller Produktbilder im Store zurück. Sie können die Bilder (mit `siege` oder einem anderen Crawler) durchsuchen, indem Sie alle für Sie verfügbaren Server und Prozessorkerne verwenden und den Cache für die Größenanpassung mit deutlich höherer Geschwindigkeit als bei anderen Ansätzen generieren.

Beim Besuch einer Bild-Cache-URL werden alle Bildgrößen im Hintergrund generiert, wenn sie noch nicht vorhanden sind. Außerdem werden Dateien übersprungen, deren Größe bereits geändert wurde.

>[!NOTE]
>
>- Adobe Commerce in Cloud-Infrastrukturprojekten kann Produktbilder in der Größenanpassung an den Fastly-Dienst abladen. Siehe [Optimierung des tiefen Bildes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) im _Cloud-Handbuch_.
>- Wenn Sie das Remote-Speichermodul verwenden, können Sie auch versuchen, die Größe des Bildes auf nginx zu verändern. Siehe [Konfigurieren der Bildgröße für Remote-Speicher](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) im _Konfigurationshandbuch_.
