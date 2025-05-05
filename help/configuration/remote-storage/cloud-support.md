---
title: Remote-Speicher für Commerce auf Cloud-Infrastruktur
description: Siehe Anleitung zum Einrichten von Remote-Speicher für Adobe Commerce in der Cloud-Infrastruktur.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Konfigurieren des Remote-Speichers für Commerce in der Cloud-Infrastruktur

Ab dem `ece-tools`-Paket 2002.1.5 können Sie eine Umgebungsvariable verwenden, um das Remote-Speichermodul zu aktivieren. Das Remote-Speichermodul bietet jedoch _begrenzte_ Unterstützung für Adobe Commerce in der Cloud-Infrastruktur. Adobe kann den Speicheradapterdienst eines Drittanbieters nicht vollständig beheben.

## Umgebungsvariable

Die Variable `REMOTE_STORAGE` wird während der [Bereitstellungsphase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=de) eines Cloud-Infrastrukturprojekts verwendet.

### `REMOTE_STORAGE`

- **Standard**—_Nicht festgelegt_
- **Version**—Commerce 2.4.2 und höher

Konfigurieren Sie einen _Speicheradapter_, um Mediendateien mithilfe eines Speicherdienstes wie AWS S3 in einem persistenten Remote-Speicher-Container zu speichern. Aktivieren Sie das Remote-Speichermodul, um die Leistung in Cloud-Projekten mit komplexen Multi-Server-Konfigurationen zu verbessern, die Ressourcen gemeinsam nutzen müssen. Im Folgenden finden Sie ein Beispiel für die Remote-Speicherkonfiguration unter Verwendung der `.magento.env.yaml`:

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Festlegen einer Variablen mit Cloud CLI

Legen Sie die `REMOTE_STORAGE`-Variable als [Variable auf Umgebungsebene) fest](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=de) sodass Dateien nicht zwischen Produktions-, Staging- und Integrationsumgebungen freigegeben werden. Das Festlegen der Variablen auf Umgebungsebene bietet die Flexibilität, nur den Remote-Speicher in ausgewählten Umgebungen zu verwenden, z. B. die Verwendung des Remote-Speichers in der Integrationsumgebung auszuschließen.

**So fügen Sie die Remote-Speichervariable über die Cloud-CLI**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Dadurch wird eine `REMOTE_STORAGE` Variable mit der angegebenen JSON-Konfiguration erstellt. Die `REMOTE_STORAGE`-Variable benötigt eine JSON-Zeichenfolge, um den Remote-Speicher zu konfigurieren. Im Folgenden finden Sie eine JSON-Beispielkonfiguration:

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

Nachdem Sie die Konfiguration erstellt und bereitgestellt haben, sollten die Bereitstellungsprotokolle Informationen zur Remote-Speicherkonfiguration enthalten, z. B. `INFO: Remote storage driver set to: "aws-s3"`

### Festlegen einer Variablen mit Project Web Interface

Alternativ können Sie die Project-Web-Schnittstelle verwenden, um die Variable der entsprechenden Umgebung hinzuzufügen.

**So fügen Sie die Remote-Speichervariable über die Project Web Interface-** hinzu:

1. Wählen _in „Projekt-_&quot; die Umgebung auf der linken Seite aus.

1. Klicken Sie auf **Symbol** Umgebung konfigurieren“.

1. Klicken Sie in der _Umgebung konfigurieren_ auf die Registerkarte **Variablen**.

1. Klicken Sie **Variable hinzufügen**.

1. Geben Sie _Feld_ Name“ `REMOTE_STORAGE`

1. Fügen Sie im _Wert_ die JSON-Konfiguration hinzu.

1. Wählen Sie **JSON-** und **sensitiv** aus, deselektieren Sie **Vererbt durch untergeordnete Umgebungen**.

1. Klicken Sie **Variable hinzufügen**.

### Optionale Authentifizierung verwenden

`key` und `secret` sind optional. Wenn Sie die Variable erstellen, können Sie die `key` und `secret` ausblenden, indem Sie die Option `sensitive` auswählen. Bei dieser Einstellung sind die Werte nicht in der Web-Oberfläche sichtbar. Siehe [Sichtbarkeit von Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=de#visibility) im Handbuch zu _Commerce in Cloud-Infrastrukturen_.

Wenn Sie eine andere Authentifizierungsmethode verwenden möchten, lassen Sie die `key` und `secret` aus der JSON-Konfiguration weg. Konfigurieren Sie die alternative Authentifizierungsmethode und überprüfen Sie, ob der Server für den S3-Bucket autorisiert ist.

### Remote-Speicher synchronisieren

Synchronisieren Sie nach der Aktivierung des Remote-Speichermoduls die aktuellen Mediendateien mit dem Remote-Speicherort.

**Starten der Synchronisierung**:

1. Verwenden Sie SSH, um sich bei der Remote-Umgebung mit konfiguriertem Remote-Speicher anzumelden.

1. Starten Sie die Synchronisierung.

```bash
bin/magento remote-storage:sync 
```

## Fastly-Konfiguration

Wenn Sie sich für die Verwendung der Remote-Speicherlösung mit einem Adobe Commerce in einem Cloud-Infrastrukturprojekt entscheiden, verwenden Sie die [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3)-Anleitung in der _Fastly_-Dokumentation, um sicherzustellen, dass Fastly Image Optimization mit AWS S3 funktioniert.

Seien Sie mit Ihren [Fastly-Anmeldedaten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#get-fastly-credentials) vorbereitet. Bei Pro-Projekten stellen Sie mit SSH eine Verbindung zu Ihrem Server her und erhalten die Fastly-Anmeldedaten aus der `/mnt/shared/fastly_tokens.txt`. Staging- und Produktionsumgebungen verfügen über eindeutige Anmeldeinformationen. Sie müssen die Anmeldeinformationen für jede Umgebung abrufen.

Fahren Sie mit den folgenden Aufgaben mit dem Einrichten des Remote-Speichers für Cloud-Projekte fort:

1. Konfigurieren einer [Fastly-Backend-Integration](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Erstellen Sie eine VCL-Logik für die [AWS S3-](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Erstellen Sie eine VCL-Logik für [Backend-Anfragen an den AWS S3-Bucket](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
