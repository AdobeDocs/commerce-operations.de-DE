---
title: Erweitert [!DNL JavaScript] Bundling
description: Erfahren Sie, wie das JavaScript-Bundling die Größe und Häufigkeit von Serveranfragen reduzieren kann.
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: f9f8aea1a77ef062d7076a61bbafd12433f15edf
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 0%

---

# Erweitertes [!DNL JavaScript]-Bundling

Beim Bundling von [!DNL JavaScript] -Modulen für eine bessere Leistung geht es darum, zwei Dinge zu reduzieren:

1. Die Anzahl der Serveranforderungen.
1. Die Größe dieser Serveranforderungen.

In einer modularen Anwendung kann die Anzahl der Serveranforderungen Hunderte erreichen. Der folgende Screenshot zeigt beispielsweise nur den Beginn der Liste der [!DNL JavaScript] -Module, die auf der Startseite einer sauberen Installation geladen wurden.

![Kein Bundling](../assets/performance/images/noBundling.png)

## Zusammenführung und Bündelung

Standardmäßig bietet [!DNL Commerce] zwei Möglichkeiten, die Anzahl der Serveranforderungen zu reduzieren: Zusammenführen und Bündeln. Diese Einstellungen sind standardmäßig deaktiviert. Sie können sie in der Admin-Benutzeroberfläche unter **[!UICONTROL Stores]** > **Einstellungen** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** oder über die Befehlszeile aktivieren.

![Bundling](../assets/performance/images/bundlingImage.png)

### Grundlegendes Bundling

So aktivieren Sie das integrierte Bundling über die Befehlszeile:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Dies ist ein nativer [!DNL Commerce]-Mechanismus, der alle im System vorhandenen Assets kombiniert und unter Bundles derselben Größe verteilt (bundle_0.js, bundle_1.js ... bundle_x.js):

![[!DNL Commerce] bundling](../assets/performance/images/magentoBundling.png)

Besser, aber der Browser lädt weiterhin alle [!DNL JavaScript] -Bundles, nicht nur die benötigten.

Durch das Bundling von [!DNL Commerce] wird die Anzahl der Verbindungen pro Seite reduziert. Für jede Seitenanforderung werden jedoch alle Bundles geladen, selbst wenn die angeforderte Seite nur von Dateien innerhalb eines oder zweier Bundles abhängig sein kann. Die Leistung verbessert sich, nachdem der Browser die Bundles zwischengespeichert hat. Da der Browser diese Bundles jedoch synchron lädt, kann es beim ersten Besuch des Benutzers in einer [!DNL Commerce] -Storefront einige Zeit dauern, bis das Rendering und die Beeinträchtigung des Benutzererlebnisses erfolgt sind.

### Grundlegende Zusammenführung

So aktivieren Sie die integrierte Zusammenführung über die Befehlszeile:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Mit diesem Befehl werden alle synchronen [!DNL JavaScript] -Dateien in einer Datei zusammengeführt. Die Aktivierung der Zusammenführung ohne die Aktivierung der Bündelung ist nicht nützlich, da [!DNL Commerce] RequireJS verwendet. Wenn Sie das Bundling nicht aktivieren, führt [!DNL Commerce] nur RequireJS und dessen Konfiguration zusammen. Wenn Sie sowohl das Bundling als auch das Zusammenführen aktivieren, erstellt [!DNL Commerce] eine einzelne [!DNL JavaScript]-Datei:

![Zusammenführung in der realen Welt](../assets/performance/images/magentoMergingDevWorld.png)

## Reale Renderzeiten

Die vorherigen gebündelten und zusammengeführten Ladezeiten sehen in einer Entwicklungsumgebung großartig aus. Aber in der realen Welt können viele Dinge das Rendering verlangsamen: langsame Verbindungen, große Verbindungsschwellen, begrenzte Netzwerke. Darüber hinaus werden Mobilgeräte nicht so schnell wie Desktops gerendert.

Um Ihre Storefront-Implementierung für die reale Welt zu testen und vorzubereiten, empfehlen wir, mit dem nativen Einschränkungsprofil von Chrome &quot;Slow 3G&quot;zu testen. Mit Slow 3G spiegeln unsere vorherigen gebündelten Ausgabezeiten jetzt die Verbindungsprobleme vieler Benutzer wider:

![Echtzeit-Bundling](../assets/performance/images/magentoBundlingRealWorld.png)

Bei langsamer 3G-Konnektivität dauert es etwa 44 Sekunden, alle Bundles für die Homepage einer sauberen [!DNL Commerce]-Installation zu laden.

Dasselbe gilt für das Zusammenführen der Bundles in einer Datei. Benutzer können weiterhin etwa 42 Sekunden auf das erste Laden der Seite warten, wie im folgenden Beispiel gezeigt:

![Zusammenführung in der realen Welt](../assets/performance/images/magentoMergingRealWorld.png)

Mit einem erweiterten Ansatz für das [!DNL JavaScript]-Bundling können wir diese Ladezeiten verbessern.

## Erweitertes Bundling

Denken Sie daran, dass das [!DNL JavaScript]-Bundling die Anzahl und Größe der angeforderten Assets für jede im Browser geladene Seite reduzieren soll. Dazu möchten wir unsere Bundles erstellen, sodass jede Seite in unserem Store nur ein gemeinsames Bundle und ein seitenspezifisches Bundle für jede aufgerufene Seite herunterladen muss.

Eine Möglichkeit, dies zu erreichen, besteht darin, Ihre Bundles nach Seitentypen zu definieren. Sie können die Seiten von [!DNL Commerce] in verschiedene Seitentypen kategorisieren, einschließlich Kategorie, Produkt, CMS, Kunde, Warenkorb und Checkout. Jede Seite, die in einen dieser Seitentypen kategorisiert ist, verfügt über einen anderen Satz von RequireJS-Modulabhängigkeiten. Wenn Sie Ihre RequireJS-Module nach Seitentyp bündeln, erhalten Sie nur eine Handvoll Pakete, die die Abhängigkeiten einer beliebigen Seite in Ihrem Store abdecken.

Sie können beispielsweise mit einem Bundle für die allen Seiten gemeinsamen Abhängigkeiten, einem Bundle für nur CMS-Seiten, einem Bundle für Nur-Katalog-Seiten, einem weiteren Bundle für Nur-Suche-Seiten und einem Bundle für Checkout-Seiten enden.

Sie können Bundles auch nach Zweck erstellen: für allgemeine Funktionen, produktbezogene Funktionen, Versandfunktionen, Checkout-Funktionen, Steuern und Formularvalidierungen. Wie Sie Ihre Bundles definieren, hängt von Ihnen und der Struktur Ihres Stores ab. Möglicherweise funktionieren einige Bundling-Strategien besser als andere.

Eine saubere [!DNL Commerce] -Installation ermöglicht es, durch Aufteilen von Bundles nach Seitentypen ausreichend gute Leistung zu erzielen. Einige Anpassungen erfordern jedoch möglicherweise eine tiefere Analyse und andere Asset-Verteilungen.

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

Erstellen Sie eine `build.js` -Datei im Stammverzeichnis von [!DNL Commerce]. Diese Datei enthält die gesamte Build-Konfiguration für Ihre Bundles.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Später ändern wir die Einstellung `optimize:` von_ `none` in `uglify2`, um die Bundle-Ausgabe zu verkleinern. Während der Entwicklung können Sie es jedoch vorerst auf `none` festlegen, um schnellere Builds sicherzustellen.

#### 2\. Hinzufügen von RequireJS-Abhängigkeiten, -Shims, -Pfaden und -Landkarten

Fügen Sie die folgenden RequireJS-Build-Konfigurationsknoten, `deps`, `shim`, `paths` und `map` zu Ihrer Build-Datei hinzu:

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

In diesem Schritt müssen Sie alle aus der `requirejs-config.js` -Datei Ihres Stores stammenden mehreren Konfigurationsknoten `deps`, `shim`, `paths` und `map` in die entsprechenden Knoten in Ihrer `build.js`-Datei aggregieren. Dazu können Sie die Registerkarte **[!UICONTROL Network]** im Bedienfeld &quot;Entwicklertools&quot;Ihres Browsers öffnen und zu einer beliebigen Seite in Ihrem Store navigieren, z. B. zur Startseite. Auf der Registerkarte &quot;Netzwerk&quot;sehen Sie die Instanz Ihres Stores der Datei &quot;`requirejs-config.js`&quot;oben, die hier hervorgehoben ist:

![RequireJS-Konfiguration](../assets/performance/images/RequireJSConfig.png)

In dieser Datei finden Sie mehrere Einträge für jeden Konfigurationsknoten (`deps`, `shim`, `paths`, `map`). Sie müssen diese verschiedenen Knotenwerte in den einzelnen Konfigurationsknoten Ihrer Datei &quot;build.js&quot;aggregieren. Wenn beispielsweise die `requirejs-config.js` -Instanz Ihres Stores Einträge für 15 verschiedene `map` -Knoten hat, müssen Sie die Einträge für alle 15 Knoten in den einzelnen `map` -Knoten in Ihrer `build.js` -Datei zusammenführen. Dasselbe gilt für die Knoten `deps`, `shim` und `paths`. Ohne ein Skript zur Automatisierung dieses Prozesses kann es Zeit dauern.

Sie müssen den Pfad `mage/requirejs/text` in `requirejs/text` im Konfigurationsknoten `paths` wie folgt ändern:

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

Fügen Sie am Ende der Datei `build.js` das Array modules[] als Platzhalter für die Bundles hinzu, die Sie später für Ihre Storefront definieren.

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

Sie können alle [!DNL RequireJS] -Modulabhängigkeiten aus den Seitentypen Ihres Stores abrufen, indem Sie Folgendes verwenden:

1. [!DNL PhantomJS] aus der Befehlszeile (vorausgesetzt, Sie haben [!DNL PhantomJS] installiert).
1. JS-Befehl in der Browser-Konsole erforderlich.

#### So verwenden Sie [!DNL PhantomJS]:

Erstellen Sie im Stammverzeichnis von [!DNL Commerce] eine neue Datei mit dem Namen `deps.js` und kopieren Sie sie in den unten stehenden Code. In diesem Code wird [!DNL [!DNL PhantomJS]] verwendet, um eine Seite zu öffnen und zu warten, bis der Browser alle Seiten-Assets lädt. Anschließend werden alle [!DNL RequireJS] -Abhängigkeiten für eine bestimmte Seite ausgegeben.

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

Öffnen Sie ein Terminal im Stammverzeichnis [!DNL Commerce] und führen Sie das Skript für jede Seite in Ihrem Store aus, die einen bestimmten Seitentyp darstellt:

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-presentation-pagetype-dependencies</i>
</pre>

Hier sind beispielsweise vier Seiten aus dem thematischen Beispiel-Store &quot;Luma&quot;, die die vier Seitentypen darstellen, die wir verwenden werden, um unsere vier Bundles (Homepage, Kategorie, Produkt, Warenkorb) zu erstellen:

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

Dieser Befehl (der im [!DNL PhantomJS] -Skript verwendet wird) erstellt dieselbe Liste von [!DNL RequireJS] -Abhängigkeiten und zeigt sie in der Browser-Konsole an. Der Nachteil dieses Ansatzes besteht darin, dass Sie Ihre eigenen Textdateien vom Typ Bundle/Seite erstellen müssen.

#### 6\. Ausgabe formatieren und filtern

Nachdem Sie die Abhängigkeiten von [!DNL RequireJS] mit Textdateien vom Typ Seite zusammengeführt haben, können Sie den folgenden Befehl für jede Abhängigkeitsdatei vom Typ Seite verwenden, um die Kommas in Ihren Dateien durch Zeilenumbrüche zu ersetzen:

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

#### 7\. Identifizieren von eindeutigen und gemeinsamen Bundles

Das Ziel besteht darin, ein gemeinsames Bundle von [!DNL JavaScript] -Dateien zu erstellen, die für alle Seiten benötigt werden. Auf diese Weise muss der Browser nur das gemeinsame Bundle zusammen mit einem oder mehreren bestimmten Seitentypen laden.

Öffnen Sie ein Terminal im Stammverzeichnis [!DNL Commerce] und überprüfen Sie mit dem folgenden Befehl, ob Sie Abhängigkeiten haben, die Sie in separate Bundles aufteilen können:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Dieser Befehl führt die Abhängigkeiten in den `bundle/*.txt` -Dateien zusammen und sortiert sie.  Die Ausgabe zeigt auch die Anzahl der Dateien an, die jede Abhängigkeit enthalten:

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

Diese Ausgabe zeigt an, dass `buildTools` nur eine Abhängigkeit in einer der Bundle/*.txt-Dateien ist. Die `jquery/jquery.metadata` -Abhängigkeit befindet sich in zwei (2) Dateien und `es6-collections` in drei (3) Dateien.

Unsere Ausgabe zeigt nur drei Seitentypen (Homepage, Kategorie und Produkt) an, die uns Folgendes mitteilen:

- Drei Abhängigkeiten sind nur für einen Seitentyp eindeutig (erkennbar an der Zahl 1).
- Drei weitere Abhängigkeiten treten auf zwei Seitentypen auf (erkennbar an der Zahl 2).
- Die letzten drei Abhängigkeiten sind allen drei unserer Seitentypen gemein (erkennbar an der Zahl 3).

Dies sagt uns, dass wir die Seitenladegeschwindigkeit unseres Stores wahrscheinlich verbessern können, indem wir unsere Abhängigkeiten in verschiedene Bundles aufteilen, sobald wir wissen, welche Seitentypen welche Abhängigkeiten benötigen.

#### 8\. Erstellen einer Verteilungsdatei für Abhängigkeiten

Um herauszufinden, welche Seitentypen welche Abhängigkeiten benötigen, erstellen Sie eine neue Datei im Stammverzeichnis [!DNL Commerce] mit dem Namen `deps-map.sh` und kopieren Sie den folgenden Code:

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

Öffnen Sie ein Terminal im Stammverzeichnis [!DNL Commerce] und führen Sie die Datei aus:

```bash
bash deps-map.sh
```

Die Ausgabe aus diesem Skript, die auf unsere drei Beispielseitentypen angewendet wird, sollte etwa wie folgt aussehen (aber viel länger):

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

Diese Informationen reichen aus, um eine Bundle-Konfiguration zu erstellen.

#### 9\. Erstellen von Bundles in Ihrer Datei &quot;build.js&quot;

Öffnen Sie die Konfigurationsdatei `build.js` und fügen Sie Ihre Bundles zum Knoten `modules` hinzu. Jedes Bundle sollte die folgenden Eigenschaften definieren:

- `name` - der Name des Bundles. Beispielsweise generiert der Name `bundles/cart` ein `cart.js` -Bundle in einem `bundles` -Unterverzeichnis.

- `create` - eine boolesche Markierung zum Erstellen des Bundles (Werte: `true` oder `false`).

- `include` - ein Array von Assets (Zeichenfolgen), die als Abhängigkeiten für die Seite enthalten sind. RequireJS verfolgt alle Abhängigkeiten und schließt sie in das Bundle ein, es sei denn, dies ist ausgeschlossen.

- `exclude` - ein Array von Bundles oder Assets, die aus dem Bundle ausgeschlossen werden sollen.

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

In diesem Beispiel werden die `mage/bootstrap` - und `requirejs/require` -Assets wiederverwendet, wobei die wichtigsten Komponenten und Komponenten, die synchron geladen werden müssen, eine höhere Priorität erhalten. Die vorhandenen Bundles sind:

- `requirejs/require` - das einzige synchron geladene Bundle
- `mage/bootstrap` - das Bootstrap-Bundle mit UI-Komponenten
- `bundles/default` - Standardpaket für alle Seiten erforderlich
- `bundles/cart` - ein für die Warenkorbseite erforderliches Bundle
- `bundles/shipping`—allgemeines Bundle für Warenkorb- und Checkout-Seite (vorausgesetzt, der Checkout wird nie direkt geöffnet, die Checkout-Seite wird sogar noch schneller geladen, wenn die Warenkorbseite zuvor geöffnet und das Versandpaket bereits geladen wurde)
- `bundles/checkout` - alles zum Auschecken
- `bundles/catalog` - alles für Produkt- und Kategorieseiten

### Teil 2: Erstellen von Bundles

Die folgenden Schritte beschreiben den grundlegenden Prozess zum Generieren effizienterer [!DNL Commerce]-Bundles. Sie können diesen Prozess beliebig automatisieren, aber Sie müssen weiterhin `nodejs` und `r.js` verwenden, um Ihre Bundles zu generieren. Wenn Ihre Designs über [!DNL JavaScript] -Anpassungen verfügen und dieselbe `build.js` -Datei nicht wiederverwenden können, müssen Sie möglicherweise mehrere `build.js` -Konfigurationen pro Design erstellen.

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

Führen Sie dann den r.js-Optimierer für die Datei `build.js` aus dem Stammverzeichnis von [!DNL Commerce] aus. Pfade zu allen Verzeichnissen und Dateien beziehen sich auf das Arbeitsverzeichnis.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Dieser Befehl generiert Bundles in einem Unterverzeichnis mit dem Namen `bundles` des Zielverzeichnisses, was in diesem Fall zu `pub/static/frontend/Magento/luma/en_US/bundles` führt.

Das Auflisten des Inhalts des neuen Bundle-Ordners könnte wie folgt aussehen:

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

#### 4. Konfigurieren von RequireJS zur Verwendung von Bundles

Um RequireJS zur Verwendung Ihrer Bundles zu erhalten, fügen Sie in der Datei `build.js` einen `onModuleBundleComplete` -Rückruf nach dem Knoten `modules` hinzu:

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

Öffnen Sie `requirejs-config.js` im Verzeichnis `pub/static/frontend/Magento/luma/en_US` , um zu überprüfen, ob RequireJS die Datei mit den gebündelten Konfigurationsaufrufen angehängt hat:

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
>Stellen Sie beim Konfigurieren von Bundles sicher, dass Sie die `requirejs.config()` -Aufrufe in der Reihenfolge platzieren, in der sie ausgeführt werden sollen, da die Aufrufe in der Reihenfolge ausgeführt werden, in der sie erscheinen.

#### 6. Testen der Ergebnisse

Beachten Sie nach dem Laden der Seite, dass der Browser verschiedene Abhängigkeiten und Bundles lädt. Hier finden Sie beispielsweise die Ergebnisse für das Profil &quot;Langsames 3G&quot;:

![Zweimal so schnell](../assets/performance/images/TwiceAsFast.png)

Die Seitenladezeit für eine leere Startseite ist jetzt doppelt so schnell wie die Verwendung des nativen [!DNL Commerce]-Bundles. Aber wir können es noch besser machen.

#### 7. Optimieren der Bundles

Auch wenn die Datei komprimiert wurde, sind die [!DNL JavaScript]-Dateien immer noch groß. Minimieren Sie sie mit RequireJS, das mithilfe von Uglifier [!DNL JavaScript] auf ein gutes Ergebnis minimiert.

Um den Optimierer in Ihrer `build.js` -Datei zu aktivieren, fügen Sie oben in der Datei `build.js` den Wert `uglify2` als Wert für die Eigenschaft &quot;optimize&quot;hinzu:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

Die Ergebnisse können von Bedeutung sein:
![Dreifachmal schneller](../assets/performance/images/ThreeTimesFaster.png)

Die Ladezeiten sind jetzt dreimal schneller als bei nativem [!DNL Commerce]-Bundling.
