---
title: Konfigurieren der Bildgröße für den Remote-Speicher
description: Optimieren Sie die Festplattenressourcen durch die Konfiguration der Server-seitigen Bildgröße.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%
---
# Konfigurieren der Bildgröße für den Remote-Speicher

Standardmäßig unterstützt Adobe Commerce das Ändern der Bildgröße in der Anwendung. Durch die Aktivierung des Remote-Speichermoduls können Sie jedoch Nginx verwenden, um die Bildgröße auf die Serverseite zu verlagern, wo Sie Festplattenressourcen sparen und die Festplattenauslastung optimieren können.

Das folgende Diagramm zeigt, wie Nginx Bilder im Cache abruft, in der Größe verändert und speichert. Die Größe wird durch die in der URL enthaltenen Parameter wie Höhe und Breite bestimmt.

![Nginx-Konfiguration für Remote-Speicher-Image-Größenanpassung mit Server-Blockeinstellungen](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Konfigurieren von Remote-Speicher für Commerce in Cloud-Infrastruktur](cloud-support.md)

## Konfigurieren des URL-Formats in Adobe Commerce

Um die Bildgröße auf der Serverseite zu ändern, müssen Sie Adobe Commerce so konfigurieren, dass Argumente für die Höhe, Breite und Position (URL) des Bildes bereitgestellt werden.

**So konfigurieren Sie Commerce für die Server-seitige Größenänderung von Bildern**:

1. Klicken Sie _Bedienfeld_ Admin) auf **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Erweitern Sie im rechten Bereich **[!UICONTROL Url options]**.

1. Löschen Sie im _Catalog media URL format_ den Eintrag **[!UICONTROL Use system value]**.

1. Wählen Sie die `Image optimization based on query parameters`-URL im Feld **_URL für Katalogmedien_** aus.

1. Klicken Sie auf **[!UICONTROL Save Config]**.

1. Fahren Sie mit der [Nginx-Konfiguration](#configure-nginx) fort.

## Konfigurieren von nginx

Um mit der Konfiguration der Server-seitigen Bildgröße fortzufahren, müssen Sie die `nginx.conf`-Datei vorbereiten und einen `proxy_pass` Wert für Ihren ausgewählten Adapter angeben.

**So aktivieren Sie Nginx zum Ändern der Bildgröße**:

1. Installieren Sie das [Nginx-Bildfiltermodul](https://nginx.org/en/docs/http/ngx_http_image_filter_module.html).

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Erstellen Sie eine `nginx.conf` Datei basierend auf der enthaltenen `nginx.conf.sample`. Beispiel:

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

1. [_Optional_] Konfigurieren Sie einen `proxy_pass` für Ihren spezifischen Adapter.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

