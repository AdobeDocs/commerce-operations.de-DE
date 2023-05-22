---
title: Remote-Speicher für Commerce in Cloud-Infrastruktur
description: Siehe Anleitungen zum Einrichten von Remote-Speicher für Adobe Commerce in der Cloud-Infrastruktur.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Remote-Speicher für Commerce in Cloud-Infrastruktur konfigurieren

Beginnen Sie mit der `ece-tools` Package 2002.1.5 können Sie eine Umgebungsvariable verwenden, um das Remote-Speichermodul zu aktivieren. Das Remote-Speichermodul verfügt jedoch über _begrenzt_ Unterstützung von Adobe Commerce für Cloud-Infrastruktur. Adobe kann keine vollständige Fehlerbehebung beim Speicheradapterdienst von Drittanbietern durchführen.

## Umgebungsvariable

Die `REMOTE_STORAGE` wird während der [Bereitstellungsphase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) eines Cloud-Infrastrukturprojekts.

### `REMOTE_STORAGE`

- **Standard**—_Nicht festgelegt_
- **Version**—Commerce 2.4.2 und höher

Konfigurieren Sie eine _Speicheradapter_ , um Mediendateien mithilfe eines Speicherdienstes wie AWS S3 in einem beständigen Remote-Speicherbehälter zu speichern. Aktivieren Sie das Remote-Speichermodul, um die Leistung bei Cloud-Projekten mit komplexen Multi-Server-Konfigurationen zu verbessern, die Ressourcen gemeinsam nutzen müssen. Im Folgenden finden Sie ein Beispiel für die Konfiguration der Remote-Datenspeicherung mit dem `.magento.env.yaml` Datei:

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

### Variable mit Cloud CLI festlegen

Legen Sie die `REMOTE_STORAGE` als [Variable auf Umgebungsebene](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) damit Dateien nicht von Produktions-, Staging- und Integrationsumgebungen gemeinsam verwendet werden. Das Festlegen der Variablen auf Umgebungsebene bietet die Flexibilität, nur Remote-Speicher in ausgewählten Umgebungen zu verwenden, z. B. den Ausschluss der Verwendung der Integrationsumgebung durch Remote-Speicher.

**So fügen Sie die Remote-Speichervariable mithilfe der Cloud-CLI hinzu**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Dadurch wird eine `REMOTE_STORAGE` mit der angegebenen JSON-Konfiguration. Die `REMOTE_STORAGE` verwendet eine JSON-Zeichenfolge, um den Remote-Speicher zu konfigurieren. Im Folgenden finden Sie ein Beispiel für eine JSON-Konfiguration:

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

Nachdem Sie die Konfiguration und Bereitstellung erstellt haben, sollten die Bereitstellungsprotokolle Informationen zur Remote-Speicherkonfiguration enthalten, z. B. `INFO: Remote storage driver set to: "aws-s3"`

### Variable mit Projekt-Web-Schnittstelle festlegen

Alternativ können Sie die Variable über die Projekt-Webschnittstelle zur entsprechenden Umgebung hinzufügen.

**So fügen Sie die Remote-Speichervariable über die Projekt-Webschnittstelle hinzu**:

1. Im _Projekt-Webschnittstelle_, wählen Sie die Umgebung links aus.

1. Klicken Sie auf **Umgebung konfigurieren** Symbol.

1. Im _Umgebung konfigurieren_ Ansicht, klicken Sie auf die **Variablen** Registerkarte.

1. Klicken **Variable hinzufügen**.

1. Im _Name_ Feld, eingeben `REMOTE_STORAGE`

1. Im _Wert_ -Feld die JSON-Konfiguration hinzu.

1. Auswählen **JSON-Wert** und **Sensitiv**; Auswahl aufheben **Vererbung durch untergeordnete Umgebungen**.

1. Klicken **Variable hinzufügen**.

### Optionale Authentifizierung verwenden

Die `key` und `secret` sind optional. Wenn Sie die Variable erstellen, können Sie die `key` und `secret` durch Auswahl der `sensitive` -Option. Mit dieser Einstellung sind die Werte nicht in der Web-Oberfläche sichtbar. Siehe [Variablenanzeige](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) im _Leitfaden zu Commerce on Cloud Infrastructure_.

Wenn Sie eine andere Authentifizierungsmethode verwenden möchten, lassen Sie die `key` und `secret` aus der JSON-Konfiguration. Konfigurieren Sie die alternative Authentifizierungsmethode und überprüfen Sie, ob der Server für den S3-Bucket autorisiert ist.

### Remote-Speicher synchronisieren

Nachdem Sie das Remote Storage-Modul aktiviert haben, synchronisieren Sie die aktuellen Mediendateien mit dem Remote Store-Speicherort.

**So starten Sie die Synchronisierung**:

1. Verwenden Sie SSH, um sich bei der Remote-Umgebung mit konfiguriertem Remote-Speicher anzumelden.

1. Starten Sie die Synchronisierung.

```bash
bin/magento remote-storage:sync 
```

## Schnelle Konfiguration

Wenn Sie die Remote-Speicherlösung mit einem Adobe Commerce-Projekt in der Cloud-Infrastruktur verwenden möchten, verwenden Sie die [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) Leitlinien _Fastly_ Dokumentation, um sicherzustellen, dass die Fastly-Bildoptimierung mit AWS S3 funktioniert.

Seien Sie auf Ihre [Schnelle Anmeldeinformationen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Verwenden Sie in Pro-Projekten SSH, um eine Verbindung zu Ihrem Server herzustellen und die Fastly-Anmeldeinformationen von der `/mnt/shared/fastly_tokens.txt` -Datei. Staging- und Produktionsumgebungen verfügen über eindeutige Anmeldeinformationen. Sie müssen die Anmeldeinformationen für jede Umgebung abrufen.

Fahren Sie mit den folgenden Aufgaben mit der Einrichtung des Remote-Speichers für Cloud-Projekte fort:

1. Konfigurieren Sie eine [Schnelle Backend-Integration](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Erstellen der VCL-Logik für [AWS S3-Authentifizierung](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Erstellen der VCL-Logik für [Backend-Anforderungen an den AWS S3-Behälter](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
