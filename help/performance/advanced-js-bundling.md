---
title: Erweitert [!DNL JavaScript] Bundle
description: Erfahren Sie, wie das JavaScript-Bundling die Größe und Häufigkeit von Serveranfragen reduzieren kann.
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---

# Erweitert [!DNL JavaScript] Bundling

Bundle [!DNL JavaScript] -Module zur Verbesserung der Leistung geht es darum, zwei Dinge zu reduzieren:

1. Die Anzahl der Serveranforderungen.
1. Die Größe dieser Serveranforderungen.

In einer modularen Anwendung kann die Anzahl der Serveranforderungen Hunderte erreichen. Beispielsweise zeigt der folgende Screenshot nur den Anfang der Liste von [!DNL JavaScript] -Module, die auf der Startseite einer sauberen Installation geladen werden.

![Kein Bundling](../assets/performance/images/noBundling.png)

## Zusammenführung und Bündelung

Vorkonfiguriert, [!DNL Commerce] bietet zwei Möglichkeiten, die Anzahl der Serveranforderungen zu reduzieren: Zusammenführen und Bündeln. Diese Einstellungen sind standardmäßig deaktiviert. Sie können sie in der Admin-Benutzeroberfläche in aktivieren **[!UICONTROL Stores]** > **Einstellungen** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** oder über die Befehlszeile.

![Bundle](../assets/performance/images/bundlingImage.png)

### Grundlegendes Bundling

So aktivieren Sie das integrierte Bundling über die Befehlszeile:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Dies ist ein natives [!DNL Commerce] -Mechanismus, der alle im System vorhandenen Assets kombiniert und unter Bundles derselben Größe verteilt (bundle_0.js, bundle_1.js ... bundle_x.js):

![[!DNL Commerce] Bundling](../assets/performance/images/magentoBundling.png)

Besser, aber der Browser lädt trotzdem ALLE [!DNL JavaScript] Bundles, nicht nur die benötigten.

[!DNL Commerce] Durch das Bundling wird die Anzahl der Verbindungen pro Seite reduziert, aber für jede Seitenanfrage werden alle Bundles geladen, selbst wenn die angeforderte Seite nur von Dateien innerhalb eines oder zweier Bundles abhängig sein kann. Die Leistung verbessert sich, nachdem der Browser die Bundles zwischengespeichert hat. Da der Browser diese Bundles jedoch synchron lädt, besucht der Benutzer zum ersten Mal eine [!DNL Commerce] Das Rendern und Schaden des Benutzererlebnisses kann eine Weile dauern.

### Grundlegende Zusammenführung

So aktivieren Sie die integrierte Zusammenführung über die Befehlszeile:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Mit diesem Befehl werden alle synchronen [!DNL JavaScript] Dateien in eine Datei. Die Aktivierung der Zusammenführung ohne die Aktivierung der Bündelung ist nicht nützlich, da [!DNL Commerce] verwendet RequireJS. Wenn Sie das Bundling nicht aktivieren, [!DNL Commerce] führt nur Zusammenführungen von RequireJS und seiner Konfiguration durch. Wenn Sie sowohl das Bundling als auch das Zusammenführen aktivieren, [!DNL Commerce] erstellt eine [!DNL JavaScript] Datei:

![Zusammenführung in der realen Welt](../assets/performance/images/magentoMergingDevWorld.png)

## Reale Renderzeiten

Die vorherigen gebündelten und zusammengeführten Ladezeiten sehen in einer Entwicklungsumgebung großartig aus. Aber in der realen Welt können viele Dinge das Rendering verlangsamen: langsame Verbindungen, große Verbindungsschwellen, begrenzte Netzwerke. Darüber hinaus werden Mobilgeräte nicht so schnell wie Desktops gerendert.

Um Ihre Storefront-Implementierung für die reale Welt zu testen und vorzubereiten, empfehlen wir, mit dem nativen Chrome-Einschränkungsprofil &quot;Slow 3G&quot;zu testen. Mit Slow 3G spiegeln unsere vorherigen gebündelten Ausgabezeiten jetzt die Verbindungsprobleme vieler Benutzer wider:

![Echtzeit-Bündelung](../assets/performance/images/magentoBundlingRealWorld.png)

Bei langsamer 3G-Konnektivität dauert es etwa 44 Sekunden, alle Bundles für die Homepage einer sauberen [!DNL Commerce] Installation.

Dasselbe gilt für das Zusammenführen der Bundles in einer Datei. Benutzer können weiterhin etwa 42 Sekunden auf das erste Laden der Seite warten, wie im folgenden Beispiel gezeigt:

![Zusammenführung in der realen Welt](../assets/performance/images/magentoMergingRealWorld.png)

Mit einem fortschrittlicheren Ansatz für [!DNL JavaScript] Bundling, können wir diese Ladezeiten verbessern.

## Erweitertes Bundling

Denken Sie daran, das Ziel von [!DNL JavaScript] Beim Bundling wird die Anzahl und Größe der angeforderten Assets für jede im Browser geladene Seite reduziert. Dazu möchten wir unsere Bundles erstellen, sodass jede Seite in unserem Store nur ein gemeinsames Bundle und ein seitenspezifisches Bundle für jede aufgerufene Seite herunterladen muss.

Eine Möglichkeit, dies zu erreichen, besteht darin, Ihre Bundles nach Seitentypen zu definieren. Sie können Kategorien [!DNL Commerce]enthält Seiten in verschiedene Seitentypen, darunter Kategorie, Produkt, CMS, Kunde, Warenkorb und Checkout. Jede Seite, die in einen dieser Seitentypen kategorisiert ist, verfügt über einen anderen Satz von RequireJS-Modulabhängigkeiten. Wenn Sie Ihre RequireJS-Module nach Seitentyp bündeln, erhalten Sie nur eine Handvoll Pakete, die die Abhängigkeiten einer beliebigen Seite in Ihrem Store abdecken.

Sie können beispielsweise mit einem Bundle für die allen Seiten gemeinsamen Abhängigkeiten, einem Bundle für nur CMS-Seiten, einem Bundle für Nur-Katalog-Seiten, einem weiteren Bundle für Nur-Suche-Seiten und einem Bundle für Checkout-Seiten enden.

Sie können Bundles auch nach Zweck erstellen: für allgemeine Funktionen, produktbezogene Funktionen, Versandfunktionen, Checkout-Funktionen, Steuern und Formularvalidierungen. Wie Sie Ihre Bundles definieren, hängt von Ihnen und der Struktur Ihres Stores ab. Möglicherweise funktionieren einige Bundling-Strategien besser als andere.

A clean [!DNL Commerce] -Installation ermöglicht es, ausreichend gute Leistung zu erzielen, indem Bundles nach Seitentypen aufgeteilt werden. Einige Anpassungen erfordern jedoch möglicherweise eine tiefere Analyse und andere Asset-Verteilungen.

### Erforderliche Tools

Für die folgenden Schritte müssen Sie die folgenden Tools installieren und mit ihnen vertraut sein:

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) (optional)

### Beispielcode

Vollständige Versionen des in diesem Artikel verwendeten Beispielcodes finden Sie hier:

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Teil 1: Erstellen einer Bundle-Konfiguration

#### 1\. Hinzufügen einer Datei &quot;build.js&quot;

Erstellen Sie eine `build.js` in der Datei [!DNL Commerce] Stammverzeichnis. Diese Datei enthält die gesamte Build-Konfiguration für Ihre Bundles.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Später werden wir die `optimize:` Einstellung von_ `none` nach `uglify2` zum Minimieren der Bundle-Ausgabe. Während der Entwicklung können Sie es jedoch vorerst auf `none` um schnellere Builds sicherzustellen.

#### 2\. Hinzufügen von RequireJS-Abhängigkeiten, -Shims, -Pfaden und -Landkarten

Fügen Sie die folgenden RequireJS-Build-Konfigurationsknoten hinzu: `deps`, `shim`, `paths`, und `map`in Ihre Build-Datei ein:

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },
})
```

#### 3\. Aggregieren Sie die Instanzwerte &quot;required.js&quot;

In diesem Schritt müssen Sie das gesamte `deps`, `shim`, `paths`, und `map` Konfigurationsknoten aus dem Store `requirejs-config.js` in die entsprechenden Knoten in Ihrer `build.js` -Datei. Dazu können Sie die **[!UICONTROL Network]** im Bedienfeld &quot;Entwicklertools&quot;Ihres Browsers und navigieren Sie zu einer beliebigen Seite in Ihrem Store, z. B. zur Startseite. Auf der Registerkarte &quot;Netzwerk&quot;sehen Sie die Instanz Ihres Stores für die `requirejs-config.js` -Datei oben, hier hervorgehoben:

![RequireJS-Konfiguration](../assets/performance/images/RequireJSConfig.png)

In dieser Datei finden Sie mehrere Einträge für jeden Konfigurationsknoten (`deps`, `shim`, `paths`, `map`). Sie müssen diese verschiedenen Knotenwerte in den einzelnen Konfigurationsknoten Ihrer Datei &quot;build.js&quot;aggregieren. Wenn beispielsweise die Variable `requirejs-config.js` -Instanz hat Einträge für 15 separate `map` -Knoten, müssen Sie die Einträge für alle 15 Knoten in der `map` Knoten in `build.js` -Datei. Dasselbe gilt für das `deps`, `shim`, und `paths` Knoten. Ohne ein Skript zur Automatisierung dieses Prozesses kann es Zeit dauern.

Sie müssen den Pfad ändern `mage/requirejs/text` nach `requirejs/text` in `paths` Konfigurationsknoten wie folgt:

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. Modulknoten hinzufügen

Am Ende des `build.js` -Datei hinzufügen, die Module hinzufügen[] -Array als Platzhalter für die Bundles, die Sie später für Ihre Storefront definieren.

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },

    modules: [],
})
```

#### 5\. RequireJS-Abhängigkeiten abrufen

Sie können alle [!DNL RequireJS] Modulabhängigkeiten von den Seitentypen Ihres Stores durch Verwendung von:

1. [!DNL PhantomJS] über die Befehlszeile (vorausgesetzt, Sie verfügen über [!DNL PhantomJS] installiert).
1. JS-Befehl in der Browser-Konsole erforderlich.

#### Verwendung [!DNL PhantomJS]:

Im [!DNL Commerce] Stammverzeichnis erstellen Sie eine neue Datei mit dem Namen `deps.js` und kopieren Sie den unten stehenden Code. Dieser Code verwendet [!DNL [!DNL PhantomJS]], um eine Seite zu öffnen und zu warten, bis der Browser alle Seiten-Assets lädt. Anschließend werden alle [!DNL RequireJS] Abhängigkeiten für eine bestimmte Seite.

```javascript
"use strict";
var page = require('webpage').create(),
    system = require('system'),
    address;

if (system.args.length === 1) {
    console.log('Usage: $phantomjs deps.js url');
    phantom.exit(1);
} else {
    address = system.args[1];
    page.open(address, function (status) {
        if (status !== 'success') {
            console.log('FAIL to load the address');
        } else {
            setTimeout(function () {
                console.log(page.evaluate(function () {
                    return Object.keys(window.require.s.contexts._.defined);
                }));
                phantom.exit();
            }, 5000);
        }
    });
}
```

Öffnen Sie ein Terminal im [!DNL Commerce] Stammverzeichnis und führen Sie das Skript für jede Seite in Ihrem Store aus, die einen bestimmten Seitentyp darstellt:

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-presentation-pagetype-dependencies</i>
</pre>

Hier sind beispielsweise vier Seiten aus dem thematischen Beispiel-Store &quot;Luma&quot;, die die vier Seitentypen darstellen, die wir verwenden werden, um unsere vier Bundles (Homepage, Kategorie, Produkt, Warenkorb) zu erstellen:

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### So verwenden Sie die Browser-Konsole:

Wenn Sie [!DNL PhantomJS]können Sie den folgenden Befehl in der Browser-Konsole ausführen, während Sie die einzelnen Seitentypen in Ihrer Storefront anzeigen:

```shell
Object.keys(window.require.s.contexts._.defined)
```

Dieser Befehl (wird innerhalb der Variablen [!DNL PhantomJS] script) erstellt dieselbe Liste von [!DNL RequireJS] Abhängigkeiten und zeigt sie in der Browser-Konsole an. Der Nachteil dieses Ansatzes besteht darin, dass Sie Ihre eigenen Textdateien vom Typ Bundle/Seite erstellen müssen.

#### 6\. Ausgabe formatieren und filtern

Nach dem Zusammenführen [!DNL RequireJS] Abhängigkeiten von Textdateien vom Typ Seite verwenden, können Sie den folgenden Befehl für jede Abhängigkeitsdatei vom Typ Seite verwenden, um die Kommas in Ihren Dateien durch Zeilenumbrüche zu ersetzen:

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

Sie sollten auch alle Mixins für jede Datei entfernen, da Mixins Abhängigkeiten duplizieren. Verwenden Sie für jede Abhängigkeitsdatei den folgenden Befehl:

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. Identifizieren von eindeutigen und gemeinsamen Bundles

Das Ziel besteht darin, ein gemeinsames Bündel von [!DNL JavaScript] Dateien, die für alle Seiten benötigt werden. Auf diese Weise muss der Browser nur das gemeinsame Bundle zusammen mit einem oder mehreren bestimmten Seitentypen laden.

Öffnen Sie ein Terminal im [!DNL Commerce] Stammverzeichnis und verwenden Sie den folgenden Befehl, um zu überprüfen, ob Sie Abhängigkeiten haben, die Sie in separate Bundles aufteilen können:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Dieser Befehl führt die Abhängigkeiten im `bundle/*.txt` -Dateien.  Die Ausgabe zeigt auch die Anzahl der Dateien an, die jede Abhängigkeit enthalten:

```terminal
1 buildTools,
1 jquery/jquery.parsequery,
1 jsbuild,
2 jquery/jquery.metadata,
2 jquery/validate,
2 mage/bootstrap,
3 jquery
3 jquery/ui
3 knockoutjs/knockout
...
```

Diese Ausgabe zeigt Folgendes: `buildTools` ist eine Abhängigkeit in nur einer der Bundle/*.txt-Dateien. Die `jquery/jquery.metadata` Die Abhängigkeit befindet sich in zwei (2) Dateien und `es6-collections` ist in drei (3) Dateien enthalten.

Unsere Ausgabe zeigt nur drei Seitentypen (Homepage, Kategorie und Produkt) an, die uns Folgendes mitteilen:

- Drei Abhängigkeiten sind nur für einen Seitentyp eindeutig (erkennbar an der Zahl 1).
- Drei weitere Abhängigkeiten treten auf zwei Seitentypen auf (erkennbar an der Zahl 2).
- Die letzten drei Abhängigkeiten sind allen drei unserer Seitentypen gemein (erkennbar an der Zahl 3).

Dies sagt uns, dass wir die Seitenladegeschwindigkeit unseres Stores wahrscheinlich verbessern können, indem wir unsere Abhängigkeiten in verschiedene Bundles aufteilen, sobald wir wissen, welche Seitentypen welche Abhängigkeiten benötigen.

#### 8\. Erstellen einer Verteilungsdatei für Abhängigkeiten

Um herauszufinden, welche Seitentypen welche Abhängigkeiten benötigen, erstellen Sie eine neue -Datei in der [!DNL Commerce] Stammordner namens `deps-map.sh` und kopieren Sie den folgenden Code:

```shell
awk 'END {
 for (R in rec) {
   n = split(rec[R], t, "/")
   if (n > 1)
     dup[n] = dup[n] ? dup[n] RS sprintf("\t%-20s -->\t%s", rec[R], R) : \
       sprintf("\t%-20s -->\t%s", rec[R], R)
   }
 for (D in dup) {
   printf "records found in %d files:\n\n", D
   printf "%s\n\n", dup[D]
   }
 }
{
 rec[$0] = rec[$0] ? rec[$0] "/" FILENAME : FILENAME
}' bundle/*.txt
```

Sie finden das Skript auch unter [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

Öffnen Sie ein Terminal im [!DNL Commerce] -Stammverzeichnis und führen Sie die Datei aus:

```bash
bash deps-map.sh
```

Die Ausgabe aus diesem Skript, die auf unsere drei Beispielseitentypen angewendet wird, sollte etwa wie folgt aussehen (aber viel länger):

```terminal
bundle/product.txt   -->   buildTools,
bundle/category.txt  -->   jquery/jquery.parsequery,
bundle/product.txt   -->   jsbuild,

bundle/category.txt/bundle/homepage.txt -->    jquery/jquery.metadata,
bundle/category.txt/bundle/homepage.txt -->    jquery/validate,
bundle/category.txt/bundle/homepage.txt -->    mage/bootstrap,

bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery/ui,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> knockoutjs/knockout,
```

Diese Informationen reichen aus, um eine Bundle-Konfiguration zu erstellen.

#### 9\. Erstellen von Bundles in Ihrer Datei &quot;build.js&quot;

Öffnen Sie die `build.js` Konfigurationsdatei erstellen und Ihre Bundles zur `modules` Knoten. Jedes Bundle sollte die folgenden Eigenschaften definieren:

- `name`- der Name des Bundles. Beispiel: ein Name von `bundles/cart` generiert eine `cart.js` Bundle in einer `bundles` -Unterverzeichnis.

- `create`— eine boolesche Markierung zum Erstellen des Bundles (Werte: `true` oder `false`).

- `include`- ein Array von Assets (Zeichenfolgen), die als Abhängigkeiten für die Seite enthalten sind. RequireJS verfolgt alle Abhängigkeiten und schließt sie in das Bundle ein, es sei denn, dies ist ausgeschlossen.

- `exclude`- ein Array von Bundles oder Assets, die aus dem Bundle ausgeschlossen werden sollen.

```javascript
{
    name: 'bundles/catalog',
    create: true,
    include: [
        'addToWishlist',
        'priceBundle',
        'priceUtils',
        'priceOptions',
        'sticky',
        'productSummary',
        'slide'
    ],
    exclude: [
        'requirejs/require',
        'bundles/default',
        'mage/bootstrap'
    ],
}
```

In diesem Beispiel werden `mage/bootstrap` und `requirejs/require` Assets mit höherer Priorität für ihre wichtigsten Komponenten und Komponenten, die synchron geladen werden müssen. Die vorhandenen Bundles sind:

- `requirejs/require`—das einzige synchron geladene Bundle
- `mage/bootstrap`—Bootstrap-Bundle mit UI-Komponenten
- `bundles/default`—Standardpaket für alle Seiten erforderlich
- `bundles/cart`—Ein für die Warenkorbseite erforderliches Bundle
- `bundles/shipping`—allgemeines Bundle für Warenkorb- und Checkout-Seite (vorausgesetzt, dass der Checkout nie direkt geöffnet wird, wird die Checkout-Seite noch schneller geladen, wenn die Warenkorbseite zuvor geöffnet und das Versandpaket bereits geladen wurde)
- `bundles/checkout`—alles zum Checkout
- `bundles/catalog`—alles für Produkt- und Kategorieseiten

### Teil 2: Erstellen von Bundles

Die folgenden Schritte beschreiben den grundlegenden Prozess zur Generierung einer effizienteren [!DNL Commerce] Pakete. Sie können diesen Prozess beliebig automatisieren, müssen aber dennoch `nodejs` und `r.js` um Ihre Bundles zu generieren. Und wenn Ihre Themen [!DNL JavaScript]-bezogene Anpassungen und können nicht dasselbe `build.js` -Datei, müssen Sie möglicherweise mehrere `build.js` Konfigurationen pro Design.

#### 1. Generieren von statischen Store-Sites

Führen Sie vor dem Generieren von Bundles den statischen Bereitstellungsbefehl aus:

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Dieser Befehl generiert statische Store-Bereitstellungen für jedes Design und Gebietsschema, das Sie eingerichtet haben. Wenn Sie beispielsweise das Luma-Design und ein benutzerdefiniertes Design mit englischen und französischen Gebietsschemata verwenden, würden Sie vier statische Implementierungen generieren:

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

Um Bundles für alle Store-Designs und -Gebietsschemas zu generieren, wiederholen Sie die folgenden Schritte für jedes Store-Design und -Gebietsschema.

#### 2. Verschieben Sie den statischen Speicherinhalt in ein temporäres Verzeichnis.

Zunächst müssen Sie den statischen Inhalt aus dem Zielordner in ein temporäres Verzeichnis verschieben, da RequireJS den gesamten Inhalt im Zielverzeichnis ersetzt.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Beispiel:

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. Führen Sie den r.js-Optimierer aus.

Führen Sie dann den r.js-Optimierer auf der `build.js` Datei aus [!DNL Commerce]des Stammverzeichnisses. Pfade zu allen Verzeichnissen und Dateien beziehen sich auf das Arbeitsverzeichnis.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Dieser Befehl generiert Bundles in einer `bundles` -Unterverzeichnis des Zielverzeichnisses, das in diesem Fall zu `pub/static/frontend/Magento/luma/en_US/bundles`.

Das Auflisten des Inhalts des neuen Bundle-Ordners könnte wie folgt aussehen:

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```terminal
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4. Konfigurieren von RequireJS zur Verwendung von Bundles

Um RequireJS zur Verwendung Ihrer Bundles zu erhalten, fügen Sie eine `onModuleBundleComplete` Callback nach `modules` Knoten in `build.js` Datei:

```javascript
[
    {
       //...
       exclude: [
           'requirejs/require',
           'bundles/default',
           'bundles/checkout',
           'bundles/cart',
           'bundles/shipping',
           'mage/bootstrap'
       ],
   },
],
bundlesConfigOutFile: `${config.dir}/requirejs-config.js`,
onModuleBundleComplete: function(data) {
    if (this.bundleConfigAppended) {
        return;
    }
    this.bundleConfigAppended = true;

    // bundlesConfigOutFile requires a simple require.config call in order to modify the configuration
    const bundleConfigPlaceholder = `
(function (require) {
require.config({});
})(require);
    `;

    fs.appendFileSync(this.bundlesConfigOutFile, bundleConfigPlaceholder);
}
```

#### 5. Befehl zum erneuten Ausführen der Bereitstellung

Führen Sie zum Bereitstellen den folgenden Befehl aus:

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Öffnen `requirejs-config.js` im `pub/static/frontend/Magento/luma/en_US` -Verzeichnis, um zu überprüfen, ob RequireJS die Datei mit den gebündelten Konfigurationsaufrufen angehängt hat:

```javascript
require.config({
    bundles: {
        "bundles/default": ["mage/template", "mage/apply/scripts", "mage/apply/main", "mage/mage", "mage/translate", "mage/loader"],
        "bundles/cart": ["Magento_Ui/js/lib/validation/utils", "Magento_Ui/js/lib/validation/rules", "Magento_Ui/js/lib/validation/validation"]
    }
}
```

>[!NOTE]
>
>Stellen Sie beim Konfigurieren von Bundles sicher, dass Sie die `requirejs.config()` -Aufrufe in der Reihenfolge, in der sie ausgeführt werden sollen, da die Aufrufe in der Reihenfolge ausgeführt werden, in der sie erscheinen.

#### 6. Testen der Ergebnisse

Beachten Sie nach dem Laden der Seite, dass der Browser verschiedene Abhängigkeiten und Bundles lädt. Hier finden Sie beispielsweise die Ergebnisse für das Profil &quot;Langsames 3G&quot;:

![Zweimal so schnell](../assets/performance/images/TwiceAsFast.png)

Die Seitenladezeit für eine leere Homepage ist jetzt doppelt so schnell wie bei der Verwendung nativer [!DNL Commerce] Bundling. Aber wir können es noch besser machen.

#### 7. Optimieren der Bundles

Selbst wenn die [!DNL JavaScript] -Dateien sind immer noch groß. Minimieren Sie sie mit RequireJS, das Uglifier zur Minimierung verwendet [!DNL JavaScript] zu einem guten Ergebnis.

So aktivieren Sie den Optimierer in Ihrer `build.js` Datei hinzufügen `uglify2` als Wert für die Eigenschaft &quot;optimize&quot;oben im `build.js` Datei:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

Die Ergebnisse können von Bedeutung sein:
![dreimal schneller](../assets/performance/images/ThreeTimesFaster.png)

Die Ladezeiten sind jetzt dreimal schneller als mit nativen [!DNL Commerce] Bundling.
