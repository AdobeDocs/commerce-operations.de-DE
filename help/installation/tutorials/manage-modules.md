---
title: Module aktivieren oder deaktivieren
description: Führen Sie diese Schritte aus, um Adobe Commerce-Module zu verwalten.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Module aktivieren oder deaktivieren

Für diesen Befehl sind keine Voraussetzungen erforderlich.

## Modulstatus

Verwenden Sie den folgenden Befehl, um aktivierte und aktivierte Module aufzulisten:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Wo

* `--enabled` listet alle aktivierten Module auf.
* `--disabled` listet alle deaktivierten Module auf.
* `<module-list>` ist eine durch Leerzeichen getrennte Liste von Modulen, die den Status überprüfen sollen. Wenn ein Modulname Sonderzeichen enthält, fügen Sie den Namen in einfache oder doppelte Anführungszeichen ein.

>[!NOTE]
>
>Sie können Module nicht direkt in Cloud-Projekten aktivieren oder deaktivieren. Sie müssen diese Befehle lokal ausführen und dann Änderungen an die Datei `app/etc/config.php` für eine Umgebung übertragen. Siehe [Pro Projekt-Workflow: Bereitstellungs-Workflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## Modul aktivieren, deaktivieren

Verwenden Sie den folgenden Befehl, um verfügbare Module zu aktivieren oder zu deaktivieren:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Wo

* `<module-list>` ist eine durch Leerzeichen getrennte Liste von Modulen, die aktiviert oder deaktiviert werden sollen. Wenn ein Modulname Sonderzeichen enthält, fügen Sie den Namen in einfache oder doppelte Anführungszeichen ein.
* `--all` , um alle Module gleichzeitig zu aktivieren oder zu deaktivieren.
* `-f` oder `--force` , um zu erzwingen, dass ein Modul trotz Abhängigkeiten aktiviert oder deaktiviert wird. Bevor Sie diese Option verwenden, lesen Sie [Informationen zum Aktivieren und Deaktivieren von Modulen](#about-enabling-and-disabling-modules).
* `-c` oder `--clear-static-content` löscht [generierte statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md).

  Wenn statische Ansichtsdateien nicht gelöscht werden, kann dies zu Problemen führen, wenn mehrere Dateien mit demselben Namen vorhanden sind und Sie nicht alle löschen.

  Anders ausgedrückt: Wenn Sie statische Dateien nicht löschen und mehr als eine Datei mit dem Namen `logo.svg` unterschiedlich sind, kann aufgrund der Ausweichregeln für statische Dateien ](../../configuration/cli/static-view-file-deployment.md) die falsche Datei angezeigt werden.[

Um beispielsweise das Modul `Magento_Weee` zu deaktivieren, geben Sie Folgendes ein:

```bash
bin/magento module:disable Magento_Weee
```

Wichtige Informationen zum Aktivieren und Deaktivieren von Modulen finden Sie unter [Über das Aktivieren und Deaktivieren von Modulen](#about-enabling-and-disabling-modules).

## Datenbank aktualisieren

Wenn Sie ein oder mehrere Module aktiviert haben, führen Sie den folgenden Befehl aus, um die Datenbank zu aktualisieren:

```bash
bin/magento setup:upgrade
```

Leeren Sie dann den Cache:

```bash
bin/magento cache:clean
```

## Informationen zum Aktivieren und Deaktivieren von Modulen

Mit Adobe Commerce können Sie derzeit verfügbare Module aktivieren oder deaktivieren, d. h. alle Adobe-bereitgestellten Module oder Drittanbietermodule, die derzeit verfügbar sind.

Bestimmte Module haben Abhängigkeiten zu anderen Modulen. In diesem Fall können Sie ein Modul möglicherweise nicht aktivieren oder deaktivieren, da es Abhängigkeiten zu anderen Modulen aufweist.

Darüber hinaus kann es *in Konflikt stehende* Module geben, die nicht beide gleichzeitig aktiviert werden können.

Beispiele:

* Modul A hängt von Modul B ab. Sie können Modul B nur deaktivieren, wenn Sie Modul A zum ersten Mal deaktivieren.

* Modul A ist von Modul B abhängig, die beide deaktiviert sind. Sie müssen Modul B aktivieren, bevor Sie Modul A aktivieren können.

* Modul A steht in Konflikt mit Modul B. Sie können Modul A und Modul B deaktivieren oder eines der beiden Module deaktivieren, aber Sie können Modul A und Modul B *nicht* gleichzeitig aktivieren.

* Abhängigkeiten werden für jedes Modul im Feld `require` in der Adobe Commerce `composer.json` -Datei deklariert. Konflikte werden im Feld `conflict` in den `composer.json` -Dateien der Module deklariert. Wir verwenden diese Informationen zum Erstellen eines Abhängigkeitsdiagramms: `A->B` bedeutet, dass Modul A von Modul B abhängig ist.

* Eine *Abhängigkeitskette* ist der Pfad von einem Modul zu einem anderen. Wenn beispielsweise Modul A von Modul B und Modul B von Modul C abhängig ist, dann ist die Abhängigkeitskette `A->B->C`.

Wenn Sie versuchen, ein Modul zu aktivieren oder zu deaktivieren, das von anderen Modulen abhängig ist, wird in der Fehlermeldung das Abhängigkeitsdiagramm angezeigt.

>[!NOTE]
>
>Es ist möglich, dass die `composer.json` von Modul A einen Konflikt mit Modul B auslöst, aber nicht umgekehrt.

*Nur Befehlszeile:* Verwenden Sie das optionale `--force`-Argument, um zu erzwingen, dass ein Modul unabhängig von seinen Abhängigkeiten aktiviert oder deaktiviert wird.

>[!NOTE]
>
>Die Verwendung von `--force` kann Ihren Store deaktivieren und Probleme beim Zugriff auf den Admin verursachen.
