---
title: Privacy JavaScript Library
description: Erfahren Sie, wie Sie mit benutzerdefinierten Tools auf von Adobe Commerce erfasste personenbezogene Kundendaten zugreifen und diese löschen können.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Privacy JavaScript Library

Die Privacy JavaScript Library ist eine Reihe von Tools, die Ihnen beim Erstellen eines Prozesses für den Zugriff auf und das Löschen von durch Adobe Commerce erfassten privaten Daten helfen.

Commerce-Datenverfolgungsdienste können personenbezogene Daten speichern, die für Datenschutzbestimmungen wie die [Datenschutz-Grundverordnung (DSGVO)](gdpr.md) und den [California Consumer Privacy Act (CCPA)](ccpa.md) gelten.

Diese Bibliothek bietet eine Reihe von Funktionen zum Erstellen von Datenschutzanfragen und zum Erfassen ihrer Antworten. Verwenden Sie diese Bibliothek, um die im Browser von Adobe Commerce-Datenverfolgungsdiensten gespeicherten Daten abzurufen und zu entfernen.

>[!NOTE]
>
>Wenn der [Cookie-Beschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Commerce erst dann Verhaltensdaten, wenn der Käufer zustimmt. Wenn der [!UICONTROL **Cookie-Beschränkungsmodus**] deaktiviert ist, erfasst Commerce standardmäßig Verhaltensdaten.

## Installation

Die Privacy JavaScript Library ist unter folgendem CDN-Speicherort verfügbar: `commerce.adobe.net/magentoprivacy.js`

Nachdem Sie über die Datei verfügen, müssen Sie sie einem benutzerdefinierten Modul oder Design hinzufügen, das in Ihrer Adobe Commerce-Instanz installiert ist. Befolgen Sie die Anweisungen, die im Thema [Verwenden von benutzerdefiniertem JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) beschrieben sind, um diese Aufgabe durchzuführen.

### Initialisierung

Importieren und instanziieren Sie ein neues `MagentoPrivacy` -Objekt oder verwenden Sie das `window` -Objekt, um auf die Privacy JavaScript-Funktionen zuzugreifen.

Beispiel mit `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Beispiel mit `window`:

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
Diese Funktion gibt ein JavaScript-Versprechen für ein Identitätsobjekt mit der booleschen Eigenschaft `isDeleted` zurück, um anzugeben, ob die Daten gelöscht wurden.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
