---
title: Statische Inhaltssignierung und Browser-Cache-Invalidierung
description: Erfahren Sie, wie das Signieren statischer Inhalte in Adobe Commerce funktioniert, um den Browser-Cache für statische Ressourcen ungültig zu machen. Erfahren Sie, wie Sie diese Funktion aktivieren und konfigurieren.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in der Cloud und lokale Projekte."
autotag-review: '2026-06-22T21:48:08.334Z'
TQID: 'https://experienceleague.adobe.com/vagWBVnjIS7tjnwVE5Dk56VDmPtbPgjsNVLBHSlOc-s'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 372
ht-degree: 0%

---

# Unterschreiben statischer Inhalte und Invalidierung des Browser-Caches

Um die Leistung zu verbessern, legt Commerce die `Expires` für statische Ressourcen wie Bilder, JavaScript und CSS fest.
Wenn Sie den `Expires`-Header für eine statische Ressource festlegen, legt der Browser fest, dass die Ressource unter dieser URL zwischengespeichert und die zwischengespeicherte Version bereitgestellt werden soll, bis sie abläuft.
Dies ist eine gängige [Best Practice](https://developer.yahoo.com/performance/rules.html#expires=) für das Caching statischer Ressourcen.

Wenn der Browser eine statische Ressource zwischenspeichert und sich diese Ressource auf dem Server ändert, müssen Sie den Browsercache löschen, damit er die neue Version herunterladen kann.
Das manuelle Löschen des Browser-Cache funktioniert, wenn Sie ein Website-Administrator sind, aber dies ist keine geeignete Anfrage an Ihre Benutzer, wenn Sie möchten, dass sie neue Versionen einer statischen Ressource herunterladen.

## Signieren von statischen Inhalten

Statische Inhaltssignierung ist eine Commerce-Funktion, mit der Sie den Browsercache für statische Ressourcen ungültig machen können.
Commerce erreicht dies, indem es der URL statischer Dateien eine Bereitstellungsversion hinzufügt.

Im Folgenden finden Sie ein Beispiel für eine URL, die mit einer -Version signiert ist:

```text
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Wenn Sie den [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) zum Bereitstellen statischer Inhalte ausführen, ändert Commerce automatisch die Bereitstellungsversion.
Dadurch wird die URL der statischen Dateien geändert und der Browser gezwungen, die neue Version der Dateien zu laden.

Commerce aktiviert diese Funktion standardmäßig, und Adobe empfiehlt, diese Funktion aktiviert zu lassen, um Probleme im Zusammenhang mit Browsern zu vermeiden, die alte statische Ressourcen bereitstellen.

Die Konfiguration für das Signieren statischer Inhalte finden Sie unter [**[!UICONTROL Stores]**> Einstellungen > Konfiguration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures).

- **Nur On-Premises**: Diese Konfiguration ist verfügbar, wenn sich Ihre Site **nicht** im [Produktionsmodus](../bootstrap/application-modes.md#production-mode).
- **Cloud**: Diese Konfiguration ist ausgeblendet, da der Produktionsmodus streng durchgesetzt wird. Daher müssen Sie die Befehlszeile wie unten dargestellt verwenden.

![Statische Dateieinstellungen](../../assets/configuration/static-files-settings.png)

Bestimmen Sie den Status:

```shell
bin/magento config:show dev/static/sign
```

Aktivieren oder Deaktivieren der statischen Inhaltssignierung:

```shell
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
