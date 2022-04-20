---
title: Verarbeitung hoher Durchsatzmengen
description: Optimieren Sie die Auftragsplatzierung und das Checkout-Erlebnis für Ihre Adobe Commerce- oder Magento Open Source-Bereitstellung.
source-git-commit: 0a902d7fe967bbcee5019fea83e5be66ce2aefd0
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---


# Verarbeitung hoher Durchsatzaufträge

Sie können die Bestellplatzierung und das Checkout-Erlebnis optimieren, indem Sie die folgenden Module für **Verarbeitung hoher Durchsatzaufträge**:

- [AsyncOrder](#asynchronous-order-placement)—Asynchron verarbeitet Bestellungen mithilfe einer Warteschlange.
- [NegotiableQuoteAsyncOrder](#negotiable-quote-asyn-order)—Asynchron verarbeitet NegotiableQuote Speicheraufträge.
- [DeferredTotalCalculation](#deferred-total-calculation)—Verschiebt Berechnungen für die Bestellsummen bis zum Start des Checkouts.

Alle Funktionen funktionieren unabhängig. Sie können alle Funktionen gleichzeitig verwenden oder Funktionen in jeder beliebigen Kombination aktivieren und deaktivieren.

Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` Datei entsprechend den entsprechenden README-Dateien, die in der Datei [_Modulreferenz-Handbuch_][mrg].

## Asynchrone Bestellplatzierung

Die _Asynchrone Reihenfolge_ -Modul aktiviert die asynchrone Bestellplatzierung, die die Bestellung als `received`, platziert die Bestellung in eine Warteschlange und verarbeitet die Bestellungen aus der Warteschlange auf der Basis des &quot;first-in-first-out&quot;-Vorgangs. AsyncOrder is **disabled** Standardmäßig.

Ein Kunde fügt beispielsweise ein Produkt zum Warenkorb hinzu und wählt **[!UICONTROL Proceed to Checkout]**. Sie füllen die **[!UICONTROL Shipping Address]** Formular, wählen Sie die gewünschten **[!UICONTROL Shipping Method]**, wählen Sie eine Zahlungsmethode aus und geben Sie die Bestellung ein. Der Warenkorb wird gelöscht, die Bestellung wird als **[!UICONTROL Received]**, aber die Produktmenge wird noch nicht angepasst und auch keine E-Mail zum Verkauf an den Kunden gesendet. Die Bestellung wird empfangen, aber die Bestelldetails sind noch nicht verfügbar, da die Bestellung noch nicht vollständig verarbeitet wurde. Er verbleibt in der Warteschlange, bis der `placeOrderProcess` Verbraucher beginnt, überprüft die Bestellung mit der [Bestandskontrolle](#disable-inventory-check) -Funktion (standardmäßig aktiviert) und aktualisiert die Reihenfolge wie folgt:

- **Produkt verfügbar**—Der Bestellstatus ändert sich in _Ausstehend_, wird die Produktmenge angepasst, eine E-Mail mit Bestelldetails wird an den Kunden gesendet und die erfolgreichen Bestelldetails können im **Bestellungen und Rückgaben** Liste mit ausführbaren Optionen, z. B. Neuanordnung.
- **Produkt nicht vorrätig oder nur wenig**—Der Bestellstatus ändert sich in _Zurückgewiesen_, wird die Produktmenge nicht angepasst, eine E-Mail mit Bestelldetails zum Problem wird an den Kunden gesendet und die zurückgewiesenen Bestelldetails werden im **Bestellungen und Rückgaben** Liste ohne ausführbare Optionen.

So aktivieren Sie AsyncOrder:

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

Siehe [AsyncOrder] im _Modulreferenz-Handbuch_.

So deaktivieren Sie AsyncOrder:

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

AsyncOrder unterstützt eine begrenzte Anzahl von [!DNL Commerce] Funktionen.

| Kategorie | Unterstützte Funktion |
|---------------- | -----------------------|
| Checkout-Typen | OnePage Checkout<br>Standard-Checkout<br>B2B Negotiatives Zitat |
| Zahlungsmethoden | Überprüfen/Money-Bestellung<br>Zustellbare Barmittel<br>Braintree<br>PayPal PayFlow Pro |
| Versandmethoden | Alle Versandmethoden werden unterstützt. |

Die folgenden Funktionen sind **not** unterstützt von AsyncOrder, aber weiterhin synchron funktionieren:

- Zahlungsmethoden, die nicht in der Liste der unterstützten Funktionen enthalten sind
- Checkout für mehrere Adressen
- Erstellung von Admin-Bestellungen

#### Web-API-Unterstützung

Wenn das AsyncOrder-Modul aktiviert ist, werden die folgenden REST-Endpunkte und GraphQL-Mutationen asynchron ausgeführt:

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL unterstützt nicht die asynchrone Platzierung übertragbarer Anführungsaufträge.

#### Zahlungsmethoden ausschließen

Entwickler können bestimmte Zahlungsmethoden explizit von der Platzierung asynchroner Aufträge ausschließen, indem sie sie zum `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` Array. Bestellungen, die ausgeschlossene Zahlungsmethoden verwenden, werden synchron verarbeitet.

## Negotiatives Anführungszeichen - Asynchrone Reihenfolge

Die _Negotiatives Anführungszeichen - Asynchrone Reihenfolge_ Mit dem B2B-Modul können Sie Bestellelemente asynchron für die `NegotiableQuote` Funktionalität. Sie müssen AsyncOrder und NegotiableQuote aktiviert haben.

## Zurückgestellte Gesamtberechnung

Die _Zurückgestellte Gesamtberechnung_ -Modul optimiert den Checkout-Prozess, indem die Gesamtberechnung aufgeschoben wird, bis sie für den Warenkorb oder während der letzten Checkout-Schritte angefordert wird. Wenn diese Option aktiviert ist, wird nur die Zwischensumme berechnet, da ein Kunde Produkte zum Warenkorb hinzufügt.

DeferredTotalCalculation is **disabled** Standardmäßig.

So aktivieren Sie DeferredTotalCalculation:

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

So deaktivieren Sie DeferredTotalCalculation:

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

Siehe [DeferredTotalCalculating] im _Modulreferenz-Handbuch_.

### Feste Produktsteuer

Wenn DeferredTotalCalculation aktiviert ist, ist die feste Produktsteuer (FPT) nach dem Hinzufügen des Produkts zum Warenkorb nicht im Produktpreis und in der Untersumme des Warenkorbs des Mini-Warenkorbs enthalten. Die FPT-Berechnung wird beim Hinzufügen eines Produkts zum Mini-Warenkorb verschoben. Der FPT wird im Warenkorb korrekt angezeigt, nachdem der Vorgang zum endgültigen Kassengang fortgesetzt wurde.

## Lagerbestandsüberprüfung deaktivieren

Die _Aktivieren des Lagerbestands beim Laden des Warenkorbs_ Die globale Einstellung bestimmt, ob beim Laden eines Produkts in den Warenkorb eine Bestandsüberprüfung durchgeführt wird. Die Deaktivierung des Prozesses zur Überprüfung des Bestands verbessert die Leistung bei allen Checkout-Schritten, insbesondere beim Umgang mit Massenprodukten im Warenkorb.

Wenn diese Option deaktiviert ist, wird beim Hinzufügen eines Produkts zum Warenkorb keine Bestandsüberprüfung durchgeführt. Wenn diese Bestandsüberprüfung übersprungen wird, können einige nicht vorrätige Szenarien andere Fehlertypen auslösen. Bestandsüberprüfung _always_ tritt beim Bestellplatzierungsschritt auf, auch wenn deaktiviert.

&quot;Bestand im Warenkorb laden&quot;aktivieren ist **enabled** Standardmäßig.

Um die Bestandsüberprüfung beim Laden des Warenkorbs zu deaktivieren, legen Sie **[!UICONTROL Enable Inventory Check On Cart Load]** nach `No` in der Admin-Benutzeroberfläche. Siehe [Globale Optionen konfigurieren][global] und [Katalogbestand][inventory] im _Benutzerhandbuch_.

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://devdocs.magento.com/guides/v2.4//mrg/intro.html
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[DeferredTotalCalculating]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
