---
title: Datenbankschema erstellen
description: Führen Sie die folgenden Schritte aus, um eine Datenbank für Ihre Adobe Commerce oder Magento Open Source zu erstellen.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
