---
title: Migrationsübersicht
description: Erfahren Sie, wie Sie mit der Migration von Daten aus Magento 1 zu Magento 2 beginnen können. [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Migrationsübersicht

Bevor Sie mit der Migration beginnen, beenden Sie alle Cron-Aufträge für Magento 1.

Befolgen Sie während des Migrationsprozesses die folgenden allgemeinen Regeln für eine erfolgreiche Migration:

1. **Nicht** Änderungen am Magento 1 Admin vorzunehmen, mit Ausnahme der Auftragsverwaltung (Versand, Erstellung von Rechnungen und Kreditkarten)
1. **Nicht** Code ändern
1. **Nicht** Änderungen in Magento 2 Admin vornehmen und [storefront](https://glossary.magento.com/storefront)

>[!TIP]
>
>Alle Vorgänge in der Storefront von Magento 1 sind zulässig.

## Führen Sie die [!DNL Data Migration Tool]

In diesem Abschnitt erfahren Sie, wie Sie die [!DNL Data Migration Tool] , um Einstellungen, Daten oder inkrementelle Änderungen zu migrieren.

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

1. Um Magento-Befehle aus einem beliebigen Verzeichnis auszuführen, fügen Sie `<magento_root>/bin` auf Ihr System `PATH`.

   Da Muscheln eine andere Syntax haben, sollten Sie einen Verweis wie [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Beispiel-Bash-Shell für CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Optional können Sie die Befehle wie folgt ausführen:

   - `cd <magento_root>/bin` und führen Sie sie als `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` ist ein Unterverzeichnis Ihres Webserver-Basisverzeichnisses.

### Befehlssyntax

Nachfolgend finden Sie ein typisches Befehlsbeispiel:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

- `<mode>` kann sein: [`settings`](settings.md), [`data`](data.md)oder [`delta`](delta.md)
- `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.
- `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.
- `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`; Dieses Argument ist erforderlich.

>[!NOTE]
>
>Protokolle werden in die `<magento_root>/var/` Verzeichnis.


## Migrationsreihenfolge

Bei der Erstellung der [!DNL Data Migration Tool]wurde die folgende Datenübertragungssequenz angenommen:

1. [Einstellungen](settings.md)
1. [Daten](data.md)
1. [Änderungen](delta.md)

Wir empfehlen dringend, Daten in derselben Reihenfolge zu migrieren.
