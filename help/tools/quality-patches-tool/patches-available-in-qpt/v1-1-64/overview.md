---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.64  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f6013ec84c1b3c65e2fe2ca062616976326d2fef
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.64

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.64 verfügbaren Patches behoben wurden.

QPT v1.1.64 enthält die folgenden Patches:

1. **ACP2E-3838**: Es wird das Problem behoben, bei dem [!DNL Page Builder] CORS-Fehler das Speichern von Änderungen im Admin-Bedienfeld im Produktionsmodus verhindern.
1. **ACP2E-3841**: Es wird das Problem behoben, dass Warenkorbpreisregeln für Produkte mit mehreren Versandarten nicht korrekt angewendet werden, wenn `subselect` Bedingungen verwendet werden und **[!UICONTROL Free Shipping]** aktiviert ist.
1. **ACSD-63139**: Es wird ein Problem behoben, bei dem der Produktexport fehlschlägt, wenn Produktattribute Tausende von Optionswerten enthalten.
1. **ACSD-65100**: Es wird ein Problem behoben, bei dem das Entfernen der Werte für **[!UICONTROL Maximum Width]** und **[!UICONTROL Maximum Height]** in der **[!UICONTROL Media Gallery Image Optimization]**-Konfiguration einen Fehler während des Bildoptimierungsprozesses verursacht.
1. **ACSD-65127**: Es wird ein Problem behoben, bei dem durch die Aktivierung der JavaScript-Minimierung im Produktionsmodus [!DNL TinyMCE] 6 Fehler in der Browser-Konsole generiert, die die Funktionalität und das Benutzererlebnis beeinträchtigen.
1. **ACSD-65787**: Es wird das Problem behoben, dass die `SchemaBuilder`-Klasse bei der Schemaerstellung oder bei Aktualisierungen aufgrund eines nicht definierten Array-Schlüssels (Spalte *bei* Verarbeitung von Tabellendaten abstürzt.
1. **ACSD-65223**: Es wird ein Problem behoben, bei dem manuell ausgewählte Bedingungen und Vereinbarungen für [!DNL B2B] Bestellungen zu einem Fehler führen.
1. **ACSD-65540**: Es wird das Problem behoben, bei dem ein SQL-Syntaxfehler auftritt, da die `REGEXP_LIKE`-Funktion beim Aktualisieren der `company_structure`-Tabelle nicht vorhanden ist.
1. **ACSD-65684**: Behebt das Leistungsproblem, bei dem das Upgrade des `Magento_Company`-Moduls nach dem Update auf [!DNL B2B] 1.5.2 übermäßig lange dauerte, wenn eine große Anzahl von Datensätzen (~100.000+) in der `company_structure` verarbeitet wurde.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
