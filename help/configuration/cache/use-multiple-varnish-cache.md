---
title: Cache-Leerung mit mehreren Lackinstanzen
description: Erfahren Sie, wie das Löschen von Caches mit mehreren Varnish-Instanzen in Adobe Commerce funktioniert. Best Practices für Konfiguration und Verwaltung
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# Cache-Leerung mit mehreren Lackinstanzen

Adobe Commerce unterstützt standardmäßig mehrere Varnish-Instanzen.

In diesem Abschnitt werden die Grundlagen zum Konfigurieren mehrerer Varnish-Instanzen mit Commerce erläutert.

{{varnish-config-cloud}}

## Konfiguration zum Bereinigen mehrerer Lackinstanzen

Commerce löscht Varnish-Hosts, nachdem Sie Varnish-Hosts mit dem Befehl [`magento setup:config:set`](../../installation/tutorials/deployment.md) konfiguriert haben.

Sie sollten den `--http-cache-hosts`-Parameter verwenden, um eine kommagetrennte Liste von Lack-Hosts und Listener-Ports anzugeben. (Hosts dürfen nicht durch Leerzeichen getrennt werden.)

Das Parameterformat muss `<hostname or ip>:<listen port>` sein, wobei Sie `<listen port>` auslassen können, wenn es sich um Port 80 handelt.

Beispiel:

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Sie können dann alle Varnish-Hosts bereinigen, wenn Sie den Commerce-Cache (auch als _bezeichnet)_ Admin aktualisieren oder die Befehlszeile verwenden.

Um den Cache mithilfe der Admin zu aktualisieren, klicken Sie auf **SYSTEM** > Tools **Cache-Verwaltung** und dann oben auf der Seite auf **Magento-** leeren. (Sie können auch einzelne Cache-Typen aktualisieren.)

Um den Cache mehrerer Varnish-Instanzen von der CLI zu aktualisieren, verwenden Sie den [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)-Befehl als [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
