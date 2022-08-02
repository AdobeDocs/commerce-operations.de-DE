---
title: Ausführen von Komponententests
description: Ausführen von Komponententests, die in der Adobe Commerce-Codebasis definiert sind.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Ausführen von Komponententests

{{file-system-owner}}

Dieser Befehl führt eine Reihe von Tests aus, die in der Commerce 2-Codebasis definiert sind. Sie können entweder alle ausgewählten Tests oder Tests ausführen. Wenn ein nicht unterstützter Typ angegeben wird, wird das Programm beendet und listet alle verfügbaren Typen auf. Nach der Ausführung wird ein detaillierter Bericht mit dem Testlauf und den Ergebnissen angezeigt.

## Voraussetzungen

Bevor Sie diesen Befehl ausführen, gehen Sie wie folgt vor: _must_ true:

- Die `Magento_Developer` -Modul aktiviert sein. Sie können sie wie folgt aktivieren:

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Verwenden Sie die `--force` nur bei Bedarf.

- Ihr System muss für die gewünschten Tests eingerichtet sein.

Um beispielsweise Integrationstests auszuführen, sollten Sie `dev/tests/integration/etc/install-config-mysql.php.dist` nach `dev/tests/integration/etc/install-config-mysql.php` und ändern Sie sie entsprechend Ihrer Umgebung.

## Ausführen von Tests

Befehlsverwendung:

```bash
bin/magento dev:tests:run <test>
```

So listen Sie die verfügbaren Testtypen auf:

```bash
bin/magento dev:tests:run --help
```

Beispielrückgabe:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

So führen Sie beispielsweise Integrationstests aus:

```bash
bin/magento dev:tests:run integration
```
