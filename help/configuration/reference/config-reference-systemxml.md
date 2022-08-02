---
title: system.xml-Referenz
description: Erfahren Sie, wie die XML-Systemdatei die Konfiguration der Commerce-Anwendung verwaltet.
contributor_name: David Lambauer
contributor_link: https://github.com/DavidLambauer
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '2671'
ht-degree: 0%

---


# system.xml-Referenz

Die `system.xml` -Datei können Sie die Konfiguration des Commerce-Systems verwalten. Verwenden Sie dieses Thema als allgemeine Referenz für die `system.xml` -Datei. Die `system.xml` Datei befindet sich unter `etc/adminhtml/system.xml` in einer gegebenen Commerce 2-Erweiterung.

Das folgende Code-Snippet zeigt das leere Skelett der Datei:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Wenn Sie eine sofortige *XSD-Validierung in Ihrer IDE wünschen, können Sie `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Registerkarten // Abschnitte // Gruppen // Felder

Im `system.xml` -Datei können vier verschiedene Entitätstypen definiert werden, die miteinander verbunden sind. Im folgenden Abschnitt wird die Beziehung zwischen Registerkarten, Abschnitten, Gruppen und Feldern beschrieben. Im folgenden Screenshot wird die Commerce 2-Systemkonfiguration im Admin-Backend angezeigt.
Die roten Quadrate markieren die verschiedenen Typen, die in der Variablen `system.xml` Datei:

![Screenshot mit einem konfigurierten Abschnitt in der Admin-Konsole.](../../assets/configuration/magento2-system-configuration.png)

Registerkarten werden verwendet, um verschiedene Konfigurationsbereiche semantisch zu teilen. Jede Registerkarte kann einen oder mehrere Abschnitte enthalten, die auch als Untermenüs referenziert werden können. Ein Abschnitt enthält eine oder mehrere Gruppen.
Jede Gruppe listet ein oder mehrere Felder auf. Sie können auch eine Gruppe verwenden, um eine allgemeine Beschreibung für die folgenden Felder hinzuzufügen. Wie bereits erwähnt, kann jede Gruppe über ein oder mehrere Felder verfügen. Felder sind die kleinste Entität im Systemkonfigurationskontext.

## Registerkarten

A `<tab>`-Tag-Verweise auf eine vorhandene oder eine neue Registerkarte in der Systemkonfiguration.

### Registerattributreferenz

A `<tab>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Definiert die Kennung, mit der auf den Abschnitt verwiesen wird. | `typeId` | erforderlich |
| `translate` | Definiert das zu übersetzende Feld. Bereitstellung `label` um den Titel übersetzbar zu machen. | `string` | optional |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements - standardmäßig `text`. | `string` | optional |
| `sortOrder` | Definiert die Sortierreihenfolge des Abschnitts. Durch hohe Zahlen wird der Abschnitt an den unteren Rand der Seite verschoben. niedrige Zahlen drücken den Abschnitt nach oben. | `float` | optional |
| `class` | Fügt dem gerenderten tab-HTML-Element eine definierte CSS-Klasse hinzu. | `string` | optional |

### Registerknotenreferenz

A `<tab>`-Tag kann das folgende untergeordnete Element aufweisen:

| Knoten | Beschreibung | Typ |
|---------|------------------------------------------------------|----------|
| `label` | Definiert den Titel, der im Frontend angezeigt wird. | `string` |

### Beispiel: Erstellen einer Registerkarte

Das folgende Codefragment zeigt die Erstellung einer neuen Registerkarte mit Beispieldaten.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

Das obige Snippet erstellt eine neue Registerkarte mit der Kennung `A_UNIQUE_ID`. Als `translate`-attribute definiert ist und auf den Titel verweist, wird das `label`-node kann übersetzt werden. Während des Rendervorgangs wird die CSS-Klasse `a-custom-css-class-to-style-this-tab` wird auf das HTML-Element angewendet, das für diese Registerkarte erstellt wurde.
Die `sortOrder`-Attribut mit dem Wert von `10` definiert die Position der Registerkarte in der Liste aller Registerkarten beim Rendern.

## Abschnitte

A `<section>`-Tag-Verweise auf einen vorhandenen oder einen neuen Abschnitt in der Systemkonfiguration.

### Referenz zum Abschnittsattribut

A `<section>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definiert die Kennung, mit der auf den Abschnitt verwiesen wird. | `typeId` | erforderlich |
| `translate` | Definiert das zu übersetzende Feld. Bereitstellung `label` um den Titel übersetzbar zu machen. | `string` | optional |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements. Standardwert ist `text`. | `string` | optional |
| `sortOrder` | Definiert die Sortierreihenfolge des Abschnitts. Durch hohe Zahlen wird der Abschnitt an den unteren Rand der Seite verschoben. niedrige Zahlen drücken den Abschnitt nach oben. | `float` | optional |
| `showInDefault` | Definiert, ob der Abschnitt im standardmäßigen Konfigurationsbereich angezeigt wird. Angeben `1` , um den Abschnitt anzuzeigen, und `0` um den Abschnitt auszublenden. | `int` | optional |
| `showInStore` | Definiert, ob der Abschnitt auf Store-Ebene angezeigt wird. Angeben `1` , um den Abschnitt anzuzeigen, und `0` um den Abschnitt auszublenden. | `int` | optional |
| `showInWebsite` | Definiert, ob der Abschnitt auf Website-Ebene angezeigt wird. Angeben `1` , um den Abschnitt anzuzeigen, und `0` um den Abschnitt auszublenden. | `int` | optional |
| `canRestore` | Definiert, ob der Abschnitt standardmäßig wiederhergestellt werden kann. | `int` | optional |
| `advanced` | Veraltet seit 100.0.2. | `bool` | optional |
| `extends` | Durch Angabe einer Kennung eines anderen Abschnitts erweitert der Inhalt dieses Knotens den von Ihnen referenzierten Abschnitt. | `string` | optional |

### Knotenreferenz für Abschnitte

A `<section>`-Tag kann die folgenden untergeordneten Elemente aufweisen:

| Knoten | Beschreibung | Typ |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Definiert den Titel, der im Frontend angezeigt wird. | `string` |
| `class` | Fügt dem gerenderten Abschnitt-HTML-Element eine definierte CSS-Klasse hinzu. | `string` |
| `tab` | Verweist auf die zugehörige Registerkarte. Erwartet die Kennung der Registerkarte. | `typeTabId` |
| `header_css` | Weder zum Zeitpunkt dieses Schreibens verwendet noch ausgewertet. | `string` |
| `resource` | Verweist auf eine ACL-Ressource, um Berechtigungseinstellungen für diesen Abschnitt bereitzustellen. | `typeAclResourceId` |
| `group` | Definieren Sie eine oder mehrere Untergruppen. | `typeGroup` |
| `frontend_model` | Gibt ein anderes Frontend-Modell an, um das Rendering zu ändern und die Ausgabe zu ändern. | `typeModel` |
| `include` | Wird verwendet, um zusätzliche `system_include.xsd` kompatible Dateien. Wird normalerweise verwendet, um eine große `system.xml` Dateien. | `includeType` |

### Beispiel: Erstellen eines Abschnitts und Zuweisen zu einer Registerkarte

Das folgende Codefragment zeigt die grundlegende Verwendung der Erstellung eines neuen Abschnitts.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

Im oben beschriebenen Abschnitt wird die ID definiert `A_UNIQUE_SECTION_ID`, ist in der standardmäßigen Konfigurationsansicht und in einem Store-Kontext sichtbar. Die `label`-node kann übersetzt werden. Der Abschnitt ist der Registerkarte mit der ID zugeordnet. `A_UNIQUE_ID`. Auf den Abschnitt können nur Benutzer zugreifen, deren Berechtigungen in der ACL definiert sind `VENDOR_MODULE::path_to_the_acl_resource`.

## Gruppen

Die `<group>`-Tag wird verwendet, um Felder zu gruppieren.

### Gruppenattributreferenz

A `<group>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definiert die Kennung, mit der auf die Gruppe verwiesen wird. | `typeId` | erforderlich |
| `translate` | Definiert die zu übersetzenden Felder. Bereitstellung `label` um den Titel übersetzbar zu machen. Mehrere Felder sollten durch ein Leerzeichen getrennt werden. | `string` | optional |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements. Standardwert ist `text`. | `string` | optional |
| `sortOrder` | Definiert die Sortierreihenfolge des Abschnitts. Durch hohe Zahlen wird der Abschnitt an den unteren Rand der Seite verschoben. niedrige Zahlen drücken den Abschnitt nach oben. | `float` | optional |
| `showInDefault` | Definiert, ob die Gruppe im standardmäßigen Konfigurationsbereich angezeigt wird. Angeben `1` um die Gruppe anzuzeigen und `0` um die Gruppe auszublenden. | `int` | optional |
| `showInStore` | Definiert, ob die Gruppe auf Store-Ebene angezeigt wird. Angeben `1` um die Gruppe anzuzeigen und `0` um die Gruppe auszublenden. | `int` | optional |
| `showInWebsite` | Definiert, ob die Gruppe auf Website-Ebene angezeigt wird. Angeben `1` um die Gruppe anzuzeigen und `0` um die Gruppe auszublenden. | `int` | optional |
| `canRestore` | Definiert, ob die Gruppe standardmäßig wiederhergestellt werden kann. | `int` | optional |
| `advanced` | Veraltet seit 100.0.2. | `bool` | optional |
| `extends` | Durch Angabe einer Kennung einer anderen Gruppe erweitert der Inhalt dieses Knotens den von Ihnen referenzierten Abschnitt. | `string` | optional |

### Knoten-Referenz für Gruppen

A `<group>`-Tag kann die folgenden untergeordneten Elemente aufweisen:

| Knoten | Beschreibung | Typ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Definiert den Titel, der im Frontend angezeigt wird. | `string` |
| `fieldset_css` | Fügt einem Gruppenfeld eine oder mehrere CSS-Klassen hinzu. | `string` |
| `frontend_model` | Gibt ein anderes Frontend-Modell an, um das Rendering zu ändern und die Ausgabe zu ändern. | `typeModel` |
| `clone_model` | Gibt ein bestimmtes Modell zum Klonen von Feldern an. | `typeModel` |
| `clone_fields` | Das Klonen von Feldern wurde aktiviert oder deaktiviert. | `int` |
| `help_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `more_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `demo_link` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `comment` | Fügt einen Kommentar unter der Gruppentitel hinzu. Durch Verwendung von `<![CDATA[//]]>` HTML kann angewendet werden. | `string` |
| `hide_in_single_store_mode` | Ob die Gruppe im Einzelspeichermodus sichtbar sein soll. `1` blendet die Gruppe aus; `0` zeigt die Gruppe an. | `int` |
| `field` | Definieren Sie ein oder mehrere Felder, die unter dieser Gruppe verfügbar sein sollen. | `field` |
| `group` | Definieren Sie eine oder mehrere Untergruppen. | `unbounded` |
| `depends` | Kann verwendet werden, um Abhängigkeiten von anderen Feldern zu deklarieren. Wird verwendet, um bestimmte Felder/Gruppen nur anzuzeigen, wenn ein bestimmtes Feld den Wert `1`. Dieser Knoten erwartet eine `section/group/field`-string. | `depends` |
| `attribute` | Benutzerdefinierte Attribute können von Frontend-Modellen verwendet werden. Wird normalerweise verwendet, um ein bestimmtes Frontend-Modell dynamischer zu gestalten. | `attribute` |
| `include` | Wird verwendet, um zusätzliche `system_include.xsd` kompatible Dateien. Wird normalerweise verwendet, um eine große `system.xml` Dateien. | `includeType` |

>[!WARNING]
>
>Die Knoten `more_url`, `demo_url` und `help_url` werden durch ein PayPal-Frontend-Modell definiert, das nur einmal verwendet wird. Diese Knoten können nicht wiederverwendet werden.

### Beispiel: Erstellen einer Gruppe für einen bestimmten Abschnitt

Das folgende Codefragment zeigt die grundlegende Verwendung der Erstellung einer neuen Gruppe.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

Die oben beschriebene Gruppe definiert die ID `A_UNIQUE_GROUP_ID`, ist in der standardmäßigen Konfigurationsansicht und in einem Store-Kontext sichtbar. Beide, die `label` und `comment` als übersetzbar markiert werden.

## Felder

Die `<field>`-Tag wird innerhalb von `<group>`-Tags , um bestimmte Konfigurationswerte zu definieren.

### Feldattributreferenz

A `<field>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definiert die Kennung, mit der auf das Feld verwiesen wird. | `typeId` | erforderlich |
| `translate` | Definiert die zu übersetzenden Felder. Bereitstellung `label` um den Titel übersetzbar zu machen. Mehrere Felder sollten durch ein Leerzeichen getrennt werden. | `string` | optional |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements. Standardwert ist `text`. | `string` | optional |
| `sortOrder` | Definiert die Sortierreihenfolge des Abschnitts. Durch hohe Zahlen wird der Abschnitt an den unteren Rand der Seite verschoben. niedrige Zahlen drücken den Abschnitt nach oben. | `float` | optional |
| `showInDefault` | Definiert, ob das Feld im standardmäßigen Konfigurationsbereich angezeigt wird. Angeben `1` zum Anzeigen des Felds und `0` um das Feld auszublenden. | `int` | optional |
| `showInStore` | Definiert, ob das Feld auf Store-Ebene angezeigt wird. Angeben `1` zum Anzeigen des Felds und `0` um das Feld auszublenden. | `int` | optional |
| `showInWebsite` | Definiert, ob das Feld auf Website-Ebene angezeigt wird. Angeben `1` zum Anzeigen des Felds und `0` um das Feld auszublenden. | `int` | optional |
| `canRestore` | Definiert, ob das Feld standardmäßig wiederhergestellt werden kann. | `int` | optional |
| `advanced` | Veraltet seit 100.0.2. | `bool` | optional |
| `extends` | Durch Angabe einer Kennung eines anderen Felds erweitert der Inhalt dieses Knotens den von Ihnen referenzierten Abschnitt. | `string` | optional |

### Feldtyp-Referenz

A `<field>`-Tag kann die folgenden Werte für die `type=""` Attribut:

| Typ | Beschreibung |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Standard-, einzeilige Textfeld |
| `textarea` | Textblock |
| `select` | Normale Dropdown-Liste erfordert möglicherweise einen benutzerdefinierten `source_model`. Wird auch für `Yes/No` Auswahlen. Siehe `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` für ein Beispiel. |
| `multiselect` | liken `select` mehrere Optionen sind jedoch gültig. |
| `button` | Eine Schaltfläche, mit der ein sofortiges Ereignis Trigger wird. Erfordert ein benutzerdefiniertes Frontend-Modell, um den Schaltflächentext und die Aktion zu definieren. Siehe `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` für ein Beispiel. |
| `obscure` | Ein Textfeld mit dem verschlüsselten Wert, der als `****`. Wenn Sie den Typ mit &quot;Inspect Element&quot;im Browser ändern, wird der Wert nicht angezeigt. |
| `password` | liken `obscure` , außer dass der ausgeblendete Wert nicht verschlüsselt ist und eine erzwungene Änderung des Typs mit &quot;Inspect Element&quot;im Browser den Wert anzeigt. |
| `file` | Ermöglicht das Hochladen einer Datei zur Verarbeitung. |
| `label` | Zeigt eine Beschriftung anstelle eines bearbeitbaren Felds an. Verwenden Sie diesen Typ, wenn ein Feld nur in bestimmten Bereichen bearbeitbar ist, z. B. nur auf der Ebene der Store-Ansicht. |
| `time` | Steuerung zum Festlegen der Zeit mithilfe von drei Dropdown-Menüs - Stunde, Minute und Sekunde. |
| `allowspecific` | Eine Liste mit mehreren ausgewählten Ländern. Erfordert eine `source_model` wie `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Ermöglicht das Hochladen eines Bildes. |
| `note` | Ermöglicht das Hinzufügen einer informativen Notiz zur Seite. Dieser Typ erfordert eine `frontend_model` , um die Notiz zu rendern. |

Sie können auch einen benutzerdefinierten Feldtyp erstellen. Dies geschieht oft, wenn eine spezielle Schaltfläche mit einer Aktion erforderlich ist. Dazu sind zwei Hauptelemente erforderlich:

- Bausteine im `adminhtml` area
- Festlegen der `type=""` zum Pfad dieses Bausteins

Der Block selbst erfordert mindestens eine `__construct` -Methode und `getElementHtml()` -Methode. Die [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) ist ein einfaches Beispiel für einen benutzerdefinierten Typ.

Beispielsweise wird im OfflineShipping-Modul die Schaltfläche Exportieren definiert in `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` und die Felddefinition sieht wie folgt aus:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Feldknotenreferenz

A `<field>`-Tag kann die folgenden untergeordneten Elemente aufweisen:

| Knoten | Beschreibung | Typ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Definiert den Titel, der im Frontend angezeigt wird. | `string` |
| `comment` | Fügt einen Kommentar unter der Feldbeschriftung hinzu. Durch Verwendung von `<![CDATA[//]]>` HTML kann angewendet werden. | `string` |
| `tooltip` | Ein weiteres mögliches Frontend-Element, mit dem die Bedeutung dieses Felds beschrieben werden kann. Wird als kleines Symbol neben dem Feld angezeigt. | `string` |
| `hint` | Zeigt zusätzliche Informationen an. Nur verfügbar mit bestimmten `frontend_model`. | `string` |
| `frontend_class` | Fügt dem gerenderten Abschnitt-HTML-Element eine definierte CSS-Klasse hinzu. | `string` |
| `frontend_model` | Gibt ein anderes Frontend-Modell an, um das Rendering zu ändern und die Ausgabe zu ändern. | `typeModel` |
| `backend_model` | Gibt ein anderes Backend-Modell an, um die konfigurierten Werte zu ändern. | `typeModel` |
| `source_model` | Gibt ein anderes Quellmodell an, das einen bestimmten Satz von Werten bereitstellt. | `typeModel` |
| `config_path` | Kann verwendet werden, um den allgemeinen Konfigurationspfad eines Felds zu überschreiben. | `typeConfigPath` |
| `validate` | Definieren Sie unterschiedliche Validierungsregeln (durch Leerzeichen getrennt). Unten finden Sie eine vollständige Referenzliste der verfügbaren Validierungsregeln. | `string` |
| `can_be_empty` | Wird verwendet, wenn `type` is `multiselect` , um anzugeben, dass ein Feld leer sein kann. | `int` |
| `if_module_enabled` | Wird nur verwendet, um ein Feld anzuzeigen, wenn ein bestimmtes Modul aktiviert ist. | `typeModule` |
| `base_url` | Wird zusammen mit `upload_dir` für Datei-Uploads. | `typeUrl` |
| `upload_dir` | Geben Sie ein Zielverzeichnis für Uploads an. Dieser Knoten verfügt über zusätzliche Attribute und Knoten. Suchen Sie sie nach, bevor Sie dies verwenden. | `typeUploadDir` |
| `button_url` | Zeigt eine Schaltfläche an, wenn `button_url` und `button_label` angegeben werden. Wird normalerweise in Kombination mit einem benutzerdefinierten Frontend-Modell verwendet. | `typeUrl` |
| `button_label` | Zeigt eine Schaltfläche an, wenn `button_label` und `button_url` angegeben werden. Wird normalerweise in Kombination mit einem benutzerdefinierten Frontend-Modell verwendet. | `string` |
| `more_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `demo_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `hide_in_single_store_mode` | Ob die Gruppe im Einzelspeichermodus sichtbar sein soll. `1` blendet die Gruppe aus; `0` zeigt die Gruppe an. | `int` |
| `source_service` | Dienst zum Ausfüllen von Auswahloptionen. | `complexType` |
| `options` | Nicht verwendet. Potenziell veraltet. | `complexType` |
| `depends` | Kann verwendet werden, um Abhängigkeiten zu anderen Feldern zu deklarieren. Wird nur verwendet, um bestimmte Felder/Gruppen anzuzeigen, wenn ein bestimmtes Feld den Wert `1`. Dieser Knoten erwartet eine `section/group/field`-string. | `complexType` |
| `attribute` | Benutzerdefinierte Attribute können von Frontend-Modellen verwendet werden. Wird normalerweise verwendet, um ein bestimmtes Frontend-Modell dynamischer zu gestalten. | `complexType` |
| `requires` | Nicht erweiterbar. Siehe unten. | `complexType` |

>[!WARNING]
>
>Die Knoten `more_url`, `demo_url`, `requires` und `options` werden durch ein anderes Kernzahlungsmodell definiert und nur einmal verwendet. Diese Knoten können nicht wiederverwendet werden.

### Beispiel: Erstellen von zwei Feldern in einer bestimmten Gruppe

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

Im obigen Beispiel werden zwei Felder erstellt, die sowohl standardmäßig als auch in der Store-Ansicht sichtbar/konfigurierbar sind. Beide Felder verfügen über einen Kommentar und eine QuickInfo, um den Zweck für den Benutzer zu beschreiben. Die `label`-node kann übersetzt werden.
Das Feld mit der Kennung `ANOTHER_UNIQUE_FIELD_ID` ist sichtbar, wenn das angegebene Modul im `if_module_enabled` global aktiviert ist. Das Feld validiert seinen Wert auch anhand der Regeln `required-entry` und `no-whitespace`.
Das Feld mit der Kennung `A_UNIQUE_FIELD_ID` definiert ein anderes Quellmodell, das diese Werte bereitstellt `Yes` und `No`.

### Allgemeine Quellmodelle

Die folgenden Quellmodelle werden vom Commerce 2 Core bereitgestellt. Im Allgemeinen gibt es viele weitere Quellmodelle. In der folgenden Liste werden die häufigsten beschrieben. Beachten Sie, dass diese Quellmodelle das Feldattribut benötigen `type` auf `select` um ordnungsgemäß zu funktionieren.

| Quellmodell | Beschreibung |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Stellt die Werte bereit `Yes`, `No` und `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Stellt die Werte bereit `Enable`, `Disable`. Speichert die Werte als `0` und `1` in der Datenbank. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Stellt die Werte bereit `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` und `24 Hours`. Werte werden als Ganzzahlen gespeichert. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Stellt die Werte für das Zeitformat bereit (12 Stunden/24 Stunden). |
| `Magento\Cron\Model\Config\Source\Frequency` | Stellt die Werte bereit `Daily`, `Weekly` und `Monthly`. Werte werden in der Datenbank als `D`, `W` und `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Stellt die Werte für einen 2-Buchstaben-Code einer bestimmten Sprache im ISO 639-1-Format bereit (z. B. en). |
| `Magento\Config\Model\Config\Source\Locale` | Stellt die Werte bereit, die dem oben genannten ähneln, enthält jedoch einen Gebietsschema-Code (z. B. en_US). |

### Feldvalidierung

In einem Feld können eine oder mehrere Validator-Klassen zugewiesen werden, um sicherzustellen, dass die Eingabe des Benutzers die Anforderungen der Erweiterung erfüllt. Validierungsregeln können mit der `<validate>`-Tag.
Im folgenden Beispiel wird ein Feld validiert und mehrere unterschiedliche Validierungsregeln hinzugefügt.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Die folgenden Validierungsregeln sind verfügbar:

| Regel | Beschreibung |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Ermöglicht nur Buchstaben, Zahlen, Leerzeichen oder Unterstriche. |
| `integer` | Ermöglicht eine positive oder negative nicht-Dezimalzahl. |
| `ipv4` | Ermöglicht eine gültige IP-v4-Adresse. |
| `ipv6` | Ermöglicht eine gültige IP v6-Adresse. |
| `letters-only` | Ermöglicht nur Briefe. Beispiel, `abcABC`. |
| `letters-with-basic-punc` | Ermöglicht nur Briefe oder Satzzeichen.<br>Muss den folgenden Ausdruck übergeben: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Ermöglicht eine (UK)-Mobiltelefonnummer. |
| `no-marginal-whitespace` | Deaktiviert Leerzeichen am Anfang oder Ende des Werts. |
| `no-whitespace` | Unterbricht Leerzeichen. |
| `phoneUK` | Ermöglicht eine Telefonnummer (UK). |
| `phoneUS` | Ermöglicht eine Telefonnummer (US). |
| `required-entry` | Blendet einen leeren Wert aus (äquivalente Validierung als `validate-no-empty`).<br>Validierungsfehlermeldung: &quot;Dies ist ein erforderliches Feld.&quot; |
| `time` | Ermöglicht eine gültige Uhrzeit im 24-Stunden-Format zwischen 00:00 und 23:59 Uhr. Beispiel `15`, `15:05` oder `15:05:48`. |
| `time12h` | Ermöglicht eine gültige Zeit im 12-Stunden-Format zwischen 12:00 und 11 Uhr:59:17 Uhr Beispiel `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Ermöglicht 7 oder mehr Zeichen, wobei sowohl numerische als auch alphabetische Zeichen verwendet werden. |
| `validate-alphanum-with-spaces` | Ermöglicht die Verwendung von Buchstaben (a-z oder A-Z), Zahlen (0-9) oder Leerzeichen. |
| `validate-clean-url` | Ermöglicht eine gültige URL. Beispiel: `https://www.example.com` oder `www.example.com`. |
| `validate-currency-dollar` | Ermöglicht einen gültigen (Dollar-)Betrag. Beispiel: 100,00 $. |
| `validate-data` | Ermöglicht nur die Verwendung von Buchstaben (a-z oder A-Z), Zahlen (0-9) oder Unterstrichen (\_).<br>Das erste Zeichen muss ein Brief sein.<br>(Muss mit dem Ausdruck übereinstimmen: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Validierungsfehlermeldung: &quot;Bitte verwenden Sie in diesem Feld nur Buchstaben (a-z oder A-Z), Zahlen (0-9) oder Unterstriche (\_), und das erste Zeichen sollte ein Brief sein.&quot; |
| `validate-date-au` | Erzwingt das folgende Datumsformat: TT/MM/JJJJ. Beispiel: 17.03.2006 für den 17. März 2006. |
| `validate-email` | Ermöglicht eine gültige E-Mail-Adresse. Beispiel: johndoe@domain.com. |
| `validate-emailSender` | Ermöglicht eine gültige E-Mail-Adresse. Beispiel: johndoe@domain.com. |
| `validate-fax` | Ermöglicht eine gültige Faxnummer. Beispiel: 123-456-7890. |
| `validate-no-empty` | Blendet einen leeren Wert aus (äquivalente Validierung als `requried-entry`).<br>Validierungsfehlermeldung: &quot;Leerer Wert&quot;. |
| `validate-no-html-tags` | Deaktiviert die Verwendung von HTML-Tags. |
| `validate-password` | Ermöglicht 6 oder mehr Zeichen. Leerstellen am Anfang und am Ende werden ignoriert. |
| `validate-phoneLax` | Ermöglicht eine gültige Telefonnummer. Beispiel: (123) 456-7890 oder 123-456-7890. |
| `validate-phoneStrict` | Ermöglicht eine gültige Telefonnummer. Beispiel: (123) 456-7890 oder 123-456-7890. |
| `validate-select` | Stellt sicher, dass die ausgewählte Option keine `null` Wert, Zeichenfolgenwert von `none` oder die Zeichenfolgenlänge 0. |
| `validate-ssn` | Ermöglicht eine gültige Sozialversicherungsnummer (US). Beispiel: 123-45-6789. |
| `validate-street` | Ermöglicht nur die Verwendung von Buchstaben (a-z oder A-Z), Zahlen (0-9), Leerzeichen und &quot;#&quot;. |
| `validate-url` | Ermöglicht eine gültige URL. Protokoll ist erforderlich (http://, https:// oder ftp://). |
| `validate-xml-identifier` | Ermöglicht eine gültige XML-Kennung. Beispiel: etwas_1, block5, id-4. |
| `validate-zip-us` | Ermöglicht eine gültige (US-) Postleitzahl. Beispiel: 90602 oder 90602-1234. |
| `vinUS` | Ermöglicht (US-) Wert der Fahrzeugkennung (VIN). |

### Standardwerte

Standardwerte für Felder können in der Modulvorlage `etc/config.xml` Datei, indem Sie den Standardwert in der `section/group/field_ID` Knoten.

#### Beispiel: Festlegen des Standardwerts für `ANOTHER_UNIQUE_FIELD_ID` (Standardbereich)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Beispiel: Festlegen des Standardwerts für `ANOTHER_UNIQUE_FIELD_ID` (Website-Geltungsbereich)

Verwenden der `websites` -Tag, geben Sie den Standardwert für eine bestimmte Website an.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
