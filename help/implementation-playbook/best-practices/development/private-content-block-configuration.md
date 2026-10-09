---
title: Best Practices für private Inhaltsblöcke
description: Erfahren Sie mehr über Best Practices für die Konfiguration privater Inhaltsblöcke zur Optimierung der Leistung von Storefronts.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Best Practices für private Inhaltsblöcke

Wenn ein privater Inhaltsblock die `_isScopePrivate`-Variable enthält, kann der Block nicht zwischengespeichert werden. Da der private Block nicht zwischengespeichert wird, muss Adobe Commerce für jede Kundenanfrage dieselben Daten abrufen, was die Serverauslastung erhöht.

Anstatt die Variable `_isScopePrivate` für private Inhalte zu verwenden, erstellen Sie einen -Block und eine -Vorlage, um benutzerunabhängige Daten anzuzeigen. Diese Daten werden durch benutzerspezifische Daten durch die Adobe Commerce-Benutzeroberflächenkomponente ersetzt, die das Pre-Rendering von Daten effizienter verarbeitet. Anweisungen finden Sie unter [Privater Inhalt](https://developer.adobe.com/commerce/php/development/cache/page/private-content) im _[!DNL Commerce PHP Extensions Guide]_.

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Potenzielle Auswirkungen auf die Leistung

Websites mit privaten Inhaltsblöcken, die die `_isScopePrivate` Variablen enthalten, die Trigger AJAX anfordert, für jede Kundenanfrage dieselben Daten abzurufen. Dies erhöht die Reaktionszeit und verwendet zusätzliche Ressourcen, die für geschäftskritischere Vorgänge in der Storefront verwendet werden können, z. B. für die Kundenregistrierung, Warenkorbaktualisierungen, die Übermittlung von Bestellungen und Zahlungsvorgänge.

## Weitere Informationen

- [Privater Inhalt](../../../performance/configuration.md#client-side-optimization-settings)
- [Zwischenspeicherbare und private Blöcke](https://developer.adobe.com/commerce/php/development/cache/page/private-content#cacheable-and-private-blocks) im _[!DNL Commerce PHP Extensions Guide]_
