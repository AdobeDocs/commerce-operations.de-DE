---
title: Modulausgabe deaktivieren
description: Erfahren Sie, wie Sie die Modulausgabe in Adobe Commerce deaktivieren, ohne Abhängigkeiten zu entfernen. Erfahren Sie mehr über Konfigurationsschritte und Anwendungsfälle.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Modulausgabe deaktivieren

Standardmäßig sind alle Module so konfiguriert, dass die Modulausgabe in eine Ansicht geschrieben werden kann. Das Deaktivieren der Ausgabe bietet eine Möglichkeit, ein Modul, das aufgrund von harten Abhängigkeiten nicht deaktiviert werden kann, im Wesentlichen zu deaktivieren.

Das `Customer` hängt beispielsweise vom `Review` ab, weshalb das `Review` nicht deaktiviert werden kann. Wenn Sie jedoch nicht möchten, dass Kunden Bewertungen bereitstellen, können Sie die Ausgabe aus dem `Review`-Modul deaktivieren.

>[!INFO]
>
>Wenn ein Händler in einer früheren Version den Administrator verwendet hat, um die Modulausgabe zu deaktivieren, müssen Sie das System manuell konfigurieren, um diese Einstellungen zu migrieren.

Die Output-Deaktivierung wird in den folgenden Klassen durchgeführt:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Durch Deaktivieren der Modulausgabe wird das Modul nicht deaktiviert. Das Modul bleibt aktiviert und funktioniert, aber es wird kein Block, keine Seite und kein Feld im Frontend oder Backend gerendert.

## Deaktivieren der Modulausgabe in einer Pipeline-Bereitstellung

So deaktivieren Sie die Modulausgabe in der Pipeline-Bereitstellung oder einer anderen Bereitstellung mit mehreren Instanzen der Commerce-Anwendung:

1. Bearbeiten Sie die `Backend` des `config.xml`.
1. Exportieren der Konfigurationsänderungen

### Bearbeiten der `Backend`-`config.xml`

1. Archivieren Sie die ursprüngliche `config.xml`.
1. Fügen Sie der `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`-Datei direkt unter dem `<default>`-Element Zeilen wie die folgenden hinzu:

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
   - `1` ist das Flag, das die Ausgabe für das `Magento_Newsletter`-Modul deaktiviert.

Aufgrund dieser Konfiguration können sich Kunden beispielsweise nicht mehr für den Erhalt von Newslettern anmelden.

### Exportieren der Konfigurationsänderungen

Führen Sie den folgenden Befehl aus, um die Konfigurationsänderungen zu exportieren:

```bash
bin/magento app:config:dump
```

Die Ergebnisse werden in die `<Magento_install_dir>/app/etc/config.php` geschrieben.

Löschen Sie anschließend den Cache, um die neue Einstellung zu aktivieren:

```bash
bin/magento cache:clean config
```

Siehe [Exportieren der Konfiguration](../cli/export-configuration.md).

## Deaktivieren der Modulausgabe in einer einfachen Bereitstellung

Die Vorgehensweise zum Deaktivieren der Modulausgabe auf einer einzigen Instanz von Commerce ist einfacher, da die Änderungen nicht verteilt werden müssen.

1. Archivieren Sie die ursprüngliche `<Magento_install_dir>/app/etc/config.php`.
1. Fügen Sie die Abschnitte `advanced` und `modules_disable_output` zur `config.php` hinzu (falls sie nicht vorhanden sind):

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

In diesem Beispiel wurde die Ausgabe für das Modul `Magento_Review` deaktiviert, sodass Kunden die Produkte nicht mehr überprüfen können.

### Erneutes Aktivieren der Modulausgabe

Um die Ausgabe wieder zu aktivieren, setzen Sie den Wert für das Modul auf `0` oder entfernen Sie die Zeile/das Modul aus der `config.php`.
