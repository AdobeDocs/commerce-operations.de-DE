---
title: Best Practices für die Checkout-Leistung
description: Erfahren Sie, wie Sie die Leistung von Checkout-Erlebnissen auf Ihrer Adobe Commerce-Site optimieren können.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# Best Practices für die Checkout-Leistung

Der [Checkout](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process)-Prozess in Adobe Commerce ist ein wichtiger Aspekt des Storefront-Erlebnisses. Sie stützt sich auf die integrierten Funktionen [Warenkorb](https://experienceleague.adobe.com/de/docs/commerce-admin/start/storefront/storefront#shopping-cart) und [Checkout](https://experienceleague.adobe.com/de/docs/commerce-admin/start/storefront/storefront#checkout-page).

Leistung ist der Schlüssel für ein gutes Benutzererlebnis. Sie können die Checkout-Leistung optimieren, indem Sie die folgenden Optionen für die **Auftragsverarbeitung mit hohem Durchsatz** konfigurieren:

- [AsyncOrder](#asynchronous-order-placement) - Verarbeitet Bestellungen asynchron mithilfe einer Warteschlange.
- [Berechnung aufgeschoben](#deferred-total-calculation) - Berechnungen für Auftragssummen werden bis zum Beginn des Checkouts aufgeschoben.
- [Bestandsprüfung beim Laden des Warenkorbs](#disable-inventory-check) - Wählen Sie diese Option, um die Inventarüberprüfung von Warenkorbartikeln zu überspringen.
- [Lastenausgleich](#load-balancing) - Aktivieren Sie sekundäre Verbindungen für die MySQL-Datenbank und die Redis-Instanz.

Die Konfigurationsoptionen „AsyncOrder“, „Deferred Total Calculation“ und „Inventory Check“ beim Laden des Warenkorbs funktionieren unabhängig voneinander. Sie können alle drei Funktionen gleichzeitig verwenden oder die Funktionen in jeder beliebigen Kombination aktivieren und deaktivieren.

>[!NOTE]
>
>Verwenden Sie keinen benutzerdefinierten PHP-Code, um die integrierten Warenkorb- und Checkout-Funktionen anzupassen. Zusätzlich zu möglichen Leistungsproblemen kann die Verwendung von benutzerdefiniertem PHP-Code zu komplexen Upgrades und Wartungsproblemen führen. Diese Probleme erhöhen Ihre Gesamtbetriebskosten. Wenn eine PHP-basierte Warenkorb- und Checkout-Anpassung unvermeidbar ist, verwenden Sie nur [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)-genehmigte Erweiterungen. Alle Marketplace-Erweiterungen unterliegen einer [umfassenden Überprüfung](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) um sicherzustellen, dass sie den Kodierungsstandards und Best Practices von Adobe Commerce entsprechen.

## Asynchrone Auftragserteilung

Das Modul _Async Order_ ermöglicht die asynchrone Auftragserteilung, die die Bestellung als `received` markiert, sie in eine Warteschlange stellt und Bestellungen aus der Warteschlange als „First-in-First-out“-Bestellungen verarbeitet. AsyncOrder ist **deaktiviert**.

Beispiel: Eine Kundin oder ein Kunde fügt ihrem bzw. seinem Warenkorb ein Produkt hinzu und wählt **[!UICONTROL Proceed to Checkout]** aus. Sie füllen das **[!UICONTROL Shipping Address]** aus, wählen ihre bevorzugte **[!UICONTROL Shipping Method]** aus, wählen eine Zahlungsmethode aus und geben die Bestellung auf. Der Warenkorb wird geleert, die Bestellung wird als **[!UICONTROL Received]** gekennzeichnet, aber die Produktmenge ist noch nicht angepasst, noch wird eine Verkaufs-E-Mail an den Kunden gesendet. Die Bestellung wird empfangen, aber die Bestelldetails sind noch nicht verfügbar, da die Bestellung noch nicht vollständig verarbeitet wurde. Er verbleibt in der Warteschlange, bis der `placeOrderProcess` Verbraucher beginnt, die Bestellung mit der Funktion [Bestandsprüfung](#disable-inventory-check) (standardmäßig aktiviert) überprüft und die Bestellung wie folgt aktualisiert:

- **Produkt verfügbar** - Der Bestellstatus ändert sich in _Ausstehend_, die Produktmenge wird angepasst, eine E-Mail mit Bestelldetails wird an den Kunden gesendet, und die erfolgreichen Bestelldetails werden für die Anzeige in der Liste **Bestellungen und Rücksendungen** mit umsetzbaren Optionen wie Neu bestellen verfügbar.
- **Nicht vorrätiges Produkt oder geringe**: Der Bestellstatus ändert sich in _Abgelehnt_, die Produktmenge wird nicht angepasst, eine E-Mail mit Bestelldetails zum Problem wird an den Kunden gesendet, und die Details zur abgelehnten Bestellung werden in der Liste **Bestellungen und Rücksendungen** ohne umsetzbare Optionen verfügbar.

Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` gemäß den entsprechenden README-Dateien, die im [_Modul-Referenzhandbuch“ definiert_](https://developer.adobe.com/commerce/php/module-reference/).

**So aktivieren Sie AsyncOrder**:

Sie können AsyncOrder über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --checkout-async 1
```

Der Befehl `set` schreibt Folgendes in die `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Siehe [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) im _Modul-Referenzhandbuch_.

**So deaktivieren Sie AsyncOrder**:

>[!WARNING]
>
>Bevor Sie das Modul „AsyncOrder“ deaktivieren, müssen Sie sicherstellen, _alle_ asynchronen Auftragsprozesse abgeschlossen sind.

Sie können AsyncOrder über die Befehlszeilenschnittstelle deaktivieren:

```bash
bin/magento setup:config:set --checkout-async 0
```

Der Befehl `set` schreibt Folgendes in die `app/etc/env.php`:

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
| Checkout-Typen | OnePage Checkout<br>Standard Checkout<br>B2B Negotiable Quote |
| Zahlungsmethoden | Scheck/Zahlungsanweisung<br>Nachnahme<br>Braintree/<br> PayFlow Pro |
| Versandmethoden | Alle Versandmethoden werden unterstützt. |

Die folgenden Funktionen werden **nicht** von AsyncOrder unterstützt, funktionieren jedoch weiterhin synchron:

- Zahlungsmethoden, die nicht in der Liste der unterstützten Funktionen enthalten sind
- Mehradressen-Checkout
- Erstellen von Admin-Aufträgen

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
>GraphQL unterstützt nicht das asynchrone Platzieren von übertragbaren Angebotsaufträgen.

#### Ausschließen von Zahlungsmethoden

Entwickler können bestimmte Zahlungsmethoden explizit von der asynchronen Auftragserteilung ausschließen, indem sie sie zum `Magento\AsyncOrder\Model\OrderManagement::paymentMethods`-Array hinzufügen. Bestellungen, die ausgeschlossene Zahlungsmethoden verwenden, werden synchron verarbeitet.

### Asynchrone Reihenfolge der verhandelbaren Angebote

Mit _B2B-Modul_ Negotiable Quote Async Order) können Sie Bestellartikel asynchron für die `NegotiableQuote` speichern. Für Sie müssen AsyncOrder und NegotiableQuote aktiviert sein.

## Berechnung zurückgestellter Beträge

Das Modul _verzögerte Gesamtberechnung_ optimiert den Checkout-Prozess, indem es die Gesamtberechnung bis zur Anforderung für den Warenkorb oder während der letzten Checkout-Schritte verschiebt. Wenn diese Option aktiviert ist, wird nur die Zwischensumme berechnet, wenn ein Kunde Produkte zum Warenkorb hinzufügt.

Die Berechnung verzögerter Gesamtwerte ist **deaktiviert**. Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` gemäß den entsprechenden README-Dateien, die im [_Modul-Referenzhandbuch“ definiert_](https://developer.adobe.com/commerce/php/module-reference/).

**So aktivieren Sie DeferredTotalCalculation**:

Sie können DeferredTotalCalculation über die Befehlszeilenschnittstelle aktivieren:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Der Befehl `set` schreibt Folgendes in die `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation deaktivieren**:

Sie können DeferredTotalCalculation mithilfe der Befehlszeilenschnittstelle deaktivieren:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Der Befehl `set` schreibt Folgendes in die `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Siehe [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) im _Modul-Referenzhandbuch_.

### feste Produktsteuer

Wenn die Berechnung verzögerter Gesamtsummen aktiviert ist, wird die feste Produktsteuer (FPT) nicht in den Produktpreis und die Zwischensumme des Warenkorbs einbezogen, nachdem das Produkt zum Warenkorb hinzugefügt wurde. Die FTP-Berechnung wird zurückgestellt, wenn ein Produkt zum Mini-Warenkorb hinzugefügt wird. Die FTP wird korrekt im Warenkorb angezeigt, nachdem mit dem endgültigen Checkout fortgefahren wurde.

## Inventarprüfung deaktivieren

Die globale Einstellung _Inventar beim Laden des Warenkorbs aktivieren_ bestimmt, ob beim Laden eines Produkts in den Warenkorb eine Bestandsprüfung durchgeführt werden soll. Die Deaktivierung des Prozesses zur Bestandsprüfung verbessert die Leistung aller Checkout-Schritte, insbesondere bei der Verwendung von Massenprodukten im Warenkorb.

Wenn diese Option deaktiviert ist, wird beim Hinzufügen eines Produkts zum Warenkorb keine Inventarprüfung durchgeführt. Wenn diese Bestandsprüfung übersprungen wird, können einige nicht vorrätige Szenarien andere Fehlertypen auslösen. Eine Bestandskontrolle _immer_ erfolgt beim Schritt der Bestellplatzierung, auch wenn diese deaktiviert ist.

**Inventarprüfung beim Laden des Warenkorbs aktivieren** ist standardmäßig aktiviert (auf Ja gesetzt). Um die Bestandsprüfung beim Laden des Warenkorbs zu deaktivieren, legen Sie **[!UICONTROL Enable Inventory Check On Cart Load]** im Abschnitt Admin-Benutzeroberfläche `No`Stores **>** Konfiguration **>** Katalog **>** Inventar **>** Stock-Optionen **auf**. Siehe [Konfigurieren globaler ](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/configuration/global-options) und [Kataloginventar](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/guide-overview) im _Benutzerhandbuch_.

## Lastausgleich

Sie können dazu beitragen, die Last auf verschiedenen Knoten auszugleichen, indem Sie sekundäre Verbindungen für die MySQL-Datenbank und die Redis-Instanz aktivieren.

Adobe Commerce kann mehrere Datenbanken oder Redis-Instanzen asynchron lesen. Wenn Sie Commerce in einer Cloud-Infrastruktur verwenden, können Sie die sekundären Verbindungen konfigurieren, indem Sie die Werte [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) und [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) in der `.magento.env.yaml`-Datei bearbeiten. Da nur ein Knoten Lese-/Schreibdatenverkehr verarbeiten muss, führt das Festlegen der Variablen auf `true` zu einer sekundären Verbindung für schreibgeschützten Datenverkehr. Legen Sie die Werte auf `false` fest, um ein vorhandenes schreibgeschütztes Verbindungs-Array aus der `env.php` zu entfernen.

Beispiel für die `.magento.env.yaml`:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
