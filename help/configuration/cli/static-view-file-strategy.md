---
title: Bereitstellungsstrategien für statische Ansichtsdateien
description: Erfahren Sie mehr über Implementierungsstrategien für die Commerce-Anwendung.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Bereitstellungsstrategien für statische Ansichtsdateien

Bei der Bereitstellung statischer Ansichtsdateien können Sie eine der drei verfügbaren Strategien auswählen. Jeder von ihnen liefert optimale Implementierungsergebnisse für verschiedene Anwendungsfälle:

- [Standard](#standard-strategy): den regulären Bereitstellungsprozess.
- [Quick](#quick-strategy) (_default_): minimiert die für die Bereitstellung erforderliche Zeit, wenn Dateien für mehr als ein Gebietsschema bereitgestellt werden.
- [Kompakt](#compact-strategy): minimiert den Speicherplatz, der von den veröffentlichten Ansichtsdateien belegt wird.

In den folgenden Abschnitten werden die Implementierungsdetails und Funktionen der einzelnen Strategien beschrieben.

## Standardstrategie

Wenn die Standardstrategie verwendet wird, werden alle statischen Ansichtsdateien für alle Pakete bereitgestellt, d. h. verarbeitet von [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Weitere Informationen finden Sie unter [Bereitstellen von statischen Ansichtsdateien](../cli/static-view-file-deployment.md).

## Schnellstrategie

Die Schnellstrategie führt die folgenden Aktionen durch:

1. Für jedes Design wird ein beliebiges Gebietsschema ausgewählt und alle Dateien für dieses Gebietsschema werden wie in der Standardstrategie bereitgestellt.
1. Für alle anderen Gebietsschemata des Designs:

   1. Dateien, die das bereitgestellte Gebietsschema überschreiben, werden definiert und bereitgestellt.
   1. Alle anderen Dateien gelten für alle Gebietsschemata als ähnlich und werden aus dem bereitgestellten Gebietsschema kopiert.

>[!INFO]
>
>von _similar_ bedeutet, dass Dateien unabhängig vom Gebietsschema, Thema oder Bereich sind. Diese Dateien können CSS, Bilder und Schriftarten enthalten.

Dieser Ansatz minimiert die für mehrere Gebietsschemata erforderliche Bereitstellungszeit, obwohl viele Dateien dupliziert werden.

## Kompakte Strategie

Die kompakte Strategie vermeidet Dateiduplizierung durch Speichern ähnlicher Dateien in `base` Unterverzeichnisse.

Für das am besten optimierte Ergebnis werden drei Bereiche für eine mögliche Ähnlichkeit zugeordnet: Bereich, Thema und Gebietsschema. Die `base` -Unterverzeichnisse werden für alle Kombinationen dieser Bereiche erstellt.

Die Dateien werden entsprechend den folgenden Mustern in diesen Unterverzeichnissen bereitgestellt.

| Muster | Beschreibung |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Spezifische Dateien für einen bestimmten Bereich, ein bestimmtes Design und ein bestimmtes Gebietsschema |
| `<area>/<theme>/default` | Dateien, die für alle Gebietsschemata eines bestimmten Designs eines bestimmten Bereichs ähnlich sind. |
| `<area>/Magento/base/<locale>` | Dateien, die für einen bestimmten Bereich und ein bestimmtes Gebietsschema spezifisch sind, aber für alle Designs ähnlich sind. |
| `<area>/Magento/base/default` | Dateien, die für einen bestimmten Bereich spezifisch sind, aber für alle Designs und Gebietsschemata ähnlich sind. |
| `base/Magento/base/<locale>` | Dateien, die für alle Bereiche und Designs ähnlich sind, aber für ein bestimmtes Gebietsschema spezifisch sind. |
| `base/Magento/base/default` | Ähnlich für alle Bereiche, Themen und Gebietsschemata. |

### Zuordnen bereitgestellter Dateien

Der in der kompakten Strategie verwendete Bereitstellungsansatz bedeutet, dass Dateien von Basisthemen und Gebietsschemata übernommen werden. Diese Vererbungsrelationen werden in den Zuordnungsdateien für jede Kombination aus Bereich, Thema und Gebietsschema gespeichert. Es gibt separate map-Dateien für PHP und JS:

- `map.php`
- `requirejs-map.js`

Die `map.php` -Datei verwendet von [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) , um die richtigen URLs zu erstellen.

Die `requirejs-map.js` wird von der `baseUrlResolver` Plug-in für RequireJS.

Beispiel für `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Beispiel für `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Tipps für Erweiterungsentwickler

Verwenden Sie zum Erstellen von URLs für statische Ansichtsdateien [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Verwenden Sie keine URL-Verkettungen, um zu vermeiden, dass Probleme mit statischen Dateien beim Rendern der Seite nicht gefunden und nicht angezeigt werden.
