---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---
# Technische Dokumentation zu Adobe Commerce

Wir freuen uns über Beiträge von unserer Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentationsteams.

## Adobe Open Source-Verhaltenskodex

Dieses Projekt hat die [Adobe Open Source-Verhaltenskodex](code-of-conduct.md) oder [.NET Foundation-Verhaltenskodex](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie unter [Beitragen](contributing.md) Artikel.

## Informationen zu Ihren Beiträgen zu Adobe-Inhalten

Siehe [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie aus reiner Herzlichkeit kleinere Updates beitragen möchten, besuchen Sie den Artikel und klicken Sie auf die Schaltfläche **Bearbeiten** -Link im Artikel, der zur GitHub-Quelle für den Artikel führt. Verwenden Sie dann einfach die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Siehe Allgemein . [Adobe Docs-Mitarbeiter-Handbuch](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) für weitere Informationen.

Kleinere Korrekturen oder Erläuterungen, die Sie für Dokumentationen und Codebeispiele in diesem Repository einreichen, werden von den Nutzungsbedingungen der Adobe abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Mitglied der Adobe Community sind und einen neuen Artikel erstellen oder umfangreiche Änderungen einreichen möchten, verwenden Sie die Registerkarte Probleme im Git-Repository, um ein Problem zu melden und eine Konversation mit dem Dokumentationsteam zu beginnen. Sobald Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diesen neuen Inhalt durch eine Kombination aus Arbeit in den öffentlichen und privaten Repositorys einzubringen.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Größere Veränderungen für Mitarbeiter der Adobe

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

Die `_jekyll` -Verzeichnis enthält vorlagenbezogene Themen und erforderliche Assets.
Die Vorlagen, die die Vorlagensprache Liquid verwenden, befinden sich im `_jekyll/templated` als HTML-Dateien.
Die `_jekyll/_data` enthält Dateien mit den Daten, die zum Rendern der Vorlagen verwendet werden.

So rendern Sie alle Vorlagen:

1. Navigieren Sie zum `_jekyll` Verzeichnis.

   cd_jekyll

1. Führen Sie das Rendering-Skript aus.

```
_scripts/render
```

> **HINWEIS:** Sie müssen das Skript über die `_jekyll` Verzeichnis.
> **HINWEIS:** Ruby muss installiert sein, um dieses Skript ausführen zu können.

Das Skript führt das Rendern aus und schreibt gerenderte Vorlagen in die `help/_includes/templated` Verzeichnis.

Weitere Informationen finden Sie in der Jekyll-Dokumentation . [Datendateien](https://jekyllrb.com/docs/datafiles), [Flüssige Filter](https://jekyllrb.com/docs/liquid/filters/)und anderen Funktionen.
