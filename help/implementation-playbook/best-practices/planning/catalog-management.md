---
title: Best Practices für die Katalogverwaltung
description: Erfahren Sie mehr über Empfehlungen zum Konfigurieren von Limits für den Warenkorb und Produktattributen, zur Listennummerierung, zu Optionen, zu Promotions und zu Varianten.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# Best Practices für die Katalogverwaltung

Die hier beschriebenen Best Practices für die Katalogverwaltung decken eine Reihe von Problemen ab, darunter (aber nicht nur):

- Warenkorbbeschränkungen
- Kategorienbeschränkungen
- Produktattribute
- Seitenumbruch für Produktliste
- Produktoptionen
- Produktvarianten
- Promotions

## Warenkorbbeschränkungen

Um eine optimale Leistung zu erzielen, verwenden Sie die folgenden Richtlinien, um Warenkorbbeschränkungen für Adobe Commerce zu verwalten.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Anzahl der Artikel im Warenkorb reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Artikel im Warenkorb zu verwalten

- Mithilfe der [!UICONTROL Add Item by SKU]-Funktion können Sie Bestellungen in mehrere kleinere Bestellungen mit einer kleineren Anzahl von Zeilen aufteilen.
- Fügen Sie nur die benutzerdefinierte Logik und die Anpassung des Warenkorbs hinzu, die zum Laden einer Liste von Elementen erforderlich sind.

## Kategorienbeschränkungen

Die Konfiguration einer großen Anzahl von Kategorien kann die Leistung beeinträchtigen.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Anzahl der Produkte reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Kategorien zu verringern:

- Verwalten eindeutiger Produktfunktionen durch Attribute und benutzerdefinierte Optionen
- Inaktive Kategorien entfernen
- Optimieren der Katalogtiefe in der Navigation

## Produktattribute

Die Konfiguration zu vieler Produktattribute oder Produktattributoptionen kann die Leistung beeinträchtigen.

>[!NOTE]
>
>Produktattribute geben Funktionen an, die global für alle Produkte gelten. Produktattributoptionen sind Anpassungen zum Festlegen von Funktionen, die für bestimmte Produkte gelten.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Anzahl der Attribute reduzieren

Für optimale Leistung bei der Verwaltung von Produkten über die Admin-Benutzeroberfläche und beim Abrufen von Produktdaten in der Storefront:

- Verwenden Sie verschiedene Produktvorlagen (Attributsätze) für verschiedene Produkte.
- Nutzung benutzerdefinierter Optionen und komplexer Produkte für das Variantenmanagement
- Minimieren Sie die Anzahl der durchsuchbaren Attribute.
- Entfernen Sie nicht verwendete Produkteigenschaften.
- Speichern und verwalten Sie nicht-Commerce-bezogene Attribute in externen Produktmanagementsystemen (PMS).

### Anzahl der Attributoptionen reduzieren

Für optimale Leistung bei der Verwaltung von Produkten über die Admin-Benutzeroberfläche und beim Abrufen von Produktdaten in der Storefront:

- Verwenden Sie verschiedene Variationsmechanismen, um Produkte zu erstellen: komplexe Produkte, benutzerdefinierte Optionen als Quelle von Produktvarianten.
- Erstellen Sie spezifische Produktvorlagen mit Zielgruppenattributen und Optionen, um allgemeine Produktvorlagen und Optionscontainer zu vermeiden.
- Eine Liste der tatsächlichen Attributoptionen verwalten.
- Verwalten Sie Produktinformationen über ein externes Produktverwaltungssystem (PMS).

### Anzahl der Attributsätze reduzieren

Entfernen Sie nicht verwendete Produktattributsätze mit MySQL.

#### Konfiguration des Attributsatzes überprüfen

1. [Verbindung zur Website-Datenbank herstellen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database).

1. Ermitteln der Anzahl der Attributsätze mit MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Entfernen Sie alle nicht verwendeten Attributsätze.

### Potenzielle Auswirkungen auf die Leistung

Durch die Konfiguration **Produktattribute** die Größe der Produktvorlage für jedes Produkt (EAV-Struktur) und die Menge der abzurufenden Daten erhöht. Dieser Anstieg wirkt sich wie folgt auf Vorgänge aus:

- Anstieg des SQL-Traffics bei Abfragen im Zusammenhang mit dem EAV-Datenabruf und der Menge an verarbeiteten Daten, was zu einem verringerten DB-Durchsatz führt
- Deutliche Vergrößerung der Adobe Commerce-Indizes und des Volltextsuchindex
- Erzielen von harten MySQL-Beschränkungen beim Erstellen eines FLAT-Index für übergroße Produktvorlagen und Unfähigkeit, ihn zu verwenden

Steigende Produktdaten und Indexgrößen können sich auf folgende Weise auf die Site-Performance auswirken:

- Erhöhte Reaktionszeit für die meisten Storefront-Szenarien im Zusammenhang mit Katalogbrowsen, Suche (schnell und erweitert) und mehrschichtiger Navigation.
- Produktverwaltungsvorgänge in der Admin-Instanz verlangsamen sich erheblich, was zu Zeitüberschreitungen führen kann.
- Die Funktion für Produkt-Massenaktionen kann blockiert werden.
- Die Zeit für die Neuerstellung von Indizes für mittelgroße und große Kataloge kann aufgrund der langen Ausführungszeiten nicht täglich ausgeführt werden.

Die Konfiguration vieler **Attributoptionen** kann die Site-Leistung auf folgende Weise beeinträchtigen:

- Lange Anfrage- und Rendering-Zeiten für Produktdetailseiten (PDP) und Kategorieseiten mit komplexen Produkten.
- Die Reaktionszeit von Admin-Produktspeichervorgängen erhöht sich über die optimalen Leistungsziele hinaus.
- Verkürzen der Rendering-Zeit für die Produktbearbeitung.
- Langsamer Checkout.

## Produktoptionen

Die Konfiguration zu vieler Produktoptionen pro Produkt kann die Leistung beeinträchtigen.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Anzahl der Optionen reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Produktoptionen pro Produkt zu reduzieren:

- Konfigurieren Sie komplexe Produkte und benutzerdefinierte Optionen als Quelle für Produktvarianten.
- Statt globale Produktvorlagen und Optionscontainer zu erstellen, die für alle Produkte gelten, verwenden Sie Attributsätze , um bestimmte Produktvorlagen mit zielgerichteten Attributen und Optionen zu erstellen.
- Verwalten Sie Produktinformationen über ein externes Produktverwaltungssystem (PMS).

### Potenzielle Auswirkungen auf die Leistung

Die Konfiguration vieler Produktoptionen erhöht die Datenmenge, die für jedes Produkt bei allen Lese- und Schreibvorgängen abgerufen wird, was zu Folgendem führt:

- Erhöhter SQL-Abfrage-Traffic und umfangreichere `JOIN` erhöhen den Datenbankdurchsatz.
- Größere Version für Adobe Commerce-Indizes und den Volltextsuchindex.

Die oben aufgeführten Erhöhungen wirken sich möglicherweise auf folgende Weise auf die Site-Leistung aus:

- Längere Reaktionszeit für die meisten Storefront-Szenarien in Bezug auf Produkte, die viele Optionen in Attributen enthalten.
- Signifikante Verkürzung der Zeit, die zum Abschließen von Produktverwaltungsvorgängen in Admin benötigt wird und zu Zeitüberschreitungen führen kann, insbesondere bei Szenarien, die mit dem Abrufen von Attributlisten und Baumstrukturen zusammenhängen, einschließlich der Verwaltung von Promotion-Regeln.
- Kann Massenaktionen blockieren, die asynchrone Massenvorgänge wie den Import und Export durchführen und benutzerdefinierte Preise mehreren Produkten in einem gemeinsamen Katalog zuweisen.

## Seitenumbruch für Produktliste

Die Anzeige zu vieler Produkte pro Seite kann die Leistung beeinträchtigen.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Aktualisieren der Konfiguration der Produktliste

Wenn eine Kategorie zu viele Produkte enthält, aktualisieren Sie die Konfiguration des Storefront-Katalogs, um die Option &quot;**Produkte pro Seite zulassen“** deaktivieren.

Nachdem Sie diese Option deaktiviert haben, verwendet Adobe Commerce die Paginierungssteuerelemente für die Produktliste, um die Anzahl der Produkte zu verwalten, die in Storefront-Komponenten angezeigt werden. Anweisungen finden Sie unter [Konfigurieren von Paginierungssteuerelementen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html?lang=de#configure-the-pagination-controls).

## Produkt-SKU-Beschränkungen

Die Konfiguration zu vieler Produkt-SKUs kann die Leistung beeinträchtigen, indem der Abruf von Produktdaten verlangsamt und die Zeit bis zum Abschluss von Admin-Vorgängen oder -Indizierungen verlängert wird.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Anzahl der Produkte reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Produkte (SKUs) zu reduzieren:

- Multiplikatoren minimieren—
   - Die Konsolidierung von Websites reduziert den Multiplikator.
   - Verwenden Sie alternative Produktfunktionen für benutzerdefinierte Preise, um freigegebene Katalog- und Kundengruppen-Multiplikatoren zu ersetzen.
   - Sowohl Kundengruppen als auch freigegebene Kataloge fungieren als Multiplikatoren für die Anzahl der effektiven SKUs in einem Geschäft.
- Katalog neu strukturieren—
   - Reduzieren Sie die Anzahl der Produkte, die Kategorien zugewiesen sind.
   - Verringern Sie die Anzahl der SKUs, indem Sie die Anzahl der Websites, Kundengruppen, freigegebenen Kataloge, die Anzahl der Produkte oder die Anzahl der konfigurierbaren Produktoptionen verringern.
- Stellen Sie mehr Produktvarianten bereit, indem Sie benutzerdefinierte Optionen verwenden, anstatt separate Produkte zu erstellen.
- Unter Berücksichtigung der Tatsache, dass eine effektive SKU eine Reihe potenzieller Permutationen von Preisen enthalten könnte, da Preise für jedes Geschäft oder jede Kundengruppe unterschiedlich angegeben werden können.
- Deaktivieren oder entfernen Sie nicht verwendete Systemkomponenten wie Module. Siehe [Module deinstallieren](../../../installation/tutorials/uninstall-modules.md).
- Verwalten Sie Produkte in einem externen Plattformverwaltungssystem (PMS).

## Produktvarianten

Die Konfiguration zu vieler Varianten pro Produkt kann die Leistung beeinträchtigen.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Anzahl der Varianten reduzieren

Für eine optimale Site-Performance sollten Sie die folgenden Strategien verwenden, um die Anzahl der Produktvarianten zu reduzieren:

- Strukturieren Sie den Katalog neu, indem Sie die Anzahl der Varianten auf verschiedene Produkte verteilen.
- Entfernen Sie konfigurierbare Attributoptionen, die nicht vorrätig sind.
- Verwalten Sie Varianten durch alternative Funktionen wie benutzerdefinierte Optionen, Kategorien, verwandte, gruppierte und gebündelte Produkte.

### Potenzielle Auswirkungen auf die Leistung

Eine Überschreitung der empfohlenen Anzahl von Produktvarianten kann sich auf folgende Weise auf die Site-Leistung auswirken:

- Lange Anfrage- und Rendering-Zeiten für Produktdetails und Kategorieseiten mit komplexen Produkten.
- Verkürzte Reaktionszeit bis zum Abschluss von Speichervorgängen im Administrator.
- Längere Zeit zum Rendern des Produktbearbeitungsformulars.
- Langsamer Checkout.

## Promotions

Befolgen Sie diese Best Practices, um Verkäufe und Promotions für Artikel in einem Warenkorb zu konfigurieren:

- **Verkaufsregeln (Regeln für den Warenkorbpreis)**
   - Verwalten und Entfernen nicht verwendeter Regeln.
   - Fügen Sie strenge Regelbedingungen (wie Attribut- oder Kategoriefilter) für eine effiziente Zuordnung hinzu.
- **Coupons**
   - Entfernen Sie nicht verwendete und abgelaufene Gutscheine.
   - Generieren Sie nur die Anzahl der Coupons, die zur Erfüllung der Kampagnenanforderungen erforderlich sind.

### Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

### Potenzielle Auswirkungen auf die Leistung

Eine Überschreitung der empfohlenen maximalen Anzahl von Warenkorbpreisregeln oder Coupons kann die Site-Leistung auf folgende Weise beeinträchtigen:

- Erhöhte Reaktionszeit, wenn Produkte zum Warenkorb hinzugefügt werden.
- Erhöhte Zeit zum Laden und Rendern des Minicart.
- Erhöhte Zeit zum Rendern der Warenkorbseite.
- Verkürzte Zeit zum Rendern des **Summen**-Blocks auf der Kaufbestätigungsseite.
