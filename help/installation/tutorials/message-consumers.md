---
title: Konfigurieren von Nachrichtenbenutzern
description: Führen Sie diese Schritte aus, um das Verhalten von Verbrauchern in der Adobe Commerce- oder Magento Open Source-Nachrichtenwarteschlange zu konfigurieren.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Konfigurieren von Nachrichtenbenutzern

Bevor Sie diesen Befehl ausführen, müssen Sie Folgendes tun: *oder* Sie müssen [Installieren des Programms](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Datenbankschema erstellen](database.md)

## Verbraucherverhalten konfigurieren

Die Konfiguration des Verbraucherverhaltens erfolgt durch Senden von Schlüssel/Wert-Paaren innerhalb der Setup-Funktion:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

{{$include /help/_includes/cli-consumers.md}}
