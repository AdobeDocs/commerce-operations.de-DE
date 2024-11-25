---
title: Best Practices für die Leistung
description: Erfahren Sie, wie Sie die Leistung von Checkout-Erlebnissen auf Ihrer Adobe Commerce-Site optimieren können.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# Best Practices für die Leistung

Der [Checkout](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) -Prozess in Adobe Commerce ist ein wichtiger Aspekt des Storefront-Erlebnisses. Sie beruht auf den integrierten Funktionen [Warenkorb](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) und [Checkout](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page).

Die Leistung ist entscheidend für die Aufrechterhaltung eines guten Benutzererlebnisses. Sie können die Leistung des Checkout optimieren, indem Sie die folgenden Optionen für die Verarbeitung von **Auftrag mit hohem Durchsatz** konfigurieren:

- [AsyncOrder](#asynchronous-order-placement) - Verarbeitet asynchron Bestellungen mithilfe einer Warteschlange.
- [Aufgeschobene Gesamtberechnung](#deferred-total-calculation): Verzögern Sie die Berechnungen für die Bestellsummen, bis der Checkout beginnt.
- [Bestandsüberprüfung beim Laden des Warenkorbs](#disable-inventory-check) - Entscheiden Sie, die Bestandsvalidierung von Warenkorbelementen zu überspringen.
- [Lastenausgleich](#load-balancing): Aktivieren Sie sekundäre Verbindungen für die MySQL-Datenbank und die Redis-Instanz.

Die Konfigurationsoptionen AsyncOrder, Deferred Total Calculation und Inventory Check on Cart Load funktionieren unabhängig voneinander. Sie können alle drei Funktionen gleichzeitig verwenden oder die Funktionen in jeder beliebigen Kombination aktivieren und deaktivieren.

>[!NOTE]
>
>Verwenden Sie keinen benutzerdefinierten PHP-Code, um die integrierten Funktionen für Warenkorb und Checkout anzupassen. Zusätzlich zu potenziellen Leistungsproblemen kann die Verwendung von benutzerdefiniertem PHP-Code zu komplexen Upgrades und Wartungsproblemen führen. Diese Probleme erhöhen Ihre Gesamtbetriebskosten. Wenn eine PHP-basierte Anpassung des Warenkorbs und des Checkout unvermeidbar ist, verwenden Sie nur die Erweiterungen, die für den [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/) genehmigt wurden. Alle Marketplace-Erweiterungen unterliegen einer [umfassenden Überprüfung](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/), um zu überprüfen, ob sie den Adobe Commerce-Kodierungsstandards und Best Practices entsprechen.

## Asynchrone Bestellplatzierung

Das Modul _Async Order_ aktiviert die asynchrone Bestellplatzierung, die die Bestellung als `received` kennzeichnet, die Bestellung in eine Warteschlange stellt und Bestellungen aus der Warteschlange auf &quot;first-in-first-out&quot;-Basis verarbeitet. AsyncOrder ist standardmäßig **disabled**.

Beispielsweise fügt ein Kunde seinem Warenkorb ein Produkt hinzu und wählt **[!UICONTROL Proceed to Checkout]** aus. Sie füllen das **[!UICONTROL Shipping Address]**-Formular aus, wählen ihr bevorzugtes **[!UICONTROL Shipping Method]** aus, wählen eine Zahlungsmethode aus und platzieren die Bestellung. Der Warenkorb wird gelöscht, die Bestellung wird als **[!UICONTROL Received]** gekennzeichnet, aber die Produktmenge wird noch nicht angepasst und auch keine Verkaufs-E-Mail an den Kunden gesendet. Die Bestellung wird empfangen, aber die Bestelldetails sind noch nicht verfügbar, da die Bestellung noch nicht vollständig verarbeitet wurde. Er verbleibt in der Warteschlange, bis der `placeOrderProcess` -Verbraucher beginnt, die Bestellung mit der Funktion [Bestandsüberprüfung](#disable-inventory-check) überprüft (standardmäßig aktiviert) und die Reihenfolge wie folgt aktualisiert:

- **Produkt verfügbar**: Der Bestellstatus ändert sich in &quot;_Ausstehend_&quot;, die Produktmenge wird angepasst, eine E-Mail mit Bestelldetails wird an den Kunden gesendet und die erfolgreichen Bestelldetails stehen in der Liste **Bestellungen und Rückgaben** zur Ansicht zur Verfügung mit ausführbaren Optionen, wie z. B. Neuanordnung.
- **Produkt nicht vorrätig oder wenig vorrätig**: Der Bestellstatus ändert sich in &quot;_Abgelehnt_&quot;, die Produktmenge wird nicht angepasst, eine E-Mail mit Bestelldetails zum Problem wird an den Kunden gesendet und die zurückgewiesenen Bestelldetails werden in der Liste **Bestellungen und Rückgaben** ohne umsetzbare Optionen verfügbar.

Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die Datei &quot;`app/etc/env.php`&quot;entsprechend den entsprechenden README-Dateien, die im [_Modulreferenzhandbuch_](https://developer.adobe.com/commerce/php/module-reference/) definiert sind.

**So aktivieren Sie AsyncOrder**:

Sie können AsyncOrder über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --checkout-async 1
```

Der Befehl `set` schreibt Folgendes in die Datei `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Siehe [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) im _Modulreferenzhandbuch_.

**So deaktivieren Sie AsyncOrder**:

>[!WARNING]
>
>Bevor Sie das AsyncOrder-Modul deaktivieren, müssen Sie sicherstellen, dass alle asynchronen Bestellprozesse von _1} abgeschlossen sind._

Sie können AsyncOrder über die Befehlszeilenschnittstelle deaktivieren:

```bash
bin/magento setup:config:set --checkout-async 0
```

Der Befehl `set` schreibt Folgendes in die Datei `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder-Kompatibilität

AsyncOrder unterstützt eine begrenzte Anzahl von Adobe Commerce-Funktionen.

| Kategorie | Unterstützte Funktion |
|------------------|--------------------------------------------------------------------------|
| Checkout-Typen | OnePage Checkout<br>Standard Checkout<br>B2B Negotiable Zitat |
| Zahlungsmethoden | Check/Money Order<br>Cash on Delivery<br>Braintree<br>PayPal PayFlow Pro |
| Versandmethoden | Alle Versandmethoden werden unterstützt. |

Die folgenden Funktionen werden von AsyncOrder zwar **nicht** unterstützt, funktionieren aber weiterhin synchron:

- Zahlungsmethoden sind nicht in der Liste der unterstützten Funktionen enthalten
- Checkout für mehrere Adressen
- Erstellung von Admin-Bestellungen

#### Web-API-Unterstützung

Wenn das AsyncOrder-Modul aktiviert ist, werden die folgenden REST-Endpunkte und GraphQL-Mutationen asynchron ausgeführt:

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL unterstützt nicht die asynchrone Platzierung übertragbarer Anführungsaufträge.

#### Zahlungsmethoden ausschließen

Entwickler können bestimmte Zahlungsmethoden explizit von der asynchronen Bestellplatzierung ausschließen, indem sie zum Array `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` hinzugefügt werden. Bestellungen, die ausgeschlossene Zahlungsmethoden verwenden, werden synchron verarbeitet.

### Negotiatives Anführungszeichen - Asynchrone Reihenfolge

Mit dem B2B-Modul _Negotiable Quote Async Order_ können Sie Bestellelemente asynchron für die Funktion `NegotiableQuote` speichern. Sie müssen AsyncOrder und NegotiableQuote aktiviert haben.

## Zurückgestellte Gesamtberechnung

Das Modul _Aufgeschobene Gesamtberechnung_ optimiert den Checkout-Prozess, indem die Gesamtberechnung aufgeschoben wird, bis sie für den Warenkorb oder während der letzten Checkout-Schritte angefordert wird. Wenn diese Option aktiviert ist, wird nur die Zwischensumme berechnet, da ein Kunde Produkte zum Warenkorb hinzufügt.

Die verzögerte Gesamtberechnung ist standardmäßig **deaktiviert**. Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die Datei &quot;`app/etc/env.php`&quot;entsprechend den entsprechenden README-Dateien, die im [_Modulreferenzhandbuch_](https://developer.adobe.com/commerce/php/module-reference/) definiert sind.

**So aktivieren Sie DeferredTotalCalculation**:

Sie können DeferredTotalCalculation über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Der Befehl `set` schreibt Folgendes in die Datei `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**So deaktivieren Sie DeferredTotalCalculation**:

Sie können DeferredTotalCalculation über die Befehlszeilenschnittstelle deaktivieren:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Der Befehl `set` schreibt Folgendes in die Datei `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Siehe [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) im _Modulreferenzhandbuch_.

### Feste Produktsteuer

Wenn die verzögerte Berechnung der Gesamtsumme aktiviert ist, ist die feste Produktsteuer (FPT) nicht im Produktpreis und der Untersumme des Warenkorbs des Mini-Warenkorbs enthalten, nachdem das Produkt zum Warenkorb hinzugefügt wurde. Die FPT-Berechnung wird beim Hinzufügen eines Produkts zum Mini-Warenkorb verschoben. Der FPT wird im Warenkorb korrekt angezeigt, nachdem der Vorgang zum endgültigen Kassengang fortgesetzt wurde.

## Lagerbestandsüberprüfung deaktivieren

Die globale Einstellung _Bestand beim Warenkorb laden aktivieren_ bestimmt, ob beim Laden eines Produkts in den Warenkorb eine Bestandsüberprüfung durchgeführt werden soll. Die Deaktivierung des Prozesses zur Überprüfung des Bestands verbessert die Leistung bei allen Checkout-Schritten, insbesondere beim Umgang mit Massenprodukten im Warenkorb.

Wenn diese Option deaktiviert ist, wird beim Hinzufügen eines Produkts zum Warenkorb keine Bestandsüberprüfung durchgeführt. Wenn diese Bestandsüberprüfung übersprungen wird, können einige nicht vorrätige Szenarien andere Fehlertypen auslösen. Eine Bestandsüberprüfung _always_ erfolgt beim Bestellplatzierungsschritt, auch wenn sie deaktiviert ist.

**Die Option &quot;Überprüfung des Lagerbestands beim Laden des Warenkorbs aktivieren&quot;** ist standardmäßig aktiviert (auf &quot;Ja&quot; eingestellt). Um die Bestandsüberprüfung beim Laden des Warenkorbs zu deaktivieren, setzen Sie in der Admin-Benutzeroberfläche **Stores** > **Konfiguration** > **Katalog** > **Bestand** > **Lageroptionen** auf `No`. **[!UICONTROL Enable Inventory Check On Cart Load]** Siehe [Globale Optionen konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) und [Katalog-Inventar](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) im _Benutzerhandbuch_.

## Lastenausgleich

Sie können den Lastenausgleich über verschiedene Knoten hinweg unterstützen, indem Sie für die MySQL-Datenbank und die Redis-Instanz sekundäre Verbindungen aktivieren.

Adobe Commerce kann mehrere Datenbanken oder Redis-Instanzen asynchron lesen. Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, können Sie die sekundären Verbindungen konfigurieren, indem Sie die Werte [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) und [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) in der Datei `.magento.env.yaml` bearbeiten. Nur ein Knoten muss Lese- und Schreibvorgänge-Traffic verarbeiten. Wenn Sie die Variablen auf `true` setzen, wird daher eine sekundäre Verbindung für schreibgeschützten Traffic erstellt. Setzen Sie die Werte auf &quot;`false`&quot;, um ein vorhandenes schreibgeschütztes Verbindungs-Array aus der `env.php` -Datei zu entfernen.

Beispiel der Datei &quot;`.magento.env.yaml`&quot;:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
