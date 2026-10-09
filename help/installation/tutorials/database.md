---
title: Erstellen des Datenbankschemas
description: Führen Sie die folgenden Schritte aus, um eine Datenbank für Ihr Adobe Commerce-Projekt zu erstellen.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '49'
ht-degree: 0%
---
# Erstellen des Datenbankschemas

Bevor Sie diesen Befehl ausführen, müssen Sie [die Bereitstellungskonfiguration erstellen oder aktualisieren](deployment.md).

## Datenbank konfigurieren und Daten hinzufügen

Befehlsverwendung:

```shell
bin/magento setup:db-schema:upgrade
```

Geben Sie Folgendes ein, um den Status der Datenbank anzuzeigen

```shell
bin/magento setup:db:status
```
