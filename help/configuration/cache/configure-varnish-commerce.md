---
title: Konfigurieren der Variante für Commerce
description: Erfahren Sie, wie Sie Ihre Varnish-Konfigurationsdatei für die Commerce-Anwendung aktualisieren und verwalten.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 11ccc59230a7a0d1768c043c39df43c7df031efd
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Konfigurieren der Commerce-Anwendung für die Verwendung von Varnish

So konfigurieren Sie Commerce für die Verwendung von Varnish:

1. Melden Sie sich bei Admin als Administrator an.
1. Klicks **[!UICONTROL Stores]** > Einstellungen > **Konfiguration** > **Erweitert** > **System** > **Vollständiger Seiten-Cache**.
1. Aus dem **[!UICONTROL Caching Application]** Liste, klicken Sie **Varnish-Zwischenspeicherung**.
1. Geben Sie im Feld **[!UICONTROL TTL for public content]** -Feld.
1. Erweitern **[!UICONTROL Varnish Configuration]** und geben Sie folgende Informationen ein:

   | Feld | Beschreibung |
   | ----- | ----------- |
   | Zugriffsliste | Geben Sie den vollständig qualifizierten Hostnamen und die IP-Adresse ein oder [Classless Inter-Domain Routing (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) -IP-Adressbereich, für den Inhalte ungültig gemacht werden sollen. Siehe [Bereinigen des Zwischenspeichers](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Backend-Host | Geben Sie den vollständig qualifizierten Hostnamen oder die IP-Adresse ein und überwachen Sie den Port des Varnish _Backend_ oder _Ursprungsserver_; d. h. der Server, der den Inhalt bereitstellt, beschleunigt Varnish. Normalerweise ist dies Ihr Webserver. Siehe [Varnish-Cache-Backend-Server](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Backend-Port | Listener Port des Herkunftsservers. |
   | Übergangsphase | Bestimmt, wie lange Varnish veraltete Inhalte bereitstellt, wenn das Backend nicht reagiert. Der Standardwert ist 300 Sekunden. |
   | Handles params size  [!BADGE 2.4.7-Beta]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Nur in 2.4.7-Beta verfügbar"} | Gibt die maximale Anzahl von [Layout-Handles](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) zur Verarbeitung in [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) HTTP-Endpunkt für die vollständige Zwischenspeicherung. Eine Größenbeschränkung kann die Sicherheit und Leistung verbessern. Der Standardwert ist 100. |

1. Klicks **Konfiguration speichern**.

Mit dem Befehlszeilen-Tool C können Sie auch die Option Varnish über die Befehlszeile aktivieren, anstatt sich beim Administrator anzumelden:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Varnish-Konfigurationsdatei exportieren

So exportieren Sie eine Varnish-Konfigurationsdatei aus dem Administrator:

1. Klicken Sie auf eine der Exportschaltflächen, um eine `varnish.vcl` können Sie mit Varnish verwenden.

   Wenn Sie beispielsweise Varnish 4 haben, klicken Sie auf **VCL für Schweine 4 ausführen**

   Die folgende Abbildung zeigt ein Beispiel:

   ![Konfigurieren von Commerce zur Verwendung von Varnish in Admin](../../assets/configuration/varnish-admin-22.png)

1. Vorhandene sichern `default.vcl`. Benennen Sie dann die `varnish.vcl` Datei, die Sie gerade in `default.vcl`. Kopieren Sie dann die Datei in die `/etc/varnish/` Verzeichnis.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe empfehlen, zu öffnen `default.vcl` und den Wert von `acl purge` an die IP-Adresse des &quot;Varnish&quot;-Hosts. (Sie können mehrere Hosts in separaten Zeilen angeben oder auch die CIDR-Notation verwenden.)

   Beispiel:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Wenn Sie die Vagrant-Konsistenzprüfungen, den Übergangmodus oder die Farbmodus-Konfiguration anpassen möchten, lesen Sie [Erweiterte Varnish-Konfiguration](config-varnish-advanced.md).

1. Starten Sie Varnish und Ihren Webserver neu:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Statische Cache-Dateien

Statische Dateien sollten nicht standardmäßig zwischengespeichert werden. Wenn Sie sie jedoch zwischenspeichern möchten, können Sie den Abschnitt bearbeiten `Static files caching` im VCL den folgenden Inhalt aufweisen:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Sie müssen diese Änderungen vornehmen, bevor Sie Commerce für die Verwendung von Varnish konfigurieren.
