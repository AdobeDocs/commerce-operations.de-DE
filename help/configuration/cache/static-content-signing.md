---
title: Statischer Inhalts-Cache
description: Hier erhalten Sie Informationen zum Signieren statischer Inhalte und zum Aktivieren oder Deaktivieren der Funktion.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Statischer Inhalts-Cache

Zur Leistungsverbesserung setzt Commerce die `Expires` Kopfzeilen für statische Ressourcen, z. B. Bilder, JavaScript- und CSS-Dateien.
Festlegen der `Expires` -Kopfzeile einer statischen Ressource weist den Browser an, die Ressource unter dieser URL zwischenzuspeichern und die zwischengespeicherte Version zu verarbeiten, bis sie abläuft.
Dies ist eine häufige [Best Practice](https://developer.yahoo.com/performance/rules.html#expires=) zum Zwischenspeichern statischer Ressourcen.

Wenn der Browser eine statische Ressource zwischenspeichert und diese Ressource auf dem Server geändert wird, müssen Sie den Browser-Cache löschen, damit die neue Version heruntergeladen werden kann.
Das manuelle Löschen des Browser-Cache funktioniert, wenn Sie [website](https://glossary.magento.com/website) Administrator, aber dies ist keine geeignete Anfrage an Ihre Benutzer, wenn Sie möchten, dass sie neue Versionen einer statischen Ressource herunterladen.

## Statische Inhaltssignatur

[Statischer Inhalt](https://glossary.magento.com/static-content) Beim Signieren handelt es sich um eine Commerce-Funktion, mit der Sie den Browsercache für statische Ressourcen ungültig machen können.
Commerce erreicht dies durch Hinzufügen einer Implementierungsversion zur URL von [statische Dateien](https://glossary.magento.com/static-files).

Im Folgenden finden Sie ein Beispiel für eine URL, die mit einer Version signiert wurde:

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Wenn Sie den Befehl ausführen [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) Um statische Inhalte bereitzustellen, ändert Commerce automatisch die Bereitstellungsversion.
Dadurch wird die URL der statischen Dateien geändert und der Browser wird gezwungen, die neue Version der Dateien zu laden.

Commerce ermöglicht diese Funktion standardmäßig. Adobe empfiehlt, diese Funktion weiterhin zu aktivieren, um Probleme mit Browsern zu vermeiden, die alte statische Ressourcen bereitstellen.

Die Konfiguration für diese Funktion finden Sie unter [**[!UICONTROL Stores]**> Einstellungen > Konfiguration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![Einstellungen für statische Dateien](../../assets/configuration/static-files-settings.png)

Status bestimmen:

```bash
bin/magento config:show dev/static/sign
```

Aktivieren oder deaktivieren Sie die statische Inhaltssignatur:

```bash
bin/magento config:set dev/static/sign <value>
```

Wo `<value>` ist 1 (aktiviert) oder 0 (deaktiviert).

## Versionsunterschriften

Commerce hängt die Versionssignatur direkt nach der Basis-URL statischer Ansichtsdateien als Pfadkomponente an, um die Integrität relativer URLs über statische Ressourcen hinweg beizubehalten.
Dies zwingt den Browser auch dazu, eine relative URL zur richtigen signierten Quelle aufzulösen, während sein Inhalt unabhängig vom Vorhandensein/Fehlen des Signaturwerts bleibt.

Wenn ein Browser eine signierte Quelle vom Server anfordert, verwendet der Server URL-Neuschreibungen, um die Signaturkomponente aus der URL zu entfernen.

## Nutzung während Bereitstellungen

Nach dem Aktualisieren oder Ändern von statischen Ressourcen müssen Sie die `setup:static-content:deploy` -Befehl zum Bereitstellen der Version und Aktualisieren der statischen Inhalte, wodurch der Browser gezwungen wird, die aktualisierten Ressourcen zu laden.

Wenn Sie Code auf einem separaten Server bereitstellen und ihn mithilfe eines Code-Repositorys in die Produktion verschieben, um Ausfallzeiten zu reduzieren, müssen Sie auch die Datei hinzufügen `pub/static/deployed_version.txt` zum Repository hinzufügen.
Diese Datei enthält die neue Version für den bereitgestellten statischen Inhalt.
