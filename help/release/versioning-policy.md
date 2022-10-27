---
title: Versionsrichtlinie
description: Erfahren Sie mehr über die verschiedenen Arten von Adobe Commerce-Versionen, einschließlich kleineren Versionen, Patch, Sicherheits-Patch, Funktion, Hotfix, individuellem Patch und benutzerdefiniertem Patch.
source-git-commit: f9bbfb86d2197ee7252602edba455ebcae5a2b18
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Adobe Commerce-Versionsrichtlinie

Verwendung von Adobe Commerce und Magento Open Source [Semantische Versionierung](https://semver.org/) auf der einzelnen Modulebene (z. B. `magento/framework 101.1.1`), jedoch nicht für die Marketing-Versionsnummer. Beispiel:

- **MAJOR-Version**—2
- **KLEINE Version**—2.4
- **PATCH-Version**—2.4.1
   - **Sicherheits-Patch-Version**—2.4.1-p1
      - Sicherheitsfehlerbehebung
      - Sicherheitsverbesserung
- **Feature Release**
- **Hotfix**
- **Individuelles Pflaster**
- **Benutzerdefinierter Patch**

## KLEINE Version

Die folgenden Richtlinien gelten für Nebenversionen:

- Wesentliche Änderungen sind möglich. Für Adobe Commerce 2.2.x geschriebener Code funktioniert möglicherweise nicht mehr mit Adobe Commerce 2.3.x. Beispielsweise können Nebenversionen Unterstützung für wichtige Systemanforderungen und Abhängigkeiten wie PHP einführen.
- Modulversionen können variieren. Beispielsweise werden einige Moduländerungen in einem neuen Patch eingeführt, während andere in einer kleineren Version eingeführt werden.
- Nebenversionen können neue Funktionen enthalten, die möglicherweise zusätzliche Arbeit von Ihnen oder Ihrem Lösungspartner während der Aktualisierung erfordern, um die Kompatibilität sicherzustellen.
- Nebenversionen können Fehlerbehebungen für Sicherheits- und Qualitätsprobleme enthalten.

## PATCH-Version

Patch-Versionen konzentrieren sich in erster Linie auf die Bereitstellung von Sicherheits-, Leistungs-, Compliance- und hochwertigen Fehlerbehebungen, die Ihnen helfen, die Leistung Ihrer Sites zu steigern.

Die folgenden Richtlinien gelten für Patch-Versionen:

- Die neueste unterstützte Nebenversion erhält vollständige Fehlerbehebungen und Verbesserungen in funktionaler Qualität.
- Änderungen, die Erweiterungen oder Codekompatibilität beeinträchtigen könnten, werden vermieden. Beispielsweise sollte Code, der für Version 2.2.0 geschrieben wurde, weiterhin für Version 2.2.7 verwendet werden.
- In Ausnahmefällen können brechende Änderungen oder zusätzliche Patches oder Hotfixes veröffentlicht werden, um Sicherheits- oder Compliance-Probleme und Qualitätsprobleme mit hoher Auswirkung zu beheben. Auf Modulebene handelt es sich dabei hauptsächlich um Änderungen auf PATCH-Ebene. manchmal Änderungen auf MINODER-Ebene.

## Sicherheits-Patch-Version

**Fehlerbehebung bei der Sicherheit**: Eine Änderung des Software-Codes, die ein festgestelltes Sicherheitsproblem behebt und erwartete Ergebnisse in einem betroffenen Produktbereich liefert. Diese Korrekturen sind im Allgemeinen abwärtskompatibel.

**Verbesserung der Sicherheit**: Eine Software-Verbesserung oder Konfigurationsänderung, um die Sicherheit innerhalb der Anwendung proaktiv zu verbessern. Diese Sicherheitsverbesserungen helfen bei der Behebung von Sicherheitsrisiken, die sich auf die Sicherheitsstellung der Adobe Commerce-Anwendung auswirken, aber abwärtskompatibel sein können.

Mit Sicherheits-Patch-Versionen können Sie Ihre Site sicherer halten, ohne zusätzliche Qualitätsverbesserungen und -verbesserungen anzuwenden, die in einer vollständigen vierteljährlichen Patch-Version enthalten sind. Sicherheits-Patch-Versionen werden mit &quot;-pN&quot;angehängt, wobei N die inkrementelle Patch-Version ist, die mit 1 beginnt (z. B. 2.3.5-p1). Sicherheits-Patch-Versionen können auch Hotfixes enthalten, die erforderlich sind, um wichtige Probleme zu beheben, die sich auf die Adobe Commerce-Anwendung auswirken.

Jede Sicherheits-Patch-Version basiert auf der vorherigen vollständigen Patch-Version. Es enthält Qualitäts- und Sicherheitskorrekturen aus früheren Patch-Versionen und Sicherheitskorrekturen, die zwischen der vorherigen vollständigen Patch-Version und der Sicherheits-Patch-Version erstellt wurden.

Mit der Ankündigung unserer [Neue Veröffentlichungsstrategie und aktualisierte Lebenszyklusrichtlinie](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (16.09.2021), werden unsere Sicherheits-Patch-Versionen danach unterschieden, ob sie auf die neueste unterstützte Nebenversion oder einen Teil einer noch unterstützten früheren Nebenversion anwendbar sind:

- **Sicherheits-Patch-Versionen für die neueste unterstützte Nebenversion**:

   - Die Sicherheits-Patch-Version für die neueste unterstützte Nebenversion (derzeit Adobe Commerce 2.4) umfasst:

      - Sicherheitsfehlerbehebungen, die seit der vorherigen vollständigen Patch-Version erstellt wurden.

      - Diese Sicherheits-Patch-Versionen können auch Hotfixes enthalten, die erforderlich sind, um wichtige Probleme zu beheben, die sich auf die Adobe Commerce-Anwendung auswirken können.
   - Die Sicherheits-Patch-Version für die neueste unterstützte Nebenversion (derzeit Adobe Commerce 2.4) umfasst in der Regel keine Sicherheitsverbesserungen. Stattdessen sind diese in der vollständigen umfassenden Patch-Version für die neueste unterstützte Nebenversion enthalten.


- **Sicherheits-Patch-Versionen für unterstützte frühere Nebenversionen**:

   - Die Sicherheits-Patch-Version für eine frühere Nebenversion, die weiterhin unterstützt wird (derzeit Adobe Commerce 2.3), umfasst:

      - Sicherheitsfehlerbehebungen, die seit der vorherigen Patch- oder Sicherheits-Patch-Version erstellt wurden, sowie neue Sicherheitsverbesserungen.

      - Diese Sicherheits-Patch-Versionen können auch Hotfixes enthalten, die erforderlich sind, um wichtige Probleme zu beheben, die sich auf die Adobe Commerce-Anwendung auswirken.

      |  | Sicherheitsfehler | Verbesserung der Sicherheit |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Sicherheits-Patch-Versionen für die neueste unterstützte Nebenversion (derzeit 2.4) | X |  |
      | Sicherheits-Patch-Versionen für vorherige, unterstützte Nebenversionen (derzeit 2.3) | X | X |


Allgemeine Informationen zu Sicherheitsfreigaben finden Sie unter [Einführung der neuen reinen Sicherheits-Patch-Version](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Anweisungen zum Herunterladen und Anwenden von Sicherheits-Patches finden Sie unter [Schnellstart-Installation](../installation/composer.md).

## Feature Release

Feature Releases enthalten neue Funktionen und Funktionsaktualisierungen, die separat von den Patch-Versionen als unabhängige Dienste bereitgestellt werden. Beispiele sind Dienste wie Product Recommendations und Live Search, unabhängige Module wie PWA Studio und Inventory management (MSI) sowie Aktualisierungen unserer Cloud-Services und -Infrastruktur.

## Hotfix

Hotfixes sind Patches, die umfassende Sicherheits- oder Qualitätsreparaturen enthalten, z. B. Fehlerbehebungen für null Tage-Schwachstellen, die viele Händler betreffen. Adobe gibt bei Bedarf Hotfixes für Adobe Commerce-Versionen heraus, die weiterhin unterstützt werden und von kritischen Sicherheits- oder Qualitätsproblemen betroffen sind. Hotfixes werden im [Abschnitt &quot;Bekannte Probleme&quot;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) unserer Wissensdatenbank. Diese Fehlerbehebungen sind in der nächsten geplanten Patch-Version enthalten.

>[!NOTE]
>
>Hotfixes können abwärtskompatible Änderungen enthalten.

## Individuelles Pflaster

Einzelne Patches enthalten Korrekturen mit geringer Auswirkung auf die Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die unterstützten Nebenversionen von Adobe Commerce angewendet. Adobe veröffentlicht individuelle Patches nach Bedarf für Adobe Commerce gemäß unserer [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Einzelne Patches enthalten keine abwärtskompatiblen Änderungen.

## Benutzerdefinierter Patch

Wird von Mitarbeitern ohne Adobe erstellt, um ein Problem zu beheben oder den Adobe Commerce-Code aus verschiedenen Gründen zu ändern. Benutzerdefinierte Patches werden über die [Werkzeug für Qualitätsmuster](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Verwandte Themen

- [Planung und Budget für Commerce-Aktualisierungszyklen](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Versionierung](https://developer.adobe.com/commerce/php/development/versioning/)
- [Bevorstehende Versionen](schedule.md)
- [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
