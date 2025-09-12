---
source-git-commit: 3948c3c59a53a023edc16698fcb9ec6150cbca21
workflow-type: tm+mt
source-wordcount: '6465'
ht-degree: 0%

---
# Adobe Commerce-Glossar

## A

### über dem Falz

_Adjektiv_

In einem Browserfenster wird der Inhalt angezeigt, der unmittelbar nach dem Laden einer Web-Seite und vor dem Scrollen der Seite durch einen Benutzer sichtbar ist.
Verwenden Sie beim Entwerfen Ihres Layouts flexible Formate, um die Produkte, Funktionen, Verkäufe, Benachrichtigungen, Optionen usw. mit der höchsten Priorität in diesem Bereich am besten anzuzeigen.

Bei Mobilgeräten und Tablets unterscheidet sich der Bereich über dem Falz erheblich, insbesondere in Bezug auf die Größe und Abmessungen des Bildschirms und die Ausrichtung beim Betrachten (Hochformat vs. Querformat).
Die Verwendung responsiver Designs und Tests kann dabei helfen, die richtige Mischung aus Inhalt und Layout zu finden.

_Attribute :_

* _Feld: design_

### aktive Verzweigung

_Substantiv_

Eine aktive Verzweigung oder Umgebung ist eine, die mit einer bereitgestellten oder ausgeführten Instanz mit Zugriff auf Services verbunden ist.
Bei der Deaktivierung wird die Verbindung zu den Services und zur laufenden Instanz entfernt, der Code bleibt jedoch erhalten.
Es wird zu einer gewöhnlichen Git-Verzweigung.

_Attribute :_

* _Feld: cloud_

### Zwischenstück

_Substantiv_

Eine Klasse, die es zwei ansonsten inkompatiblen Systemen ermöglicht, zusammenzuarbeiten, ohne den Quellcode des Systems zu ändern.
Beispiele sind Datenbankadapter, Cache-Adapter, Dateisystemadapter, Adapter für Postprozessorbibliotheken und andere Arten von Computing-Adaptern.

_Attribute :_

* _Feld: programmierung_

### Administrator

_Substantiv_

In der -Software eine Benutzerrolle mit vollständigen Administratorrechten, um alle Funktionen zu verwalten.
In Adobe Commerce haben Admin-Benutzer vollständige Berechtigungen und Zugriff auf alle Funktionen, Optionen und Funktionen in Admin.
Sie können auch Benutzer und Rollen erstellen.

Weitere Informationen: [Benutzer hinzufügen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=de)

_Attribute :_

* _Feld: Commerce-Software_
* _Synonyme: Administrator, Superuser_
* _Verwandte Begriffe: Commerce-Admin_

### Administratorbereich

_Substantiv_

Das kennwortgeschützte Backoffice Ihres Geschäfts, in dem Bestellungen, Kataloge, Inhalte und Konfigurationen verwaltet werden.
Benutzer greifen auf den Admin-Bereich zu, um den Store zu verwalten, einschließlich Produkte, Bestellungen, Sendungen, CMS-Inhalte, Design der Storefront, Kundeninformationen usw.
Admin-Benutzende haben eine -Rolle mit Berechtigungen, die den Zugriff auf Funktionen, Optionen und Funktionen steuern.

Weitere Informationen: [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=de)

_Attribute :_

* _Feld: Commerce-Software_
* _Synonyme: Admin, Admin-Bedienfeld, Backend, Administration-Benutzeroberfläche, Admin-Benutzeroberfläche_
* _Verwandte Begriffe: admin_

### ADMIN-Variablen

_Substantiv_

ADMIN-Variablen sind Projektumgebungsvariablen, mit denen die Konfigurationseinstellungen für das Admin-Benutzerkonto für den Zugriff auf die Admin-Benutzeroberfläche außer Kraft gesetzt werden können.

Weitere Informationen: &quot;[-Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=de)

_Attribute :_

* _Feld: admin, cloud_

### adminHTML

_Substantiv_

Der interne Bereichsname, der dem Administrator zugewiesen wurde.

Weitere Informationen: [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=de)

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Bereich, Commerce-Admin_

### Bereich

_Substantiv_

Bereich ist ein abstrakter Begriff für einen Magento-Anwendungsbereich.
Gebiete sind logische Komponenten, die Code für eine optimierte Anfrageverarbeitung organisieren.
Gebiete reduzieren den Speicherbedarf der Konfigurationsobjekte, auf die von der Storefront zugegriffen wird, und sie optimieren Webservice-Aufrufe, indem sie nur den erforderlichen abhängigen Code laden.
Jeder Bereich kann einen völlig anderen Code zur Verarbeitung von URLs und Anfragen enthalten.

Zu den Adobe Commerce-Bereichen gehören:

* Admin (adminhtml)
* Schaufenster
* Web API REST (webapi_rest)

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Commerce-Komponente, Storefront_

### Attribut

_Substantiv_

Ein Merkmal oder eine Eigenschaft eines Produkts, das bzw. die einen Aspekt des Produkts beschreibt.
Adobe Commerce-Benutzer können benutzerdefinierte Attribute erstellen, die dem standardmäßigen -Attributsatz oder einem benutzerdefinierten Attributsatz hinzugefügt werden können.
Erstellen Sie diese Attribute über den Administrator oder programmgesteuert.
Beispiele: Farbe, Größe, Gewicht, Preis, Alter, Geschlecht usw.

Benutzerdefinierte Attribute sind ein Typ des Attributs „Entity-Attribute-Value“ (EAV).

Bei Integrationen wie Google Shopping Ads Channel und Amazon Sales Channel ordnen Sie Commerce-Attribute den Attributen im Drittanbieter zu, um Produkte richtig anzuzeigen und zu verkaufen, Anzeigen anzuzeigen.

Weitere Informationen: [EAV und extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Synonyme: Produktattribut, benutzerdefiniertes Attribut_
* _Verwandte Begriffe: Erweiterungsattribut_

### Attributgruppe

_Substantiv_

Eine logische Gruppierung von Attributen innerhalb eines Attributsatzes.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Attribut_

### Attributsatz

_Substantiv_

Eine Sammlung von Attributgruppen, angepasst für ein bestimmtes Produkt.
Beispiel: Ein T-Shirt-Attributsatz kann Farbe, Größe, Geschlecht und Marke enthalten.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Attribut_

### Durchschnittliche Lagerkosten

_Substantiv_

Produktpreis, abzüglich Coupons oder Rabatte, zuzüglich Fracht und anfallende Steuern.
Der Durchschnitt wird ermittelt, indem die monatlichen Anfangskosten des Lagers plus die Endkosten des Lagers für den letzten Monat des Zeitraums addiert werden.

_Attribute :_

* _Feld: Produkt, Preise, Bestand_

## B

### Basiswährung

_Substantiv_

Die primäre Währung, die pro Shop-Ansicht für alle Online-Zahlungen verwendet wird.
Geschäfte können Währungen aus mehr als 200 Ländern auf der ganzen Welt akzeptieren.
Die Storefront bietet einen Währungsselektor für mehrere akzeptierte Währungen für ein bestimmtes Land oder Gebietsschema.
Währungssymbole werden in Produktpreisen und Verkaufsdokumenten wie Bestellungen und Rechnungen angezeigt.
Sie können die Währungssymbole nach Bedarf anpassen und die Anzeige des Preises für jeden Shop oder jede Ansicht separat festlegen.

Weitere Informationen: [Währung](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html?lang=de)

_Attribute :_

* _Feld: price_

### Stapelverarbeitung

_Substantiv_

So führen Sie eine Aufgabe aus oder ändern mehrere Elemente gleichzeitig ohne manuelle Wiederholung.

_Attribute :_

* _Feld: programmierung_
* _Synonyme: Massenvorgänge_

### Blockieren

_Substantiv_

Eine Einheit der Seitenausgabe, die einen unverwechselbaren Inhalt - eine Information, ein Benutzeroberflächenelement - alles visuell für den Endbenutzer bzw. die Endbenutzerin greifbar macht.
[Blöcke](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=de) werden durch Module implementiert und bereitgestellt.
Blöcke verwenden Vorlagen zum Generieren von HTML.
Beispiele für Bausteine sind eine Kategorieliste, ein Mini-Warenkorb, Produkt-Tags und eine Produktliste.

[Dynamische Blöcke](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html?lang=de) stellen Inhalte bereit, die auf Logik basieren, z. B. Preisregeln.

Page Builder erweitert die Interaktivität und Erstellung von [Blöcken](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html?lang=de) und [dynamischen Blöcken](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html?lang=de).

_Attribute :_

* _Feld: Commerce-Software_
* _Synonyme: Dynamische Blöcke_
* _Verwandte Begriffe: cms-Block, statischer Block, Container, Layout_

### Marke

_Substantiv, Verb_

Eine eindeutige Kennung, die ein bestimmtes Produkt oder eine bestimmte Gruppe von Produkten durch den Hersteller oder Designer definiert.
Dazu gehören Namensmarken für Kleidung, Geräte, Luxusartikel und so weiter.
Ihr Unternehmen kann auch die Marke sein und Produkte unter mehreren Marken basierend auf der Geschäftseinheit, der Zielgruppe usw. verkaufen.

Verwenden Sie benutzerdefinierte Attribute, um Markeninformationen für Produkte zu speichern.

Bei einigen Erweiterungen und Integrationen kann eine Marke für Ihre Produkte verwendet werden oder erforderlich sein, z. B. Google Shopping Ads Channel und Amazon Sales Channel.

_Attribute :_

* _Feld: business_

### gemauert

_Adjektiv_

Ein Einzelhandelsgeschäft mit einem festen physischen Standort im Gegensatz zu Unternehmen, die virtuell oder ausschließlich über das Internet funktionieren.

Für [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html?lang=de) und [Order Management](#oms) ist dieser Store eine Quelle für die Verfolgung von Produktmengen, Versandaufträgen und die Unterstützung der Abholung im Laden.

_Attribute :_

* _Feld: business, inventory_

### Massenvorgänge

_Substantiv_

Massenvorgänge sind Aktionen, die in großem Umfang durchgeführt werden.
Beispiele für Massenvorgänge sind der Import oder Export von Artikeln, Preisänderungen in großem Maßstab und die Zuweisung von Produkten zu einem Lager.

Weitere Informationen: [DevDocs-Massenvorgänge](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Attribute :_

* _Feld: programmierung_

### Produktpaket

_Substantiv_

Ermöglicht Kunden, ein benutzerdefiniertes Produkt aus verschiedenen Optionen und Konfigurationen zusammenzustellen.
Jedes Element im Bundle ist entweder ein separates einfaches oder ein virtuelles Produkt.

Weitere Informationen: [Konfigurierbare ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html?lang=de)

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: einfaches Produkt, virtuelles Produkt, Produkttypen_

### gebündelte Erweiterung

_Substantiv_

Der Code, der das Verhalten von Adobe Commerce erweitert oder anpasst, wird als gebündelte Erweiterung betrachtet.
Es kann Module, Designs und Sprachpakete enthalten.

_Attribute :_

* _Feld: gebündelte Erweiterung, Erweiterung_
* _Synonyme: extension_
* _Verwandte Begriffe: Erweiterung, Erweiterung im Lieferantenpaket_

## C

### Cache-Backend

_Substantiv_

Speichert Cache-Einträge in einem zweistufigen Backend-System innerhalb des Standard-Frameworks von Zend.
Ein Cache der ersten Ebene ist schnell, z. B. ein APC oder Memcached Backend, aber er ist begrenzt und unterstützt kein Tagging und keine Gruppierung von Cache-Einträgen.
Ein Cache der zweiten Ebene, z. B. ein Dateisystem oder ein Redis-Backend, ist langsamer, unterstützt jedoch Tagging und Gruppierung.

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: Backend_

### Cache-Frontend

_Substantiv_

Gibt an, welche Art von Daten im Cache-Backend gespeichert werden.

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: frontend_

### Cache-Typ

_Substantiv_

Ein Cache speichert Daten, damit zukünftige Aufrufe für diese Daten schneller geladen werden.

Adobe Commerce umfasst die folgenden Typen:
* Konfiguration
* Layouts
* HTML-Ausgabe blockieren
* Sammlungsdaten
* Reflexionsdaten
* Datenbank-DDL-Vorgänge
* Kompilierte Konfiguration
* EAV-Typen und -Attribute
* Kundenbenachrichtigung
* Integrationskonfiguration
* Integrations-API-Konfiguration
* Seiten-Cache (der bekannteste)
* Konfiguration von Web-Services
* Übersetzungen
* Zielregel
* Google-Produkt-Cache
* Scheitelpunkt

Andere Typen können erstellt und definiert werden.

_Attribute :_

* _Feld: programmierung_

### einfangen

_Verb_

Der Prozess der Umwandlung eines autorisierten Bestellbetrags in eine fakturierbare Transaktion.
Transaktionen können erst erfasst werden, wenn eine Genehmigung erteilt wurde, und Genehmigungen können erst erfasst werden, wenn die Waren oder Dienstleistungen versandt wurden.

_Attribute :_

* _Feld: business_
* _Verwandte Begriffe: Autorisierung, Bestellstatus_

### Karteninhaber

_Substantiv_

Eine Person, die von einem Finanzinstitut ermächtigt wurde, Einkäufe auf einem Kreditkartenkonto zu tätigen.

_Attribute :_

* _Feld: business, order_

### Warenkorbregeln

_Substantiv_

Preisregeln, die auf den Warenkorb angewendet werden, und Trigger einer Aktion als Reaktion auf eine Reihe von Bedingungen.
Wird zum Erstellen von Promotions verwendet.

_Attribute :_

* _Feld: Commerce-Software, Preise, Produkt_
* _Verwandte Begriffe: Katalogregeln, Warenkorb_

### Katalog

_Substantiv_

Für Händler stellt der Katalog ihren Produktbestand dar.
Innerhalb der Adobe Commerce-Architektur besteht der Katalog aus Kategorien, Produkten und Produktattributen.

Jeder Commerce-Store verfügt über nur einen Produktkatalog, der von allen Store-Ansichten geteilt wird.
Bei einer Installation mit mehreren Stores kann jeder Store über einen separaten Katalog verfügen oder den Katalog freigeben.
Der aktuelle Store-Katalog wird durch die standardmäßige Root-Kategorie bestimmt, die für den Benutzer in der oberen Navigation (Hauptmenü) des Stores sichtbar ist.
(Der Begriff „Root-Kategorie“ kann verwirrend sein, da die „Root-Kategorie“ eigentlich gar keine Kategorie ist, sondern ein Container für das Menü, das aus Kategorien und Unterkategorien besteht.)

Sie können beliebig viele Stammkategorien erstellen, es kann jedoch immer nur eine (Standard) gleichzeitig verwendet werden.

_Attribute :_

* _Feld: Commerce-Software, Preise, Produkt_
* _Verwandte Begriffe: freigegebener Katalog, Katalogregel_

### Katalogregeln

_Substantiv_

Preisregeln, die auf bestimmte Produkte angewendet werden, und Trigger einer Aktion als Reaktion auf eine Reihe von Bedingungen.
Wird zum Erstellen von Promotions verwendet.

_Attribute :_

* _Feld: Commerce-Software, Preise, Produkt_
* _Verwandte Begriffe: Warenkorbregeln, Katalog_

### Kategorie

_Substantiv_

Eine Gruppe von Produkten, die etwas gemeinsam haben.
Das Hauptmenü des Ladens ist in Kategorien und Unterkategorien von Produkten unterteilt.

_Attribute :_

* _Feld: Commerce-Software, Produkt_

### Auschecken

_Substantiv_

Der Prozess der Erfassung der Zahlungs- und Versandinformationen, die erforderlich sind, um den Kauf von Artikeln im Warenkorb abzuschließen.
Nachdem der Kunde die Informationen geprüft und die Bestellung eingereicht hat, wird eine E-Mail-Bestätigung an den Kunden gesendet.

Checkout bietet viele Optionen und Konfigurationen, die vorkonfiguriert und über Erweiterungen verfügbar sind.

Weitere Informationen: [Checkout-Tutorial](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Attribute :_

* _Feld: Business, Design, Bestellung, Produkt, Programmierung_

### Cloud-Variablen

_Substantiv_

Cloud-Variablen sind Umgebungsvariablen, die für Adobe Commerce in der Cloud-Infrastruktur spezifisch sind und das **`MAGENTO_CLOUD`** Präfix verwenden.

Weitere Informationen: [Cloud-Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=de)

_Attribute :_

* _Feld: cloud_

### CMS-Block

_Substantiv_

Eine spezielle Variante von [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=de), die nur in der Admin erstellt und nicht über Layout-Dateien referenziert werden kann.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Block, statischer Block_

### komplexe Daten

_Substantiv_

Daten, die mit mehreren Produktoptionen verknüpft sind.

_Attribute :_

* _Feld: programmierung_

### Komponente

_Substantiv_

Wird verwendet, um auf ein Modul, Design oder Sprachpaket in Adobe Commerce zu verweisen.

_Attribute :_

* _Feld: Commerce-Software_
* _Synonyme: Komponente_
* _Verwandte Begriffe: UI-Komponente_

### konfigurierbares Produkt

_Substantiv_

Ein konfigurierbares Produkt sieht aus wie ein einzelnes Produkt mit Dropdown-Listen mit Optionen für jede Variante.
Jede Option ist eigentlich ein separates einfaches Produkt mit einer eindeutigen SKU, die es ermöglicht, den Bestand für jede Produktvariante zu verfolgen.
Um einen ähnlichen Effekt zu erzielen, kann ein einfaches Produkt mit benutzerdefinierten Optionen verwendet werden, aber ohne die Möglichkeit, den Bestand für jede Variante zu verfolgen.
Produkte mit mehreren Optionen werden manchmal als zusammengesetzte Produkte bezeichnet.

Obwohl ein konfigurierbares Produkt mehr SKUs verwendet und die Einrichtung anfangs etwas länger dauern kann, kann es Ihnen am Ende Zeit sparen.
Wenn Sie planen, Ihr Unternehmen auszubauen, ist der konfigurierbare Produkttyp möglicherweise eine bessere Wahl für ein Produkt mit mehreren Optionen.

Beispiel: T-Shirts, die in zwei Farben und drei Größen erhältlich sind.
Sechs Varianten müssen als einzelne Produkte erstellt werden (jede mit einer eigenen SKU).
Anschließend werden alle Varianten zu einem konfigurierbaren Produkt hinzugefügt, bei dem Kundinnen und Kunden die Größe und Farbe auswählen und es dann zum Warenkorb hinzufügen können.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produktarten_

### Konversionsrate

_Substantiv_

Der Prozentsatz der Besucherinnen und Besucher, die in Käufer umgewandelt werden.

_Attribute :_

* _Feld: business, order_

### Core-Tier-Skalierung

_Substantiv_

Die Skalierung auf Kernebene umfasst drei Service-Knoten für Datenspeicherung, Cache und Services, z. B. OpenSearch, Elasticsearch, MariaDB und Redis.

_Attribute :_

* _Feld: cloud_

### Gutschriftsanzeige

_Substantiv_

Ein Dokument, das der Händler einem Kunden ausstellt, um einen ausstehenden Saldo aufgrund von Preisaufschlag, Rabatt oder Warenrückgabe abzuschreiben.
Die Mitteilung stellt die Mittel auf dem Konto des Kunden wieder her.

_Attribute :_

* _Feld: business, order_

### Gutschriftskommentar

_Substantiv_

Details, warum dem Kunden ein Gutschriftsbetrag gutgeschrieben wurde.

_Attribute :_

* _Feld: business, order_

### Gutschriftposten

_Substantiv_

Ein fakturierter Artikel, für den ein Händler eine Gutschrift erstellt.

_Attribute :_

* _Feld: business, order_

### Crosssell

_Substantiv, Adjektiv, Verb_

Ein Produkt, das neben dem Warenkorb angezeigt wird.
Wenn ein Kunde zur Warenkorbseite navigiert, werden diese Produkte als Crosssell zu den Artikeln angezeigt, die sich bereits im Warenkorb befinden.
Sie ähneln Impulsverkäufen, wie Magazinen und Süßigkeiten an den Registrierkassen in Lebensmittelläden.

_Attribute :_

* _Feld: business, product_
* _Verwandte Begriffe: Upsell_

### CVM

_Substantiv_

Eine Abkürzung für „Karteninhaber-Verifizierungsmethode“.
Eine Möglichkeit, die Identität des Kunden zu überprüfen, indem ein 3-stelliger oder 4-stelliger Kreditkarten-Sicherheitscode mit dem Zahlungsprozessor bestätigt wird.

_Attribute :_

* _Feld: business, order_
* _Synonyme: Karteninhaber-Verifizierungsmethode_
* _Verwandte Begriffe: Sicherheits-Code_

## D

### Datenbankschema

_Substantiv_

Die Struktur der Daten in einer Datenbank.
Definiert, wie Daten organisiert sind und wie Datenbeziehungen gesteuert werden, einschließlich aller auf die Daten angewendeten Einschränkungen.
Ein Modul kann Fragmente des Datenbankschemas enthalten, wenn dieses Modul Daten enthält, die in der Datenbank gespeichert werden müssen.

_Attribute :_

* _Feld: programmierung_
* _Synonyme: schema_

### Injektion einer Abhängigkeit

_Substantiv_

Ein Software-Design-Muster, das es einer Klasse ermöglicht, ihre Abhängigkeiten anzugeben, ohne sie erstellen zu müssen.
Diese Klasse delegiert die Verantwortung für das Einfügen der Abhängigkeit an die aufrufende Klasse.
Wird verwendet, um das Testen zu vereinfachen.
Um Abhängigkeiten für Klassen zu definieren, bearbeiten Sie die Konfigurationsdatei „di.xml“.

_Attribute :_

* _Feld: programmierung_

### Bereitstellungsschlüssel

_Substantiv_

Ein Bereitstellungsschlüssel ist Ihr öffentlicher SSH-Schlüssel für das Projekt und ermöglicht schreibgeschützten oder (falls aktiviert) Lese-/Schreibzugriff auf ein Git-Repository.

Weitere Informationen: [Sichere Verbindungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de)

_Attribute :_

* _Feld: cloud_

### Double-Opt-in

_Substantiv, Verb_

Ein E-Mail-Verifizierungsprozess, bei dem potenzielle Abonnenten einen zweiten Schritt ausführen müssen, der ihre Absicht bestätigt, sich zu abonnieren.

_Attribute :_

* _Feld: business_

### herunterladbares Produkt

_Substantiv_

Ein digital herunterladbares Produkt, das aus einer oder mehreren heruntergeladenen Dateien besteht, z. B. einem E-Book, Musik, Video, einer Softwareanwendung oder einem Update.
Sie können ein Album zum Verkauf anbieten und jedes Lied einzeln verkaufen.
Ein herunterladbares Produkt kann eine elektronische Version Ihres Produktkatalogs bereitstellen.

Herunterladbare Dateien können sich auf Ihrem -Server befinden oder als URLs zu einem anderen Server oder einem Content Delivery Network bereitgestellt werden.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produktarten_

### Dynamische Inhalte

_Substantiv_

Inhalte, die durch Code generiert werden, anstatt aus einer statischen Vorlage gelesen zu werden.
Nachdem dynamische Inhalte anfänglich gerendert werden, wenn ein Benutzer eine Seite besucht, kann der Inhalt manchmal zwischengespeichert und wiederverwendet werden, ohne dass ein weiterer dynamischer Aufruf bei einem erneuten Besuch erforderlich ist.

_Attribute :_

* _Feld: design_
* _Verwandte Begriffe: php_

### Dynamic Media-URL

_Substantiv_

Eine URL-Adresse, die vom System dynamisch generiert wird, um auf ein Bild oder andere Medien zu verweisen.
Die Adresse verweist direkt auf Assets, die auf einem Server oder in einem Content Delivery Network gespeichert sind.
Um eine statische URL zu verwenden, ändern Sie die Konfigurationseinstellung.
Wenn Dynamic Media-URLs jedoch im Katalog enthalten sind, wenn Sie die Einstellung deaktivieren, wird jeder Verweis im Katalog zu einem fehlerhaften Link.
Links können wiederhergestellt werden, indem Dynamic Media-URLs erneut aktiviert werden.
Die Verwendung von Dynamic Media-URLs kann die Suchleistung im Katalog beeinträchtigen.

Codeformat: media url=&quot;path/to/image.jpg&quot;

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: Content Delivery Network, URL_

## E

### ECE-Tools-Paket

_Substantiv_

Eine Reihe von Skripten und Tools, die zur Verwaltung und Bereitstellung des Commerce-Programms entwickelt wurden. Dieses Paket vereinfacht viele Adobe Commerce-Prozesse in der Cloud-Infrastruktur, einschließlich der Bereitstellung in einer Docker-Umgebung, der Verwaltung von Zuordnungen, der Überprüfung der Projektkonfiguration und der Anwendung von Adobe-Patches.

Weitere Informationen: [ece-tools-Paket](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html?lang=de)

_Attribute :_

* _Feld: cli, cloud, deploy_

### Entität

_Substantiv_

Eine eindeutige Einheit oder ein eindeutiges Objekt in der Programmierung.
Enthält Attribute oder Parameter zum Ändern.
Beispiele sind Staging - bei dem eine Aktualisierung Entitäten wie Preisregeln, Produkte oder Kategorien ändern kann - und Datenbankdatensätze - bei denen Dienstverträge Datenstrukturen enthalten, die gesendet und empfangen werden.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Attribut, Regeln für den Warenkorb, Katalogregeln_

### Entitätsattributwert

_Substantiv_

Für Datenbankentitäten ein Datenmodell, das Entitäten effizient codiert.
Speichert die Entitäts-ID, den Attributnamen und den Wert als Triple, sodass jederzeit neue Entitätsattributnamen erstellt werden können.
Bei der Kodierung kann die Anzahl der Attribute, die zur Beschreibung von Entitäten verwendet werden können, umfassend skaliert werden. Die Anzahl, die für eine bestimmte Entität gilt, wird jedoch minimiert.
Dieses Datenmodell ist flexibel, kann aber langsam sein.

Weitere Informationen: [EAV und extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attribute :_

* _Feld: programmierung_
* _Synonyme: eav_

### Immergrüne Inhalte

_Substantiv_

Inhalte mit langer Haltbarkeit oder wiederverwendbare Inhalte.

_Attribute :_

* _Feld: business_

### Erweiterung

_Substantiv_

Code, der das Verhalten von Adobe Commerce erweitert oder anpasst.
Sie können optional eine Erweiterung in Commerce Marketplace oder einem anderen Erweiterungsverteilungssystem verpacken und verteilen.
Eine Commerce-Erweiterung kann Module, Designs und Sprachpakete enthalten.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Komponente, Modul, Paket_

### Erweiterungsattribut

_Substantiv_

Erweitern Sie die Funktionalität und verwenden Sie häufig komplexere Datentypen als benutzerdefinierte Attribute. Diese Attribute werden nicht auf der Benutzeroberfläche angezeigt.

Weitere Informationen: [Hinzufügen von Erweiterungsattributen zur Entität](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Attribut, Entitätsattributwert_

## F

### Fracht an Bord

_Substantiv_

Im internationalen Versand bedeutet dieser Begriff, dass die empfangende Partei für die Versandkosten verantwortlich ist.
FOB kann auf dem Ursprungs- oder Bestimmungsort basieren und entweder als Fracht abholen oder als Fracht vorausbezahlt gekennzeichnet sein.

_Attribute :_

* _Feld: Geschäft, Bestellung, Preise_
* _Synonyme: fob_

### Frontend

_Adjektiv_

In einer Client-Server-Anwendung gibt es das Backend und das Frontend.
Die Frontend-Komponente (oder Client) ist eine Schnittstelle, die es Benutzern ermöglicht, den zugrunde liegenden Backend-Code zu bearbeiten oder mit ihm zu interagieren.
Backend-Code wird auf einem Server ausgeführt.
Ein Benutzer kann nicht direkt auf den Backend-Code zugreifen.
Ein Benutzer interagiert mit der Storefront, die wiederum Code verwendet, der auf dem Commerce-Server ausgeführt wird.

Hinweis: In der Vergangenheit wurde die Storefront als „Frontend“ und der Admin als „Backend“ bezeichnet. Diese Verwendung wird nicht mehr unterstützt.

_Attribute :_

* _Feld: design, programmierung_
* _Synonyme: Client-Seite_
* _Verwandte Begriffe: Backend, Storefront, Cache-Frontend_

### Frontend-Eigenschaften

_Substantiv_

Eigenschaften, die die Darstellung und das Verhalten eines Attributs aus Sicht des Kunden in Ihrem Store bestimmen.

_Attribute :_

* _Feld: design, programmierung_

### Erfüllung

_Substantiv_

Der Prozess der Verwaltung von Kundensendungen.

_Attribute :_

* _Feld: business_

## G

### Geschenkkarte

_Substantiv_

Eine Prepaid-Karte oder ein Geschenkgutschein, mit dem Einkäufe im Geschäft getätigt werden können.
Jeder Geschenkkarte wird ein eindeutiger Code zugewiesen, der an der Kasse eingegeben wird.
Der Wert der Geschenkkarte wird im Guthaben des Geschenkkartenkontos angezeigt.
Es gibt drei Arten von Geschenkkarten:

* „Physische“ Geschenkkarten können aus Kunststoff oder Kartenvorrat hergestellt und an den Kunden versendet werden.
* „Virtuelle“ Geschenkkarten werden per E-Mail verschickt.
* „Kombinierte“ Geschenkkarten sind eine Kombination aus beiden, die als physische Karte an den Empfänger gesendet und auch per E-Mail zugestellt werden.
Geschenkgutscheine sind konfigurierbar, einschließlich Optionen für die Produkteignung und die Auswahl offener oder fester Beträge.

Eine Geschenkkarte kann auch vom Store-Administrator auf Kundenwunsch eingelöst werden, wenn die Bestellung im Backend erstellt wird.

Geschenkgutscheine helfen auch bei Werbeaktionen, da Geschenkgutscheinadministratoren die Geschenkgutscheinkonten im Backend manuell erstellen und die Geschenkgutscheincodes an das spezifische Kundensegment senden können.
Geschenkgutscheine können als Treueprogramm für die aktivsten Kundinnen und Kunden dienen, die während der Feiertage zahlreiche Käufe im Webstore oder eine bestimmte Werbekampagne tätigen.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Produktarten_

### Bruttomarge

_Substantiv_

Die Differenz zwischen den Kosten und dem Preis eines Produkts.

_Attribute :_

* _Feld: business_

### Produkt in Gruppen

_Substantiv_

Ein Produkttyp mit mehreren ähnlichen, eigenständigen Produkten, die auf einer Seite gruppiert sind.
Kann mit Varianten eines einzelnen Produkts angeboten werden oder indem sie nach Saison oder Thema gruppiert werden, um ein koordiniertes Set zu erstellen.
Jedes Produkt kann separat oder als Teil der Gruppe erworben werden.

Beispielsweise können bei einem Messer, das in vier Größen verfügbar ist, alle vier Messer innerhalb einer gruppierten Produktseite angezeigt werden.
Kunden können die gewünschten Größen auswählen und sie über diese Seite zum Warenkorb hinzufügen.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: einfaches Produkt, Produktarten_

## H

### handhaben

_Substantiv_

Im Allgemeinen ist ein Handle eine Möglichkeit, auf ein Objekt zu verweisen.
In Adobe Commerce werden Handles an vielen Stellen verwendet, am häufigsten zur Identifizierung einer Seite.
Bei Seiten-Handles wird der Handle-Name von der URL abgeleitet und dann verwendet, um die Layout-Dateien für die referenzierte Seite zu suchen und zu laden.
Im Modul Kunde gibt es beispielsweise eine Layout-Datei mit dem Namen &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Hier ist „frontend“ der Bereichsname und „checkout_cart_index“ der Handle-Name, die beide von der URL abgeleitet sind.

_Attribute :_

* _Feld: programmierung_
* _Synonyme: Seiten-Handle_

### horizontale Skalierung

_Substantiv_

Horizontale Skalierung (auch als Skalierung bezeichnet) ist der Prozess des Hinzufügens zusätzlicher Knoten oder Maschinen zu Ihrer Infrastruktur, um den wachsenden Bedarf zu decken.

_Attribute :_

* _Feld: cloud_

## I

### instanceID

_Substantiv_

Siehe [Mandanten-ID](#tenant-id).

_Attribute :_

* _Feld: cloud_
* _Synonyme: Mandanten-ID_

### Abfangen

_Substantiv_

Der Prozess des Einfügens von neuem Code vor, nach oder um eine vorhandene öffentliche Funktion einer PHP-Klasse.

Um eine Funktion abzufangen, implementiert ein Plug-in den zusätzlichen Code, der aufgerufen werden soll.
Plug-ins werden durch die Konfigurationsdatei für die Injektion von Abhängigkeiten (di.xml) mit Abfangpunkten verknüpft.
Wenn mehrere Plug-ins für dieselbe Funktion definiert sind, definiert die Konfiguration der Abhängigkeitseinschleusung die Reihenfolge, in der die Plug-ins aufgerufen werden, sodass mehrere Plug-ins ohne Konflikte verwendet werden können.

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: Plug-in_

## L

### Layout

_Substantiv_

Beim Erstellen einer Commerce-Seite besteht ein Layout aus einer Reihe von Blöcken, die hierarchisch zusammengestellt sind und die Seitenstruktur darstellen.

Seiten-Layout-Dateien konzentrieren sich auf die höchste Ebene der Seitenstruktur (Kopfzeile, Fußzeile, Hauptinhaltsbereich, linke Seitenleiste usw.).
Layout-Dateien stellen dann Inhalte (Blöcke) in diesen verschiedenen Bereichen der Seite zusammen.

_Attribute :_

* _Bereich: Design, Commerce-Software_
* _Verwandte Begriffe: Layout-Anweisungen, Block_

### Layoutanweisungen

_Substantiv_

Markup in einer Layout-Datei, die die Änderungen beschreibt, die auf eine Baumstruktur strukturierter Elemente aus Blöcken, Containern und UI-Komponenten angewendet werden sollen.
Eine einzelne Layout-Datei kann mehrere Layout-Anweisungen enthalten.
Layout-Anweisungen werden in Layout-Dateien in XML kodiert.

_Attribute :_

* _Feld: design, programmierung_
* _Verwandte Begriffe: Layout, Block, Container, UI-Komponente_

### Layout-Aktualisierung

_Substantiv_

Wird für Codeausschnitte verwendet, die hinzugefügt werden, um das XML-Layout zu ändern oder die Layout-Anweisungen aus einer anderen Datei zu importieren.

_Attribute :_

* _Bereich: Design, Commerce-Software_

### Lizenzinhaber

_Substantiv_

Der Lizenzinhaber (auch als Kontoinhaber bezeichnet) ist die benannte Person in einer Geschäftsorganisation, die Zahlungen und andere geschäftliche Probleme für das Adobe Commerce on Cloud Infrastructure-Konto verwaltet.
Diese Person dient als Ansprechpartner für Adobe.
Nachdem ein Unternehmen ein Adobe Commerce on Cloud Infrastructure-Abonnement erworben hat, steht der anfängliche Projekt- und Code-Zugriff nur der als Lizenzinhaber bestimmten Person zur Verfügung.

_Attribute :_

* _Feld: business_

## M

### MAGEID

_Substantiv_

MAGEID ist in der Regel der Rechnungskontakt für das Adobe Commerce-Konto (und möglicherweise nicht der Projektbesitzer des Adobe Commerce on Cloud Infrastructure-Projekts).
Für die Zugriffsberechtigung auf Adobe Commerce und Adobe Commerce auf Cloud-Infrastrukturpakete müssen Sie Zugriffsschlüssel verwenden, die mit einer MAGEID verknüpft sind, der Zugriff auf diese Pakete gewährt wurde.

Weitere Informationen: [Authentifizierungsschlüssel abrufen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=de)

_Attribute :_

* _Feld: Commerce-Software_

### Aufschlag

_Substantiv_

In Marketing und Einzelhandel ein Prozentsatz, der zu den Kosten eines Artikels addiert wird, um den Einzelhandelspreis zu bestimmen.
[Konfigurieren des ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html?lang=de) oder Markdown eines Produkts durch anpassbare Optionen.

In der Entwicklung eine Computersprache, die die Verarbeitung, Darstellung und Formatierung von Text steuert.
Markup-Tags sind Code-Ausschnitte, die einer CMS-Seite oder einem -Block Funktionen oder Inhalte hinzufügen.

_Attribute :_

* _Feld: business, programmierung_
* _Synonyme: Markdown_

### Masterumgebung

_Substantiv_

Auf Adobe Commerce in der Cloud-Infrastruktur verwenden Pro-Projekte eine aktive Platform as a Service (PaaS)-Umgebung namens „master“, die eine Kopie Ihrer Produktionsumgebungsdatenbank und Ihres Webservers enthält.

_Attribute :_

* _Feld: cloud_

### Händlerkonto

_Substantiv_

Ein Konto bei einer Bank oder einem Finanzinstitut, das die Annahme von Kreditkartentransaktionen ermöglicht.

_Attribute :_

* _Feld: business_

### MFTF

_Substantiv_

MFTF ist ein [Funktionstest-Framework](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Es bietet ein Test-Framework für Commerce-Entwickler und Software-Ingenieure wie QA-Spezialisten, PHP-Entwickler und Systemintegratoren.
Entwickler und QA können Tests schreiben, um Benutzerinteraktionen mit Web-Anwendungen auszuprobieren, die Funktionalität zu überprüfen und Regressionstests zu automatisieren.

_Attribute :_

* _Bereich: Commerce-Software, Programmierung_
* _Verwandte Begriffe: cms-Block, statischer Block, Container, Layout_

### Modul

_Substantiv_

Code, der von der Magento-Anwendung bereitgestellte Funktionen ändert oder erweitert.
Ein Modul ist in einer Verzeichnisstruktur enthalten, die PHP- und XML-Dateien (Konfiguration, Bausteine, Controller, Helper, Modelle usw.) enthält, die sich auf eine bestimmte Funktionalität beziehen, um eine bestimmte Sammlung von Produktfunktionen bereitzustellen.
Der Zweck jedes Moduls besteht darin, spezifische Produktfunktionen bereitzustellen, indem neue Funktionen implementiert oder die Funktionalität anderer Module erweitert wird.
Jedes Modul ist so konzipiert, dass es unabhängig funktioniert, sodass das Ein- oder Ausschließen eines bestimmten Moduls die Funktionalität anderer Module nicht beeinträchtigt.

Ein Modul kann auch Widgets implementieren, bei denen es sich um Seitenelemente handelt, die von Geschäftsbenutzern in der Admin angepasst werden können.

Module können deaktiviert oder entfernt werden, ohne dass die Konsistenz des Magento-Programms beeinträchtigt wird.
Eine Ausnahme: Wenn das Modul von anderen Modulen abhängig ist, was erfordert, dass die abhängigen Module deaktiviert oder entfernt werden.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: php, xml, block_

## O

### OMS

_Substantiv_

OMS ist das Order Management-Systemangebot von Adobe.

>[!IMPORTANT]
>
>Adobe Commerce Order Management (OMS) hat das Ende der Lebensdauer erreicht und wird nicht mehr unterstützt.

OMS ist eine flexible und erschwingliche Lösung für die Verwaltung, den Verkauf und die Erfüllung von Lagerbeständen über jeden Vertriebskanal.
OMS bietet ein nahtloses Kundenerlebnis, das den Umsatz steigert und gleichzeitig die Kosten senkt und die Markteinführungszeit beschleunigt.

Zu den OMS-Funktionen gehören:

* Globale Übersicht und Verwaltung des gesamten Bestands
* Möglichkeit zum Versand an und von überall
* Einfacherer und reaktionsschnellerer Kundendienst
* Bessere Kundenerfahrung und Kundenloyalität

Weitere Informationen: [Archivierte OMS-Dokumentations-Site](https://commerce-docs.github.io/oms-documentation-archive/)

_Attribute :_

* _Feld: Funktion, Commerce-Software, Auftragsverwaltung_
* _Synonyme: Order Management, MOM, Order Management System, Magento Order Management_
* _Verwandte Begriffe: Auftragsverwaltung_

### Ursprungsverkleidung

_Substantiv_

Origin Cloaking ist eine Sicherheitsfunktion, mit der Adobe Commerce in der Cloud-Infrastruktur jeden Nicht-Fastly-Traffic blockieren kann, um DDoS-Angriffe zu verhindern, die an die Cloud-Infrastruktur (Herkunft) gesendet werden.

Weitere Informationen: [Fastly Origin Cloaking](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html?lang=de)

_Attribute :_

* _Feld: security_
* _Verwandte Begriffe: Web Application Firewall_

## P

### Page Builder

_Substantiv_

Page Builder ist eine Commerce-Erweiterung zum Erstellen inhaltsreicher Seiten durch Ziehen und Ablegen von vordefinierten Steuerelementen zum Definieren benutzerdefinierter Layouts.
Diese Steuerelemente werden auch als „Inhaltstypen“ bezeichnet.
Händler können Layouts und Seiten ohne Programmiererfahrung entwerfen.
Entwicklerinnen und Entwickler erhalten Unterstützung bei Erweiterungen, um Page Builder zu erweitern.

Weitere Informationen: [Page Builder-Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=de), [Page Builder-DevDocs](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Attribute :_

* _Bereich: Commerce-Software, Design_
* _Synonyme: Admin, Admin-Bedienfeld, Backend, Administration-Benutzeroberfläche, Admin-Benutzeroberfläche_
* _Verwandte Begriffe: admin_

### Zahlungs-Gateway

_Substantiv_

Ein Zahlungs-Gateway ist ein Drittanbieterdienst, der nahtlos Kreditkartentransaktionen verarbeitet, ohne dass der Kunde die Website des Händlers verlässt.

_Attribute :_

* _Feld: business, order, programmierung_

## R

### verwandtes Produkt

_Substantiv_

Eine Auswahl von Produkten, die als Anreiz zum Kauf zusätzlicher Artikel präsentiert wird.
Wenn der Kunde beispielsweise die Produktseite für eine Kamera aufruft, können zu den zugehörigen Produkten andere vergleichbare Kameras, ein Kameratui und ein Stativ gehören.

_Attribute :_

* _Feld: Commerce-Software, Produkt_

## s

### Verkaufsregeln

_Substantiv_

Enthält Regeln für den Warenkorb und den Katalog, mit denen ein Produkt für Werbeaktionen bewertet wird.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Regeln für den Warenkorb, Katalogregeln_

### Umfang

_Substantiv_

In Adobe Commerce beschreibt der Umfang das Ausmaß der Store-Hierarchie, das eine Einstellung beeinflussen kann.
Der Umfang kann auf Folgendes angewendet werden:

* Global - alle Websites, Stores und Store-Ansichten
* Website - die ausgewählte Website und alle Stores und Store-Ansichten darunter
* Store - der ausgewählte Store und alle darunter liegenden Store-Ansichten
* Shop-Ansicht - die ausgewählte Shop-Ansicht.

Innerhalb der Hierarchie können Einstellungen, die auf einer niedrigeren Ebene angewendet werden, einige Einstellungen einer höheren Ebene überschreiben.

_Attribute :_

* _Feld: Commerce-Software_

### Dienstvertrag

_Substantiv_

Ein Satz von PHP-Schnittstellen, die für ein Modul definiert sind.
Ein Dienstvertrag umfasst Datenschnittstellen, die die Datenintegrität wahren, und Dienstschnittstellen, die Geschäftslogikdetails vor Dienstanforderern wie Controllern, Webdiensten und anderen Modulen ausblenden.
Web-APIs können über Konfigurationsdateien an Dienstverträge gebunden werden.

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: php, Web-API_

### Abrechnung

_Substantiv_

Die Abrechnung erfolgt, wenn die Händlerbank und der Emittent Geldbeträge austauschen und die Erlöse auf das Händlerkonto einzahlen.

_Attribute :_

* _Feld: business_

### Shared CATALOG

_Substantiv_

Eine Funktion, mit der Händler einen Katalog erstellen können, der als ganzer Katalog oder als Untergruppe davon dienen kann, und dann benutzerdefinierte Preise für ein oder mehrere Produkte zuweisen.
Händler können diesen Katalog dann einem oder mehreren Unternehmen zuweisen.

So hat ein B2B-Händler beispielsweise drei Kunden, die bestimmte Tarife für die Elektronikvertriebsstelle des Händlers ausgehandelt haben.
Mit der Funktion „Freigegebener Katalog“ verfügt der Händler über:

* Ein Hauptkatalog
* Ein Kunden-1-Katalog (möglicherweise nur drei SKUs mit hohen Rabatten für sie im Hauptkatalog)
* Katalog für Kunde 2 (kann der gesamte Katalog mit 10 % Rabatt sein)
* Customer 3-Katalog (einige Dutzend Produkte mit Rabatten von 5 % bis 60 % gegenüber dem Hauptkatalog).

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Katalog, b2b_

### Versand

_Substantiv_

Eine Sendung enthält zu liefernde Produkte und generiert eine Aufzeichnung der Produkte in einer Bestellung, die versendet wurden.
Einer Bestellung können mehrere Sendungen zugeordnet werden.

_Attribute :_

* _Feld: business, order_

### Lieferschein

_Substantiv_

Ein Dokument, das eine Sendung begleitet. Das Dokument listet die Produkte und ihre Mengen im Lieferpaket auf.

_Attribute :_

* _Feld: business, order_

### Spediteur

_Substantiv_

Ein Unternehmen, das Pakete transportiert. Häufige Spediteure sind UPS, FedEx, DHL und USPS.

_Attribute :_

* _Feld: business, order_

### Warenkorb

_Substantiv_

Die Produktgruppe, die ein Kunde ausgewählt hat, aber noch nicht gekauft hat.
Bezieht sich auch auf einen Bereich einer E-Commerce-Website, in dem diese Produkte zum Überprüfen und Checkout gefunden werden können.

_Attribute :_

* _Bereich: Business, Design, Produkt, Programmierung_
* _Synonyme: Warenkorb, Warenkorb_
* _Verwandte Begriffe: Regeln für den Warenkorb_

### einfaches Erzeugnis

_Substantiv_

Der einfachste Produkttyp, ein physisches Element mit einer einzelnen SKU.
Einfache Produkte verfügen über verschiedene Preis- und Eingabesteuerungen, die es ermöglichen, Varianten des Produkts zu verkaufen.
Einfache Produkte können in Verbindung mit gruppierten, gebündelten und konfigurierbaren Produkten verwendet werden.
Ein einfaches Produkt mit benutzerdefinierten Optionen wird manchmal als zusammengesetztes Produkt bezeichnet.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produktarten_

### SKU

_Substantiv_

Abkürzung für Stock Keeping Unit.
Eine Zahl oder ein Code, der einem Produkt zugewiesen wird, um das Produkt, die Optionen, den Preis und den Hersteller zu identifizieren.

_Attribute :_

* _Feld: Business, Preisgestaltung, Produkt, Programmierung_
* _Verwandte Begriffe: freigegebener Katalog_

### Begrüßungsseite

_Substantiv_

Eine Werbeseite mit einem Produkt oder einer Werbung, die normalerweise vor der Startseite angezeigt wird.

_Attribute :_

* _Feld: design_

### statischer Block

_Substantiv_

Eine modulare Inhaltseinheit, die von einem Benutzer in der CMS auf einer Seite platziert werden kann, um Text und Bilder anzuzeigen oder Code-Ausschnitte auszuführen.
Statische Blöcke enthalten bearbeitbare Inhalte und können als Landingpages für Produktkategorien fungieren.
Widgets können zu statischen Blöcken hinzugefügt werden, um zusätzliche Funktionen bereitzustellen.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: cms-Block, block_

### Statischer Inhalt

_Substantiv_

Benutzergenerierte Inhalte (nicht vom Code generiert), die sich nicht häufig ändern.

_Attribute :_

* _Feld: design_
* _Verwandte Begriffe: dynamische Inhalte_

### Statische Dateien

_Substantiv_

Die Sammlung von Assets wie CSS, Schriftarten, Bildern und JavaScript, die von einem Design verwendet wird.

_Attribute :_

* _Feld: Commerce-Software_

### store

_Substantiv_

Die Commerce-Bereichsebene von „Store“ ist die zweite Ebene der Hierarchie Ihrer Website, die wie folgt aussieht: Website > Store > Store-Ansicht.
Läden können in einem oder mehreren Gruppen organisiert werden. Jeder Store verfügt potenziell über eine eigene Stammkategorie und gibt alle Katalog- und Kundendaten frei.

Jeder Store kann über mehrere Store-Ansichten verfügen, die normalerweise verwendet werden, um die Storefront in einem anderen Gebietsschema und in einer anderen Sprache darzustellen.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Store-Ansicht, Website_

### Shop-Ansicht

_Substantiv_

Die Commerce-Bereichsebene „Store-Ansicht“ bezieht sich auf die dritte Ebene in der Hierarchie der Websites, Stores und Store-Ansichten.
Store-Ansichten präsentieren die Storefront normalerweise in einem anderen Gebietsschema und in einer anderen Sprache.
Um die Store-Ansichten zu ändern, verwenden Sie die Store-Auswahl in der Kopfzeile.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Store, Website_

### Schaufenster

_Substantiv_

Der Online-Store, den Kundinnen und Kunden beim Besuch Ihrer Commerce-Site erleben.

_Attribute :_

* _Feld: Commerce-Software, Produkt_

## T

### Steuervorschrift

_Substantiv_

Eine Kombination aus einer Produkt-Steuerklasse, einer Kunden-Steuerklasse und einem Steuersatz. Diese Regel definiert, welche Steuerberechnung angewendet wird.

_Attribute :_

* _Feld: business_

### Vorlage

_Substantiv_

Abkürzung für HTML-Vorlage oder PHTML-Vorlage.
Eine PHTML-Datei enthält eine Mischung aus HTML-Markup und PHP-Code, um dynamische Inhalte in die HTML einzufügen.
Die meisten Blöcke verfügen über mindestens eine PHTML-Datei (Vorlage), die die vom Block generierte statische HTML enthält.
In den Admin-, E-Mail- und Newsletter-Vorlagen werden Text, Bilder und Variablen mit HTML-Markup kombiniert, um personalisierte Inhalte zu erstellen, die vom System gesendet werden.

_Attribute :_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: block_

### Mandanten-ID

_Substantiv_

Eine Adobe Commerce-Mandanten-ID ist eine eindeutige Kennung für Ihre spezifische Adobe Commerce-Instanz in der Adobe Experience Cloud.
wird verwendet, um Daten zu routen und sicherzustellen, dass die Ressourcen korrekt mit dem Namespace versehen sind, insbesondere für Integrationen und APIs. Sie finden die Mandanten-ID
in den Zugriffs-URLs für Ihre Commerce-Instanz oder über die Commerce Cloud Manager-Instanzdetails.

Weitere Informationen:

[Grundlagen zu Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/de/docs/commerce/cloud-service/getting-started#adobe-commerce-as-a-cloud-service-basics)
[Erste Schritte mit Adobe Commerce Optimizer](https://experienceleague.adobe.com/de/docs/commerce/optimizer/get-started#manage-instances)

_Attribute :_

* _Feld: cloud_
* _Synonyme: Instanz-ID_

### Thema

_Substantiv_

Enthält Grafik- und Erscheinungsbildinformationen.
Passt das Erscheinungsbild des Stores an.
Adobe Commerce kann Designs in (Composer)-Paketen bereitstellen.
Designs können jedoch unter App/Design platziert werden, das nicht im Paket bereitgestellt wird.
Pakete sind die Download-Einheit für Composer, und über Commerce Marketplace können Commerce-Benutzer CE oder EE als eine Serie von Paketen herunterladen, wobei Pakete Module, Themen oder Sprachpakete enthalten.

_Attribute :_

* _Feld: Commerce-Software_

## U

### UI-Komponente

_Substantiv_

Ein Tag, das für die Adobe Commerce-Software entwickelt wurde, um ein einfacheres und flexibleres Rendern der Benutzeroberfläche zu ermöglichen.
Die Ziele des Benutzeroberflächen-Komponentensystems umfassen Folgendes:

* Vereinfachen des Layouts zur Handhabung von XML-Dateien
* Verschieben von Elementen der Admin-Benutzeroberfläche von HTML+JavaScript in ein benutzerdefiniertes Widget-System des Typs „reines JavaScript&quot;
* Ermöglichen der Erstellung komplexerer UI-Komponenten aus kleineren Komponenten
* Vorrendern von Daten für Benutzeroberflächenkomponenten als JSON, enge Bindung an Backend-Datenobjekte
* Verwenden von AJAX zum Aktualisieren von Komponentendaten
* Einführung einer neuen DSL für die Erstellung der oben genannten Elemente

Weitere Informationen: [Handbuch zu Benutzeroberflächen](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=de)

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: JavaScript, Layout, Komponente, Page Builder_

### NACH OBEN

_Substantiv_

[PWA Studio](https://github.com/magento/pwa-studio) verwendet [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) in der Entwicklung.
UPWARD ist ein Akronym für Unified Progressive Web App Response Definition.
Eine UPWARD-Definitionsdatei beschreibt, wie ein Webserver eine Progressive Web Application bereitstellt und unterstützt.

UPWARD-Definitionsdateien liefern Details zum Serververhalten mit plattformunabhängiger, deklarativer Sprache.
Dadurch kann eine Progressive Web Application auf einem UPWARD-kompatiblen Server in jeder beliebigen Sprache auf jedem Technologie-Stack ausgeführt werden, da die Anwendung nur das HTTP-Endpunktverhalten vom UPWARD-Server berücksichtigt.

Ein UPWARD-Server verwendet eine Definitionsdatei, um den entsprechenden Prozess oder Service für eine Anforderung von einer Anwendungs-Shell zu ermitteln.
Darin wird beschrieben, wie der Server eine Anfrage verarbeiten und die Antwort dafür erstellen soll.

Ein PWA-Projekt kann eine UPWARD-Definitionsdatei enthalten, um die Service-Abhängigkeiten anzugeben.

_Attribute :_

* _Bereich: Design, Commerce-Software, Programmierung_
* _Synonyme: PWA Studio, Unified Progressive Web App Response Definition_
* _Verwandte Begriffe: pwa_

## V

### Vom Anbieter gebündelte Erweiterung

_Substantiv_

Vom Anbieter erstellter Code, der das Verhalten von Commerce erweitert oder anpasst und als Drittanbietererweiterung funktioniert, wird als VBE (Vendor Bundled Extension) betrachtet.
VBEs werden gründlich getestet und in jeder unterstützten Version von Adobe Commerce enthalten.
Eine VBE kann Module, Designs und Sprachpakete enthalten.

Weitere Informationen finden Sie unter [Thema zur Bundle-Erweiterung für Anbieter](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html?lang=de).

_Attribute :_

* _Feld: Commerce-Erweiterung, Anbieter-gebündelte Erweiterung, Erweiterung, VBE_
* _Synonyme: extension, VBE_
* _Verwandte Begriffe: Erweiterung, gebündelte Erweiterung_

### vertikale Skalierung

_Substantiv_

Vertikale Skalierung (Hochskalierung) bezieht sich auf die Erhöhung der Verarbeitungsleistung eines einzelnen Servers oder Clusters durch Hinzufügen von Festplatten- oder Netzwerk-E/A, CPUs oder RAM.

_Attribute :_

* _Feld: environment_

### virtuelles Produkt

_Substantiv_

Stellt ein nicht physisches Produkt dar, das verkauft werden kann, z. B. eine Mitgliedschaft, ein Service, eine Garantie oder ein Abonnement.
Virtuelle Produkte können einzeln verkauft oder als Teil der folgenden Produkttypen enthalten sein: gruppiertes Produkt und gebündeltes Produkt.
Erfordert weder Versand noch Inventar.

Der Prozess der Erstellung eines virtuellen Produkts und eines einfachen Produkts ist nahezu identisch.
Da ein virtuelles Produkt jedoch nicht ausgeliefert wird, gibt es kein Gewichtsfeld oder eine Option, um eine Geschenkkarte einzuschließen.

_Attribute :_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produktarten_

### Virtueller Typ

_Substantiv_

Virtuelle Typen sind eine Möglichkeit, verschiedene Abhängigkeiten in bestehende PHP-Klassen einzufügen, ohne andere Klassen zu beeinflussen und ohne eine Klassendatei erstellen zu müssen.
Auf virtuelle Typen kann nur durch Argumentüberschreibungen in einem `<type>`-Element innerhalb von di.xml-Dateien verwiesen werden, niemals im Quellcode.
Sie können nicht erweitert werden und sie können keine Verweise als Abhängigkeiten in einem Klassenkonstruktor sein.

_Attribute :_

* _Feld: programmierung_
* _Verwandte Begriffe: php_

## W

### Website

_Substantiv_

In der Adobe Commerce-Software die höchste Ebene einer Website-Hierarchie über der Store- und Store-Ansicht.
Sie können mehrere Websites haben, und jede Website kann einen anderen Domain-Namen haben.
Websites können so eingerichtet werden, dass Kundendaten gemeinsam genutzt oder nicht gemeinsam genutzt werden.

_Attribute :_

* _Bereich: Commerce-Software, Design, Produkt_
* _Verwandte Begriffe: store, store view_

### Widget

_Substantiv_

Ein [Widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html?lang=de) ist ein vorbereiteter Code-Ausschnitt, der verwendet werden kann, um Blöcke, Links und dynamische Inhalte an bestimmten Stellen auf Speicherseiten zu platzieren.
Sie können Widgets verwenden, um Landingpages für Marketing-Kampagnen zu erstellen und Werbeinhalte an bestimmten Stellen im gesamten Store anzuzeigen.
Widgets können auch verwendet werden, um interaktive Elemente und Aktionsblöcke für externe Überprüfungssysteme, Videochats, Abstimmungs- und Abonnementformulare hinzuzufügen oder Navigationselemente für Tag-Clouds und Bild-Regler bereitzustellen.

_Attribute :_

* _Bereich: Business, Commerce-Software, Design_
* _Verwandte Begriffe: block_
