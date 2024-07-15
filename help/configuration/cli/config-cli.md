---
title: Befehlszeilen-Tool
description: Verwenden Sie das Befehlszeilen-Tool von Commerce, um Installations- und Konfigurationsaufgaben auszuführen.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Befehlszeilen-Tool

Commerce verfügt über eine Befehlszeilenschnittstelle (CLI)—`<magento_root>/bin/magento`, über die Installations- und Konfigurationsaufgaben ausgeführt werden, darunter:

- Installieren von Commerce (und damit zusammenhängende Aufgaben wie das Aktualisieren des Datenbankschemas, Erstellen einer Bereitstellungskonfiguration)
- Löschen des Caches
- Verwalten von Indizes, einschließlich Neuindizierung
- Erstellen von Übersetzungswörterbüchern und Übersetzungspaketen
- Generieren nicht vorhandener Klassen wie Fabriken und Abfänger für Plug-ins, Generieren der Konfiguration für die Injektion von Abhängigkeiten für den Objektmanager
- Bereitstellen von statischen Ansichtsdateien
- Erstellen von CSS aus weniger

Weitere Vorteile sind:

- Ein einzelner Befehl (`<magento_root>/bin/magento list`) listet alle verfügbaren Installations- und Konfigurationsbefehle auf.
- Konsistente Benutzeroberfläche basierend auf Symfony.
- Die CLI ist erweiterbar, sodass Entwickler von Drittanbietern sie &quot;einbinden&quot;können. Dies hat den zusätzlichen Vorteil, dass die Lernkurve der Benutzer entfernt wird.
- Befehle für deaktivierte Module werden nicht angezeigt.

In diesem Thema wird die Konfiguration der Adobe Commerce-Software mithilfe der CLI erläutert. Informationen zum Installieren von Commerce finden Sie unter [Installationsfluss](../../installation/overview.md) im _Installationshandbuch_.

## Voraussetzungen

Bevor Sie mit der Verwendung der CLI beginnen, stellen Sie Folgendes sicher:

1. Ihr System erfüllt die in [Systemanforderungen](../../installation/system-requirements.md) im _Installationshandbuch_ beschriebenen Anforderungen.
1. Sie haben alle erforderlichen Aufgaben abgeschlossen, die in [Voraussetzungen](../../installation/prerequisites/overview.md) im _Installationshandbuch_ beschrieben sind.
1. Nachdem Sie sich beim Commerce-Server angemeldet haben, wechseln Sie zu einem Benutzer, der zum Schreiben in das Commerce-Dateisystem berechtigt ist. Siehe [Wechseln zum Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) im _Installationshandbuch_.

## Ausführen von Befehlen

Verwenden Sie für die Bash-Shell die folgende Syntax, um zum Dateisysteminhaber zu wechseln und den Befehl gleichzeitig einzugeben:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Wenn der Dateisysteminhaber keine Anmeldung zulässt, können Sie Folgendes verwenden:

```bash
sudo -u <file system owner> <command>
```

**Ausführen von CLI-Befehlen aus einem beliebigen Verzeichnis**:

Fügen Sie `<magento_root>/bin` zu Ihrem System `PATH` hinzu.

Beispiel-Bash-Shell für CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Optional können Sie Folgendes ausführen:

- `cd <magento_root>/bin` und führen Sie sie als `./magento <command name>` aus
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` ist ein Unterverzeichnis Ihres Webserver-Basisverzeichnisses.
