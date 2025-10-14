---
title: Abrufen der Adobe Commerce-Software
description: Erfahren Sie, wie Sie die Adobe Commerce-Software herunterladen.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Abrufen der Adobe Commerce-Software

Sie gehören zu den 240.000 Händlern weltweit, die ihr Vertrauen in unsere eCommerce-Software setzen. Wir haben einige Informationen gesammelt, um Ihnen bei den ersten Schritten mit Ihrer Installation zu helfen.

## So erhalten Sie die Software

Informieren Sie sich über die Verfügbarkeit aufregender neuer Funktionen und Releases und erfahren Sie, wie Sie diese auf unserer [Produktverfügbarkeitsseite“ &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/release/product-availability) können.

In der folgenden Tabelle finden Sie Informationen zu den ersten Schritten bei der Installation von Adobe Commerce.

<table>
    <tbody>
        <tr>
            <th>Benutzeranforderungen</th>
            <th>Beschreibung</th>
            <th>Allgemeine Schritte zur Installation und Aktualisierung</th>
            <th>Link „Erste Schritte“</th>
        </tr>
    <tr>
        <td><p>Integrator, Packager</p></td>
        <td><p>Will die volle Kontrolle über alle installierten Komponenten, hat Zugriff auf den Anwendungsserver, hochtechnisch, könnte Magento Open Source mit anderen Komponenten neu verpacken.</p>
        </td>
        <td><ol><li>Erstellt einen Composer <em>Projekt</em> der die Liste der zu verwendenden Komponenten enthält.</li>
            <li>Verwendet Composer, um Paketabhängigkeiten zu aktualisieren; verwendet <code>composer create-project</code>, um das Composer-Metapaket abzurufen.</li>
            <li>Installiert die Anwendung über die <a href="../advanced.md">Befehlszeile</a>.</li>
        <li>Aktualisiert die Anwendung und die Erweiterungen über <a href="../../upgrade/implementation/perform-upgrade.md">Befehlszeile</a>.</li></ol></td>
        <td><p><a href="../composer.md">Abrufen des Metapakets</a></p></td>
    </tr>
    <tr>
        <td><p>Mitwirkender Entwickler</p></td>
        <td><p>Trägt zur Magento Open Source-Codebasis bei, behebt Fehler und passt die Anwendung an. Hochtechnisch, hat einen eigenen Entwicklungs-Server, versteht Composer und GitHub.</p>
            <p>Sie <em>können</em> die Anwendung nicht in einer Produktionsumgebung verwenden.</p>
      <p>Sie müssen ein Upgrade mit <a href="../../upgrade/developer/git-installs.md">Composer- und Git-Befehlen</a> durchführen.</p></td>
        <td><ol><li>Klonen Sie das GitHub-Repository.</li>
            <li>Verwendet Composer zum Aktualisieren von Paketabhängigkeiten.</li>
            <li>Installiert die Anwendung über <a href="../advanced.md">Befehlszeile</a>.</li>
            <li>Aktualisiert die Anwendung mit <a href="../../upgrade/developer/git-installs.md">Composer- und Git-</a>)</li>
            <li>Passt den Code unter dem <code>app/code</code> an.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Klonen des GitHub-Repositorys</a></p></td>
    </tr>
    </tbody>
</table>

## Nützliche Informationen

Verwenden Sie die Links auf der linken Seite der Seite, um durch die Themen in den einzelnen Teilen der Installation zu navigieren.

## Erforderliche Serverberechtigungen

UNIX-Systeme benötigen `root` Berechtigungen, um Software wie einen Webserver, PHP, zu installieren und zu konfigurieren. Wenn Sie diese Software installieren müssen, stellen Sie sicher, dass Sie `root` Zugriff haben.

Installieren *nicht* die Anwendung im Webserver-Stammverzeichnis als `root` Benutzer, da der Webserver möglicherweise nicht mit diesen Dateien interagieren kann.

Sie benötigen `root` Berechtigungen, um den [Dateisystembesitzer“ &#x200B;](file-system/overview.md) erstellen und diesen Besitzer zur Gruppe des Webservers hinzuzufügen. Sie verwenden den Dateisystembesitzer, um `bin/magento` Befehle über die Befehlszeile auszuführen und Cron-Aufträge einzurichten, die Aufgaben für Sie planen.
