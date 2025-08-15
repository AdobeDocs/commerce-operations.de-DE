---
title: Best Practices für die Änderung von Kern- und PHP-Code von Drittanbietern
description: Erfahren Sie, wie und wann Sie den Kern-Adobe Commerce und PHP-Code von Drittanbietern ändern.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Best Practices für die Änderung oder Außerkraftsetzung von PHP-Code von Kernkomponenten und Drittanbietern

In diesem Dokument werden Best Practices beschrieben, wenn die Notwendigkeit besteht, die Funktionalität, das Ergebnis oder die Eingabe von Code zu ändern, den Sie nicht erstellt haben oder nicht direkt steuern. Mit anderen Worten, Kern-Code und Drittanbieter-Code. Dieses Dokument konzentriert sich in erster Linie auf Backend-PHP-Code.

## Methoden zum Ändern von Code

Beim Ändern von Code ist es wichtig, den Umfang Ihrer Änderungen zu berücksichtigen. Der „Umfang“ der Änderungen bezieht sich darauf, wie weit reichend die Auswirkungen der Code-Änderungen sind. Entscheiden Sie am besten anhand der Option mit dem geringsten Platzbedarf und der geringsten Ressourcennutzung, wie die Implementierung letztendlich abgeschlossen wird. Je weiter reichend die Code-Überschreibungen sind, desto mehr weicht ein Entwicklungs-Team von der Kernfunktionalität von Adobe Commerce ab, was die Wahrscheinlichkeit von Fehlern erhöht und den Aufwand für die zukünftige Pflege der Code-Basis erhöht.

### Fleck

Ein Patch ist eine Datei mit Anweisungen zum direkten Ändern des Codes innerhalb einer Datei, die nicht unter der direkten Kontrolle des Entwicklungs-Teams steht. Dies ist eine Option, die normalerweise als letztes Mittel in Betracht gezogen werden sollte, wenn keine anderen Optionen vorhanden sind. Patches sind als temporäre Lösung gedacht. Wenn Sie ein Pflaster erstellen müssen, entfernen Sie das Pflaster als allgemeine Best Practice zugunsten einer dauerhafteren Lösung innerhalb der folgenden 2-4 Wochen. 

Patches zerbrechen leicht. Wenn die Dateien, auf die sich der Patch bezieht, aktualisiert werden, führt dies oft dazu, dass der Patch nicht mehr funktioniert. Dies liegt daran, dass eine Patch-Datei Zeilennummern und Spaltennummern enthält, die genau angeben, was durch den Patch geändert werden soll. Wenn etwas nicht dem entspricht, was der Patch erwartet hat, wird es nicht mehr angewendet und bricht den Code.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### Was mit einem Patch geändert werden kann

Alles. Es können buchstäblich alle Zeichen in einer Zieldatei geändert werden. Patches sind nicht auf einen bestimmten Dateityp oder eine bestimmte Codesprache beschränkt. Normalerweise würden Sie einen Patch verwenden, um Dateien im `vendor` Verzeichnis als Ziel festzulegen. 

#### Wann ein Pflaster zu verwenden ist

Wenn Sie erkennen, dass keine andere Option existiert. Wenn beispielsweise der Anbieter noch keine Fehlerbehebung für den Code veröffentlicht hat, können Sie einen Patch verwenden, um das Problem vorübergehend zu beheben, während Sie auf eine dauerhafte Lösung warten.

#### Nachteile

Patches zerbrechen leicht. Sobald sich der Ziel-Code ändert, funktioniert der Patch nicht mehr. Sie sollen nur eine kurzfristige Lösung sein.

### Voreinstellung

Eine Präferenz ist ein Konzept, das in die Adobe Commerce-Plattform integriert ist. Es handelt sich im Wesentlichen um einen „PHP-Klassenersatz“.

Die Adobe Commerce-Plattform verwendet einen „Object Manager“, um PHP-Klassen zu instanziieren, da PHP-Klassen nicht mit dem neuen Keyword instanziiert werden, wie dies in herkömmlichen PHP-Anwendungen der Fall ist. Stattdessen verweist der Object Manager den Namen der PHP-Klasse, die gegen eine kompilierte Konfiguration instanziiert werden soll, um zu ermitteln, ob ein Modul eine Voreinstellung für die ursprüngliche Klasse deklariert hat. Wenn eine Voreinstellung für die PHP-Klasse gefunden wird, instanziiert der Objekt-Manager stattdessen die angegebene Klasse.

Es sollte beachtet werden, dass (normalerweise) die neue PHP-Klasse, die die ursprüngliche PHP-Klasse ersetzt, von der ursprünglichen PHP-Klasse erweitert/erbt. Dies geschieht aus mehreren Gründen:

- Um sicherzustellen, dass Abhängigkeiten beim Einschleusen/Hinweisen auf den Typ eingehalten werden. Andernfalls tritt ein schwerwiegender Fehler auf und die Anwendung wird unterbrochen.
- , um nur minimales Schreiben von Code zu ermöglichen. Wenn die ursprüngliche PHP-Klasse zehn Methoden enthält, Sie aber nur eine Methode überschreiben müssen, können Sie normalerweise eine Methode allein ändern und die anderen neun Methoden intakt lassen. Dies ist wichtig, um sicherzustellen, dass Sie Aktualisierungen der Kernfunktionen nicht blockieren, wenn die Plattform auf neue Versionen aktualisiert wird.

#### Voreinstellung deklarieren

Es ist ein ziemlich einfacher Prozess, eine Präferenz zu deklarieren. Zu einer `di.xml`-Datei innerhalb eines Moduls muss eine einzelne Codezeile hinzugefügt werden. Dies kann global oder in jedem Adobe Commerce-„Bereich“ erfolgen, z. B. `frontend`, `adminhtml`, `graphql`, `webapi_rest` und `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### Was mit einer Voreinstellung geändert werden kann

Nur PHP-Klassen können mit einer Voreinstellung überschrieben werden. Innerhalb der PHP-Klasse können Sie öffentliche und geschützte Methoden und Eigenschaften modifizieren. Bei öffentlichen und geschützten Methoden können Sie die Methode vollständig überschreiben oder die Argumente für die ursprüngliche übergeordnete Methode (oder das Ergebnis, das aus ihr hervorgeht) ändern.

Private Methoden können technisch nicht überschrieben werden. Sie können jedoch eine eigene Ersetzung für die ursprüngliche private Methode erstellen. Sie können ihm sogar einen beliebigen Namen geben, Sie können auch den ursprünglichen Namen verwenden. Dies spielt keine Rolle, da eine private Methode nur in der eigentlichen Datei vorhanden ist, die sie enthält. Um eine private Methode zu überschreiben, müssen Sie die öffentliche oder geschützte Methode überschreiben oder ändern, die die ursprüngliche private Methode aufruft, und Sie müssen an ihrer Stelle Ihre eigene Funktionalität ersetzen.

#### Wann eine Voreinstellung verwendet werden soll

Auch hier sollten Sie Voreinstellungen verwenden, wenn keine andere Option existiert und Sie Ihr Ziel mit Dependency Injection, einem Plug-in oder einem Beobachter nicht erreichen können. Manchmal ist eine Präferenz erforderlich, wenn Sie private oder geschützte Methoden oder Eigenschaften ändern oder überschreiben müssen. Es ist darauf hinzuweisen, dass die Präferenzen sparsam genutzt werden sollten. Sie sind eine ziemlich „gierige“ Methode, um die Anwendung zu ändern, und Sie übernehmen effektiv den Besitz der PHP-Klasse. Dies kann zu Konflikten mit Drittanbietermodulen führen, Aktualisierungen der Hauptklasse blockieren und zu schwer diagnostizierbaren Fehlern führen. Die Adobe Commerce-Plattform wurde so konzipiert, dass sie andere Möglichkeiten beinhaltet, um Änderungen am zugrunde liegenden Code mit einem kleineren Platzbedarf vorzunehmen.

#### Nachteile

Voreinstellungen sind eine gierige Möglichkeit, Code zu ändern und sollten nur verwendet werden, wenn andere Optionen nicht vorhanden sind. Voreinstellungen können oft zu Konflikten innerhalb der Code-Basis führen und - was noch schlimmer ist - Kernaktualisierungen blockieren, die bei Platform-Upgrades auftreten. 

### Beobachter

Ein Beobachter ist das Konzept eines Ereignis-Listeners, wie er in vielen Anwendungen, Plattformen, Bibliotheken und Programmiersprachen verwendet wird. Dieses Konzept ist nicht auf die Adobe Commerce-Plattform beschränkt. Beobachter werden seit den Tagen von Magento 1 in die Plattform integriert und gelten als Hauptentscheidung für die Änderung von Kern- und Drittanbieter-Code. 

Die Kern-Code-Basis und alle Drittanbietermodule können ein Ereignis an einer ausgewählten Stelle im Code senden. Der Beobachter, der in einer `events.xml` deklariert ist und das gesendete Ereignis nach Namen überwacht, kann auf globaler Ebene arbeiten oder auf einen beliebigen Adobe Commerce-„Bereich“ beschränkt sein, z. B. `frontend`, `adminhtml`, `graphql`, `webapi_rest` und `crontab`.

#### Wie man einen Beobachter erklärt

Beobachter können in einer globalen oder gebietsspezifischen `events.xml` konfiguriert werden.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### Was mit einem Beobachter geändert werden kann

Beobachter gelten nur für PHP-Code innerhalb der Adobe Commerce-Plattform. Sie können nur die spezifischen Daten und Objekte ändern, die mit dem Ereignis-Dispatch übergeben werden.

#### Verwendung eines Beobachters

Wann immer verfügbar! Wären die Beobachter breiter verfügbar und flexibler, dann würden sie auf Platz zwei dieser Liste stehen. Beobachter haben weniger Verarbeitungsaufwand als Plug-ins, sie sind weniger verfügbar und weniger flexibel.

#### Nachteile

Obwohl Beobachter eine hervorragende Möglichkeit zum Abfangen und Ändern von Code sind, muss der Versand der Ereignisse zum Kern- oder Drittanbieter-Code hinzugefügt werden, damit der Code darauf warten kann. Das macht das Konzept der Beobachter etwas eingeschränkt. Sie sind auf Ereignisse beschränkt, die ein Entwickler voraussehen konnte, um sie in den Code aufzunehmen.

Ein weiterer limitierender Faktor für Beobachter besteht darin, dass das Dispatch-Ereignis nur Zugriff auf die spezifischen Daten und Objekte bietet, die der Entwickler zusammen mit dem Ereignis weitergeben möchte.

### Plug-in

Ein Plug-in ist ein flexibles Konzept, das in der Adobe Commerce-Plattform eingeführt wird. Es ermöglicht das Abfangen, Ersetzen und Ändern von öffentlichen PHP-Methoden. Plug-ins ermöglichen es Ihnen, die Argumente einer Methode zu ändern, bevor die Zielmethode ausgeführt wird, das Ergebnis nach der Ausführung der Zielmethode zu ändern oder die Zielmethode vollständig zu ersetzen. Sie können viele Methoden einer PHP-Klasse innerhalb einer Plugin-Datei modifizieren. Außerdem können Sie das `$subject`-Argument verwenden, um alle öffentlichen Methoden auszuführen, die in der PHP-Zielklasse vorhanden sind.

#### Deklarieren eines Plug-ins

Plug-ins können in einer globalen oder bereichsspezifischen `di.xml`-Datei konfiguriert werden.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### Was mit einem Plug-in geändert werden kann

Diese Funktion ist nur für PHP-Zielklassen verfügbar. Sie können die Eingabe oder Ausgabe einer öffentlichen Methode ändern und ein Plug-in verwenden, um andere Funktionen Trigger. Wenn mehrere Plug-ins dieselbe PHP-Klasse ansprechen, kann eine Sortierreihenfolge für die Ausführung von Plug-ins festgelegt werden, damit Ihr Plug-in vor oder nach anderen Plug-ins ausgeführt werden kann.

#### Verwendung eines Plug-ins

Wann immer keine Abhängigkeitsersetzung verfügbar ist. Plug-ins werden häufig in der gesamten Code-Basis von Drittanbietern und in Ihrem eigenen benutzerspezifischen Code verwendet. In den meisten Fällen, in denen Sie Funktionen ändern müssen, die nicht Ihrem benutzerdefinierten Code gehören oder von diesem gesteuert werden, ist ein Plug-in der richtige Weg.

#### Nachteile

Geschützte Methoden oder Eigenschaften können nicht geändert werden. Der Verarbeitungsaufwand ist höher als der eines Beobachters. Das ist kein wirkliches Argument, keine Plugins zu verwenden, der Unterschied ist trivial. Das sollten Sie sich jedoch vor Augen halten.

### Ersetzung von Abhängigkeiten

Die Injektion von Abhängigkeiten ist ein standardmäßiges objektorientiertes Codierungs-Konzept, bei dem Sie Ihre erforderlichen Abhängigkeiten mit dem -Konstruktor in eine -Klasse übergeben. Die Adobe Commerce-Plattform geht jedoch noch einen Schritt weiter, indem sie mehrere Möglichkeiten bietet, Abhängigkeiten durch XML zu ersetzen. Im Wesentlichen Ersetzung von Abhängigkeiten. Der Ersatz von Abhängigkeiten ist nicht für jede Situation geeignet, ermöglicht jedoch minimales Schreiben von Code, geringen Overhead und Sie können nur exakte Code-Abschnitte gezielt auswählen. Sie können private und geschützte Methoden mit Ersetzung von Abhängigkeiten ändern.

#### Verwenden der Abhängigkeitsersetzung

Abhängigkeitsersatz kann global oder bereichsspezifisch erfolgen.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

Nachdem Sie diese Schritte ausgeführt haben, haben Sie das Verhalten einer privaten Methode erfolgreich geändert.

#### Was durch Ersetzen von Abhängigkeiten geändert werden kann

Öffentliche, geschützte und private Methoden können durch Ersetzen der Abhängigkeit geändert werden. Wie bei einem Plug-in können Sie die eingehenden Argumente ändern, die Funktion vollständig ersetzen oder die Ausgabe der Funktion ändern.

#### Verwendung der Abhängigkeitsersetzung

Dies ist eine gute erste Option, wenn das gewünschte Ziel tatsächlich erreicht werden würde, vorausgesetzt, es muss nichts zu komplexes getan werden, um es zu implementieren.

#### Nachteile

Nicht viele. Es ist nicht in jeder Situation brauchbar. Der Hauptnachteil besteht darin, dass Sie die ursprüngliche Klasse erweitern müssen, die die Funktionalität enthält, die Sie ändern möchten. Das widerspricht dem Prinzip „Komposition statt Vererbung“.
