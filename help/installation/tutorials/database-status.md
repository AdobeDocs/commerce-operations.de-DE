---
title: Überprüfen des Datenbankstatus
description: Führen Sie diese Schritte aus, um den Status Ihrer Adobe Commerce- oder Magento Open Source-Datenbank zu überprüfen.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 2%

---


# Überprüfen des Datenbankstatus

Bevor Sie diesen Befehl ausführen, müssen Sie [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md).

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
| 1 | Einige Module verwenden Codeversionen, die neuer oder älter als die Datenbank sind | Ausführen [`magento setup:upgrade`](database-upgrade.md) , um das Datenbankschema zu aktualisieren und `composer update` aus dem Stammverzeichnis der Anwendung, um Komponentenabhängigkeiten zu aktualisieren |
| 2 | `magento setup:upgrade` ist erforderlich | [`magento setup:upgrade`](database-upgrade.md) , um die [Datenbankschema](https://glossary.magento.com/database-schema) |