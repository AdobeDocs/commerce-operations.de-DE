---
title: Audit der Frontend-Leistung
description: Identifizieren und beheben Sie Probleme, die sich negativ auf die Site-Leistung auswirken, indem Sie Web-Leistungs-Tools verwenden, um Vorgänge der Adobe Commerce-Storefront zu überprüfen.
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# Best Practices für die Frontend-Leistung

Verwenden Sie Web-Leistungs-Tools, um die Frontend-Leistung Ihrer Adobe Commerce-Stores zu überprüfen.
Diese Tools verwenden verschiedene Metriken, um leistungsstarke Einblicke und Empfehlungen zur Verbesserung der Leistung Ihres Online-Shops bereitzustellen.

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Frontend-Leistung überprüfen

So überprüfen Sie die Frontend-Leistung Ihres Website-Stores:

1. Audit der Frontend-Leistung mithilfe von Web-Performance-Tools wie:

   - **[Google Lighthouse](https://web.dev/measure/)**: Lighthouse verfügt über Audits für Leistung, Barrierefreiheit, Progressive Web Apps, SEO und mehr. Weitere Informationen zu den verschiedenen Methoden zum Ausführen von Lighthouse finden Sie unter [Lighthouse-Übersicht](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)** - PageSpeed Insights liefert schnell einen detaillierten Bericht über die Ursachen der langsamen Webseitenleistung sowie Empfehlungen, wie diese behoben werden können.

1. Überprüfen Sie die Auditberichte und implementieren Sie die bereitgestellten Empfehlungen zur Verbesserung der Store-Leistung.

## Weitere Informationen

- [Indexverwaltung für Admin-Benutzer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexverwaltung über die CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Übersicht über die Indizierung für Entwickler](https://developer.adobe.com/commerce/php/development/components/indexing/)
