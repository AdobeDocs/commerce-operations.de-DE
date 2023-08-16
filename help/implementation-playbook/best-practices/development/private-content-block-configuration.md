---
title: Best Practices für private Inhaltsbausteine
description: Erfahren Sie mehr über Best Practices zum Konfigurieren privater Inhaltsbausteine zur Optimierung der Storefront-Leistung.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Best Practices für private Inhaltsbausteine

Wenn ein privater Inhaltsbaustein die `_isScopePrivate` nicht zwischenspeicherbar ist. Da der private Block nicht zwischengespeichert wird, muss Adobe Commerce für jede Kundenanfrage dieselben Daten abrufen, was die Serverlast erhöht.

Statt die `_isScopePrivate` für privaten Inhalt erstellen Sie einen Block und eine Vorlage, um benutzeragnostische Daten anzuzeigen. Diese Daten werden durch benutzerspezifische Daten durch die Adobe Commerce-UI-Komponente ersetzt, die die Vorab-Rendering-Daten effizienter verarbeitet. Anweisungen finden Sie unter [Private Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) im _[!DNL Commerce PHP Extensions Guide]_.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Potenzielle Auswirkung auf die Leistung

Sites mit privaten Inhaltsbausteinen, die `_isScopePrivate` Variablen Trigger AJAX Anforderungen zum Abrufen der gleichen Daten für jede Kundenanfrage. Dies erhöht die Reaktionszeit und verwendet zusätzliche Ressourcen, die für geschäftskritische Storefront-Vorgänge wie Kundenregistrierung, Warenkorbaktualisierungen, Bestellübermittlung und Zahlungsvorgänge verwendet werden können.

## Zusätzliche Informationen

- [Private Inhalte](../../../performance/configuration.md#client-side-optimization-settings)
- [Hohe Durchsatzraten AJAX Anforderungen führen zu schlechter Leistung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
