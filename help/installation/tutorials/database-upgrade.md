---
title: Datenbankschema und Daten aktualisieren
description: Führen Sie diese Schritte aus, um Ihr Adobe Commerce- oder Magento Open Source-Datenbankschema zu aktualisieren.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Datenbankschema und Daten aktualisieren

Bevor Sie diesen Befehl verwenden, müssen Sie [Installieren des Programms](../advanced.md).

## Datenbankschema und Daten aktualisieren

Jedes Mal, wenn Sie eine Aktion ausführen, die eine Änderung des Datenbankschemas oder der Daten bewirkt, müssen Sie diese aktualisieren, indem Sie den in diesem Abschnitt beschriebenen Befehl ausführen. Es folgt eine teilweise Liste der Gründe:

* Sie haben das Programm mithilfe der Befehlszeile aktualisiert.
* Sie haben eine Komponente mithilfe der Befehlszeile installiert oder aktualisiert.
* Sie haben eine Komponente über die Befehlszeile aktiviert oder deaktiviert.

>[!NOTE]
>
>A *component* kann ein Modul, ein Design oder ein Sprachpaket sein; es spielt keine Rolle, ob die Komponente von der Commerce Marketplace stammt oder nicht.

1. Starten Sie das Upgrade:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Wo `--keep-generated` ist ein optionales Argument, das nicht aktualisiert wird [statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md). Dieses optionale Argument ist zur Verwendung vorgesehen. *only* unter begrenzten Umständen von erfahrenen Systemintegratoren. Es sollte verwendet werden *only* in [Produktionsmodus](../../configuration/bootstrap/application-modes.md#production-mode). Es sollte *not* in [Entwicklermodus](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```
