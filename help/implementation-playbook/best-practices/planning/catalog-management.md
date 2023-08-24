---
title: Best Practices für die Katalogverwaltung
description: Erfahren Sie mehr über Empfehlungen zum Konfigurieren von Warenkorbbeschränkungen und Produktattributen, zum Auflisten von Paginierung, Optionen, Promotions und Varianten.
role: Developer
feature: Best Practices, Catalog Management
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '1876'
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

Um eine optimale Leistung zu erzielen, sollten Sie die folgenden Richtlinien verwenden, um die Einschränkungen des Warenkorbs für Adobe Commerce und Magento Open Source zu verwalten:

- Für die Versionen 2.3.x - 2.4.2 dürfen maximal 100 Produkte in einem Warenkorb enthalten sein.
- In den Versionen 2.4.3 und höher wurde durch die Verbesserung der Funktionen für Verkaufsregeln der Warenkorb auf maximal 750 erhöht.

Für die Versionen 2.3.x - 2.4.2 lautet die erwartete Leistung basierend auf den Beschränkungen für Warenkorbartikel:

- Bis **100** Produkte in einem Warenkorb - das Produkt funktioniert, indem es Leistungsziele für die Reaktionszeit erfüllt.
- Bis **300** Produkte in einem Warenkorb - das Produkt funktioniert, aber die Reaktionszeit erhöht sich über den Zielwerten.
- Oben **500** Produkte in einem Warenkorb - der Warenkorb und die Checkout-Flüsse funktionieren nicht garantiert

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Verringerung der Anzahl der Artikel im Warenkorb

Verwenden Sie die folgenden Strategien, um die Anzahl der Artikel im Warenkorb zu verwalten

- Aufteilen von Bestellungen in mehrere kleinere Bestellungen mit einer kleineren Anzahl von Zeilen mithilfe der [!UICONTROL Add Item by SKU] Funktion.
- Fügen Sie nur die benutzerdefinierte Logik und die Anpassung des Warenkorbs hinzu, die zum Laden einer Liste von Elementen erforderlich sind.

### Potenzielle Auswirkung auf die Leistung

Wenn Sie mehr als die empfohlene maximale Anzahl von Produkten im Warenkorb haben, kann sich dies auf die Site-Leistung wie folgt auswirken:

- Erhöhte Reaktionszeit für Datenabruffunktionen, Validierung von Warenkorbelementen, Überprüfung der Anwendung von Preisregeln sowie Steuer- und Gesamtberechnungen.
- Verbesserte Reaktionszeit für Minicart-Rendering, einschließlich Darstellung von Warenkorbansichten, Checkout-Fluss und Ausführung.
- Erhöhte Ladezeit für alle Seiten der Site, auf denen das Minicart vorhanden ist.

## Kategorienbeschränkungen

Konfigurieren Sie für optimale Leistung nicht mehr als die maximal empfohlene Anzahl von Kategorien für Adobe Commerce-Sites.

- Konfigurieren Sie für Adobe Commerce-Version 2.4.2 und höher maximal 6000 Kategorien.
- Konfigurieren Sie für die Adobe Commerce-Versionen 2.3.x und 2.4.0 bis 2.4.1-p1 maximal 3000 Kategorien.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Kategorien zu reduzieren:

- Verwalten einzigartiger Produktfunktionen über Attribute und benutzerdefinierte Optionen
- Inaktive Kategorien entfernen
- Optimieren der Katalogtiefe in der Navigation

### Potenzielle Auswirkung auf die Leistung

Eine höhere als die empfohlene maximale Anzahl von Kategorien kann die Site-Leistung auf folgende Weise beeinflussen:

- Deutliche Steigerung der Reaktionszeit für nicht zwischengespeicherte Katalogseiten
- Lange Ausführung und Timeouts bei der Verwaltung von Kategorien über den Administrator
- Vergrößerung der entsprechenden Datenbanktabellen
- Größere Indextabellen erhöhen die Zeit, die zum Ausführen von Indizierungsvorgängen für die `[category/product relation index\]`
- Erhöhte Verarbeitungszeit zum Abschließen der Kategoriestruktur, des Menüabrufs und der Kategorieregelverwaltung

## Produktattribute

- Für eine optimale Leistung sollten Sie nur die maximal empfohlene Anzahl von Produktattributen oder Produktattributoptionen konfigurieren.

- **Produktattribute**—
   - Konfigurieren Sie für die Adobe Commerce-Versionen 2.3.x und 2.4.0 bis 2.4.1-p1 maximal 500 Attribute.
   - Für Adobe Commerce-Version 2.4.2 und höher konfigurieren Sie bis zu 1500 Produktattribute
- **Produktattributoptionen**-Konfigurieren Sie bis zu 100 Attributoptionen für jedes Attribut.
- **Produktattributsätze**-Konfigurieren Sie maximal 1000 Attributsätze.

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

Konfigurieren Sie für optimale Leistung maximal 100 Produktoptionen pro Produkt.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Anzahl der Optionen reduzieren

Verwenden Sie die folgenden Strategien, um die Anzahl der Produktoptionen zu reduzieren, um eine optimale Site-Leistung zu erzielen:

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

Um die beste Leistung zu erzielen, zeigen Sie maximal 48 Produkte pro Seite an.

Sie können Adobe Commerce so konfigurieren, dass Käufer alle Kategorieprodukte auf einer Seite anzeigen können. Wenn die Anzahl der Kategorieprodukte deutlich über 48 Produkte liegt, aktualisieren Sie die Katalogkonfiguration für die Steuerelemente für die Storefront-Paginierung.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Aktualisieren der Produktlistenkonfiguration

Wenn Sie mehr als 48 Produkte in einer Kategorie haben, aktualisieren Sie die Storefront-Katalogkonfiguration, um die Option **Alle Produkte pro Seite zulassen**.

Nachdem Sie diese Option deaktiviert haben, verwendet Adobe Commerce die Steuerelemente für die Storefront-Paginierung, um die Anzahl der Produkte zu verwalten, die in Storefront-Komponenten angezeigt werden. Anweisungen finden Sie unter [Paginierungssteuerelemente konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Produkt-SKU-Beschränkungen

Um die Leistung zu maximieren, wird für effektive Bestandseinheiten (SKUs) eine maximale Anzahl von 242 Millionen empfohlen. Diese effektive Produkt-SKU-Obergrenze wird wie folgt berechnet:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Dabei gilt:

- N steht für die Anzahl der Artikel für diese Kategorie
- Kundengruppen enthalten freigegebene Kataloge, da sie eine zusätzliche Kundengruppe erstellen.

Wenn mehr als die maximale Anzahl effektiver SKUs vorhanden ist, wird der Abruf von Produktdaten verlangsamt und die Zeit zum Abschließen von Vorgängen oder Indizierungen im Admin-Bedienfeld erhöht.

### Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

### Verringerung der Produktanzahl

Verwenden Sie die folgenden Strategien, um die Anzahl der Produkte zu reduzieren:

- Minimieren von Multiplikatoren—
   - Durch die Konsolidierung von Websites wird der Multiplikator reduziert. Wenn Sie 50.000 SKUs, zehn Websites und zehn Kundengruppen haben, beträgt die effektive Anzahl der SKUs 5 Millionen. Wenn fünf Kundengruppen entfernt werden, werden die effektiven SKUs auf 2,5 Millionen reduziert.
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

Konfigurieren Sie für optimale Leistung maximal 50 Varianten pro Produkt.

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

- **Verkaufsregeln (Regeln für den Warenkorbpreis)**-Konfigurieren Sie nicht mehr als 1000 Warenkorbpreisregeln für alle Websites.
   - Nicht verwendete Regeln verwalten und entfernen
   - Fügen Sie strenge Regelbedingungen (wie Attribut- oder Kategoriefilter) hinzu, um eine optimale Übereinstimmung zu erzielen.
- **Coupons**—
   - Stellen Sie sicher, dass die Gesamtzahl der Gutscheine in der Datenbank unter 250.000 liegt.
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
- Das Anwenden von Coupons kann mehr als 2 Sekunden dauern.
