---
title: Überprüfen des Datenbankstatus
description: Führen Sie diese Schritte aus, um den Status Ihrer Adobe Commerce-Datenbank zu überprüfen.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# Überprüfen des Datenbankstatus

Bevor Sie diesen Befehl ausführen, müssen Sie [die Bereitstellungskonfiguration erstellen oder aktualisieren](deployment.md).

## Befehlsverwendung

Überprüfen des Datenbankstatus.

```bash
bin/magento setup:db:status
```

Dieser Befehl hat keine Argumente oder Optionen.

Beispielausgabe:

```terminal
All modules are up to date.
```

Der Befehl gibt einen der folgenden Ausstiegscodes zurück:

| Ausstiegscode | Beschreibung | Vorgeschlagene Aktion |
|--------------|--------------|---------------|
| 0 | Normal | Keines |
| 1 | Einige Module verwenden Codeversionen, die neuer oder älter als die Datenbank sind | Führen Sie [`magento setup:upgrade`](database-upgrade.md) aus, um das Datenbankschema zu aktualisieren, und führen Sie `composer update` aus dem Stammverzeichnis der Anwendung aus, um die Komponentenabhängigkeiten zu aktualisieren |
| 2 | `magento setup:upgrade` ist erforderlich | [`magento setup:upgrade`](database-upgrade.md) zum Aktualisieren des Datenbankschemas |
