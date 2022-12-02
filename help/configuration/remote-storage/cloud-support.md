---
title: Remote-Speicher für Commerce in Cloud-Infrastruktur
description: Siehe Anleitungen zum Einrichten von Remote-Speicher für Adobe Commerce in der Cloud-Infrastruktur.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Remote-Speicher für Commerce in Cloud-Infrastruktur konfigurieren

Wenn Sie die Remote-Speicherlösung mit einem Adobe Commerce-Projekt in der Cloud-Infrastruktur verwenden möchten, verwenden Sie die [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) Leitlinien _Fastly_ Dokumentation, um sicherzustellen, dass die Fastly-Bildoptimierung mit AWS S3 funktioniert.

Seien Sie auf Ihre [Schnelle Anmeldeinformationen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Verwenden Sie in Pro-Projekten SSH, um eine Verbindung zu Ihrem Server herzustellen und die Fastly-Anmeldeinformationen von der `/mnt/shared/fastly_tokens.txt` -Datei. Staging- und Produktionsumgebungen verfügen über eindeutige Anmeldeinformationen. Sie müssen die Anmeldeinformationen für jede Umgebung abrufen.

Fahren Sie mit den folgenden Aufgaben mit der Einrichtung des Remote-Speichers für Cloud-Projekte fort:

1. Konfigurieren Sie eine [Schnelle Backend-Integration](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Erstellen der VCL-Logik für [AWS S3-Authentifizierung](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Erstellen der VCL-Logik für [Backend-Anforderungen an den AWS S3-Behälter](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
