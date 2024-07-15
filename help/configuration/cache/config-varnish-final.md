---
title: Endgültige Überprüfung
description: Stellen Sie sicher, dass Ihre Varnish-Konfiguration ordnungsgemäß für die Verwendung mit der Adobe Commerce-Anwendung eingerichtet ist.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Abschließende Überprüfung der tierischen Konfiguration

Nachdem Sie jetzt den von Commerce generierten `default.vcl` verwenden, können Sie einige endgültige Überprüfungen durchführen, um sicherzustellen, dass Varnish funktioniert.

## Überprüfen von HTTP-Antwortheadern

Verwenden Sie `curl` oder ein anderes Dienstprogramm, um HTTP-Antwortheader anzuzeigen, wenn Sie eine Commerce-Seite in einem Webbrowser besuchen.

Stellen Sie zunächst sicher, dass Sie den [Entwicklermodus](../cli/set-mode.md#change-to-developer-mode) verwenden. Andernfalls werden die Kopfzeilen nicht angezeigt.

Beispiel:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Wichtige Kopfzeilen:

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Dieser Wert ist auch zulässig: `X-Magento-Cache-Debug: HIT`.

## Überprüfen der Seitenladezeiten

Wenn Varnish funktioniert, sollte jede Commerce-Seite mit zwischenspeicherbaren Blöcken in weniger als 150 ms geladen werden. Beispiele für solche Seiten sind die Kategorieseiten &quot;Haustür&quot;und &quot;Storefront&quot;.

Verwenden Sie einen Browser-Inspektor, um die Seitenladezeiten zu messen.

So verwenden Sie beispielsweise den Chrome-Inspektor:

1. Greifen Sie auf eine beliebige zwischenspeicherbare Commerce-Seite in Chrome zu.
1. Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle auf der Seite.
1. Klicken Sie im Popup-Menü auf **[!UICONTROL Inspect Element]**
1. Klicken Sie im Bedienfeld des Inspektors auf die Registerkarte **[!UICONTROL Network]** .
1. Aktualisieren Sie die Seite.
1. Scrollen Sie zum oberen Rand des Inspektorbereichs, damit Sie die URL der angezeigten Seite sehen können.

   Die folgende Abbildung zeigt ein Beispiel für das Laden der Indexseite &quot;`magento2`&quot;.

   ![Klicken Sie auf die angezeigte Seite](../../assets/configuration/varnish-inspector.png)

   Die Seitenladezeit wird neben der Seiten-URL angezeigt. In diesem Fall beträgt die Ladezeit 5 ms. Dies hilft zu bestätigen, dass Varnish die Seite zwischengespeichert hat.

1. Um HTTP-Antwortheader anzuzeigen, klicken Sie auf die Seiten-URL (in der Spalte Name ).

   Sie können HTTP-Header anzeigen, die im Abschnitt HTTP-Antwortheader überprüfen ausführlicher beschrieben werden.

## Überprüfen des Commerce-Cache

Stellen Sie sicher, dass der Ordner &quot;`<magento_root>/var/page_cache`&quot; leer ist:

1. Melden Sie sich bei Ihrem Commerce-Server an oder wechseln Sie zum Dateisysteminhaber.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Greifen Sie auf eine oder mehrere zwischenspeicherbare Commerce-Seiten zu.
1. Überprüfen Sie den Ordner &quot;`var/page_cache/`&quot;.

   Wenn das Verzeichnis leer ist, gratulieren Sie dazu! Sie haben Varnish und Commerce erfolgreich für die Zusammenarbeit konfiguriert.

1. Wenn Sie den Ordner &quot;`var/page_cache/`&quot;gelöscht haben, starten Sie &quot;Varnish&quot;neu.

>[!TIP]
>
>Wenn Fehler des Typs 503 (Backend-Abruf fehlgeschlagen) auftreten, finden Sie weitere Informationen unter [Fehlerbehebung für Fehler des Typs 503 (Dienst nicht verfügbar)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) im _Adobe Commerce Help Center_.
