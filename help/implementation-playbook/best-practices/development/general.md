---
title: Allgemeine Best Practices zur Entwicklung
description: Erfahren Sie mehr über allgemeine Best Practices für die Entwicklung von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Allgemeine Best Practices zur Entwicklung für Adobe Commerce

In diesem Abschnitt werden die Grundlagen für einen reibungslosen Adobe Commerce-Entwicklungsprozess beschrieben. Es beschreibt grundlegende Prozesse, Kodierungsprinzipien und Anwendungsentwurfsprinzipien, die Entwicklerinnen und Entwicklern als Orientierungshilfe dienen.

>[!NOTE]
>
>Technische Architekten von Adobe verwenden diese Best Practices als Referenz bei Projekten, die mit der Entwicklung in Zusammenhang stehen.

Diese Best Practices basieren auf jahrelanger Erfahrung in der Entwicklung und Bereitstellung von Commerce-Projekten. Adobe empfiehlt, dass technische Initiativen diesen Best Practices folgen und dass Sie bestehende Prozesse und den Code verbessern, um sie an diese anzupassen.

## Textkonventionen

Die Schlüsselwörter „MUSS“, „DARF NICHT“, „ERFORDERLICH“, „MUSS“, „DARF NICHT“, „SOLLTE NICHT“, „SOLLTE NICHT“, „EMPFOHLEN“, „MAI“ und „OPTIONAL“ in diesem Thema sind wie in [RFC 2119“ ](https://datatracker.ietf.org/doc/html/rfc2119).

## Prozess

1. Vor Beginn der Projektaktivitäten muss eine definierte Projektmethodik vereinbart werden. Es KANN sich um Scrum, Waterfall oder eine andere Methodik oder eine Kombination von Methodiken handeln, solange sie definiert ist.
1. Die Entwicklung SOLLTE ERST beginnen, wenn dem Entwicklungs-Team eine Verzweigungsstrategie für das Versionskontrollsystem zur Verfügung steht.
1. Die Entwicklung SOLLTE ERST nach der Genehmigung für technische Spezifikationen, die Genehmigung für Benutzergeschichten und Anwendungsfälle und die Genehmigung für Testfälle beginnen, die dem Entwicklungs-Team zur Verfügung stehen.
1. Die Entwicklung SOLLTE ERST beginnen, wenn mindestens eine Entwicklungs- und QS-Umgebung verfügbar ist.
1. Projektspezifische Anforderungen, die für den Start der Entwicklung zwingend erforderlich sind, KÖNNEN in einer _Definition von Bereit_ dokumentiert werden.
1. Die Genehmigung SOLLTE von einem Kundenbetreuer erfolgen, der befugt ist, Projektlieferungen zu genehmigen.
1. In agilen Projektmethoden können nach der Genehmigung zusätzliche Anforderungen folgen. Diese Anforderungen SOLLTEN als neue Anforderungen behandelt und entsprechend erfasst, architektonisch gestaltet und geplant werden.
1. Die gesamte Entwicklung MUSS vom Entwickler vor der Übermittlung funktionell getestet werden.
1. Alle Entwickler SOLLTEN automatisierte Tests bestehen, bevor sie zur Code-Überprüfung übermittelt werden. KANN nach der Erstellung einer Pull-Anfrage als automatisierter Prozess konfiguriert werden.
1. Alle Entwicklungsprojekte MÜSSEN eine manuelle Code-Prüfung durch einen technischen Architekten oder einen leitenden Entwickler bestehen, bevor sie zur Qualitätssicherung eingereicht werden.
1. Die gesamte Entwicklung MUSS vor der Lieferung an den Kunden die Qualitätssicherung bestehen.
1. Projektspezifische Anforderungen, die für die Bereitstellung obligatorisch sind, KÖNNEN in einer „Definition von „Fertig“ dokumentiert werden.

## Umgebung

1. Alle Entwickler SOLLTEN dieselbe IDE verwenden. PhpStorm ist die empfohlene IDE für die Adobe Commerce-Entwicklung.
1. Alle Entwickler SOLLTEN mit demselben Technologie-Stack entwickeln und testen, der auf den (zukünftigen) Produktions-Servern verwendet wird. Die Versionen der Software in diesem Technologie-Stack MÜSSEN mit der Haupt- und Nebenversion der auf den Produktions-Servern installierten Software übereinstimmen. Weitere [ zum typischen Technologie](../../../installation/system-requirements.md)Stack für Adobe Commerce finden Sie unter „Systemanforderungen“.
1. Der Systemadministrator oder technische Architekt kann dem Team eine zentral gepflegte lokale Entwicklungsumgebung zur Verfügung stellen, um gleiche und aktuelle lokale Umgebungen zu gewährleisten und zu fördern.
1. Entwickler und QA-Techniker MÜSSEN Zugriff auf die Befehlszeile, die Datenbank und die Protokolldateien der QS-Umgebung haben. Dies erfordert MÖGLICHERWEISE eine VPN-Verbindung.

## Versionierung

Modulversionen MÜSSEN dem Standard [Semantic Versioning 2.0.0“ ](https://semver.org/).
Abhängigkeiten von der Adobe Commerce-Codebasis SOLLTEN den [Richtlinien für Modulversionsabhängigkeiten](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) entsprechen.

## REVISIONSKONTROLLE

Commits MÜSSEN von aussagekräftigen Commit-Nachrichten begleitet werden.

## Sicherheit

1. [Nicht sichere Funktionen](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) SOLLTEN NICHT verwendet werden.
1. [XSS-Präventionsstrategien](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) SOLLTEN angewendet werden.
1. [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) SOLLTEN angewendet werden.
1. Neue Adobe Commerce-Instanzen SOLLTEN mit der neuesten Sicherheitsversion einer Version bereitgestellt werden, die das Datum des „Endes der Sicherheitskorrekturen“ noch nicht erreicht hat. Siehe [Adobe Commerce-Software-Lebenszyklusrichtlinie](../../../release/lifecycle-policy.md).
