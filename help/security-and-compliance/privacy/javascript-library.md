---
title: Privacy JavaScript-Bibliothek
description: Erfahren Sie, wie Sie mit benutzerdefinierten Tools auf von Adobe Commerce erfasste personenbezogene Kundendaten zugreifen und diese löschen können.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Privacy JavaScript-Bibliothek

Die Privacy JavaScript-Bibliothek umfasst eine Reihe von Tools, mit denen Sie einen Prozess für den Zugriff auf und das Löschen von privaten Daten erstellen können, die von Adobe Commerce erfasst werden.

Commerce-Datenverfolgungsdienste können private Informationen speichern, die für Datenschutzbestimmungen wie die [Datenschutz-Grundverordnung (DSGVO)](gdpr.md) und den California Consumer Privacy Act ([) gelten](ccpa.md).

Diese Bibliothek bietet eine Reihe von Funktionen zum Erstellen von Datenschutzanfragen und zum Erfassen ihrer Antworten. Verwenden Sie diese Bibliothek, um die im Browser gespeicherten Daten von den Adobe Commerce-Datenverfolgungs-Services abzurufen und zu entfernen.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Commerce keine Verhaltensdaten, bis der Käufer einwilligt. Wenn [!UICONTROL **Cookie-Einschränkungsmodus**] deaktiviert ist, erfasst Commerce standardmäßig Verhaltensdaten.

## Installation

Die Privacy JavaScript-Bibliothek ist unter dem folgenden CDN-Speicherort verfügbar: `commerce.adobe.net/magentoprivacy.js`

Nachdem Sie die Datei haben, müssen Sie sie einem benutzerdefinierten Modul oder Design hinzufügen, das in Ihrer Adobe Commerce-Instanz installiert ist. Befolgen Sie die Anweisungen unter [Verwenden benutzerdefinierter JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/), um diese Aufgabe durchzuführen.

### Initialisierung

Importieren und instanziieren Sie ein neues `MagentoPrivacy`-Objekt oder verwenden Sie das `window`-Objekt, um auf die Privacy JavaScript-Funktionen zuzugreifen.

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

Die Privacy JS Library bietet verschiedene Funktionen zum Verwalten von Identitätsdaten, die im Browser gespeichert sind.

`retrieveIdentity()`
: Gibt eine JavaScript-Zusage für ein Identitätsobjekt aus einem Service im Browser zurück.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Entfernt die Identitätsdaten aus einem Service im Browser.
Diese Funktion gibt eine JavaScript-Zusage für ein Identitätsobjekt mit einer `isDeleted` booleschen Eigenschaft zurück, die angibt, ob die Daten gelöscht wurden.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
