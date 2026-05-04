---
title: Konfigurieren von Nachrichtenkonsumenten
description: Führen Sie die folgenden Schritte aus, um das Verhalten der Nachrichtenwarteschlange-Verbraucher von Adobe Commerce zu konfigurieren.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
