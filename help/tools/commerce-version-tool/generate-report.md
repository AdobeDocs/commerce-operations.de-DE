---
title: Erstellen eines Berichts zum Patch-Status
description: Erfahren Sie, wie Sie mit  [!DNL Commerce Version Tool]  Patch-Statusberichte für Adobe Commerce im JSON- oder CSV-Format erstellen können.
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# Erstellen eines Patch-Statusberichts

Verwenden Sie [!DNL Commerce Version Tool] ([!DNL CVT]), um einen Patch-Statusbericht für eine Adobe Commerce-Installation zu generieren. Der Bericht identifiziert angewendete, fehlende und unbekannte monatliche Sicherheits-Patches und gibt standardmäßig JSON-Ausgaben zurück.

## Voraussetzungen

Bevor Sie [!DNL CVT] ausführen, überprüfen Sie Folgendes:

- Die Target-Installation verwendet eine unterstützte Adobe Commerce-Version und -Edition.
- `composer.lock` ist vorhanden und entspricht der Umgebung, die Sie untersuchen möchten.
- PHP und das System `patch` Binärdatei sind verfügbar.
- Sie können die Projektdateien aus der Umgebung lesen, in der Sie den Befehl ausführen.
- Das Tool kann in `var/patch_metadata/` schreiben und `var/log/`, wenn Sie Cache-Dateien und Audit-Protokolleinträge speichern möchten.
- Anmeldeinformationen sind über `COMPOSER_AUTH` oder `auth.json` verfügbar, wenn berechtigungsbezogene Patches für die Installation gelten.

Das [!DNL CVT]-Tool überprüft `COMPOSER_AUTH`, die Adobe Commerce-`auth.json` und die Global Composer-`auth.json` auf berechtigungsbezogene Patch-Anmeldeinformationen.

## Bericht erstellen

Führen Sie im Stammverzeichnis des Adobe Commerce-Projekts Folgendes aus:

```bash
vendor/bin/patch-status
```

Um eine andere Adobe Commerce-Installation zu überprüfen, verwenden Sie die `--root`:

```bash
vendor/bin/patch-status --root=/path/to/commerce
```

## Befehlsoptionen

JSON ist das Standardausgabeformat. Die CSV-Ausgabe wird für Scanner, Dashboards und Konformitätsberichte unterstützt.

| Option | Beschreibung |
| --- | --- |
| `--root=PATH` | Gibt den Pfad zum Adobe Commerce-Installationsstamm an. Der Standardwert ist das aktuelle Verzeichnis. |
| `--format=json\|csv` | Legt das Ausgabeformat fest. Der Standardwert lautet `json`. |
| `--no-cache` | Umgeht Registrierungs- und Patch-Diff-Caches, erzwingt neue Remote-Abrufe und beendet den Vorgang mit einem Fehler, wenn die Remote-Registrierung nicht verfügbar ist. |
| `--version`, `-V` | Druckt die Tool-Version. |
| `--help`, `-h` | Druckt die Hilfemeldung. |

{style="table-layout:auto"}

## Überprüfen der JSON- und CSV-Ausgabe

Das folgende Beispiel zeigt die standardmäßige JSON-Ausgabe.

```bash
vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

Um eine CSV-Ausgabe zu generieren, verwenden Sie die Option `--format=csv` :

```bash
vendor/bin/patch-status --format=csv
```

Die CSV-Ausgabe erzeugt eine Zeile pro CVE und eignet sich für Tabellen, Scanner, Dashboards und Compliance-Tools.

## Berichtsergebnisse verstehen

Überprüfen Sie fehlende und unbekannte Patches, bevor Sie Ansprüche auf den Sicherheitsstatus erheben.

### Patch-Statuswerte

Der Bericht „patch-status“ gruppiert die Patch-Ergebnisse anhand der folgenden Werte:

| Patch-Status | Bedeutung |
| --- | --- |
| Angewendet | Das [!DNL CVT]-Tool erkennt den monatlichen Sicherheits-Patch in der Adobe Commerce-Code-Basis. |
| Fehlend | Der Patch gilt für die installierte Adobe Commerce-Version oder -Komponente, das [!DNL CVT]-Tool erkennt ihn jedoch nicht. |
| Unbekannt | Das Tool kann den Patch-Status nicht über die verfügbare Registrierung, den Patch-Unterschied oder das Erkennungsergebnis bestätigen. |

{style="table-layout:auto"}

### CVE-Statuswerte

Die JSON-Ausgabe meldet CVE-Statuswerte in Großbuchstaben.

| CVE-Status | Bedeutung |
| --- | --- |
| `PROTECTED` | Der entsprechende Patch wird für den CVE oder die Komponente erkannt. |
| `VULNERABLE` | Für den CVE oder die Komponente fehlt ein entsprechender Patch. |
| `UNKNOWN` | Das [!DNL CVT]-Tool kann den CVE-Status nicht aus den verfügbaren Registrierungs- und Erkennungsdaten ermitteln. |
| `NOT_APPLICABLE` | Der CVE gilt für eine Komponente, die nicht installiert ist, z. B. Adobe Commerce Business-to-Business (B2B), Adobe Commerce Page Builder oder Adobe Commerce Inventory. |

{style="table-layout:auto"}

### Wichtige Ausgabefelder

Der Bericht kann die folgenden Informationen enthalten:

- **Adobe Commerce-Basisversion** - Die installierte Basisversion, die von `composer.lock` erkannt wurde.
- **Registrierungsquelle** - Ob Patch-Metadaten von `remote`, `cache` oder `stale_cache` stammen.
- **Installierte Komponenten** - Von `composer.lock` erkannte Adobe Commerce-Paketbereiche.
- **Angewendete Patches** - Monatliche Sicherheits-Patches, die in der Adobe Commerce-Code-Basis erkannt werden.
- **Fehlende Patches** - Monatliche Sicherheits-Patches, die gelten, aber nicht erkannt werden.
- **Unbekannte Patches** - Patches, die das [!DNL CVT]-Tool nicht klassifizieren kann.
- **Vulnerabilitätsstatus nach CVE** - CVE-Abdeckung zugeordnet zu Status „Geschützt“, „Anfällig“, „Nicht anwendbar“ oder „Unbekannt“.
- **Warnungen** - Bedingungen, die sich auf die Zuverlässigkeit oder Vollständigkeit des Berichts auswirken können.

## Patch-Registrierung und -Cache

Die Patch-Registrierungsdatei enthält die Patch-Metadaten, mit denen das [!DNL CVT]-Tool bestimmt, welche Patches für eine installierte Version gelten. Das Tool verwendet einen neuen Registrierungscache, sofern verfügbar, ruft bei Bedarf die Remote-Registrierung ab und kann einen veralteten Cache mit einer Warnung verwenden, wenn das Netzwerk nicht verfügbar ist. Verwenden Sie `--no-cache` nur, wenn Sie neue Remote-Abrufe benötigen.

## Verwandte Themen

- [Einführung](intro.md)
- [Fehlerbehebung](troubleshooting.md)
- [Versionshinweise](release-notes.md)
