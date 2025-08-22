---
title: Konfigurieren von Nachrichtenkonsumenten
description: Führen Sie die folgenden Schritte aus, um das Verhalten der Nachrichtenwarteschlange-Verbraucher von Adobe Commerce zu konfigurieren.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Konfigurieren von Nachrichtenkonsumenten

Bevor Sie diesen Befehl ausführen, müssen Sie Folgendes tun *oder* Sie müssen [die Anwendung installieren](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Erstellen des Datenbankschemas](database.md)

## Verbraucherverhalten konfigurieren

Die Konfiguration des Verbraucherverhaltens erfolgt durch Senden von Schlüssel/Wert-Paaren innerhalb der Einrichtungsfunktion:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
