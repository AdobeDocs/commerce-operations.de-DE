---
title: 'Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.84'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.84 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f0b3307638e56d5930753a4123a98ddea6714faa
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%
---
# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.84

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.84 verfügbaren Patches behoben wurden.

QPT v1.1.84 enthält die folgenden Patches:

1. **ACP2E-4913**: Behebt das Problem, dass Versand- und Rechnungsvorgänge aufgrund eines Deadlocks fehlschlagen.
1. **ACP2E-5005**: Behebt das Problem, dass die Menge einer Bundle-Produktoption in einem verhandelbaren Angebot auf ihren vorherigen Wert zurückgesetzt wird, wenn das Bundle-Produkt in der Admin neu konfiguriert und die Menge bearbeitet wird.
1. **ACP2E-5009**: Es wird das Problem behoben, dass bei der Datenmigration von Magento Open Source zu Adobe Commerce geplante Designänderungen für Kategorien und geplante Produktaktualisierungen nicht korrekt migriert werden, sodass einige geplante Aktualisierungen während der Migration fehlen oder übersprungen werden und die Migrationsleistung verbessert **[!UICONTROL Special Price]**.
1. **ACP2E-5017**: Es wird ein Problem behoben, bei dem die Abfrage einer Kundenrolle über GraphQL einen *Internen Server-Fehler* zurückgibt, wenn der Kunde keinem Unternehmen zugewiesen ist.
1. **ACP2E-5027**: Behebt das Problem, dass Indexer in einer Schleife stecken bleiben und die Neuindizierung nicht abgeschlossen werden kann, wenn die Dateisperrung aktiviert ist.
1. **ACP2E-5029**: Es wird ein Problem behoben, bei dem Änderungen an Katalogpreisregeln erst dann in **[!DNL Live Search]** angezeigt werden, wenn eine manuelle Resynchronisierung durchgeführt wurde.
1. **ACP2E-5041**: Behebt das Problem, dass beim Speichern eines Produkts während eines geplanten Updates die Storefront nach dem Ende des Updates den regulären Preis anstelle des **[!UICONTROL Special Price]** anzeigt.
1. **ACP2E-5059**: Es wird das Problem behoben, dass Kundinnen und Kunden doppelte Auftragsbestätigungs-E-Mails für dieselbe Bestellung erhalten.
1. **ACP2E-5122**: Es wird das Problem behoben, dass behandelte Fehler von GraphQL-Anfragen für den Warenkorb fälschlicherweise in Ausnahmeprotokollen als Anwendungsfehler aufgezeichnet werden.
1. **ACP2E-5143**: Es wird das Problem behoben, dass die GraphQL-Routenabfrage vollständige CMS-Seiteninhalte rendert, wenn nur Routing-Metadaten angefordert werden, was die Datenbankabfragen für CMS-Seiten erhöht, die Page Builder-Widgets enthalten.
1. **ACP2E-5183**: Behebt das Problem, dass die Bereitstellung statischer Inhalte in PHP 8.5 beim Kompilieren einer `LESS`-Datei, die die `@magento_import`-Direktive verwendet, fehlschlägt.
1. **ACP2E-5242**: Es wurde ein Problem behoben, bei dem beim Überprüfen der Produktverfügbarkeit beim Hinzufügen von Artikeln zum Warenkorb ein Fehler angezeigt wurde, der angibt, dass die Website nicht gefunden werden kann.
1. **ACP2E-5263**: Es wird das Problem behoben, dass das Exportieren von Produkten in eine CSV-Datei gestoppt werden kann, bevor alle Produkte einbezogen werden, was zu einer unvollständigen Datei führt.
1. **ACP2E-5034**: Es wird ein Problem behoben, bei dem die Gesamtsummen bei der Neuberechnung eines Angebots nach der Auswahl einer Versandmethode fälschlicherweise auf *null* zurückgesetzt werden. Außerdem werden Aktualisierungen der Produktoptionsmengen verworfen, die durch die **[!UICONTROL Configure]**-Aktion in der Admin vorgenommen wurden, und es werden keine korrekten Rabatte auf Artikelebene berücksichtigt, die auf dynamische Preispaketprodukte in Angebots-Zwischensummen angewendet werden.
1. **ACP2E-4741**: Behebt das Problem, dass ein Produkt aus der Storefront verschwindet, nachdem ein mit ihm verknüpftes Produkt als [!UICONTROL Related Product], [!UICONTROL Up-Sell] oder Crosssell gespeichert wurde, während ein nicht standardmäßiger Bestand und eine Quelle verwendet werden.
1. **ACP2E-5079**: Es wird ein Problem behoben, durch das bei der Auswertung eines Kundensegments, das mehreren Websites zugewiesen wurde, übereinstimmende Kunden nur von der ersten Website zurückgibt, wenn Kundenkonten global freigegeben werden.
1. **ACP2E-5127**: Es wird ein Problem behoben, bei dem das Bearbeiten eines Unternehmenskontos im Admin-Bedienfeld mit einem nicht standardmäßigen Gebietsschema dessen **[!UICONTROL Credit Limit]** auf &quot;*&quot;*.
1. **AC-15494**: Es wird das Problem behoben, bei dem die Produktabfrage Produktnamen mit HTML-Escape-Sonderzeichen anstelle der Originalzeichen zurückgibt.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
