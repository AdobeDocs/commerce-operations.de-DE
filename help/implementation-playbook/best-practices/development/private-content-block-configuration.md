---
title: Best Practices für private Inhaltsblöcke
description: Erfahren Sie mehr über Best Practices für die Konfiguration privater Inhaltsblöcke zur Optimierung der Leistung von Storefronts.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Best Practices für private Inhaltsblöcke

Wenn ein privater Inhaltsblock die `_isScopePrivate`-Variable enthält, kann der Block nicht zwischengespeichert werden. Da der private Block nicht zwischengespeichert wird, muss Adobe Commerce für jede Kundenanfrage dieselben Daten abrufen, was die Serverauslastung erhöht.

Anstatt die Variable `_isScopePrivate` für private Inhalte zu verwenden, erstellen Sie einen -Block und eine -Vorlage, um benutzerunabhängige Daten anzuzeigen. Diese Daten werden durch benutzerspezifische Daten durch die Adobe Commerce-Benutzeroberflächenkomponente ersetzt, die das Pre-Rendering von Daten effizienter verarbeitet. Anweisungen finden Sie unter [Privater Inhalt](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) im _[!DNL Commerce PHP Extensions Guide]_.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Potenzielle Auswirkungen auf die Leistung

Websites mit privaten Inhaltsblöcken, die die `_isScopePrivate` Variablen enthalten Trigger-AJAX-Anfragen , um für jede Kundenanfrage dieselben Daten abzurufen. Dies erhöht die Reaktionszeit und verwendet zusätzliche Ressourcen, die für geschäftskritischere Vorgänge in der Storefront verwendet werden können, z. B. für die Kundenregistrierung, Warenkorbaktualisierungen, die Übermittlung von Bestellungen und Zahlungsvorgänge.

## Weitere Informationen

- [Privater Inhalt](../../../performance/configuration.md#client-side-optimization-settings)
- [AJAX-Anfragen mit hohem Durchsatz führen zu schlechter Leistung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
