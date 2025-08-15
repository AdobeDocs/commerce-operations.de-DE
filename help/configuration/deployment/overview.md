---
title: Bereitstellungsübersicht
description: Informationen zu Bereitstellungsstrategien für das Commerce-Programm.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Bereitstellungsübersicht

In diesen Themen wird der Prozess der Bereitstellung der Commerce-Anwendung auf einer Produktions-Site für Adobe Commerce Version 2.2 und höher erläutert. Adobe empfiehlt diese Bereitstellungsmethode für alle Benutzer mit einer großen Site, die keine Ausfallzeiten während der Bereitstellung erleben möchten.

Wenn Sie Commerce auf einem einzelnen Computer bereitstellen und einige Ausfallzeiten während der Bereitstellung tolerieren, finden Sie weitere Informationen unter [Bereitstellung auf einem einzelnen Computer](../deployment/single-machine.md).

## Pipeline-Bereitstellung

Mit Commerce Version 2.2 führte Adobe _Pipeline-Bereitstellung_ als neue Methode zur Bereitstellung von in der Produktionsumgebung bei minimalen Ausfallzeiten ein. Dieser Bereitstellungsprozess erfolgt auf verschiedenen Systemen und bietet die Möglichkeit, konsistente Konfigurationen für alle Pipeline-Bereitstellungssysteme beizubehalten. Es handelt sich dabei um ein einfaches, aber leistungsstarkes Modell, mit dem Sie die üblichen Konfigurationseinstellungen von systemspezifischen Einstellungen (wie Host und Port) oder sensiblen Einstellungen (wie Namen und Kennwörtern) trennen können.

Bei der Verwendung der Pipeline-Bereitstellung geht Adobe davon aus, dass Sie:

- Ein erfahrener Systemintegrator mit hervorragenden Kenntnissen in den Konfigurationsoptionen von Adobe Commerce.
- Verwaltung eines großen Commerce-Standorts (Tausende Lagereinheiten (SKUs)) und Minimierung der Ausfallzeiten des Produktionsstandorts.
- Kenntnisse in der PHP-Programmierung.
- Erfahrung mit Quellcodeverwaltungsmethoden.
- Ihr Code befindet sich in einem Repository der Quell-Code-Verwaltung. In diesem Handbuch gehen wir davon aus, dass Sie ein Git-basiertes Repository verwenden.

### Geringere Ausfallzeiten

Wenn Sie statische Assets bereitstellen und Code auf einem Computer kompilieren, der von Ihrem Produktionssystem getrennt ist, minimieren Sie Ausfallzeiten. Die Ausfallzeit auf dem Produktionssystem ist auf den Zeitraum beschränkt, der für die Übertragung statischer Dateien und kompilierten Codes auf den Server erforderlich ist.

## Bereitstellungssysteme

Wir verwenden die folgenden Begriffe, um die an der Bereitstellung beteiligten Systeme zu beschreiben.

- **Entwicklungssystem**: Computer, auf dem Entwickler Code anpassen und Erweiterungen, Designs und Sprachpakete von Commerce Marketplace installieren. Darüber hinaus nehmen Sie alle Konfigurationsänderungen an Ihrem Entwicklungssystem vor. Es gibt viele Entwicklungssysteme.

- **Build system**: Ein System, auf dem Sie statische Assets bereitstellen und Code für Ihr Produktionssystem kompilieren. Da Sie diese Assets auf einem System erstellen, das sich nicht in der Produktion befindet, wird die Ausfallzeit Ihres Produktionssystems minimiert.

  Auf Ihrem Build-System muss Commerce nicht installiert sein. Es wird nur der Commerce-Code benötigt, es ist jedoch keine Datenbankverbindung erforderlich. Außerdem muss Ihr Build-System kein physisch separater Server sein.

- **Staging-**: _Optional_. Optional können Sie ein Staging-System einrichten, das für das abschließende Testen des gesamten integrierten Codes verwendet wird, einschließlich Benutzerakzeptanztests (UAT). Richten Sie ein Staging-System auf die gleiche Weise ein wie ein Produktionssystem. Mit Ausnahme der Tatsache, dass die Staging-Umgebung nicht Ihr Live-Store ist und keine Bestellungen von Kunden verarbeitet, ist sie identisch mit der Produktion.

- **Produktionssystem** - Ihr Live-Store. Hier sollten Sie minimale direkte Konfigurationsänderungen vornehmen und erst recht nichts, was nicht auf einer Staging-Instanz getestet wurde. Nehmen Sie nach Möglichkeit Konfigurationsänderungen mit [Daten-Patches](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) vor, die auf einer Staging-/Entwicklungsinstanz getestet wurden.

## Andere Bereitstellungsmethoden

Optional können Sie auch andere Bereitstellungsmethoden verwenden, darunter:

- Sicheres Kopieren mit SCP oder rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- Das [Bereitstellungs-Tool](https://deployer.org/)

## Konfiguration verwalten

Bei der Modellierung nach [Faktor 3 im 12-Faktor-App](https://12factor.net/config)Design speichert Commerce jetzt die Konfiguration für jedes System im System selbst. (Entwicklungskonfigurationseinstellungen werden im Entwicklungssystem und Produktionseinstellungen im Produktionssystem gespeichert.)

Wir bieten eine Möglichkeit, die Konfiguration Ihrer Systeme zu synchronisieren:

- **Freigegebene Konfiguration** - Einstellungen, die weder systemspezifisch noch sensibel sind.

  Freigegebene Einstellungen sind Einstellungen, die in Entwicklungs- und Produktionssystemen konsistent sein sollen. Legen Sie die freigegebene Konfiguration im Admin-System in Ihrer Entwicklungsumgebung (oder Adobe Commerce on Cloud Infrastructure _Integration)_.

  Die freigegebene Konfigurationsdatei `app/etc/config.php` sollte in die Quell-Code-Verwaltung aufgenommen werden, damit sie für Entwicklungs-, Build- und Produktionssysteme freigegeben werden kann.

- **Systemspezifische Konfiguration** - Einstellungen, die je nach System variieren, z. B. Hostnamen und Ports von Suchmaschinen.

- **Sensitive Konfiguration** - Einstellungen, die sich _nicht_ der Quell-Code-Verwaltung befinden sollten, da sie personenbezogene Daten (PII) oder Einstellungen wie API-Schlüssel oder Kennwörter bereitstellen.

  Die systemspezifische Konfigurationsdatei `app/etc/env.php` sollte _nicht_ in die Quell-Code-Verwaltung aufgenommen oder anderweitig zwischen Systemen freigegeben werden. Verwenden Sie stattdessen die Befehle [`magento config:set` und `magento:sensitive:set`](../cli/set-configuration-values.md) um Werte für diese Einstellungen in Ihrem Produktionssystem bereitzustellen.

>[!INFO]
>
>Diese neuen Methoden zur Verwaltung Ihrer Konfiguration sind optional. Sie müssen es nicht, aber es wird dringend empfohlen, sie zu verwenden.

Meistens können die Konfigurationsoptionen, die Sie in der freigegebenen, systemspezifischen oder sensiblen Konfiguration festlegen, nicht in der Admin bearbeitet werden. Dadurch werden Ihre Einstellungen auf allen Systemen konsistent gehalten. (Sie können optional den Befehl [`magento config:set` verwenden](../cli/set-configuration-values.md) ohne die Option `--lock`, um Einstellungen zu konfigurieren, die in Admin bearbeitet werden können.)

Jede Commerce-Konfigurationsoption hat einen eindeutigen _Konfigurationspfad_. Um einen Wert für eine Konfigurationsoption festzulegen, können Sie entweder einen CLI-Befehl oder eine Umgebungsvariable verwenden, um den Wert für diesen Konfigurationspfad auf einem bestimmten System festzulegen.
