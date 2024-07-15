---
source-git-commit: 0709cd6510adce0f513894fdecb2de5ac88d0e87
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Technische Dokumentation zu Adobe Commerce

Wir freuen uns über Beiträge aus der Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentationsteams.

## Adobe Öffnen des Source-Verhaltenskodex

Dieses Projekt beachtet den [Adobe Open Source Code of Conduct](code-of-conduct.md) bzw. den [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie in [diesem Artikel](contributing.md).

## Über Ihre Beiträge zum Adobe von Inhalten

Siehe [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie kleinere Aktualisierungen vornehmen, rufen Sie den Artikel auf und klicken Sie auf den Feedback-Bereich, der unten im Artikel angezeigt wird. Klicken Sie auf **Detaillierte Feedback-Optionen** und klicken Sie dann auf **Bearbeiten vorschlagen** , um zur Markdown-Quelldatei auf GitHub zu wechseln. Verwenden Sie die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Weitere Informationen finden Sie im allgemeinen Leitfaden [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) .

Kleinere Korrekturen oder Erläuterungen, die Sie für Dokumentationen und Codebeispiele in diesem Repository einreichen, werden von den Adobe-Nutzungsbedingungen abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Mitglied der Adobe-Community sind und einen neuen Artikel erstellen oder umfangreiche Änderungen einreichen möchten, verwenden Sie die Registerkarte Probleme im Git-Repository, um ein Problem zu melden und eine Konversation mit dem Dokumentationsteam zu beginnen. Sobald Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diesen neuen Inhalt durch eine Kombination aus Arbeit in den öffentlichen und privaten Repositorys einzubringen.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Größere Veränderungen für Adobe-Mitarbeiter

Wenn Sie technischer Redakteur, Programmmanager oder Entwickler des Produktteams für eine Adobe Experience Cloud-Lösung sind und es Ihr Auftrag ist, technische Artikel zu erstellen oder zu diesen beizutragen, sollten Sie das private Repository unter `https://git.corp.adobe.com/AdobeDocs` verwenden.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Tools und Einrichtung

Community-Mitarbeiter können die GitHub-Benutzeroberfläche für die grundlegende Bearbeitung verwenden oder das Repository abspalten, um wichtige Beiträge zu leisten.

Weitere Informationen finden Sie im [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) .

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
* [Tabellen mit Systemanforderungen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Vorlageninhalt generieren

Im Allgemeinen müssen die meisten Autoren nur eine Release-Version zu den Tabellen zur Produktverfügbarkeit und zu den Systemanforderungen hinzufügen. Die Wartung aller anderen Vorlageninhalte wird entweder von einem dedizierten Team-Mitglied automatisiert oder verwaltet. Diese Anweisungen sind für die meisten Autoren gedacht.

>**HINWEIS:**
>
>* Das Generieren von Vorlageninhalten erfordert das Arbeiten an der Befehlszeile in einem Terminal.
>* Ruby muss installiert sein, um das Rendering-Skript ausführen zu können. Die erforderliche Version finden Sie unter [_jekyll/.ruby-version](_jekyll/.ruby-version) .

Im Folgenden finden Sie eine Beschreibung der Dateistruktur für Vorlageninhalte:

* `_jekyll` - Enthält Vorlagenthemen und erforderliche Assets
* `_jekyll/_data` - Enthält die maschinenlesbaren Dateiformate zum Rendern von Vorlagen
* `_jekyll/templated` - Enthält HTML-basierte Vorlagendateien, die die Flüssig-Vorlagensprache verwenden
* `help/_includes/templated` - Enthält die generierte Ausgabe für Vorlageninhalte im Dateiformat `.md` , damit sie in Experience League-Themen veröffentlicht werden kann. Das Rendering-Skript schreibt die generierte Ausgabe automatisch in dieses Verzeichnis für Sie

So aktualisieren Sie Vorlageninhalte:

1. Öffnen Sie in Ihrem Texteditor eine Datendatei im Verzeichnis `/jekyll/_data` . Beispiel:

   * [Tabellen zur Produktverfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [Tabellen mit Systemanforderungen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Verwenden Sie die vorhandene YAML-Struktur, um Einträge zu erstellen.

   Um beispielsweise eine Version von Adobe Commerce zu den Verfügbarkeitstabellen des Produkts hinzuzufügen, fügen Sie jedem Eintrag in den Abschnitten `extensions` und `services` der Datei `/jekyll/_data/product-availability.yml` Folgendes hinzu (ändern Sie die Versionsnummern nach Bedarf):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navigieren Sie zum Verzeichnis &quot;`_jekyll`&quot;.

   ```
   cd _jekyll
   ```

1. Generieren Sie den Vorlageninhalt und schreiben Sie die Ausgabe in das Verzeichnis `help/_includes/templated` .

   ```
   rake render
   ```

   >**HINWEIS:** Sie müssen das Skript aus dem Verzeichnis `_jekyll` ausführen. Wenn Sie das Skript zum ersten Mal ausführen, müssen Sie die Ruby-Abhängigkeiten zuerst mit dem Befehl `bundle install` installieren.

1. Navigieren Sie zurück zum Verzeichnis &quot;`root`&quot;.

   ```
   cd ..
   ```

1. Überprüfen Sie, ob die erwarteten `help/_includes/templated` -Dateien geändert wurden.

   ```
   git status
   ```

   Sie sollten die Ausgabe ähnlich der folgenden sehen:

   ```
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Push deine Änderungen.

   ```
   git add
   git commit -m "_descriptive message of the intended commit_"
   git push
   ```

Weitere Informationen zu [Datendateien](https://jekyllrb.com/docs/datafiles), [Liquid-Filtern](https://jekyllrb.com/docs/liquid/filters/) und anderen Funktionen finden Sie in der Jekyll-Dokumentation .
