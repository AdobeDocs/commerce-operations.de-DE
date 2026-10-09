---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.24 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin
exl-id: 7f88a28b-f166-4c5b-8d69-239c57cc4001
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%
---
# Übersicht über [!DNL Quality Patches Tool] (QPT) v1.1.24

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.24 verfügbaren Patches behoben wurden.

QPT v1.1.24 enthält die folgenden Patches:

1. **ACSD-45168**: Es wird das Problem behoben, dass SEO-freundliche URLs nicht für Produkte generiert werden, bei denen *url_key*-Attribute auf Store-Ansichtsebene überschrieben wurden.
1. **ACSD-46617**: Es wird ein Problem behoben, bei dem die Schaltfläche &quot;**[!UICONTROL Continue to Checkout]**&quot; ausgegraut ist, selbst wenn die Zwischensumme größer als der konfigurierte *Mindestbestellbetrag* ist.
1. **ACSD-46770**: Es wurde ein Problem behoben, bei dem E-Mails zu Admin-Bestellungen gesendet wurden, selbst wenn *E-Mail-Bestellbestätigung* deaktiviert war.
1. **ACSD-46865**: Es wird das Problem behoben, dass das [!UICONTROL Shipment and Credit Memo] nicht ausgefüllt wird, wenn die asynchrone Indizierung aktiviert ist.
1. **ACSD-47004**: Es wird das Problem behoben, dass keine MwSt. auf eine Rechnungsadresse ohne MwSt.-Kennung angewendet wird.
1. **ACSD-47079**: Es wird das Problem behoben, dass der Lagerstatus von zusammengesetzten Produkten (Bundle, Gruppiert und Konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus von Unterprodukten über REST API POST /rest/V1/inventory/source-items ändert.
1. **ACSD-47137**: Verbessert die Ladegeschwindigkeit der Bildergalerie, wenn der Pub/Media-Ordner sehr groß ist.
1. **ACSD-47336**: Fehlerbehebungen *Etwas ist schiefgelaufen.* Fehler beim Verwerfen von Benachrichtigungen in Commerce Admin.
1. **ACSD-47559**: Es wird ein Problem behoben, bei dem der Bereich E-Mail-Vorlagenvorschau nicht vollständig sichtbar ist.
1. **ACSD-47803**: Es wird das Problem behoben, bei dem nicht vorrätige konfigurierbare Produktmuster als verfügbar angezeigt werden.
1. **ACSD-47920**: Es wurde ein Problem behoben, bei dem Bestellungen über die REST-API als Gastbenutzer platziert werden können, selbst wenn die Option *Gast-Checkout zulassen* deaktiviert ist.
1. **ACSD-47955**: Es wurde ein Problem behoben, durch das in GraphQL der Warenkorbabschlag nicht korrekt angezeigt wurde.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
