---
title: JavaScript-Bibliothek zum Datenschutz in Adoben
description: Erfahren Sie, wie Sie mit benutzerdefinierten Tools auf personenbezogene Daten von Adobe Commerce und Magento Open Source zugreifen und diese löschen können.
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# JavaScript-Bibliothek zum Datenschutz in Adoben

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

Die [JavaScript-Bibliothek zum Datenschutz in Adoben](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) ist eine Reihe von Tools, mit denen Sie einen Prozess für den Zugriff auf und das Löschen von privaten Daten erstellen können.

Adobe Commerce- und Magento Open Source-Datenverfolgungsdienste können personenbezogene Daten speichern, die auf Datenschutzbestimmungen wie die [Die Datenschutz-Grundverordnung (DSGVO)](gdpr.md) und [California Consumer Privacy Act (CCPA)](ccpa.md).

Diese Bibliothek bietet eine einheitliche Reihe von Funktionen zum Erstellen von Datenschutzanfragen, Senden dieser Anfragen an die Implementierungen der einzelnen Produkte und Erfassen der Antworten. Verwenden Sie diese Bibliothek, um die Daten abzurufen und zu entfernen, die von diesen Daten-Tracking-Diensten im Browser gespeichert werden.

## Installation

Verwenden Sie eine der folgenden Methoden, um die Bibliotheksdatei herunterzuladen:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Nachdem Sie über die -Datei verfügen, müssen Sie sie einem benutzerdefinierten Modul oder Thema hinzufügen, das in Ihrer Adobe Commerce- und Magento Open Source-Instanz installiert ist. Befolgen Sie die Anweisungen im Abschnitt [Verwenden von benutzerdefiniertem JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) Thema, um diese Aufgabe zu erfüllen.

## Nutzung

Die AdobePrivacy JS Library bietet verschiedene Funktionen zum Verwalten von im Browser gespeicherten Identitätsdaten.

`retrieveIdentities()`
: Gibt ein Array von Identitäten aus einem Dienst zusammen mit einem Array von Identitäten zurück, die nicht im Dienst vorhanden sind

`removeIdentities()`
: Entfernt Identitäten aus dem Browser und gibt ein Array von Identitätsobjekten mit einer `isDeleteClientSide` boolesche Eigenschaft, die angibt, ob die Daten gelöscht wurden.

`retrieveThenRemoveIdentities()`
: Diese Funktion ähnelt der `removeIdentities()` , sodass ein Array von Identitäten abgerufen und aus dem Browser entfernt wird.

Weitere Informationen und Beispiele für die Verwendung dieser Funktionen finden Sie im Abschnitt [Offizielle Bibliotheksdokumentation](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Initialisierung

Neu instanziieren `AdobePrivacy` -Objekt, um die AdobePrivacy JS Library in Ihrem Implementierungscode zu verwenden.

```js
var adobePrivacy = new AdobePrivacy({});
```

Der Konstruktor akzeptiert ein Konfigurationsobjekt mit Parametern während der Instanziierung.
Siehe Abschnitt [Offizielle Bibliotheksdokumentation](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) für eine Liste dieser Konfigurationsparameter.
