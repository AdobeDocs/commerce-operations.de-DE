---
title: Best Practices für private Inhaltsbausteine
description: Erfahren Sie mehr über Best Practices zum Konfigurieren privater Inhaltsbausteine zur Optimierung der Storefront-Leistung.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Best Practices für private Inhaltsbausteine

Wenn ein privater Inhaltsbaustein die Variable `_isScopePrivate` nicht zwischenspeicherbar ist. Da der private Block nicht zwischengespeichert wird, muss Adobe Commerce für jede Kundenanfrage dieselben Daten abrufen, was die Serverlast erhöht.

Statt die `_isScopePrivate` für privaten Inhalt erstellen Sie einen Block und eine Vorlage, um benutzeragnostische Daten anzuzeigen. Diese Daten werden von der Adobe Commerce durch benutzerspezifische Daten ersetzt [UI-Komponente](https://glossary.magento.com/ui-component/), die die Vorab-Rendering-Daten effizienter verarbeitet. Anweisungen finden Sie unter [Private Inhalte](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) im _[!DNL Commerce PHP Extensions Guide]_.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Potenzielle Auswirkung auf die Leistung

Sites mit privaten Inhaltsbausteinen, die die `_isScopePrivate` Variablen Trigger AJAX Anforderungen zum Abrufen der gleichen Daten für jede Kundenanfrage. Dies erhöht die Reaktionszeit und verwendet zusätzliche Ressourcen, die für geschäftskritische Storefront-Vorgänge wie Kundenregistrierung, Warenkorbaktualisierungen, Bestellübermittlung und Zahlungsvorgänge verwendet werden können.

## Zusätzliche Informationen

- [Private Inhalte](../../../performance/configuration.md#client-side-optimization-settings)
- [Hohe Durchsatzraten AJAX Anforderungen führen zu schlechter Leistung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)

