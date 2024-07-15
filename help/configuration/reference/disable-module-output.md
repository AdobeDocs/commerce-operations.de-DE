---
title: Modulausgabe deaktivieren
description: Erfahren Sie, wie Sie die Modulausgabe deaktivieren.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Modulausgabe deaktivieren

Standardmäßig sind alle Module so konfiguriert, dass die Modulausgabe in eine Ansicht geschrieben werden kann. Das Ausschalten der Ausgabe bietet eine Möglichkeit, ein Modul zu deaktivieren, das aufgrund harter Abhängigkeiten nicht deaktiviert werden kann.

Beispielsweise hängt das Modul `Customer` vom Modul `Review` ab, sodass das Modul `Review` nicht deaktiviert werden kann. Wenn Sie jedoch nicht möchten, dass Kunden Bewertungen bereitstellen, können Sie die Ausgabe vom `Review`-Modul deaktivieren.

>[!INFO]
>
>Wenn ein Händler die Modulausgabe in einer früheren Version mit dem Admin deaktiviert hat, müssen Sie das System für die Migration dieser Einstellungen manuell konfigurieren.

Die Deaktivierung der Ausgabe erfolgt in folgenden Klassen:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Durch Deaktivieren der Modulausgabe wird das Modul nicht deaktiviert. Das Modul bleibt aktiviert und funktioniert, es werden jedoch keine Blöcke, Seiten oder Felder am Frontend oder Backend gerendert.

## Deaktivieren der Modulausgabe in einer Pipeline-Bereitstellung

So deaktivieren Sie die Modulausgabe in der Pipeline-Bereitstellung oder einer anderen Bereitstellung mit mehreren Instanzen der Commerce-Anwendung:

1. Bearbeiten Sie die Datei `config.xml` des `Backend`-Moduls.
1. Exportieren Sie die Konfigurationsänderungen.

### Bearbeiten der Datei `Backend` module `config.xml`

1. Archivieren Sie die ursprüngliche `config.xml` -Datei.
1. Fügen Sie der Datei `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` Zeilen ähnlich den folgenden hinzu, direkt unter dem Element `<default>` :

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Hier:

   - `<modules_disable_output>` enthält eine Liste von Modulen.
   - `<Magento_Newsletter></Magento_Newsletter>` gibt an, für welches Modul die Ausgabe deaktiviert werden soll.
   - `1` ist die Markierung, die die Ausgabe für das `Magento_Newsletter`-Modul deaktiviert.

Als Beispielergebnis dieser Konfiguration können Kunden sich nicht mehr für den Erhalt von Newslettern anmelden.

### Konfigurationsänderungen exportieren

Führen Sie den folgenden Befehl aus, um die Konfigurationsänderungen zu exportieren:

```bash
bin/magento app:config:dump
```

Die Ergebnisse werden in die Datei `<Magento_install_dir>/app/etc/config.php` geschrieben.

Löschen Sie dann den Cache, um die neue Einstellung zu aktivieren:

```bash
bin/magento cache:clean config
```

Siehe [Konfiguration exportieren](../cli/export-configuration.md).

## Deaktivieren der Modulausgabe in einer einfachen Bereitstellung

Die Deaktivierung der Modulausgabe in einer einzigen Instanz von Commerce ist einfacher, da die Änderungen nicht verteilt werden müssen.

1. Archivieren Sie die ursprüngliche `<Magento_install_dir>/app/etc/config.php` -Datei.
1. Fügen Sie die Abschnitte `advanced` und `modules_disable_output` zur Datei `config.php` hinzu (sofern sie nicht vorhanden sind):

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

In diesem Beispiel wurde die Ausgabe für das Modul `Magento_Review` deaktiviert und Kunden können Produkte nicht mehr überprüfen.
Um die Ausgabe erneut zu aktivieren, setzen Sie den Wert auf `0`.
