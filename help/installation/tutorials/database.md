---
title: Erstellen des Datenbankschemas
description: Führen Sie die folgenden Schritte aus, um eine Datenbank für Ihr Adobe Commerce-Projekt zu erstellen.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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
