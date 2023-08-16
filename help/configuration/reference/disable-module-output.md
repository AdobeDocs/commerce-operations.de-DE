---
title: Modulausgabe deaktivieren
description: Erfahren Sie, wie Sie die Modulausgabe deaktivieren.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Modulausgabe deaktivieren

Standardmäßig sind alle Module so konfiguriert, dass die Modulausgabe in eine Ansicht geschrieben werden kann. Das Ausschalten der Ausgabe bietet eine Möglichkeit, ein Modul zu deaktivieren, das aufgrund harter Abhängigkeiten nicht deaktiviert werden kann.

Beispiel: die `Customer` -Modul hängt von der `Review` -Modul, also die `Review` -Modul kann nicht deaktiviert werden. Wenn Sie jedoch nicht möchten, dass Kunden Bewertungen bereitstellen, können Sie die Ausgabe aus der `Review` -Modul.

>[!INFO]
>
>Wenn ein Händler die Modulausgabe in einer früheren Version mit dem Admin deaktiviert hat, müssen Sie das System für die Migration dieser Einstellungen manuell konfigurieren.

Die Deaktivierung der Ausgabe erfolgt in folgenden Klassen:

- [\Magento\Framework\View\Element\AbstractBlock::toHTML](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Durch Deaktivieren der Modulausgabe wird das Modul nicht deaktiviert. Das Modul bleibt aktiviert und funktioniert, es werden jedoch keine Blöcke, Seiten oder Felder am Frontend oder Backend gerendert.

## Deaktivieren der Modulausgabe in einer Pipeline-Bereitstellung

So deaktivieren Sie die Modulausgabe in der Pipeline-Bereitstellung oder einer anderen Bereitstellung mit mehreren Instanzen der Commerce-Anwendung:

1. Bearbeiten Sie die `Backend` -Modul `config.xml` -Datei.
1. Exportieren Sie die Konfigurationsänderungen.

### Bearbeiten Sie die `Backend` Modul `config.xml` file

1. Original archivieren `config.xml` -Datei.
1. Fügen Sie Zeilen ähnlich den folgenden hinzu, um die `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` direkt unter der `<default>` element:

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
   - `1` ist das Flag, das die Ausgabe für `Magento_Newsletter` -Modul.

Als Beispielergebnis dieser Konfiguration können Kunden sich nicht mehr für den Erhalt von Newslettern anmelden.

### Konfigurationsänderungen exportieren

Führen Sie den folgenden Befehl aus, um die Konfigurationsänderungen zu exportieren:

```bash
bin/magento app:config:dump
```

Die Ergebnisse werden in die `<Magento_install_dir>/app/etc/config.php` -Datei.

Löschen Sie dann den Cache, um die neue Einstellung zu aktivieren:

```bash
bin/magento cache:clean config
```

Siehe [Konfiguration exportieren](../cli/export-configuration.md).

## Deaktivieren der Modulausgabe in einer einfachen Bereitstellung

Die Deaktivierung der Modulausgabe in einer einzelnen Instanz von Commerce ist einfacher, da die Änderungen nicht verteilt werden müssen.

1. Original archivieren `<Magento_install_dir>/app/etc/config.php` -Datei.
1. Fügen Sie die `advanced` und `modules_disable_output` -Abschnitte `config.php` Datei (sofern nicht vorhanden):

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

In diesem Beispiel wird die Ausgabe für `Magento_Review` -Modul deaktiviert wurde und Kunden keine Produkte mehr überprüfen können.
Um die Ausgabe erneut zu aktivieren, setzen Sie den Wert auf `0`.
