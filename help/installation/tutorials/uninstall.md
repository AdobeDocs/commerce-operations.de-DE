---
title: Adobe Commerce deinstallieren oder neu installieren
description: Führen Sie diese Schritte aus, um lokale Installationen von Adobe Commerce zu deinstallieren und erneut zu installieren.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Adobe Commerce deinstallieren oder neu installieren

Bevor Sie diese Befehle verwenden, müssen Sie [die Anwendung installieren](../tutorials/install.md).

## Aktualisieren der Anwendung

So aktualisieren Sie die Anwendung:

* Falls Sie die Software aus einem Archiv installiert haben oder „composer-create-project“ benutzt haben, lesen Sie bitte das [Upgrade-Handbuch](../../upgrade/overview.md).
* Wenn Sie selbst Entwickler sind (also `git clone` verwendet haben), finden Sie weitere Informationen unter [Aktualisieren der Anwendung](../../upgrade/developer/git-installs.md).

## Neuinstallation der Anwendung

Wie Sie die Anwendung über die Befehlszeile neu installieren, hängt von Ihrer Rolle ab:

* Falls Sie die Software aus einem Archiv installiert haben oder „composer-create-project“ benutzt haben, lesen Sie [Installationsabhängigkeiten aktualisieren](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).
* Wenn Sie selbst Entwickler sind (d. h. bereits mit der Verwendung von `git clone` begonnen haben), finden Sie weitere Informationen unter [Aktualisieren von Installationsabhängigkeiten](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).

## Deinstallieren der Anwendung

Bei der Deinstallation der Anwendung wird die Datenbank gelöscht und wiederhergestellt, die Bereitstellungskonfiguration entfernt und Verzeichnisse unter `var` gelöscht.

Um die Anwendung zu deinstallieren, geben Sie den folgenden Befehl ein:

```bash
bin/magento setup:uninstall
```

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```
[SUCCESS]: Magento uninstallation complete.
```

## Optional generierte Dateien beibehalten

Standardmäßig löscht `bin/magento setup:upgrade` kompilierten Code und den Cache. Normalerweise verwenden Sie `bin/magento setup:upgrade`, um Komponenten zu aktualisieren, und jede Komponente kann unterschiedliche kompilierte Klassen erfordern.

In einigen Situationen (insbesondere bei der Bereitstellung in der Produktion) sollten Sie jedoch den kompilierten Code möglicherweise nicht löschen, da dies einige Zeit in Anspruch nehmen kann. (Der Cache wird weiterhin geleert.) Um das Datenbankschema und die Daten zu aktualisieren *ohne* kompilierten Code zu löschen, geben Sie Folgendes ein:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>Die optionale `--keep-generated`-Option sollte unter bestimmten Umständen von erfahrenen Systemintegratoren (*)* werden. Diese Option sollte *nie* in einer Entwicklungsumgebung verwendet werden. Die unsachgemäße Verwendung dieses optionalen Parameters kann zu Fehlern bei der Code-Ausführung führen.

## Installieren des Programms

* [Installieren über die Befehlszeile](../advanced.md)
