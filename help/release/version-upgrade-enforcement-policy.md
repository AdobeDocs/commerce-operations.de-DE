---
title: Richtlinie zur Durchsetzung des Cloud-Versions-Upgrades
description: Erfahren Sie mehr über die Durchsetzung von Versionsaktualisierungen für Adobe Commerce in Cloud - warum Adobe Upgrades, Erzwingungstermine, Stilllegungen und erforderliche Maßnahmen erzwingt. Übergangsbestimmungen und Migrationspfade finden Sie in der Lebenszyklusrichtlinie .
nudge: false
source-git-commit: 797f067de451c8b1b4d735e82de66a3fd9b56563
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Durchsetzungsrichtlinie für die Versionsaktualisierung für Adobe Commerce in Cloud

Wenn die reguläre Unterstützung und die erweiterte Unterstützung für eine Adobe Commerce-Version endet, behält sich Adobe das Recht vor, Adobe Commerce in Cloud-Umgebungen, in denen diese nicht unterstützte Version noch ausgeführt wird, außer Betrieb zu setzen. Die Durchsetzung des Versions-Upgrades gilt nur für Adobe Commerce in Cloud-Umgebungen. Kunden vor Ort verwalten ihre eigene Infrastruktur.

Sie müssen eine unterstützte Adobe Commerce-Version verwenden oder vor dem Veröffentlichungsdatum [Ende der erweiterten Unterstützung](lifecycle-policy.md#end-of-support-dates) für Ihre Release-Zeile zu [!DNL Adobe Commerce as a Cloud Service] migrieren.

In den folgenden Abschnitten wird erläutert, warum Adobe Upgrades erzwingt, wie Erzwingungstermine berechnet werden und was am Erzwingungsdatum geschieht. Versionsspezifische Erzwingungstermine finden Sie in der Tabelle [Ende der Support-](lifecycle-policy.md#end-of-support-dates)&quot; in der Lebenszyklusrichtlinie.

>[!NOTE]
>
>Dieses Thema behandelt nur die Durchsetzung von Cloud-Upgrades. Definitionen der Support-Stufe finden Sie unter [Ende der Support](lifecycle-policy.md#end-of-support-dates)Daten, Tabelle [Übergangsbestimmungen nur für die Sicherheit](lifecycle-policy.md#security-only-transitional-period), [Abhängigkeiten von Software von Drittanbietern](lifecycle-policy.md#platform-dependencies), [Ende der Lebensdauer von PHP und PCI-](lifecycle-policy.md#php-end-of-life-and-pci-compliance) und [Upgrade- und Migrationsoptionen](lifecycle-policy.md#upgrade-and-migration-options) finden Sie in der [Lebenszyklusrichtlinie](lifecycle-policy.md). Zusätzlich zum Upgrade auf eine unterstützte Adobe Commerce-Version verlangt Adobe auch, dass Sie die Abhängigkeit von Software von Drittanbietern von aktiv unterstützten Versionen beibehalten.

## Warum Adobe diese Richtlinie einführt

Adobe ist für die Sicherheit und Compliance der gehosteten Plattforminfrastruktur verantwortlich, auf der Adobe Commerce on Cloud-Kunden ausgeführt werden. Dazu gehört, alle zugrunde liegenden Softwareabhängigkeiten auf dem neuesten Stand zu halten, Sicherheits-Patches anzuwenden und Compliance-Standards wie PCI zu erfüllen, auf die sich Kunden verlassen.

Wenn die Sicherheitsunterstützung für die zugrunde liegenden Softwareabhängigkeiten offiziell von Anbietern beendet wird, kann Adobe nicht mehr die erforderliche Sicherheitsabdeckung und Plattformunterstützung bereitstellen. Wenn Geschäfte weiterhin auf nicht unterstützter Infrastruktur betrieben werden, sind Kunden, ihre Kunden und Adobe einem inakzeptablen Risiko ausgesetzt. Adobe führt daher eine formale Richtlinie zur Durchsetzung des Versions-Upgrades ein, die definiert, wann Adobe Commerce in Cloud-Umgebungen, in denen nicht unterstützte Commerce-Versionen ausgeführt werden, eingestellt wird.

## Berechnen der Erzwingungstermine eines Upgrades

Für jede Adobe Commerce-Release-Zeile wird das Erzwingungsdatum des Upgrades wie folgt berechnet:

**Upgrade-Erzwingungsdatum** = Allgemeine Verfügbarkeit + 3 Jahre regelmäßiger Support + bis zu 1 Jahr erweiterter Support

Die erweiterte Unterstützung wird für jede Release-Zeile kurz vor dem Ende der regulären Unterstützung angekündigt.

## Was passiert am Erzwingungsdatum des Versions-Upgrades?

Am veröffentlichten Datum der Durchsetzung des Upgrades stoppt Adobe die Wartung aller Adobe Commerce in Cloud-Umgebungen, in denen die betroffene Release-Version noch ausgeführt wird, und behält sich das Recht vor, sie stillzulegen. Sie erhalten vorab Benachrichtigungen zu wichtigen Meilensteinen, bevor das Versions-Upgrade durchgesetzt wird. Adobe stellt vor der Deaktivierung der Umgebung ein Datenexportfenster zur Verfügung, damit Sie Ihre Daten abrufen können.

Das erste Durchsetzungsdatum im Rahmen dieser Richtlinie ist **1. Juni 2027** für Veröffentlichungszeilen, die vor diesem Datum das Ende der erweiterten Unterstützung erreichen. In der [Ende der Support-](lifecycle-policy.md#end-of-support-dates)&quot; finden Sie versionsspezifische Erzwingungsdaten.
