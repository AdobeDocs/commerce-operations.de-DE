---
title: Bildgröße für Remote-Speicher konfigurieren
description: Optimieren Sie die Festplattenressourcen, indem Sie die Größe des serverseitigen Bildes konfigurieren.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Bildgröße für Remote-Speicher konfigurieren

Standardmäßig unterstützt Adobe Commerce die Größenanpassung von Bildern auf der Anwendungsseite. Durch Aktivierung des Remote Storage-Moduls können Sie jedoch Nginx verwenden, um die Größe des Bildes auf die Server-Seite zu verschieben, wo Sie Festplattenressourcen sparen und die Festplattenauslastung optimieren können.

Das folgende Diagramm zeigt, wie Nginx Bilder im Cache abruft, in der Größe ändert und speichert. Die Größenanpassung wird durch die in der URL enthaltenen Parameter bestimmt, z. B. Höhe und Breite.

![Bildgröße](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Konfigurieren des Remote-Speichers für Commerce in der Cloud-Infrastruktur](cloud-support.md) .

## Konfigurieren des URL-Formats in Adobe Commerce

Um die Größe von Bildern serverseitig zu ändern, müssen Sie Adobe Commerce so konfigurieren, dass Argumente für die Höhe, Breite und Position (URL) des Bildes angegeben werden.

**So konfigurieren Sie Commerce für die serverseitige Bildgröße**:

1. Klicken Sie im Bedienfeld _Admin_ auf **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Erweitern Sie im rechten Bereich den Wert **[!UICONTROL Url options]**.

1. Löschen Sie im Abschnitt _Catalog Media URL format_ den Wert **[!UICONTROL Use system value]**.

1. Wählen Sie die URL `Image optimization based on query parameters` im Feld **_URL-Format der Katalogmedien-URL_** aus.

1. Klicken Sie auf **[!UICONTROL Save Config]**.

1. Fahren Sie mit der [Nginx-Konfiguration](#configure-nginx) fort.

## Nginx konfigurieren

Um mit der Konfiguration der serverseitigen Bildgröße fortzufahren, müssen Sie die Datei &quot;`nginx.conf`&quot;vorbereiten und einen &quot;`proxy_pass`&quot;-Wert für den ausgewählten Adapter angeben.

**So aktivieren Sie Nginx, um die Bildgröße zu ändern**:

1. Installieren Sie das [Nginx-Bildfiltermodul][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Erstellen Sie eine `nginx.conf` -Datei basierend auf der eingeschlossenen Vorlage `nginx.conf.sample` . Beispiel:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Optional_] Konfigurieren Sie einen `proxy_pass` -Wert für Ihren spezifischen Adapter.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
