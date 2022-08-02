---
title: Befehlszeilen-Tool
description: Verwenden Sie das Befehlszeilen-Tool Commerce , um Installations- und Konfigurationsaufgaben auszuführen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Befehlszeilen-Tool

Commerce verfügt über eine Befehlszeilenschnittstelle (CLI)—`<magento_root>/bin/magento`—die Installations- und Konfigurationsaufgaben ausführt, einschließlich:

- Installation von Commerce (und damit zusammenhängende Aufgaben wie Aktualisierung des Datenbankschemas, Erstellung einer Bereitstellungskonfiguration)
- Löschen des Caches
- Verwalten von Indizes, einschließlich Neuindizierung
- Erstellen von Übersetzungswörterbüchern und Übersetzungspaketen
- Generieren nicht vorhandener Klassen wie Fabriken und Abfänger für Plug-ins, Generieren der Konfiguration für die Injektion von Abhängigkeiten für den Objektmanager
- Bereitstellen von statischen Ansichtsdateien
- Erstellen von CSS aus weniger

Weitere Vorteile:

- Ein einzelner Befehl (`<magento_root>/bin/magento list`) listet alle verfügbaren Installations- und Konfigurationsbefehle auf.
- Konsistente Benutzeroberfläche basierend auf Symfony.
- Die CLI ist erweiterbar, sodass Entwickler von Drittanbietern sie &quot;einbinden&quot;können. Dies hat den zusätzlichen Vorteil, dass die Lernkurve der Benutzer entfernt wird.
- Befehle für deaktivierte Module werden nicht angezeigt.

In diesem Thema wird die Konfiguration der Adobe Commerce- und Magento Open Source-Software mithilfe der CLI erläutert. Informationen zur Installation von Commerce finden Sie unter [Installationsübersicht](https://devdocs.magento.com/guides/2.4/install-gde/bk-install-guide.html) im _Installationshandbuch_.

## Voraussetzungen

Bevor Sie mit der Verwendung der CLI beginnen, stellen Sie Folgendes sicher:

1. Ihr System erfüllt die in [Systemanforderungen](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) im _Installationshandbuch_.
1. Sie alle erforderlichen Aufgaben abgeschlossen haben, die unter [Voraussetzungen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) im _Installationshandbuch_.
1. Nachdem Sie sich beim Commerce-Server angemeldet haben, wechseln Sie zu einem Benutzer, der über Schreibberechtigungen für das Commerce-Dateisystem verfügt. Siehe [Wechseln zum Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) im _Installationshandbuch_.

## Ausführen von Befehlen

Verwenden Sie für die Bash-Shell die folgende Syntax, um zum Dateisysteminhaber zu wechseln und den Befehl gleichzeitig einzugeben:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Wenn der Dateisysteminhaber keine Anmeldung zulässt, können Sie Folgendes verwenden:

```bash
sudo -u <file system owner> <command>
```

**So führen Sie CLI-Befehle aus einem beliebigen Verzeichnis aus**:

Hinzufügen `<magento_root>/bin` auf Ihr System `PATH`.

Beispiel-Bash-Shell für CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Optional können Sie Folgendes ausführen:

- `cd <magento_root>/bin` und führen Sie sie als `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` ist ein Unterverzeichnis Ihres Webserver-Basisverzeichnisses
