---
title: Code-Compiler
description: Erfahren Sie, wie Sie den Code-Compiler über die Befehlszeile ausführen.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Code-Compiler

{{file-system-owner}}

Die Codekompilierung umfasst Folgendes (in keiner bestimmten Reihenfolge):

- Generierung von Anwendungscode (Fabriken, Proxys)
- Aggregation der Bereichskonfiguration (optimierte Konfigurationen für die Abhängigkeitsinjektion pro Bereich)
- Generierung von Interceptoren (optimierte Codegenerierung von Interceptoren)
- Generierung des Abhörcache
- Code-Generierung von Repositorys (generierter Code für APIs)
- Generierung von Dienstdatenattributen (generierte Erweiterungsklassen für Datenobjekte)

Sie finden Code-Kompilierungsklassen in der [\Magento\Setup\Module\Di\App\Task\Operation][operation] Namespace.

So führen Sie den Einzelmandanten-Compiler aus:

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

So kompilieren Sie den Code vor der Installation der Commerce-Anwendung:

In einigen Fällen möchten Sie möglicherweise Code kompilieren, bevor Sie die Commerce-Anwendung installieren.

1. Aktivieren Sie die Module.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Verwenden Sie die `[-c|--clear-static-content]` Option zum Löschen von statischem Inhalt. Dies ist erforderlich, wenn Sie zuvor Module aktiviert oder deaktiviert haben und den zuvor für sie generierten statischen Inhalt löschen müssen.

   Siehe [Module aktivieren](../../installation/tutorials/manage-modules.md).

1. Kompilieren Sie den Code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Informationen zum Kompilieren von Code ohne Datenbank finden Sie unter [Bereitstellen von statischen Ansichtsdateien ohne Installieren von Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
