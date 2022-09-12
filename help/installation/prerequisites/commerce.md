---
title: Herunterladen der Adobe Commerce-Software
description: Erfahren Sie, wie Sie die Adobe Commerce- und Magento Open Source-Software herunterladen.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Herunterladen der Adobe Commerce-Software

Sie gehören zu den 240.000 Händlern weltweit, die ihr Vertrauen in unsere E-Commerce-Software setzen. Wir haben einige Informationen gesammelt, die Ihnen bei den ersten Schritten mit Ihrer Installation helfen.

## Software abrufen

Überprüfen Sie die Verfügbarkeit aufregender neuer Funktionen und Versionen und erfahren Sie, wie Sie sie in unserer [Seite zur Produktverfügbarkeit](https://devdocs.magento.com/release/availability.html).

In der folgenden Tabelle finden Sie Informationen zu den ersten Schritten mit der Installation von Adobe Commerce oder Magento Open Source.

<table>
    <tbody>
        <tr>
            <th>Benutzeranforderungen</th>
            <th>Beschreibung</th>
            <th>Schritte zur Installation und Aktualisierung auf hoher Ebene</th>
            <th>Link "Erste Schritte"</th>
        </tr>
    <tr>
        <td><p>Integrator, Packager</p></td>
        <td><p>Möchte die vollständige Kontrolle über alle installierten Komponenten erhalten, hat Zugriff auf den Anwendungsserver, hochtechnisch, kann die Magento Open Source mit anderen Komponenten umverpacken.</p>
        </td>
        <td><ol><li>Erstellt einen Composer <em>Projekt</em> , die die Liste der zu verwendenden Komponenten enthält.</li>
            <li>Verwendet Composer zum Aktualisieren von Paketabhängigkeiten; uses <code>composer create-project</code> , um das Composer-Metapaket abzurufen.</li>
            <li>Installiert die Anwendung mit dem <a href="../advanced.md">Befehlszeile</a>.</li>
        <li>Aktualisieren Sie die Anwendung und die Erweiterungen mithilfe des  <a href="../../upgrade/implementation/perform-upgrade.md">Befehlszeile</a>.</li></ol></td>
        <td><p><a href="../composer.md">Metapaket abrufen</a></p></td>
    </tr>
    <tr>
        <td><p>Beitragende Entwickler</p></td>
        <td><p>trägt zur Magento Open Source-Codebase, zu Dateifehlern bei und passt die Anwendung an. Hochtechnisch, hat einen eigenen Entwicklungsserver, versteht Composer und GitHub.</p>
            <p>You <em>cannot</em> die Anwendung in einer Produktionsumgebung verwenden.</p>
      <p>Sie müssen ein Upgrade mit <a href="../../upgrade/developer/git-installs.md">Composer- und Git-Befehle</a>.</p></td>
        <td><ol><li>Klont das GitHub-Repository.</li>
            <li>Verwendet Composer zum Aktualisieren von Paketabhängigkeiten.</li>
            <li>Installiert das Programm mit <a href="../advanced.md">Befehlszeile</a>.</li>
            <li>Aktualisieren Sie die Anwendung mit <a href="../../upgrade/developer/git-installs.md">Composer- und Git-Befehle</a>.</li>
            <li>Passt Code unter dem <code>app/code</code> Verzeichnis.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">GitHub-Repository klonen</a></p></td>
    </tr>
    </tbody>
</table>

## Nützliche Informationen

Über die Links auf der linken Seite der Seite können Sie in den einzelnen Abschnitten der Installation durch Themen navigieren.

## Erforderliche Serverberechtigungen

UNIX-Systeme erfordern `root` Berechtigungen zum Installieren und Konfigurieren von Software wie einem Webserver, PHP. Wenn Sie diese Software installieren müssen, stellen Sie sicher, dass Sie `root` Zugriff.

Do *not* Installieren Sie die Anwendung im Basisverzeichnis des Webservers als `root` -Benutzer, da der Webserver möglicherweise nicht mit diesen Dateien interagieren kann.

Sie benötigen `root` Berechtigungen zum Erstellen der [Dateisysteminhaber](file-system/overview.md) und fügen Sie diesen Eigentümer zur Gruppe des Webservers hinzu. Sie verwenden die [Dateisysteminhaber](https://glossary.magento.com/magento-file-system-owner) zum Ausführen `bin/magento` -Befehle über die Befehlszeile und zum Einrichten von Cron-Aufträgen, die Aufgaben für Sie planen.
