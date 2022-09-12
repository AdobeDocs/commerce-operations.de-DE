---
title: Code-Compiler
description: Erfahren Sie, wie Sie den Code-Compiler über die Befehlszeile ausführen.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Code-Compiler

{{file-system-owner}}

Die Codekompilierung umfasst Folgendes (in keiner bestimmten Reihenfolge):

- Generierung von Anwendungscode (Fabriken, Proxys)
- Aggregation der Bereichskonfiguration (optimiert) [Abhängigkeitsinjektion](https://glossary.magento.com/dependency-injection) Konfigurationen pro Bereich)
- Generierung von Interceptoren (optimierte Codegenerierung von Interceptoren)
- Generierung des Abhörcache
- Code-Generierung von Repositorys (generierter Code für APIs)
- Generierung von Dienstdatenattributen (generiert) [Erweiterung](https://glossary.magento.com/extension) Klassen für Datenobjekte)

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

   Verwenden Sie die `[-c|--clear-static-content]` Option zum Löschen [statische Inhalte](https://glossary.magento.com/static-content). Dies ist erforderlich, wenn Sie zuvor Module aktiviert oder deaktiviert haben und den zuvor für sie generierten statischen Inhalt löschen müssen.

   Siehe [Module aktivieren](../../installation/tutorials/manage-modules.md).

1. Kompilieren Sie den Code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Informationen zum Kompilieren von Code ohne Datenbank finden Sie unter [Bereitstellen von statischen Ansichtsdateien ohne Installation von Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
