---
title: Ausführen von Modultests
description: Erfahren Sie, wie Sie in der Adobe Commerce-Code-Basis definierte Modultests ausführen. Entdecken Sie Testbefehle, Ausführungsoptionen und Ergebnisberichte.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Ausführen von Modultests

{{file-system-owner}}

Dieser Befehl führt eine Reihe von Tests aus, die in der Code-Basis von Commerce 2 definiert sind. Sie können entweder alle ausgewählten Tests oder Tests ausführen. Sobald ein nicht unterstützter Typ angegeben wird, wird das Programm beendet und alle verfügbaren Typen werden aufgelistet. Nach der Ausführung wird ein detaillierter Bericht mit dem Testlauf und den Ergebnissen angezeigt.

## Voraussetzungen

Bevor Sie diesen Befehl ausführen, muss _folgende_ zutreffen:

- Das `Magento_Developer` muss aktiviert sein. Sie können ihn wie folgt aktivieren:

  ```shell
  bin/magento module:enable [--force] Magento_Developer
  ```

  Verwenden Sie die Option `--force` nur, wenn sie erforderlich ist.

- Ihr System muss für die Ausführung der gewünschten Tests eingerichtet sein.

Um beispielsweise Integrationstests durchzuführen, sollten Sie `dev/tests/integration/etc/install-config-mysql.php.dist` in `dev/tests/integration/etc/install-config-mysql.php` kopieren und an Ihre Umgebung anpassen.

## Ausführen von Tests

Befehlsverwendung:

```shell
bin/magento dev:tests:run <test>
```

Auflisten der verfügbaren Testtypen:

```shell
bin/magento dev:tests:run --help
```

Musterrückgabe:

```text
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

So führen Sie beispielsweise Integrationstests durch:

```shell
bin/magento dev:tests:run integration
```
