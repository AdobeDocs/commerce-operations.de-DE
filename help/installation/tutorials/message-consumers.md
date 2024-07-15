---
title: Konfigurieren von Nachrichtenbenutzern
description: Führen Sie diese Schritte aus, um das Verhalten von Verbrauchern in der Adobe Commerce-Nachrichtenwarteschlange zu konfigurieren.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Konfigurieren von Nachrichtenbenutzern

Bevor Sie diesen Befehl ausführen, müssen Sie die folgenden *oder* ausführen, die Anwendung [installieren](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Datenbankschema erstellen](database.md)

## Verbraucherverhalten konfigurieren

Die Konfiguration des Verbraucherverhaltens erfolgt durch Senden von Schlüssel/Wert-Paaren innerhalb der Setup-Funktion:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

{{$include /help/_includes/cli-consumers.md}}
