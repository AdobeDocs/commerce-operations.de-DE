---
title: Ausführen von Komponententests
description: Ausführen von Komponententests, die in der Adobe Commerce-Codebasis definiert sind.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Ausführen von Komponententests

{{file-system-owner}}

Mit diesem Befehl wird eine Reihe von Tests ausgeführt, die in der Codebasis von Commerce 2 definiert sind. Sie können entweder alle ausgewählten Tests oder Tests ausführen. Wenn ein nicht unterstützter Typ angegeben wird, wird das Programm beendet und listet alle verfügbaren Typen auf. Nach der Ausführung wird ein detaillierter Bericht mit dem Testlauf und den Ergebnissen angezeigt.

## Voraussetzungen

Bevor Sie diesen Befehl ausführen, muss der folgende _must_ wahr sein:

- Das Modul `Magento_Developer` muss aktiviert sein. Sie können sie wie folgt aktivieren:

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  Verwenden Sie die Option `--force` nur, wenn dies erforderlich ist.

- Ihr System muss für die gewünschten Tests eingerichtet sein.

Um beispielsweise Integrationstests auszuführen, sollten Sie `dev/tests/integration/etc/install-config-mysql.php.dist` in `dev/tests/integration/etc/install-config-mysql.php` kopieren und an Ihre Umgebung anpassen.

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

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

So führen Sie beispielsweise Integrationstests aus:

```bash
bin/magento dev:tests:run integration
```
