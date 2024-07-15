---
title: Migrationsübersicht
description: Erfahren Sie, wie Sie mit der Migration von Daten von Magento 1 zu Magento 2 mit dem  [!DNL Data Migration Tool] beginnen.
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Migrationsübersicht

Bevor Sie mit der Migration beginnen, beenden Sie alle Magento 1 Cron-Aufträge.

Befolgen Sie während des Migrationsprozesses die folgenden allgemeinen Regeln für eine erfolgreiche Migration:

1. **Nehmen Sie keine** Änderungen am Magento 1 Admin vor, mit Ausnahme der Auftragsverwaltung (Versand, Erstellung von Rechnungen und Kreditkarten).
1. **Ändern Sie keinen Code**
1. **Nehmen Sie keine** Änderungen an der Magento 2 Admin- und Storefront vor.

>[!TIP]
>
>Alle Vorgänge in der Magento 1 Storefront sind erlaubt.

## Führen Sie die [!DNL Data Migration Tool] aus.

In diesem Abschnitt wird gezeigt, wie Sie den [!DNL Data Migration Tool] ausführen, um Einstellungen, Daten oder inkrementelle Änderungen zu migrieren.

### Erste Schritte

1. Melden Sie sich beim Anwendungsserver als Benutzer an oder wechseln Sie zu einem Benutzer mit Schreibberechtigung für das Dateisystem. Siehe [Wechseln zum Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md).

   Wenn Sie die Bash-Shell verwenden, können Sie die folgende Syntax verwenden, um zum Dateisysteminhaber zu wechseln und den Befehl gleichzeitig einzugeben:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Wenn der Dateisysteminhaber keine Anmeldung zulässt, können Sie Folgendes tun:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Um Magento-Befehle aus einem beliebigen Verzeichnis auszuführen, fügen Sie `<magento_root>/bin` zu Ihrem System `PATH` hinzu.

   Da Muscheln eine andere Syntax haben, sollten Sie einen Verweis wie [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables) konsultieren.

   Beispiel-Bash-Shell für CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Optional können Sie die Befehle wie folgt ausführen:

   - `cd <magento_root>/bin` und führen Sie sie als `./magento <command name>` aus
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` ist ein Unterverzeichnis Ihres Webserver-Basisverzeichnisses.

### Befehlssyntax

Nachfolgend finden Sie ein typisches Befehlsbeispiel:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

- `<mode>` kann sein: [`settings`](settings.md), [`data`](data.md) oder [`delta`](delta.md)
- `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.
- `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.
- `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`; dieses Argument ist erforderlich.

>[!NOTE]
>
>Protokolle werden in das Verzeichnis `<magento_root>/var/` geschrieben.


## Migrationsreihenfolge

Bei der Erstellung des [!DNL Data Migration Tool] gingen wir von der folgenden Datenübertragungssequenz aus:

1. [Einstellungen](settings.md)
1. [Daten](data.md)
1. [Änderungen](delta.md)

Es wird dringend empfohlen, Daten in derselben Reihenfolge zu migrieren.
