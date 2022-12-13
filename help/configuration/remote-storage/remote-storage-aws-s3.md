---
title: Konfigurieren des AWS S3-Buckets für Remote-Speicher
description: Konfigurieren Sie Ihr Commerce-Projekt für die Verwendung des AWS S3-Speicherdienstes für Remote-Speicher.
source-git-commit: 31078c836fb088a10712c8c4cf4430a38d1962f2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Konfigurieren des AWS S3-Buckets für Remote-Speicher

Die [Amazon Simple Storage Service (Amazon S3)][AWS S3] ist ein Objektspeicherdienst, der branchenführende Skalierbarkeit, Datenverfügbarkeit, Sicherheit und Leistung bietet. Der AWS S3-Dienst verwendet Behälter oder Container für die Datenspeicherung. Für diese Konfiguration müssen Sie eine _privat_ Eimer. Informationen zu Adobe Commerce zur Cloud-Infrastruktur finden Sie unter [Remote-Speicher für Commerce in Cloud-Infrastruktur konfigurieren](cloud-support.md).

>[!WARNING]
>
>Adobe rät dringend von der Verwendung öffentlicher Buckets ab, da sie ein ernsthaftes Sicherheitsrisiko darstellt.

**So aktivieren Sie Remote-Speicher mit dem AWS S3-Adapter**:

1. Melden Sie sich bei Ihrem Amazon S3-Dashboard an und erstellen Sie eine _privat_ Eimer.

1. Einrichten [AWS IAM] Rollen. Alternativ können Sie Zugriff- und geheime Schlüssel generieren.

1. Deaktivieren Sie den standardmäßigen Datenbankspeicher.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Konfigurieren Sie Commerce für die Verwendung des privaten Buckets. Siehe [Remote-Speicheroptionen](remote-storage.md#remote-storage-options) für eine vollständige Liste der Parameter.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Synchronisieren Sie Mediendateien mit Remote-Speicher.

   ```bash
   bin/magento remote-storage:sync
   ```

## Nginx konfigurieren

Nginx erfordert eine zusätzliche Konfiguration, um die Authentifizierung mit dem `proxy_pass` Richtlinie. Fügen Sie die folgenden Proxy-Informationen zum `nginx.conf` Datei:

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

Wenn Sie Zugriff- und geheime Schlüssel anstelle von [AWS IAM] -Rollen, müssen Sie die [`ngx_aws_auth` Nginx-Modul][ngx repo].

### Berechtigungen

Die S3-Integration beruht auf der Möglichkeit, zwischengespeicherte Bilder im lokalen Dateisystem zu generieren und zu speichern. Daher sind Ordnerberechtigungen für `pub/media` und ähnliche Ordner sind für S3 identisch mit denen bei der Verwendung des lokalen Speichers.

### Dateivorgänge

Es wird dringend empfohlen, [!DNL Commerce] Dateiadaptermethoden in Ihrer Kodierung oder Erweiterungsentwicklung, unabhängig vom Dateityp. Verwenden Sie bei Verwendung von S3 zum Speichern keine nativen I/O-Vorgänge für PHP-Dateien, z. B. `copy`, `rename`oder `file_put_contents`, da sich S3-Dateien nicht im Dateisystem befinden. Siehe [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) für Codebeispiele.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
