---
title: Datenbankschema erstellen
description: Führen Sie die folgenden Schritte aus, um eine Datenbank für Ihre Adobe Commerce oder Magento Open Source zu erstellen.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Datenbankschema erstellen

Bevor Sie diesen Befehl ausführen, müssen Sie [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md).

## Datenbank konfigurieren und Daten hinzufügen

Befehlsverwendung:

```bash
bin/magento setup:db-schema:upgrade
```

Um den Status der Datenbank anzuzeigen, geben Sie

```bash
bin/magento setup:db:status
```
