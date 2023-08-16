---
title: Befehlszeilen-Tool
description: Verwenden Sie das Befehlszeilen-Tool Commerce , um Installations- und Konfigurationsaufgaben auszuführen.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
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

Weitere Vorteile sind:

- Ein einzelner Befehl (`<magento_root>/bin/magento list`) enthält alle verfügbaren Installations- und Konfigurationsbefehle.
- Konsistente Benutzeroberfläche basierend auf Symfony.
- Die CLI ist erweiterbar, sodass Entwickler von Drittanbietern sie &quot;einbinden&quot;können. Dies hat den zusätzlichen Vorteil, dass die Lernkurve der Benutzer entfernt wird.
- Befehle für deaktivierte Module werden nicht angezeigt.

In diesem Thema wird die Konfiguration der Adobe Commerce- und Magento Open Source-Software mithilfe der CLI erläutert. Informationen zur Installation von Commerce finden Sie unter [Installationsfluss](../../installation/overview.md) im _Installationshandbuch_.

## Voraussetzungen

Bevor Sie mit der Verwendung der CLI beginnen, stellen Sie Folgendes sicher:

1. Ihr System erfüllt die in [Systemanforderungen](../../installation/system-requirements.md) im _Installationshandbuch_.
1. Sie alle erforderlichen Aufgaben abgeschlossen haben, die unter [Voraussetzungen](../../installation/prerequisites/overview.md) im _Installationshandbuch_.
1. Nachdem Sie sich beim Commerce-Server angemeldet haben, wechseln Sie zu einem Benutzer, der über Schreibberechtigungen für das Commerce-Dateisystem verfügt. Siehe [Wechseln zum Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) im _Installationshandbuch_.

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
