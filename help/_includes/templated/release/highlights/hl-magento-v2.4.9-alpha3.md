---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.9-alpha3)

## Highlights in v2.4.9-alpha3

Die folgenden Highlights gelten für die Magento Open Source-Version 2.4.9-alpha3.

### Braintree

#### Vaulting Google Pay über den Kontobereich

In Magento 2.4.9-alpha3 können Kundinnen und Kunden ihre Google Pay Cards jetzt über den Kontobereich tresoren, wenn Google Pay Vault in Braintree aktiviert ist. Tresorkarten erscheinen unter gespeicherten Zahlungsmethoden, können für zukünftige Käufe an der Kasse verwendet werden und können vom Kunden gelöscht werden. Dies erweitert die Vaulting-Unterstützung über Cards und PayPal hinaus auf Google Pay.

_BUNDLE-3459_

#### Verknüpfen der Magento-Bestellung mit der Braintree Portal-Bestellung

In Magento 2.4.9-alpha3 wurde nun ein Braintree Portal-Link zu den Bestelldetails in Magento Admin hinzugefügt. Wenn Sie auf den Link klicken, wird die zugehörige Transaktion im Braintree-Portal (auf einer neuen Registerkarte) unter Verwendung der Händler-ID und der Transaktions-ID aus der Magento-Bestellung geöffnet. Dies ermöglicht einen direkten Querverweis, ohne sich separat bei beiden Systemen anzumelden.

_BUNDLE-3461_

#### Real-Time Account Updater (RTAU)

Die Funktion Real-Time Account Updater (RTAU) in Magento 2.4.9-alpha3 für Braintree stellt sicher, dass die Details von Visa-, MasterCard- und Discover-Karten in Vault automatisch aktualisiert werden, wenn die Gültigkeit der Karten endet oder sie ersetzt werden. Dadurch werden fehlgeschlagene Zahlungen minimiert, Magento Vault wird aktuell gehalten und nicht unterstützte Typen (Prepaid, Apple Pay, Google Pay) werden fehlerfrei übersprungen.

_BUNDLE-3462_

#### Unterstützung des ELO-Kartentyps für Braintree-Kartenzahlungen

In Magento 2.4.9-alpha3 wurde die Unterstützung für den ELO-Kartentyp zu Braintree Payments hinzugefügt. Administratoren können jetzt ELO in der Kreditkartenkonfiguration aktivieren, und Kunden können erfolgreich Bestellungen mit ELO-Karten an der Kasse aufgeben, wodurch nahtlose Transaktionen über Braintree sichergestellt werden.

_BUNDLE-3464_

### Framework

#### Migration von RabbitMQ zu Apache ActiveMQ

_AC-14558_

#### Aktualisieren der chart.js-Abhängigkeit auf die neueste Version

Die Chart.js-Abhängigkeit wird auf die neueste Version 4.5.0 aktualisiert

_AC-15133 - [GitHub-Code-Beitrag](https://github.com/magento/magento2/commit/657f983e)_

#### Migration von Laminas MVC

Adobe Commerce hat eine native MVC-Implementierung eingeführt, die das alte Laminas-MVC ersetzt, um die langfristige Kompatibilität und Stabilität über PHP 8.5 hinaus sicherzustellen. Diese Änderung stärkt die Leistung, reduziert externe Abhängigkeiten und bietet eine zukunftsfähigere Grundlage für Commerce

_AC-15160_
