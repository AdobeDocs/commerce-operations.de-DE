---
source-git-commit: 405c1d7073e5936aefc7fb3c6eb1d5dd4d69a066
workflow-type: tm+mt
source-wordcount: '6574'
ht-degree: 0%

---
# Adobe Commerce-Glossar

## A

### oberhalb der Kante

_adjektiv_

In einem Browserfenster wird der Inhalt, der unmittelbar nach dem Laden einer Webseite und vor dem Scrollen eines Benutzers auf der Seite sichtbar ist, angezeigt.
Verwenden Sie beim Entwerfen Ihres Layouts flexible Formate, um in diesem Bereich Produkte, Funktionen, Verkäufe, Benachrichtigungen, Optionen usw. mit der höchsten Priorität anzuzeigen.

Bei Mobil- und Tablets unterscheidet sich der Bereich über der Kante stark, insbesondere in Bezug auf die Größe und Abmessungen des Bildschirms und die Ausrichtung bei der Anzeige (Hochformat vs. Querformat).
Die Verwendung responsiver Designs und Tests kann dabei helfen, die richtige Mischung aus Inhalt und Layout zu finden.

_Begriffsattribute:_

* _Feld: Design_

### aktive Verzweigung

_noun_

Eine aktive Verzweigung oder Umgebung ist eine, die mit einer bereitgestellten oder ausgeführten Instanz mit Zugriff auf Dienste verbunden ist.
Wenn Sie deaktivieren, wird die Verbindung zu den Diensten und zur laufenden Instanz entfernt, der Code wird jedoch beibehalten.
Es wird zu einem normalen Git-Zweig.

_Begriffsattribute:_

* _Feld: cloud_

### Adapter

_noun_

Eine Klasse, die es ermöglicht, zwei ansonsten inkompatible Systeme zusammenzuarbeiten, ohne den Quellcode des Systems zu ändern.
Beispiele sind Datenbankadapter, Cache-Adapter, Dateisystemadapter, Adapter für Postprozessor-Bibliotheken und andere Typen von Computer-Adaptern.

_Begriffsattribute:_

* _Feld: Programmiersprache_

### admin

_noun_

Bei Software: eine Benutzerrolle mit vollen Administratorrechten für die Verwaltung aller Funktionen.
In Adobe Commerce verfügen Admin-Benutzer über vollständige Berechtigungen und Zugriff auf alle Funktionen, Optionen und Funktionen des Administrators.
Sie können auch Benutzer und Rollen erstellen.

Weitere Informationen: [Benutzer hinzufügen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Synonyme: administrator, super user_
* _Verwandte Begriffe: Commerce-Admin_

### Admin-Bereich

_noun_

Das kennwortgeschützte Backoffice Ihres Stores, in dem Bestellungen, Katalog, Inhalt und Konfigurationen verwaltet werden.
Benutzer greifen auf den Admin-Bereich zu, um den Store zu verwalten, einschließlich Produkten, Bestellungen, Sendungen, CMS-Inhalten, Design der Storefront, Kundeninformationen usw.
Admin-Benutzer haben eine zugehörige Rolle mit Berechtigungen, die den Zugriff auf Funktionen, Optionen und Funktionen steuern.

Weitere Informationen: [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Synonyme: Admin, Admin Panel, Backend, Administrationsoberfläche, Admin-Benutzeroberfläche_
* _Verwandte Begriffe: admin_

### ADMIN-Variablen

_noun_

ADMIN-Variablen sind Projektumgebungsvariablen, mit denen die Konfigurationseinstellungen für das Admin-Benutzerkonto für den Zugriff auf die Admin-Benutzeroberfläche außer Kraft gesetzt werden.

Weitere Informationen: [ADMIN-Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Begriffsattribute:_

* _Feld: Admin, Cloud_

### adminhtml

_noun_

Der dem Administrator zugewiesene interne Bereichsname.

Weitere Informationen: [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Bereich, Commerce-Administrator_

### area

_noun_

Bereich ist ein abstrakter Begriff für den Anwendungsbereich eines Magentos.
Bereiche sind logische Komponenten, die Code für eine optimierte Anforderungsverarbeitung organisieren.
Bereiche reduzieren die Speicheranforderungen von Konfigurationsobjekten, auf die über die Storefront zugegriffen wird, und optimieren Webdienstaufrufe, indem nur der erforderliche abhängige Code geladen wird.
Jeder Bereich kann einen völlig anderen Code zur Verarbeitung von URLs und Anforderungen enthalten.

Zu den Adobe Commerce-Bereichen gehören:

* Admin (adminhtml)
* Storefront
* Web API REST (webapi_rest)

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Commerce-Komponente, Storefront_

### attribute

_noun_

Ein Merkmal oder eine Eigenschaft eines Produkts, das einen Aspekt des Produkts beschreibt.
Adobe Commerce- oder Magento Open Source-Benutzer können benutzerdefinierte Attribute erstellen, um sie dem standardmäßigen Attributsatz oder einem benutzerdefinierten Attributsatz hinzuzufügen.
Erstellen Sie diese Attribute über den Administrator oder programmgesteuert.
Beispiele: Farbe, Größe, Gewicht, Preis, Alter, Geschlecht usw.

Benutzerdefinierte Attribute sind ein Typ des Attributs &quot;Entity-Attribute-Value&quot;(EAV).

Bei Integrationen wie Google Shopping Ads Channel und Amazon Sales Channel ordnen Sie Commerce-Attribute Attributen Attributen im Drittanbieter zu, um Produkte ordnungsgemäß anzuzeigen und zu verkaufen, Anzeigen anzuzeigen.

Weitere Informationen: [EAV und Erweiterungsattribute](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Synonyme: Produktattribut, benutzerdefiniertes Attribut_
* _Verwandte Begriffe: Erweiterungsattribut_

### Attributgruppe

_noun_

Eine logische Gruppierung von Attributen innerhalb eines Attributsatzes.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: attribute_

### Attributset

_noun_

Eine Sammlung von Attributgruppen, die für ein bestimmtes Produkt angepasst sind.
Beispiel: Ein T-Shirt-Attributsatz kann Farbe, Größe, Geschlecht und Marke enthalten.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: attribute_

### durchschnittliche Lagerkosten

_noun_

Produktpreis, abzüglich Gutscheine oder Rabatte, zuzüglich Fracht und anwendbaren Steuern.
Der Durchschnitt wird ermittelt, indem die Anfangskosten des Bestands jeden Monat zuzüglich der Endkosten des Bestands für den letzten Monat des Zeitraums hinzugefügt werden.

_Begriffsattribute:_

* _Feld: Produkt, Preis, Bestand_

## B

### Basiswährung

_noun_

Die Primärwährung, die pro Store-Ansicht für alle Online-Zahlungen verwendet wird.
Geschäfte können Währungen aus über 200 Ländern auf der ganzen Welt aufnehmen.
Die Storefront bietet eine Währungsauswahl für mehrere akzeptierte Währungen für ein bestimmtes Land oder Gebietsschema.
Währungssymbole erscheinen in Produktpreisen und Verkaufsunterlagen wie Bestellungen und Rechnungen.
Sie können die Währungssymbole nach Bedarf anpassen und die Anzeige des Preises für jeden Store oder jede Ansicht separat festlegen.

Weitere Informationen: [Währung](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Begriffsattribute:_

* _Feld: Preise_

### Stapelverarbeitung

_noun_

Um eine Aufgabe auszuführen oder mehrere Elemente gleichzeitig zu ändern, ohne manuelle Wiederholung.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Synonyme: Massenvorgänge_

### block

_noun_

Eine Einheit der Seitenausgabe, die bestimmte Inhalte (Informationen, Elemente der Benutzeroberfläche) visuell für den Endbenutzer darstellt.
[Blöcke](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) werden von Modulen implementiert und bereitgestellt.
Blöcke verwenden Vorlagen zum Generieren von HTML.
Beispiele für Bausteine sind eine Kategorienliste, ein Mini-Warenkorb, Produkt-Tags und die Produktliste.

[Dynamische Blöcke](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) Inhalte basierend auf Logik bereitstellen, z. B. Preisregeln.

Der Seitenaufbau erweitert die Interaktivität und Erstellung von [Bausteine](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) und [dynamische Blöcke](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Synonyme: Dynamische Blöcke_
* _Verwandte Begriffe: cms-Block, statischer Block, Container, Layout_

### Marke

_noun, verb_

Eine eindeutige Identität, die ein bestimmtes Produkt oder eine bestimmte Produktgruppe durch den Hersteller oder Designer definiert.
Dazu gehören Namensmarken für Kleidung, Geräte, Luxusartikel usw.
Ihr Unternehmen kann auch die Marke sein, Produkte unter mehreren Marken verkaufen, die auf der Geschäftseinheit, der Zielgruppe usw. basieren.

Verwenden Sie benutzerdefinierte Attribute, um Markeninformationen für Produkte zu speichern.

Einige Erweiterungen und Integrationen können eine Marke für Ihre Produkte verwenden oder erfordern, z. B. Google Shopping Ads Channel und Amazon Sales Channel.

_Begriffsattribute:_

* _Feld: Business_

### Ziegel und Mörtel

_adjektiv_

Ein Einzelhandelsgeschäft mit festem physischen Standort, im Gegensatz zu Unternehmen, die praktisch oder ausschließlich über das Internet funktionieren.

Für [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) und [Auftragsverwaltung](https://omsdocs.magento.com/getting-started/terminology/), ist dieser Speicher eine Quelle für die Nachverfolgung von Produktmengen, Versandaufträgen und die Unterstützung der In-store-Abholung.

_Begriffsattribute:_

* _Feld: Geschäft, Inventar_

### Massenvorgänge

_noun_

Massenvorgänge sind Aktionen, die in großem Maßstab ausgeführt werden.
Zu den Aufgaben des Massenvorgangs gehören beispielsweise der Import oder Export von Artikeln, die Preisänderung in großem Maßstab und die Zuordnung von Produkten zu einem Lager.

Weitere Informationen: [Massenvorgänge von DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Begriffsattribute:_

* _Feld: Programmiersprache_

### Paket-Produkt

_noun_

Ermöglicht es Kunden, aus verschiedenen Optionen und Konfigurationen ein benutzerdefiniertes &quot;eigenes&quot;Produkt zu erstellen.
Jedes Element im Bundle ist entweder ein separates einfaches oder virtuelles Produkt.

Weitere Informationen: [Konfigurierbare Produkte](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: einfaches Produkt, virtuelles Produkt, Produktarten_

### gebündelte Erweiterung

_noun_

Der Code, der das Adobe Commerce-Verhalten erweitert oder anpasst, gilt als gebündelte Erweiterung.
Sie kann Module, Designs und Sprachpakete enthalten.

_Begriffsattribute:_

* _Feld: gebündelte Erweiterung, Erweiterung_
* _Synonyme: Erweiterung_
* _Verwandte Begriffe: Erweiterung, Lieferantenpaketerweiterung_

## C

### Cache-Backend

_noun_

Speichert Cache-Datensätze in einem zweistufigen Backend-System innerhalb des Standard-Frameworks von Zend.
Ein Cache der ersten Ebene ist schnell - z. B. ein APC- oder Memcached-Backend - aber er ist begrenzt und unterstützt kein Tagging und Gruppieren von Cache-Einträgen.
Ein Cache der zweiten Ebene, z. B. ein Dateisystem oder ein Redis-Backend, ist langsamer, unterstützt jedoch Tagging und Gruppierung.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: Backend_

### Cache-Frontend

_noun_

Gibt an, welche Art von Daten im Cache-Backend gespeichert wird.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: frontend_

### Cache-Typ

_noun_

Ein Cache speichert Daten, damit zukünftige Aufrufe für diese Daten schneller geladen werden.

Adobe Commerce umfasst die folgenden Typen:
* Konfiguration
* Layouts
* Blockausgabe HTML
* Sammlungsdaten
* Reflexionsdaten
* Datenbank-DDL-Vorgänge
* Kompilierte Konfiguration
* EAV-Typen und -Attribute
* Kundenbenachrichtigung
* Integrationskonfiguration
* Integrations-API-Konfiguration
* Seiten-Cache (der bekannteste)
* Web-Services-Konfiguration
* Übersetzungen
* Zielregel
* Google-Produktcache
* Vertex

Andere Typen können erstellt und definiert werden.

_Begriffsattribute:_

* _Feld: Programmiersprache_

### erfassen

_verb_

Der Prozess der Umwandlung eines genehmigten Bestellbetrags in eine abrechnungsfähige Transaktion.
Transaktionen können erst mit Genehmigung erfasst werden, und die Genehmigungen können erst nach dem Versand der Waren oder Dienstleistungen erfasst werden.

_Begriffsattribute:_

* _Feld: Business_
* _Verwandte Begriffe: Bewilligung, Bestellstatus_

### Karteninhaber

_noun_

Eine Person, die von einem Finanzinstitut befugt ist, auf einem Kreditkartenkonto Einkäufe zu tätigen.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Warenkorbregeln

_noun_

Preisregeln, die auf den Warenkorb angewendet werden, und Trigger einer Aktion als Reaktion auf eine Reihe von Bedingungen.
Wird zum Erstellen von Promotions verwendet.

_Begriffsattribute:_

* _Feld: Commerce-Software, Preise, Produkt_
* _Verwandte Begriffe: Katalogregeln, Warenkorb_

### Katalog

_noun_

Für Händler stellt der Katalog ihr Produktinventar dar.
Innerhalb der Adobe Commerce-Architektur besteht der Katalog aus Kategorien, Produkten und Produktattributen.

Jeder Commerce-Store hat nur einen Produktkatalog, der von allen Store-Ansichten gemeinsam genutzt wird.
In einer Installation mit mehreren Stores kann jeder Store über einen separaten Katalog verfügen oder den Katalog freigeben.
Der aktuelle Store-Katalog wird durch die standardmäßige Stammkategorie bestimmt, die dem Benutzer in der oberen Navigation (Hauptmenü) des Stores angezeigt wird.
(Der Begriff &quot;Stammkategorie&quot;kann verwirrend sein, da die &quot;Stammkategorie&quot;überhaupt keine Kategorie ist, sondern ein Container für das Menü, der aus Kategorien und Unterkategorien besteht.)

Sie können beliebig viele Stammkategorien erstellen, es kann jedoch jeweils nur eine (die Standardeinstellung) verwendet werden.

_Begriffsattribute:_

* _Feld: Commerce-Software, Preise, Produkt_
* _Verwandte Begriffe: freigegebener Katalog, Katalogregel_

### Katalogregeln

_noun_

Preisregeln, die auf bestimmte Produkte angewendet werden, und Trigger einer Aktion als Reaktion auf eine Reihe von Bedingungen.
Wird zum Erstellen von Promotions verwendet.

_Begriffsattribute:_

* _Feld: Commerce-Software, Preise, Produkt_
* _Verwandte Begriffe: Warenkorbregeln, Katalog_

### category

_noun_

Eine Gruppe von Produkten, die etwas gemeinsam haben.
Das Hauptmenü des Stores ist in Kategorien und Unterkategorien von Produkten unterteilt.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_

### Kasse

_noun_

Der Prozess der Erhebung der Zahlung und Versandinformationen, die erforderlich sind, um den Kauf von Artikeln im Warenkorb abzuschließen.
Nachdem der Kunde die Informationen überprüft und die Bestellung übermittelt hat, wird eine E-Mail-Bestätigung an den Kunden gesendet.

Der Checkout verfügt über zahlreiche Optionen und Konfigurationen, die standardmäßig und über die Erweiterung verfügbar sind.

Weitere Informationen: [Checkout-Tutorial](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Begriffsattribute:_

* _Feld: Business, Design, Bestellung, Produkt, Programmierung_

### Cloud-Variablen

_noun_

Cloud-Variablen sind Umgebungsvariablen, die für Adobe Commerce in der Cloud-Infrastruktur spezifisch sind und die **`MAGENTO_CLOUD`** -Präfix.

Weitere Informationen: [Cloud-Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Begriffsattribute:_

* _Feld: cloud_

### CMS-Block

_noun_

Eine spezielle Variante von [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) , die nur im Admin erstellt werden können und nicht über Layout-Dateien referenziert werden können.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Block, statischer Block_

### komplexe Daten

_noun_

Daten, die mit mehreren Produktoptionen verknüpft sind.

_Begriffsattribute:_

* _Feld: Programmiersprache_

### component

_noun_

Wird verwendet, um auf ein Modul-, Design- oder Sprachpaket in Adobe Commerce zu verweisen.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Synonyme: component_
* _Verwandte Begriffe: ui-Komponente_

### konfigurierbares Produkt

_noun_

Ein konfigurierbares Produkt sieht aus wie ein einzelnes Produkt mit Dropdown-Listen mit Optionen für jede Variante.
Jede Option ist eigentlich ein separates einfaches Produkt mit einer eindeutigen SKU, die es ermöglicht, das Inventar für jede Produktvariante zu verfolgen.
Um einen ähnlichen Effekt zu erzielen, kann ein einfaches Produkt mit benutzerdefinierten Optionen verwendet werden, jedoch ohne die Möglichkeit, Inventar für jede Variante zu verfolgen.
Produkte mit mehreren Optionen werden manchmal auch als zusammengesetzte Produkte bezeichnet.

Obwohl ein konfigurierbares Produkt mehr SKUs verwendet und die Einrichtung zunächst etwas länger dauern kann, kann es am Ende Zeit sparen.
Wenn Sie Ihr Unternehmen erweitern möchten, ist der konfigurierbare Produkttyp möglicherweise eine bessere Wahl für ein Produkt mit mehreren Optionen.

Beispiel: T-Shirts, die in zwei Farben und drei Größen erhältlich sind.
Sechs Varianten müssen als einzelne Produkte erstellt werden (jede mit eigener SKU).
Anschließend werden alle Varianten zu einem konfigurierbaren Produkt hinzugefügt, in dem Kunden die Größe und Farbe auswählen und dann zum Warenkorb hinzufügen können.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produkttypen_

### Konversionsrate

_noun_

Der Prozentsatz der Besucher, die in Käufer umgewandelt werden.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Skalierung auf der Kernebene

_noun_

Die Skalierung der Kernstufe besteht aus drei Dienstknoten für Datenspeicherung, Cache und Dienste wie OpenSearch, Elasticsearch, MariaDB, Redis.

_Begriffsattribute:_

* _Feld: cloud_

### Credit Memo

_noun_

Ein vom Händler an einen Kunden ausgestelltes Dokument zur Abschreibung eines ausstehenden Saldos aufgrund von Überlastung, Rabatt oder Rückgabe von Waren.
Das Memo gibt dem Konto des Kunden die Mittel wieder.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Kommentar zur Kreditkarte

_noun_

Details, warum dem Kunden ein Kreditnachrichtenbetrag gutgeschrieben wurde.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Credit Memo Item

_noun_

Ein fakturiertes Element, für das ein Händler ein Kreditmemo erstellt.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Crosssell

_noun, adjektiv, verb_

Ein Produkt, das neben dem Warenkorb angezeigt wird.
Wenn ein Kunde zur Einkaufswagenseite navigiert, werden diese Produkte als Querverkäufe zu den Artikeln angezeigt, die sich bereits im Warenkorb befinden.
Sie ähneln Impulskäufen, wie Magazinen und Süßigkeiten in den Kassenbüchern in Lebensmittelgeschäften.

_Begriffsattribute:_

* _Feld: Geschäft, Produkt_
* _Verwandte Begriffe: Upsell_

### CVM

_noun_

Eine Abkürzung für &quot;Verifizierungsmethode für Karteninhaber&quot;.
Eine Möglichkeit, die Identität des Kunden durch Bestätigung eines dreistelligen oder vierstelligen Kreditkartensicherheits-Codes mit dem Zahlungsverarbeiter zu überprüfen.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_
* _Synonyme: Überprüfungsmethode des Karteninhabers_
* _Verwandte Begriffe: Sicherheitscode_

## D

### Datenbankschema

_noun_

Die Datenstruktur in einer Datenbank.
Definiert, wie Daten organisiert werden und wie Datenbeziehungen verwaltet werden, einschließlich aller Einschränkungen, die auf die Daten angewendet werden.
Ein Modul kann Fragmente des Datenbankschemas enthalten, wenn dieses Modul Daten enthält, die in der Datenbank gespeichert werden müssen.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Synonyme: schema_

### Abhängigkeitsinjektion

_noun_

Ein Software-Design-Muster, das es einer Klasse ermöglicht, ihre Abhängigkeiten anzugeben, ohne sie erstellen zu müssen.
Diese Klasse delegiert die Verantwortung für das Einfügen der Abhängigkeit an die aufrufende Klasse.
Dient zur Vereinfachung von Tests.
Um Abhängigkeiten für Klassen zu definieren, bearbeiten Sie die Konfigurationsdatei &quot;di.xml&quot;.

_Begriffsattribute:_

* _Feld: Programmiersprache_

### deploy key

_noun_

Ein Bereitstellungsschlüssel ist der öffentliche SSH-Schlüssel Ihres Projekts und ermöglicht schreibgeschützten oder schreibgeschützten Zugriff (sofern aktiviert) auf ein Git-Repository.

Weitere Informationen: [Sichere Verbindungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Begriffsattribute:_

* _Feld: cloud_

### Anmeldung mit zweifacher Bestätigung

_noun, verb_

Ein E-Mail-Verifizierungsprozess, bei dem potenzielle Abonnenten einen zweiten Schritt abschließen müssen, der ihre Abonnementabsicht bestätigt.

_Begriffsattribute:_

* _Feld: Business_

### herunterladbares Produkt

_noun_

Ein digital herunterladbares Produkt, das aus einer oder mehreren heruntergeladenen Dateien besteht, z. B. einem E-Book, einer Musik, einem Video, einer Software-Anwendung oder einem Update.
Sie können ein Album zum Verkauf anbieten und jedes Lied einzeln verkaufen.
Ein herunterladbares Produkt kann eine elektronische Version Ihres Produktkatalogs liefern.

Herunterladbare Dateien können sich auf Ihrem Server befinden oder als URLs für andere Server- oder Inhaltsbereitstellungsnetzwerke bereitgestellt werden.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produkttypen_

### dynamischer Inhalt

_noun_

Inhalt, der durch Code anstatt aus einer statischen Vorlage gelesen wird.
Nachdem dynamische Inhalte anfänglich gerendert werden, wenn ein Benutzer eine Seite besucht, können die Inhalte manchmal zwischengespeichert und wiederverwendet werden, ohne dass bei einem erneuten Besuch ein weiterer dynamischer Aufruf erforderlich ist.

_Begriffsattribute:_

* _Feld: Design_
* _Verwandte Begriffe: php_

### Dynamic Media-URL

_noun_

Eine URL-Adresse, die vom System dynamisch generiert wird, um auf ein Bild oder andere Medien zu verweisen.
Die Adresse verknüpft direkt mit Assets, die auf einem Server oder einem Inhaltsbereitstellungsnetzwerk gespeichert sind.
Um eine statische URL zu verwenden, ändern Sie die Konfigurationseinstellung.
Wenn jedoch dynamische Medien-URLs beim Deaktivieren der Einstellung in Ihrem Katalog enthalten sind, wird jeder Verweis in Ihrem Katalog zu einem fehlerhaften Link.
Links können wiederhergestellt werden, indem dynamische Medien-URLs erneut aktiviert werden.
Die Verwendung von URLs für dynamische Medien kann die Leistung der Katalogsuche beeinträchtigen.

Codeformat: media url=&quot;path/to/image.jpg&quot;

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: Content Delivery Network, URL_

## E

### ece-tools-Paket

_noun_

Eine Reihe von Skripten und Tools zum Verwalten und Bereitstellen der Commerce-Anwendung. Dieses Paket vereinfacht viele Adobe Commerce-Prozesse für Cloud-Infrastruktur, einschließlich der Bereitstellung in einer Docker-Umgebung, der Verwaltung von Crons, der Überprüfung der Projektkonfiguration und der Anwendung von Adobe-Patches.

Weitere Informationen: [ece-tools-Paket](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Begriffsattribute:_

* _Feld: cli, cloud, deploy_

### entity

_noun_

Eine eindeutige Einheit oder ein Objekt in der Programmierung.
Enthält Attribute oder Parameter, die geändert werden können.
Beispiele sind Staging, bei dem durch eine Aktualisierung Entitäten wie Preisregeln, Produkte oder Kategorien geändert werden können, und Datenbankdatensätze, bei denen Dienstleistungsaufträge Datenstrukturen enthalten, die gesendet und empfangen werden.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: -Attribut, Warenkorbregeln, Katalogregeln_

### Entitätsattributwert

_noun_

Für Datenbankentitäten ein Datenmodell, das Entitäten effizient kodiert.
Speichert die Entitäts-ID, den Attributnamen und den Wert als Dreifach, wodurch jederzeit neue Entitätsattributnamen erstellt werden können.
Bei der Kodierung kann die Anzahl der Attribute, die zur Beschreibung von Entitäten verwendet werden können, stark skaliert werden, aber die Zahl, die für eine bestimmte Entität gilt, wird minimiert.
Dieses Datenmodell ist flexibel, kann jedoch langsam sein.

Weitere Informationen: [EAV und Erweiterungsattribute](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Synonyme: eav_

### evergreen content

_noun_

Inhalt mit langer Haltbarkeitsdauer oder Inhalt, der wiederverwendet werden kann.

_Begriffsattribute:_

* _Feld: Business_

### Erweiterung

_noun_

Code, der das Adobe Commerce-Verhalten erweitert oder anpasst.
Sie können optional eine Erweiterung auf Commerce Marketplace oder einem anderen Erweiterungsverteilungssystem verpacken und verteilen.
Eine Commerce-Erweiterung kann Module, Designs und Sprachpakete enthalten.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Komponente, Modul, Paket_

### Erweiterungsattribut

_noun_

Erweitern Sie die Funktionalität und verwenden häufig komplexere Datentypen als benutzerdefinierte Attribute. Diese Attribute werden nicht in der grafischen Benutzeroberfläche angezeigt.

Weitere Informationen: [Hinzufügen von Erweiterungsattributen zur Entität](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Attribut, Entitätsattributwert_

## F

### Fracht an Bord

_noun_

Im internationalen Versand bedeutet dieser Begriff, dass der empfangende Partner für die Versandkosten verantwortlich ist.
FOB kann auf dem Herkunfts- oder Zielort basieren und entweder als Frachtabholung oder als Frachtvorbereitung bezeichnet werden.

_Begriffsattribute:_

* _Feld: Geschäft, Auftrag, Preisgestaltung_
* _Synonyme: fob_

### frontend

_adjektiv_

In einer Client-Server-Anwendung gibt es das Backend und das Frontend.
Die Frontend-Komponente oder der Client ist eine Schnittstelle, über die Benutzer den zugrunde liegenden Backend-Code bearbeiten oder mit ihm interagieren können.
Backend-Code wird auf einem Server ausgeführt.
Ein Benutzer kann nicht direkt auf Backend-Code zugreifen.
Ein Benutzer interagiert mit der Storefront, die wiederum Code verwendet, der auf dem Commerce-Server ausgeführt wird.

Hinweis: In der Vergangenheit wurde die Storefront als &quot;Frontend&quot;bezeichnet und der Administrator wurde als &quot;Backend&quot;bezeichnet. Diese Verwendung wird nicht mehr unterstützt.

_Begriffsattribute:_

* _Feld: Design, Programmierung_
* _Synonyme: Client-seitig_
* _Verwandte Begriffe: Backend, Storefront, Cache-Frontend_

### Frontend-Eigenschaften

_noun_

Eigenschaften, die die Darstellung und das Verhalten eines Attributs vom Standpunkt des Kunden in Ihrem Store aus bestimmen.

_Begriffsattribute:_

* _Feld: Design, Programmierung_

### fulfillment

_noun_

Der Prozess der Verwaltung von Kundensendungen.

_Begriffsattribute:_

* _Feld: Business_

## G

### Geschenkkarte

_noun_

Ein Prepaid-Karten- oder Geschenkgutschein, mit dem Käufe im Laden getätigt werden können.
Jeder Geschenkkarte wird ein eindeutiger Code zugewiesen, der beim Checkout eingegeben wird.
Der Wert der Geschenkkarte wird im Kontostand der Geschenkkarte angezeigt.
Es gibt drei Arten von Geschenkkarten:

* &quot;Physikalische&quot; Geschenkkarten können aus Kunststoff oder Kartenvorräten hergestellt und an den Kunden versandt werden.
* &quot;Virtuelle&quot; Geschenkkarten werden per E-Mail verschickt.
* &quot;Kombinierte&quot; Geschenkkarten sind eine Kombination aus den beiden, die dem Empfänger als physische Karte zugestellt und auch per E-Mail zugestellt werden.
Geschenkkarten sind konfigurierbar, einschließlich Optionen für die Produkteignung und die Auswahl von offenen oder festen Beträgen.

Eine Geschenkkarte kann auch vom Store-Administrator auf Kundenanfrage eingelöst werden, wenn die Bestellung im Backend erstellt wird.

Geschenkgutscheine helfen auch bei Promotions, da Store-Administratoren die Geschenkkartenkonten manuell im Backend erstellen und die Geschenkkarten-Codes an das spezifische Kundensegment senden können.
Geschenkkarten können als Treueprogramm für die aktivsten Kunden dienen, die während der Feiertage zahlreiche Käufe im Webstore tätigen oder eine spezifische Werbekampagne durchführen.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Produkttypen_

### Brutto-Marge

_noun_

Differenz zwischen Kosten und Preis eines Produkts.

_Begriffsattribute:_

* _Feld: Business_

### gruppiertes Produkt

_noun_

Ein Produkttyp mit mehreren ähnlichen eigenständigen Produkten, die auf einer Seite gruppiert sind.
Kann mit Varianten eines einzelnen Produkts angeboten werden oder indem sie nach Saison oder Thema gruppiert werden, um einen koordinierten Satz zu erstellen.
Jedes Produkt kann separat oder als Teil der Gruppe erworben werden.

Für ein Messer, das in vier Größen erhältlich ist, können alle vier Messer auf einer gruppierten Produktseite dargestellt werden.
Kunden können die gewünschten Größen auswählen und diese auf dieser Seite zum Warenkorb hinzufügen.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: einfaches Produkt, Produktarten_

## H

### handle

_noun_

Im Allgemeinen ist ein Handle eine Möglichkeit, auf ein Objekt zu verweisen.
In Adobe Commerce werden Handles an vielen Stellen verwendet, meist zur Identifizierung einer Seite.
Bei Seiten-Handles wird der Handle-Name von der URL abgeleitet und dann zum Suchen und Laden der Layout-Dateien für die referenzierte Seite verwendet.
Im Kundenmodul gibt es beispielsweise eine Layout-Datei mit dem Namen &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Hier ist &quot;frontend&quot;der Bereichsname und &quot;checkout_cart_index&quot;der Handle-Name, die beide von der URL abgeleitet werden.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Synonyme: Seitenkanal_

### horizontale Skalierung

_noun_

Horizontale Skalierung (auch als &quot;Ausskalierung&quot;bezeichnet) ist der Prozess, zusätzliche Knoten oder Maschinen zu Ihrer Infrastruktur hinzuzufügen, um die wachsende Nachfrage zu decken.

_Begriffsattribute:_

* _Feld: cloud_

## I

### Abfangen

_noun_

Der Prozess der Injektion von neuem Code vor, nach oder um eine bestehende öffentliche Funktion einer PHP-Klasse.

Um eine Funktion abzufangen, implementiert ein Plug-in den aufzurufenden zusätzlichen Code.
Plug-ins werden über die Konfigurationsdatei für die Abhängigkeitsinjektion (di.xml) mit Abfangpunkten verknüpft.
Wenn mehrere Plug-ins für dieselbe Funktion definiert sind, definiert die Konfiguration für die Abhängigkeitsinjektion die Reihenfolge, in der die Plug-ins aufgerufen werden, sodass mehrere Plug-ins ohne Konflikte verwendet werden können.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: Plug-in_

## L

### layout

_noun_

Beim Erstellen einer Commerce-Seite handelt es sich bei einem Layout um eine Reihe von Bausteinen, die in einer Hierarchie zusammengestellt sind und die Struktur der Seite darstellen.

Seitenlayoutdateien konzentrieren sich auf die höchste Ebene der Seitenstruktur (Kopf-, Fußzeile, Hauptinhaltsbereich, linke Seitenleiste usw.).
Layout-Dateien sammeln dann Inhalte (Bausteine) in diese verschiedenen Bereiche auf der Seite.

_Begriffsattribute:_

* _Feld: Design, Commerce-Software_
* _Verwandte Begriffe: Layoutanleitungen, Block_

### Layoutanleitungen

_noun_

Markup in einer Layout-Datei, die Änderungen beschreibt, die auf eine strukturierte Elementstruktur von Bausteinen, Containern und UI-Komponenten angewendet werden sollen.
Eine Layout-Datei kann mehrere Layoutanweisungen enthalten.
Layoutanweisungen sind in XML in Layoutdateien kodiert.

_Begriffsattribute:_

* _Feld: Design, Programmierung_
* _Verwandte Begriffe: Layout, Block, Container, UI-Komponente_

### Layoutaktualisierung

_noun_

Wird für Codefragmente verwendet, die hinzugefügt werden, um das XML-Layout zu ändern oder die Layoutanweisungen aus einer anderen Datei zu importieren.

_Begriffsattribute:_

* _Feld: Design, Commerce-Software_

### Lizenzinhaber

_noun_

Der Lizenzinhaber (auch als Kontoinhaber bezeichnet) ist die benannte Person in einem Unternehmen, das Zahlungen und andere geschäftsbezogene Probleme für die Adobe Commerce im Cloud-Infrastrukturkonto verwaltet.
Diese Person dient als Kontaktstelle für Adobe.
Nachdem ein Unternehmen eine Adobe Commerce für ein Cloud-Infrastrukturabonnement erworben hat, ist der anfängliche Projektzugriff und der Codezugriff nur für die Person verfügbar, die als Lizenzinhaber bezeichnet wurde.

_Begriffsattribute:_

* _Feld: Business_

## M

### MAGEID

_noun_

MAGEID ist normalerweise der Abrechnungskontakt für das Adobe Commerce-Konto (und möglicherweise nicht der Projektinhaber des Adobe Commerce-Projekts für Cloud-Infrastruktur).
Für die Zugriffsberechtigung auf Adobe Commerce und Adobe Commerce in Cloud-Infrastrukturpaketen müssen Sie Zugriffsschlüssel verwenden, die mit einem MAGEID verknüpft sind, dem Zugriff auf diese Pakete gewährt wurde.

Weitere Informationen: [Abrufen der Authentifizierungsschlüssel](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Begriffsattribute:_

* _Feld: Commerce-Software_

### Markup

_noun_

In Marketing- und Einzelhandelsgeschäften wird ein Prozentsatz zu den Kosten eines Artikels hinzugefügt, um den Einzelhandelspreis zu ermitteln.
[Markup konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html)oder Markdown für ein Produkt durch anpassbare Produktoptionen.

In der Entwicklung, eine Computersprache, die die Verarbeitung, Darstellung und Formatierung von Text steuert.
Markup-Tags sind außerdem Codefragmente, die einer CMS-Seite oder -Blöcken Funktionen oder Inhalte hinzufügen.

_Begriffsattribute:_

* _Feld: Business, Programmierung_
* _Synonyme: Markdown_

### Übergeordnete Umgebung

_noun_

In Adobe Commerce auf Cloud-Infrastruktur verwenden Pro-Projekte eine Übergeordnete aktive Platform as a Service-Umgebung (PAs), die eine Kopie Ihrer Produktionsumgebungsdatenbank und Ihres Webservers enthält.

_Begriffsattribute:_

* _Feld: cloud_

### Händlerkonto

_noun_

Ein Konto bei einer Bank oder einem Finanzinstitut, das die Annahme von Kreditkartengeschäften ermöglicht.

_Begriffsattribute:_

* _Feld: Business_

### MFTF

_noun_

MFTF ist eine [Funktionstests-Framework](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Es bietet ein Test-Framework für Commerce-Entwickler und Software-Ingenieure wie QA-Spezialisten, PHP-Entwickler und Systemintegratoren.
Entwickler und QA können Tests schreiben, um Benutzerinteraktionen mit Webanwendungen zu versuchen, die Funktionalität zu überprüfen und Regressionstests zu automatisieren.

_Begriffsattribute:_

* _Feld: Commerce-Software, Programmierung_
* _Verwandte Begriffe: cms-Block, statischer Block, Container, Layout_

### Modul

_noun_

Code, der die von der Magento-Anwendung bereitgestellten Funktionen ändert oder erweitert.
Ein Modul ist in einer Verzeichnisstruktur enthalten, die PHP- und XML-Dateien (Konfiguration, Blöcke, Controller, Helfer, Modelle usw.) enthält, die sich auf eine bestimmte Funktionalität beziehen, um eine bestimmte Sammlung von Produktfunktionen bereitzustellen.
Jedes Modul soll spezifische Produktfunktionen bereitstellen, indem neue Funktionen implementiert oder die Funktionalität anderer Module erweitert wird.
Jedes Modul ist so konzipiert, dass es unabhängig funktioniert, sodass das Einschließen oder Ausschließen eines bestimmten Moduls die Funktionalität anderer Module nicht beeinträchtigt.

Ein Modul kann auch Widgets implementieren, bei denen es sich um Seitenelemente handelt, die von Geschäftsbenutzern im Admin angepasst werden können.

Module können deaktiviert oder entfernt werden, ohne die Konsistenz der Magento-Anwendung zu beeinträchtigen.
Eine Ausnahme: Wenn das Modul von anderen Modulen abhängig ist, die das Deaktivieren oder Entfernen der abhängigen Module erfordern.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: php, xml, block_

## O

### OMS

_noun_

[OMS](https://omsdocs.magento.com) ist das Auftragsverwaltungssystem von Adobe.

OMS ist eine flexible und erschwingliche Lösung für das Verwalten, Verkaufen und Erfüllen von Lagerbeständen aus allen Vertriebskanälen.
OMS bietet ein nahtloses Kundenerlebnis, das den Umsatz steigert und gleichzeitig die Kosten senkt und die Markteinführungszeit verkürzt.

Zu den OMS-Funktionen gehören:

* Globale Sichtbarkeit und Verwaltung des gesamten Bestands
* Möglichkeit der Beförderung von und zu jedem Ort
* Einfacherer und reaktionsfähigerer Kundendienst
* Besseres Kundenerlebnis und Kundentreue

Weitere Informationen: [Erste Schritte mit OMS](https://omsdocs.magento.com/en/getting-started/), [OMS Docs-Site](https://omsdocs.magento.com/en/)

_Begriffsattribute:_

* _Feld: Funktion, Commerce-Software, Bestellverwaltung_
* _Synonyme: Auftragsverwaltung, MOM, Auftragsverwaltungssystem, Magento Order Management_
* _Verwandte Begriffe: Order Management_

### Ursprungsverdeckung

_noun_

Die Ursprungsverschlüsselung ist eine Sicherheitsfunktion, mit der Adobe Commerce in der Cloud-Infrastruktur jeglichen nicht schnellen Traffic blockieren kann, um DDoS-Angriffe zu verhindern und die Cloud-Infrastruktur (Ursprung) zu nutzen.

Weitere Informationen: [Schnell hergestelltes Verdecken](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Begriffsattribute:_

* _Feld: security_
* _Verwandte Begriffe: Webanwendungs-Firewall_

## P

### Page Builder

_noun_

Page Builder ist eine Commerce-Erweiterung zum Erstellen von inhaltsreichen Seiten durch Ziehen und Ablegen vordefinierter Steuerelemente zum Definieren benutzerdefinierter Layouts.
Diese Steuerelemente werden auch als &quot;Inhaltstypen&quot;bezeichnet.
Merchants können Layouts und Seiten ohne Programmierung erstellen.
Entwickler können den Seitenaufbau erweitern.

Weitere Informationen: [Benutzerhandbuch für Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [Entwicklungsdokumente für den Seitenaufbau](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Begriffsattribute:_

* _Feld: Commerce-Software, Design_
* _Synonyme: Admin, Admin Panel, Backend, Administrationsoberfläche, Admin-Benutzeroberfläche_
* _Verwandte Begriffe: admin_

### Zahlungseingang

_noun_

Ein Payment Gateway ist ein Drittanbieter-Service, der Kreditkartentransaktionen nahtlos verarbeitet, ohne dass der Kunde die Website des Händlers verlässt.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung, Programmierung_

## R

### verwandte Ware

_noun_

Eine Auswahl von Produkten, die als Anreiz zum Kauf zusätzlicher Artikel präsentiert werden.
Wenn der Kunde z. B. die Produktseite für eine Kamera anzeigt, können die zugehörigen Produkte andere vergleichbare Kameras, einen Kamerasatz und ein Stativ umfassen.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_

## S

### Verkaufsregeln

_noun_

Umfasst Warenkorb- und Katalogregeln, mit denen ein Produkt für Werbeaktionen gewertet wird.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Warenkorbregeln, Katalogregeln_

### Umfang

_noun_

In Adobe Commerce beschreibt scope den Umfang Ihrer Store-Hierarchie, auf den sich eine Einstellung auswirken kann.
Der Umfang kann für Folgendes gelten:

* Global - alle Websites, Stores und Store-Ansichten
* Website — die ausgewählte Website sowie alle Geschäfte und Store-Ansichten darunter
* Store - der ausgewählte Store und alle darin enthaltenen Store-Ansichten
* Store-Ansicht - die ausgewählte Store-Ansicht.

Innerhalb der Hierarchie können Einstellungen, die auf eine niedrigere Ebene angewendet werden, einige Einstellungen auf höherer Ebene überschreiben.

_Begriffsattribute:_

* _Feld: Commerce-Software_

### Dienstleistungsauftrag

_noun_

Ein Satz von PHP-Schnittstellen, die für ein Modul definiert sind.
Ein Servicevertrag umfasst Datenschnittstellen, die die Datenintegrität und Service-Schnittstellen beibehalten, die Details der Geschäftslogik von Dienstanfragen wie Controllern, Webdiensten und anderen Modulen ausblenden.
Web-APIs können über Konfigurationsdateien an Dienstverträge gebunden werden.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: PHP, Web API_

### Abrechnung

_noun_

Die Abwicklung erfolgt, wenn die übernehmende Bank und die Devisenfonds des Emittenten sowie die Erlöse auf dem Handelskonto hinterlegt werden.

_Begriffsattribute:_

* _Feld: Business_

### Freigegebener Katalog

_noun_

Eine Funktion, mit der Händler einen Katalog erstellen können, der als ganzer Katalog oder Teilmenge davon dienen kann, und dann benutzerdefinierte Preise für ein oder mehrere Produkte zuweisen können.
Händler können diesen Katalog dann einem oder mehreren Unternehmen zuweisen.

Beispielsweise hat ein B2B-Händler drei Kunden, die spezifische Tarife für die Elektronikverteilungssite des Händlers ausgehandelt haben.
Mithilfe der Funktion &quot;Freigegebener Katalog&quot;verfügt der Händler über:

* Ein Hauptkatalog
* Ein Katalog für Kunden 1 (möglicherweise sind es nur drei SKUs mit Rabatten auf Kunden aus dem Hauptkatalog)
* Kunden-2-Katalog (könnte der gesamte Katalog mit 10 % Rabatt sein)
* Kunden-3-Katalog (einige Dutzend Produkte mit Rabatten vom Hauptkatalog von 5 % bis 60 %).

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Katalog, b2b_

### Verbringung

_noun_

Eine Sendung enthält zu liefernde Produkte und erstellt einen Datensatz der versandten Produkte.
Mehr als eine Sendung kann mit einer Bestellung verbunden werden.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Versandpapier

_noun_

Ein Dokument, das eine Sendung begleitet. In dem Dokument werden die Erzeugnisse und ihre Mengen im Lieferpaket aufgeführt.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Reederei

_noun_

Ein Unternehmen, das Packages transportiert. Zu den gängigen Netzbetreibern zählen UPS, FedEx, DHL und USPS.

_Begriffsattribute:_

* _Feld: Geschäft, Bestellung_

### Warenkorb

_noun_

Die Produktgruppe, die ein Kunde gekauft, aber noch nicht gekauft hat.
Bezieht sich auch auf einen Bereich einer E-Commerce-Site, in dem diese Produkte zur Überprüfung und zum Checkout gefunden werden können.

_Begriffsattribute:_

* _Feld: Business, Design, Produkt, Programmierung_
* _Synonyme: Warenkorb, Warenkorb_
* _Verwandte Begriffe: Warenkorbregeln_

### einfaches Produkt

_noun_

Der einfachste Warentyp, ein physisches Produkt mit einer einzigen SKU.
Einfache Produkte verfügen über verschiedene Preis- und Eingangskontrollen, die den Verkauf von Produktvarianten ermöglichen.
Einfache Produkte können zusammen mit gruppierten, gebündelten und konfigurierbaren Produkten verwendet werden.
Ein einfaches Produkt mit benutzerdefinierten Optionen wird manchmal als zusammengesetztes Produkt bezeichnet.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produkttypen_

### SKU

_noun_

Abkürzung für Stock Keeping Unit.
Eine Nummer oder ein Code, der einem Produkt zugewiesen wird, um das Produkt, die Optionen, den Preis und den Hersteller zu identifizieren.

_Begriffsattribute:_

* _Feld: Business, Preisgestaltung, Produkt, Programmierung_
* _Verwandte Begriffe: freigegebener Katalog_

### Begrüßungsseite

_noun_

eine Werbeseite mit einem Produkt oder einer Werbung; wird normalerweise vor der Startseite angezeigt.

_Begriffsattribute:_

* _Feld: Design_

### statischer Block

_noun_

Eine modulare Inhaltseinheit, die von einem Benutzer in das CMS auf einer Seite platziert werden kann, um Text und Bilder anzuzeigen oder Codefragmente auszuführen.
Statische Blöcke enthalten bearbeitbaren Inhalt und können als Landingpages für Produktkategorien verwendet werden.
Widgets können statischen Bausteinen hinzugefügt werden, um zusätzliche Funktionen bereitzustellen.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: Block cms, Block_

### statische Inhalte

_noun_

Benutzergenerierte Inhalte (nicht vom Code generiert), die sich nicht häufig ändern.

_Begriffsattribute:_

* _Feld: Design_
* _Verwandte Begriffe: dynamischer Inhalt_

### statische Dateien

_noun_

Die Sammlung von Assets wie CSS, Schriftarten, Bildern und JavaScript, die von einem Design verwendet werden.

_Begriffsattribute:_

* _Feld: Commerce-Software_

### store

_noun_

Die Commerce-Bereichsebene &quot;store&quot;ist die zweite Hierarchieebene Ihrer Website, die wie folgt aussieht: website > store > store view.
Geschäfte können in eine oder mehrere Geschäfte unterteilt werden. Jeder Store verfügt möglicherweise über eine eigene Stammkategorie und alle freigeben Katalog- und Kundendaten.

Jeder Store kann über mehrere Store-Ansichten verfügen, die normalerweise verwendet werden, um die Storefront in einem anderen Gebietsschema und einer anderen Sprache darzustellen.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Store-Ansicht, Website_

### Store-Ansicht

_noun_

Die Commerce-Bereichsebene der &quot;Store-Ansicht&quot;bezieht sich auf die dritte Ebene in der Hierarchie der Websites, Stores und Store-Ansichten.
Store-Ansichten stellen die Storefront normalerweise in einem anderen Gebietsschema und einer anderen Sprache dar.
Verwenden Sie zum Ändern von Store-Ansichten die Store-Auswahl in der Kopfzeile.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Geschäft, Website_

### storefront

_noun_

Der Online-Store, den Kunden beim Besuch Ihrer Commerce-Site erleben.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_

## T

### Steuervorschriften

_noun_

Eine Kombination aus Produktsteuerklasse, Kundensteuerklasse und Steuersatz. Diese Regel definiert, welche Steuerberechnung angewendet wird.

_Begriffsattribute:_

* _Feld: Business_

### template

_noun_

Kurz für HTML-Vorlage oder PHTML-Vorlage.
Eine PHTML-Datei enthält eine Mischung aus HTML Markup und PHP-Code, um dynamischen Inhalt in die HTML einzufügen.
Die meisten Blöcke verfügen über mindestens eine PHTML-Datei (Vorlage), die die vom Block erzeugte statische HTML enthält.
In den Admin-, E-Mail- und Newsletter-Vorlagen werden Text, Bilder und Variablen mit HTML-Markup kombiniert, um personalisierte Inhalte zu erstellen, die vom System gesendet werden.

_Begriffsattribute:_

* _Feld: Commerce-Software_
* _Verwandte Begriffe: block_

### Design

_noun_

Enthält Grafiken und Darstellungsinformationen.
Passt das Erscheinungsbild des Stores an.
Adobe Commerce kann Designs in (Composer-)Packages versenden.
Themen können jedoch unter App/Design platziert werden, das nicht in einem Paket enthalten ist.
Pakete sind die Download-Einheit für Composer, und — über Commerce Marketplace — Commerce-Benutzer können CE oder EE als eine Reihe von Paketen herunterladen, in denen Pakete Module, Designs oder Sprachpakete enthalten.

_Begriffsattribute:_

* _Feld: Commerce-Software_

## U

### UI-Komponente

_noun_

Ein Tag, das für Adobe Commerce-Software entwickelt wurde, um ein einfacheres und flexibleres Rendering der Benutzeroberfläche zu ermöglichen.
Die Ziele des UI-Komponentensystems umfassen Folgendes:

* Vereinfachen der Layout Handle-XML-Dateien
* Verschieben der Elemente der Admin-Benutzeroberfläche von HTML+JavaScript in ein benutzerdefiniertes Widget-System &quot;reines JavaScript&quot;
* Erstellen komplexerer UI-Komponenten aus kleineren Komponenten
* Vorab-Rendering von Daten für UI-Komponenten als JSON, enge Bindung an Backend-Datenobjekte
* AJAX zum Aktualisieren von Komponentendaten verwenden
* Einführung einer neuen DSL zum Erstellen der oben genannten Elemente

Weitere Informationen: [Komponentenleitfaden für UI](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: JavaScript, Layout, Komponente, Seiten-Builder_

### UPWARD

_noun_

[PWA Studio](https://github.com/magento/pwa-studio) uses [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) in der Entwicklung.
UPWARD ist ein Akronym für die einheitliche Definition der progressiven Web-App-Antwort.
Eine UPWARD-Definitionsdatei beschreibt, wie ein Webserver eine Progressive Web Application bereitstellt und unterstützt.

UPWARD-Definitionsdateien bieten Details zum Serververhalten in plattformunabhängiger, deklarativer Sprache.
Dadurch kann eine Progressive Web Application auf einem UPWARD-kompatiblen Server in jeder beliebigen Sprache auf einem beliebigen Technologiestapel ausgeführt werden, da die Anwendung nur über das HTTP-Endpunktverhalten vom UPWARD-Server besorgt ist.

Ein UPWARD-Server verwendet eine Definitionsdatei, um den entsprechenden Prozess oder Dienst für eine Anfrage von einer Anwendungs-Shell zu bestimmen.
Es wird beschrieben, wie der Server eine Anfrage verarbeiten und die Antwort dafür erstellen sollte.

Ein PWA-Projekt kann eine UPWARD-Definitionsdatei enthalten, um seine Dienstabhängigkeiten anzugeben.

_Begriffsattribute:_

* _Feld: Design, Commerce-Software, Programmierung_
* _Synonyme: PWA Studio: Einheitliche Definition der progressiven Web-App-Antwort_
* _Verwandte Begriffe: pwa_

## V

### Anbietergebündelte Erweiterung

_noun_

Von Anbietern erstellter Code, der das Commerce-Verhalten erweitert oder anpasst und als Drittanbietererweiterung fungiert, gilt als VBE (Vendor Bundle Extension).
VBEs werden gründlich getestet und in jeder unterstützten Version von Magento Open Source und Adobe Commerce integriert.
Eine VBE kann Module, Designs und Sprachpakete enthalten.

Weitere Informationen finden Sie unter [Thema &quot;Gebündelte Erweiterung&quot;des Anbieters](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Begriffsattribute:_

* _Feld: Commerce-Erweiterung, herstellergebündelte Erweiterung, Erweiterung, VBE_
* _Synonyme: Erweiterung, VBE_
* _Verwandte Begriffe: Erweiterung, gebündelte Erweiterung_

### vertikale Skalierung

_noun_

Vertikale Skalierung (Vergrößern) bezieht sich auf die Steigerung der Verarbeitungsleistung eines einzelnen Servers oder Clusters durch Hinzufügen von Festplatten- oder Netzwerk-I/O, CPUs oder RAM.

_Begriffsattribute:_

* _Feld: Umgebung_

### virtuelles Produkt

_noun_

Stellt ein nicht physisches Produkt dar, das verkauft werden kann, z. B. eine Mitgliedschaft, ein Service, eine Garantie oder ein Abonnement.
Virtual Produkte können einzeln oder als Teil der folgenden Produkttypen verkauft werden: gruppiertes Produkt und Bundle-Produkt.
Versand oder Inventar ist nicht erforderlich.

Der Prozess der Erstellung eines virtuellen Produkts und eines einfachen Produkts ist fast identisch.
Da jedoch ein virtuelles Produkt nicht ausgeliefert wird, gibt es kein Feld für die Gewichtung oder die Option, eine Geschenkkarte einzuschließen.

_Begriffsattribute:_

* _Feld: Commerce-Software, Produkt_
* _Verwandte Begriffe: Produkttypen_

### virtueller Typ

_noun_

Virtuelle Typen sind eine Möglichkeit, verschiedene Abhängigkeiten in bestehende PHP-Klassen zu injizieren, ohne dass andere Klassen betroffen sind und ohne dass eine Klassendatei erstellt werden muss.
Virtuelle Typen können nur durch Überschreibungen von Argumenten in einer `<type>` -Element in &quot;di.xml&quot;-Dateien, niemals im Quellcode.
Sie können nicht erweitert werden und sie können keine Referenzen als Abhängigkeiten in einem Klassen-Konstruktor sein.

_Begriffsattribute:_

* _Feld: Programmiersprache_
* _Verwandte Begriffe: php_

## W

### website

_noun_

In der Adobe Commerce-Software die höchste Ebene einer Website-Hierarchie über der Store- und Store-Ansicht.
Sie können mehrere Websites haben und jede Website kann einen anderen Domänennamen haben.
Websites können eingerichtet werden, um Kundendaten zu teilen oder keine Daten freizugeben.

_Begriffsattribute:_

* _Feld: Commerce-Software, Design, Produkt_
* _Verwandte Begriffe: Store, Store-Ansicht_

### Widget

_noun_

A [Widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) ist ein vorbereitetes Codefragment, mit dem Blöcke, Links und dynamische Inhalte an bestimmten Stellen auf Store-Seiten platziert werden können.
Sie können Widgets verwenden, um Landingpages für Marketingkampagnen zu erstellen, Werbeinhalte an bestimmten Stellen im gesamten Store anzuzeigen.
Widgets können auch verwendet werden, um interaktive Elemente und Aktionsblöcke für externe Prüfungssysteme, Videokassetten, Abstimmungs- und Anmeldeformulare hinzuzufügen oder um Navigationselemente für Tag-Clouds und Bild-Slider bereitzustellen.

_Begriffsattribute:_

* _Feld: Business, Commerce-Software, Design_
* _Verwandte Begriffe: block_
