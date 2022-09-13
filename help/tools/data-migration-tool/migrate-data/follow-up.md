---
title: Folgemaßnahmen zur Datenmigration
description: Erfahren Sie, wie Sie überprüfen können, ob die Datenmigration von Magento 1 nach Magento 2 erfolgreich war und ob alle Funktionen erwartungsgemäß funktionieren.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Folgemaßnahmen zur Datenmigration

Einige Verhaltensweisen und Logiken von Magento 1 wurden in Magento 2 unterschiedlich implementiert. Die [!DNL Data Migration Tool] kümmert sich darum. Es gibt einige Migrationsaspekte, die Sie kennen sollten. Manchmal müssen Sie kleinere Schritte unternehmen, damit einige Funktionen nach der Migration reibungslos funktionieren.

## Informationen

### Geteilte Datenbank nicht unterstützt

Die [!DNL Data Migration Tool] unterstützt keine Split-Datenbanken.

### Gruppenpreise in Tier-Preise umgerechnet

Alle Gruppenpreise werden während der Migration automatisch in Tier-Preise umgewandelt.

### Neue Nummerierung für Verkaufseinheiten

Referenznummern für Bestellungen, Rechnungen, Sendungen, Credit Memos und RMA migrieren unverändert. Nach der Migration gelten die neuen Magento 2-Zahlenzuweisungsregeln. Die Zahl für die neuen Verkaufseinheiten ist unterschiedlich.

## Schritte

### Kundensegmente erneut speichern [Nur Adobe Commerce]

Nach der Migration müssen Kundensegmente aus dem [Admin](https://glossary.magento.com/admin) Bedienfeld zum Einrichten und Ausführen.

### Zeitzone konfigurieren

Das Tool migriert keine Zeitzoneneinstellungen. Daher müssen Sie die Zeitzone nach der Migration manuell konfigurieren, indem Sie **Stores** > **Konfiguration** > **Gebietsschemaoptionen** > **Zeitzone**.

Standardmäßig speichert Magento Zeitdaten in der UTC-0-Zone in der Datenbank und zeigt sie entsprechend den aktuellen Zeitzoneneinstellungen an. Wenn Zeitdaten bereits in einer anderen Zone als UTC-0 in der Datenbank gespeichert wurden, müssen Sie die vorhandene Zeit mithilfe der [!DNL Data Migration Tool]s `\Migration\Handler\Timezone` Handler.

Im folgenden Beispiel wurde in Magento 1 fälschlicherweise Zeit in der UTC-7-Zone der Datenbank gespart (z. B. aufgrund einer fehlerhaften Drittanbietererweiterung). Gehen Sie wie folgt vor, um die Erstellungszeit des Kundenkontos bei der Migration ordnungsgemäß in die UTC-0-Zone zu konvertieren:

1. Kopieren Sie die `map-customer.xml.dist` Konfigurationsdatei aus dem entsprechenden Verzeichnis der [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) in die `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` -Datei.

1. Aktualisieren Sie die `<customer_map_file>` Knoten in `config.xml` und entfernen Sie die `.dist` Erweiterung von `map-customer.xml.dist`

1. Fügen Sie die folgende Regel zum `map-customer.xml` Datei:

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