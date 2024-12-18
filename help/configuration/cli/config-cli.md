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

Commerce verfügt über eine Befehlszeilenschnittstelle (CLI) - `<magento_root>/bin/magento` -, über die Installations- und Konfigurationsaufgaben ausgeführt werden, darunter:

- Installieren von Commerce (und damit zusammenhängende Aufgaben wie das Aktualisieren des Datenbankschemas, Erstellen einer Bereitstellungskonfiguration)
- Löschen des Cache
- Verwalten von Indizes, einschließlich Neuindizierung
- Erstellen von Wörterbüchern und Übersetzungspaketen
- Generieren nicht vorhandener Klassen wie Factories und Interceptors für Plug-ins, Generieren der Konfiguration für die Injektion von Abhängigkeiten für den Objekt-Manager
- Bereitstellen von statischen Ansichtsdateien
- Erstellen von CSS aus Less

Weitere Vorteile:

- Ein einzelner Befehl (`<magento_root>/bin/magento list`) listet alle verfügbaren Installations- und Konfigurationsbefehle auf.
- Konsistente Benutzeroberfläche basierend auf Symfony.
- Die CLI ist erweiterbar, sodass sich Drittanbieter-Entwickler damit „verbinden“ können. Dies hat den zusätzlichen Vorteil, dass die Lernkurve der Benutzer eliminiert wird.
- Befehle für deaktivierte Module werden nicht angezeigt.

In diesem Abschnitt wird die Konfiguration der Adobe Commerce-Software mithilfe der CLI beschrieben. Informationen zur Installation von Commerce finden [ unter &quot;](../../installation/overview.md)&quot; im _Installationshandbuch_.

## Voraussetzungen

Bevor Sie mit der Verwendung der CLI beginnen, stellen Sie Folgendes sicher:

1. Ihr System erfüllt die Anforderungen, die unter [Systemanforderungen](../../installation/system-requirements.md) im _Installationshandbuch_ erläutert werden.
1. Sie haben alle erforderlichen Aufgaben abgeschlossen, die unter [Voraussetzungen](../../installation/prerequisites/overview.md) im _Installationshandbuch_ erläutert werden.
1. Wechseln Sie nach der Anmeldung beim Commerce-Server zu einem Benutzer, der über die Berechtigung zum Schreiben in das Commerce-Dateisystem verfügt. Siehe [Wechseln zum Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md) im _Installationshandbuch_.

## Ausführen von Befehlen

Verwenden Sie für die Bash-Shell die folgende Syntax, um zum Dateisystembesitzer zu wechseln und gleichzeitig den Befehl einzugeben:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Wenn der Dateisystembesitzer keine Anmeldungen zulässt, können Sie Folgendes verwenden:

```bash
sudo -u <file system owner> <command>
```

**So führen Sie CLI-Befehle aus einem beliebigen Verzeichnis aus**:

Fügen Sie `<magento_root>/bin` zu Ihrem `PATH` hinzu.

Beispiel-Bash-Shell für CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Optional können Sie Folgendes ausführen:

- `cd <magento_root>/bin` und als `./magento <command name>` ausführen
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` ist ein Unterverzeichnis Ihres Webserver-Stammverzeichnisses
