---
title: Statischer Inhalts-Cache
description: Hier erhalten Sie Informationen zum Signieren statischer Inhalte und zum Aktivieren oder Deaktivieren der Funktion.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: d099d60bcf3c960b2e40b48c386041d8865cfb50
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Statischer Inhalts-Cache

Um die Leistung zu verbessern, legt Commerce die `Expires` -Kopfzeilen für statische Ressourcen wie Bilder, JavaScript- und CSS-Dateien fest.
Durch das Festlegen der Kopfzeile &quot;`Expires`&quot;für eine statische Ressource wird der Browser angewiesen, die Ressource unter dieser URL zwischenzuspeichern und die zwischengespeicherte Version zu verarbeiten, bis sie abläuft.
Dies ist eine gängige [Best Practice](https://developer.yahoo.com/performance/rules.html#expires=) für das Zwischenspeichern statischer Ressourcen.

Wenn der Browser eine statische Ressource zwischenspeichert und diese Ressource auf dem Server geändert wird, müssen Sie den Browser-Cache löschen, damit die neue Version heruntergeladen werden kann.
Das manuelle Löschen des Browser-Cache funktioniert, wenn Sie ein Website-Administrator sind. Dies ist jedoch keine geeignete Anfrage an Ihre Benutzer, wenn Sie möchten, dass sie neue Versionen einer statischen Ressource herunterladen.

## Statische Inhaltssignatur

Die statische Inhaltssignatur ist eine Commerce-Funktion, mit der Sie den Browsercache für statische Ressourcen ungültig machen können.
Commerce erreicht dies durch Hinzufügen einer Bereitstellungsversion zur URL statischer Dateien.

Im Folgenden finden Sie ein Beispiel für eine URL, die mit einer Version signiert wurde:

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Wenn Sie den Befehl [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) zum Bereitstellen von statischem Inhalt ausführen, ändert Commerce automatisch die Bereitstellungsversion.
Dadurch wird die URL der statischen Dateien geändert und der Browser wird gezwungen, die neue Version der Dateien zu laden.

Commerce aktiviert diese Funktion standardmäßig. Adobe empfiehlt, diese Funktion weiterhin zu aktivieren, um Probleme mit Browsern zu vermeiden, die alte statische Ressourcen bereitstellen.

Die Konfiguration für das Signieren statischer Inhalte befindet sich unter [**[!UICONTROL Stores]**> Einstellungen > Konfiguration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

- **Nur On-Premises**: Diese Konfiguration ist verfügbar, wenn Ihre Site im [Produktionsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode) den Wert **nicht** aufweist.
- **Cloud**: Diese Konfiguration ist ausgeblendet, da der Produktionsmodus strikt durchgesetzt wird. Daher müssen Sie die Befehlszeile wie unten dargestellt verwenden.

![Einstellungen für statische Dateien](../../assets/configuration/static-files-settings.png)

Status bestimmen:

```bash
bin/magento config:show dev/static/sign
```

Aktivieren oder deaktivieren Sie die statische Inhaltssignatur:

```bash
bin/magento config:set dev/static/sign <value>
```

Wobei `<value>` 1 (aktiviert) oder 0 (deaktiviert) ist.

## Versionsunterschriften

Commerce hängt die Versionssignatur direkt nach der Basis-URL statischer Ansichtsdateien als Pfadkomponente an, um die Integrität relativer URLs über statische Ressourcen hinweg beizubehalten.
Dies zwingt den Browser auch dazu, eine relative URL zur richtigen signierten Quelle aufzulösen, während sein Inhalt unabhängig vom Vorhandensein/Fehlen des Signaturwerts bleibt.

Wenn ein Browser eine signierte Quelle vom Server anfordert, verwendet der Server URL-Neuschreibungen, um die Signaturkomponente aus der URL zu entfernen.

## Nutzung während Bereitstellungen

Nach der Aktualisierung oder Änderung statischer Ressourcen müssen Sie den Befehl `setup:static-content:deploy` ausführen, um die Version bereitzustellen und die statischen Inhalte zu aktualisieren, wodurch der Browser gezwungen wird, die aktualisierten Ressourcen zu laden.

Wenn Sie Code auf einem separaten Server bereitstellen und ihn mithilfe eines Code-Repositorys in die Produktion verschieben, um Ausfallzeiten zu reduzieren, müssen Sie auch die Datei &quot;`pub/static/deployed_version.txt`&quot;zum Repository hinzufügen.
Diese Datei enthält die neue Version für den bereitgestellten statischen Inhalt.
