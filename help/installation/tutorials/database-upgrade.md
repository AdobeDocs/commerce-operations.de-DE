---
title: Datenbankschema und Daten aktualisieren
description: Führen Sie diese Schritte aus, um Ihr Adobe Commerce- oder Magento Open Source-Datenbankschema zu aktualisieren.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Datenbankschema und Daten aktualisieren

Bevor Sie diesen Befehl verwenden, müssen Sie [Installieren des Programms](../advanced.md).

## Datenbankschema und Daten aktualisieren

Jedes Mal, wenn Sie eine Aktion ausführen, die die [Datenbankschema](https://glossary.magento.com/database-schema) oder Daten, die geändert werden sollen, müssen Sie sie aktualisieren, indem Sie den in diesem Abschnitt beschriebenen Befehl ausführen. Es folgt eine teilweise Liste der Gründe:

* Sie haben das Programm mithilfe der Befehlszeile aktualisiert.
* Sie haben eine Komponente mithilfe der Befehlszeile installiert oder aktualisiert.
* Sie haben eine Komponente über die Befehlszeile aktiviert oder deaktiviert.

>[!NOTE]
>
>A *component* kann ein Modul, Design oder Sprachpaket sein; Es spielt keine Rolle, ob die Komponente aus dem Commerce Marketplace stammt oder nicht.

1. Starten Sie das Upgrade:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Wo `--keep-generated` ist ein optionales Argument, das nicht aktualisiert wird [statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md). Dieses optionale Argument ist zur Verwendung vorgesehen. *only* unter begrenzten Umständen von erfahrenen Systemintegratoren. Es sollte *only* in [Produktionsmodus](../../configuration/bootstrap/application-modes.md#production-mode). Es sollte *not* in [Entwicklermodus](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```
