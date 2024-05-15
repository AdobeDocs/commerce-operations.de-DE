---
title: Best Practices für die Leistung
description: Erfahren Sie, wie Sie die Leistung von Checkout-Erlebnissen auf Ihrer Adobe Commerce-Site optimieren können.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Best Practices für die Leistung

Die [Kasse](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) -Prozess in Adobe Commerce ist ein wichtiger Aspekt der Storefront-Erfahrung. Sie beruht auf dem integrierten [Warenkorb](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) und [Kasse](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) Funktionen.

Die Leistung ist entscheidend für die Aufrechterhaltung eines guten Benutzererlebnisses. Überprüfen Sie die [Performance-Benchmark-Zusammenfassung](../implementation-playbook/infrastructure/performance/benchmarks.md) , um mehr über Leistungserwartungen zu erfahren. Sie können die Leistung des Checkout optimieren, indem Sie die folgenden Optionen für **Verarbeitung hoher Durchsatzaufträge**:

- [AsyncOrder](#asynchronous-order-placement)—Asynchron verarbeitet Bestellungen mithilfe einer Warteschlange.
- [Zurückgestellte Gesamtberechnung](#deferred-total-calculation)—Verzögern Sie Berechnungen für die Bestellsummen, bis der Checkout beginnt.
- [Inventarprüfung beim Laden des Warenkorbs](#disable-inventory-check)—Entscheiden Sie, die Bestandsvalidierung von Warenkorbelementen zu überspringen.
- [Lastenausgleich](#load-balancing)—Aktivieren Sie sekundäre Verbindungen für die MySQL-Datenbank und die Redis-Instanz.

Die Konfigurationsoptionen AsyncOrder, Deferred Total Calculation und Inventory Check on Cart Load funktionieren unabhängig voneinander. Sie können alle drei Funktionen gleichzeitig verwenden oder die Funktionen in jeder beliebigen Kombination aktivieren und deaktivieren.

>[!NOTE]
>
>Verwenden Sie keinen benutzerdefinierten PHP-Code, um die integrierten Funktionen für Warenkorb und Checkout anzupassen. Zusätzlich zu potenziellen Leistungsproblemen kann die Verwendung von benutzerdefiniertem PHP-Code zu komplexen Upgrades und Wartungsproblemen führen. Diese Probleme erhöhen Ihre Gesamtbetriebskosten. Wenn eine PHP-basierte Anpassung des Warenkorbs und des Checkout unvermeidbar ist, verwenden Sie [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)-nur genehmigte Erweiterungen. Alle Marketplace-Erweiterungen unterliegen [ausführliche Überprüfung](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) , um zu überprüfen, ob sie den Adobe Commerce-Kodierungsstandards und -Best Practices entsprechen.

## Asynchrone Bestellplatzierung

Die _Asynchrone Reihenfolge_ -Modul aktiviert die asynchrone Bestellplatzierung, die die Bestellung als `received`, platziert die Bestellung in eine Warteschlange und verarbeitet die Bestellungen aus der Warteschlange auf der Basis des &quot;first-in-first-out&quot;. AsyncOrder is **disabled** Standardmäßig.

Ein Kunde fügt beispielsweise ein Produkt zum Warenkorb hinzu und wählt **[!UICONTROL Proceed to Checkout]**. Sie füllen die **[!UICONTROL Shipping Address]** Formular, wählen Sie die gewünschten **[!UICONTROL Shipping Method]**, wählen Sie eine Zahlungsmethode aus und geben Sie die Bestellung ein. Der Warenkorb wird gelöscht, die Bestellung wird als **[!UICONTROL Received]**, aber die Produktmenge wird noch nicht angepasst und auch keine E-Mail zum Verkauf an den Kunden gesendet. Die Bestellung wird empfangen, aber die Bestelldetails sind noch nicht verfügbar, da die Bestellung noch nicht vollständig verarbeitet wurde. Er verbleibt in der Warteschlange, bis der `placeOrderProcess` Verbraucher beginnt, überprüft die Bestellung mit der [Bestandskontrolle](#disable-inventory-check) -Funktion (standardmäßig aktiviert) und aktualisiert die Reihenfolge wie folgt:

- **Produkt verfügbar**—Der Bestellstatus ändert sich in _Ausstehend_, wird die Produktmenge angepasst, eine E-Mail mit Bestelldetails wird an den Kunden gesendet und die erfolgreichen Bestelldetails können im **Bestellungen und Rückgaben** Liste mit ausführbaren Optionen, z. B. Neuanordnung.
- **Produkt nicht vorrätig oder nur wenig**—Der Bestellstatus ändert sich in _Abgelehnt_, wird die Produktmenge nicht angepasst, eine E-Mail mit Bestelldetails zum Problem wird an den Kunden gesendet und die zurückgewiesenen Bestelldetails werden im **Bestellungen und Rückgaben** Liste ohne ausführbare Optionen.

Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` Datei entsprechend den entsprechenden README-Dateien, die in der Datei [_Modulreferenz-Handbuch_](https://developer.adobe.com/commerce/php/module-reference/).

**Aktivieren von AsyncOrder**:

Sie können AsyncOrder über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --checkout-async 1
```

Die `set` -Befehl schreibt Folgendes in die `app/etc/env.php` Datei:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Siehe [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) im _Modulreferenz-Handbuch_.

**So deaktivieren Sie AsyncOrder**:

>[!WARNING]
>
>Bevor Sie das AsyncOrder-Modul deaktivieren, müssen Sie sicherstellen, dass _all_ Die asynchronen Bestellprozesse sind abgeschlossen.

Sie können AsyncOrder über die Befehlszeilenschnittstelle deaktivieren:

```bash
bin/magento setup:config:set --checkout-async 0
```

Die `set` -Befehl schreibt Folgendes in die `app/etc/env.php` Datei:

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
| Checkout-Typen | OnePage Checkout<br>Standard-Checkout<br>B2B Negotiatives Zitat |
| Zahlungsmethoden | Überprüfen/Money Order<br>Zustellbare Barmittel<br>Braintree<br>PayPal PayFlow Pro |
| Versandmethoden | Alle Versandmethoden werden unterstützt. |

Die folgenden Funktionen sind **not** unterstützt von AsyncOrder, aber weiterhin synchron funktionieren:

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

Entwickler können bestimmte Zahlungsmethoden explizit von der asynchronen Bestellplatzierung ausschließen, indem sie zum `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` Array. Bestellungen, die ausgeschlossene Zahlungsmethoden verwenden, werden synchron verarbeitet.

### Negotiatives Anführungszeichen - Asynchrone Reihenfolge

Die _Negotiatives Anführungszeichen - Asynchrone Reihenfolge_ Mit dem B2B-Modul können Sie Bestellelemente asynchron für die `NegotiableQuote` Funktionalität. Sie müssen AsyncOrder und NegotiableQuote aktiviert haben.

## Zurückgestellte Gesamtberechnung

Die _Zurückgestellte Gesamtberechnung_ optimiert den Checkout-Prozess, indem die Gesamtberechnung aufgeschoben wird, bis sie für den Warenkorb oder die letzten Checkout-Schritte angefordert wird. Wenn diese Option aktiviert ist, wird nur die Zwischensumme berechnet, da ein Kunde Produkte zum Warenkorb hinzufügt.

Zurückgestellte Gesamtberechnung ist **disabled** Standardmäßig. Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` Datei entsprechend den entsprechenden README-Dateien, die in der Datei [_Modulreferenz-Handbuch_](https://developer.adobe.com/commerce/php/module-reference/).

**So aktivieren Sie DeferredTotalCalculation**:

Sie können DeferredTotalCalculation über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Die `set` -Befehl schreibt Folgendes in die `app/etc/env.php` Datei:

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

Die `set` -Befehl schreibt Folgendes in die `app/etc/env.php` Datei:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Siehe [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) im _Modulreferenz-Handbuch_.

### Feste Produktsteuer

Wenn die verzögerte Berechnung der Gesamtsumme aktiviert ist, ist die feste Produktsteuer (FPT) nicht im Produktpreis und der Untersumme des Warenkorbs des Mini-Warenkorbs enthalten, nachdem das Produkt zum Warenkorb hinzugefügt wurde. Die FPT-Berechnung wird beim Hinzufügen eines Produkts zum Mini-Warenkorb verschoben. Der FPT wird im Warenkorb korrekt angezeigt, nachdem der Vorgang zum endgültigen Kassengang fortgesetzt wurde.

## Lagerbestandsüberprüfung deaktivieren

Die _Aktivieren des Lagerbestands beim Laden des Warenkorbs_ Die globale Einstellung bestimmt, ob beim Laden eines Produkts in den Warenkorb eine Bestandsüberprüfung durchgeführt wird. Die Deaktivierung des Prozesses zur Überprüfung des Bestands verbessert die Leistung bei allen Checkout-Schritten, insbesondere beim Umgang mit Massenprodukten im Warenkorb.

Wenn diese Option deaktiviert ist, wird beim Hinzufügen eines Produkts zum Warenkorb keine Bestandsüberprüfung durchgeführt. Wenn diese Bestandsüberprüfung übersprungen wird, können einige nicht vorrätige Szenarien andere Fehlertypen auslösen. Bestandsüberprüfung _always_ tritt beim Bestellplatzierungsschritt auf, auch wenn deaktiviert.

**Aktivieren der Lagerbestandsüberprüfung beim Laden des Warenkorbs** ist standardmäßig aktiviert (auf Ja gesetzt). Um die Bestandsüberprüfung beim Laden des Warenkorbs zu deaktivieren, legen Sie **[!UICONTROL Enable Inventory Check On Cart Load]** nach `No` in der Admin-Benutzeroberfläche **Stores** > **Konfiguration** > **Katalog** > **Bestand** > **Lageroptionen** Abschnitt. Siehe [Globale Optionen konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) und [Katalog-Inventar](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) im _Benutzerhandbuch_.

## Lastenausgleich

Sie können den Lastenausgleich über verschiedene Knoten hinweg unterstützen, indem Sie für die MySQL-Datenbank und die Redis-Instanz sekundäre Verbindungen aktivieren.

Adobe Commerce kann mehrere Datenbanken oder Redis-Instanzen asynchron lesen. Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, können Sie die sekundären Verbindungen konfigurieren, indem Sie die [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) und [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) -Werte in `.magento.env.yaml` -Datei. Nur ein Knoten muss Lese- und Schreibvorgänge-Traffic verarbeiten, sodass die Variablen auf `true` führt zu einer sekundären Verbindung für schreibgeschützten Traffic. Legen Sie die Werte auf `false` , um ein vorhandenes schreibgeschütztes Verbindungs-Array aus dem `env.php` -Datei.

Beispiel der `.magento.env.yaml` Datei:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
