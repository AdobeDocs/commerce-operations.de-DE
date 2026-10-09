---
title: Datenbankschema und -daten aktualisieren
description: Führen Sie diese Schritte aus, um Ihr Adobe Commerce-Datenbankschema zu aktualisieren.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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

   ```shell
   bin/magento setup:upgrade [--keep-generated]
   ```

   Dabei ist `--keep-generated` ein optionales Argument, das nicht aktualisiert [statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md). Dieses optionale Argument ist nur für *(*) erfahrene Systemintegratoren geeignet. Sie sollte *nur* im [Produktionsmodus) &#x200B;](../../configuration/bootstrap/application-modes.md#production-mode). Sie sollte *nicht* im [Entwicklermodus“ &#x200B;](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Cache leeren:

   ```shell
   bin/magento cache:clean
   ```
