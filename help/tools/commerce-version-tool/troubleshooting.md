---
title: Fehlerbehebung bei [!DNL Commerce Version Tool]
description: Erfahren Sie, wie Sie Fehler  [!DNL Commerce Version Tool]  der Composer-Erkennung, interne Probelauf-Prüfungen, Registrierungs-Cache, JSON-Ausgabe und Auditprotokollprobleme beheben können.
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# Fehlerbehebung bei [!DNL Commerce Version Tool]

Verwenden Sie diese Seite, um häufige [!DNL Commerce Version Tool] ([!DNL CVT]) Probleme mit der Composer-Erkennung, dem Laden der Registrierung, der internen Probelauf-Patch-Erkennung, der Ausgabegenerierung und der Auditprotokollierung zu beheben.

## Schritte zur schnellen Fehlerbehebung

Wenn das [!DNL CVT]-Tool nicht den erwarteten Patch-Statusbericht zurückgibt:

- Vergewissern Sie sich, dass die Target-Installation eine unterstützte Adobe Commerce-Version und -Edition verwendet.
- Vergewissern Sie sich, dass `composer.lock` vorhanden ist und der Umgebung entspricht, die Sie untersuchen möchten.
- Vergewissern Sie sich, dass PHP und das System `patch` Binärdatei verfügbar sind.
- Vergewissern Sie sich, dass [!DNL CVT] die Patch-Registrierungsdatei lesen können.
- Überprüfen Sie `warnings`, `missing_patches` und `unknown_patches` in der Ausgabe.
- Wenn die Protokolldatei erstellt wurde, prüfen Sie `var/log/patch_status.log` auf die Audit-Zusammenfassung aus der Ausführung.

>[!TIP]
>
> Die Protokolldatei ist am hilfreichsten, wenn Sie verstehen müssen, warum ein Patch nicht klassifiziert werden konnte. Für jeden unbekannten Patch wird im Protokoll die Rohausgabe der Vorwärts- und Rückwärts-Probelauf-Versuche aufgezeichnet, einschließlich aller Fehler oder Hunk-Fehler.
>
> Wenn beim Abrufen der Registrierung oder der Patch-Dateien Probleme auftreten, überprüfen Sie das Feld Warnungen im Bericht. Diese Details werden nicht im Protokoll angezeigt.

## Häufige Probleme und Lösungen

### Basisversion kann nicht erkannt werden

Wenn das [!DNL CVT]-Tool die Adobe Commerce-Basisversion nicht finden kann, überprüfen Sie die folgenden Bedingungen:

**Überprüfen:**

- `composer.lock` fehlt.
- Der `patch-status`-Befehl wird außerhalb des Adobe Commerce-Projektstamms ausgeführt (oder `--root` auf den falschen Pfad verweist) und `composer.lock` nicht gefunden.
- `composer.lock` ist vorhanden, ist aber kein gültiges JSON oder kann nicht gelesen werden.
- `composer.lock` enthält keines der erkannten Basispakete (`magento/product-enterprise-edition`, `magento/product-community-edition`, `magento/magento2-base`).

**Warnmeldungen:**

Wenn `composer.lock` vorhanden, aber nicht lesbar oder nicht analysierbar ist oder kein erkanntes Basispaket enthält, gibt das Tool eine der folgenden Zeichenfolgen im Feld Warnausgabe aus:

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> Wenn `composer.lock` vollständig fehlt, meldet das Tool `base_version: "unknown"` mit **überhaupt keine Warnmeldung**. Überprüfen Sie `base_version` immer direkt in der Ausgabe. Verlassen Sie sich nicht auf das Vorhandensein einer Warnung, um dieses Problem zu finden.

Eine der zuvor erwähnten Bedingungen deutet darauf hin, dass das Tool die Basisversion nicht erkennen kann. Das Tool wird mit Code `1` beendet, ohne dass eine Patch-Erkennung durchgeführt wird.

**Aktionen:**

- Führen Sie den `patch-status`-Befehl aus dem Stammverzeichnis des [!DNL Adobe Commerce]-Projekts aus oder übergeben Sie die richtigen `--root`.
- Vergewissern Sie sich, dass `composer.lock` vorhanden, aktuell und gültiges JSON ist.
- Bestätigen Sie, dass bei der Installation eine unterstützte Adobe Commerce-Edition verwendet wird, sodass `composer.lock` eines der erkannten Basispakete enthält.

### Für die installierte Version gelten keine Patches

Wenn [!DNL CVT] einen gültigen `base_version` meldet, aber die `applied_patches`, `missing_patches` und `unknown_patches` leer sind, wird die installierte Version nicht von der aktuellen Patch-Registrierung abgedeckt.

**Überprüfen:**

- Die installierte Version [!DNL Adobe Commerce] wird in der Patch-Registrierungsdatei nicht angezeigt. Beispielsweise eine Version, die neuer ist als die neuesten Einträge in der Registrierung.

**Warnmeldungen:**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

Diese Warnung unterscheidet sich von „Basisversion kann nicht erkannt werden“. Der `base_version` ist korrekt, das Tool wird `0` beendet, und es gibt nichts in der Registrierung, mit dem man vergleichen könnte.

**Aktionen:**

- Bestätigen Sie, dass `base_version` in der Ausgabe das ist, was Sie erwarten.
- Vergewissern Sie sich, `registry_source` es sich um eine `remote` oder eine aktuelle `cache` handelt, nicht um eine veraltete.
- Wenden Sie sich an den Adobe Commerce-Support, wenn die Version bereits abgedeckt sein sollte.

### Patch-Registrierung kann nicht abgerufen werden

Wenn das [!DNL CVT]-Tool die neueste Patch-Registrierungsdatei nicht abrufen kann, überprüfen Sie die Netzwerk- und Cache-Einstellungen:

**Überprüfen:**

- Das Netzwerk ist nicht verfügbar.
- Zeitüberschreitung bei Adobe-Patch-Endpunktanfrage.
- `--no-cache` wurde verwendet und die Remote-Registrierung kann nicht erreicht werden.
- `PATCH_REGISTRY_URL` verweist auf eine nicht verfügbare Registrierung oder ist keine gültige HTTPS-URL.
- Wenn das [!DNL CVT]-Tool die neueste Patch-Registrierungsdatei nicht abrufen kann, überprüfen Sie die Netzwerk- und Cache-Einstellungen:

>[!NOTE]
>
>Wenn die Registrierungsdatei fehlt oder abgelaufen ist, lädt das Tool die neueste Registrierung vom Remote-Host herunter.

**Warnmeldungen:**

Das Tool gibt für dieses Szenario die folgenden Zeichenfolgen im Feld „Warnausgabe“ aus:

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

Die veraltete Cache-Nachricht enthält das tatsächliche Alter in Stunden, z. B. `(3 hours old)`.

Die `patch registry could not be loaded`- und `could not fetch remote registry`-Warnungen zeigen an, dass das Tool beendet wurde, ohne die Patch-Erkennung auszuführen.

**Aktionen:**

- Führen Sie den Befehl `patch-status` erneut aus, wenn die Netzwerkverbindung verfügbar ist.
- Lassen Sie das [!DNL CVT]-Tool die zwischengespeicherte Registrierung verwenden, wenn eine veraltete Cache-Warnung für die Überprüfung akzeptabel ist.
- Entfernen Sie `--no-cache`, es sei denn, Sie benötigen neue Remote-Abrufe.
- Vergewissern Sie sich, dass das [!DNL CVT]-Tool `var/patch_metadata/` schreiben kann, wenn Sie den Registrierungs-Cache wiederverwenden möchten.

### Patch-Differenz kann nicht abgerufen oder überprüft werden

Wenn das [!DNL CVT]-Tool ein oder mehrere anwendbare Patches nicht testen kann, überprüfen Sie den Patch-Vergleichszugriff:

**Überprüfen:**

- Vom Patch-Endpunkt von Adobe kann keine Patch-Differenz heruntergeladen werden.
- Erforderliche Anmeldeinformationen für authentifizierte Patch-Downloads fehlen oder sind ungültig.
- `PATCH_DIFF_BASE_URL` verweist auf eine nicht verfügbare Patch-Diff-Quelle oder ist keine gültige HTTPS-URL.
- Die zwischengespeicherte Patch-Differenz fehlt oder ist nicht lesbar.
- Die SHA-256-Verifizierung schlägt bei einem heruntergeladenen Patch-Diff fehl.
- Das [!DNL CVT] kann nicht in `var/patch_metadata/.patch_diffs/` schreiben.

**Warnmeldungen:**

Das Tool gibt für dieses Szenario die folgenden Zeichenfolgen im Feld „Warnausgabe“ aus:

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

Die Patch-ID in jeder Nachricht ist die tatsächliche Registrierungs-Eintrags-ID, z. B. `247p9-2026-05-001-EE`. `SHA-256 verification failed` bedeutet, dass eine neu heruntergeladene Patch-Datei nicht der erwarteten Prüfsumme entsprach. Das Tool verwirft es ohne Zwischenspeicherung und klassifiziert die Patch-`unknown` für diese Ausführung. Ein beschädigter *lokaler* Cache-Eintrag wird erkannt und im Hintergrund innerhalb derselben Ausführung ohne Warnung erneut abgerufen. In beiden Fällen ist keine manuelle Cache-Bereinigung erforderlich.

**Aktionen:**

- Überprüfen Sie die Netzwerkverbindung und führen Sie den Befehl erneut aus.
- Überprüfen Sie, ob die erforderlichen Anmeldeinformationen für authentifizierte Patch-Downloads konfiguriert sind.
- Vergewissern Sie sich, dass das [!DNL CVT]-Tool `var/patch_metadata/.patch_diffs/` schreiben kann.
- Behalten Sie die Warn- und Ausgabedetails bei, wenn der Patch weiterhin als unbekannt klassifiziert bleibt.

### Fehlende oder unbekannte Patches werden gemeldet

Wenn der Bericht unerwartete `missing_patches`- oder `unknown_patches` enthält, überprüfen Sie die Installations- und Ausgabedetails:

**Überprüfen:**

- Monatliche Patches wurden nicht in der richtigen Reihenfolge angewendet.
- Ein komponentenspezifischer Patch, z. B. Adobe Commerce Business-to-Business (B2B) oder Adobe Commerce Page Builder, fehlt.
- `composer.lock` meldet eine installierte Komponentenversion, für die der Patch erforderlich ist.
- Eine Patch-Differenz ist nicht verfügbar oder das Erkennungsergebnis ist nicht schlüssig.

**Warnmeldungen:**

Das Tool gibt für dieses Szenario die folgenden Zeichenfolgen im Feld „Warnausgabe“ aus:

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

Wenn Sie in einer Warnung auf `may be inaccurate` stoßen, wird die Probelauf-Prüfung weiterhin ausgeführt, jedoch mit reduzierter Konfidenz. Der Patch könnte weiterhin in `applied_patches` oder `missing_patches` kategorisiert werden, nicht unbedingt `unknown_patches`.

Insbesondere für unbekannte Patches zeichnet `var/log/patch_status.log` die Rohdaten der Patch-Probelauf-Ausgabe (vor und zurück) auf, die angibt, welche Dateien und Blöcke nicht übereinstimmen.

Wenn die Warnung „Keine Patches gefunden“ angezeigt wird, lesen Sie den Abschnitt [Keine Patches für die installierte Version](#no-patches-apply-to-the-installed-version) für Anleitungen.

**Aktionen:**

- Überprüfen Sie die Felder `applied_patches`, `missing_patches` und `unknown_patches` .
- Überprüfen Sie, ob die fehlenden Patches für die installierte Edition und die Komponenten gelten.
- Vergleichen Sie das Ergebnis mit den entsprechenden Sicherheits-Patch-Versionshinweisen.
- Vergewissern Sie sich, dass die überprüfte Code-Basis mit der bereitgestellten Umgebung übereinstimmt, über die Sie einen Bericht erstellen möchten.
- Wenden Sie sich an den Adobe Commerce-Support, wenn der unbekannte Status die Planung von Korrekturen blockiert.

### Ausgabe wird nicht generiert

Wenn das [!DNL CVT]-Tool abgeschlossen wird, aber die erwartete JSON- oder CSV-Ausgabe fehlt, überprüfen Sie die Befehlssyntax und die Terminal-Ausgabe:

**Aktionen:**

- Verwenden Sie die standardmäßige JSON-Ausgabe, wenn keine CSV-Ausgabe erforderlich ist.
- Verwenden Sie `--format=csv`, um eine CSV-Ausgabe zu generieren.
- Vergewissern Sie sich, dass die Befehlsausgabe von der Shell, dem Skript oder dem Scanner, auf dem das [!DNL CVT]-Tool ausgeführt wird, nicht umgeleitet oder verworfen wird.
- Überprüfen Sie `stderr` auf `patch-status:` Fehlermeldungen.
- Wenn Sie die Ausgabe an eine Datei umleiten, z. B. `patch-status > report.json`, bestätigen Sie, dass die Shell über Schreibberechtigungen für dieses Ziel verfügt. Das Tool schreibt nur in `stdout`.
- Vergewissern Sie sich, dass das [!DNL CVT]-Tool `var/log/patch_status.log` schreiben kann.
- Führen Sie den Befehl erneut aus und erfassen Sie die Terminal-Ausgabe zur Fehlerbehebung.

## Hilfe wird abgerufen

Wenn Sie sich an den Adobe Commerce-Support wenden, geben Sie nur die Details an, die zur Untersuchung des Problems erforderlich sind.

Einschließen:

- Adobe Commerce-Version und -Edition
- Version des [!DNL CVT] Tools
- Registrierungsquelle aus der Ausgabe des [!DNL CVT]-Tools
- Relevante `applied_patches`-, `missing_patches`- und `unknown_patches`
- Relevante Warnhinweise
- Fehlermeldung oder Befehlsausgabe

Geheime Daten, Anmeldeinformationen, private Schlüssel oder nicht verwandte Kundendaten dürfen nicht in freigegebene Protokolle oder Anhänge aufgenommen werden.

## Verwandte Themen

- [Einführung](intro.md)
- [Erstellen eines Patch-Statusberichts](generate-report.md)
- [Versionshinweise](release-notes.md)
