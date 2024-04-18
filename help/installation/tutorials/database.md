---
title: Datenbankschema erstellen
description: Führen Sie diese Schritte aus, um eine Datenbank für Ihr Adobe Commerce-Projekt zu erstellen.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
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
