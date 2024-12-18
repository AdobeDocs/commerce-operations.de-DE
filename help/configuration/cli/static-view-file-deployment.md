---
title: Statische Ansichtsdateien bereitstellen
description: Erfahren Sie, wie Sie im Produktionsmodus statische Dateien in das Commerce-Dateisystem schreiben.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Statische Ansichtsdateien bereitstellen

{{file-system-owner}}

Mit dem Bereitstellungsbefehl für statische Ansichtsdateien können Sie statische Dateien in das Commerce-Dateisystem schreiben, wenn die Commerce-Software für den [Produktionsmodus) ](../bootstrap/application-modes.md#production-mode) ist.

Der Begriff _statische Ansichtsdatei_ bezieht sich auf Folgendes:

- „Statisch“ bedeutet, dass die Datei für eine Site zwischengespeichert werden kann (d. h. die Datei wird nicht dynamisch generiert). Beispiele sind Bilder und CSS, die aus LESS generiert wurden.
- „Ansicht“ bezieht sich auf die Präsentationsebene (aus MVC).

Statische Ansichtsdateien befinden sich im Verzeichnis `<magento_root>/pub/static` und einige werden auch im Verzeichnis `<magento_root>/var/view_preprocessed` zwischengespeichert.

Die Bereitstellung von statischen Ansichtsdateien wird wie folgt von den Anwendungsmodi beeinflusst:

- [Standard](../bootstrap/application-modes.md#default-mode)- und [Entwicklermodus](../bootstrap/application-modes.md#developer-mode): Commerce generiert sie bei Bedarf, aber der Rest wird zur Beschleunigung des Zugriffs in einer Datei zwischengespeichert.
- [Produktion](../bootstrap/application-modes.md#production-mode) Modus: Statische Dateien werden _generiert_ zwischengespeichert.

Sie müssen statische Ansichtsdateien manuell unter Verwendung des in diesem Thema beschriebenen Befehls in das Commerce-Dateisystem schreiben. Danach können Sie die Berechtigungen einschränken, um Ihre Sicherheitslücken zu begrenzen und versehentliches oder böswilliges Überschreiben von Dateien zu verhindern.

>[!WARNING]
>
>_Nur Entwicklermodus_: Wenn Sie ein neues Modul installieren oder aktivieren, werden möglicherweise neue JavaScript-, CSS-, Layout-Elemente usw. geladen. Um Probleme mit statischen Dateien zu vermeiden, müssen Sie die alten Dateien bereinigen, um sicherzustellen, dass Sie alle Änderungen für das neue Modul erhalten. Sie haben verschiedene Möglichkeiten, generierte statische Ansichtsdateien zu bereinigen. Weitere Informationen finden [ unter „Bereinigen des Cache für statische ](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache)&quot;.

**Bereitstellen von statischen Ansichtsdateien**:

1. Melden Sie sich beim Commerce-Server an oder [ Sie zum Dateisystembesitzer ](../../installation/prerequisites/file-system/overview.md).
1. Löschen Sie den Inhalt von `<magento_root>/pub/static` mit Ausnahme der `.htaccess`. Diese Datei nicht löschen.
1. Führen Sie das Bereitstellungs-Tool für statische Ansichtsdateien `<magento_root>/bin/magento setup:static-content:deploy` aus.

   >[!INFO]
   >
   >Wenn Sie die Zusammenführung von statischen Ansichtsdateien im Admin-Ordner aktivieren, muss das `pub/static` beschreibbar sein.

   Befehlsoptionen:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

In der folgenden Tabelle werden die Parameter und Werte dieses Befehls erläutert.

| Option | Beschreibung | Erforderlich? |
| ------ | ----------- | --------- |
| `<languages>` | Durch Leerzeichen getrennte Liste von [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php)-Sprachcodes, für die statische Ansichtsdateien ausgegeben werden sollen. (Der Standardwert lautet `en_US`.)<br>Finden Sie die Liste, indem Sie ausführen: `bin/magento info:language:list` | Nein |
| `--language (-l)` | Generieren Sie Dateien nur für die angegebenen Sprachen. Die Standardeinstellung ohne angegebene Option besteht darin, Dateien für alle ISO-639-Sprachcodes zu generieren. Sie können den Namen jeweils eines Sprach-Codes angeben. Der Standardwert ist **all**.<br>Beispiel: `--language en_US --language es_ES` | Nein |
| `--exclude-language` | Generieren von Dateien für die angegebenen Sprachcodes. Wenn keine Option angegeben ist, wird standardmäßig nichts ausgeschlossen. Sie können den Namen eines Sprach-Codes oder eine kommagetrennte Liste von Sprach-Codes angeben. Der Standardwert ist **none**. | Nein |
| `--theme <theme>` | Designs, für die statische Inhalte bereitgestellt werden sollen. Der Standardwert ist **all**.<br>Beispiel: `--theme Magento/blank --theme Magento/luma` | Nein |
| `--exclude-theme <theme>` | Designs, die bei der Bereitstellung statischer Inhalte ausgeschlossen werden sollen. Der Standardwert ist **none**.<br>Zum Beispiel `--exclude-theme Magento/blank` | Nein |
| `--area (-a)` | Generieren Sie Dateien nur für die angegebenen Bereiche. Standardmäßig werden ohne die angegebene Option Dateien für alle Bereiche generiert. Gültige Werte sind `adminhtml` und `frontend`. Der Standardwert ist **all**.<br>Beispiel: `--area adminhtml` | Nein |
| `--exclude-area` | Keine Dateien für die angegebenen Bereiche erzeugen Wenn keine Option angegeben ist, wird standardmäßig nichts ausgeschlossen. Der Standardwert ist **none**. | Nein |
| `--jobs (-j)` | Aktivieren [Parallelverarbeitung](manage-indexers.md#reindexing-in-parallel-mode) mithilfe der angegebenen Anzahl von Aufträgen. Der Standardwert ist 0 (nicht in parallelen Prozessen ausführen). Der Standardwert ist **0**. | Nein |
| `--symlink-locale` | Erstellen Sie Symlinks für die Dateien dieser Gebietsschemata, die für die Bereitstellung übergeben werden, aber keine Anpassungen aufweisen. | Nein |
| `--content-version=CONTENT-VERSION` | Benutzerdefinierte Versionen statischer Inhalte können verwendet werden, wenn die Bereitstellung auf mehreren Knoten ausgeführt wird, um sicherzustellen, dass die Version statischer Inhalte identisch ist und die Zwischenspeicherung ordnungsgemäß funktioniert. | Nein |
| `--no-javascript` | JavaScript-Dateien nicht bereitstellen | Nein |
| `--no-css` | Stellen Sie keine CSS-Dateien bereit. | Nein |
| `--no-less` | Stellen Sie keine LESS-Dateien bereit. | Nein |
| `--no-images` | Keine Bilder bereitstellen. | Nein |
| `--no-fonts` | Stellen Sie keine Schriftarten bereit. | Nein |
| `--no-html` | Keine HTML-Dateien bereitstellen. | Nein |
| `--no-misc` | Stellen Sie keine anderen Dateitypen bereit: MD, JBF, CSV, JSON, TXT, HTC, SWF | Nein |
| `--no-html-minify` | Minimieren Sie keine HTML-Dateien. | Nein |
| `-s <quick\|standard\|compact>` | Definieren Sie die Bereitstellungsstrategie. Verwenden Sie diese Optionen nur, wenn Sie mehr als eine lokale haben.<ul><li>Verwenden Sie die [Schnellstrategie](static-view-file-strategy.md#quick-strategy) um die Bereitstellungszeit zu minimieren. Dies ist die Standardbefehlsoption, wenn sie nicht angegeben ist.</li><li>Verwenden Sie die [Standardstrategie](static-view-file-strategy.md#standard-strategy) um alle statischen Ansichtsdateien für alle Pakete bereitzustellen.</li><li>Verwenden Sie die [Kompaktstrategie](static-view-file-strategy.md#compact-strategy), um Speicherplatz auf dem Server zu sparen.</li></ul> | Nein |
| `--no-parent` | Keine Dateien für die übergeordneten Designs des aktuellen Designs generieren. Es wird dringend empfohlen, dieses Flag zu verwenden, wenn Sie das übergeordnete Design des aktuellen Designs, das Sie bereitstellen möchten, nicht explizit verwenden. Dies erhöht die Geschwindigkeit des Prozesses erheblich. Dieses Flag ist in Commerce 2.4.2 verfügbar | Nein |
| `--force (-f)` | Dateien in jedem Modus bereitstellen. (Standardmäßig kann das statische Inhaltsbereitstellungs-Tool nur im Produktionsmodus ausgeführt werden. Verwenden Sie diese Option, um sie im Standard- oder Entwicklermodus auszuführen). | Nein |

>[!INFO]
>
>Wenn Sie Werte für `<languages>` und `--language` angeben, hat `<languages>` Vorrang.

## Beispiele

Im Folgenden finden Sie einige Beispielbefehle.

### Ausschließen eines Designs und HTML-Minimierung

Der folgende Befehl stellt statische Inhalte für die US-amerikanische Sprache (`en_US`) bereit, schließt das mit Commerce bereitgestellte Luma-Design aus und minimiert HTML-Dateien nicht.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Beispielausgabe:

```
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

Der folgende Befehl stellt nur JavaScript mit vier Aufträgen mit einer standardmäßigen Bereitstellungsstrategie bereit:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

Der folgende Befehl stellt nur CSS und LESS mit drei Aufträgen und einer schnellen Bereitstellungsstrategie bereit:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Erstellen von statischen Ansichtsdateien für ein Design und einen Bereich

Der folgende Befehl generiert statische Ansichtsdateien für alle Sprachen, nur für den Frontend-Bereich und nur für das Commerce Luma-Design, ohne Schriftarten zu generieren:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Beispielausgabe:

```
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

Möglicherweise möchten Sie den Bereitstellungsprozess in einer separaten, produktionsfremden Umgebung ausführen, um Build-Prozesse auf sensiblen Produktionscomputern zu vermeiden.

Gehen Sie dazu wie folgt vor:

1. Führen Sie [`bin/magento app:config:dump`](../cli/export-configuration.md) aus, um die Konfiguration aus Ihrem Produktionssystem zu exportieren.
1. Kopieren Sie die exportierten Dateien in die Code-Basis außerhalb der Produktion.
1. Statische Ansichtsdateien bereitstellen: `bin/magento setup:static-content:deploy`

## Fehlerbehebung beim Bereitstellungs-Tool für statische Ansichtsdateien

[Installieren Sie zuerst die Commerce](../../installation/overview.md). Andernfalls können Sie das Bereitstellungs-Tool für statische Ansichtsdateien nicht ausführen.

**Problem**: Beim Ausführen des Bereitstellungs-Tools für statische Ansichtsdateien wird der folgende Fehler angezeigt:

```
ERROR: You need to install the Commerce application before running this utility.
```

**Lösung**:

Führen Sie dazu folgende Schritte aus:

1. Installieren Sie die Commerce-Software über [Befehlszeile](../../installation/composer.md).
1. Melden Sie sich beim Anwendungsserver als Eigentümer des Dateisystems an oder [wechseln Sie ](../../installation/prerequisites/file-system/overview.md) zu diesem.
1. Löschen Sie den Inhalt `<app_root>/pub/static` Verzeichnisses mit Ausnahme der `.htaccess`. Diese Datei nicht löschen.
1. Statische Ansichtsdateien bereitstellen: `bin/magento setup:static-content:deploy`

## Tipp für Entwicklerinnen und Entwickler zum Anpassen des statischen Tools zur Inhaltsbereitstellung

Verwenden Sie beim Erstellen einer benutzerdefinierten Implementierung des statischen Tools zur Inhaltsbereitstellung nur das Schreiben atomarer Dateien für Dateien, die auf dem Client verfügbar sein sollten. Wenn Sie nicht-atomares Schreiben von Dateien verwenden, werden diese Dateien möglicherweise mit partiellem Inhalt auf den Client geladen.

Eine der Optionen, um dies atomisch zu gestalten, besteht darin, in Dateien zu schreiben, die in einem temporären Verzeichnis gespeichert sind, und sie nach dem Schreiben in das Zielverzeichnis (von dem aus sie in den Client geladen werden) zu kopieren oder zu verschieben. Einzelheiten zum Schreiben in Dateien finden Sie unter [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
