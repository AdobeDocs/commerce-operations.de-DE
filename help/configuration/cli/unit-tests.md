---
title: Ausführen von Komponententests
description: Ausführen von Komponententests, die in der Adobe Commerce-Codebasis definiert sind.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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

  Verwenden Sie die `--force` nur dann, wenn dies erforderlich ist.

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
