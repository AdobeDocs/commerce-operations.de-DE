---
title: Upgrade-Kompatibilitätstool installieren
description: Führen Sie diese Schritte aus, um das Upgrade-Kompatibilitätstool für Ihr Adobe Commerce-Projekt zu installieren.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# Upgrade-Kompatibilitätstool installieren

Das Upgrade-Kompatibilitätstool ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste mit Fehlern und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

## Workflow

Das folgende Diagramm zeigt den erwarteten Workflow beim Ausführen des Aktualisierungskompatibilitätstools:

![Diagramm des Upgrade-Kompatibilitätstools](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Für wen ist das Upgrade-Kompatibilitätstool gedacht?

Im folgenden Anwendungsbeispiel wird der typische Prozess für einen Adobe Commerce-Partner zum Aktualisieren der Client-Instanz beschrieben:

1. Der Softwareingenieur eines Partners lädt das Paket des Upgrade-Kompatibilitätstools aus dem [Adobe Commerce-Repository](https://repo.magento.com/) und führt es in der Betaphase der neuesten Adobe Commerce-Version aus. Siehe [Upgrade-Kompatibilitätstool herunterladen](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) für weitere Informationen.
1. Der Softwareingenieur generiert eine Vanilla-Instanz für die spezifische Version von Adobe Commerce, die derzeit installiert ist. Siehe [Mitarbeiter-Handbuch](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) Weitere Informationen zur Verwendung der `instance` -Befehl, um eine Vanilla-Installation zu generieren.
1. Der Softwareingenieur sieht, dass in den Inventar- und Katalogmodulen mehrere benutzerdefinierte Bereiche fehlerhaft sind und auch eine Komplexitätsbewertung von X erhalten. Siehe [Entwickler](../upgrade-compatibility-tool/developer.md) Anleitung für weitere Informationen zum Komplexitätswert.
1. Mit diesen Informationen kann der Softwareingenieur die Komplexität des Upgrades verstehen und diese Informationen an den Kundenbetreuer des Partners weiterleiten.
1. Der Kundenbetreuer erstellt einen Zeitplan und die Kosten für das Adobe Commerce-Upgrade, damit er die Genehmigung seines Managers erhalten kann.
1. Mit der Genehmigung ihres Managers arbeitet der Softwareingenieur an den erforderlichen Code-Änderungen, um die fehlerhaften Module zu beheben.
1. Der Softwareingenieur führt das Upgrade-Kompatibilitätstool erneut mit einer Adobe Commerce-Vorabversion aus, um sicherzustellen, dass keine neuen Probleme auftreten und dass die in der Beta-Phase auftretenden Probleme durch Codeänderungen behoben wurden.
1. Alles wird ausgecheckt und der Softwareingenieur sendet den Code in eine Staging-Umgebung, in der Regressionstests bestätigen, dass alle Tests grün sind. Dadurch können sie die neueste Adobe Commerce-Version am selben Tag, an dem die Adobe Commerce-Vorabversion veröffentlicht wird, in der Produktion freigeben.

   ![Zielgruppe des Aktualisierungskompatibilitätstools](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Eine Vanilla-Instanz ist eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

## Voraussetzungen

Siehe [Voraussetzungen](../upgrade-compatibility-tool/prerequisites.md) für weitere Informationen.

>[!NOTE]
>
>Sie können das Upgrade-Kompatibilitätstool in jedem beliebigen Betriebssystem ausführen. Es ist nicht erforderlich, das Upgrade-Kompatibilitätstool dort auszuführen, wo sich Ihre Adobe Commerce-Instanz befindet. Das Upgrade-Kompatibilitätstool muss Zugriff auf den Quellcode der Adobe Commerce-Instanz haben. Beispielsweise können Sie das Tool auf einem Server installieren und es auf Ihre Adobe Commerce-Installation auf einem anderen Server verweisen.

Wenn Sie das Upgrade-Kompatibilitätstool für eine Adobe Commerce-Instanz mit großen Modulen und Dateien ausführen, erfordert das Tool möglicherweise eine hohe RAM-Menge von mindestens 2 GB RAM.

### Empfohlene Aktionen

Es wird empfohlen, zwei Module mit demselben Namen zu vermeiden. In diesem Fall zeigt das Upgrade-Kompatibilitätstool einen Segmentierungsfehler an.

Um diesen Fehler zu vermeiden, wird empfohlen, die `bin` -Befehl mit der hinzugefügten Option `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>Die `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Die `-m` ermöglicht es dem Upgrade-Kompatibilitätstool, jedes spezifische Modul unabhängig zu analysieren, um zu vermeiden, dass in Ihrer Adobe Commerce-Instanz zwei Module mit demselben Namen auftreten.

Mit dieser Befehlsoption kann das Upgrade-Kompatibilitätstool auch einen Ordner analysieren, der mehrere Module enthält:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Diese Empfehlung hilft auch bei Speicherproblemen, die beim Ausführen des Upgrade-Kompatibilitätstools auftreten können.

## Upgrade-Kompatibilitätstool herunterladen

Führen Sie den folgenden Befehl aus, um das Upgrade-Kompatibilitätstool herunterzuladen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installieren

Um das Upgrade-Kompatibilitätstool zu installieren, müssen Sie die erforderlichen Voraussetzungen installieren:

* Adobe Commerce-Zugriffsschlüssel
* Verfasser
* Node.js

### Adobe Commerce-Zugriffsschlüssel

Sie müssen [Adobe Commerce-Zugriffsschlüssel](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) , um das Upgrade-Kompatibilitätstool herunterzuladen und zu verwenden. Fügen Sie Ihre Adobe Commerce-Zugriffsschlüssel zu Ihren `auth.json` Datei, die sich unter `~/.composer` Standardmäßig.

>[!WARNING]
>
>Überprüfen Sie Ihre **COMPOSER_HOME** Umgebungsvariable, um zu sehen, wo die `auth.json` -Datei befindet.

Die **öffentlicher Schlüssel** entspricht _Benutzername_ in der Erwägung, dass **privater Schlüssel** ist die _password_:

### Beispiel für Adobe Commerce-Zugriffsschlüssel

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Verfasser

Klonen Sie das Repository des Aktualisierungs-Kompatibilitätstools und führen Sie `composer install` in Ihrem Terminal, um Abhängigkeiten zu installieren.

>[!WARNING]
>
>Wenn die Variable **Adobe Commerce-Zugriffsschlüssel** nicht korrekt konfiguriert sind, wird das Upgrade-Kompatibilitätstool nicht installiert und Sie erhalten Fehler, wenn Sie `composer install` Befehl.

### Node.js

Informationen zum Installieren von Node.js finden Sie unter Node.js . [Dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Drittanbietererweiterungen

Adobe empfiehlt, dass Sie sich an Ihren Erweiterungsanbieter wenden, um zu ermitteln, ob Ihre Erweiterung vollständig mit Adobe Commerce 2.4.x kompatibel ist.

Siehe [Tool ausführen](../upgrade-compatibility-tool/run.md) Informationen zum Ausführen des Upgrade-Kompatibilitätstools.
