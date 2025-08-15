---
title: Adobe Privacy JavaScript Library
description: Erfahren Sie, wie Sie mit benutzerdefinierten Tools auf von Adobe Commerce erfasste personenbezogene Kundendaten zugreifen und diese löschen können.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe Privacy JavaScript Library

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

Die [Adobe Privacy JavaScript Library](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) ist eine Reihe von Tools, die Ihnen bei der Erstellung eines Prozesses für den Zugriff auf und das Löschen privater Daten helfen.

Adobe Commerce-Datenverfolgungsdienste können private Informationen speichern, die für Datenschutzbestimmungen wie die [Datenschutz-Grundverordnung (DSGVO)](gdpr.md) und den California Consumer Privacy Act ([) gelten](ccpa.md).

Diese Bibliothek bietet einen einheitlichen Satz von Funktionen zum Erstellen von Datenschutzanfragen, zum Senden an die Implementierungen der einzelnen Produkte und zum Erfassen der Antworten. Verwenden Sie diese Bibliothek, um die im Browser gespeicherten Daten von diesen Datenverfolgungsdiensten abzurufen und zu entfernen.

## Installation

Verwenden Sie eine der folgenden Methoden, um die Bibliotheksdatei herunterzuladen:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Nachdem Sie die Datei haben, müssen Sie sie einem benutzerdefinierten Modul oder Design hinzufügen, das in Ihrer Adobe Commerce-Instanz installiert ist. Befolgen Sie die Anweisungen unter [Verwenden benutzerdefinierter JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/), um diese Aufgabe durchzuführen.

## Nutzung

Die Adobe Privacy JS Library bietet verschiedene Funktionen zum Verwalten von Identitätsdaten, die im Browser gespeichert sind.

`retrieveIdentities()`
: Gibt ein Array von Identitäten aus einem Service zusammen mit einem Array von Identitäten zurück, die nicht im Service gefunden wurden.

`removeIdentities()`
: Entfernt Identitäten aus dem Browser und gibt ein Array von Identitätsobjekten mit einer `isDeleteClientSide` booleschen Eigenschaft zurück, die angibt, ob die Daten gelöscht wurden.

`retrieveThenRemoveIdentities()`
: Diese Funktion ähnelt `removeIdentities()` insofern, als sie ein Array von Identitäten abruft und aus dem Browser entfernt.

Weitere Informationen und Beispiele zur Verwendung dieser Funktionen finden Sie unter [Offizielle Bibliotheksdokumentation](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html).

### Initialisierung

Instanziieren Sie ein neues `AdobePrivacy`-Objekt, um die Adobe Privacy JS-Bibliothek in Ihrem Implementierungs-Code zu verwenden.

```js
var adobePrivacy = new AdobePrivacy({});
```

Der Konstruktor akzeptiert während der Instanziierung ein Konfigurationsobjekt mit Parametern.
Eine Liste [ Konfigurationsparameter finden Sie in der ](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)offiziellen Bibliotheksdokumentation).
