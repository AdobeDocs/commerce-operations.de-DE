---
title: Privacy JavaScript Library
description: Erfahren Sie, wie Sie mit benutzerdefinierten Tools auf personenbezogene Daten von Adobe Commerce und Magento Open Source zugreifen und diese löschen können.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Privacy JavaScript Library

Die Datenschutz-JavaScript-Bibliothek ist eine Reihe von Tools, mit denen Sie einen Prozess für den Zugriff auf und das Löschen von durch Adobe Commerce und Magento Open Source erfassten privaten Daten erstellen können.

Tracking-Dienste für Commerce-Daten können private Informationen speichern, die auf Datenschutzbestimmungen wie [Die Datenschutz-Grundverordnung (DSGVO)](gdpr.md) und [California Consumer Privacy Act (CCPA)](ccpa.md).

Diese Bibliothek bietet eine Reihe von Funktionen zum Erstellen von Datenschutzanfragen und zum Erfassen ihrer Antworten. Verwenden Sie diese Bibliothek, um die im Browser von Adobe Commerce und Magento Open Source-Datenverfolgungsdiensten gespeicherten Daten abzurufen und zu entfernen.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Commerce erst dann Verhaltensdaten, wenn der Käufer zustimmt. Wenn [!UICONTROL **Cookie-Einschränkungsmodus**] deaktiviert ist, erfasst Commerce standardmäßig Verhaltensdaten.

## Installation

Die Datenschutz-JavaScript-Bibliothek ist unter folgendem CDN-Speicherort verfügbar: `commerce.adobe.net/magentoprivacy.js`

Nachdem Sie über die -Datei verfügen, müssen Sie sie einem benutzerdefinierten Modul oder Thema hinzufügen, das in Ihrer Adobe Commerce- oder Magento Open Source-Instanz installiert ist. Befolgen Sie die Anweisungen im Abschnitt [Verwenden von benutzerdefiniertem JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) Thema, um diese Aufgabe zu erfüllen.

### Initialisierung

Importieren und Instanziieren eines neuen `MagentoPrivacy` -Objekt oder verwenden Sie `window` -Objekt, um auf die Privacy JavaScript-Funktionen zuzugreifen.

Anwendungsbeispiel `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Anwendungsbeispiel `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Nutzung

Die Privacy JS Library bietet verschiedene Funktionen zum Verwalten von im Browser gespeicherten Identitätsdaten.

`retrieveIdentity()`
: Gibt ein JavaScript-Versprechen für ein Identitätsobjekt aus einem Dienst im Browser zurück.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Entfernt die Identitätsdaten aus einem Dienst im Browser.
Diese Funktion gibt ein JavaScript-Versprechen für ein Identitätsobjekt mit einer `isDeleted` boolesche Eigenschaft, die angibt, ob die Daten gelöscht wurden.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
