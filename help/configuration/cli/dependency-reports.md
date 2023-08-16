---
title: Abhängigkeitsberichte
description: Erstellen Sie Berichte, die die Summen für Modul-, Rundschreiben- und Framework-Abhängigkeiten anzeigen.
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Abhängigkeitsberichte

{{file-system-owner}}

Sie können die folgenden Berichtstypen ausführen:

- **Modulabhängigkeiten**: Zeigt die Gesamtanzahl der Abhängigkeiten zwischen Modulen und ob die Abhängigkeiten hart oder weich sind.
- **Zirkuläre Abhängigkeiten**: Zeigt die Gesamtanzahl der Abhängigkeitsketten sowie die Anzahl und Liste der zirkulären Abhängigkeiten für jedes Modul an.
- **Framework-Abhängigkeiten**: Zeigt die Gesamtanzahl der Abhängigkeiten vom Commerce-Framework nach Modul an (einschließlich der Gesamtanzahl der Framework-Einträge für jede Bibliothek).

Eine Abhängigkeit in einem Kommentar ist auch eine Abhängigkeit.

## Ausführen von Abhängigkeitsberichten

Befehlsoptionen:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

In der folgenden Tabelle werden die Optionen, Parameter und Werte dieses Befehls erläutert.

| Parameter | Wert | Erforderlich? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Modulabhängigkeitsbericht. | Ja |
| `show-modules-circular` | Bericht zu zirkulären Abhängigkeiten . | Ja |
| `show-framework` | Framework-Abhängigkeitsbericht. | Ja |
| `-d --directory` | Pfad zum Basisverzeichnis, um mit der Suche nach Berichtsdaten zu beginnen. | Nein |
| `-o --output` | Gibt den absoluten Dateisystempfad und Dateinamen der CSV-Ausgabedatei (CSV) für den Bericht an. | Nein |

Wenn kein Ordner oder Dateiname als Argument übergeben wird, wird der folgende Anwendungsstamm als Standardordner verwendet und die folgenden Standarddateinamen werden verwendet:

| Befehl | Dateiname |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Bericht zu Modulabhängigkeiten

Im Folgenden finden Sie einen Teil der Ausgabe eines Beispielmodulabhängigkeitsberichts:

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Beispielbericht zu zirkulären Abhängigkeiten

Im Folgenden finden Sie einen Teil der Ausgabe eines Beispiel-Berichts mit zirkulären Abhängigkeiten :

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Beispiel für Framework-Abhängigkeitsbericht

Im Folgenden finden Sie einen Teil der Ausgabe für einen Beispiel-Framework-Abhängigkeitsbericht:

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
