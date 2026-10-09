---
title: '[!DNL Commerce Version Tool]'
description: Erfahren Sie mehr über die [!DNL Commerce Version Tool] für Adobe Commerce und überprüfen Sie mithilfe von Vendor/bin/patch-status den monatlichen Sicherheits-Patch-Status.
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
    internal-label: Reporting
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%
---
# [!DNL Commerce Version Tool]

Die monatlichen Sicherheits-Patches für Adobe Commerce sind nicht kumulativ und müssen nacheinander angewendet werden. Die [!DNL Commerce Version Tool] ([!DNL CVT]) hilft Händlern bei der Überprüfung der Patch-Abdeckung, indem sie meldet, welche monatlichen Sicherheits-Patches installiert sind, welche Patches fehlen und gegen welche CVEs die Installation geschützt ist.

>[!IMPORTANT]
>
>Das [!DNL CVT]-Tool dient nur zu Informationszwecken. Es werden keine Patches angewendet, Patches zurückgesetzt oder Adobe Commerce-Quelldateien geändert. Er kann Cache-Dateien, temporäre Dry-Run-Dateien und Audit-Protokolleinträge schreiben, um Patch-Statusberichte zu unterstützen.

## Tool-Übersicht

Das [!DNL CVT]-Tool ist eine eigenständige ausführbare Datei, die in jedem monatlichen Adobe Commerce-Sicherheits-Patch enthalten ist. Wenn der Patch auf eine Adobe Commerce-Installation angewendet wird, wird das Tool unter `vendor/bin/patch-status` installiert. Es erfordert PHP 8.1 oder höher und das System `patch` binär. Es erfordert keine Composer-Pakete, nicht standardmäßige PHP-Erweiterungen, Adobe Commerce-Bootstrap oder einen separaten Installationsschritt.

Das [!DNL CVT]-Tool kann Ihnen dabei helfen:

- Erkennen angewendeter Sicherheits-Patches für eine unterstützte Adobe Commerce-Installation.
- Identifizieren Sie fehlende Patches in einer monatlichen isolierten Sicherheits-Patch-Sequenz.
- Melden Sie geschützte, anfällige oder unbekannte Sicherheitsstatus für Patch-bezogene CVE-Aufzeichnungen (Common Vulnerabilities and Expositions).
- Erstellen von maschinenlesbaren Ausgaben wie JSON oder CSV für Scanner, Dashboards und Compliance-Berichte
- Patch-Status für unterstützte Plattformen und Komponenten erkennen.

## Verfügbarkeit

Das [!DNL CVT]-Tool unterstützt die Patch-Statusberichterstattung für die folgenden Plattformen und Komponenten, wenn Adobe Patch-Metadaten für die installierte Version in der Patch-Registrierungsdatei bereitstellt.

| Plattform oder Komponente | Verfügbarkeit |
| --- | --- |
| Adobe Commerce On-Premises | Unterstützt |
| [!DNL Magento Open Source] | Unterstützt |
| Adobe Commerce Business-to-Business (B2B) | Bei Installation unterstützt |
| Adobe Commerce Page Builder | Bei Installation unterstützt |
| Adobe Commerce-Inventar | Bei Installation unterstützt |
| Zusätzliche Komponenten von `composer.lock` erkannt | Wird unterstützt, wenn dies in der Patch-Registrierungsdatei dargestellt wird |

{style="table-layout:auto"}

## Häufige Anwendungsfälle

Verwenden Sie das [!DNL CVT] Tool, wenn Sie Folgendes tun müssen:

- Überprüfen Sie, ob eine Adobe Commerce-Installation erforderliche isolierte Sicherheits-Patches enthält.
- Überprüfen Sie, ob übersprungene oder unvollständige Patch-Sets die CVE-Abdeckung unvollständig lassen.
- JSON- oder CSV-Ausgabe für internes Reporting oder automatisiertes Scannen generieren.
- Geben Sie Informationen zum Patch-Status an, bevor Sie eine Support-Anfrage öffnen oder eine Problembehebung planen.

## Richtlinien für die Verwendung von Ergebnissen

Die Ausgabe des [!DNL CVT]-Tools als Erkennungsdaten behandeln, die die Patch-Planung und Sicherheitsüberprüfung unterstützen.

Befolgen Sie diese Richtlinien:

- Führen Sie das [!DNL CVT]-Tool für eine stabile und unterstützte Adobe Commerce-Installation aus.
- Überprüfen Sie fehlende und unbekannte Patches, bevor Sie Ansprüche auf den Sicherheitsstatus erheben.
- Bewahren Sie die JSON- oder CSV-Ausgabe für Prüfbarkeit und Automatisierung auf.
- Scanausgabe als sicherheitsrelevante Betriebsdaten behandeln.
- Geben Sie nur die Details frei, die für Support oder Problembehebung benötigt werden.

## Patch-Erkennung

Das [!DNL CVT]-Tool führt die Erkennung in zwei festen Schritten durch. Beide Schritte werden immer ausgeführt, wenn Sie einen Patch-Statusbericht generieren.

- **Composer-Erkennung:** Das Tool liest die `composer.lock`-Datei, um die [!DNL Adobe Commerce] Basisversion und die installierten Komponentenbereiche zu ermitteln. Wenn das Tool eine Basisversion nicht erkennen kann, wird sie mit Code `1` beendet.

- **Dry-Run-Erkennung:** Für jeden anwendbaren Patch verwendet das Tool eine Dry-Run-Prüfung anhand der Patch-Änderungen, um festzustellen, ob der Patch bereits angewendet wurde, nicht angewendet wurde oder ob der Patch-Status unbekannt ist. Das Tool behandelt Patch-Abhängigkeiten während dieser Prüfung, sodass die Ergebnisse die installierte Komponentenversion widerspiegeln.

Der Bericht enthält nur Patches, die für die erkannte Installation und die installierten Komponenten gelten. Wenn das Tool nicht bestätigen kann, ob ein entsprechender Patch vorhanden ist, wird der Patch als unbekannt klassifiziert.

## Mit der Verwendung von [!DNL CVT] beginnen

Verwenden Sie diese Themen, um Patch-Statusberichte zu generieren, zu beheben und zu verfolgen:

- [Erzeugen eines Patch-Statusberichts](generate-report.md), um das [!DNL CVT] Tool auszuführen, die Befehlsoptionen zu überprüfen und die Berichtsergebnisse zu interpretieren.
- [[!DNL Commerce Version Tool] Fehlerbehebung](troubleshooting.md) um unerwartete Ergebnisse oder Befehlsfehler zu beheben.
- [[!DNL Commerce Version Tool] Versionshinweise](release-notes.md) zur Überprüfung von Versionsaktualisierungen.
