---
title: Adobe Commerce-Software herunterladen
description: Erfahren Sie, wie Sie die Adobe Commerce-Software herunterladen.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Adobe Commerce-Software herunterladen

Sie gehören zu den 240.000 Händlern weltweit, die ihr Vertrauen in unsere E-Commerce-Software setzen. Wir haben einige Informationen gesammelt, die Ihnen bei den ersten Schritten mit Ihrer Installation helfen.

## Wie Sie die Software erhalten

Überprüfen Sie die Verfügbarkeit aufregender neuer Funktionen und Versionen und erfahren Sie, wie Sie diese auf unserer [Seite zur Produktverfügbarkeit](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) erhalten können.

In der folgenden Tabelle finden Sie die ersten Schritte zur Installation von Adobe Commerce.

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
        <td><ol><li>Erstellt einen Composer <em>project</em>, der die Liste der zu verwendenden Komponenten enthält.</li>
            <li>Verwendet Composer zum Aktualisieren von Paketabhängigkeiten; verwendet <code>composer create-project</code>, um das Composer-Metapaket zu erhalten.</li>
            <li>Installiert die Anwendung mit der <a href="../advanced.md">Befehlszeile</a>.</li>
        <li>Aktualisieren Sie die Anwendung und die Erweiterungen mithilfe der <a href="../../upgrade/implementation/perform-upgrade.md">Befehlszeile</a>.</li></ol></td>
        <td><p><a href="../composer.md">Metapaket abrufen</a></p></td>
    </tr>
    <tr>
        <td><p>Beitragende Entwickler</p></td>
        <td><p>trägt zur Magento Open Source-Codebase, zu Dateifehlern bei und passt die Anwendung an. Hochtechnisch, hat einen eigenen Entwicklungsserver, versteht Composer und GitHub.</p>
            <p>Sie können die Anwendung <em> nicht in einer Produktionsumgebung verwenden.</em></p>
      <p>Sie müssen ein Upgrade mit <a href="../../upgrade/developer/git-installs.md">Composer- und Git-Befehlen</a> durchführen.</p></td>
        <td><ol><li>Klont das GitHub-Repository.</li>
            <li>Verwendet Composer zum Aktualisieren von Paketabhängigkeiten.</li>
            <li>Installiert die Anwendung mit der <a href="../advanced.md">Befehlszeile</a>.</li>
            <li>Aktualisieren Sie die Anwendung mit <a href="../../upgrade/developer/git-installs.md">Composer- und Git-Befehlen</a>.</li>
            <li>Passt Code im Verzeichnis <code>app/code</code> an.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">GitHub-Repository klonen</a></p></td>
    </tr>
    </tbody>
</table>

## Nützliche Informationen

Über die Links auf der linken Seite der Seite können Sie in den einzelnen Abschnitten der Installation durch Themen navigieren.

## Erforderliche Serverberechtigungen

UNIX-Systeme benötigen `root` Berechtigungen, um Software wie einen Webserver, PHP, zu installieren und zu konfigurieren. Wenn Sie diese Software installieren müssen, stellen Sie sicher, dass Sie über `root` Zugriff verfügen.

Installieren Sie *nicht* die Anwendung im Basisverzeichnis des Webservers als `root` Benutzer, da der Webserver möglicherweise nicht mit diesen Dateien interagieren kann.

Sie benötigen `root` -Berechtigungen, um den [Dateisysteminhaber](file-system/overview.md) zu erstellen und diesen Inhaber zur Gruppe des Webservers hinzuzufügen. Sie verwenden den Dateisysteminhaber, um `bin/magento`-Befehle über die Befehlszeile auszuführen und Cron-Aufträge einzurichten, die Aufgaben für Sie planen.
