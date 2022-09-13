---
title: Module aktivieren oder deaktivieren
description: Führen Sie diese Schritte aus, um Adobe Commerce- oder Magento Open Source-Module zu verwalten.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '557'
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
* `<module-list>` ist eine durch Leerzeichen getrennte Liste von Modulen zur Statusprüfung. Wenn [Modul](https://glossary.magento.com/module) name enthält Sonderzeichen, die den Namen in einfache oder doppelte Anführungszeichen setzen.

## Modul aktivieren, deaktivieren

Verwenden Sie den folgenden Befehl, um verfügbare Module zu aktivieren oder zu deaktivieren:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Wo

* `<module-list>` ist eine durch Leerzeichen getrennte Liste von Modulen, die aktiviert oder deaktiviert werden sollen. Wenn [Modul](https://glossary.magento.com/module) name enthält Sonderzeichen, die den Namen in einfache oder doppelte Anführungszeichen setzen.
* `--all` um alle Module gleichzeitig zu aktivieren oder zu deaktivieren.
* `-f` oder `--force` , um zu erzwingen, dass ein Modul trotz von Abhängigkeiten aktiviert oder deaktiviert wird. Bevor Sie diese Option verwenden, lesen Sie [Informationen zum Aktivieren und Deaktivieren von Modulen](#about-enabling-and-disabling-modules).
* `-c` oder `--clear-static-content` cleans [generierte statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md).

   Wenn statische Ansichtsdateien nicht gelöscht werden, kann dies zu Problemen führen, wenn mehrere Dateien mit demselben Namen vorhanden sind und Sie nicht alle löschen.

   Mit anderen Worten, wegen der [Fallback statischer Dateien](../../configuration/cli/static-view-file-deployment.md) Regeln, wenn Sie statische Dateien nicht löschen und mehr als eine Datei mit dem Namen `logo.svg` die sich unterscheiden, kann die Fallback-Funktion dazu führen, dass die falsche Datei angezeigt wird.

Um beispielsweise die `Magento_Weee` -Modul, geben Sie ein:

```bash
bin/magento module:disable Magento_Weee
```

Wichtige Informationen zum Aktivieren und Deaktivieren von Modulen finden Sie unter [Informationen zum Aktivieren und Deaktivieren von Modulen](#about-enabling-and-disabling-modules).

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

Mit Adobe Commerce und Magento Open Source können Sie die derzeit verfügbaren Module aktivieren oder deaktivieren. mit anderen Worten: alle von Adoben bereitgestellten Module oder Drittanbietermodule, die derzeit verfügbar sind.

Bestimmte Module haben Abhängigkeiten zu anderen Modulen. In diesem Fall können Sie ein Modul möglicherweise nicht aktivieren oder deaktivieren, da es Abhängigkeiten zu anderen Modulen aufweist.

Darüber hinaus kann es *Konflikt* -Module, die nicht beide gleichzeitig aktiviert werden können.

Beispiele:

* Modul A hängt von Modul B ab. Sie können Modul B nur deaktivieren, wenn Sie Modul A zum ersten Mal deaktivieren.

* Modul A ist von Modul B abhängig, die beide deaktiviert sind. Sie müssen Modul B aktivieren, bevor Sie Modul A aktivieren können.

* Modul A steht in Konflikt mit Modul B. Sie können Modul A und Modul B deaktivieren oder eines der beiden Module deaktivieren, Sie jedoch *cannot* Modul A und Modul B gleichzeitig aktivieren.

* Abhängigkeiten werden im `require` -Feld in Adobe Commerce und Magento Open Source `composer.json` -Datei für jedes Modul. Konflikte werden im `conflict` -Feld in Modulen&quot; `composer.json` Dateien. Diese Informationen werden zum Erstellen eines Abhängigkeitsdiagramms verwendet: `A->B` bedeutet, dass Modul A von Modul B abhängig ist.

* A *Abhängigkeitskette* ist der Pfad von einem Modul zu einem anderen. Wenn beispielsweise Modul A von Modul B und Modul B von Modul C abhängig ist, ist die Abhängigkeitskette `A->B->C`.

Wenn Sie versuchen, ein Modul zu aktivieren oder zu deaktivieren, das von anderen Modulen abhängig ist, wird in der Fehlermeldung das Abhängigkeitsdiagramm angezeigt.

>[!NOTE]
>
>Es ist möglich, dass Modul A `composer.json` bezeichnet einen Konflikt mit Modul B, jedoch nicht umgekehrt.

*Nur Befehlszeile:* Um zu erzwingen, dass ein Modul unabhängig von seinen Abhängigkeiten aktiviert oder deaktiviert wird, verwenden Sie die optionale `--force` -Argument.

>[!NOTE]
>
>Verwenden `--force` kann Ihren Store deaktivieren und Probleme beim Zugriff auf den Admin verursachen.