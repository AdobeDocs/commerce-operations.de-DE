---
title: Konfigurieren des AWS S3-Buckets für Remote-Speicher
description: Konfigurieren Sie Ihr Commerce-Projekt für die Verwendung des AWS S3-Speicherdienstes für Remote-Speicher.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Konfigurieren des AWS S3-Buckets für Remote-Speicher

Der [Amazon Simple Storage Service (Amazon S3)][AWS S3] ist ein Objektspeicherdienst, der branchenführende Skalierbarkeit, Datenverfügbarkeit, Sicherheit und Leistung bietet. Der AWS S3-Dienst verwendet Behälter oder Container für die Datenspeicherung. Für diese Konfiguration müssen Sie einen _privaten_ Behälter erstellen. Informationen zu Adobe Commerce in der Cloud-Infrastruktur finden Sie unter [Konfigurieren des Remote-Speichers für Commerce in der Cloud-Infrastruktur](cloud-support.md).

>[!WARNING]
>
>Adobe rät dringend von der Verwendung öffentlicher Buckets ab, da dies ein ernsthaftes Sicherheitsrisiko darstellt.

**So aktivieren Sie Remote-Speicher mit dem AWS S3-Adapter**:

1. Melden Sie sich bei Ihrem Amazon S3-Dashboard an und erstellen Sie einen Bucket _privat_ .

1. Richten Sie die Rollen [AWS IAM] ein. Alternativ können Sie Zugriff- und geheime Schlüssel generieren.

1. Deaktivieren Sie den standardmäßigen Datenbankspeicher.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Konfigurieren Sie Commerce für die Verwendung des privaten Buckets. Eine vollständige Liste der Parameter finden Sie unter [Remote-Speicheroptionen](remote-storage.md#remote-storage-options) .

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Mediendateien mit Remote-Speicher synchronisieren.

   ```bash
   bin/magento remote-storage:sync
   ```

## Nginx konfigurieren

Nginx benötigt eine zusätzliche Konfiguration, um die Authentifizierung mit der Anweisung `proxy_pass` durchzuführen. Fügen Sie der Datei `nginx.conf` die folgenden Proxy-Informationen hinzu:

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

Wenn Sie Zugriff- und geheime Schlüssel anstelle der Rollen [AWS IAM] verwenden, müssen Sie das [`ngx_aws_auth` Nginx-Modul][ngx repo] einschließen.

### Berechtigungen

Die S3-Integration beruht auf der Möglichkeit, zwischengespeicherte Bilder im lokalen Dateisystem zu generieren und zu speichern. Daher sind die Ordnerberechtigungen für `pub/media` und ähnliche Ordner für S3 identisch mit denen für die Verwendung des lokalen Speichers.

### Dateivorgänge

Es wird dringend empfohlen, die [!DNL Commerce]-Dateiadaptermethoden unabhängig vom Dateispeichertyp in der Code- oder Erweiterungsentwicklung zu verwenden. Verwenden Sie bei Verwendung von S3 zum Speichern keine nativen I/O-Vorgänge für PHP-Dateien wie `copy`, `rename` oder `file_put_contents`, da sich S3-Dateien nicht im Dateisystem befinden. Codebeispiele finden Sie unter [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) .

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
