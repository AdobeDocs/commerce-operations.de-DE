---
title: Best Practices für die Konfiguration von Produktattributen
description: Erfahren Sie, wie Sie die Leistung von Adobe Commerce optimieren können, indem Sie die Anzahl der Produktattribute, Attributoptionen und Attributsätze einschränken.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Best Practices für die Produktattributkonfiguration

- Für eine optimale Leistung sollten Sie nur die maximal empfohlene Anzahl von Produktattributen oder Produktattributoptionen konfigurieren.

- **Produktattribute**—
   - Konfigurieren Sie für die Adobe Commerce-Versionen 2.3.x und 2.4.0 bis 2.4.1-p1 maximal 500 Attribute.
   - Für Adobe Commerce-Version 2.4.2 und höher konfigurieren Sie bis zu 1500 Produktattribute
- **Produktattributoptionen**-Konfigurieren Sie bis zu 100 Attributoptionen für jedes Attribut.
- **Produktattributsätze**-Konfigurieren von maximal 1000 Attributsätzen _

>[!NOTE]
>
>Produktattribute geben Funktionen an, die global für alle Produkte gelten. Produktattributoptionen sind Anpassungen, um Funktionen anzugeben, die für bestimmte Produkte gelten.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Anzahl der Produktattribute reduzieren

Für eine optimale Leistung bei der Verwaltung von Produkten über den Administrator und beim Abrufen von Produktdaten im Storefront:

- Verwenden Sie verschiedene Produktvorlagen (Attributsätze) für verschiedene Produkte.
- Nutzen benutzerdefinierter Optionen und komplexer Produkte für die Variantenverwaltung
- Minimieren Sie die Anzahl der durchsuchbaren Attribute.
- Entfernen Sie nicht verwendete Produkteigenschaften.
- Speichern und verwalten Sie nicht Commerce-bezogene Attribute in externen Produktverwaltungssystemen (PMS).

## Optionen für Zahlenproduktattribute reduzieren

Für eine optimale Leistung bei der Verwaltung von Produkten über den Administrator und beim Abrufen von Produktdaten im Storefront:

- Verwenden Sie verschiedene Variantenmechanismen, um Produkte zu erstellen: komplexe Produkte, benutzerdefinierte Optionen als Quelle für Produktvarianten.
- Erstellen Sie spezifische Produktvorlagen mit Zielgruppenattributen und Optionen, um allgemeine Produktvorlagen und Optionscontainer zu vermeiden.
- Verwalten Sie eine Liste der tatsächlichen Attributoptionen.
- Verwalten Sie Produktinformationen über ein externes Produktverwaltungssystem (PMS).

## Verringerung der Anzahl von Produktattributsätzen

Entfernen Sie nicht verwendete Produktattributsätze mit MySQL.

### Konfiguration der Attributsätze überprüfen

1. [Verbindung zur Site-Datenbank herstellen](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Anzahl der Attributsätze mit MySQL suchen

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Entfernen Sie alle nicht verwendeten Attributsätze.

## Mögliche Leistungseinbußen

Konfigurieren vieler **Produktattribute** erhöht die Produktvorlagengröße für jedes Produkt (EAV-Struktur) und die Menge der Daten, die abgerufen werden müssen. Dieser Anstieg wirkt sich auf Vorgänge wie folgt aus:

- Erhöhung des Traffics von SQL-Abfragen im Zusammenhang mit dem Abrufen von EAV-Daten und der Menge der verarbeiteten Daten, was zu einem geringeren DB-Durchsatz führt
- Deutliche Vergrößerung der Adobe Commerce-Indizes und des Volltextsuchindex
- Erreichen von MySQL-Einschränkungen bei der Erstellung eines FLAT-Index für überdimensionierte Produktvorlagen und deren Unfähigkeit, diesen zu verwenden

Erhöhungen von Produktdaten und Indexgrößen können die Site-Performance auf folgende Weise beeinflussen:

- Verbesserte Reaktionszeit für die meisten Storefront-Szenarien im Zusammenhang mit Katalogsuche, Suche (schnell und erweitert) und Navigation auf mehreren Ebenen.
- Produktverwaltungsvorgänge in der Admin-Konsole verlangsamen sich erheblich, was zu Timeouts führen kann.
- Die Funktion für Massenaktionen von Produkten kann blockiert werden.
- Die Neuerstellungszeit von Indizes für mittelgroße und große Kataloge kann aufgrund langer Ausführungszeiten nicht täglich ausgeführt werden.

Konfigurieren vieler **Attributoptionen** kann die Site-Leistung wie folgt beeinflussen:

- Lange Anforderungs- und Wiedergabezeiten für Produktdetails (PDP) und Kategorieseiten mit komplexen Produkten.
- Die Reaktionszeit von Vorgängen zur Produktspeicherung für Administratoren erhöht sich über den optimalen Leistungszielen.
- Verkürzen Sie die Wiedergabedauer des Formulars für die Produktbearbeitung.
- Langsamer Checkout.

## Zusätzliche Informationen

- [Übersicht über Produktattribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Attributsätze](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Produkt erstellen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutorials zum Anpassen > Formular zur Produkterstellung anpassen](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

