---
title: Bereitstellungsstrategien für statische Ansichtsdateien
description: Informationen zu Bereitstellungsstrategien für das Commerce-Programm.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Bereitstellungsstrategien für statische Ansichtsdateien

Beim Bereitstellen von statischen Ansichtsdateien können Sie eine der drei verfügbaren Strategien auswählen. Jeder dieser Schritte liefert optimale Bereitstellungsergebnisse für verschiedene Anwendungsfälle:

- [Standard](#standard-strategy): der reguläre Bereitstellungsprozess.
- [Quick](#quick-strategy) (_default_): minimiert den Zeitaufwand für die Bereitstellung, wenn Dateien für mehr als ein Gebietsschema bereitgestellt werden.
- [Kompakt](#compact-strategy): Minimiert den Speicherplatz, der von den veröffentlichten Ansichtsdateien belegt wird.

In den folgenden Abschnitten werden die Implementierungsdetails und -funktionen der einzelnen Strategien beschrieben.

## Standardstrategie

Wenn die Standardstrategie verwendet wird, werden alle statischen Ansichtsdateien für alle Pakete bereitgestellt, d. h. von [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php) verarbeitet.

Weitere Informationen finden Sie unter [Bereitstellen von statischen Ansichtsdateien](../cli/static-view-file-deployment.md).

## Schnelle Strategie

Die Schnellstrategie führt die folgenden Aktionen aus:

1. Für jedes Design wird ein beliebiges Gebietsschema ausgewählt und alle Dateien für dieses Gebietsschema werden bereitgestellt, wie in der Standardstrategie.
1. Für alle anderen Gebietsschemata des Designs:

   1. Dateien, die das bereitgestellte Gebietsschema überschreiben, werden definiert und bereitgestellt.
   1. Alle anderen Dateien gelten für alle Gebietsschemata als ähnlich und werden aus dem bereitgestellten Gebietsschema kopiert.

>[!INFO]
>
>Mit _similar_ meinen wir Dateien, die unabhängig vom Gebietsschema, Design oder Bereich sind. Diese Dateien können CSS, Bilder und Schriftarten enthalten.

Dieser Ansatz minimiert die Bereitstellungszeit, die für mehrere Gebietsschemata erforderlich ist, obwohl eine Vielzahl von Dateien dupliziert wird.

## Kompakte Strategie

Die kompakte Strategie vermeidet Dateiduplizierung, indem ähnliche Dateien in `base` Unterverzeichnissen gespeichert werden.

Für das am besten optimierte Ergebnis werden drei Bereiche für mögliche Ähnlichkeit zugewiesen: Bereich, Design und Gebietsschema. Die `base` Unterverzeichnisse werden für alle Kombinationen dieser Bereiche erstellt.

Die Dateien werden gemäß den folgenden Mustern in diesen Unterverzeichnissen bereitgestellt.

| Muster | Beschreibung |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Für einen bestimmten Bereich, ein bestimmtes Design und ein bestimmtes Gebietsschema spezifische Dateien |
| `<area>/<theme>/default` | Ähnliche Dateien für alle Gebietsschemata eines bestimmten Designs eines bestimmten Bereichs. |
| `<area>/Magento/base/<locale>` | Dateien, die für einen bestimmten Bereich und ein bestimmtes Gebietsschema spezifisch sind, aber für alle Designs ähnlich sind. |
| `<area>/Magento/base/default` | Dateien, die für einen bestimmten Bereich spezifisch sind, aber für alle Designs und Gebietsschemata ähnlich sind. |
| `base/Magento/base/<locale>` | Dateien, die für alle Bereiche und Designs ähnlich sind, aber für ein bestimmtes Gebietsschema spezifisch sind. |
| `base/Magento/base/default` | Ähnlich für alle Bereiche, Themen und Gebietsschemata. |

### Zuordnen von bereitgestellten Dateien

Der in der kompakten Strategie verwendete Bereitstellungsansatz bedeutet, dass Dateien von Basisthemen und Gebietsschemata übernommen werden. Diese Vererbungsbeziehungen werden in den Zuordnungsdateien für jede Kombination von Bereich, Design und Gebietsschema gespeichert. Es gibt separate Map-Dateien für PHP und JS:

- `map.php`
- `requirejs-map.js`

Die `map.php` wird von [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) zum Erstellen korrekter URLs verwendet.

Die `requirejs-map.js` wird vom `baseUrlResolver`-Plug-in für RequireJS verwendet.

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

## Tipps für Entwickler von Erweiterungen

Um URLs für statische Ansichtsdateien zu erstellen, verwenden Sie [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Verwenden Sie keine URL-Verkettungen, um Probleme mit statischen Dateien zu vermeiden, die beim Rendern der Seite nicht gefunden und nicht angezeigt werden.
