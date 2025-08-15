---
title: Datenbankschema und -daten aktualisieren
description: Führen Sie diese Schritte aus, um Ihr Adobe Commerce-Datenbankschema zu aktualisieren.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Datenbankschema und -daten aktualisieren

Bevor Sie diesen Befehl verwenden, müssen Sie [die Anwendung installieren](../advanced.md).

## Datenbankschema und -daten aktualisieren

Jedes Mal, wenn Sie eine Aktion ausführen, die dazu führt, dass sich das Datenbankschema oder die Daten ändern, müssen Sie sie aktualisieren, indem Sie den in diesem Abschnitt beschriebenen Befehl ausführen. Es folgt eine unvollständige Liste der Gründe:

* Sie haben die Anwendung über die Befehlszeile aktualisiert
* Sie haben eine Komponente über die Befehlszeile installiert oder aktualisiert
* Sie haben eine Komponente über die Befehlszeile aktiviert oder deaktiviert

>[!NOTE]
>
>Eine *Komponente* kann ein Modul, ein Design oder ein Sprachpaket sein. Es spielt keine Rolle, ob die Komponente von Commerce Marketplace stammt oder nicht.

1. Starten Sie das Upgrade:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Dabei ist `--keep-generated` ein optionales Argument, das nicht aktualisiert [statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md). Dieses optionale Argument ist nur für *(*) erfahrene Systemintegratoren geeignet. Sie sollte *nur* im [Produktionsmodus) ](../../configuration/bootstrap/application-modes.md#production-mode). Sie sollte *nicht* im [Entwicklermodus“ ](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```
