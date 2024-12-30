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

Die Code-Kompilierung umfasst Folgendes (in keiner bestimmten Reihenfolge):

- Anwendungscodegenerierung (Factories, Proxys)
- Aggregation der Bereichskonfiguration (optimierte Injektion-Abhängigkeitskonfigurationen pro Bereich)
- Interceptor-Erzeugung (optimierte Code-Erzeugung von Interceptoren)
- Zwischenspeicher-Generierung
- Erzeugung von Repository-Code (für APIs generierter Code)
- Generieren von Service-Datenattributen (generierte Erweiterungsklassen für Datenobjekte)

Codekompilierungsklassen finden Sie im Namespace [\Magento\Setup\Module\Di\App\Task\Operation][operation].

So führen Sie den Einzelmandant-Compiler aus:

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

So kompilieren Sie Code vor der Installation der Commerce-Anwendung:

In einigen Fällen empfiehlt es sich, den Code vor der Installation der Commerce-Anwendung zu kompilieren.

1. Aktivieren Sie die Module.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Verwenden Sie die Option `[-c|--clear-static-content]` , um statische Inhalte zu löschen. Dies ist erforderlich, wenn Sie zuvor Module aktiviert oder deaktiviert haben, und Sie müssen den zuvor für sie generierten statischen Inhalt löschen.

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
