---
title: Advanced [!DNL JavaScript] Bundling
description: Erfahren Sie, wie die JavaScript-Bündelung die Größe und Häufigkeit von Server-Anfragen reduzieren kann.
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: f9f8aea1a77ef062d7076a61bbafd12433f15edf
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 0%

---

# Erweiterte [!DNL JavaScript]

Beim Bündeln von [!DNL JavaScript]-Modulen für eine bessere Leistung geht es darum, zwei Dinge zu reduzieren:

1. Die Anzahl der Server-Anfragen.
1. Die Größe dieser Server-Anfragen.

Bei einer modularen Anwendung kann die Anzahl der Server-Anfragen bis in die Hunderte reichen. Beispielsweise zeigt die folgende Bildschirmabbildung nur den Anfang der Liste [!DNL JavaScript] Module, die auf der Startseite einer sauberen Installation geladen wurden.

![Keine Bündelung](../assets/performance/images/noBundling.png)

## Zusammenführen und Bündeln

Standardmäßig bietet [!DNL Commerce] zwei Möglichkeiten, die Anzahl der Server-Anfragen zu reduzieren: Zusammenführen und Bündeln. Diese Einstellungen sind standardmäßig deaktiviert. Sie können sie in der Admin-Benutzeroberfläche unter **[!UICONTROL Stores]** > **Einstellungen** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** oder über die Befehlszeile aktivieren.

![Bundling](../assets/performance/images/bundlingImage.png)

### Grundlegende Bündelung

So aktivieren Sie die integrierte Bündelung über die Befehlszeile:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Dies ist ein nativer [!DNL Commerce], der alle im System vorhandenen Assets kombiniert und sie in Bundles derselben Größe (bundle_0.js, bundle_1.js … bundle_x.js) verteilt:

![[!DNL Commerce] Bündelung](../assets/performance/images/magentoBundling.png)

Besser, aber der Browser lädt weiterhin ALLE [!DNL JavaScript] Pakete, nicht nur die benötigten.

[!DNL Commerce] Bundle reduziert die Anzahl der Verbindungen pro Seite, aber für jede Seitenanfrage werden alle Bundles geladen, auch wenn die angeforderte Seite möglicherweise nur von Dateien in einem oder zwei der Bundles abhängt. Die Leistung verbessert sich, nachdem der Browser die Bundles zwischenspeichert. Da der Browser diese Bundles jedoch synchron lädt, kann es beim ersten Besuch einer [!DNL Commerce] Storefront eine Weile dauern, bis das Benutzererlebnis gerendert und beschädigt wird.

### Einfache Zusammenführung

So aktivieren Sie die integrierte Zusammenführung über die Befehlszeile:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Dieser Befehl führt alle synchronen [!DNL JavaScript]-Dateien in einer Datei zusammen. Das Aktivieren der Zusammenführung ohne gleichzeitiges Aktivieren der Bündelung ist nicht nützlich, da [!DNL Commerce] RequireJS verwendet. Wenn Sie das Bundling nicht aktivieren, führt [!DNL Commerce] nur RequireJS und dessen Konfiguration zusammen. Wenn Sie sowohl Bündelung als auch Zusammenführung aktivieren, erstellt [!DNL Commerce] eine einzelne [!DNL JavaScript]:

![Zusammenführung realer ](../assets/performance/images/magentoMergingDevWorld.png)

## Reale Render-Zeiten

Die vorherigen gebündelten und zusammengeführten Ladezeiten sehen in einer Entwicklungsumgebung gut aus. Aber in der realen Welt können viele Dinge das Rendering verlangsamen. Langsame Verbindungen, große Verbindungsschwellen, begrenzte Netzwerke. Darüber hinaus werden Mobilgeräte nicht so schnell gerendert wie Desktops.

Um Ihre Storefront-Bereitstellung zu testen und für die reale Welt vorzubereiten, empfehlen wir, mit dem nativen Drosselungsprofil „Langsam 3G“ von Chrome zu testen. Mit Slow 3G spiegeln unsere bisherigen gebündelten Ausgabezeiten jetzt die Verbindungsrealitäten vieler Nutzer wider:

![Bundle in der realen Welt](../assets/performance/images/magentoBundlingRealWorld.png)

Bei langsamer 3G-Konnektivität dauert es etwa 44 Sekunden, bis alle Pakete für die Homepage einer sauberen [!DNL Commerce]-Installation geladen sind.

Dasselbe gilt für die Zusammenführung der Bundles in einer Datei. Benutzer konnten immer noch etwa 42 Sekunden auf das erste Laden der Seite warten, wie hier gezeigt:

![Zusammenführung realer ](../assets/performance/images/magentoMergingRealWorld.png)

Mit einem fortschrittlicheren Ansatz für die [!DNL JavaScript] können wir diese Ladezeiten verbessern.

## Erweiterte Pakete

Das Ziel [!DNL JavaScript] Bundles besteht darin, die Anzahl und Größe der angeforderten Assets für jede im Browser geladene Seite zu reduzieren. Dazu möchten wir unsere Bundles so aufbauen, dass jede Seite in unserem Store nur ein gemeinsames Bundle und ein seitenspezifisches Bundle für jede aufgerufene Seite herunterladen muss.

Eine Möglichkeit, dies zu erreichen, besteht darin, die Bundles nach Seitentypen zu definieren. Sie können die Seiten von [!DNL Commerce] in verschiedene Seitentypen kategorisieren, darunter Kategorie, Produkt, CMS, Kunde, Warenkorb und Checkout. Jede Seite, die in einen dieser Seitentypen kategorisiert ist, verfügt über einen anderen Satz von RequireJS-Modulabhängigkeiten. Wenn Sie Ihre RequireJS-Module nach Seitentyp bündeln, erhalten Sie nur eine Handvoll Bundles, die die Abhängigkeiten einer beliebigen Seite in Ihrem Store abdecken.

Beispielsweise könnten Sie am Ende ein Bundle für die Abhängigkeiten, die für alle Seiten gelten, ein Bundle für Nur-CMS-Seiten, ein Bundle für Nur-Katalog-Seiten, ein weiteres Bundle für Nur-Suche-Seiten und ein Bundle für Checkout-Seiten erhalten.

Sie können Bundles auch nach Zweck erstellen: für allgemeine Funktionen, produktbezogene Funktionen, Versandfunktionen, Checkout-Funktionen, Steuern und Formularvalidierungen. Wie Sie Ihre Bundles definieren, liegt an Ihnen und der Struktur Ihres Stores. Möglicherweise werden einige Bündelungsstrategien besser funktionieren als andere.

Eine saubere [!DNL Commerce]-Installation ermöglicht es, durch die Aufteilung von Bundles nach Seitentypen eine ausreichend gute Leistung zu erzielen, aber einige Anpassungen können eine tiefere Analyse und andere Asset-Verteilungen erfordern.

### Erforderliche Tools

Für die folgenden Schritte müssen Sie die folgenden Tools installieren und damit vertraut sein:

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) (optional)

### Beispielcode

Die vollständigen Versionen des in diesem Artikel verwendeten Beispiel-Codes finden Sie hier:

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Teil 1: Erstellen einer Bundling-Konfiguration

#### 1\ Hinzufügen einer „build.js“-Datei

Erstellen Sie eine `build.js` Datei im [!DNL Commerce] Stammverzeichnis. Diese Datei enthält die gesamte Build-Konfiguration für Ihre Bundles.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Später werden wir die `optimize:` von_ `none` auf `uglify2` ändern, um die Bundle-Ausgabe zu minimieren. Vorerst können Sie es während der Entwicklung jedoch auf `none` setzen, um schnellere Builds sicherzustellen.

#### 2\ Hinzufügen von RequireJS-Abhängigkeiten, Shims, Pfaden und Zuordnungen

Fügen Sie die folgenden RequireJS-Build-Konfigurationsknoten, `deps`, `shim`, `paths` und `map`, zu Ihrer Build-Datei hinzu:

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

#### 3\ Aggregieren Sie die Instanzwerte „required-config.js“

In diesem Schritt müssen Sie alle `deps`, `shim`, `paths` und `map` Konfigurationsknoten aus der `requirejs-config.js`-Datei Ihres Stores in den entsprechenden Knoten in Ihrer `build.js`-Datei aggregieren. Öffnen Sie dazu die Registerkarte **[!UICONTROL Network]** im Bereich Entwickler-Tools Ihres Browsers und navigieren Sie zu einer beliebigen Seite in Ihrem Store, z. B. zur Homepage. Auf der Registerkarte „Netzwerk“ wird die Instanz der `requirejs-config.js`-Datei in Ihrem Store oben angezeigt, wie hier hervorgehoben:

![RequireJS-Konfiguration](../assets/performance/images/RequireJSConfig.png)

In dieser Datei finden Sie mehrere Einträge für jeden Konfigurationsknoten (`deps`, `shim`, `paths`, `map`). Sie müssen diese mehreren Knotenwerte in dem einzelnen Konfigurationsknoten Ihrer build.js-Datei aggregieren. Wenn beispielsweise die `requirejs-config.js`-Instanz Ihres Stores Einträge für 15 separate `map`-Knoten hat, müssen Sie die Einträge für alle 15 -Knoten in dem einzelnen `map`-Knoten in Ihrer `build.js` zusammenführen. Dasselbe gilt für die Knoten `deps`, `shim` und `paths`. Ohne ein Skript zur Automatisierung dieses Prozesses kann es einige Zeit dauern.

Sie müssen den Pfad `mage/requirejs/text` im Konfigurationsknoten wie folgt in `requirejs/text` `paths` ändern:

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\ Modulknoten hinzufügen

Fügen Sie am Ende der `build.js` die Module[] Array als Platzhalter für die Bundles hinzu, die Sie später für Ihre Storefront definieren werden.

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

#### 5\ Abrufen erforderlicher JS-Abhängigkeiten

Sie können alle [!DNL RequireJS] Modulabhängigkeiten aus den Seitentypen Ihres Stores abrufen, indem Sie Folgendes verwenden:

1. [!DNL PhantomJS] über die Befehlszeile (vorausgesetzt, Sie [!DNL PhantomJS] installiert haben).
1. RequireJS-Befehl in der Browser-Konsole.

#### So verwenden Sie [!DNL PhantomJS]:

Erstellen Sie im [!DNL Commerce] Stammverzeichnis eine neue Datei mit dem Namen `deps.js` und kopieren Sie sie in den unten stehenden Code. Dieser Code verwendet [!DNL [!DNL PhantomJS]], um eine Seite zu öffnen und darauf zu warten, dass der Browser alle Seiten-Assets lädt. Anschließend werden alle [!DNL RequireJS] Abhängigkeiten für eine bestimmte Seite ausgegeben.

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
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-Representating-PageType-dependencies</i>
</pre>

Hier finden Sie beispielsweise vier Seiten aus dem Beispielspeicher mit dem Thema Luma, die die vier Seitentypen darstellen, die wir verwenden werden, um unsere vier Bundles (Homepage, Kategorie, Produkt, Warenkorb) zu erstellen:

```
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### So verwenden Sie die Browser-Konsole:

Wenn Sie [!DNL PhantomJS] nicht verwenden möchten, können Sie den folgenden Befehl in der Browser-Konsole ausführen, während Sie die einzelnen Seitentypen in Ihrer Storefront anzeigen:

```shell
Object.keys(window.require.s.contexts._.defined)
```

Dieser Befehl (der im [!DNL PhantomJS]-Skript verwendet wird) erstellt dieselbe Liste [!DNL RequireJS] Abhängigkeiten und zeigt sie in der Browser-Konsole an. Der Nachteil dieses Ansatzes besteht darin, dass Sie Ihre eigenen Textdateien vom Typ Paket/Seite erstellen müssen.

#### 6\ Formatieren und Filtern der Ausgabe

Nachdem Sie die [!DNL RequireJS] Abhängigkeiten in Textdateien vom Typ Seite zusammengeführt haben, können Sie den folgenden Befehl in jeder Abhängigkeitsdatei vom Typ Seite verwenden, um die Kommas in Ihren Dateien durch Zeilenumbrüche zu ersetzen:

```bash
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

Sie sollten auch alle Mixins für jede Datei entfernen, da Mixins Abhängigkeiten duplizieren. Verwenden Sie für jede Abhängigkeitsdatei den folgenden Befehl:

```bash
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\ Identifizieren eindeutiger und allgemeiner Bundles

Ziel ist es, ein gemeinsames Paket von [!DNL JavaScript]-Dateien zu erstellen, die für alle Seiten benötigt werden. Auf diese Weise muss der Browser nur das gemeinsame Bundle mit einem oder mehreren bestimmten Seitentypen laden.

Öffnen Sie ein Terminal im [!DNL Commerce] Stammverzeichnis und verwenden Sie den folgenden Befehl, um zu überprüfen, ob Sie Abhängigkeiten haben, die Sie in separate Bundles aufteilen können:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Dieser Befehl führt die in den `bundle/*.txt` Dateien gefundenen Abhängigkeiten zusammen und sortiert sie.  Die Ausgabe zeigt auch die Anzahl der Dateien an, die jede Abhängigkeit enthalten:

```
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

Diese Ausgabe zeigt, dass `buildTools` nur in einer der Bundle/*.txt-Dateien eine Abhängigkeit ist. Die `jquery/jquery.metadata` ist in zwei (2) -Dateien und `es6-collections` in drei (3) -Dateien.

Unsere Ausgabe zeigt nur drei Seitentypen (Homepage, Kategorie und Produkt), was uns sagt:

- Drei Abhängigkeiten sind nur für einen Seitentyp eindeutig (angezeigt durch die Zahl 1).
- Drei weitere Abhängigkeiten treten bei zwei Seitentypen auf (angezeigt durch die Zahl 2).
- Die letzten drei Abhängigkeiten gelten für alle drei unserer Seitentypen (angezeigt durch die Zahl 3).

Dies zeigt uns, dass wir die Seitenladegeschwindigkeiten unseres Stores wahrscheinlich verbessern können, indem wir unsere Abhängigkeiten in verschiedene Bundles aufteilen, sobald wir wissen, welche Seitentypen welche Abhängigkeiten benötigen.

#### 8\ Erstellen einer Verteilungsdatei für Abhängigkeiten

Um herauszufinden, welche Seitentypen welche Abhängigkeiten benötigen, erstellen Sie eine neue Datei im [!DNL Commerce] Stammverzeichnis mit dem Namen `deps-map.sh` und kopieren Sie sie in den folgenden Code:

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

Öffnen Sie ein Terminal im [!DNL Commerce] Stammverzeichnis und führen Sie die Datei aus:

```bash
bash deps-map.sh
```

Die Ausgabe dieses Skripts, das auf unsere drei Beispielseitentypen angewendet wird, sollte in etwa so aussehen (aber viel länger):

```
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

Dies ist ausreichend, um eine Bundles-Konfiguration zu erstellen.

#### 9\ Erstellen von Bundles in der Datei build.js

Öffnen Sie die `build.js` Konfigurationsdatei und fügen Sie Ihre Bundles zum `modules` hinzu. Jedes Bundle sollte die folgenden Eigenschaften definieren:

- `name` - Der Name des Bundles. Beispielsweise generiert ein Name von `bundles/cart` ein `cart.js`-Bundle in einem `bundles` Unterverzeichnis.

- `create` - Eine boolesche Markierung zum Erstellen des Bundles (Werte: `true` oder `false`).

- `include` - Ein Array von Assets (Zeichenfolgen), die als Abhängigkeiten für die Seite enthalten sind. RequireJS verfolgt alle Abhängigkeiten und schließt sie in das Bundle ein, es sei denn, es wird ausgeschlossen.

- `exclude` - Ein Array von Bundles oder Assets, die aus dem Bundle ausgeschlossen werden sollen.

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

In diesem Beispiel werden `mage/bootstrap`- und `requirejs/require`-Assets wiederverwendet, wobei den wichtigsten Komponenten und Komponenten, die synchron geladen werden müssen, eine höhere Priorität eingeräumt wird. Folgende Bundles sind vorhanden:

- `requirejs/require` - das einzige synchron geladene Bundle
- `mage/bootstrap` - das Bootstrap-Bundle mit UI-Komponenten
- `bundles/default` - Für alle Seiten ist ein Standardpaket erforderlich
- `bundles/cart` - Ein für die Warenkorbseite erforderliches Bundle
- `bundles/shipping` - Allgemeines Bundle für Warenkorb und Kaufbestätigungsseite (unter der Annahme, dass die Kaufbestätigungsseite nie direkt geöffnet wird, wird die Kaufbestätigungsseite noch schneller geladen, wenn die Warenkorbseite zuvor geöffnet wurde und das Versandpaket bereits geladen wurde)
- `bundles/checkout` - alles für den Checkout
- `bundles/catalog` - alles für Produkt- und Kategorieseiten

### Teil 2: Bundles generieren

Die folgenden Schritte beschreiben den grundlegenden Prozess zum Generieren effizienterer [!DNL Commerce]. Sie können diesen Prozess beliebig automatisieren, müssen jedoch weiterhin `nodejs` und `r.js` verwenden, um Ihre Bundles tatsächlich zu generieren. Und wenn Ihre Designs [!DNL JavaScript] Anpassungen aufweisen und dieselbe `build.js`-Datei nicht wiederverwenden können, müssen Sie möglicherweise mehrere `build.js` Konfigurationen pro Design erstellen.

#### &#x200B;1. Generieren von statischen Store-Sites

Führen Sie vor dem Generieren von Bundles den statischen Bereitstellungsbefehl aus:

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Dieser Befehl generiert statische Store-Bereitstellungen für jedes Design und Gebietsschema, das Sie eingerichtet haben. Wenn Sie beispielsweise das Luma-Design und ein benutzerdefiniertes Design mit Gebietsschemata in Englisch und Französisch verwenden, generieren Sie vier statische Bereitstellungen:

- …luma/en_US
- …luma/fr_FR
- …custom/en_US
- …custom/fr_FR

Um Bundles für alle Store-Designs und Gebietsschemata zu generieren, wiederholen Sie die folgenden Schritte für jedes Store-Design und Gebietsschema.

#### &#x200B;2. Verschieben des statischen Speicherinhalts in ein temporäres Verzeichnis

Zunächst müssen Sie den statischen Inhalt aus dem Zielverzeichnis in ein temporäres Verzeichnis verschieben, da RequireJS den gesamten Inhalt im Zielverzeichnis ersetzt.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Beispiel:

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### &#x200B;3. Ausführen von r.js Optimizer

Führen Sie dann „r.js Optimizer“ für die `build.js`-Datei aus dem Stammverzeichnis von [!DNL Commerce] aus. Die Pfade zu allen Verzeichnissen und Dateien sind relativ zum Arbeitsverzeichnis.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Dieser Befehl erzeugt Bundles in einem `bundles` Unterverzeichnis des Zielverzeichnisses, was in diesem Fall zu `pub/static/frontend/Magento/luma/en_US/bundles` führt.

Die Auflistung des Inhalts des neuen Bundle-Verzeichnisses könnte wie folgt aussehen:

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### &#x200B;4. Konfigurieren von RequireJS für die Verwendung von Bundles

Um RequireJS dazu zu bringen, Ihre Bundles zu verwenden, fügen Sie der `onModuleBundleComplete`-Datei nach dem Knoten `modules` einen `build.js`-Callback hinzu:

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

#### &#x200B;5. Erneutes Ausführen des Bereitstellungsbefehls

Führen Sie den folgenden Befehl aus, um bereitzustellen:

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Öffnen Sie `requirejs-config.js` im `pub/static/frontend/Magento/luma/en_US` Verzeichnis, um zu überprüfen, ob RequireJS die Datei mit Bundle-Konfigurationsaufrufen angehängt hat:

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
>Stellen Sie beim Konfigurieren von Bundles sicher, dass Sie die `requirejs.config()` Aufrufe in der Reihenfolge ausführen, in der sie ausgeführt werden sollen, da die Aufrufe in der Reihenfolge ausgeführt werden, in der sie angezeigt werden.

#### &#x200B;6. Testen der Ergebnisse

Beachten Sie, dass der Browser nach dem Laden der Seite verschiedene Abhängigkeiten und Bundles lädt. Hier finden Sie beispielsweise die Ergebnisse für das Profil „Langsames 3G“:

![doppelt so schnell](../assets/performance/images/TwiceAsFast.png)

Die Seitenladezeit für eine leere Homepage ist jetzt doppelt so schnell wie bei der Verwendung des nativen [!DNL Commerce]-Bundles. Aber wir können es noch besser machen.

#### &#x200B;7. Optimieren der Bundles

Selbst wenn die Dateien im Gzip-Format komprimiert werden, sind die [!DNL JavaScript]-Dateien immer noch groß. Minimieren Sie sie mit RequireJS, das einen Verzweiger verwendet, um [!DNL JavaScript] zu einem guten Ergebnis zu verkleinern.

Um den Optimizer in Ihrer `build.js`-Datei zu aktivieren, fügen Sie `uglify2` als Wert für die Eigenschaft „optimize“ oben in der `build.js`-Datei hinzu:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

Die Ergebnisse können erheblich sein:
![Dreimal schneller](../assets/performance/images/ThreeTimesFaster.png)

Die Ladezeiten sind jetzt dreimal schneller als bei der nativen [!DNL Commerce].
