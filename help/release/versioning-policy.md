---
title: Release-Richtlinie
description: Erfahren Sie mehr über die verschiedenen Typen von Adobe Commerce-Versionen.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: fd2ebc358850e47975ce6a3b8df058774440bcf2
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# Adobe Commerce-Veröffentlichungsrichtlinie

Adobe Commerce verwendet [semantische Versionierung](https://semver.org/) auf der Ebene einzelner Module (z. B. `magento/framework 101.1.1`), aber nicht für die Marketing-Versionsnummer. Beispiel:

- **HAUPTVERSION**—2
- **NEBENVERSION**—2.4
- **PATCH-Version**—2.4.8
   - **SECURITY Patch-Version**—2.4.8-p1
      - Fehlerbehebung bei der Sicherheit
      - Sicherheitsverbesserung
- **ALPHA Patch-Version**—2.4.8-alpha1
- **BETA Patch-Version**—2.4.8-beta1
- **Version für Erweiterbarkeit, Infrastruktur und Services**
- **Hotfix**
- **Individuelles Patch**
- **Benutzerdefinierter Patch**

## NEBENVERSION

Die folgenden Richtlinien gelten für Nebenversionen:

- Umfassende Änderungen sind möglich. Code, der für Adobe Commerce 2.2.x geschrieben wurde, funktioniert möglicherweise nicht mehr mit Adobe Commerce 2.3.x. Beispielsweise können kleinere Versionen die Unterstützung für wichtige Systemanforderungen und -abhängigkeiten wie PHP einführen.
- Modulversionen können variieren. Beispielsweise werden einige Moduländerungen in einem neuen Patch eingeführt, während andere in einer Nebenversion eingeführt werden.
- Nebenversionen können neue Funktionen enthalten, die möglicherweise zusätzliche Arbeit von Ihnen oder Ihrem Lösungspartner während eines Upgrades erfordern, um die Kompatibilität sicherzustellen.
- Nebenversionen können Fehlerbehebungen für Sicherheits- und Qualitätsprobleme enthalten.

## PATCH-Version

Patch-Versionen konzentrieren sich in erster Linie auf die Bereitstellung von Sicherheits-, Leistungs-, Kompatibilitäts- und Qualitätskorrekturen mit hoher Priorität, damit Sie Ihre Sites auch weiterhin optimal nutzen können.

Die folgenden Richtlinien gelten für Patch-Versionen:

- Die neueste unterstützte Nebenversion erhält Fehlerbehebungen und Verbesserungen für die vollständige Funktionsqualität.
- Änderungen, die Erweiterungen oder die Code-Kompatibilität beeinträchtigen könnten, werden vermieden. Beispielsweise sollte Code, der für Version 2.2.0 geschrieben wurde, weiterhin in Version 2.2.7 funktionieren.
- In Ausnahmefällen können umfassende Änderungen oder zusätzliche Patches oder Hotfixes veröffentlicht werden, um Sicherheits- oder Compliance-Probleme zu beheben und Probleme mit der Qualität zu beheben. Auf Modulebene sind diese Änderungen hauptsächlich auf PATCH-Ebene, manchmal auch auf NEBENSÄCHLICHER Ebene.

### SICHERHEITS-Patch-Version

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## ALPHA Patch-Version

Pre-Beta-Versionen von Adobe Commerce-Funktionen werden für alle Adobe Commerce-Kunden und Adobe-Partner öffentlich verfügbar gemacht. Alpha-Versionen sind für frühzeitiges Feedback und die Bewertung von Funktionen vorgesehen, die sich noch in der Entwicklung befinden. Diese Versionen bieten die Möglichkeit für frühzeitige Tests und Integrationsplanung im Vorfeld von Beta- und allgemeinen Verfügbarkeitsversionen.

Alpha-Versionen können unvollständig sein und enthalten wahrscheinlich Fehler. Sie werden „WIE BESEHEN“ und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, Alpha-Versionen (über Adobe Support Services oder anderweitig) zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Kunden sollten sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Alpha-Versionen oder Begleitdokumenten oder -materialien verlassen. Die Verwendung von Alpha-Versionen erfolgt vollständig auf eigene Gefahr des Kunden.

## BETA Patch-Version

Vorabversionen der Adobe Commerce-Funktionen werden allen Adobe Commerce-Kunden und Adobe-Partnern öffentlich zugänglich gemacht. Dadurch wird mehr Zeit bis zur allgemeinen Verfügbarkeit zur Überprüfung des Codes und der betroffenen Komponenten bereitgestellt.

Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, Beta-Versionen (über Adobe Support Services oder anderweitig) zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Kunden sollten sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder Begleitdokumenten oder -materialien verlassen. Dementsprechend erfolgt die Verwendung der Beta-Versionen vollständig auf eigenes Risiko des Kunden.

## Hotfix

Hotfixes sind Patches, die wirkungsvolle Sicherheits- oder Qualitätskorrekturen enthalten, z. B. Fehlerbehebungen für Zero-Day-Sicherheitslücken, die viele Händler betreffen. Adobe veröffentlicht Hotfixes (nach Bedarf) für unterstützte Adobe Commerce-Versionen, wenn kritische Sicherheits- oder Qualitätsprobleme sie betreffen. Hotfixes werden im Abschnitt [Bekannte Probleme](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) der Wissensdatenbank veröffentlicht. Diese Fehlerbehebungen sind in der nächsten geplanten Patch-Version enthalten.

>[!NOTE]
>
>Hotfixes können abwärtsinkompatible Änderungen enthalten.

## Einzelnes Patch

Einzelne Patches enthalten Korrekturen von geringer Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die unterstützten Nebenversionen von Adobe Commerce angewendet. Adobe veröffentlicht individuelle Patches nach Bedarf für Adobe Commerce gemäß der [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Einzelne Patches enthalten keine rückwärts inkompatiblen Änderungen.

## Isolierte Sicherheitskorrekturen

Isolierte Patches sind nicht kumulative Sicherheitskorrekturen, die unabhängig von einem vollständigen Sicherheits-Patch veröffentlicht werden, um eine schnellere Implementierung zu ermöglichen. Jede einzelne Sicherheitskorrektur behandelt ein bestimmtes Sicherheitsproblem und ist entweder im neuesten oder im kommenden vollständigen Sicherheitspatch enthalten. Details zum Problem finden Sie im entsprechenden Sicherheitsbulletin, das auf einen Knowledgebase-Artikel (KB) verweist, der die Fehlerbehebungsdetails, die Anwendung der Fehlerbehebung und zusätzliche Informationen enthält.

Im [Sicherheitscenter](https://helpx.adobe.com/security/products/magento.html) finden Sie die neuesten Sicherheitsupdates für Adobe Commerce.

## Benutzerdefinierter Patch

von Nicht-Adobe-Mitarbeitern erstellt wurden, um ein Problem zu beheben oder den Adobe Commerce-Code aus verschiedenen Gründen zu ändern. Benutzerdefinierte Patches werden über das [Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) bereitgestellt.

<!-- Last updated from includes: 2025-05-28 16:37:31 -->
