---
title: Migrationsübersicht
description: Erfahren Sie, wie Sie mit der Migration von Daten von Magento 1 auf Magento 2 mit dem  [!DNL Data Migration Tool] beginnen.
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Migrationsübersicht

Bevor Sie mit der Migration beginnen, stoppen Sie alle Magento 1-Cron-Aufträge.

Befolgen Sie während des Migrationsprozesses die folgenden allgemeinen Regeln für eine erfolgreiche Migration:

1. **Nehmen Sie** Änderungen am Magento 1-Administrator vor, mit Ausnahme der Auftragsverwaltung (Versand, Rechnungserstellung und Gutschriften)
1. **Code** ändern
1. **Nehmen Sie** Änderungen in der Magento 2 Admin- und Storefront vor

>[!TIP]
>
>Alle Vorgänge in der Magento 1-Storefront sind zulässig.

## Ausführen des [!DNL Data Migration Tool]

In diesem Abschnitt wird gezeigt, wie Sie den [!DNL Data Migration Tool] ausführen, um Einstellungen, Daten oder inkrementelle Änderungen zu migrieren.

### Erste Schritte

1. Melden Sie sich beim Anwendungsserver als Benutzer an oder wechseln Sie zu einem Benutzer mit Berechtigungen zum Schreiben in das Dateisystem. Siehe [Wechseln zum Dateisystembesitzer](../../../installation/prerequisites/file-system/overview.md).

   Wenn Sie die Bash-Shell verwenden, können Sie die folgende Syntax verwenden, um zum Dateisystembesitzer zu wechseln und den Befehl gleichzeitig einzugeben:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Wenn der Dateisystembesitzer keine Anmeldungen zulässt, können Sie Folgendes tun:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Um Magento-Befehle aus einem beliebigen Verzeichnis auszuführen, fügen Sie `<magento_root>/bin` zu Ihrem `PATH` hinzu.

   Da Shell unterschiedliche Syntax haben, sollten Sie einen Verweis wie [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables) heranziehen.

   Beispiel-Bash-Shell für CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Optional können Sie die Befehle wie folgt ausführen:

   - `cd <magento_root>/bin` und als `./magento <command name>` ausführen
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` ist ein Unterverzeichnis Ihres Webserver-Stammverzeichnisses.

### Befehlssyntax

Im Folgenden finden Sie ein typisches Befehlsbeispiel:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

- `<mode>` können sein: [`settings`](settings.md), [`data`](data.md) oder [`delta`](delta.md)
- `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.
- `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn Fehler bei der Integritätsprüfung auftreten.
- `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`. Dieses Argument ist erforderlich.

>[!NOTE]
>
>Protokolle werden in das `<magento_root>/var/` geschrieben.


## Migrationsreihenfolge

Bei der Erstellung des [!DNL Data Migration Tool] haben wir die folgende Datenübertragungssequenz angenommen:

1. [Einstellungen](settings.md)
1. [Daten](data.md)
1. [Änderungen](delta.md)

Es wird dringend empfohlen, Daten in derselben Reihenfolge zu migrieren.
