---
title: Best Practices für die Katalogverwaltung
description: Erfahren Sie mehr über Empfehlungen zum Konfigurieren von Warenkorbbeschränkungen und Produktattributen, zum Auflisten von Paginierung, Optionen, Promotions und Varianten.
role: Developer
feature: Best Practices, Catalog Management
source-git-commit: a81e88a4293880ae90cd531ce60c5a2b177188f2
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---


# Best Practices für die Katalogverwaltung

Die hier beschriebenen Best Practices für die Katalogverwaltung decken eine Reihe von Problemen ab, darunter (aber nicht beschränkt auf):

- Begrenzung des Warenkorbs
- Kategorienbeschränkungen
- Produktattribute
- Paginierung von Produktlisten
- Produktoptionen
- Produktvarianten
- Promotions

## Begrenzung des Warenkorbs

Verwenden Sie die folgenden Richtlinien, um die Einschränkungen des Warenkorbs für Adobe Commerce und Magento Open Source zu verwalten, um eine optimale Leistung zu erzielen.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Verringerung der Anzahl der Artikel im Warenkorb

Verwenden Sie die folgenden Strategien, um die Anzahl der Artikel im Warenkorb zu verwalten

- Aufteilen von Bestellungen in mehrere kleinere Bestellungen mit einer kleineren Anzahl von Zeilen mithilfe der [!UICONTROL Add Item by SKU] Funktion.
- Fügen Sie nur die benutzerdefinierte Logik und die Anpassung des Warenkorbs hinzu, die zum Laden einer Liste von Elementen erforderlich sind.

## Kategorienbeschränkungen

Die Konfiguration einer großen Anzahl von Kategorien kann sich auf die Leistung auswirken.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Kategorien zu reduzieren:

- Verwalten einzigartiger Produktfunktionen über Attribute und benutzerdefinierte Optionen
- Inaktive Kategorien entfernen
- Optimieren der Katalogtiefe in der Navigation

## Produktattribute

Das Konfigurieren zu vieler Produktattribute oder Produktattributoptionen kann sich auf die Leistung auswirken.

>[!NOTE]
>
>Produktattribute geben Funktionen an, die global für alle Produkte gelten. Produktattributoptionen sind Anpassungen, um Funktionen anzugeben, die für bestimmte Produkte gelten.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Anzahl der Attribute reduzieren

Für eine optimale Leistung bei der Verwaltung von Produkten über den Administrator und beim Abrufen von Produktdaten im Storefront:

- Verwenden Sie verschiedene Produktvorlagen (Attributsätze) für verschiedene Produkte.
- Nutzen benutzerdefinierter Optionen und komplexer Produkte für die Variantenverwaltung
- Minimieren Sie die Anzahl der durchsuchbaren Attribute.
- Entfernen Sie nicht verwendete Produkteigenschaften.
- Speichern und verwalten Sie nicht Commerce-bezogene Attribute in externen Produktverwaltungssystemen (PMS).

### Verringerung der Anzahl der Attributoptionen

Für eine optimale Leistung bei der Verwaltung von Produkten über den Administrator und beim Abrufen von Produktdaten im Storefront:

- Verwenden Sie verschiedene Variantenmechanismen, um Produkte zu erstellen: komplexe Produkte, benutzerdefinierte Optionen als Quelle für Produktvarianten.
- Erstellen Sie spezifische Produktvorlagen mit Zielgruppenattributen und Optionen, um generalisierte Produktvorlagen und Optionscontainer zu vermeiden.
- Verwalten Sie eine Liste der tatsächlichen Attributoptionen.
- Verwalten Sie Produktinformationen über ein externes Produktverwaltungssystem (PMS).

### Verringern der Anzahl der Attributsätze

Entfernen Sie nicht verwendete Produktattributsätze mit MySQL.

#### Konfiguration der Attributsätze überprüfen

1. [Verbindung zur Site-Datenbank herstellen](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Anzahl der Attributsätze mit MySQL suchen

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Entfernen Sie alle nicht verwendeten Attributsätze.

### Potenzielle Auswirkung auf die Leistung

Viele Konfigurationen **Produktattribute** erhöht die Produktvorlagengröße für jedes Produkt (EAV-Struktur) und die Menge der Daten, die abgerufen werden müssen. Dieser Anstieg wirkt sich auf Vorgänge wie folgt aus:

- Erhöhung des Traffics von SQL-Abfragen im Zusammenhang mit dem Abrufen von EAV-Daten und der Menge der verarbeiteten Daten, was zu einem geringeren DB-Durchsatz führt
- Deutliche Vergrößerung der Adobe Commerce-Indizes und des Volltextsuchindex
- Erreichen von MySQL-Einschränkungen bei der Erstellung eines FLAT-Index für überdimensionierte Produktvorlagen und deren Unfähigkeit, diesen zu verwenden

Erhöhungen von Produktdaten und Indexgrößen können die Site-Performance auf folgende Weise beeinflussen:

- Verbesserte Reaktionszeit für die meisten Storefront-Szenarien im Zusammenhang mit Katalogsuche, Suche (schnell und erweitert) und Navigation auf mehreren Ebenen.
- Produktverwaltungsvorgänge in der Admin-Konsole verlangsamen sich erheblich, was zu Timeouts führen kann.
- Die Funktion für Massenaktionen von Produkten kann blockiert werden.
- Die Neuerstellungszeit von Indizes für mittelgroße und große Kataloge kann aufgrund langer Ausführungszeiten nicht täglich ausgeführt werden.

Viele Konfigurationen **Attributoptionen** kann die Site-Leistung wie folgt beeinflussen:

- Lange Anforderungs- und Wiedergabezeiten für Produktdetails (PDP) und Kategorieseiten mit komplexen Produkten.
- Die Reaktionszeit von Vorgängen zur Produktspeicherung für Administratoren erhöht sich über den optimalen Leistungszielen.
- Verkürzen Sie die Wiedergabedauer des Formulars für die Produktbearbeitung.
- Langsamer Checkout.

## Produktoptionen

Die Konfiguration zu vieler Produktoptionen pro Produkt kann sich auf die Leistung auswirken.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Anzahl der Optionen reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Produktoptionen pro Produkt zu reduzieren:

- Konfigurieren Sie komplexe Produkte und benutzerdefinierte Optionen als Quelle für Produktvarianten.
- Verwenden Sie anstelle der Erstellung globaler Produktvorlagen und Optionscontainer, die für alle Produkte gelten, Attributsätze, um spezifische Produktvorlagen mit Zielattributen und Optionen zu erstellen.
- Verwalten Sie Produktinformationen über ein externes Produktverwaltungssystem (PMS).

### Potenzielle Auswirkung auf die Leistung

Durch die Konfiguration vieler Produktoptionen erhöht sich die Datenmenge, die für jedes Produkt bei allen Lese- und Schreibvorgängen abgerufen wird. Dies führt zu Folgendem:

- Erhöhter SQL-Abfrageverkehr und schwerer `JOIN` -Vorgänge erhöhen den Datenbankdurchsatz.
- Erhöhte Größe für Adobe Commerce-Indizes und den Volltextsuchindex.

Die oben aufgeführten Steigerungen können sich auf die Site-Leistung wie folgt auswirken:

- Längere Reaktionszeiten für die meisten Storefront-Szenarien im Zusammenhang mit Produkten, die viele Optionen in Attributen enthalten.
- Deutliche Zeiteinsparungen beim Ausführen von Produktverwaltungsvorgängen in Admin, die zu Timeouts führen können, insbesondere bei Szenarien, die sich auf die Attributliste und den Abruf von Baumstrukturen einschließlich der Verwaltung von Promotion-Regeln beziehen.
- Kann Massenaktionen blockieren, die asynchrone Massenvorgänge wie Import und Export abschließen und benutzerdefinierte Preise mehreren Produkten in einem freigegebenen Katalog zuweisen.

## Paginierung von Produktlisten

Die Anzeige zu vieler Produkte pro Seite kann die Leistung beeinträchtigen.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Aktualisieren der Produktlistenkonfiguration

Wenn eine Kategorie zu viele Produkte enthält, aktualisieren Sie die Konfiguration des Storefront-Katalogs, um die Option zu deaktivieren, **Alle Produkte pro Seite zulassen**.

Nachdem Sie diese Option deaktiviert haben, verwendet Adobe Commerce die Steuerelemente für die Storefront-Paginierung, um die Anzahl der Produkte zu verwalten, die in Storefront-Komponenten angezeigt werden. Anweisungen finden Sie unter [Paginierungssteuerelemente konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Produkt-SKU-Beschränkungen

Die Konfiguration zu vieler Produkt-SKUs kann die Leistung beeinträchtigen, indem sie das Abrufen von Produktdaten verlangsamt und die Zeit für den Abschluss von Admin-Vorgängen oder -Indizierungen verlängert.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Produkte zu reduzieren:

- Minimieren von Multiplikatoren—
   - Durch die Konsolidierung von Websites wird der Multiplikator reduziert.
   - Verwenden Sie alternative Produktfunktionen für benutzerdefinierte Preise, um freigegebene Katalog- und Kundengruppen-Multiplikatoren zu ersetzen.
   - Sowohl Kundengruppen als auch freigegebene Kataloge fungieren als Multiplikatoren für die Anzahl der effektiven SKUs in einem Geschäft.
- Neustrukturierung des Katalogs—
   - Reduzieren Sie die Anzahl der den Kategorien zugewiesenen Produkte.
   - Verringern Sie die Anzahl der SKUs, indem Sie die Anzahl der Websites, Kundengruppen, freigegebenen Kataloge, die Anzahl der Produkte oder die Anzahl der konfigurierbaren Produktoptionen reduzieren.
- Stellen Sie mehr Produktvarianten bereit, indem Sie benutzerdefinierte Optionen verwenden, anstatt separate Produkte zu erstellen.
- Unter Berücksichtigung der Tatsache, dass eine effektive SKU eine Reihe potenzieller Preisveränderungen umfassen könnte, da die Preise je Geschäft oder Kundengruppe unterschiedlich angegeben werden können.
- Deaktivieren oder entfernen Sie nicht verwendete Systemkomponenten wie Module. Siehe  [Module deinstallieren](../../../installation/tutorials/uninstall-modules.md).
- Verwalten Sie Produkte in einem externen Platform Management System (PMS).

## Produktvarianten

Die Konfiguration zu vieler Varianten pro Produkt kann sich auf die Leistung auswirken.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Anzahl der Varianten reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Produktvarianten zu reduzieren, um eine optimale Site-Leistung zu erzielen:

- Strukturieren Sie den Katalog neu, indem Sie die Anzahl der Varianten auf verschiedene Produkte verteilen.
- Entfernen Sie konfigurierbare Attributoptionen, die nicht auf Lager sind.
- Verwalten Sie Varianten durch alternative Funktionen wie benutzerdefinierte Optionen, Kategorien, zugehörige, gruppierte und gebündelte Produkte.

### Potenzielle Auswirkung auf die Leistung

Eine Überschreitung der empfohlenen Anzahl von Produktvarianten kann die Site-Performance auf folgende Weise beeinflussen:

- Lange Anforderungs- und Wiedergabezeiten für Produktdetails und Kategorieseiten mit komplexen Produkten.
- Verbesserte Reaktionszeit zum Abschließen von Speichervorgängen in der Admin-Konsole.
- Die Zeit zum Rendern des Formulars zur Produktbearbeitung wurde verlängert.
- Langsamer Checkout.

## Promotions

Befolgen Sie diese Best Practices, um Verkäufe und Promotions für Artikel in einem Warenkorb zu konfigurieren:

- **Verkaufsregeln (Regeln für den Warenkorbpreis)**
   - Nicht verwendete Regeln verwalten und entfernen
   - Fügen Sie strenge Regelbedingungen (wie Attribut- oder Kategoriefilter) hinzu, um eine optimale Übereinstimmung zu erzielen.
- **Coupons**
   - Entfernen Sie nicht verwendete und abgelaufene Gutscheine.
   - Generieren Sie nur die Anzahl der Coupons, die zur Erfüllung der Kampagnenanforderungen erforderlich sind.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Potenzielle Auswirkung auf die Leistung

Wenn Sie mehr als die empfohlene maximale Anzahl von Regeln oder Gutscheinen für den Warenkorbpreis haben, kann sich dies wie folgt auf die Site-Leistung auswirken:

- Die Reaktionszeit beim Hinzufügen von Produkten zum Warenkorb wurde verlängert.
- Die Zeit zum Laden und Rendern des Minicarts wurde verlängert.
- Die Zeit zum Rendern der Warenkorbseite wurde verlängert.
- Erhöhte Zeit zum Rendern der **Gesamt** auf der Checkout-Seite.

