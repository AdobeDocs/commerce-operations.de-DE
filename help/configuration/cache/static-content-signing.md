---
title: Cache für statische Inhalte
description: Erfahren Sie mehr über das Signieren im Cache für statische Inhalte und die Leistungsoptimierung in Adobe Commerce. Erfahren Sie, wie Sie Caching-Funktionen aktivieren, deaktivieren und konfigurieren.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Cache für statische Inhalte

Um die Leistung zu verbessern, legt Commerce die `Expires` für statische Ressourcen wie Bilder, JavaScript und CSS fest.
Wenn Sie den `Expires`-Header für eine statische Ressource festlegen, legt der Browser fest, dass die Ressource unter dieser URL zwischengespeichert und die zwischengespeicherte Version bereitgestellt werden soll, bis sie abläuft.
Dies ist eine gängige [Best Practice](https://developer.yahoo.com/performance/rules.html#expires=) für das Caching statischer Ressourcen.

Wenn der Browser eine statische Ressource zwischenspeichert und sich diese Ressource auf dem Server ändert, müssen Sie den Browsercache löschen, damit er die neue Version herunterladen kann.
Das manuelle Löschen des Browser-Cache funktioniert, wenn Sie ein Website-Administrator sind, aber dies ist keine geeignete Anfrage an Ihre Benutzer, wenn Sie möchten, dass sie neue Versionen einer statischen Ressource herunterladen.

## Signieren von statischen Inhalten

Statische Inhaltssignierung ist eine Commerce-Funktion, mit der Sie den Browsercache für statische Ressourcen ungültig machen können.
Commerce erreicht dies, indem es der URL statischer Dateien eine Bereitstellungsversion hinzufügt.

Im Folgenden finden Sie ein Beispiel für eine URL, die mit einer -Version signiert ist:

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Wenn Sie den [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) zum Bereitstellen statischer Inhalte ausführen, ändert Commerce automatisch die Bereitstellungsversion.
Dadurch wird die URL der statischen Dateien geändert und der Browser gezwungen, die neue Version der Dateien zu laden.

Commerce aktiviert diese Funktion standardmäßig, und Adobe empfiehlt, diese Funktion aktiviert zu lassen, um Probleme im Zusammenhang mit Browsern zu vermeiden, die alte statische Ressourcen bereitstellen.

Die Konfiguration für das Signieren statischer Inhalte finden Sie unter [**[!UICONTROL Stores]**> Einstellungen > Konfiguration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures).

- **Nur On-Premises**: Diese Konfiguration ist verfügbar, wenn sich Ihre Site **nicht** im [Produktionsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode).
- **Cloud**: Diese Konfiguration ist ausgeblendet, da der Produktionsmodus streng durchgesetzt wird. Daher müssen Sie die Befehlszeile wie unten dargestellt verwenden.

![Statische Dateieinstellungen](../../assets/configuration/static-files-settings.png)

Bestimmen Sie den Status:

```bash
bin/magento config:show dev/static/sign
```

Aktivieren oder Deaktivieren der statischen Inhaltssignierung:

```bash
bin/magento config:set dev/static/sign <value>
```

Dabei ist `<value>` 1 (aktiviert) oder 0 (deaktiviert).

## Versionssignaturen

Commerce hängt die Versionssignatur direkt nach der Basis-URL von statischen Ansichtsdateien als Pfadkomponente an, um die Integrität von relativen URLs in statischen Ressourcen zu wahren.
Dadurch wird der Browser auch gezwungen, eine relative URL in die richtige signierte Quelle aufzulösen und ihren Inhalt dabei unabhängig vom Vorhandensein/Fehlen des Signaturwerts zu halten.

Wenn ein Browser eine signierte Quelle vom Server anfordert, verwendet der Server URL-Umschreibungen, um die Signaturkomponente aus der URL zu entfernen.

## Verwendung während der Bereitstellung

Nach dem Upgrade oder Ändern von statischen Ressourcen müssen Sie den `setup:static-content:deploy`-Befehl ausführen, um die Version bereitzustellen und die statischen Inhalte zu aktualisieren, wodurch der Browser gezwungen wird, die aktualisierten Ressourcen zu laden.

Wenn Sie Code auf einem separaten Server bereitstellen und mithilfe eines Code-Repositorys in die Produktion verschieben, um Ausfallzeiten zu reduzieren, müssen Sie auch die `pub/static/deployed_version.txt` zum Repository hinzufügen.
Diese Datei enthält die neue Version für den bereitgestellten statischen Inhalt.
