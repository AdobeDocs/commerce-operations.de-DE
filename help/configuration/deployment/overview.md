---
title: Implementierungsübersicht
description: Erfahren Sie mehr über Implementierungsstrategien für die Commerce-Anwendung.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Implementierungsübersicht

In diesen Themen wird der Prozess der Bereitstellung der Commerce-Anwendung auf einer Produktions-Site für Adobe Commerce Version 2.2 und höher beschrieben. Adobe empfiehlt diese Bereitstellungsmethode für alle Benutzer mit einer großen Site, die keine Ausfallzeiten während der Bereitstellung erleben möchten.

Wenn Sie Commerce auf einem einzigen Computer bereitstellen und Ausfallzeiten während der Bereitstellung tolerieren können, finden Sie weitere Informationen unter [Bereitstellung auf einem einzelnen Computer](../deployment/single-machine.md).

## Pipeline-Bereitstellung

Mit Commerce-Version 2.2 führte Adobe die _Pipeline-Bereitstellung_ als neue Methode ein, um eine Bereitstellung für die Produktion mit minimalen Ausfallzeiten durchzuführen. Dieser Implementierungsprozess erfolgt auf verschiedenen Systemen und bietet eine Möglichkeit, konsistente Konfigurationen für alle Pipelinebereitstellungssysteme zu erhalten. Es handelt sich dabei um ein einfaches, aber leistungsstarkes Modell, mit dem Sie normale Konfigurationseinstellungen von systemspezifischen Einstellungen (wie Host und Port) oder vertraulichen Einstellungen (wie Namen und Passwörter) trennen können.

Um die Pipeline-Bereitstellung zu verwenden, geht Adobe davon aus, dass Sie:

- Ein erfahrener Systemintegrator mit hervorragenden Kenntnissen der Adobe Commerce-Konfigurationsoptionen.
- Verwalten einer großen Commerce-Site (Tausende von Bestandseinheiten (SKUs)) und Minimieren der Ausfallzeiten von Produktionsstandorten.
- Kenntnisse über PHP-Programmierung.
- Erfahren Sie mehr über die Methoden der Quellcodeverwaltung.
- Ihr Code befindet sich in einem Quellcodeverwaltungs-Repository. In diesem Handbuch gehen wir davon aus, dass Sie ein Git-basiertes Repository verwenden.

### Geringere Ausfallzeiten

Wenn Sie statische Assets bereitstellen und Code auf einem anderen Computer als Ihrem Produktionssystem kompilieren, minimieren Sie Ausfallzeiten. Die Ausfallzeit in Ihrem Produktionssystem ist auf die Zeit beschränkt, die zum Übertragen von statischen Dateien und kompiliertem Code auf den Server erforderlich ist.

## Bereitstellungssysteme

Wir verwenden die folgenden Begriffe, um die Systeme zu beschreiben, die mit der Implementierung verbunden sind.

- **Entwicklungssystem**: Computer, auf dem Entwickler Code anpassen und Erweiterungen, Designs und Sprachpakete von Commerce Marketplace installieren. Darüber hinaus nehmen Sie alle Konfigurationsänderungen auf Ihrem Entwicklungssystem vor. Sie können viele Entwicklungssysteme haben.

- **System erstellen** - Ein System, auf dem Sie statische Assets bereitstellen und Code für Ihr Produktionssystem kompilieren. Da Sie diese Assets auf einem System erstellen, das sich nicht in der Produktion befindet, wird die Ausfallzeit Ihres Produktionssystems minimiert.

  Auf Ihrem Build-System muss Commerce nicht installiert sein. Es ist nur der Commerce-Code erforderlich, es ist jedoch keine Datenbankverbindung erforderlich. Außerdem muss Ihr Build-System kein physisch separater Server sein.

- **Staging-System**—_Optional_. Sie können optional ein Staging-System einrichten, das zum endgültigen Testen des gesamten integrierten Codes einschließlich UAT (User Acceptance Testing) verwendet wird. Richten Sie ein Staging-System auf die gleiche Weise ein wie ein Produktionssystem. Mit Ausnahme der Tatsache, dass Staging nicht Ihr Live Store ist und keine Bestellungen von Kunden verarbeitet, ist es identisch mit der Produktion.

- **Produktionssystem** - Ihr Live Store. Sie sollten hier minimale direkte Konfigurationsänderungen vornehmen und sicherlich nichts, das nicht auf einer Staging-Instanz getestet wurde. Nehmen Sie nach Möglichkeit Konfigurationsänderungen mit [Datenmustern](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) vor, die auf einer Staging-/Entwicklungsinstanz getestet wurden.

## Andere Bereitstellungsmethoden

Optional können Sie auch andere Bereitstellungsmethoden verwenden, darunter:

- Sicheres Kopieren mit SCP oder Rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- Das [Bereitstellungswerkzeug](https://deployer.org/)

## Konfiguration verwalten

Durch die Modellierung nach dem Faktor 3 im 12-Faktor-App-Design](https://12factor.net/config) speichert Commerce jetzt die Konfiguration für jedes System im System selbst. [ (Die Entwicklungs-Konfigurationseinstellungen werden im Entwicklungssystem gespeichert, die Produktionseinstellungen im Produktionssystem.)

Wir bieten eine Möglichkeit, die Konfiguration Ihrer Systeme zu synchronisieren:

- **Freigegebene Konfiguration** - Einstellungen, die weder systemspezifisch noch vertraulich sind.

  Freigegebene Einstellungen sind Einstellungen, die auf Entwicklungs- und Produktionssystemen konsistent sein sollen. Legen Sie die freigegebene Konfiguration im Admin in Ihrem Entwicklungs- (oder Adobe Commerce- in Cloud-Infrastruktur-_Integrations-_)-System fest.

  Die freigegebene Konfigurationsdatei `app/etc/config.php` sollte in die Quell-Code-Verwaltung aufgenommen werden, damit sie von Entwicklungs-, Build- und Produktionssystemen gemeinsam genutzt werden kann.

- **Systemspezifische Konfiguration** - Einstellungen, die je nach System variieren, z. B. Hostnamen und Ports von Suchmaschinen.

- **Vertrauliche Konfiguration** - Einstellungen, die _nicht_ in der Quell-Code-Verwaltung enthalten sollten, da sie personenbezogene Daten (PII) oder Einstellungen wie API-Schlüssel oder Kennwörter verfügbar machen.

  Die systemspezifische Konfigurationsdatei `app/etc/env.php` sollte _nicht_ in der Quell-Code-Verwaltung enthalten oder anderweitig von Systemen gemeinsam genutzt werden. Verwenden Sie stattdessen die Befehle [`magento config:set` und `magento:sensitive:set` ](../cli/set-configuration-values.md) , um Werte für diese Einstellungen in Ihrem Produktionssystem bereitzustellen.

>[!INFO]
>
>Diese neuen Methoden zur Verwaltung Ihrer Konfiguration sind optional. Sie müssen dies nicht tun, es wird jedoch dringend empfohlen, sie zu verwenden.

Meistens können die Konfigurationsoptionen, die Sie in der freigegebenen, systemspezifischen oder sensiblen Konfiguration festlegen, nicht in Admin bearbeitet werden. Auf diese Weise bleiben Ihre Einstellungen in allen Systemen konsistent. (Sie können optional den Befehl [`magento config:set`](../cli/set-configuration-values.md) ohne die Option `--lock` verwenden, um Einstellungen zu konfigurieren, die in der Admin-Konsole bearbeitet werden können.)

Jede Commerce-Konfigurationsoption hat einen eindeutigen _Konfigurationspfad_. Um einen Wert für eine Konfigurationsoption festzulegen, können Sie entweder einen CLI-Befehl oder eine Umgebungsvariable verwenden, um den Wert für diesen Konfigurationspfad auf einem bestimmten System festzulegen.
