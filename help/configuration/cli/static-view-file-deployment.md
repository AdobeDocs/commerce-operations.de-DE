---
title: Bereitstellen von statischen Ansichtsdateien
description: Erfahren Sie, wie Sie im Produktionsmodus statische Dateien in das Commerce-Dateisystem schreiben.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# Bereitstellen von statischen Ansichtsdateien

{{file-system-owner}}

Mit dem Bereitstellungsbefehl für statische Ansichtsdateien können Sie statische Dateien in das Commerce-Dateisystem schreiben, wenn die Commerce-Software für [Produktionsmodus](../bootstrap/application-modes.md#production-mode).

Der Begriff _statische Ansichtsdatei_ bezieht sich auf Folgendes:

- &quot;Statisch&quot;bedeutet, dass sie für eine Site zwischengespeichert werden kann (d. h., die Datei wird nicht dynamisch generiert). Beispiele sind Bilder und CSS, die aus LESS generiert wurden.
- &quot;Ansicht&quot;bezieht sich auf die Präsentationsschicht (aus MVC).

Statische Ansichtsdateien befinden sich im `<magento_root>/pub/static` und einige werden im `<magento_root>/var/view_preprocessed` -Verzeichnis.

Die Bereitstellung von statischen Ansichtsdateien wird wie folgt von den Anwendungsmodi beeinflusst:

- [Standard](../bootstrap/application-modes.md#default-mode) und [Entwickler](../bootstrap/application-modes.md#developer-mode) Modi: Commerce erstellt sie nach Bedarf, der Rest wird jedoch in einer Datei zwischengespeichert, um den Zugriff zu beschleunigen.
- [Produktion](../bootstrap/application-modes.md#production-mode) mode: Statische Dateien sind _not_ generiert oder zwischengespeichert.

Sie müssen statische Ansichtsdateien manuell in das Commerce-Dateisystem schreiben, indem Sie den in diesem Thema besprochenen Befehl verwenden. Danach können Sie die Berechtigungen einschränken, um Ihre Sicherheitslücken zu begrenzen und ein versehentliches oder bösartiges Überschreiben von Dateien zu verhindern.

>[!WARNING]
>
>_Nur Entwicklermodus_: Wenn Sie ein neues Modul installieren oder aktivieren, werden möglicherweise neue JavaScript-, CSS-, Layouts usw. geladen. Um Probleme mit statischen Dateien zu vermeiden, müssen Sie die alten Dateien bereinigen, um sicherzustellen, dass Sie alle Änderungen für das neue Modul erhalten. Sie können generierte statische Ansichtsdateien auf verschiedene Arten bereinigen. Siehe Abschnitt [Thema zum Zwischenspeichern statischer Dateien mit Details bereinigen](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) für weitere Informationen.

**So stellen Sie statische Ansichtsdateien bereit**:

1. Melden Sie sich beim Commerce-Server als oder an. [Wechseln zum Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Löschen Sie den Inhalt von `<magento_root>/pub/static`, mit Ausnahme der `.htaccess` -Datei. Löschen Sie diese Datei nicht.
1. Implementierungstool für statische Ansichtsdateien ausführen `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Wenn Sie die Zusammenführung von statischen Ansichtsdateien in der Admin-Konsole aktivieren, wird die `pub/static` Verzeichnissystem muss schreibbar sein.

   Befehlsoptionen:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

In der folgenden Tabelle werden die Parameter und Werte dieses Befehls erläutert.

| Option | Beschreibung | Erforderlich? |
| ------ | ----------- | --------- |
| `<languages>` | Durch Leerzeichen getrennte Liste von [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) Sprachcodes, für die statische Ansichtsdateien ausgegeben werden sollen. (Der Standardwert ist `en_US`.<br>Suchen Sie die Liste, indem Sie Folgendes ausführen: `bin/magento info:language:list` | Nein |
| `--language (-l)` | Generieren Sie Dateien nur für die angegebenen Sprachen. Standardmäßig werden Dateien für alle ISO-639-Sprachcodes generiert, ohne dass eine Option angegeben ist. Sie können den Namen eines Sprachcodes gleichzeitig angeben. Der Standardwert ist **all**.<br>Beispiel: `--language en_US --language es_ES` | Nein |
| `--exclude-language` | Generieren Sie Dateien für die angegebenen Sprachcodes. Standardmäßig wird ohne Angabe einer Option nichts ausgeschlossen. Sie können den Namen eines Sprachcodes oder eine kommagetrennte Liste von Sprachcodes angeben. Der Standardwert ist **Keine**. | Nein |
| `--theme <theme>` | Designs, für die statische Inhalte bereitgestellt werden sollen. Der Standardwert ist **all**.<br>Beispiel: `--theme Magento/blank --theme Magento/luma` | Nein |
| `--exclude-theme <theme>` | Themen, die bei der Bereitstellung statischer Inhalte ausgeschlossen werden sollen. Der Standardwert ist **Keine**.<br>Beispiel, `--exclude-theme Magento/blank` | Nein |
| `--area (-a)` | Generieren Sie Dateien nur für die angegebenen Bereiche. Standardmäßig werden Dateien für alle Bereiche generiert, ohne dass eine Option angegeben ist. Gültige Werte sind `adminhtml` und `frontend`. Der Standardwert ist **all**.<br>Beispiel: `--area adminhtml` | Nein |
| `--exclude-area` | Generieren Sie keine Dateien für die angegebenen Bereiche. Standardmäßig wird ohne Angabe einer Option nichts ausgeschlossen. Der Standardwert ist **Keine**. | Nein |
| `--jobs (-j)` | Aktivieren Sie die parallele Verarbeitung mit der angegebenen Anzahl von Aufträgen. Der Standardwert ist 0 (nicht in parallelen Prozessen ausgeführt). Der Standardwert ist **0**. | Nein |
| `--symlink-locale` | Erstellen Sie Symlinks für die Dateien dieser Gebietsschemas, die zur Bereitstellung übergeben werden, aber keine Anpassungen aufweisen. | Nein |
| `--content-version=CONTENT-VERSION` | Benutzerdefinierte Version von statischem Inhalt kann verwendet werden, wenn die Bereitstellung auf mehreren Knoten ausgeführt wird, um sicherzustellen, dass die statische Inhaltsversion identisch ist und die Zwischenspeicherung ordnungsgemäß funktioniert. | Nein |
| `--no-javascript` | JavaScript-Dateien nicht bereitstellen | Nein |
| `--no-css` | Stellen Sie keine CSS-Dateien bereit. | Nein |
| `--no-less` | Stellen Sie keine LESS-Dateien bereit. | Nein |
| `--no-images` | Stellen Sie keine Bilder bereit. | Nein |
| `--no-fonts` | Stellen Sie keine Schriftartdateien bereit. | Nein |
| `--no-html` | Stellen Sie keine HTML-Dateien bereit. | Nein |
| `--no-misc` | Stellen Sie keine anderen Dateitypen bereit: MD, JBF, CSV, JSON, TXT, HTC, SWF | Nein |
| `--no-html-minify` | Minimieren Sie keine HTML-Dateien. | Nein |
| `-s <quick\|standard\|compact>` | Definieren Sie die Implementierungsstrategie. Verwenden Sie diese Optionen nur, wenn Sie mehrere lokale Optionen haben.<ul><li>Verwenden Sie die [Schnellstrategie](static-view-file-strategy.md#quick-strategy) um die Bereitstellungszeit zu minimieren. Dies ist die standardmäßige Befehlsoption, falls nicht anders angegeben.</li><li>Verwenden Sie die [Standardstrategie](static-view-file-strategy.md#standard-strategy) , um alle statischen Ansichtsdateien für alle Pakete bereitzustellen.</li><li>Verwenden Sie die [kompakte Strategie](static-view-file-strategy.md#compact-strategy) um Speicherplatz auf dem Server zu sparen.</li></ul> | Nein |
| `--no-parent` | Generieren Sie keine Dateien für die übergeordneten Designs des aktuellen Designs. Es wird dringend empfohlen, dieses Flag zu verwenden, wenn Sie nicht explizit das übergeordnete Design des aktuellen Designs verwenden, das Sie bereitstellen möchten. Dies erhöht die Geschwindigkeit des Prozesses erheblich. Dieses Flag ist in Commerce 2.4.2 verfügbar. | Nein |
| `--force (-f)` | Bereitstellen von Dateien in einem beliebigen Modus. (Standardmäßig kann das Werkzeug zur Bereitstellung statischer Inhalte nur im Produktionsmodus ausgeführt werden. Verwenden Sie diese Option, um sie im Standard- oder Entwicklermodus auszuführen. | Nein |

>[!INFO]
>
>Wenn Werte für `<languages>` und `--language`, `<languages>` hat Vorrang.

## Beispiele

Im Folgenden finden Sie einige Beispielbefehle.

### Ausschließen eines Designs und HTML-Minimierung

Der folgende Befehl stellt statische Inhalte für die US-amerikanische Sprache (`en_US`), schließt das mit Commerce bereitgestellte Luma-Design aus und minimiert keine HTML-Dateien.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Beispielausgabe:

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

Der folgende Befehl stellt nur JavaScript mit 4 Aufträgen und einer standardmäßigen Bereitstellungsstrategie bereit:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

Der folgende Befehl stellt nur CSS und LESS mit 3 Aufträgen und einer schnellen Bereitstellungsstrategie bereit:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Erstellen von statischen Ansichtsdateien für ein Design und einen Bereich

Der folgende Befehl generiert statische Ansichtsdateien für alle Sprachen, nur für den Frontend-Bereich, nur für das Commerce Luma-Design, ohne Schriftarten zu generieren:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Beispielausgabe:

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Bereitstellen von statischen Ansichtsdateien ohne Installation von Commerce

Möglicherweise möchten Sie den Bereitstellungsprozess in einer separaten, produktionsfremden Umgebung ausführen, um Build-Prozesse auf sensiblen Produktionsmaschinen zu vermeiden.

Gehen Sie dazu wie folgt vor:

1. Ausführen [`bin/magento app:config:dump`](../cli/export-configuration.md) , um die Konfiguration aus Ihrem Produktionssystem zu exportieren.
1. Kopieren Sie die exportierten Dateien in die Nicht-Produktions-Codebasis.
1. Statische Ansichtsdateien bereitstellen: `bin/magento setup:static-content:deploy`

## Fehlerbehebung für das Bereitstellungswerkzeug für statische Ansichtsdateien

[Installieren Sie zuerst die Commerce-Software](../../installation/overview.md); andernfalls können Sie das Bereitstellungswerkzeug für statische Ansichtsdateien nicht ausführen.

**Symptom**: Der folgende Fehler wird angezeigt, wenn Sie das Bereitstellungswerkzeug für statische Ansichtsdateien ausführen:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Lösung**:

Führen Sie die folgenden Schritte aus:

1. Installieren Sie die Commerce-Software mit dem [Befehlszeile](../../installation/composer.md).
1. Melden Sie sich beim Anwendungsserver als [Switch zu](../../installation/prerequisites/file-system/overview.md), der Dateisysteminhaber.
1. Löschen Sie den Inhalt von `<app_root>/pub/static` Verzeichnis, mit Ausnahme der `.htaccess` -Datei. Löschen Sie diese Datei nicht.
1. Statische Ansichtsdateien bereitstellen: `bin/magento setup:static-content:deploy`

## Tipp für Entwickler, die das Werkzeug zur Bereitstellung statischer Inhalte anpassen

Verwenden Sie beim Erstellen einer benutzerdefinierten Implementierung des Tools für die Bereitstellung statischer Inhalte nur das Schreiben von Atomdateien für Dateien, die auf dem Client verfügbar sein sollten. Wenn Sie nicht atomare Dateischreibungen verwenden, werden diese Dateien möglicherweise auf den Client mit partiellem Inhalt geladen.

Eine der Optionen, um es atomisch zu gestalten, besteht darin, in Dateien zu schreiben, die in einem temporären Verzeichnis gespeichert sind, und sie nach dem Schreiben in das Zielverzeichnis zu kopieren oder in dieses zu verschieben (von wo sie auf den Client geladen werden). Weitere Informationen zum Schreiben in Dateien finden Sie unter [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
