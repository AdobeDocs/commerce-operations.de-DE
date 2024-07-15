---
title: Datenbankschema und Daten aktualisieren
description: Führen Sie diese Schritte aus, um Ihr Adobe Commerce-Datenbankschema zu aktualisieren.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Datenbankschema und Daten aktualisieren

Bevor Sie diesen Befehl verwenden, müssen Sie [die Anwendung installieren](../advanced.md).

## Datenbankschema und Daten aktualisieren

Jedes Mal, wenn Sie eine Aktion ausführen, die eine Änderung des Datenbankschemas oder der Daten bewirkt, müssen Sie diese aktualisieren, indem Sie den in diesem Abschnitt beschriebenen Befehl ausführen. Es folgt eine teilweise Liste der Gründe:

* Sie haben das Programm mithilfe der Befehlszeile aktualisiert.
* Sie haben eine Komponente mithilfe der Befehlszeile installiert oder aktualisiert.
* Sie haben eine Komponente über die Befehlszeile aktiviert oder deaktiviert.

>[!NOTE]
>
>Eine *Komponente* kann ein Modul, ein Design oder ein Sprachpaket sein. Es spielt keine Rolle, ob die Komponente vom Commerce Marketplace stammt oder nicht.

1. Starten Sie das Upgrade:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Wobei `--keep-generated` ein optionales Argument ist, das [statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md) nicht aktualisiert. Dieses optionale Argument ist für erfahrene Systemintegratoren zur Verwendung von *nur* unter bestimmten Umständen vorgesehen. Sie sollte *nur* im [Produktionsmodus](../../configuration/bootstrap/application-modes.md#production-mode) verwendet werden. Sie sollte *nicht* im [Entwicklermodus](../../configuration/bootstrap/application-modes.md#developer-mode) verwendet werden.

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```
