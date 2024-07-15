---
title: Folgemaßnahmen zur Datenmigration
description: Erfahren Sie, wie Sie überprüfen können, ob die Datenmigration von Magento 1 zu Magento 2 erfolgreich war und ob alle Funktionen erwartungsgemäß funktionieren.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Folgemaßnahmen zur Datenmigration

Das Verhalten und die Logik von Magento 1 sind in Magento 2 unterschiedlich implementiert. Die [!DNL Data Migration Tool] kümmert sich darum. Es gibt einige Migrationsaspekte, die Sie kennen sollten. Manchmal müssen Sie kleinere Schritte unternehmen, damit einige Funktionen nach der Migration reibungslos funktionieren.

## Informationen

### Geteilte Datenbank nicht unterstützt

Die [!DNL Data Migration Tool] unterstützt keine geteilten Datenbanken.

### Gruppenpreise in Tier-Preise umgerechnet

Alle Gruppenpreise werden während der Migration automatisch in Tier-Preise umgewandelt.

### Neue Nummerierung für Verkaufseinheiten

Referenznummern für Bestellungen, Rechnungen, Sendungen, Credit Memos und RMA migrieren unverändert. Nach der Migration gelten die neuen Magento 2-Zahlenzuweisungsregeln. Die Zahl für die neuen Verkaufseinheiten ist unterschiedlich.

## Schritte

### Kundensegmente erneut speichern [Nur Adobe Commerce]

Nach der Migration müssen Kundensegmente aus dem Admin Panel entfernt werden, damit sie funktionieren.

### Zeitzone konfigurieren

Das Tool migriert keine Zeitzoneneinstellungen. Daher müssen Sie die Zeitzone nach der Migration unter **Stores** > **Konfiguration** > **Gebietsschemaoptionen** > **Zeitzone** manuell konfigurieren.

Standardmäßig speichert Magento Zeitdaten in der UTC-0-Zone der Datenbank und zeigt sie entsprechend den aktuellen Zeitzoneneinstellungen an. Wenn Zeitdaten bereits in der Datenbank in einem anderen Bereich als UTC-0 gespeichert wurden, müssen Sie die vorhandene Zeit mithilfe des `\Migration\Handler\Timezone` -Handlers von [!DNL Data Migration Tool] in UTC-0 konvertieren.

Im folgenden Beispiel hat Magento 1 fälschlicherweise Zeit in der UTC-7-Zone der Datenbank gespart (z. B. aufgrund einer fehlerhaften Drittanbietererweiterung). Gehen Sie wie folgt vor, um die Erstellungszeit des Kundenkontos bei der Migration ordnungsgemäß in die UTC-0-Zone zu konvertieren:

1. Kopieren Sie die Konfigurationsdatei `map-customer.xml.dist` aus dem entsprechenden Verzeichnis der [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) in die Datei `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Aktualisieren Sie den Knoten `<customer_map_file>` in `config.xml` und entfernen Sie die Erweiterung `.dist` von `map-customer.xml.dist`

1. Fügen Sie der Datei `map-customer.xml` die folgende Regel hinzu:

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
