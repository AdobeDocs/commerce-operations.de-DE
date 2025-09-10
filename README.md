---
source-git-commit: 21a4ec57b49f896cffefbec8db4ce97c161315a0
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 3%

---
# Technische Dokumentation zu Adobe Commerce

Wir freuen uns über Beiträge von der Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentations-Teams.

## Pre-commit-Hooks für die Bildoptimierung

Dieses Repository enthält automatisierte Hooks zur Vorabbestätigung, mit denen Bilder vor dem Commit optimiert werden. **Alle Mitwirkenden sollten diese Erweiterungspunkte aktivieren** um eine konsistente Bildoptimierung und eine reduzierte Repository-Größe sicherzustellen.

### Schnelleinrichtung

Führen Sie nach dem Klonen des Repositorys Folgendes aus:

```bash
.githooks/setup-hooks.sh
```

### Was die Haken tun

- Gestaffelte Bilddateien automatisch erkennen (PNG, JPG, JPEG, GIF, SVG)
- `image_optim` ausführen, um Bilder zu komprimieren und zu optimieren
- Optimierte Bilder automatisch neu inszenieren
- Sicherstellen, dass alle übergebenen Bilder ordnungsgemäß optimiert sind

### Vorteile

- Verringerte Repository-Größe
- Schnelleres Laden von Seiten für die Dokumentation
- Konsistente Bildqualität für alle Mitwirkenden
- Keine manuelle Optimierung erforderlich

Detaillierte Setup-Anweisungen, Fehlerbehebung und Konfiguration finden Sie unter [`.githooks/README.md`](.githooks/README.md).

## Adobe Open Source-Verhaltenskodex

Dieses Projekt beachtet den [Adobe Open Source Code of Conduct](code-of-conduct.md) bzw. den [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie in [diesem Artikel](contributing.md).

## Über Ihre Beiträge zu Adobe-Inhalten

Siehe das [Handbuch für Mitwirkende an Adobe-Dokumenten](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie kleinere Aktualisierungen beitragen möchten, besuchen Sie den Artikel und klicken Sie auf den Feedback-Bereich unten im Artikel, klicken Sie auf **Detaillierte Feedback-Optionen** und dann auf **Bearbeiten vorschlagen**, um zur Markdown-Quelldatei auf GitHub zu gelangen. Verwenden Sie die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Weitere Informationen finden Sie im allgemeinen Leitfaden für Beitragende zu Adobe[Dokumenten .](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)

Kleinere Korrekturen oder Erläuterungen, die Sie zur Dokumentation und zu Code-Beispielen in diesem Repository eingeben, werden von den Adobe-Nutzungsbedingungen abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Teil der Adobe-Community sind und einen neuen Artikel erstellen oder wichtige Änderungen vornehmen möchten, verwenden Sie im Git-Repository die Registerkarte „Probleme“, um ein Problem zu senden und eine Konversation mit dem Dokumentations-Team zu beginnen. Sobald Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diese neuen Inhalte durch eine Kombination von Arbeiten in den öffentlichen und privaten Repositorys einzubringen.

### Wesentliche Veränderungen durch Adobe Mitarbeiter

Wenn Sie technischer Redakteur/technische Redakteurin, Programmmanager oder Entwickler(in) des Produktteams für eine Adobe Experience Cloud-Lösung sind und es Ihre Aufgabe ist, technische Artikel zu erstellen oder zu diesen beizutragen, sollten Sie das private Repository unter `https://git.corp.adobe.com/AdobeDocs` verwenden.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Tools und Einrichtung

Community-Mitwirkende können für eine einfache Bearbeitung die GitHub-Benutzeroberfläche oder für wichtige Beiträge das Repository nutzen.

Weitere Informationen finden Sie im Adobe-Handbuch für Mitwirkende [ Dokumenten .](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)

## Verwenden von Markdown zum Formatieren des Themas

Alle Artikel in diesem Repository verwenden GitHub-Markdown. Wenn Sie mit Markdown nicht vertraut sind, lesen Sie:

- [Markdown-Grundlagen](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [Druckbare Markdown-Anleitung](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Vorlagen

Bei einigen Themen verwenden wir Datendateien und Vorlagen, um veröffentlichte Inhalte zu generieren. Anwendungsfälle für diesen Ansatz sind:

- Veröffentlichen großer Mengen programmgesteuert generierter Inhalte
- Bereitstellung einer zentralen Datenquelle für Kunden über mehrere Systeme hinweg, die maschinenlesbare Dateiformate wie YAML für die Integration benötigen (z. B. das Site-Wide Analysis Tool)

Beispiele für vorlagenbasierte Inhalte sind unter anderem:

- [CLI-Tools-Referenz](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [Produktverfügbarkeitstabellen](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [Systemanforderungstabellen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Vorlageninhalt generieren

Im Allgemeinen müssen die meisten Autoren nur eine Release-Version zu den Tabellen Produktverfügbarkeit und Systemanforderungen hinzufügen. Die Pflege aller anderen vorlagenbasierten Inhalte wird entweder automatisiert oder von einem dedizierten Team-Mitglied verwaltet. Diese Anweisungen sind für die meisten Autoren gedacht.

>**HINWEIS:**
>
>- Für das Generieren von Vorlageninhalten muss an der Befehlszeile in einem Terminal gearbeitet werden.
>- Ruby muss installiert sein, damit das Renderskript ausgeführt werden kann. Siehe [_jekyll/.ruby-version] (_jekyll/.ruby-version) für die erforderliche Version.

Nachfolgend finden Sie eine Beschreibung der Dateistruktur für vorlagenbasierte Inhalte:

- `_jekyll` - Enthält vorlagenbasierte Themen und erforderliche Assets
- `_jekyll/_data` - Enthält die maschinenlesbaren Dateiformate, die zum Rendern von Vorlagen verwendet werden
- `_jekyll/templated` - Enthält HTML-basierte Vorlagendateien, die die Liquid Templating-Sprache verwenden
- `help/_includes/templated` - Enthält die generierte Ausgabe für Vorlageninhalte `.md` Dateiformat, damit sie in Experience League-Themen veröffentlicht werden können. Das Renderskript schreibt die generierte Ausgabe automatisch in dieses Verzeichnis für Sie

So aktualisieren Sie Vorlageninhalte:

1. Öffnen Sie in Ihrem Texteditor eine Datendatei im `/jekyll/_data`. Beispiel:

   - [Produktverfügbarkeitstabellen](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   - [Systemanforderungstabellen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Verwenden Sie die vorhandene YAML-Struktur, um Einträge zu erstellen.

   Um beispielsweise eine Version von Adobe Commerce zu den Produktverfügbarkeitstabellen hinzuzufügen, fügen Sie jedem Eintrag in den Abschnitten `extensions` und `services` der `/jekyll/_data/product-availability.yml` Folgendes hinzu (ändern Sie die Versionsnummern nach Bedarf):

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navigieren Sie zum `_jekyll`.

   ```bash
   cd _jekyll
   ```

1. Generieren von Vorlageninhalten und Schreiben der Ausgabe in das `help/_includes/templated`.

   ```bash
   bundle exec rake render
   ```

   >**HINWEIS** Sie müssen das Skript im `_jekyll` ausführen. Wenn Sie das Skript zum ersten Mal ausführen, müssen Sie zuerst Ruby-Abhängigkeiten mit dem `bundle install` Befehl installieren. Die RAKE-Aufgaben werden vom `adobe-comdox-exl-rake-tasks` gem bereitgestellt, um die Wartung in allen Dokumentations-Repositorys von Adobe Commerce zu verbessern.

1. Navigieren Sie zurück zum `root`.

   ```bash
   cd ..
   ```

1. Stellen Sie sicher, dass die erwarteten `help/_includes/templated` geändert wurden.

   ```bash
   git status
   ```

   Es sollte eine Ausgabe ähnlich der folgenden angezeigt werden:

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Übertragen Sie Ihre Änderungen.

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

In der Jekyll-Dokumentation finden Sie weitere Details zu [Datendateien](https://jekyllrb.com/docs/datafiles), [Flüssigkeitsfiltern](https://jekyllrb.com/docs/liquid/filters/) und anderen Funktionen.

## Verfügbare Rake-Aufgaben

Dieses Repository verwendet RAKE-Aufgaben, die vom `adobe-comdox-exl-rake-tasks`-Gem bereitgestellt werden. Um alle verfügbaren Aufgaben anzuzeigen, führen Sie Folgendes aus:

```bash
cd _jekyll
bundle exec rake --tasks
```
