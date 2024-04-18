---
title: Verarbeitung hoher Durchsatzreihenfolgen
description: Optimieren Sie die Auftragsplatzierung und das Checkout-Erlebnis für Ihre Adobe Commerce-Implementierung.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Verarbeitung hoher Durchsatzaufträge

Sie können die Bestellplatzierung und das Checkout-Erlebnis optimieren, indem Sie die folgenden Module für **Verarbeitung hoher Durchsatzaufträge**:

- [AsyncOrder](#asynchronous-order-placement)—Asynchron verarbeitet Bestellungen mithilfe einer Warteschlange.
- [Zurückgestellte Gesamtberechnung](#deferred-total-calculation)—Verschiebt Berechnungen für die Bestellsummen bis zum Start des Checkouts.
- [Inventarprüfung beim Anführungszeichenladevorgang](#disable-inventory-check)—Entscheiden Sie, die Bestandsvalidierung von Warenkorbelementen zu überspringen.

Alle Funktionen - AsyncOrder, verzögerte Gesamtberechnung und Bestandsüberprüfung - funktionieren unabhängig voneinander. Sie können alle drei Funktionen gleichzeitig verwenden oder Funktionen in jeder beliebigen Kombination aktivieren und deaktivieren.

## Asynchrone Bestellplatzierung

Die _Asynchrone Reihenfolge_ -Modul aktiviert die asynchrone Bestellplatzierung, die die Bestellung als `received`, platziert die Bestellung in eine Warteschlange und verarbeitet die Bestellungen aus der Warteschlange auf der Basis des &quot;first-in-first-out&quot;. AsyncOrder is **disabled** Standardmäßig.

Ein Kunde fügt beispielsweise ein Produkt zum Warenkorb hinzu und wählt **[!UICONTROL Proceed to Checkout]**. Sie füllen die **[!UICONTROL Shipping Address]** Formular, wählen Sie die gewünschten **[!UICONTROL Shipping Method]**, wählen Sie eine Zahlungsmethode aus und geben Sie die Bestellung ein. Der Warenkorb wird gelöscht, die Bestellung wird als **[!UICONTROL Received]**, aber die Produktmenge wird noch nicht angepasst und auch keine E-Mail zum Verkauf an den Kunden gesendet. Die Bestellung wird empfangen, aber die Bestelldetails sind noch nicht verfügbar, da die Bestellung noch nicht vollständig verarbeitet wurde. Er verbleibt in der Warteschlange, bis der `placeOrderProcess` Verbraucher beginnt, überprüft die Bestellung mit der [Bestandskontrolle](#disable-inventory-check) -Funktion (standardmäßig aktiviert) und aktualisiert die Reihenfolge wie folgt:

- **Produkt verfügbar**—Der Bestellstatus ändert sich in _Ausstehend_, wird die Produktmenge angepasst, eine E-Mail mit Bestelldetails wird an den Kunden gesendet und die erfolgreichen Bestelldetails können im **Bestellungen und Rückgaben** Liste mit ausführbaren Optionen, z. B. Neuanordnung.
- **Produkt nicht vorrätig oder nur wenig**—Der Bestellstatus ändert sich in _Abgelehnt_, wird die Produktmenge nicht angepasst, eine E-Mail mit Bestelldetails zum Problem wird an den Kunden gesendet und die zurückgewiesenen Bestelldetails werden im **Bestellungen und Rückgaben** Liste ohne ausführbare Optionen.

Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` Datei entsprechend den entsprechenden README-Dateien, die in der Datei [_Modulreferenz-Handbuch_][mrg].

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

Siehe [AsyncOrder] im _Modulreferenz-Handbuch_.

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

AsyncOrder unterstützt eine begrenzte Anzahl von [!DNL Commerce] Funktionen.

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

### Negotiatives Anführungszeichen - Asynchrone Reihenfolge

Die _Negotiatives Anführungszeichen - Asynchrone Reihenfolge_ Mit dem B2B-Modul können Sie Bestellelemente asynchron für die `NegotiableQuote` Funktionalität. Sie müssen AsyncOrder und NegotiableQuote aktiviert haben.

## Zurückgestellte Gesamtberechnung

Die _Zurückgestellte Gesamtberechnung_ -Modul optimiert den Checkout-Prozess, indem die Gesamtberechnung aufgeschoben wird, bis sie für den Warenkorb oder während der letzten Checkout-Schritte angefordert wird. Wenn diese Option aktiviert ist, wird nur die Zwischensumme berechnet, da ein Kunde Produkte zum Warenkorb hinzufügt.

DeferredTotalCalculation is **disabled** Standardmäßig. Verwenden Sie die Befehlszeilenschnittstelle, um diese Funktionen zu aktivieren, oder bearbeiten Sie die `app/etc/env.php` Datei entsprechend den entsprechenden README-Dateien, die in der Datei [_Modulreferenz-Handbuch_][mrg].

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

Siehe [DeferredTotalCalculating] im _Modulreferenz-Handbuch_.

### Feste Produktsteuer

Wenn DeferredTotalCalculation aktiviert ist, ist die feste Produktsteuer (FPT) nach dem Hinzufügen des Produkts zum Warenkorb nicht im Produktpreis und in der Untersumme des Warenkorbs des Mini-Warenkorbs enthalten. Die FPT-Berechnung wird beim Hinzufügen eines Produkts zum Mini-Warenkorb verschoben. Der FPT wird im Warenkorb korrekt angezeigt, nachdem der Vorgang zum endgültigen Kassengang fortgesetzt wurde.

## Lagerbestandsüberprüfung deaktivieren

Die _Aktivieren des Lagerbestands beim Laden des Warenkorbs_ Die globale Einstellung bestimmt, ob beim Laden eines Produkts in den Warenkorb eine Bestandsüberprüfung durchgeführt wird. Die Deaktivierung des Prozesses zur Überprüfung des Bestands verbessert die Leistung bei allen Checkout-Schritten, insbesondere beim Umgang mit Massenprodukten im Warenkorb.

Wenn diese Option deaktiviert ist, wird beim Hinzufügen eines Produkts zum Warenkorb keine Bestandsüberprüfung durchgeführt. Wenn diese Bestandsüberprüfung übersprungen wird, können einige nicht vorrätige Szenarien andere Fehlertypen auslösen. Bestandsüberprüfung _always_ tritt beim Bestellplatzierungsschritt auf, auch wenn deaktiviert.

**Aktivieren der Lagerbestandsüberprüfung beim Laden des Warenkorbs** ist standardmäßig aktiviert (auf Ja gesetzt). Um die Bestandsüberprüfung beim Laden des Warenkorbs zu deaktivieren, legen Sie **[!UICONTROL Enable Inventory Check On Cart Load]** nach `No` in der Admin-Benutzeroberfläche **Stores** > **Konfiguration** > **Katalog** > **Bestand** > **Lageroptionen** Abschnitt. Siehe [Globale Optionen konfigurieren][global] und [Katalog-Inventar][inventory] im _Benutzerhandbuch_.

## Lastenausgleich

Sie können den Lastenausgleich über verschiedene Knoten hinweg unterstützen, indem Sie für die MySQL-Datenbank und die Redis-Instanz sekundäre Verbindungen aktivieren.

Adobe Commerce kann mehrere Datenbanken oder Redis-Instanzen asynchron lesen. Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, können Sie die sekundären Verbindungen konfigurieren, indem Sie die [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) und [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) -Werte in `.magento.env.yaml` -Datei. Nur ein Knoten muss Lese- und Schreibvorgänge-Traffic verarbeiten, sodass die Variablen auf `true` führt zu einer sekundären Verbindung für schreibgeschützten Traffic. Legen Sie die Werte auf `false` , um ein vorhandenes schreibgeschütztes Verbindungs-Array aus dem `env.php` -Datei.

Beispiel der `.magento.env.yaml` Datei:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[global]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/global-options.html
[inventory]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html
[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://developer.adobe.com/commerce/php/module-reference/module-async-order/
[DeferredTotalCalculating]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
