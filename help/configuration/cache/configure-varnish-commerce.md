---
title: Lacke für Commerce konfigurieren
description: Erfahren Sie, wie Sie Ihre Varnish-Konfigurationsdatei für das Commerce-Programm aktualisieren und verwalten.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Konfigurieren des Commerce-Programms für die Verwendung von Varnish

So konfigurieren Sie Commerce für die Verwendung von „Varnish“:

1. Melden Sie sich bei Admin als Admin an.
1. Klicken Sie auf **[!UICONTROL Stores]** > Einstellungen **Konfiguration** > **Erweitert** > **System** > **Vollständiger Seitencache**.
1. Klicken Sie in der Liste **[!UICONTROL Caching Application]** auf **Zwischenspeicherung löschen**.
1. Geben Sie einen Wert in das Feld **[!UICONTROL TTL for public content]** ein.
1. Erweitern Sie **[!UICONTROL Varnish Configuration]** und geben Sie die folgenden Informationen ein:

   | Feld | Beschreibung |
   | ----- | ----------- |
   | Auf Liste zugreifen | Geben Sie den vollqualifizierten Hostnamen, die IP-Adresse oder den [Classless Inter-Domain Routing (CIDR)-](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking)-Adressbereich ein, für den Inhalte ungültig gemacht werden sollen. Siehe [Löschen des Lackcache](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Backend-Host | Geben Sie den vollqualifizierten Hostnamen oder die IP-Adresse ein und überwachen Sie den Port des Varnish _Backend_ oder _Ursprungs-Servers_, d. h. der Server, der den Inhaltslack bereitstellt, beschleunigt. Normalerweise ist dies Ihr Webserver. Siehe [Löschen von Cache-Backend-Servern](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Backend-Port | Lauschender Port des Ursprungs-Servers |
   | Karenzzeit | Legt fest, wie lange Varnish veraltete Inhalte bereitstellt, wenn das Backend nicht responsiv ist. Der Standardwert ist 300 Sekunden. |
   | Verarbeitet Parameter der Größe | Gibt die maximale Anzahl von [Layout-Handles](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) an, die für das Zwischenspeichern ganzer Seiten am [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) HTTP-Endpunkt verarbeitet werden sollen. Durch Größenbeschränkungen können die Sicherheit und Leistung verbessert werden. Der Standardwert lautet 100. |

1. Klicken Sie **Konfiguration speichern**.

Sie können Varnish auch über die Befehlszeile aktivieren, anstatt sich beim Admin anzumelden, indem Sie das Befehlszeilen-Tool C verwenden:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportieren einer Lackkonfigurationsdatei

So exportieren Sie eine Lackkonfigurationsdatei vom Administrator:

1. Klicken Sie auf eine der Exportschaltflächen, um eine `varnish.vcl` zu erstellen, die Sie mit Lack verwenden können.

   Wenn Sie beispielsweise Lack 4 haben, klicken Sie auf **VCL für Lack 4 exportieren**

   Die folgende Abbildung zeigt ein Beispiel:

   ![Konfigurieren von Commerce für die Verwendung von „Lack“ in der Admin-Liste](../../assets/configuration/varnish-admin-22.png)

1. Sichern Sie Ihr vorhandenes `default.vcl`. Benennen Sie dann die soeben exportierte `varnish.vcl`-Datei in `default.vcl` um. Kopieren Sie dann die Datei in das `/etc/varnish/`.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe empfiehlt, `default.vcl` zu öffnen und den Wert von `acl purge` in die IP-Adresse des Lack-Hosts zu ändern. (Sie können mehrere Hosts in separaten Zeilen angeben oder auch die CIDR-Notation verwenden.)

   Beispiel:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Wenn Sie die Vagrant-Konsistenzprüfungen oder die Konfiguration des Gnadenmodus oder des Heiligen Modus anpassen möchten, lesen Sie den Abschnitt [Erweiterte Lackkonfiguration](config-varnish-advanced.md).

1. Starten Sie Lack und Ihren Webserver neu:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Statische Dateien zwischenspeichern

Statische Dateien sollten nicht standardmäßig zwischengespeichert werden. Wenn Sie sie jedoch zwischenspeichern möchten, können Sie die `Static files caching` im VCL so bearbeiten, dass sie die folgenden Inhalte haben:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Sie müssen diese Änderungen vornehmen, bevor Sie Commerce für die Verwendung von Varnish konfigurieren.
