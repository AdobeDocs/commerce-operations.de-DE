---
title: Datenbankstatus überprüfen
description: Führen Sie diese Schritte aus, um den Status Ihrer Adobe Commerce-Datenbank zu überprüfen.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
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
source-wordcount: '104'
ht-degree: 3%
---
# Datenbankstatus überprüfen

Bevor Sie diesen Befehl ausführen, müssen Sie [die Bereitstellungskonfiguration erstellen oder aktualisieren](deployment.md).

## Befehlsverwendung

, um den Status der Datenbank zu überprüfen.

```shell
bin/magento setup:db:status
```

Dieser Befehl hat keine Argumente oder Optionen.

Beispielausgabe folgt:

```text
All modules are up to date.
```

Der Befehl gibt einen der folgenden Exitcodes zurück:

| Exitcode | Beschreibung | Vorgeschlagene Aktion |
|--------------|--------------|---------------|
| 0 | Normal | Keine |
| 1 | Einige Module verwenden Code-Versionen, die neuer oder älter als die Datenbank sind | Führen Sie [`magento setup:upgrade`](database-upgrade.md) aus, um das Datenbankschema zu aktualisieren, und führen Sie `composer update` vom Anwendungsstammverzeichnis aus, um die Komponentenabhängigkeiten zu aktualisieren |
| 2 | `magento setup:upgrade` ist erforderlich | [`magento setup:upgrade`](database-upgrade.md) des Datenbankschemas |
