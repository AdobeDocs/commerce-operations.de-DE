---
title: Best Practices zur Änderung von PHP-Code von Kern- und Drittanbietern
description: Erfahren Sie, wie und wann Adobe Commerce und PHP-Code von Drittanbietern geändert werden.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
source-git-commit: ab02552939d595627f0de83b8508c7cd21777642
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Best Practices zum Ändern oder Überschreiben von Kern- und Drittanbieter-PHP-Code

In diesem Dokument werden Best Practices beschrieben, wenn die Notwendigkeit auftritt, die Funktionalität, das Ergebnis oder die Eingabe von Code zu ändern, den Sie nicht erstellt haben oder den Sie nicht direkt steuern. Anders ausgedrückt: Core-Code und Drittanbieter-Code. Dieses Dokument konzentriert sich in erster Linie auf Backend-PHP-Code.

## Methoden zum Ändern des Codes

Beim Ändern des Codes ist es wichtig, den Umfang Ihrer Änderungen zu berücksichtigen. Der &quot;Umfang&quot;der Änderungen bezieht sich auf die weit reichenden Auswirkungen der Codeänderungen. Als Best Practice wird empfohlen, die Entscheidung für den Abschluss der Implementierung auf der Grundlage der Option zu treffen, die den geringsten Platzbedarf und die geringste Ressourcennutzung aufweist. Je breiter die Codeüberschreibungen sind, desto mehr weicht ein Entwicklungsteam von der Adobe Commerce-Kernfunktionalität ab, wodurch sich die Wahrscheinlichkeit von Fehlern erhöht und der Aufwand für die zukünftige Pflege der Codebasis erhöht wird.

### Patch

Ein Patch ist eine Datei, die Anweisungen zum direkten Ändern des Codes in einer Datei enthält, die nicht unter der direkten Kontrolle des Entwicklungsteams steht. Dies ist eine Option, die normalerweise als letztes Mittel betrachtet werden sollte, wenn keine anderen Optionen vorhanden sind. Patches sollen eine temporäre Lösung sein. Wenn Sie ein Pflaster als allgemeine Best Practice erstellen müssen, entfernen Sie das Pflaster innerhalb der folgenden 2-4 Wochen zugunsten einer dauerhafteren Lösung. 

Pflaster brechen leicht. Wenn die Dateien, die der Patch als Ziel hat, aktualisiert werden, führt dies oft dazu, dass der Patch nicht mehr funktioniert. Das liegt daran, dass eine Patch-Datei Zeilennummern und Spaltennummern enthält, die explizit angeben, was durch den Patch geändert werden soll. Wenn etwas nicht mit dem übereinstimmt, was der Patch erwartet hat, wird er nicht mehr angewendet und der Code wird beschädigt.

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

#### Was kann mit einem Patch geändert werden?

Alles. Jedes Zeichen in einer Zieldatei kann wörtlich geändert werden. Patches sind nicht auf einen bestimmten Dateityp oder eine bestimmte Codesprache beschränkt. Normalerweise würden Sie einen Patch verwenden, um Dateien innerhalb der `vendor` Verzeichnis. 

#### Verwendung eines Pflasters

Wenn Sie erkennen, dass es keine andere Option gibt. Wenn der Anbieter beispielsweise noch keine Fehlerbehebung für den Code veröffentlicht, können Sie einen Patch verwenden, um das Problem vorübergehend zu beheben, während auf eine dauerhafte Lösung gewartet wird.

#### Nachteile

Pflaster brechen leicht. Sobald sich der zielgerichtete Code ändert, funktioniert der Patch nicht mehr. Sie sollen nur eine kurzfristige Lösung sein.

### Präferenz

Eine Präferenz ist ein Konzept, das in die Adobe Commerce-Plattform integriert wurde. Es ist im Wesentlichen ein &quot;PHP-Klassenersatz&quot;.

Die Adobe Commerce-Plattform verwendet einen &quot;Objektmanager&quot;, um PHP-Klassen zu instanziieren, da sie PHP-Klassen nicht mit dem neuen Keyword instanziiert, wie es in herkömmlichen PHP-Anwendungen der Fall ist. Stattdessen verweist der Objektmanager auf den Namen der zu instanziierenden PHP-Klasse gegenüber einer kompilierten Konfiguration, um zu bestimmen, ob ein Modul eine Voreinstellung für die ursprüngliche Klasse festgelegt hat. Wenn eine Voreinstellung für die PHP-Klasse gefunden wird, instanziiert der Objektmanager stattdessen die angegebene Klasse.

Es sollte beachtet werden, dass (in der Regel) die neue PHP-Klasse, die die ursprüngliche PHP-Klasse ersetzt, erweitert/erbt von der ursprünglichen PHP-Klasse. Dies geschieht aus mehreren Gründen:

- Um sicherzustellen, dass die Abhängigkeitseinfügung/Typhinweise eingehalten wird. Andernfalls tritt ein schwerwiegender Fehler auf und die Anwendung bricht ab.
- Um das minimale Schreiben von Code zu ermöglichen. Wenn die ursprüngliche PHP-Klasse zehn Methoden enthält, Sie aber nur eine Methode überschreiben müssen, können Sie normalerweise eine Methode allein ändern und die anderen neun Methoden intakt lassen. Dies ist wichtig, damit Sie Aktualisierungen der Kernfunktionalität nicht blockieren, da die Plattform auf neue Versionen aktualisiert wird.

#### Präferenz deklarieren

Es ist ein ziemlich einfacher Prozess, eine Präferenz zu deklarieren. Eine einzelne Codezeile muss zu einem `di.xml` -Datei in einem -Modul. Dies kann global oder innerhalb eines beliebigen Adobe Commerce-&quot;Bereichs&quot;erfolgen, z. B. `frontend`, `adminhtml`, `graphql`, `webapi_rest`, und `crontab`.

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

#### Was kann mit einer Voreinstellung geändert werden

Nur PHP-Klassen können mit einer Präferenz überschrieben werden. Innerhalb der PHP-Klasse können Sie öffentliche und geschützte Methoden und Eigenschaften ändern. Bei öffentlichen und geschützten Methoden können Sie die -Methode vollständig außer Kraft setzen oder die Argumente ändern, die in die ursprüngliche übergeordnete Methode eingehen (oder aus dem Ergebnis herauskommen).

Private Methoden können technisch nicht überschrieben werden. Sie können jedoch einen eigenen Ersatz für die ursprüngliche private Methode erstellen. Sie können ihm sogar einen beliebigen Namen geben, Sie können auch den ursprünglichen Namen verwenden. Es spielt keine Rolle, da eine private Methode nur in der eigentlichen Datei vorhanden ist, die sie enthält. Um eine private Methode zu überschreiben, müssen Sie die öffentliche oder geschützte Methode überschreiben oder ändern, die die ursprüngliche private Methode aufruft, und Sie müssen stattdessen Ihre eigene Funktion ersetzen.

#### Verwendung einer Voreinstellung

Wieder sollten Sie Voreinstellungen verwenden, wenn keine andere Option vorhanden ist und Sie Ihr Ziel nicht mit Abhängigkeitsinjektion, einem Plug-in oder einem Beobachter erreichen können. Manchmal benötigen Sie eine Voreinstellung, wenn Sie private oder geschützte Methoden oder Eigenschaften ändern oder überschreiben müssen. Es ist darauf hinzuweisen, dass die Präferenzen sparsam verwendet werden sollten. Sie sind eine ziemlich &quot;gierige&quot; Methode, die Anwendung zu ändern und Sie übernehmen effektiv die Eigentümerschaft der PHP-Klasse. Dies kann zu Konflikten mit Drittanbietermodulen führen und Aktualisierungen der Kernklasse blockieren und zu schwer zu diagnostizierenden Fehlern führen. Die Adobe Commerce-Plattform wurde entwickelt, um andere Wege einzuschließen, durch die Änderungen am zugrunde liegenden Code mit geringerem Platzbedarf vorgenommen werden können.

#### Nachteile

Voreinstellungen sind eine gute Möglichkeit, Code zu ändern. Sie sollten nur verwendet werden, wenn keine anderen Optionen vorhanden sind. Voreinstellungen können oft zu Konflikten innerhalb der Codebase führen und, schlimmer noch, sie können Kernaktualisierungen blockieren, die bei Plattformaktualisierungen auftreten. 

### Beobachter

Ein Beobachter ist das Konzept eines Ereignis-Listeners, das in vielen Anwendungen, Plattformen, Bibliotheken und Programmiersprachen vorkommt. Das Konzept ist nicht auf die Adobe Commerce-Plattform beschränkt. Beobachter sind seit Magento 1 in die Plattform gebacken und gelten als Hauptauswahl für die Änderung von Kerncode und Drittanbietercode. 

Die Core-Codebase und alle Module von Drittanbietern können ein Ereignis an einer bestimmten Stelle im Code senden. Der Beobachter, der in einem `events.xml` -Datei und überwacht nach Namen das gesendete Ereignis, kann auf globaler Ebene funktionieren oder auf einen beliebigen Adobe Commerce-&quot;Bereich&quot;beschränkt sein, z. B. `frontend`, `adminhtml`, `graphql`, `webapi_rest`, und `crontab`.

#### Deklarieren eines Beobachters

Beobachter können in einer globalen oder gebietsspezifischen `events.xml` -Datei.

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

#### Was kann mit einem Beobachter geändert werden

Beobachter gelten nur für PHP-Code innerhalb der Adobe Commerce-Plattform. Sie können nur die spezifischen Daten und Objekte ändern, die mit dem Ereignisversand übergeben werden.

#### Verwendung eines Beobachters

Wann immer verfügbar! Wäre die Beobachter breiter verfügbar und flexibler, würden sie die Nummer zwei in dieser Liste nehmen. Beobachter haben weniger Verarbeitungsaufwand als Plugins, sie sind weniger verfügbar und weniger flexibel.

#### Nachteile

Beobachter eignen sich hervorragend zum Abfangen und Ändern von Code, doch muss der Versand der Ereignisse in den Kern- oder Drittanbieter-Code eingefügt werden, damit er für Ihren Code verfügbar ist. Das macht die Verwendung von Beobachtern etwas eingeschränkt. Sie sind auf Ereignisse beschränkt, die ein Entwickler in den Code einbeziehen konnte.

Ein weiterer begrenzender Faktor für Beobachter ist, dass das gesendete Ereignis nur Zugriff auf die spezifischen Daten und Objekte bietet, die der Entwickler für die Weiterleitung an das Ereignis festgelegt hat.

### Plugin

Ein Plug-in ist ein flexibles Konzept, das auf der Adobe Commerce-Plattform eingeführt wurde. Es ermöglicht Ihnen, alle öffentlichen PHP-Methoden zu erfassen, zu ersetzen und zu ändern. Mithilfe von Plug-ins können Sie die Argumente ändern, die in einer Methode vor der Ausführung der Targeting-Methode eingegeben werden, das Ergebnis nach der Ausführung der Targeting-Methode ändern oder die Targeting-Methode vollständig ersetzen. Sie können viele Methoden einer zielgerichteten PHP-Klasse in einer einzelnen Plug-in-Datei ändern. Außerdem können Sie die `$subject` -Argument, um alle öffentlichen Methoden auszuführen, die in der Ziel-PHP-Klasse vorhanden sind.

#### Deklarieren eines Plug-ins

Plug-ins können in einem globalen oder gebietsspezifischen `di.xml` -Datei.

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

#### Was kann mit einem Plug-in geändert werden

Diese Funktionalität steht nur für PHP-Klassen zur Verfügung. Sie können die Eingabe oder Ausgabe einer öffentlichen Methode ändern und ein Plug-in verwenden, um andere Funktionen Trigger. Wenn mehrere Plug-ins auf dieselbe PHP-Klasse abzielen, kann eine Sortierreihenfolge für die Ausführung von Plug-ins festgelegt werden, damit Ihr Plug-in vor oder nach anderen Plug-ins ausgeführt werden kann.

#### Verwendung eines Plug-ins

Wann immer der Abhängigkeitsersatz nicht verfügbar ist. Plug-ins werden häufig in der gesamten Core-Codebase und im Drittanbieter-Code verwendet und können häufig in Ihrem eigenen benutzerdefinierten Code verwendet werden. Wenn Sie Funktionen ändern müssen, die nicht Ihrem benutzerspezifischen Code gehören oder von ihm gesteuert werden, ist normalerweise ein Plug-in der richtige Weg.

#### Nachteile

Geschützte Methoden oder Eigenschaften können nicht geändert werden. Der Verarbeitungsaufwand ist höher als der eines Beobachters. Das ist nicht wirklich ein Argument, keine Plugins zu verwenden, der Unterschied ist trivial. Dies ist jedoch ein guter Gedanke.

### Austausch von Abhängigkeiten

Die Abhängigkeitsinjektion ist ein standardmäßiges objektorientiertes Kodierungskonzept, bei dem Sie Ihre erforderlichen Abhängigkeiten mit dem Konstruktor in eine Klasse übergeben. Die Adobe Commerce-Plattform geht jedoch noch einen Schritt weiter, indem sie mehrere Möglichkeiten bietet, Abhängigkeiten durch XML zu ersetzen. Im Wesentlichen, die Ersetzung der Abhängigkeit. Der Austausch von Abhängigkeiten ist nicht für jede Situation geeignet, ermöglicht jedoch ein minimales Code-Schreiben, geringen Verwaltungsaufwand und eine engmaschige Zielgruppenbestimmung nur für bestimmte Codeabschnitte. Sie können private und geschützte Methoden mit der Ersetzung von Abhängigkeiten ändern.

#### Verwenden des Abhängigkeitsersatzes

Der Austausch von Abhängigkeiten kann global oder gebietsspezifisch erfolgen.

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

#### Was kann mit dem Abhängigkeitsersatz geändert werden?

Öffentliche, geschützte und private Methoden können mit der Ersetzung der Abhängigkeit geändert werden. Wie bei einem Plug-in können Sie die eingehenden Argumente ändern, die Funktion vollständig ersetzen oder die Ausgabe der Funktion ändern.

#### Verwendung des Abhängigkeitsersatzes

Dies ist eine gute erste Option, bei der das gewünschte Ziel tatsächlich erreicht wird, vorausgesetzt, dass zur Implementierung nichts zu Kompliziertes getan werden muss.

#### Nachteile

Nicht viele. Es ist nicht in jeder Situation verwendbar. Der wesentliche Nachteil besteht darin, dass Sie die Originalklasse erweitern müssen, die die zu ändernde Funktion enthält. Dies widerspricht dem Prinzip &quot;Komposition über Vererbung&quot;.
