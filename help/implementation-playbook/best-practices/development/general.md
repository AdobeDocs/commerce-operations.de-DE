---
title: Allgemeine Best Practices für die Entwicklung
description: Erfahren Sie mehr über die allgemeinen Best Practices für die Entwicklung von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Allgemeine Best Practices für die Entwicklung von Adobe Commerce

Hier wird die Grundlinie für einen gesunden Adobe Commerce-Entwicklungsprozess beschrieben. Es beschreibt grundlegende Prozesse, Kodierungsprinzipien und Grundsätze für das Anwendungsdesign, die Entwicklern als Orientierung dienen.

>[!NOTE]
>
>Adobe Technical Architects verwenden diese Best Practices als Referenz bei Entwicklungsinteraktionen.

Diese bewährten Verfahren wurden auf der Grundlage jahrelanger Erfahrung bei der Entwicklung und Durchführung von Commerce-Projekten entwickelt. Adobe empfiehlt, dass technische Initiativen diesen Best Practices folgen und bestehende Prozesse und Code zur Anpassung an sie verbessern.

## Textkonventionen

Die Schlüsselwörter &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHALL&quot;, &quot;SHALL NOT&quot;, &quot;SOULD&quot;, &quot;SOULD NOT&quot;, &quot;EMPFOHLEN&quot;, &quot;MAY&quot;und &quot;OPTIONAL&quot;in diesem Thema sind wie in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) beschrieben zu interpretieren.

## Prozess

1. Vor Beginn der Projektaktivitäten MUSS eine definierte Projektmethodik vereinbart werden. Es kann sich um Scrum, Waterfall oder eine andere Methode oder eine Kombination von Methoden handeln, solange sie definiert ist.
1. Die Entwicklung SOLLTE NICHT beginnen, bis dem Entwicklungsteam eine Verzweigungsstrategie für das Versionskontrollsystem zur Verfügung steht.
1. Die Entwicklung SOLLTE NICHT beginnen, bis nach der Abmeldung von technischen Spezifikationen, der Abmeldung von Benutzermeldungen und Nutzungsszenarios und der Abmeldung von Testfällen dem Entwicklungsteam zur Verfügung stehen.
1. Die Entwicklung SOLLTE NICHT beginnen, bis mindestens eine Entwicklungs- und QA-Umgebung verfügbar ist.
1. Projektspezifische Anforderungen, die zum Starten der Entwicklung erforderlich sind, KÖNNEN in einer _Definition von Bereit_ dokumentiert werden.
1. Die Abmeldung SOLLTE von einem Kundenbetreuer vorgenommen werden, der zur Abmeldung von Projektlieferungen berechtigt ist.
1. Bei den Agile-Projektmethoden können nach der Unterzeichnung zusätzliche Anforderungen gestellt werden. Diese Anforderungen SOLLTEN als neue Anforderungen behandelt und entsprechend erfasst, gestaltet und geplant werden.
1. Die gesamte Entwicklung MUSS vom Entwickler vor der Übermittlung funktional getestet werden.
1. Die gesamte Entwicklung SOLLTE automatisierte Tests bestehen, bevor sie zur Codeüberprüfung eingereicht wird. Dies kann als automatisierter Prozess nach der Erstellung von Pull-Anforderungen konfiguriert werden.
1. Jede Entwicklung MUSS eine manuelle Code-Überprüfung durch einen technischen Architekten oder Lead-Entwickler bestehen, bevor sie zur Qualitätssicherung eingereicht wird.
1. Alle Entwicklungen MÜSSEN vor der Lieferung an den Kunden die Qualitätssicherung bestehen.
1. Projektspezifische Anforderungen, die für den Versand erforderlich sind, KÖNNEN in einer &quot;Definition der Fertig&quot;dokumentiert werden.

## Umgebung

1. Alle Entwickler sollten dieselbe IDE verwenden. PhpStorm ist die empfohlene IDE für die Adobe Commerce-Entwicklung.
1. Alle Entwickler SOLLTEN den gleichen Technologiestapel entwickeln und testen wie auf den (zukünftigen) Produktionsservern. Die Versionen der Software in diesem Technologie-Stack MÜSSEN mit der Haupt- und Nebenversion der Software übereinstimmen, die auf den Produktionsservern installiert ist. Weitere Informationen zum typischen Technologiestapel für Adobe Commerce finden Sie unter [Systemanforderungen](../../../installation/system-requirements.md) .
1. Der Systemadministrator oder Technische Architekt kann dem Team eine zentral gepflegte lokale Entwicklungsumgebung zur Verfügung stellen, um gleiche und aktuelle lokale Umgebungen zu gewährleisten und zu fördern.
1. Entwickler und QA-Techniker MÜSSEN Zugriff auf die Befehlszeile, die Datenbank und die Protokolldateien der QA-Umgebung haben. Dies kann eine VPN-Verbindung erfordern.

## Versionierung

Modulversionen MÜSSEN dem [Semantic Versioning 2.0.0 standard](https://semver.org/) entsprechen.
Abhängigkeiten von der Adobe Commerce-Codebasis sollten den [Richtlinien für Modulversionsabhängigkeiten](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) entsprechen.

## REVISIONSKONTROLLE

Commits MÜSSEN von aussagekräftigen Commit-Nachrichten begleitet werden.

## Sicherheit

1. [Nicht sichere Funktionen](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) SOLLTEN NICHT verwendet werden.
1. [XSS-Präventionsstrategien](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) SOLLTEN angewendet werden.
1. [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) SOLLTEN angewendet werden.
1. Neue Adobe Commerce-Instanzen SOLLTEN bei der neuesten Sicherheitsversion einer Version bereitgestellt werden, die noch nicht das Datum &quot;Ende der Sicherheitskorrekturen&quot;erreicht hat. Siehe [Adobe Commerce-Software-Lebenszyklusrichtlinie](../../../release/lifecycle-policy.md).
