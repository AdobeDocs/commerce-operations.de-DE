---
title: AWS S3-Bucket für Remote-Speicher konfigurieren
description: Konfigurieren Sie Ihr Commerce-Projekt für die Verwendung des AWS S3-Speicher-Services für die Remote-Speicherung.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# AWS S3-Bucket für Remote-Speicher konfigurieren

Der [Amazon Simple Storage Service (Amazon S3)][AWS S3] ist ein Objektspeicher-Service, der branchenführende Skalierbarkeit, Datenverfügbarkeit, Sicherheit und Leistung bietet. Der AWS S3-Service verwendet Buckets (oder Container) für die Datenspeicherung. Für diese Konfiguration müssen Sie einen _privaten“_ erstellen. Informationen zu Adobe Commerce in Cloud-Infrastrukturen finden Sie unter [Konfigurieren von Remote-Speicher für Commerce in Cloud-Infrastrukturen](cloud-support.md).

>[!WARNING]
>
>Adobe rät von der Verwendung öffentlicher Behälter ab, da dies ein ernstes Sicherheitsrisiko darstellt.

**So aktivieren Sie die Remote-Speicherung mit dem AWS S3-Adapter**:

1. Melden Sie sich bei Ihrem Amazon S3-Dashboard an und erstellen Sie einen _privaten_ Bucket.

1. Richten Sie [AWS IAM]-Rollen ein. Alternativ können Sie Zugriffs- und Geheimschlüssel generieren.

1. Deaktivieren Sie den standardmäßigen Datenbankspeicher.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Konfigurieren Sie Commerce für die Verwendung des privaten Buckets. Siehe [Remote-Speicheroptionen](remote-storage.md#remote-storage-options) für eine vollständige Liste der Parameter.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Synchronisieren von Mediendateien mit dem Remote-Speicher.

   ```bash
   bin/magento remote-storage:sync
   ```

## Konfigurieren von nginx

Nginx erfordert eine zusätzliche Konfiguration, um die Authentifizierung mit der `proxy_pass`-Direktive durchzuführen. Fügen Sie der `nginx.conf`-Datei die folgenden Proxy-Informationen hinzu:

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Authentifizierung

Wenn Sie anstelle von [AWS IAM]-Rollen Zugriffs- und Geheimschlüssel verwenden, müssen Sie das [`ngx_aws_auth` Nginx-Modul ][ngx repo].

### Berechtigungen

Die S3-Integration beruht auf der Möglichkeit, zwischengespeicherte Bilder im lokalen Dateisystem zu generieren und zu speichern. Daher sind die Ordnerberechtigungen für `pub/media` und ähnliche Ordner für S3 und für die Verwendung des lokalen Speichers identisch.

### Dateifunktionen

Es wird dringend empfohlen, bei der Codierung oder Erweiterungsentwicklung [!DNL Commerce] Dateiadaptermethoden zu verwenden, unabhängig vom Dateispeichertyp. Wenn Sie S3 für die Speicherung verwenden, verwenden Sie keine nativen PHP-Datei-I/O-Vorgänge wie `copy`, `rename` oder `file_put_contents`, da sich S3-Dateien nicht im Dateisystem befinden. Code[Beispiele finden Sie unter ](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18)DriverInterface.php).

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
