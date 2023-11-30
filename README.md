---
source-git-commit: 580a15c908fc8ac4ef5d62582dfdd87d75dde994
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 3%

---
# Technische Dokumentation zu Adobe Commerce

Wir freuen uns über Beiträge von unserer Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentationsteams.

## Adobe Open Source-Verhaltenskodex

Dieses Projekt beachtet den [Adobe Open Source Code of Conduct](code-of-conduct.md) bzw. den [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie in [diesem Artikel](contributing.md).

## Über Ihre Beiträge zum Adobe von Inhalten

Siehe [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie kleinere Aktualisierungen vornehmen, rufen Sie den Artikel auf und klicken Sie auf den Feedback-Bereich, der unten im Artikel angezeigt wird. Klicken Sie auf **Detaillierte Feedback-Optionen** und klicken Sie anschließend auf **Vorschlagen und Bearbeiten** , um zur Markdown-Quelldatei auf GitHub zu wechseln. Verwenden Sie die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Siehe Allgemein . [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) für weitere Informationen.

Kleinere Korrekturen oder Erläuterungen, die Sie für Dokumentationen und Codebeispiele in diesem Repository einreichen, werden von den Adobe-Nutzungsbedingungen abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Mitglied der Adobe-Community sind und einen neuen Artikel erstellen oder umfangreiche Änderungen einreichen möchten, verwenden Sie die Registerkarte Probleme im Git-Repository, um ein Problem zu melden und eine Konversation mit dem Dokumentationsteam zu beginnen. Sobald Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diesen neuen Inhalt durch eine Kombination aus Arbeit in den öffentlichen und privaten Repositorys einzubringen.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Größere Veränderungen für Adobe-Mitarbeiter

Wenn Sie technischer Redakteur, Programmmanager oder Entwickler des Produktteams für eine Adobe Experience Cloud-Lösung sind und es Ihr Auftrag ist, technische Artikel zu erstellen oder zu diesen beizutragen, sollten Sie das private Repository unter `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Tools und Einrichtung

Community-Mitarbeiter können die GitHub-Benutzeroberfläche für die grundlegende Bearbeitung verwenden oder das Repository abspalten, um wichtige Beiträge zu leisten.

Siehe [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) für Details.

## Verwenden von Markdown zum Formatieren Ihres Themas

Alle Artikel in diesem Repository verwenden GitHub Flavored Markdown. Wenn Sie mit Markdown nicht vertraut sind, lesen Sie:

* [Markdown-Grundlagen](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Druckbares Markdown-Cheatsheet](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Vorlagen

Für einige Themen verwenden wir Datendateien und Vorlagen, um veröffentlichte Inhalte zu generieren. Anwendungsbeispiele für diesen Ansatz:

* Veröffentlichen großer Mengen programmatisch generierter Inhalte
* Bereitstellung einer einzigen &quot;Source of Truth&quot; für Kunden auf mehreren Systemen, die maschinenlesbare Dateiformate wie YAML für die Integration benötigen (z. B. Site-Wide Analysis Tool)

Beispiele für vorlagenbasierte Inhalte sind unter anderem:

* [Referenz zu CLI-Tools](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [Tabellen zur Produktverfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [Systemanforderungen - Tabellen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Vorlageninhalt generieren

Im Allgemeinen müssen die meisten Autoren nur eine Release-Version zu den Tabellen zur Produktverfügbarkeit und zu den Systemanforderungen hinzufügen. Die Wartung aller anderen Vorlageninhalte wird entweder von einem dedizierten Team-Mitglied automatisiert oder verwaltet. Diese Anweisungen sind für &quot;die meisten&quot;Autoren gedacht.

>**NOTE:**
>
>* Das Generieren von Vorlageninhalten erfordert das Arbeiten an der Befehlszeile in einem Terminal.
>* Ruby muss installiert sein, um das Rendering-Skript ausführen zu können. Siehe [_jekyll/.ruby-version](_jekyll/.ruby-version) für die erforderliche Version.

Im Folgenden finden Sie eine Beschreibung der Dateistruktur für Vorlageninhalte:

* `_jekyll`—Enthält vorlagenbasierte Themen und erforderliche Assets
* `_jekyll/_data`—Enthält die maschinenlesbaren Dateiformate zum Rendern von Vorlagen
* `_jekyll/templated`—Enthält HTML-basierte Vorlagendateien, die die Sprache Liquid Template verwenden
* `help/_includes/templated`—Enthält die generierte Ausgabe für den Vorlageninhalt in `.md` Dateiformat, damit es in Experience League-Themen veröffentlicht werden kann; das Rendering-Skript schreibt die generierte Ausgabe automatisch für Sie in dieses Verzeichnis

So aktualisieren Sie Vorlageninhalte:

1. Öffnen Sie in Ihrem Texteditor eine Datendatei im `/jekyll/_data` Verzeichnis. Beispiel:

   * [Tabellen zur Produktverfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [Systemanforderungen - Tabellen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Verwenden Sie die vorhandene YAML-Struktur, um Einträge zu erstellen.

   Um beispielsweise eine Version von Adobe Commerce zu den Produktenverfügbarkeitstabellen hinzuzufügen, fügen Sie jedem Eintrag in der `extensions` und `services` der `/jekyll/_data/product-availability.yml` Datei (ändern Sie die Versionsnummern nach Bedarf):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navigieren Sie zum `_jekyll` Verzeichnis.

   ```
   cd _jekyll
   ```

1. Generieren von Vorlageninhalt und Schreiben der Ausgabe in die `help/_includes/templated` Verzeichnis.

   ```
   rake render
   ```

   >**NOTE:** Sie müssen das Skript über die `_jekyll` Verzeichnis. Wenn Sie das Skript zum ersten Mal ausführen, müssen Sie die Ruby-Abhängigkeiten zuerst mit der `bundle install` Befehl.

1. Überprüfen Sie, ob die erwarteten `help/_includes/templated` -Dateien geändert.

   ```
   git status
   ```

   Sie sollten die Ausgabe ähnlich der folgenden sehen:

   ```
   modified:   _data/product-availability.yml
   modified:   ../help/_includes/templated/product-availability-extensions.md
   ```

Weitere Informationen finden Sie in der Jekyll-Dokumentation . [Datendateien](https://jekyllrb.com/docs/datafiles), [Flüssige Filter](https://jekyllrb.com/docs/liquid/filters/)und anderen Funktionen.
