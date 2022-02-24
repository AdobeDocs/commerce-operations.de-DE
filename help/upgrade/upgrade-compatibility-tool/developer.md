---
title: '"[!DNL Upgrade Compatibility Tool] Entwicklerinformationen"'
description: Anpassen der [!DNL Upgrade Compatibility Tool] Verwendung der API-Indexintegration.
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] Entwicklerinformationen

Dieses Thema enthält Informationen für Entwickler, die eng mit dem Adobe Commerce-Code zusammenarbeiten und detaillierte Informationen über die [!DNL Upgrade Compatibility Tool]. Sie können dieses Wissen verwenden, um die Komponenten des Tools anzupassen.

## Adobe Commerce API-Indexintegration

Die Adobe Commerce API-Indexintegration ist eine interne Integrationslösung, die eine Reihe von Tools zur Erforschung von Adobe Commerce-Erweiterungen umfasst, die von Adobe, Adobe Commerce-Partnern und Drittanbietern basierend auf der statischen Codeanalyse entwickelt wurden.

Die Integration mit dem Adobe Commerce-API-Index erfolgt über:

`sut\Domain\MRay\MRayInterface`

Die Implementierung erfolgt über das `config/services.yaml` -Datei. Der Wert bestimmt, wo die Antwort der Methoden liegt `api()` und `modules()` kommt aus.

Bearbeiten Sie diese Datei, um die Antwort entsprechend Ihrer Installation anzupassen. Ersetzen Sie den zugewiesenen Wert `sut\Domain\MRay\MRayInterface`:

### Beispiel eines benutzerdefinierten Werts

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

Im vorherigen Beispiel wurde die [!DNL Upgrade Compatibility Tool] uses `@sut_mray_mock` als `MRayInterface` Implementierung. Die Antworten der `api()` und `modules()` -Methoden stammen aus den folgenden Dateien:

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>Wenn Sie die `services.yaml` Datei, löschen Sie die `var/cache/` Ordner, um die Änderungen korrekt anzuwenden.

## Unit-Tests

Führen Sie einen der folgenden Befehle aus, um die Komponententests durchzuführen:

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Integrationstests

Führen Sie einen der folgenden Befehle aus, um die Integrationstests auszuführen:

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Abnahmeprüfung

1. Bevor Sie Akzeptanztests durchführen, müssen Sie die Adobe Commerce-URL im `phpunit` Konfigurationsdatei.
1. Den Standard kopieren `tests/acceptance/phpunit.xml` -Datei (ohne das Suffix .dist ).
1. Ändern Sie die `TESTS_BASE_URL` -Wert auf die Adobe Commerce-URL verweisen, die Sie testen möchten.
1. Führen Sie einen der folgenden Befehle aus, um die Akzeptanztests durchzuführen:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL-Komponententests und ESLint-Codeanalyse

### Voraussetzungen

>[!NOTE]
>
>Sie müssen Node.js auf Ihrem System installiert haben, siehe [Node.js-Dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

Die folgenden Anweisungen gelten für MacOS-Systeme:

1. Öffnen Sie ein Terminal und navigieren Sie zum Stammverzeichnis des Projekts.
1. Installieren von Projektabhängigkeiten:

   ```bash
   npm install
   ```

### GraphQL-Komponententests

Die [Jest](https://jestjs.io/docs/getting-started) Framework wurde verwendet, um diese JS-Komponententests zu erstellen:

Die Tests befinden sich in `dev/tests/Js`.

Die zu testenden Zeichenfolgenschemas befinden sich in `dev/tests/Acceptance/_files/graphql_schemas`.

Ausführen von Komponententests oder `jest` wie folgt:

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint-Codeanalyse

[ESLint](https://eslint.org/docs/user-guide/getting-started) ist ein statisches Code-Analyse-Tool zur Identifizierung von problematischen Mustern im JavaScript-Code, mit dem Ziel, den Code konsistenter zu machen und Fehler zu vermeiden.

Ausführen `eslint` Codeanalyse wie folgt:

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Komplexitätswert

Die **Komplexitätswert** ist eine Abbildung, die anzeigt, wie schwierig ein Upgrade von der aktuellen Version auf die neue sein könnte. Niedrigere Zahlen zeigen einfachere Upgrades an.

>[!NOTE]
>
>Die Komplexitätswerte liegen zwischen 0 und û.

Diese Punktzahl basiert auf den Analyseergebnissen:

- Anzahl der festgestellten Probleme
- Schweregrad der festgestellten Probleme

Die [!DNL Upgrade Compatibility Tool] berechnet diesen Wert anhand der unten stehenden Formel für den Komplexitätswert.

### Formel für Komplexitätsbewertung

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Dies sind absolute Werte.
