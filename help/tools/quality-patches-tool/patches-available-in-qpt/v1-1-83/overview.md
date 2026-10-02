---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.83 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 6fedf98a6936fe842230003e0c2d52598bcf999d
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.83

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.83 verfügbaren Patches behoben wurden.

QPT v1.1.83 enthält die folgenden Patches:

1. **AC-17975**: Behebt mehrere Kompatibilitätsprobleme mit PHP 8.5, die sich auf Admin-Workflows, Checkout-Authentifizierung, CAPTCHA-Verarbeitung, Kategorieverwaltung, Konfigurationsseiten und Befehlszeilenvorgänge in bestimmten PHP-Umgebungen auswirken.
1. **AC-18128**: Es wird das Problem behoben, bei dem von GraphQL zurückgegebene Bestelldaten und Bestellkommentar-Zeitstempel falsche Kalenderdaten in nicht englischen Gebietsschemaeinstellungen anzeigen.
1. **AC-18096**: Es wird das Problem behoben, bei dem Datumsfelder in Sales GraphQL Datumsangaben in einem anderen Format als frühere Versionen zurückgeben, indem das Datumsformat von Schrägstrich (`/`) auf Strich (`-`) zurückgesetzt wird.
1. **ACP2E-4639**: Es wurde ein Problem behoben, bei dem der Elementtyp der Anforderungsliste im GraphQL-Schema falsch geschrieben wurde, während das Feld „Ältere Elemente“ und der `RequistionListItems`-Typ weiterhin verfügbar sind, aber veraltet sind.
1. **ACP2E-4838**: Es wurde das Problem behoben, dass ein Admin-Benutzer mit eingeschränkten Berechtigungen Kundinnen und Kunden nicht aus dem Kundenraster löschen kann.
1. **ACP2E-4877**: Behebt das Problem, dass mit **[!UICONTROL Payment on Account]** aufgegebene Bestellungen nicht in Admin bearbeitet werden konnten, während sie den Status *Ausstehend* hatten.
1. **ACP2E-4908**: Es wird das Problem behoben, dass große Kataloge zu übermäßiger Speichernutzung in Redis oder Valkey führen, da für jedes Produkt in jeder Shop-Ansicht separate Layout-Cache-Einträge erstellt wurden.
1. **AC-12854**: Es wird ein Problem behoben, bei dem durch die Neuanordnung einer Bestellung im Administrator eine neue Bestellnummer mit einem *-1* Suffix erstellt wird, anstatt die nächste sequenzielle Bestellnummer zuzuweisen.
1. **ACP2E-4977**: Behebt das Problem, dass die Gesamtsummen der Rechnungen und Gutschriften für konfigurierbare Produkte keine **[!UICONTROL Fixed Product Tax]** (FPT) enthalten, was zu Gesamtsummen führt, die niedriger als die Bestellsumme sind.
1. **AC-16530**: Es wird ein Problem behoben, bei dem der Warenkorb geplante Aktualisierungen der Katalogpreisregeln nicht einheitlich widerspiegelte.
1. **AC-11389**: Es wird das Problem behoben, bei dem Rabatte, Steuern und Bestellsummen in einigen Rundungsszenarien falsch berechnet werden.
1. **ACP2E-4998**: Behebt das Problem, dass die `POST /V1/products/tier-prices` REST-API-Anfrage für die gesamte Anfrage fehlgeschlagen ist, wenn keine SKU in der Payload vorhanden war, was verhindert, dass gültige SKUs aktualisiert werden.
1. **ACP2E-5015**: Es wird ein Problem behoben, durch das das Speichern eines freigegebenen Katalogs in der Admin unbeabsichtigt zugewiesene Produkte und Preise entfernen kann, wenn erforderliche Katalogdaten nicht verfügbar sind.
1. **AC-14940**: Es wurde ein Problem behoben, bei dem durch Klicken auf **[!UICONTROL Reset Password]** für ein Kundenkonto im Admin-Bereich in einigen Fällen im Zusammenhang mit dem Store die E-Mail zum Zurücksetzen des Kennworts nicht gesendet wurde.
1. **ACP2E-5101**: Es wurde ein Problem behoben, bei dem die Installation des B2B-Moduls fehlgeschlagen ist, wenn Indexer auf **[!UICONTROL Update on Schedule]** gesetzt wurden.
1. **ACP2E-5205**: Behebt das Problem, wenn das Laden von Kategorien viel Zeit in Anspruch nimmt oder eine Zeitüberschreitung verursacht, wenn eine große Anzahl von Kategorien und Produkten betroffen ist. Außerdem wird die Produktanzahl jetzt für jedes Kategorieblatt korrekt angezeigt.
1. **ACP2E-3211**: Es wird ein Problem behoben, durch das beim gleichzeitigen Hinzufügen desselben Produkts zum Warenkorb in der Storefront separate Artikel im Warenkorb für dieselbe SKU erstellt werden, anstatt sie in einem einzigen Artikel zu kombinieren.
1. **ACP2E-5223**: Es wird das Problem behoben, dass der Katalog-Berechtigungsindex Websites enthält, die aus einer Kundengruppe ausgeschlossen sind.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
