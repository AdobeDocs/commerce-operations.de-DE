---
title: "Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.50"
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.50 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.50

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.50 verfügbaren Patches behoben wurden.

QPT v1.1.50 umfasst die folgenden Patches:

1. **ACSD-59280**: Behebung des Problems, bei dem der Fehler *Aufruf der nicht definierten Methode ReflectionUnionType::getName()* auftritt, wenn 2.4.4-pX-Versionen installiert werden.
1. **ACSD-45049**: Behebung des Problems, bei dem die Kundenattributeinstellung *[!UICONTROL Is required]* gemäß dem Website-Umfang in Admin nicht ordnungsgemäß funktioniert.
1. **ACSD-46938**: Behebt das Problem mit der Leistung der DB-Trigger-Neuerstellung während `setup:upgrade`.
1. **ACSD-48210**: Behebung des Problems, bei dem beim Aktualisieren des *[!UICONTROL website scope]* -Attributs in einer bestimmten Store-Ansicht die Attributwerte im globalen Gültigkeitsbereich außer Kraft gesetzt werden.
1. **ACSD-54887**: Behebung des Problems, bei dem der Warenkorb für Kunden gelöscht wird, nachdem die Kundensitzung abgelaufen ist und *[!UICONTROL Persistent Shopping Cart]* aktiviert ist.
1. **ACSD-58141**: Behebung des Problems, bei dem `PHPSESSID` bei POST-Anforderungen im Storefront-Bereich für einen angemeldeten  neu generiert wurde, wenn [!UICONTROL L2 Redis cache] aktiviert ist und der Kunde vom Administrator aktualisiert wird.
1. **ACSD-58352**: Behebung des Problems, bei dem Rückgabeattributbeschriftungen für die standardmäßige Store-Ansicht über die GraphQL-API zurückgegeben werden, wenn eine nicht standardmäßige Store-Ansicht im Anfrageheader angegeben ist.
1. **ACSD-58442**: Behebung des Problems, bei dem Geräte mit einer Breite von *768 px* als Mobilgeräte behandelt werden, wodurch das Menü und die Kopfzeile in einer Mobile-Ansicht statt auf dem Desktop geladen werden.
1. **ACSD-58790**: Behebt die Funktion *Pinch-to-Zoom* für die Produktdetailseiten-Bilder in der Mobile-Ansicht auf [!DNL Chrome].
1. **ACSD-59036**: Behebt eine Ausnahme, die beim Laden von Produktpreisen mit niedrigeren und oberen Grenzen von *$0* auftritt.
1. **ACSD-59229**: Behebung des Problems, bei dem gruppenbezogene Kundeninformationen aufgrund des alten Werts von [!UICONTROL X-Magento-Vary] in der Anfrage im falschen Segment gespeichert wurden.
1. **ACSD-59378**: Behebung des Problems, bei dem URL-Neuschreibungen auf Store-Ebene beim Import falsch aktualisiert werden.
1. **ACSD-59514**: Behebung des Problems, bei dem Formulare im Admin-Bereich mit [!DNL Page Builder] die *[!DNL Page Builder]5 Sekunden lang gerendert wurden, ohne Sperren freizugeben.* -Fehler in der Browser-Konsole nach dem Senden des Formulars und Änderungen können nicht gespeichert werden.
1. **ACSD-60303**: Behebung des Problems, bei dem eine Bestellung von Admin nicht platziert werden kann, wenn die HTML-Minimierung aktiviert ist.
1. **ACSD-60441**: Behebung des Problems beim Aktualisieren von Kunden über den `V1/customers REST API` -Endpunkt bei Verwendung des vom Backend generierten Integrationszugriffstokens.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
