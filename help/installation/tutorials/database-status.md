---
title: Datenbankstatus überprüfen
description: Führen Sie diese Schritte aus, um den Status Ihrer Adobe Commerce-Datenbank zu überprüfen.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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
