---
title: Adobe Commerce deinstallieren oder neu installieren
description: Führen Sie diese Schritte aus, um Vor-Ort-Installationen von Adobe Commerce zu deinstallieren und neu zu installieren.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Adobe Commerce deinstallieren oder neu installieren

Bevor Sie diese Befehle verwenden, müssen Sie [die Anwendung installieren](../tutorials/install.md).

## Anwendung aktualisieren

So aktualisieren Sie die Anwendung:

* Wenn Sie die Software aus einem Archiv installiert haben oder &quot;Composer-create-project&quot;verwendet haben, lesen Sie das [Upgrade-Handbuch](../../upgrade/overview.md).
* Wenn Sie ein beitragender Entwickler sind (d. h., Sie haben `git clone` verwendet), lesen Sie den Abschnitt [Anwendung aktualisieren](../../upgrade/developer/git-installs.md).

## Installieren Sie die Anwendung.

Wie Sie die Anwendung über die Befehlszeile neu installieren, hängt von Ihrer Rolle ab:

* Wenn Sie die Software aus einem Archiv installiert haben oder &quot;Composer-create-project&quot;verwendet haben, finden Sie weitere Informationen unter [Aktualisieren der Installationsabhängigkeiten](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Wenn Sie ein beitragender Entwickler sind (d. h., Sie haben mit `git clone` begonnen), finden Sie weitere Informationen unter [Aktualisieren der Installationsabhängigkeiten](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Deinstallieren des Programms

Durch das Deinstallieren des Programms wird die Datenbank gelöscht, die Bereitstellungskonfiguration entfernt und die Ordner unter `var` werden gelöscht.

Geben Sie den folgenden Befehl ein, um das Programm zu deinstallieren:

```bash
bin/magento setup:uninstall
```

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Optional generierte Dateien beibehalten

Standardmäßig löscht `bin/magento setup:upgrade` den kompilierten Code und den Cache. In der Regel verwenden Sie `bin/magento setup:upgrade`, um Komponenten zu aktualisieren, und jede Komponente kann unterschiedliche kompilierte Klassen erfordern.

In einigen Situationen (insbesondere bei der Bereitstellung in der Produktion) möchten Sie jedoch möglicherweise vermeiden, kompilierten Code zu löschen, da dies einige Zeit in Anspruch nehmen kann. (Der Cache wird weiterhin gelöscht.) Geben Sie Folgendes ein, um das Datenbankschema und die Daten *zu aktualisieren, ohne dass* den kompilierten Code bereinigt.

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>Die optionale Option `--keep-generated` sollte unter bestimmten Umständen von erfahrenen Systemintegratoren *nur* verwendet werden. Diese Option sollte *never* in einer Entwicklungsumgebung verwendet werden. Eine fehlerhafte Verwendung dieses optionalen Parameters kann während der Codeausführung zu Fehlern führen.

## Installieren des Programms

* [Installieren mithilfe der Befehlszeile](../advanced.md)
