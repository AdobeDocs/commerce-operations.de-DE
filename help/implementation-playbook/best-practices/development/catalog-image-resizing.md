---
title: Best Practices für die Größenanpassung von Katalogbildern
description: Erfahren Sie, wie Sie vor einem Produktionsstart Ihrer Adobe Commerce-Site eine Leistungsbeeinträchtigung verhindern können.
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Best Practices für die Größenanpassung von Katalogbildern

Die Größe aller Katalogbilder sollte geändert werden, bevor ein Geschäft in die Produktion geht. Wenn die Bildgröße nicht vor der Produktion geändert wird, muss die Bildgröße beim Laden der Seite geändert werden, was die Site-Geschwindigkeit erheblich reduziert und die Server-Last in den ersten Tagen bis Wochen nach dem Start erhöht.

## Der langsame Weg

Verwenden Sie den CLI-Standardbefehl, um die Größe aller Bilder zu ändern:

```bash
bin/magento catalog:images:resize
```

Zu den Nachteilen dieses Ansatzes gehören:

- Der Prozess erfolgt in einem einzigen Thread
- Der Prozess ändert die Größe von Bildern, die bereits geändert wurden
- Der Vorgang kann nicht unterbrochen werden, was Tage dauern kann

## Der schnelle(e) Weg

Die asynchrone Größenanpassung von Bildern wurde in Adobe Commerce 2.4 eingeführt und kann die Bildgröße schneller ändern.

1. Starten Sie auf jedem Webserver vorübergehend einige zusätzliche Warteschlangen-Handler (doppelt so viele physische Prozessoren pro Server):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Stellen Sie sicher, dass die Warteschlangen-Handler ausgeführt werden:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Füllen Sie die Warteschlange mit allen Bildgrößenanforderungen:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Beenden Sie den Prozess, nachdem die Größe aller Bilder geändert wurde:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## Der schnelle Weg

Es gibt eine andere Möglichkeit, die Größe von Bildern mithilfe des Frontends zu ändern.

Zu den Vorteilen dieses Ansatzes gehören:

- Der Prozess umfasst mehrere Threads
- Der Prozess ist Multi-Server (wenn Sie mehrere Web-Knoten, einen Lastenausgleich und gemeinsamen Speicherplatz für das `media/` haben)
- Der Prozess überspringt Bilder, die bereits in der Größe geändert wurden

Bei diesem Ansatz werden 100.000 Bilder in weniger als 8 Stunden skaliert, während der CLI-Befehl 6 Tage dauert.

1. Melden Sie sich beim -Server an.
1. Navigieren Sie zu `pub/media/catalog/product` und notieren Sie sich einen der Hash-Werte (z. B. 0047d83143a5a3a4683afdf1116df680).
1. Ersetzen Sie in den folgenden Beispielen `www.example.com` durch die Domain Ihres Stores und ersetzen Sie den Hash durch den genannten.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB Belagerung]

Der Nachteil von `siege` besteht darin, dass alle URLs 10-mal aufgerufen werden, wenn die gleichzeitige Nutzung auf 10 gesetzt ist.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB cURL]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

Das `-P` Argument bestimmt die Anzahl der Threads.

>[!TAB Bash One-Liner]

Der Einzeiler für das `find/curl` Beispiel, falls Sie `curl` von demselben Computer ausführen können, auf dem sich die Bilder befinden:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Ersetzen Sie erneut `www.example.com` durch die Domain Ihrer Website und legen Sie `-P` auf die Anzahl der Threads fest, die Ihr Server verarbeiten kann, ohne abzustürzen.

>[!ENDTABS]

Die Ausgabe gibt eine Liste aller Produktbilder im Store zurück. Sie können die Bilder (mit `siege` oder einem anderen Crawler) mit allen Servern und Prozessorkernen durchsuchen, die Ihnen zur Verfügung stehen, und den Cache mit einer deutlich höheren Geschwindigkeit als andere Ansätze verändern.

Beim Besuch einer Bild-Cache-URL werden alle Bildgrößen im Hintergrund generiert, sofern sie noch nicht vorhanden sind. Außerdem werden Dateien übersprungen, deren Größe bereits geändert wurde.

>[!NOTE]
>
>- Adobe Commerce in Cloud-Infrastrukturprojekten kann die Größenanpassung des Produktbilds auf den Fastly-Service auslagern. Siehe [Tiefenbildoptimierung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html#deep-image-optimization) im _Cloud-Handbuch_.
>- Wenn Sie das Remote-Speichermodul verwenden, können Sie auch versuchen, die Größe des Bildes auf nginx zu ändern. Siehe [Konfigurieren der Bildgröße für den Remote](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) im _Konfigurationshandbuch_.
