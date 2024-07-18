---
title: Code-Compiler
description: Erfahren Sie, wie Sie den Code-Compiler über die Befehlszeile ausführen.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '161'
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

Sie finden Code-Kompilierungsklassen im Namespace [\Magento\Setup\Module\Di\App\Task\Operation][operation] .

So führen Sie den Einzelmandanten-Compiler aus:

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

So kompilieren Sie den Code vor der Installation der Commerce-Anwendung:

In einigen Fällen möchten Sie möglicherweise Code kompilieren, bevor Sie die Commerce-Anwendung installieren.

1. Aktivieren Sie die Module.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Verwenden Sie die Option &quot;`[-c|--clear-static-content]`&quot;, um statischen Inhalt zu löschen. Dies ist erforderlich, wenn Sie zuvor Module aktiviert oder deaktiviert haben und den zuvor für sie generierten statischen Inhalt löschen müssen.

   Siehe [Module aktivieren](../../installation/tutorials/manage-modules.md).

1. Kompilieren Sie den Code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

Informationen zum Kompilieren von Code ohne Datenbank finden Sie unter [Bereitstellen von statischen Ansichtsdateien ohne Installation von Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
