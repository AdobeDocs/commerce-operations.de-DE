---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.50  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e136531-6bd4-4294-9a5a-66d19eb136db
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.50

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.50 verfügbaren Patches behoben wurden.

QPT v1.1.50 enthält die folgenden Patches:

1. **ACSD-59280**: Es wurde das Problem behoben, bei dem der Fehler *Aufruf an undefinierte Methode ReflectionUnionType::getName()* bei der Installation von 2.4.4-pX-Versionen auftritt.
1. **ACSD-45049**: Es wurde ein Problem behoben, bei dem die Einstellung des Kundenattributs *[!UICONTROL Is required]* gemäß Website-Umfang in Admin nicht ordnungsgemäß funktioniert.
1. **ACSD-46938**: Behebt das Problem mit der Performance der DB-Trigger-Neuerstellung während der `setup:upgrade`.
1. **ACSD-48210**: Es wird ein Problem behoben, bei dem durch die Aktualisierung des *[!UICONTROL website scope]*-Attributs in einer bestimmten Store-Ansicht die Attributwerte im globalen Umfang überschrieben werden.
1. **ACSD-54887**: Es wurde ein Problem behoben, bei dem der Warenkorb des Kunden geleert wurde, nachdem die Kundensitzung mit aktiviertem *[!UICONTROL Persistent Shopping Cart]* abgelaufen war.
1. **ACSD-58141**: Es wurde ein Problem behoben, bei dem `PHPSESSID` bei POST-Anfragen im Storefront-Bereich für einen angemeldeten Kunden neu generiert wird, wenn die [!UICONTROL L2 Redis cache] aktiviert ist und der Kunde von „Admin“ aktualisiert wurde.
1. **ACSD-58352**: Es wird das Problem behoben, bei dem Rückgabeattributbeschriftungen für die Standardspeicheransicht über die GraphQL-API zurückgegeben werden, wenn in der Anfragekopfzeile eine nicht standardmäßige Speicheransicht angegeben ist.
1. **ACSD-58442**: Es wird das Problem behoben, dass Geräte mit einer Breite von *768px* als Mobilgeräte behandelt werden, wodurch das Menü und die Kopfzeile in einer Mobilansicht anstelle eines Desktops geladen werden.
1. **ACSD-58790**: Korrigiert *Pinch-to-Zoom*-Funktion auf den Produktdetailseiten-Bildern in der Mobilansicht auf [!DNL Chrome].
1. **ACSD-59036**: Behebt eine Ausnahme, die beim Laden von Produktpreisen mit unteren und oberen Grenzen gleich *$0* auftritt.
1. **ACSD-59229**: Es wird das Problem behoben, dass Informationen zu Kundengruppen aufgrund des alten Werts der [!UICONTROL X-Magento-Vary] in der Anfrage im falschen Segment gespeichert werden.
1. **ACSD-59378**: Es wird das Problem behoben, dass URL-Neuschreibungen auf Store-Ebene beim Import fälschlicherweise aktualisiert werden.
1. **ACSD-59514**: Es wurde das Problem behoben, dass Formulare im Admin-Bereich mit [!DNL Page Builder] den *[!DNL Page Builder]5 Sekunden lang gerendert haben, ohne Sperren freizugeben.* Fehler in der Browser-Konsole nach dem Senden des Formulars und Änderungen können nicht gespeichert werden.
1. **ACSD-60303**: Es wurde ein Problem behoben, bei dem eine Bestellung vom Administrator nicht aufgegeben werden konnte, wenn die HTML-Minimierung aktiviert war.
1. **ACSD-60441**: Es wurde ein Problem behoben, bei dem Kunden über `V1/customers REST API` Endpunkt aktualisiert wurden, wenn das vom Backend generierte Integrations-Zugriffstoken verwendet wurde.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
