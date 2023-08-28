---
title: Best Practices bei der Ausnahmebehandlung
description: Erfahren Sie mehr über die empfohlenen Methoden zur Protokollierung von Ausnahmen bei der Entwicklung von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Best Practices bei der Ausnahmebehandlung

Wenn eine Ausnahme nicht in die `exception.log` -Datei mit dem Ausnahmemodell als Kontext, wird sie in New Relic oder anderen monolog-kompatiblen PSR-3-Protokollspeichern nicht korrekt erkannt und analysiert. Die Protokollierung nur eines Teils der Ausnahme (oder die Protokollierung in die falsche Datei) führt zu Produktionsfehlern, wenn Ausnahmen übersehen werden.

## Korrekte Ausnahmebehandlung

Die folgende Checkliste enthält Beispiele für die korrekte Handhabung von Ausnahmen.

### ![korrekt](../../../assets/yes.svg) In das Ausnahmeprotokoll schreiben

Schreiben Sie mit dem folgenden Muster in das Ausnahmeprotokoll, unabhängig von weiteren Aktionen, es sei denn, es gibt einen zwingenden Grund, dies nicht zu tun.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Dieser Ansatz speichert automatisch die `$e->getMessage` zur Protokollmeldung und `$e` -Objekt zum Kontext hinzu, folgen Sie dem [PSR-3-Kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context). Dies geschieht in `\Magento\Framework\Logger\Monolog::addRecord`.

### ![korrekt](../../../assets/yes.svg) Schallzeichen

Stummschaltsignale, indem keine Ausnahmen protokolliert werden, die Teil des beabsichtigten Betriebsablaufs sind. Wenn die Ausnahme auftritt, ist keine Folgeaktion erforderlich, sodass sie nicht protokolliert und analysiert werden muss, wenn sie auftritt. Fügen Sie einen Kommentar hinzu, der angibt, warum Signale stummgeschaltet werden und ob dies beabsichtigt ist. Kombinieren mit `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![korrekt](../../../assets/yes.svg) Herabstufungsausnahmen

Herabstufen von Ausnahmen durch Befolgen der [PSR-3-Kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![korrekt](../../../assets/yes.svg) Die Protokollierung kommt immer zuerst

Als Best Practice wird die Protokollierung immer zuerst im Code durchgeführt, um Fälle zu verhindern, in denen eine andere Ausnahme oder ein schwerwiegender Fehler ausgelöst wird, bevor in das Protokoll geschrieben wird.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![korrekt](../../../assets/yes.svg) Protokollmeldungen und der gesamte Ausnahmeverlauf

Loggen Sie Meldungen und den gesamten Ausnahmeverlauf ein, indem Sie [PSR-3-Kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Falsche Ausnahmebehandlung

Die folgenden Beispiele zeigen eine falsche Ausnahmebehandlung.

### ![falsch](../../../assets/no.svg) Logik vor der Protokollierung

Die Logik vor der Protokollierung kann zu einer weiteren Ausnahme oder einem schwerwiegenden Fehler führen, der verhindert, dass die Ausnahme protokolliert wird, und durch ersetzt werden sollte. [korrekt example](#correct-logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![falsch](../../../assets/no.svg) Empty `catch`

Empty `catch` -Blöcke können ein Zeichen für eine unbeabsichtigte Mutation sein und sollten durch die [korrekt example](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![falsch](../../../assets/no.svg) Doppelte Lokalisierung

Wenn die erfasste lokalisierte Ausnahme noch nicht übersetzt ist, beheben Sie das Problem an der Stelle, an der die Ausnahme zum ersten Mal ausgelöst wird.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![falsch](../../../assets/no.svg) Meldungen protokollieren und Verfolgen zu verschiedenen Protokolldateien

Der folgende Code protokolliert fälschlicherweise den Stacktrace für eine Ausnahme als Zeichenfolge in einer Protokolldatei.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Durch diesen Ansatz werden Zeilenumbrüche in der Nachricht eingeführt, die nicht mit PSR-3 konform sind. Die Ausnahme, einschließlich Stacktrace, muss Teil des Nachrichtenkontexts sein, um sicherzustellen, dass sie mit der Nachricht in New Relic oder einem anderen monolog-kompatiblen PSR-3-Protokollspeicher korrekt gespeichert wird.

Beheben Sie dieses Problem, indem Sie den Code ersetzen, der den korrekten Beispielen folgt, die unter [In das Ausnahmeprotokoll schreiben](#correct-write-to-the-exception-log) oder [Herabstufungsausnahmen](#correct-downgrade-exceptions).

### ![falsch](../../../assets/no.svg) Herabstufen von Ausnahmen ohne Kontext

Die Ausnahme wird auf einen Fehler herabgestuft, bei dem kein Objekt, sondern nur eine Zeichenfolge übergeben werden darf. Daher wird die `getMessage()`. Dadurch geht die Spur verloren und sollte durch die korrekten Beispiele ersetzt werden, die in [In das Ausnahmeprotokoll schreiben](#correct-write-to-the-exception-log) oder [Herabstufungsausnahmen](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![falsch](../../../assets/no.svg) Melden Sie nur die Meldung im Ausnahmeprotokoll an.

Anstelle der Übergabe des Objekts `$e`, nur `$e->getMessage()` übergeben wird. Dadurch geht die Spur verloren und sollte durch die richtigen Beispiele ersetzt werden [In das Ausnahmeprotokoll schreiben](#correct-write-to-the-exception-log) oder [Herabstufungsausnahmen](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![falsch](../../../assets/no.svg) Fehlt `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Auslassen der `phpcs:ignore` las Trigger eine Warnung in PHPCS und sollte Ihr CI nicht übergeben. Dies sollte durch das richtige Beispiel ersetzt werden, das in [Schallzeichen](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
