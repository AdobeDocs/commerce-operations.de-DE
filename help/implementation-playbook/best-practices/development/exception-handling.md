---
title: Best Practices für die Ausnahmebehandlung
description: Erfahren Sie mehr über die empfohlenen Methoden zum Protokollieren von Ausnahmen bei der Entwicklung von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Best Practices für die Ausnahmebehandlung

Wenn eine Ausnahme nicht in die `exception.log` geschrieben wird, wobei das Ausnahmemodell als Kontext dient, wird sie in New Relic oder einem anderen PSR-3 Monolog-kompatiblen Protokollspeicher nicht korrekt erkannt und analysiert. Wenn Sie nur einen Teil der Ausnahme protokollieren (oder sie in der falschen Datei protokollieren), führt dies zu Fehlern in der Produktion, wenn Ausnahmen übersehen werden.

## Korrekte Ausnahmebehandlung

Die folgende Checkliste enthält Beispiele zur Veranschaulichung der korrekten Ausnahmebehandlung.

### ![korrekt](../../../assets/yes.svg) Schreiben in das Ausnahmenprotokoll

Schreiben Sie unabhängig von weiteren Aktionen unter Verwendung des folgenden Musters in das Ausnahmenprotokoll, es sei denn, es gibt einen zwingenden Grund, dies nicht zu tun.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Bei diesem Ansatz werden die `$e->getMessage` zur Protokollmeldung und das `$e` gemäß dem [PSR-3-Kontextstandard) automatisch im Kontext &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context). Dies geschieht in `\Magento\Framework\Logger\Monolog::addRecord`.

### ![korrekt](../../../assets/yes.svg) Stummschaltung

Stummschalten von Signalen durch Nichtprotokollieren von Ausnahmen, die Teil des beabsichtigten Betriebsablaufs sind. Wenn eine Ausnahme auftritt, sind keine Folgemaßnahmen erforderlich, sodass sie nicht protokolliert und analysiert werden muss, wenn sie auftritt. Fügen Sie einen Kommentar hinzu, der den Grund für die Stummschaltung der Signale angibt und angibt, dass dies beabsichtigt ist. Kombinieren mit `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![korrekt](../../../assets/yes.svg) Ausnahmen beim Downgrade

Downgrade-Ausnahmen nach dem [PSR-3-](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![korrekt](../../../assets/yes.svg) Die Protokollierung kommt immer zuerst

Als Best Practice wird die Protokollierung immer zuerst im Code angezeigt, um zu verhindern, dass eine weitere Ausnahme oder ein schwerwiegender Fehler ausgelöst wird, bevor in das Protokoll geschrieben wird.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![korrekt](../../../assets/yes.svg) Protokollmeldungen und die gesamte Ausnahmenverfolgung

Protokollmeldungen und die gesamte Ausnahmenablaufverfolgung gemäß dem [PSR-3-](https://www.php-fig.org/psr/psr-3/#13-context).

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

Die Logik vor der Protokollierung kann zu einer weiteren Ausnahme oder einem schwerwiegenden Fehler führen. Dies verhindert, dass die Ausnahme protokolliert wird, und sollte durch [richtiges Beispiel“ &#x200B;](#logging-always-comes-first) werden.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![falsch](../../../assets/no.svg) Leere `catch`

Leere `catch` können ein Zeichen für eine unbeabsichtigte Stummschaltung sein und sollten durch das richtige [&#x200B; ersetzt &#x200B;](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![falsch](../../../assets/no.svg) Doppelte Lokalisierung

Wenn die erfasste lokalisierte Ausnahme noch nicht übersetzt wurde, beheben Sie das Problem an der Stelle, an der die Ausnahme zum ersten Mal ausgelöst wurde.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![inkorrekt](../../../assets/no.svg) Protokollmeldungen und Verfolgung zu verschiedenen Protokolldateien

Der folgende Code protokolliert den Stacktrace für eine Ausnahme fälschlicherweise als Zeichenfolge in einer Protokolldatei.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Dieser Ansatz führt zu Zeilenumbrüchen in der Nachricht, die nicht mit PSR-3 konform sind. Die Ausnahme, einschließlich Stacktrace, muss Teil des Nachrichtenkontexts sein, um sicherzustellen, dass sie korrekt mit der Nachricht in New Relic oder einem anderen PSR-3 Monolog-kompatiblen Protokollspeicher gespeichert wird.

Beheben Sie dieses Problem, indem Sie den Code durch die richtigen Beispiele ersetzen, die unter [Schreiben in das Ausnahmenprotokoll](#write-to-the-exception-log) oder [Downgrade-Ausnahmen](#downgrade-exceptions) zu sehen sind.

### ![falsch](../../../assets/no.svg) Ausnahmen ohne Kontext herunterstufen

Die Ausnahme wird zu einem Fehler heruntergestuft, wodurch nicht die Übergabe eines -Objekts, sondern nur einer Zeichenfolge ermöglicht wird. Daher die `getMessage()`. Dadurch geht die Ablaufverfolgung verloren und sollte durch die richtigen Beispiele ersetzt werden, die unter [Schreiben in das Ausnahmenprotokoll](#write-to-the-exception-log) oder [Downgrade-Ausnahmen](#downgrade-exceptions) zu sehen sind.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![falsch](../../../assets/no.svg) Nur die Nachricht im Ausnahmenprotokoll protokollieren

Anstatt das -Objekt `$e` zu übergeben, wird nur `$e->getMessage()` übergeben. Dadurch geht die Ablaufverfolgung verloren und sollte durch die richtigen Beispiele ersetzt werden, die gezeigt werden [Schreiben in das Ausnahmenprotokoll](#write-to-the-exception-log) oder [Downgrade-Ausnahmen](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![falsch](../../../assets/no.svg) Fehlende `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Das Auslassen der `phpcs:ignore`-Trigger ist ein Warnhinweis in PHPCS und sollte nicht Ihren CI übergeben. Dies sollte durch das richtige Beispiel ersetzt werden, das unter [Stummschaltungssignale“ &#x200B;](#mute-signals) ist.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
