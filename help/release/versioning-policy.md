---
title: Versionsrichtlinie
description: Erfahren Sie mehr über die verschiedenen Arten von Adobe Commerce-Versionen, einschließlich kleineren Versionen, Patch, Sicherheits-Patch, Funktion, Hotfix, individuellem Patch und benutzerdefiniertem Patch.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Adobe Commerce-Versionsrichtlinie

Adobe Commerce verwendet [Semantische Versionierung](https://semver.org/) auf der einzelnen Modulebene (z. B. `magento/framework 101.1.1`), jedoch nicht für die Marketing-Versionsnummer. Beispiel:

- **MAJOR-Version**—2
- **Geringfügige Version**—2.4
- **PATCH-Version**—2.4.5
   - **Sicherheits-Patch-Version**—2.4.5-p1
      - Sicherheitsfehlerbehebung
      - Sicherheitsverbesserung
- **BETA Patch-Version**—2.4.7-beta2
- **Erweiterbarkeit, Infrastruktur und Freigabe von Diensten**
- **Hotfix**
- **Individuelles Pflaster**
- **Benutzerdefinierter Patch**

## Geringfügige Version

Die folgenden Richtlinien gelten für Nebenversionen:

- Umfassende Änderungen sind möglich. Für Adobe Commerce 2.2.x geschriebener Code funktioniert möglicherweise nicht mehr mit Adobe Commerce 2.3.x. Beispielsweise können Nebenversionen Unterstützung für wichtige Systemanforderungen und Abhängigkeiten wie PHP einführen.
- Modulversionen können variieren. Beispielsweise werden einige Moduländerungen in einem neuen Patch eingeführt, während andere in einer kleineren Version eingeführt werden.
- Nebenversionen können neue Funktionen enthalten, die möglicherweise zusätzliche Arbeit von Ihnen oder Ihrem Lösungspartner während der Aktualisierung erfordern, um die Kompatibilität sicherzustellen.
- Nebenversionen können Fehlerbehebungen für Sicherheits- und Qualitätsprobleme enthalten.

## PATCH-Version

Patch-Versionen konzentrieren sich in erster Linie auf die Bereitstellung von Sicherheits-, Leistungs-, Compliance- und hochwertigen Fehlerbehebungen, die Ihnen helfen, die Leistung Ihrer Sites zu steigern.

Die folgenden Richtlinien gelten für Patch-Versionen:

- Die neueste unterstützte Nebenversion erhält vollständige Fehlerbehebungen und Verbesserungen in funktionaler Qualität.
- Änderungen, die Erweiterungen oder Codekompatibilität beeinträchtigen könnten, werden vermieden. Beispielsweise sollte Code, der für Version 2.2.0 geschrieben wurde, weiterhin für Version 2.2.7 verwendet werden.
- In Ausnahmefällen können brechende Änderungen oder zusätzliche Patches oder Hotfixes veröffentlicht werden, um Sicherheits- oder Compliance-Probleme und Qualitätsprobleme mit hoher Auswirkung zu beheben. Auf Modulebene handelt es sich dabei hauptsächlich um Änderungen auf PATCH-Ebene, manchmal aber auch um Änderungen auf MINOR-Ebene.

### Sicherheits-Patch-Version

{{$include /help/_includes/security-patch-release-overview.md}}

## BETA Patch-Version

Vorabversionen von Adobe Commerce-Funktionen werden allen Adobe Commerce-Kunden und Adobe-Partnern öffentlich zugänglich gemacht. Es ermöglicht Ihnen mehr Zeit, bevor die allgemeine Verfügbarkeit den Code und die betroffenen Komponenten überprüft.

Beta-Versionen können Mängel enthalten und werden ohne Gewährleistung jeglicher Art &quot;AS IS&quot; bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die korrekte Funktionsweise oder Leistung der Beta-Versionen und/oder der zugehörigen Dokumentation oder Materialien zu verlassen. Dementsprechend erfolgt die Nutzung der Beta-Versionen auf eigenes Risiko des Kunden.

## Erweiterbarkeit, Infrastruktur und Freigabe von Diensten

Funktionsversionen, die neue Funktionen und Funktionsaktualisierungen enthalten, die separat von Patch-Versionen als unabhängige Dienste bereitgestellt werden. Beispiele sind Erweiterbarkeitstechnologien wie API Mesh und Eventing, SaaS-Produkte wie Product Recommendations und Live Search, unabhängige Module wie B2B und PWA Studio sowie Aktualisierungen unserer Cloud-Hosting-Dienste und -Infrastruktur.

## Hotfix

Hotfixes sind Patches, die umfassende Sicherheits- oder Qualitätsreparaturen enthalten, z. B. Fehlerbehebungen für null Tage-Schwachstellen, die viele Händler betreffen. Adobe gibt Hotfixes für Adobe Commerce-Versionen frei, die weiterhin unterstützt werden und von kritischen Sicherheits- oder Qualitätsproblemen betroffen sind. Hotfixes werden im [Abschnitt &quot;Bekannte Probleme&quot;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) unserer Wissensdatenbank. Diese Fehlerbehebungen sind in der nächsten geplanten Patch-Version enthalten.

>[!NOTE]
>
>Hotfixes können abwärtskompatible Änderungen enthalten.

## Individuelles Pflaster

Einzelne Patches enthalten Korrekturen mit geringer Auswirkung auf die Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die unterstützten Nebenversionen von Adobe Commerce angewendet. Adobe veröffentlicht individuelle Patches nach Bedarf für Adobe Commerce gemäß unserer [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Einzelne Patches enthalten keine abwärtskompatiblen Änderungen.

## Benutzerdefinierter Patch

Wird von Nicht-Adobe-Mitarbeitern erstellt, um ein Problem zu beheben oder den Adobe Commerce-Code aus verschiedenen Gründen zu ändern. Benutzerdefinierte Patches werden über die [Werkzeug für Qualitätsmuster](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Verwandte Themen

- [Versionierung](https://developer.adobe.com/commerce/php/development/versioning/)
- [Bevorstehende Versionen](schedule.md)
- [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
