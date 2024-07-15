---
title: Best Practices bei der Ausnahmebehandlung
description: Erfahren Sie mehr über die empfohlenen Methoden zur Protokollierung von Ausnahmen bei der Entwicklung von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Best Practices bei der Ausnahmebehandlung

Wenn eine Ausnahme nicht in die Datei `exception.log` geschrieben wurde, mit dem Ausnahmemodell als Kontext, wird sie in New Relic oder einem anderen monolog-kompatiblen PSR-3-Protokollspeicher nicht korrekt erkannt und analysiert. Die Protokollierung nur eines Teils der Ausnahme (oder die Protokollierung in die falsche Datei) führt zu Produktionsfehlern, wenn Ausnahmen übersehen werden.

## Korrekte Ausnahmebehandlung

Die folgende Checkliste enthält Beispiele für die korrekte Handhabung von Ausnahmen.

### ![Korrigieren](../../../assets/yes.svg) Schreiben Sie in das Ausnahmeprotokoll

Schreiben Sie mit dem folgenden Muster in das Ausnahmeprotokoll, unabhängig von weiteren Aktionen, es sei denn, es gibt einen zwingenden Grund, dies nicht zu tun.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Bei diesem Ansatz wird der `$e->getMessage` automatisch in der Protokollmeldung und das `$e` -Objekt im Kontext gespeichert, entsprechend dem [PSR-3-Kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context). Dies erfolgt in `\Magento\Framework\Logger\Monolog::addRecord`.

### ![Korrigieren](../../../assets/yes.svg) Stummschaltsignale

Stummschaltsignale, indem keine Ausnahmen protokolliert werden, die Teil des beabsichtigten Betriebsablaufs sind. Wenn die Ausnahme auftritt, ist keine Folgeaktion erforderlich, sodass sie nicht protokolliert und analysiert werden muss, wenn sie auftritt. Fügen Sie einen Kommentar hinzu, der angibt, warum Signale stummgeschaltet werden und ob dies beabsichtigt ist. Kombinieren Sie mit `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![Korrigieren](../../../assets/yes.svg) Herabstufungsausnahmen

Aktualisieren Sie Ausnahmen, indem Sie dem [PSR-3-Kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context) folgen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![Korrigieren](../../../assets/yes.svg) Die Protokollierung kommt immer zuerst

Als Best Practice wird die Protokollierung immer zuerst im Code durchgeführt, um Fälle zu verhindern, in denen eine andere Ausnahme oder ein schwerwiegender Fehler ausgelöst wird, bevor in das Protokoll geschrieben wird.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![Korrigieren](../../../assets/yes.svg) Protokollmeldungen und der gesamte Ausnahmeverlauf

Protokollieren Sie Meldungen und den gesamten Ausnahmeverlauf, indem Sie dem [PSR-3-Kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context) folgen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Falsche Ausnahmebehandlung

Die folgenden Beispiele zeigen eine falsche Ausnahmebehandlung.

### ![falsche](../../../assets/no.svg) Logik vor Protokollierung

Die Logik vor der Protokollierung kann zu einer weiteren Ausnahme oder zu einem schwerwiegenden Fehler führen, der verhindert, dass die Ausnahme protokolliert wird, und durch [korrektes Beispiel](#logging-always-comes-first) ersetzt werden sollte.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![inkorrekt](../../../assets/no.svg) leerer `catch`

Leere `catch` -Blöcke können ein Zeichen für eine unbeabsichtigte Mutation sein und sollten durch das [richtige Beispiel](#mute-signals) ersetzt werden.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![inkorrekt](../../../assets/no.svg) Doppelte Lokalisierung

Wenn die erfasste lokalisierte Ausnahme noch nicht übersetzt ist, beheben Sie das Problem an der Stelle, an der die Ausnahme zum ersten Mal ausgelöst wird.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![inkorrekt](../../../assets/no.svg) Protokollmeldungen und Verfolgung zu verschiedenen Protokolldateien

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

Beheben Sie dieses Problem, indem Sie den Code ersetzen, der den korrekten Beispielen folgt, die in [Schreiben in das Ausnahmeprotokoll](#write-to-the-exception-log) oder [Herabstufen von Ausnahmen](#downgrade-exceptions) dargestellt sind.

### ![inkorrekt](../../../assets/no.svg) Herabstufungsausnahmen ohne Kontext

Die Ausnahme wird auf einen Fehler herabgestuft, bei dem kein Objekt, sondern nur eine Zeichenfolge, also das `getMessage()`, übergeben werden kann. Dadurch geht die Trace verloren und sollte durch die korrekten Beispiele ersetzt werden, die in [Schreiben in das Ausnahmeprotokoll](#write-to-the-exception-log) oder [Downgrade-Ausnahmefehler](#downgrade-exceptions) angezeigt werden.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![inkorrekt](../../../assets/no.svg) Protokollieren Sie nur die Meldung im Ausnahmeprotokoll

Statt das Objekt `$e` zu übergeben, wird nur `$e->getMessage()` übergeben. Dadurch geht die Trace verloren und sollte durch die richtigen Beispiele ersetzt werden, die für [Schreiben in das Ausnahmeprotokoll](#write-to-the-exception-log) oder [Herabstufen von Ausnahmen](#downgrade-exceptions) stehen.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![falsch](../../../assets/no.svg) Fehlt `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Wenn Sie die Zeile `phpcs:ignore` auslassen, wird eine Warnung in PHPCS Trigger und Ihre CI sollte nicht übergeben werden. Dies sollte durch das richtige Beispiel aus [Stummschaltsignale](#mute-signals) ersetzt werden.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
