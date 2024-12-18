---
title: Release-Richtlinie
description: Erfahren Sie mehr über die verschiedenen Versionen von Adobe Commerce, einschließlich „Minor“, „Patch“, „Security Patch“, „Feature“, „Hotfix“, „Individual Patch“ und „Custom Patch“.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b5d120893668f4315e289a204649270db4f7a6bc
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Adobe Commerce-Veröffentlichungsrichtlinie

Adobe Commerce verwendet [semantische Versionierung](https://semver.org/) auf der Ebene einzelner Module (z. B. `magento/framework 101.1.1`), aber nicht für die Marketing-Versionsnummer. Beispiel:

- **HAUPTVERSION**—2
- **NEBENVERSION**—2.4
- **PATCH-Version**—2.4.5
   - **SECURITY Patch-Version**—2.4.5-p1
      - Fehlerbehebung bei der Sicherheit
      - Sicherheitsverbesserung
- **BETA Patch-Version**—2.4.7-beta2
- **Version für Erweiterbarkeit, Infrastruktur und Services**
- **Hotfix**
- **Individuelles Patch**
- **Benutzerdefinierter Patch**

## NEBENVERSION

Die folgenden Richtlinien gelten für Nebenversionen:

- Umfassende Änderungen sind möglich. Code, der für Adobe Commerce 2.2.x geschrieben wurde, funktioniert möglicherweise nicht mehr mit Adobe Commerce 2.3.x. Beispielsweise können kleinere Versionen die Unterstützung für wichtige Systemanforderungen und -abhängigkeiten wie PHP einführen.
- Modulversionen können variieren. Beispielsweise werden einige Moduländerungen in einem neuen Patch eingeführt, während andere in einer Nebenversion eingeführt werden.
- Nebenversionen können neue Funktionen enthalten, für die Sie oder Ihr Lösungspartner während des Upgrades möglicherweise zusätzliche Arbeit benötigen, um die Kompatibilität sicherzustellen.
- Nebenversionen können Fehlerbehebungen für Sicherheits- und Qualitätsprobleme enthalten.

## PATCH-Version

Patch-Versionen konzentrieren sich in erster Linie auf die Bereitstellung von Sicherheits-, Leistungs-, Kompatibilitäts- und Qualitätskorrekturen mit hoher Priorität, damit Sie Ihre Sites auch weiterhin optimal nutzen können.

Die folgenden Richtlinien gelten für Patch-Versionen:

- Die neueste unterstützte Nebenversion erhält Fehlerbehebungen und Verbesserungen für die vollständige Funktionsqualität.
- Änderungen, die Erweiterungen oder die Code-Kompatibilität beeinträchtigen könnten, werden vermieden. Beispielsweise sollte Code, der für Version 2.2.0 geschrieben wurde, weiterhin in Version 2.2.7 funktionieren.
- In Ausnahmefällen können umfassende Änderungen oder zusätzliche Patches oder Hotfixes veröffentlicht werden, um Sicherheits- oder Compliance-Probleme zu beheben und Probleme mit der Qualität zu beheben. Auf Modulebene sind dies hauptsächlich Änderungen auf PATCH-Ebene, manchmal kleinere Änderungen.

### SICHERHEITS-Patch-Version

{{$include /help/_includes/security-patch-release-overview.md}}

## BETA Patch-Version

Vorabversionen von Adobe Commerce-Funktionen werden für alle Adobe Commerce-Kunden und Adobe-Partner öffentlich verfügbar gemacht. Dadurch wird mehr Zeit bis zur allgemeinen Verfügbarkeit zur Überprüfung des Codes und der betroffenen Komponenten bereitgestellt.

Beta-Versionen können Mängel enthalten und werden ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (über Adobe-Support-Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung der Beta-Versionen und/oder der zugehörigen Dokumentation oder Materialien zu verlassen. Dementsprechend erfolgt die Verwendung der Beta-Versionen vollständig auf eigene Gefahr des Kunden.

## Versionen mit Funktionen, Cloud-Infrastruktur und Erweiterbarkeit

Cloud-Infrastruktur- und Funktionsversionen enthalten neue Funktionen und Funktionsaktualisierungen, die als unabhängige Services bereitgestellt werden, die von Patch-Versionen getrennt sind. Beispiele sind Aktualisierungen unserer Cloud-Hosting-Services und -Infrastruktur, B2B-, SaaS-Produkte (Catalog Service, Data Connection, Product Recommendations und Live Search) und Erweiterbarkeitstechnologie (API Mesh, Integration Starter Kit und Eventing).

## Hotfix

Hotfixes sind Patches, die wirkungsvolle Sicherheits- oder Qualitätskorrekturen enthalten, z. B. Fehlerbehebungen für Zero-Day-Sicherheitslücken, die viele Händler betreffen. Adobe veröffentlicht Hotfixes für Adobe Commerce-Versionen, die weiterhin unterstützt werden und bei Bedarf von kritischen Sicherheits- oder Qualitätsproblemen betroffen sind. Hotfixes werden im Abschnitt [Bekannte Probleme](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) unserer Wissensdatenbank veröffentlicht. Diese Fehlerbehebungen sind in der nächsten geplanten Patch-Version enthalten.

>[!NOTE]
>
>Hotfixes können abwärtsinkompatible Änderungen enthalten.

## Einzelnes Patch

Einzelne Patches enthalten Korrekturen von geringer Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die unterstützten Nebenversionen von Adobe Commerce angewendet. Adobe veröffentlicht individuelle Patches nach Bedarf für Adobe Commerce gemäß unserer [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Einzelne Patches enthalten keine rückwärts inkompatiblen Änderungen.

## Isoliertes Pflaster

Enthält eine eigenständige Fehlerbehebung, die im neuesten Nur-Sicherheit-Patch enthalten ist, oder einen bevorstehenden Nur-Sicherheit-Patch, der separat veröffentlicht wird, um eine schnellere Implementierung zu ermöglichen.

## Benutzerdefinierter Patch

Wird von Nicht-Adobe-Mitarbeitern erstellt, um ein Problem zu beheben oder den Adobe Commerce-Code aus verschiedenen Gründen zu ändern. Benutzerdefinierte Patches werden über das [Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) bereitgestellt.
