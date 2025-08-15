---
title: Follow-up zur Datenmigration
description: Erfahren Sie, wie Sie überprüfen können, ob Ihre Datenmigration von Magento 1 auf Magento 2 erfolgreich war und ob alle Funktionen erwartungsgemäß funktionieren.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Follow-up zur Datenmigration

Einige Verhaltensweisen und Logiken von Magento 1 wurden in Magento 2 anders implementiert. Der [!DNL Data Migration Tool] kümmert sich darum. Es gibt einige Migrationsaspekte, die Sie kennen sollten, und manchmal müssen Sie kleinere Schritte unternehmen, damit einige Funktionen nach der Migration reibungslos funktionieren.

## Informationen

### Aufspaltung der Datenbank nicht unterstützt

Die [!DNL Data Migration Tool] unterstützt keine geteilten Datenbanken.

### Gruppenpreise in Stufenpreise umgerechnet

Alle Gruppenpreise werden während der Migration automatisch in Stufenpreise umgerechnet.

### Neue Nummerierung für Verkaufsstellen

Referenznummern für Bestellungen, Rechnungen, Lieferungen, Gutschriften und Rücksendungen migrieren wie sie sind. Nach der Migration gelten die neuen Regeln für die Zahlenzuweisung an Magento 2. Die Zählung für die neuen Verkaufsstellen ist anders.

## Schritte

### Kundensegmente erneut speichern [nur Adobe Commerce]

Nach der Migration müssen Kundensegmente aus dem Admin Panel gespeichert werden, um sie einzurichten und auszuführen.

### Zeitzone konfigurieren

Das Tool migriert keine Zeitzoneneinstellungen. Daher müssen Sie die Zeitzone nach der Migration manuell unter **Stores** > **Configuration** > **Locale Options** > **Timezone** konfigurieren.

Standardmäßig speichert Magento Zeitdaten in der UTC-0-Zone in der Datenbank und zeigt sie entsprechend den aktuellen Zeitzoneneinstellungen an. Wenn Zeitdaten bereits in einer anderen Zone als UTC-0 in der Datenbank gespeichert wurden, müssen Sie die vorhandene Zeit mithilfe des [!DNL Data Migration Tool]-Handlers des `\Migration\Handler\Timezone` in UTC-0 konvertieren.

Im folgenden Beispiel hat Magento 1 fälschlicherweise Zeit in der UTC-7-Zone in der Datenbank gespart (z. B. aufgrund einer fehlerhaften Erweiterung eines Drittanbieters). Gehen Sie wie folgt vor, um die Erstellungszeit des Kundenkontos bei der Migration ordnungsgemäß in die UTC-0-Zone zu konvertieren:

1. Kopieren Sie die `map-customer.xml.dist` Konfigurationsdatei aus dem entsprechenden Verzeichnis der [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) in die `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Aktualisieren Sie den `<customer_map_file>` Knoten in `config.xml` und entfernen Sie die `.dist` Erweiterung aus `map-customer.xml.dist`

1. Fügen Sie der `map-customer.xml`-Datei die folgende Regel hinzu:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
